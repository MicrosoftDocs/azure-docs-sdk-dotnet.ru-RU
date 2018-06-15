---
title: API-интерфейсы хранилища Azure для .NET
description: Справочник по библиотекам службы хранилища Azure для .NET
keywords: Azure, .NET, SDK, API, storage, blob
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: storage
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 8f6e0414b54698d0a1dbe3d4c074456a6ad7b7be
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
ms.locfileid: "29728355"
---
# <a name="azure-storage-apis-for-net"></a><span data-ttu-id="83c2c-104">API-интерфейсы хранилища Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="83c2c-104">Azure Storage APIs for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="83c2c-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="83c2c-105">Overview</span></span>

<span data-ttu-id="83c2c-106">Выполняйте чтение и запись файлов, данных блочных BLOB-объектов, пар "ключ-значение" и сообщений в приложениях .NET с помощью [службы хранилища Azure](https://review.docs.microsoft.com/azure/storage/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="83c2c-106">Read and write files, blob (object) data, key-value pairs, and messages from your .NET applications with [Azure Storage](https://review.docs.microsoft.com/azure/storage/storage-introduction).</span></span>

<span data-ttu-id="83c2c-107">Чтобы начать работу со службой хранилища Azure см. статью [Приступая к работе с хранилищем BLOB-объектов Azure с помощью .NET](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="83c2c-107">To get started with Azure Storage, see [Get started with Azure Blob storage using .NET](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="client-library"></a><span data-ttu-id="83c2c-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="83c2c-108">Client library</span></span>

<span data-ttu-id="83c2c-109">Подключитесь к учетной записи хранения Azure с помощью [строк подключения](/azure/storage/storage-create-storage-account#manage-your-storage-account), а затем используйте классы и методы клиентских библиотек для работы с хранилищем BLOB-объектов, таблиц, файлов и очередей.</span><span class="sxs-lookup"><span data-stu-id="83c2c-109">Use [connection strings](/azure/storage/storage-create-storage-account#manage-your-storage-account) to connect to an Azure Storage account, then use the client libraries' classes and methods to work with blob, table, file, or queue storage.</span></span>

<span data-ttu-id="83c2c-110">Установите [пакет NuGet](https://www.nuget.org/packages/WindowsAzure.Storage) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="83c2c-110">Install the [NuGet package](https://www.nuget.org/packages/WindowsAzure.Storage) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="83c2c-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83c2c-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package WindowsAzure.Storage
```

### <a name="net-core-cli"></a><span data-ttu-id="83c2c-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="83c2c-112">.NET Core CLI</span></span>

```bash
dotnet add package WindowsAzure.Storage
```

### <a name="code-example"></a><span data-ttu-id="83c2c-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="83c2c-113">Code Example</span></span>

<span data-ttu-id="83c2c-114">В этом примере в новом контейнере существующей учетной записи хранения создается большой двоичный объект.</span><span class="sxs-lookup"><span data-stu-id="83c2c-114">This example creates a new blob to a new container in an existing storage account.</span></span>

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
> [<span data-ttu-id="83c2c-115">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="83c2c-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/storage/client)

## <a name="management-apis"></a><span data-ttu-id="83c2c-116">API управления</span><span class="sxs-lookup"><span data-stu-id="83c2c-116">Management APIs</span></span>

<span data-ttu-id="83c2c-117">Создавайте учетные записи хранения Azure и ключи подключения и управляйте ими с помощью API управления.</span><span class="sxs-lookup"><span data-stu-id="83c2c-117">Create and manage Azure Storage accounts and connection keys with the management API.</span></span>

<span data-ttu-id="83c2c-118">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="83c2c-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="83c2c-119">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83c2c-119">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Storage.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="83c2c-120">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="83c2c-120">.NET Core CLI</span></span>

````bash
dotnet add package Microsoft.Azure.Management.Storage.Fluent
````

### <a name="code-example"></a><span data-ttu-id="83c2c-121">Пример кода</span><span class="sxs-lookup"><span data-stu-id="83c2c-121">Code Example</span></span>

<span data-ttu-id="83c2c-122">В этом примере создается учетная запись хранения.</span><span class="sxs-lookup"><span data-stu-id="83c2c-122">This example creates a storage account.</span></span>

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
> [<span data-ttu-id="83c2c-123">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="83c2c-123">Explore the management APIs</span></span>](/dotnet/api/overview/azure/storage/management)

## <a name="samples"></a><span data-ttu-id="83c2c-124">Примеры</span><span class="sxs-lookup"><span data-stu-id="83c2c-124">Samples</span></span>

* <span data-ttu-id="83c2c-125">[Azure Blob Storage Samples for .NET](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/) (Примеры для хранилища BLOB-объектов Azure для .NET)</span><span class="sxs-lookup"><span data-stu-id="83c2c-125">[Get started with Azure Blob Storage in .NET](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)</span></span> 
* <span data-ttu-id="83c2c-126">[Getting Started with Azure Queue Service in .NET](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/) (Начало работы со службой очередей Azure в .NET)</span><span class="sxs-lookup"><span data-stu-id="83c2c-126">[Get started with Azure Queue Storage in .NET](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/)</span></span>

<span data-ttu-id="83c2c-127">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) примеров для службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="83c2c-127">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) of Azure Storage samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package