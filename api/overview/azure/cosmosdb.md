---
title: "Библиотеки Azure CosmosDB для .NET"
description: "Справочник по библиотекам Azure CosmosDB для .NET"
keywords: Azure, .NET, SDK, API, CosmosDB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 11/17/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 9f29e53e7f202e48ade12e28f08487bbacd2833c
ms.sourcegitcommit: 9cc5f8da9e9a15ba07fd67fe8b9a2d4ee6b57c73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a><span data-ttu-id="02655-104">Библиотеки Azure CosmosDB для .NET</span><span class="sxs-lookup"><span data-stu-id="02655-104">Azure CosmosDB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="02655-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="02655-105">Overview</span></span>

<span data-ttu-id="02655-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) — это распределенное и масштабируемое хранилище данных, которое поддерживает несколько типов баз данных.</span><span class="sxs-lookup"><span data-stu-id="02655-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

<span data-ttu-id="02655-107">[Начало работы с Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-documentdb-dotnet).</span><span class="sxs-lookup"><span data-stu-id="02655-107">[Get started with CosmosDB](https://docs.microsoft.com/azure/cosmos-db/create-documentdb-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="02655-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="02655-108">Client library</span></span>

<span data-ttu-id="02655-109">Клиентская библиотека Cosmos DB .NET используется для осуществления доступа к данным и их хранения в существующем хранилище Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="02655-109">Use the CosmosDB .NET client library to access and store data in an existing CosmosDB data store.</span></span>  <span data-ttu-id="02655-110">Создайте учетную запись Cosmos DB автоматически с помощью портала Azure, интерфейса командной строки или PowerShell.</span><span class="sxs-lookup"><span data-stu-id="02655-110">To automate creation of a new CosmosDB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="02655-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="02655-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="02655-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="02655-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="02655-113">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="02655-113">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="02655-114">Пример кода</span><span class="sxs-lookup"><span data-stu-id="02655-114">Code Example</span></span>

<span data-ttu-id="02655-115">В этом примере устанавливается подключение к существующей базе данных API DocumentDB в CosmosDB, затем документ из коллекции считывается и десериализируется как объект `Item`.</span><span class="sxs-lookup"><span data-stu-id="02655-115">This example connects to an existing CosmosDB DocumentDB API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="02655-116">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="02655-116">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="02655-117">Примеры</span><span class="sxs-lookup"><span data-stu-id="02655-117">Samples</span></span>

* <span data-ttu-id="02655-118">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/) (Разработка приложения .NET с помощью API MongoDB Cosmos DB)</span><span class="sxs-lookup"><span data-stu-id="02655-118">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)</span></span>

<span data-ttu-id="02655-119">Просмотрите [полный список](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) примеров для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="02655-119">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
