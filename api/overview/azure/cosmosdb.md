---
title: Библиотеки Azure Cosmos DB для .NET
description: Справочник по библиотекам Azure Cosmos DB для .NET
keywords: Azure, .NET, пакет SDK, API, Cosmos DB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 08/31/2018
ms.topic: reference
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 4928c1dfdb7a5bb50ca4f5023cbfec71e05e9061
ms.sourcegitcommit: 299aa7bdbb9cec1b56e42e25550999e53e23de2c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43839500"
---
# <a name="azure-cosmos-db-libraries-for-net"></a>Библиотеки Azure Cosmos DB для .NET

## <a name="overview"></a>Обзор

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) — это многомодельная глобально распределенная служба баз данных. Она позволяет эластично и независимо масштабировать пропускную способность и ресурсы хранилища в любом количестве географических регионов в рамках всестороннего соглашения об уровне обслуживания. Благодаря Azure Cosmos DB можно хранить и использовать базы данных документов, пар "ключ — значение", базы данных с широкими столбцами и базы данных графов при помощи API-интерфейсов и моделей программирования. 

[Начало работы с Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)

## <a name="client-library"></a>Клиентская библиотека

Клиентская библиотека Azure Cosmos DB для .NET используется для доступа к данным и их хранения в существующем хранилище данных Azure Cosmos DB. Автоматически создать учетную запись Azure Cosmos DB можно с помощью портала Azure, интерфейса командной строки или PowerShell.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a>Пример кода

В этом примере устанавливается подключение к существующей базе данных API SQL в Azure Cosmos DB, считывается документ из коллекции, который затем десериализируется как объект `Item`.   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>Примеры

* [Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/) (Разработка приложения .NET с помощью API MongoDB Cosmos DB)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) примеров для Azure Cosmos DB.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
