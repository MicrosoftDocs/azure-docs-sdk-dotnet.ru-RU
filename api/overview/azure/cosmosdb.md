---
title: Библиотеки Azure Cosmos DB для .NET
description: Справочник по библиотекам Azure Cosmos DB для .NET
ms.date: 08/31/2018
ms.topic: reference
ms.service: cosmos-db
ms.openlocfilehash: 95fcd8468c3d472cfcadeaae3b56ae789c3b1e7a
ms.sourcegitcommit: 55ee51501678d1575e5159f0ac0e475b5bf9daf3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2019
ms.locfileid: "54453998"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="39b2d-103">Библиотеки Azure Cosmos DB для .NET</span><span class="sxs-lookup"><span data-stu-id="39b2d-103">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="39b2d-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="39b2d-104">Overview</span></span>

<span data-ttu-id="39b2d-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) — это многомодельная глобально распределенная служба баз данных.</span><span class="sxs-lookup"><span data-stu-id="39b2d-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a globally distributed, multi-model database service.</span></span> <span data-ttu-id="39b2d-106">Она позволяет эластично и независимо масштабировать пропускную способность и ресурсы хранилища в любом количестве географических регионов в рамках всестороннего соглашения об уровне обслуживания.</span><span class="sxs-lookup"><span data-stu-id="39b2d-106">It is designed to elastically and independently scale throughput and storage across any number of geographical regions with a comprehensive SLA.</span></span> <span data-ttu-id="39b2d-107">Благодаря Azure Cosmos DB можно хранить и использовать базы данных документов, пар "ключ — значение", базы данных с широкими столбцами и базы данных графов при помощи API-интерфейсов и моделей программирования.</span><span class="sxs-lookup"><span data-stu-id="39b2d-107">With Azure Cosmos DB, you can store and access document, key-value, wide-column, and graph databases by using APIs and programming models.</span></span> 

<span data-ttu-id="39b2d-108">[Начало работы с Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)</span><span class="sxs-lookup"><span data-stu-id="39b2d-108">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="39b2d-109">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="39b2d-109">Client library</span></span>

<span data-ttu-id="39b2d-110">Клиентская библиотека Azure Cosmos DB для .NET используется для доступа к данным и их хранения в существующем хранилище данных Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="39b2d-110">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span> <span data-ttu-id="39b2d-111">Автоматически создать учетную запись Azure Cosmos DB можно с помощью портала Azure, интерфейса командной строки или PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39b2d-111">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="39b2d-112">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="39b2d-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

<span data-ttu-id="39b2d-113">Для установки версии 2.x требуется следующее:</span><span class="sxs-lookup"><span data-stu-id="39b2d-113">To install version 2.x:</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="39b2d-114">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39b2d-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="39b2d-115">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="39b2d-115">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

<span data-ttu-id="39b2d-116">Для установки предварительной версии 3.0 для использования с .NET Standard:</span><span class="sxs-lookup"><span data-stu-id="39b2d-116">To install the preview of version 3.0, which targets .NET standard:</span></span> 

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="39b2d-117">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39b2d-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Cosmos -prerelease
```

#### <a name="net-core-cli"></a><span data-ttu-id="39b2d-118">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="39b2d-118">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Cosmos
```


### <a name="code-example"></a><span data-ttu-id="39b2d-119">Пример кода</span><span class="sxs-lookup"><span data-stu-id="39b2d-119">Code Example</span></span>

<span data-ttu-id="39b2d-120">В этом примере устанавливается подключение к существующей базе данных API SQL в Azure Cosmos DB, считывается документ из коллекции, который затем десериализируется как объект `TodoItem`.</span><span class="sxs-lookup"><span data-stu-id="39b2d-120">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `TodoItem` object.</span></span> <span data-ttu-id="39b2d-121">В этом примере используется версия 2.x пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="39b2d-121">This example uses version 2.x of the .NET SDK.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
var todoItem = client.ReadDocumentAsync<TodoItem>(documentUri);
```

<span data-ttu-id="39b2d-122">В этом примере устанавливается подключение к существующей базе данных API SQL в Azure Cosmos DB, создается база данных и контейнер, считывается элемент из контейнера, который затем десериализируется как объект `TodoItem`.</span><span class="sxs-lookup"><span data-stu-id="39b2d-122">This example connects to an existing Azure Cosmos DB SQL API database, creates a new database and container, reads an item from the container, and deserializes it to a `TodoItem` object.</span></span> <span data-ttu-id="39b2d-123">В этом примере используется версия 3.x пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="39b2d-123">This example uses version 3.x of the .NET SDK.</span></span>   

```csharp
using (CosmosClient cosmosClient = new CosmosClient("endpoint", "primaryKey"))
{
    // Read item from container
    CosmosItemResponse<TodoItem> todoItemResponse = await cosmosClient.Databases["DatabaseId"].Containers["ContainerId"].Items.ReadItemAsync<TodoItem>("partitionKeyValue", "ItemId");
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="39b2d-124">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="39b2d-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="39b2d-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="39b2d-125">Samples</span></span>

* [<span data-ttu-id="39b2d-126">Разработка приложения .NET с помощью API SQL Azure Cosmos DB (версия 2.x)</span><span class="sxs-lookup"><span data-stu-id="39b2d-126">Developing a .NET app using Azure Cosmos DB's SQL API (Version 2.x)</span></span>](https://github.com/Azure-Samples/documentdb-dotnet-todo-app/)
* [<span data-ttu-id="39b2d-127">Разработка приложения .NET с помощью API SQL Azure Cosmos DB (предварительная версия 3.x)</span><span class="sxs-lookup"><span data-stu-id="39b2d-127">Developing a .NET app using Azure Cosmos DB's SQL API (Version 3.x Preview)</span></span>](https://github.com/Azure-Samples/cosmos-dotnet-todo-app/)
* [<span data-ttu-id="39b2d-128">Разработка приложения .NET Core с помощью API SQL Azure Cosmos DB (предварительная версия 3.x)</span><span class="sxs-lookup"><span data-stu-id="39b2d-128">Developing a .NET Core app using Azure Cosmos DB's SQL API (Version 3.x Preview)</span></span>](https://github.com/Azure-Samples/cosmos-dotnet-core-getting-started)

<span data-ttu-id="39b2d-129">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) примеров для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="39b2d-129">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
