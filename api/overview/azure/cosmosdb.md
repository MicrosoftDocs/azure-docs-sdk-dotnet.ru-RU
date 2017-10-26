---
title: "Библиотеки Azure CosmosDB для .NET"
description: "Справочник по библиотекам Azure CosmosDB для .NET"
keywords: Azure, .NET, SDK, API, CosmosDB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 890c00caeca06bf863425c7159d7833c4db8df38
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a><span data-ttu-id="54eac-104">Библиотеки Azure CosmosDB для .NET</span><span class="sxs-lookup"><span data-stu-id="54eac-104">Azure CosmosDB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="54eac-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="54eac-105">Overview</span></span>

<span data-ttu-id="54eac-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) — это распределенное и масштабируемое хранилище данных, которое поддерживает несколько типов баз данных.</span><span class="sxs-lookup"><span data-stu-id="54eac-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

## <a name="client-library"></a><span data-ttu-id="54eac-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="54eac-107">Client library</span></span>

<span data-ttu-id="54eac-108">Клиентская библиотека CosmosDB .NET используется для осуществления доступа к данным и их хранения в хранилище CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="54eac-108">Use the CosmosDB .NET client library to access and store data in a CosmosDB data store.</span></span>

<span data-ttu-id="54eac-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="54eac-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="54eac-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="54eac-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="54eac-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="54eac-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="54eac-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="54eac-112">Code Example</span></span>

<span data-ttu-id="54eac-113">В этом примере устанавливается подключение к существующей базе данных API DocumentDB в CosmosDB, затем документ из коллекции считывается и десериализируется как объект `Item`.</span><span class="sxs-lookup"><span data-stu-id="54eac-113">This example connects to an existing CosmosDB DocumentDB API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
// "Item" is a class defined elsewhere...
Item item = client.ReadDocumentAsync<Item>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="54eac-114">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="54eac-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="54eac-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="54eac-115">Samples</span></span>

* <span data-ttu-id="54eac-116">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/) (Разработка приложения .NET с помощью API MongoDB Cosmos DB)</span><span class="sxs-lookup"><span data-stu-id="54eac-116">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)</span></span>

<span data-ttu-id="54eac-117">Просмотрите [полный список](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) примеров для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="54eac-117">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
