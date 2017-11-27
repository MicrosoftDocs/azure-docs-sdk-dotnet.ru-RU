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
# <a name="azure-cosmosdb-libraries-for-net"></a>Библиотеки Azure CosmosDB для .NET

## <a name="overview"></a>Обзор

[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) — это распределенное и масштабируемое хранилище данных, которое поддерживает несколько типов баз данных.

[Начало работы с Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-documentdb-dotnet).

## <a name="client-library"></a>Клиентская библиотека

Клиентская библиотека Cosmos DB .NET используется для осуществления доступа к данным и их хранения в существующем хранилище Cosmos DB.  Создайте учетную запись Cosmos DB автоматически с помощью портала Azure, интерфейса командной строки или PowerShell.

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

В этом примере устанавливается подключение к существующей базе данных API DocumentDB в CosmosDB, затем документ из коллекции считывается и десериализируется как объект `Item`.   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>Примеры

* [Developing a .NET app using Azure Cosmos DB's MongoDB API](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/) (Разработка приложения .NET с помощью API MongoDB Cosmos DB)

Просмотрите [полный список](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) примеров для Azure Cosmos DB.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
