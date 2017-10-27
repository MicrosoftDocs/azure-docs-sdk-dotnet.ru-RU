---
title: "База данных Azure для библиотек PostgreSQL для .NET"
description: "Справочная документация по библиотекам клиента .NET для базы данных Azure для PostgreSQL"
keywords: Azure, .NET ODBC, SDK, API, SQL, ADO.NET, database, PostGres, PostgreSQL
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: postgresql
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e3153a35845a2d7660aded64e5dbc3787c62afb6
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
---
# <a name="azure-database-for-postgresql-libraries-for-net"></a>База данных Azure для библиотек PostgreSQL для .NET

## <a name="overview"></a>Обзор

Работа с данными и ресурсами, хранящимися в [базе данных Azure для PostgreSQL](https://docs.microsoft.com/azure/postgresql/).

## <a name="client-api"></a>API клиента

Рекомендуемая клиентская библиотека для доступа к базе данных Azure для PostgreSQL — это [поставщик данных с открытым кодом Npgsql ADO.NET](http://www.npgsql.org/). Используйте поставщик ADO.NET для подключения к базе данных и выполнения инструкций SQL непосредственно или через Entity Framework с поставщиками Npgsql [Entity Framework 6](http://www.npgsql.org/ef6/index.html) или [Entity Framework Core](http://www.npgsql.org/efcore/index.html).

Установите [пакет NuGet](https://www.nuget.org/packages/Npgsql) непосредственно из [консоли диспетчера пакетов][PackageManager] или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Npgsql
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Npgsql
```

### <a name="code-example"></a>Пример кода

```csharp
/* Include this 'using' directive...
using Npgsql;
*/

// Always store connection strings securely. 
string connectionString = "Server=[servername].postgres.database.azure.com; " +
    "Port=5432; Database=myDataBase; User Id=[userid]@[servername]; Password=password;";

// Best practice is to scope the NpgsqlConnection to a "using" block
using (NpgsqlConnection conn = new NpgsqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    NpgsqlCommand selectCommand = new NpgsqlCommand("SELECT * FROM MyTable", conn);
    NpgsqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

### <a name="samples"></a>Примеры

- [ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples) (Примеры кода ADO.NET)
- [Проектирование первой базы данных Azure для PostgreSQL с помощью Azure CLI](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli) [PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console [DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package