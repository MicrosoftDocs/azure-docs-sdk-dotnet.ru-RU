---
title: "API-интерфейсы хранилища Azure для .NET"
description: "Справочник по библиотекам службы хранилища Azure для .NET"
keywords: Azure, .NET, SDK, API, storage, blob
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 4e494952b48bfbf3b10f9af9936648634353db78
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-storage-apis-for-net"></a>API-интерфейсы хранилища Azure для .NET

## <a name="overview"></a>Обзор

Выполняйте чтение и запись файлов, данных блочных BLOB-объектов, пар "ключ-значение" и сообщений в приложениях .NET с помощью [службы хранилища Azure](https://review.docs.microsoft.com/en-us/azure/storage/storage-introduction).

Чтобы начать работу со службой хранилища Azure см. статью [Приступая к работе с хранилищем BLOB-объектов Azure с помощью .NET](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="client-library"></a>Клиентская библиотека

Подключитесь к учетной записи хранения Azure с помощью [строк подключения](/azure/storage/storage-create-storage-account#manage-your-storage-account), а затем используйте классы и методы клиентских библиотек для работы с хранилищем BLOB-объектов, таблиц, файлов и очередей.

Установите [пакет NuGet](https://www.nuget.org/packages/WindowsAzure.Storage) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package WindowsAzure.Storage
```

### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package WindowsAzure.Storage
```

### <a name="code-example"></a>Пример кода

В этом примере в новом контейнере существующей учетной записи хранения создается большой двоичный объект.

```csharp
/* Include these "using" directives...
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Blob;
*/

string storageConnectionString = "DefaultEndpointsProtocol=https;"
    + "AccountName=[Storage Account Name]"
    + ";AccountKey=[Storage Account Key]"
    + ";EndpointSuffix=core.windows.net";

CloudStorageAccount account = CloudStorageAccount.Parse(storageConnectionString);
CloudBlobClient serviceClient = account.CreateCloudBlobClient();

// Create container. Name must be lower case.
Console.WriteLine("Creating container...");
var container = serviceClient.GetContainerReference("mycontainer");
container.CreateIfNotExistsAsync().Wait();

// write a blob to the container
CloudBlockBlob blob = container.GetBlockBlobReference("helloworld.txt");
blob.UploadTextAsync("Hello, World!").Wait();
```

> [!div class="nextstepactions"]
> [Обзор API-интерфейсов клиента](/dotnet/api/overview/azure/storage/client)

## <a name="management-apis"></a>API управления

Создавайте учетные записи хранения Azure и ключи подключения и управляйте ими с помощью API управления.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Storage.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

````bash
dotnet add package Microsoft.Azure.Management.Storage.Fluent
````

### <a name="code-example"></a>Пример кода

В этом примере создается учетная запись хранения.

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Management.Storage.Fluent
*/

IStorageAccount storage = azure.StorageAccounts.Define(storageAccountName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .Create();
```

> [!div class="nextstepactions"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/storage/management)

## <a name="samples"></a>Примеры

* [Azure Blob Storage Samples for .NET](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/) (Примеры для хранилища BLOB-объектов Azure для .NET) 
* [Getting Started with Azure Queue Service in .NET](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/) (Начало работы со службой очередей Azure в .NET)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) примеров для службы хранилища Azure.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package