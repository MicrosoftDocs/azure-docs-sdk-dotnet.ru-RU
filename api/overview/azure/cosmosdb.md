---
title: Библиотеки Azure Cosmos DB для .NET
description: Справочник по библиотекам Azure Cosmos DB для .NET
keywords: Azure, .NET, пакет SDK, API, Cosmos DB
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
ms.openlocfilehash: fa9bc7497ac189f18ee0ba14d72d4cdb23a05f0b
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2018
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="de317-104">Библиотеки Azure Cosmos DB для .NET</span><span class="sxs-lookup"><span data-stu-id="de317-104">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="de317-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="de317-105">Overview</span></span>

<span data-ttu-id="de317-106">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) — это распределенное и масштабируемое хранилище данных, которое поддерживает несколько типов баз данных.</span><span class="sxs-lookup"><span data-stu-id="de317-106">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

<span data-ttu-id="de317-107">[Начало работы с Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)</span><span class="sxs-lookup"><span data-stu-id="de317-107">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="de317-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="de317-108">Client library</span></span>

<span data-ttu-id="de317-109">Клиентская библиотека Azure Cosmos DB для .NET используется для доступа к данным и их хранения в существующем хранилище данных Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="de317-109">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span>  <span data-ttu-id="de317-110">Автоматически создать учетную запись Azure Cosmos DB можно с помощью портала Azure, интерфейса командной строки или PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de317-110">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="de317-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="de317-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="de317-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de317-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="de317-113">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="de317-113">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="de317-114">Пример кода</span><span class="sxs-lookup"><span data-stu-id="de317-114">Code Example</span></span>

<span data-ttu-id="de317-115">В этом примере устанавливается подключение к существующей базе данных API SQL в Azure Cosmos DB, считывается документ из коллекции, который затем десериализируется как объект `Item`.</span><span class="sxs-lookup"><span data-stu-id="de317-115">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="de317-116">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="de317-116">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="de317-117">Примеры</span><span class="sxs-lookup"><span data-stu-id="de317-117">Samples</span></span>

* <span data-ttu-id="de317-118">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/) (Разработка приложения .NET с помощью API MongoDB Cosmos DB)</span><span class="sxs-lookup"><span data-stu-id="de317-118">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)</span></span>

<span data-ttu-id="de317-119">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) примеров для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="de317-119">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
