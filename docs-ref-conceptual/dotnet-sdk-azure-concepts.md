---
title: 'Библиотеки управления Azure для .NET: принципы использования и шаблоны'
description: ''
ms.date: 10/19/2017
ms.openlocfilehash: 0a6ae94046680b81f1222c3c2acc6df9871bff4a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190607"
---
# <a name="azure-management-library-for-net-fluent-concepts"></a><span data-ttu-id="cc00d-102">Библиотека управления Azure для .NET: принципы использования текучего интерфейса</span><span class="sxs-lookup"><span data-stu-id="cc00d-102">Azure management library for .NET fluent concepts</span></span>

<span data-ttu-id="cc00d-103">Эта статья поможет вам понять, как эффективно использовать текучий интерфейс в библиотеках управления Azure для .NET.</span><span class="sxs-lookup"><span data-stu-id="cc00d-103">This article will help you understand how to effectively use the fluent interface in the Azure management libraries for .NET.</span></span>

## <a name="building-resources-using-a-fluent-interface"></a><span data-ttu-id="cc00d-104">Создание ресурсов с помощью текучего интерфейса</span><span class="sxs-lookup"><span data-stu-id="cc00d-104">Building resources using a fluent interface</span></span>

<span data-ttu-id="cc00d-105">Текучий интерфейс — это специальная форма шаблона построителя, которая создает объекты с помощью цепочки методов, обеспечивающей правильную конфигурацию ресурса.</span><span class="sxs-lookup"><span data-stu-id="cc00d-105">A fluent interface is a specific form of the builder pattern that creates objects through a method chain that enforces correct configuration of a resource.</span></span> <span data-ttu-id="cc00d-106">Например, точка входа объекта Azure создается с помощью текучего интерфейса:</span><span class="sxs-lookup"><span data-stu-id="cc00d-106">For example, the entry-point Azure object is created using a fluent interface:</span></span>

```csharp
var azure = Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

## <a name="resource-collections"></a><span data-ttu-id="cc00d-107">Коллекции ресурсов</span><span class="sxs-lookup"><span data-stu-id="cc00d-107">Resource collections</span></span>

<span data-ttu-id="cc00d-108">Объект `Microsoft.Azure.Management.Fluent.Azure`, показанный выше, — это точка входа для создания всех ресурсов в текучих библиотеках управления.</span><span class="sxs-lookup"><span data-stu-id="cc00d-108">The `Microsoft.Azure.Management.Fluent.Azure` object shown above is the entry point for all resource creation in the fluent management libraries.</span></span> <span data-ttu-id="cc00d-109">Выберите тип ресурсов для работы, используя методы коллекций ресурсов в объекте `Azure`.</span><span class="sxs-lookup"><span data-stu-id="cc00d-109">Select which type of resources to work with using the resource collections in the `Azure` object.</span></span> <span data-ttu-id="cc00d-110">Например, ресурсы для базы данных SQL:</span><span class="sxs-lookup"><span data-stu-id="cc00d-110">For example, for SQL Database:</span></span>

```csharp
var sql = azure.SqlServers.Define(sqlServerName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithAdministratorLogin(administratorLogin)
    .WithAdministratorPassword(administratorPassword)
    .Create();
```

<span data-ttu-id="cc00d-111">Как видно из примера выше, текучее взаимодействие с API начинается с выбора соответствующего ресурса коллекции для ресурсов Azure, которые вам необходимы для работы.</span><span class="sxs-lookup"><span data-stu-id="cc00d-111">As seen above, most fluent "conversations" you have with the API start with selecting the appropriate resource collection for the Azure resources you need to work with.</span></span>  <span data-ttu-id="cc00d-112">Технология IntelliSense в Visual Studio поможет вам продолжить это взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="cc00d-112">Intellisense in Visual Studio then guides you through the conversation.</span></span> 

![GIF-изображение: технология Intellisense в Visual Studio, обеспечивающая взаимодействие](media/dotnet-sdk-azure-concepts/vs-fluent.gif)   

## <a name="lists-and-iterations"></a><span data-ttu-id="cc00d-114">Списки и итерации</span><span class="sxs-lookup"><span data-stu-id="cc00d-114">Lists and iterations</span></span>

<span data-ttu-id="cc00d-115">Каждая коллекция ресурсов использует метод `List()`, который возвращает каждый экземпляр этого ресурса в текущей подписке.</span><span class="sxs-lookup"><span data-stu-id="cc00d-115">Every resource collection has a `List()` method to return every instance of that resource in your current subscription.</span></span> <span data-ttu-id="cc00d-116">Например, `Azure.SqlServers.List()` возвращает все серверы SQL в подписке.</span><span class="sxs-lookup"><span data-stu-id="cc00d-116">For example, `Azure.SqlServers.List()` returns all SQL servers in the subscription.</span></span>

<span data-ttu-id="cc00d-117">Используйте метод `ListByResourceGroup()`, чтобы ограничить возвращаемый список определенной [группой ресурсов Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups).</span><span class="sxs-lookup"><span data-stu-id="cc00d-117">Use the `ListByResourceGroup()` method to scope the returned List to a specific [Azure resource group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups).</span></span>  

<span data-ttu-id="cc00d-118">Выполните итерацию для возвращенной коллекции так же, как для обычного списка `List<T>`:</span><span class="sxs-lookup"><span data-stu-id="cc00d-118">Iterate over the returned collection just as you would a normal `List<T>`:</span></span>

```csharp
var vmList = azure.VirtualMachines.List();
foreach(var vm in vmList)
{
    Console.WriteLine("VM Name: {0}", vm.Name);
}
```   

## <a name="actionable-verbs"></a><span data-ttu-id="cc00d-119">Готовые к работе команды</span><span class="sxs-lookup"><span data-stu-id="cc00d-119">Actionable verbs</span></span>

<span data-ttu-id="cc00d-120">Методы коллекции ресурсов с командами в именах выполняются в Azure немедленно.</span><span class="sxs-lookup"><span data-stu-id="cc00d-120">Resource collection methods with verbs in their names take immediate action in Azure.</span></span> <span data-ttu-id="cc00d-121">Эти методы работают синхронно. Пока они не будут завершены, выполнение в текущем потоке блокируется.</span><span class="sxs-lookup"><span data-stu-id="cc00d-121">These methods work synchronously and block execution in the current thread until they complete.</span></span> 

| <span data-ttu-id="cc00d-122">Команда</span><span class="sxs-lookup"><span data-stu-id="cc00d-122">Verb</span></span>   |  <span data-ttu-id="cc00d-123">Пример использования</span><span class="sxs-lookup"><span data-stu-id="cc00d-123">Sample usage</span></span> |
|--------|---------------|
| <span data-ttu-id="cc00d-124">Создание</span><span class="sxs-lookup"><span data-stu-id="cc00d-124">Create</span></span> | `azure.VirtualMachines.Create(listOfVMCreatables)` |
| <span data-ttu-id="cc00d-125">Применить</span><span class="sxs-lookup"><span data-stu-id="cc00d-125">Apply</span></span>  | `virtualMachineScaleSet.Update().WithCapacity(6).Apply()` |
| <span data-ttu-id="cc00d-126">Delete</span><span class="sxs-lookup"><span data-stu-id="cc00d-126">Delete</span></span> | `azure.Disks.DeleteById(id)` | 
| <span data-ttu-id="cc00d-127">список</span><span class="sxs-lookup"><span data-stu-id="cc00d-127">List</span></span>   | `azure.SqlServers.List()` | 
| <span data-ttu-id="cc00d-128">Получить</span><span class="sxs-lookup"><span data-stu-id="cc00d-128">Get</span></span>    | `var vm  = azure.VirtualMachines.GetByResourceGroup(group, vmName)` |

>[!NOTE]
> <span data-ttu-id="cc00d-129">`Define()` и `Update()` являются командами, но они не блокируют выполнение, если не сопровождаются `Create()` или `Apply()`.</span><span class="sxs-lookup"><span data-stu-id="cc00d-129">`Define()` and `Update()` are verbs but do not block unless followed by a `Create()` or `Apply()`.</span></span>
 
<span data-ttu-id="cc00d-130">Определенные объекты ресурсов содержат команды, которые изменяют состояние ресурса в Azure.</span><span class="sxs-lookup"><span data-stu-id="cc00d-130">Specific resource objects have verbs that change the state of the resource in Azure.</span></span> <span data-ttu-id="cc00d-131">Например: </span><span class="sxs-lookup"><span data-stu-id="cc00d-131">For example:</span></span>

```csharp
var vmToRestart = azure.VirtualMachines.GetById(id);
vmToRestart.Restart();
```

<span data-ttu-id="cc00d-132">Большинство методов, описанных в этом разделе, имеют также асинхронную версию, которая обозначается суффиксом `Async`.</span><span class="sxs-lookup"><span data-stu-id="cc00d-132">Most of the methods described in this section have an asynchronous version as well, denoted by the suffix `Async`.</span></span>

```csharp
Task restartTask = azure.VirtualMachines.GetById(id).RestartAsync();
```

## <a name="lazy-resource-creation"></a><span data-ttu-id="cc00d-133">Создание отложенных ресурсов</span><span class="sxs-lookup"><span data-stu-id="cc00d-133">Lazy resource creation</span></span>

<span data-ttu-id="cc00d-134">При создании ресурсов Azure возникает проблемная ситуация, когда новый ресурс зависит от другого ресурса, который еще не существует.</span><span class="sxs-lookup"><span data-stu-id="cc00d-134">A challenge when creating Azure resources arises when a new resource depends on another resource that doesn't yet exist.</span></span> <span data-ttu-id="cc00d-135">Пример — резервирование общедоступного IP-адреса и настройка диска при создании виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="cc00d-135">An example is reserving a public IP address and setting up a disk when creating a new virtual machine.</span></span> <span data-ttu-id="cc00d-136">Предположим, вам не нужно проверять резервирование адреса или создание диска — вы просто хотите настроить виртуальную машину с этими ресурсами.</span><span class="sxs-lookup"><span data-stu-id="cc00d-136">You don't want to verify reserving the address or the creating the disk, you just want to configure the virtual machine with those resources.</span></span>

<span data-ttu-id="cc00d-137">Используйте создаваемые объекты, чтобы определить ресурсы Azure для использования в коде. Но создавайте их, только если они нужны вам в Azure.</span><span class="sxs-lookup"><span data-stu-id="cc00d-137">Use creatable objects to define Azure resources for use in your code but only create them when needed in Azure.</span></span> <span data-ttu-id="cc00d-138">Код, написанный с использованием создаваемых объектов, перенаправляет нагрузку создания ресурсов в среде Azure в API управления, что повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="cc00d-138">Code written with creatable objects offloads resource creation in the Azure environment to the management API, boosting performance.</span></span> 

<span data-ttu-id="cc00d-139">Получить создаваемые объекты можно с помощью команды `Define()` коллекций ресурсов без команды `Create()`:</span><span class="sxs-lookup"><span data-stu-id="cc00d-139">Generate creatable objects through the resource collections' `Define()` verb without a `Create()` verb:</span></span>

```csharp
// Init a creatable Public IP Address
var publicIpAddressCreatable = azure.PublicIPAddresses.Define("publicIPAddressName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName);
```

<span data-ttu-id="cc00d-140">Ресурс Azure, определенный создаваемым объектом, еще не существует в вашей подписке.</span><span class="sxs-lookup"><span data-stu-id="cc00d-140">The Azure resource defined by the creatable object does not yet exist in your subscription.</span></span> <span data-ttu-id="cc00d-141">Создаваемый объект — это локальное представление ресурса, которое при необходимости создает API управления (при вызове `.Create()`).</span><span class="sxs-lookup"><span data-stu-id="cc00d-141">A creatable object is a local representation of a resource that the management API will create when it's needed (when `.Create()` is called).</span></span> <span data-ttu-id="cc00d-142">Используйте этот создаваемый объект в определении других ресурсов Azure, которым требуется этот ресурс.</span><span class="sxs-lookup"><span data-stu-id="cc00d-142">Use this creatable object in the definition of other Azure resources that need this resource.</span></span> 

```csharp
// Init a creatable VM using the creatable Public IP Address
var vmCreatable = azure.VirtualMachines.Define("creatableVM")
    // ...
    .withNewPrimaryPublicIPAddress(publicIPAddressCreatable)
    // ...
```

<span data-ttu-id="cc00d-143">Создайте ресурсы в подписке Azure с помощью метода `Create()` для коллекции ресурсов.</span><span class="sxs-lookup"><span data-stu-id="cc00d-143">Create the resources in your Azure subscription using the `Create()` method for the resource collection.</span></span> 

```csharp
// Create the VM and its Public IP Address
var virtualMachine = azure.VirtualMachines.Create(vmCreatable);
```

<span data-ttu-id="cc00d-144">Передача создаваемых объектов в `Create()` возвращает объект `ICreatedResources` вместо объекта с одним ресурсом.</span><span class="sxs-lookup"><span data-stu-id="cc00d-144">Passing creatable objects to `Create()` returns a `ICreatedResources` object instead of a single resource object.</span></span>  <span data-ttu-id="cc00d-145">Объект `CreatedRelatedResource` обеспечивает доступ ко всем ресурсам, созданным вызовом `Create()`, а не только к типу из коллекции ресурсов.</span><span class="sxs-lookup"><span data-stu-id="cc00d-145">The `CreatedRelatedResource` object lets you access all resources created by the `Create()` call, not just the type from the resource collection.</span></span> <span data-ttu-id="cc00d-146">Доступ к общедоступному IP-адресу, созданному в Azure для виртуальной машины, которая создается в примере выше:</span><span class="sxs-lookup"><span data-stu-id="cc00d-146">To access the public IP address created in Azure for the virtual machine created in the above example:</span></span>

```csharp
var pip = virtualMachine.CreatedRelatedResource(publicIPAddressCreatable.Key()) as PublicIPAddress;;
```    

## <a name="exception-handling"></a><span data-ttu-id="cc00d-147">Обработка исключений</span><span class="sxs-lookup"><span data-stu-id="cc00d-147">Exception handling</span></span>

<span data-ttu-id="cc00d-148">API управления определяет классы исключений, которые расширяют `Microsoft.Rest.RestException`.</span><span class="sxs-lookup"><span data-stu-id="cc00d-148">The management API defines exception classes that extend `Microsoft.Rest.RestException`.</span></span> <span data-ttu-id="cc00d-149">Перехват исключений, создаваемых API управления, выполняется с помощью блока `catch (RestException exception)` после соответствующей инструкции `try`.</span><span class="sxs-lookup"><span data-stu-id="cc00d-149">Catch exceptions generated by management API, with a `catch (RestException exception)` block after the relevant `try` statement.</span></span>

## <a name="logs-and-tracing"></a><span data-ttu-id="cc00d-150">Журналы и трассировка</span><span class="sxs-lookup"><span data-stu-id="cc00d-150">Logs and tracing</span></span>

<span data-ttu-id="cc00d-151">Для ведения журналов в текучих библиотеках управления Azure для .NET используется базовая трассировка клиентской службы [AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="cc00d-151">Logging in the fluent Azure management libraries for .NET leverages the underlying [AutoRest](https://github.com/Azure/AutoRest) service client tracing.</span></span>

<span data-ttu-id="cc00d-152">Создайте класс, реализующий перехватчик `Microsoft.Rest.IServiceClientTracingInterceptor`.</span><span class="sxs-lookup"><span data-stu-id="cc00d-152">Create a class that implements `Microsoft.Rest.IServiceClientTracingInterceptor`.</span></span>  <span data-ttu-id="cc00d-153">Этот класс будет отвечать за перехват сообщений журнала и их передачу в любое используемое средство ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="cc00d-153">This class will be responsible for intercepting log messages and passing them to whatever logging mechanism you're using.</span></span>  <span data-ttu-id="cc00d-154">В этом примере мы просто записываем сообщения в консоль, но их также можно передать в Log4Net, `Microsoft.Extensions.Logging` или любую другую платформу ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="cc00d-154">In this example, we're just writing messages to the console, but you could also pass them to Log4Net, `Microsoft.Extensions.Logging`, or any other logging framework.</span></span>

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

<span data-ttu-id="cc00d-155">Перед созданием объекта `Microsoft.Azure.Management.Fluent.Azure` инициализируйте перехватчик `IServiceClientTracingInterceptor`, созданный выше с помощью вызова `ServiceClientTracing.AddTracingInterceptor()`, и задайте для параметра `ServiceClientTracing.IsEnabled` значение *true*.</span><span class="sxs-lookup"><span data-stu-id="cc00d-155">Before creating the `Microsoft.Azure.Management.Fluent.Azure` object, initialize the `IServiceClientTracingInterceptor` you created above by calling `ServiceClientTracing.AddTracingInterceptor()` and set `ServiceClientTracing.IsEnabled` to *true*.</span></span>  <span data-ttu-id="cc00d-156">При создании объекта `Azure` включите методы `.WithDelegatingHandler()` и `.WithLogLevel()`, чтобы подключить клиент к трассировке клиентской службы AutoRest.</span><span class="sxs-lookup"><span data-stu-id="cc00d-156">When you create the `Azure` object, include the `.WithDelegatingHandler()` and `.WithLogLevel()` methods to wire up the client to AutoRest's service client tracing.</span></span>

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

<span data-ttu-id="cc00d-157">Уровни журнала `HttpLoggingDelegatingHandler` определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cc00d-157">The `HttpLoggingDelegatingHandler` log levels are defined as follows:</span></span>

| <span data-ttu-id="cc00d-158">Уровень трассировки</span><span class="sxs-lookup"><span data-stu-id="cc00d-158">Trace level</span></span> | <span data-ttu-id="cc00d-159">Ведение журнала включено</span><span class="sxs-lookup"><span data-stu-id="cc00d-159">Logging enabled</span></span> 
| ------------ | ---------------
| <span data-ttu-id="cc00d-160">HttpLoggingDelegatingHandler.Level.None</span><span class="sxs-lookup"><span data-stu-id="cc00d-160">HttpLoggingDelegatingHandler.Level.None</span></span> | <span data-ttu-id="cc00d-161">Нет выходных данных.</span><span class="sxs-lookup"><span data-stu-id="cc00d-161">No output</span></span>
| <span data-ttu-id="cc00d-162">HttpLoggingDelegatingHandler.Level.Basic</span><span class="sxs-lookup"><span data-stu-id="cc00d-162">HttpLoggingDelegatingHandler.Level.Basic</span></span> | <span data-ttu-id="cc00d-163">Регистрация URL-адресов для базовых вызовов REST, кодов и времени ответов.</span><span class="sxs-lookup"><span data-stu-id="cc00d-163">Logs the URLs to underlying REST calls, response codes and times</span></span>
| <span data-ttu-id="cc00d-164">HttpLoggingDelegatingHandler.Level.Body</span><span class="sxs-lookup"><span data-stu-id="cc00d-164">HttpLoggingDelegatingHandler.Level.Body</span></span> | <span data-ttu-id="cc00d-165">Регистрация тех же элементов, что и для уровня Basic, а также текста запросов и ответов для вызовов REST.</span><span class="sxs-lookup"><span data-stu-id="cc00d-165">Everything in Basic plus request and response bodies for the REST calls</span></span>
| <span data-ttu-id="cc00d-166">HttpLoggingDelegatingHandler.Level.Headers</span><span class="sxs-lookup"><span data-stu-id="cc00d-166">HttpLoggingDelegatingHandler.Level.Headers</span></span> | <span data-ttu-id="cc00d-167">Регистрация тех же элементов, что и для уровня Basic, а также заголовков запросов и ответов для вызовов REST.</span><span class="sxs-lookup"><span data-stu-id="cc00d-167">Everything in Basic plus the request and response headers REST calls</span></span>
| <span data-ttu-id="cc00d-168">HttpLoggingDelegatingHandler.Level.BodyAndHeaders</span><span class="sxs-lookup"><span data-stu-id="cc00d-168">HttpLoggingDelegatingHandler.Level.BodyAndHeaders</span></span> | <span data-ttu-id="cc00d-169">Регистрация тех же элементов, что и для уровней журнала BODY и HEADERS в совокупности.</span><span class="sxs-lookup"><span data-stu-id="cc00d-169">Everything in both Body and Headers log level</span></span>
