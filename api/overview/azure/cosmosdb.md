---
title: Библиотеки Azure Cosmos DB для .NET
description: Справочник по библиотекам Azure Cosmos DB для .NET
ms.date: 08/31/2018
ms.topic: reference
ms.service: cosmos-db
ms.openlocfilehash: 21a2f2168259528a0d27103783e34aa532d7e17a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190804"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="9eccc-103">Библиотеки Azure Cosmos DB для .NET</span><span class="sxs-lookup"><span data-stu-id="9eccc-103">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9eccc-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="9eccc-104">Overview</span></span>

<span data-ttu-id="9eccc-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) — это многомодельная глобально распределенная служба баз данных.</span><span class="sxs-lookup"><span data-stu-id="9eccc-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a globally distributed, multi-model database service.</span></span> <span data-ttu-id="9eccc-106">Она позволяет эластично и независимо масштабировать пропускную способность и ресурсы хранилища в любом количестве географических регионов в рамках всестороннего соглашения об уровне обслуживания.</span><span class="sxs-lookup"><span data-stu-id="9eccc-106">It is designed to elastically and independently scale throughput and storage across any number of geographical regions with a comprehensive SLA.</span></span> <span data-ttu-id="9eccc-107">Благодаря Azure Cosmos DB можно хранить и использовать базы данных документов, пар "ключ — значение", базы данных с широкими столбцами и базы данных графов при помощи API-интерфейсов и моделей программирования.</span><span class="sxs-lookup"><span data-stu-id="9eccc-107">With Azure Cosmos DB, you can store and access document, key-value, wide-column, and graph databases by using APIs and programming models.</span></span> 

<span data-ttu-id="9eccc-108">[Начало работы с Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)</span><span class="sxs-lookup"><span data-stu-id="9eccc-108">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="9eccc-109">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="9eccc-109">Client library</span></span>

<span data-ttu-id="9eccc-110">Клиентская библиотека Azure Cosmos DB для .NET используется для доступа к данным и их хранения в существующем хранилище данных Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="9eccc-110">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span> <span data-ttu-id="9eccc-111">Автоматически создать учетную запись Azure Cosmos DB можно с помощью портала Azure, интерфейса командной строки или PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9eccc-111">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="9eccc-112">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9eccc-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9eccc-113">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9eccc-113">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="9eccc-114">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9eccc-114">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="9eccc-115">Пример кода</span><span class="sxs-lookup"><span data-stu-id="9eccc-115">Code Example</span></span>

<span data-ttu-id="9eccc-116">В этом примере устанавливается подключение к существующей базе данных API SQL в Azure Cosmos DB, считывается документ из коллекции, который затем десериализируется как объект `Item`.</span><span class="sxs-lookup"><span data-stu-id="9eccc-116">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9eccc-117">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="9eccc-117">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="9eccc-118">Примеры</span><span class="sxs-lookup"><span data-stu-id="9eccc-118">Samples</span></span>

* <span data-ttu-id="9eccc-119">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/) (Разработка приложения .NET с помощью API MongoDB Cosmos DB)</span><span class="sxs-lookup"><span data-stu-id="9eccc-119">[Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)</span></span>

<span data-ttu-id="9eccc-120">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) примеров для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="9eccc-120">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
