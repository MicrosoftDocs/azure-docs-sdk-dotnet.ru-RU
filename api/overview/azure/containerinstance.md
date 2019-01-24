---
title: Библиотеки службы "Экземпляры контейнеров Azure" для .NET
description: Справочник по библиотекам службы "Экземпляры контейнеров Azure" для .NET
ms.date: 06/11/2018
ms.topic: reference
ms.service: container-instances
ms.openlocfilehash: 552746b316f1ba80adce5f55bb22412749fd93bc
ms.sourcegitcommit: 4f7bc5c5cd333e41446a3ebe5639a211d8ac9b90
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54841281"
---
# <a name="azure-container-instances-libraries-for-net"></a>Библиотеки службы "Экземпляры контейнеров Azure" для .NET

Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки службы "Экземпляры контейнеров Azure" для .NET. Дополнительные сведения см. в статье [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-overview).

## <a name="management-library"></a>Библиотека управления

Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки управления.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="example-source"></a>Пример исходного кода

Чтобы просмотреть приведенные ниже примеры кода в контексте, перейдите к следующему репозиторию GitHub:

[Azure-Samples/aci-docs-sample-dotnet](https://github.com/Azure-Samples/aci-docs-sample-dotnet)

## <a name="authentication"></a>Authentication

[Аутентификация с использованием файла][sdk-auth] — самый простой способ аутентификации клиентов SDK. Во время создания экземпляра клиентского объекта [IAzure][iazure] функция файловой аутентификации анализирует файл учетных данных, после чего объект использует эти учетные данные для аутентификации в Azure. Использование аутентификации на основе файла

1. Создайте файл учетных данных с помощью [Azure CLI](/cli/azure) или [Cloud Shell](https://shell.azure.com/):

   `az ad sp create-for-rbac --sdk-auth > my.azureauth`

   Если файл учетных данных создается с помощью [Cloud Shell](https://shell.azure.com/), скопируйте содержимое этого файла в локальный файл, к которому у приложения .NET есть доступ.

2. Задайте для переменной среды `AZURE_AUTH_LOCATION` полный путь к созданному файлу учетных данных. Например (оболочка Bash):

   ```bash
   export AZURE_AUTH_LOCATION=/home/yourusername/my.azureauth
   ```

Создав файл учетных данных и указав значение для переменной среды `AZURE_AUTH_LOCATION`, инициализируйте клиентский объект [IAzure][iazure] с помощью метода [Azure.Authenticate][iazure-authenticate]. В примере проекта сначала получается значение `AZURE_AUTH_LOCATION`, а затем вызывается метод, возвращающий инициализированный клиентский объект `IAzure`.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]

Этот метод из примера приложения возвращает инициализированный экземпляр [IAzure][iazure], который затем передается в первом параметре во все другие методы в примере.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]

Дополнительные сведения о доступных способах аутентификации в библиотеках управления .NET для Azure см. в [этой статье][sdk-auth].

## <a name="create-container-group---single-container"></a>Создание группы контейнеров с одним контейнером

В этом примере создается группа контейнеров с одним контейнером.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]

## <a name="create-container-group---multiple-containers"></a>Создание группы контейнеров с несколькими контейнерами

В этом примере создается группа контейнеров с двумя контейнерами: контейнером приложения и контейнером расширения.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]

## <a name="asynchronous-container-create-with-polling"></a>Асинхронное создание контейнера с использованием опроса

В этом примере создается группа контейнеров с одним контейнером с использованием метода асинхронного создания. Затем опрашивается служба Azure на наличие группы контейнеров и выводятся сведения о состоянии группы контейнеров, пока оно имеет значение "Running".

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]

## <a name="create-task-based-container-group"></a>Создание группы контейнеров на основе задач

В этом примере создается группа контейнеров с одним контейнером на основе задач. Для контейнера настраивается [пользовательская командная строка](/azure/container-instances/container-instances-restart-policy#command-line-override), для [политики перезапуска](/azure/container-instances/container-instances-restart-policy) устанавливается значение "Never".

Чтобы выполнить одну команду с несколькими аргументами командной строки, например `echo FOO BAR`, укажите их в качестве массива строк для метода `WithStartingCommandLines`. Например: 

`WithStartingCommandLines("echo", "FOO", "BAR")`

Если нужно использовать несколько команд (возможно) с несколькими аргументами, выполните сценарий оболочки и передайте связанные команды в виде аргумента. Например, в этом случае выполняются команды `echo` и `tail`:

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]

## <a name="list-container-groups"></a>Получение списка групп контейнеров

В этом примере выводится список групп контейнеров в группе ресурсов.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]

## <a name="get-an-existing-container-group"></a>Получение сведений о существующей группе контейнеров

В этом примере возвращаются данные определенной группы контейнеров в группе ресурсов и выводятся некоторые свойства группы контейнеров, а также их значения.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]

## <a name="delete-a-container-group"></a>Удаление группы контейнеров

В этом примере группа контейнеров удаляется из группы ресурсов.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->  
[!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]

## <a name="api-reference"></a>Справочник по API

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a>Примеры

* Исходный код для приведенных выше примеров можно найти на сайте GitHub:

  [Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]

* Дополнительные примеры кода для службы "Экземпляры контейнеров Azure":

  [Примеры кода Azure][samples]

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

<!-- LINKS - External -->
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[sdk-auth]: https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md

<!-- LINKS - Internal -->
[DotNetCLI]: /dotnet/core/tools/dotnet-add-package
[PackageManager]: /nuget/tools/package-manager-console
[iazure]: /dotnet/api/microsoft.azure.management.fluent.azure
[iazure-authenticate]: /dotnet/api/microsoft.azure.management.fluent.azure.authenticate
