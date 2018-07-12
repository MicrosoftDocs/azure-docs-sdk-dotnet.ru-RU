---
title: 'Библиотеки управления Azure для .NET: принципы использования и шаблоны'
description: ''
keywords: Azure, .NET, SDK, API, patterns, concepts, fluent, logging
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: b817216e114e5ab3ff22c1c5adb0f892c7874147
ms.sourcegitcommit: 1c2e1fd031ad012d6888fcde3cd325f7e8e49e0f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2018
ms.locfileid: "29752866"
---
# <a name="azure-management-library-for-net-fluent-concepts"></a>Библиотека управления Azure для .NET: принципы использования текучего интерфейса

Эта статья поможет вам понять, как эффективно использовать текучий интерфейс в библиотеках управления Azure для .NET.

## <a name="building-resources-using-a-fluent-interface"></a>Создание ресурсов с помощью текучего интерфейса

Текучий интерфейс — это специальная форма шаблона построителя, которая создает объекты с помощью цепочки методов, обеспечивающей правильную конфигурацию ресурса. Например, точка входа объекта Azure создается с помощью текучего интерфейса:

```csharp
var azure = Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

## <a name="resource-collections"></a>Коллекции ресурсов

Объект `Microsoft.Azure.Management.Fluent.Azure`, показанный выше, — это точка входа для создания всех ресурсов в текучих библиотеках управления. Выберите тип ресурсов для работы, используя методы коллекций ресурсов в объекте `Azure`. Например, ресурсы для базы данных SQL:

```csharp
var sql = azure.SqlServers.Define(sqlServerName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithAdministratorLogin(administratorLogin)
    .WithAdministratorPassword(administratorPassword)
    .Create();
```

Как видно из примера выше, текучее взаимодействие с API начинается с выбора соответствующего ресурса коллекции для ресурсов Azure, которые вам необходимы для работы.  Технология IntelliSense в Visual Studio поможет вам продолжить это взаимодействие. 

![GIF-изображение: технология Intellisense в Visual Studio, обеспечивающая взаимодействие](media/dotnet-sdk-azure-concepts/vs-fluent.gif)   

## <a name="lists-and-iterations"></a>Списки и итерации

Каждая коллекция ресурсов использует метод `List()`, который возвращает каждый экземпляр этого ресурса в текущей подписке. Например, `Azure.SqlServers.List()` возвращает все серверы SQL в подписке.

Используйте метод `ListByResourceGroup()`, чтобы ограничить возвращаемый список определенной [группой ресурсов Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups).  

Выполните итерацию для возвращенной коллекции так же, как для обычного списка `List<T>`:

```csharp
var vmList = azure.VirtualMachines.List();
foreach(var vm in vmList)
{
    Console.WriteLine("VM Name: {0}", vm.Name);
}
```   

## <a name="actionable-verbs"></a>Готовые к работе команды

Методы коллекции ресурсов с командами в именах выполняются в Azure немедленно. Эти методы работают синхронно. Пока они не будут завершены, выполнение в текущем потоке блокируется. 

| Команда   |  Пример использования |
|--------|---------------|
| Создание | `azure.VirtualMachines.Create(listOfVMCreatables)` |
| Применить  | `virtualMachineScaleSet.Update().WithCapacity(6).Apply()` |
| Delete | `azure.Disks.DeleteById(id)` | 
| список   | `azure.SqlServers.List()` | 
| Получить    | `var vm  = azure.VirtualMachines.GetByResourceGroup(group, vmName)` |

>[!NOTE]
> `Define()` и `Update()` являются командами, но они не блокируют выполнение, если не сопровождаются `Create()` или `Apply()`.
 
Определенные объекты ресурсов содержат команды, которые изменяют состояние ресурса в Azure. Например: 

```csharp
var vmToRestart = azure.VirtualMachines.GetById(id);
vmToRestart.Restart();
```

Большинство методов, описанных в этом разделе, имеют также асинхронную версию, которая обозначается суффиксом `Async`.

```csharp
Task restartTask = azure.VirtualMachines.GetById(id).RestartAsync();
```

## <a name="lazy-resource-creation"></a>Создание отложенных ресурсов

При создании ресурсов Azure возникает проблемная ситуация, когда новый ресурс зависит от другого ресурса, который еще не существует. Пример — резервирование общедоступного IP-адреса и настройка диска при создании виртуальной машины. Предположим, вам не нужно проверять резервирование адреса или создание диска — вы просто хотите настроить виртуальную машину с этими ресурсами.

Используйте создаваемые объекты, чтобы определить ресурсы Azure для использования в коде. Но создавайте их, только если они нужны вам в Azure. Код, написанный с использованием создаваемых объектов, перенаправляет нагрузку создания ресурсов в среде Azure в API управления, что повышает производительность. 

Получить создаваемые объекты можно с помощью команды `Define()` коллекций ресурсов без команды `Create()`:

```csharp
// Init a creatable Public IP Address
var publicIpAddressCreatable = azure.PublicIPAddresses.Define("publicIPAddressName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName);
```

Ресурс Azure, определенный создаваемым объектом, еще не существует в вашей подписке. Создаваемый объект — это локальное представление ресурса, которое при необходимости создает API управления (при вызове `.Create()`). Используйте этот создаваемый объект в определении других ресурсов Azure, которым требуется этот ресурс. 

```csharp
// Init a creatable VM using the creatable Public IP Address
var vmCreatable = azure.VirtualMachines.Define("creatableVM")
    // ...
    .withNewPrimaryPublicIPAddress(publicIPAddressCreatable)
    // ...
```

Создайте ресурсы в подписке Azure с помощью метода `Create()` для коллекции ресурсов. 

```csharp
// Create the VM and its Public IP Address
var virtualMachine = azure.VirtualMachines.Create(vmCreatable);
```

Передача создаваемых объектов в `Create()` возвращает объект `ICreatedResources` вместо объекта с одним ресурсом.  Объект `CreatedRelatedResource` обеспечивает доступ ко всем ресурсам, созданным вызовом `Create()`, а не только к типу из коллекции ресурсов. Доступ к общедоступному IP-адресу, созданному в Azure для виртуальной машины, которая создается в примере выше:

```csharp
var pip = virtualMachine.CreatedRelatedResource(publicIPAddressCreatable.Key()) as PublicIPAddress;;
```    

## <a name="exception-handling"></a>Обработка исключений

API управления определяет классы исключений, которые расширяют `Microsoft.Rest.RestException`. Перехват исключений, создаваемых API управления, выполняется с помощью блока `catch (RestException exception)` после соответствующей инструкции `try`.

## <a name="logs-and-tracing"></a>Журналы и трассировка

Для ведения журналов в текучих библиотеках управления Azure для .NET используется базовая трассировка клиентской службы [AutoRest](https://github.com/Azure/AutoRest).

Создайте класс, реализующий перехватчик `Microsoft.Rest.IServiceClientTracingInterceptor`.  Этот класс будет отвечать за перехват сообщений журнала и их передачу в любое используемое средство ведения журнала.  В этом примере мы просто записываем сообщения в консоль, но их также можно передать в Log4Net, `Microsoft.Extensions.Logging` или любую другую платформу ведения журналов.

```csharp
class ConsoleTracer : IServiceClientTracingInterceptor
{
    public void Information(string message)
    {
        Console.WriteLine(message);
    }

    public void TraceError(string invocationId, Exception exception)
    {
        Console.WriteLine("Exception in {0}: {1}", invocationId, exception);
    }

    public void ReceiveResponse(string invocationId, HttpResponseMessage response) { }

    public void SendRequest(string invocationId, HttpRequestMessage request) { }

    public void Configuration(string source, string name, string value) { }

    public void EnterMethod(string invocationId, object instance, string method, IDictionary<string, object> parameters) { }

    public void ExitMethod(string invocationId, object returnValue) { }
}
```

Перед созданием объекта `Microsoft.Azure.Management.Fluent.Azure` инициализируйте перехватчик `IServiceClientTracingInterceptor`, созданный выше с помощью вызова `ServiceClientTracing.AddTracingInterceptor()`, и задайте для параметра `ServiceClientTracing.IsEnabled` значение *true*.  При создании объекта `Azure` включите методы `.WithDelegatingHandler()` и `.WithLogLevel()`, чтобы подключить клиент к трассировке клиентской службы AutoRest.

```csharp
ServiceClientTracing.AddTracingInterceptor(new ConsoleTracer());
ServiceClientTracing.IsEnabled = true;

var azure = Azure
    .Configure()
    .WithDelegatingHandler(new HttpLoggingDelegatingHandler())
    .WithLogLevel(HttpLoggingDelegatingHandler.Level.Basic)
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

Уровни журнала `HttpLoggingDelegatingHandler` определяются следующим образом:

| Уровень трассировки | Ведение журнала включено 
| ------------ | ---------------
| HttpLoggingDelegatingHandler.Level.None | Нет выходных данных.
| HttpLoggingDelegatingHandler.Level.Basic | Регистрация URL-адресов для базовых вызовов REST, кодов и времени ответов.
| HttpLoggingDelegatingHandler.Level.Body | Регистрация тех же элементов, что и для уровня Basic, а также текста запросов и ответов для вызовов REST.
| HttpLoggingDelegatingHandler.Level.Headers | Регистрация тех же элементов, что и для уровня Basic, а также заголовков запросов и ответов для вызовов REST.
| HttpLoggingDelegatingHandler.Level.BodyAndHeaders | Регистрация тех же элементов, что и для уровней журнала BODY и HEADERS в совокупности.
