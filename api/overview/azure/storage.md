---
title: API-интерфейсы хранилища Azure для .NET
description: Справочник по библиотекам службы хранилища Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: storage
ms.openlocfilehash: 2f278f0e3cb10d11190d529f427fa64040ee8b1d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189977"
---
# <a name="azure-storage-apis-for-net"></a><span data-ttu-id="26948-103">API-интерфейсы хранилища Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="26948-103">Azure Storage APIs for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="26948-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="26948-104">Overview</span></span>

<span data-ttu-id="26948-105">Выполняйте чтение и запись файлов, данных блочных BLOB-объектов, пар "ключ-значение" и сообщений в приложениях .NET с помощью [службы хранилища Azure](https://docs.microsoft.com/azure/storage/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="26948-105">Read and write files, blob (object) data, key-value pairs, and messages from your .NET applications with [Azure Storage](https://docs.microsoft.com/azure/storage/storage-introduction).</span></span>

<span data-ttu-id="26948-106">Чтобы начать работу со службой хранилища Azure см. статью [Приступая к работе с хранилищем BLOB-объектов Azure с помощью .NET](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="26948-106">To get started with Azure Storage, see [Get started with Azure Blob storage using .NET](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="client-library"></a><span data-ttu-id="26948-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="26948-107">Client library</span></span>

<span data-ttu-id="26948-108">Подключитесь к учетной записи хранения Azure с помощью [строк подключения](/azure/storage/storage-create-storage-account#manage-your-storage-account), а затем используйте классы и методы клиентских библиотек для работы с хранилищем BLOB-объектов, таблиц, файлов и очередей.</span><span class="sxs-lookup"><span data-stu-id="26948-108">Use [connection strings](/azure/storage/storage-create-storage-account#manage-your-storage-account) to connect to an Azure Storage account, then use the client libraries' classes and methods to work with blob, table, file, or queue storage.</span></span>

<span data-ttu-id="26948-109">Установите [пакет NuGet](https://www.nuget.org/packages/WindowsAzure.Storage) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="26948-109">Install the [NuGet package](https://www.nuget.org/packages/WindowsAzure.Storage) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="26948-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26948-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package WindowsAzure.Storage
```

### <a name="net-core-cli"></a><span data-ttu-id="26948-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="26948-111">.NET Core CLI</span></span>

```bash
dotnet add package WindowsAzure.Storage
```

### <a name="code-example"></a><span data-ttu-id="26948-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="26948-112">Code Example</span></span>

<span data-ttu-id="26948-113">В этом примере в новом контейнере существующей учетной записи хранения создается большой двоичный объект.</span><span class="sxs-lookup"><span data-stu-id="26948-113">This example creates a new blob to a new container in an existing storage account.</span></span>

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
> [<span data-ttu-id="26948-114">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="26948-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/storage/client)

## <a name="management-apis"></a><span data-ttu-id="26948-115">API управления</span><span class="sxs-lookup"><span data-stu-id="26948-115">Management APIs</span></span>

<span data-ttu-id="26948-116">Создавайте учетные записи хранения Azure и ключи подключения и управляйте ими с помощью API управления.</span><span class="sxs-lookup"><span data-stu-id="26948-116">Create and manage Azure Storage accounts and connection keys with the management API.</span></span>

<span data-ttu-id="26948-117">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="26948-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="26948-118">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26948-118">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Storage.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="26948-119">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="26948-119">.NET Core CLI</span></span>

````bash
dotnet add package Microsoft.Azure.Management.Storage.Fluent
````

### <a name="code-example"></a><span data-ttu-id="26948-120">Пример кода</span><span class="sxs-lookup"><span data-stu-id="26948-120">Code Example</span></span>

<span data-ttu-id="26948-121">В этом примере создается учетная запись хранения.</span><span class="sxs-lookup"><span data-stu-id="26948-121">This example creates a storage account.</span></span>

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
> [<span data-ttu-id="26948-122">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="26948-122">Explore the management APIs</span></span>](/dotnet/api/overview/azure/storage/management)

## <a name="samples"></a><span data-ttu-id="26948-123">Примеры</span><span class="sxs-lookup"><span data-stu-id="26948-123">Samples</span></span>

* <span data-ttu-id="26948-124">[Azure Blob Storage Samples for .NET](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/) (Примеры для хранилища BLOB-объектов Azure для .NET)</span><span class="sxs-lookup"><span data-stu-id="26948-124">[Get started with Azure Blob Storage in .NET](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)</span></span> 
* <span data-ttu-id="26948-125">[Getting Started with Azure Queue Service in .NET](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/) (Начало работы со службой очередей Azure в .NET)</span><span class="sxs-lookup"><span data-stu-id="26948-125">[Get started with Azure Queue Storage in .NET](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/)</span></span>

<span data-ttu-id="26948-126">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) примеров для службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="26948-126">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) of Azure Storage samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package