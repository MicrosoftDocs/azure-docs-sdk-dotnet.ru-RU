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
# <a name="azure-database-for-postgresql-libraries-for-net"></a><span data-ttu-id="884b2-104">База данных Azure для библиотек PostgreSQL для .NET</span><span class="sxs-lookup"><span data-stu-id="884b2-104">Azure Database for PostgreSQL libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="884b2-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="884b2-105">Overview</span></span>

<span data-ttu-id="884b2-106">Работа с данными и ресурсами, хранящимися в [базе данных Azure для PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span><span class="sxs-lookup"><span data-stu-id="884b2-106">Work with data and resources stored in [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span></span>

## <a name="client-api"></a><span data-ttu-id="884b2-107">API клиента</span><span class="sxs-lookup"><span data-stu-id="884b2-107">Client API</span></span>

<span data-ttu-id="884b2-108">Рекомендуемая клиентская библиотека для доступа к базе данных Azure для PostgreSQL — это [поставщик данных с открытым кодом Npgsql ADO.NET](http://www.npgsql.org/).</span><span class="sxs-lookup"><span data-stu-id="884b2-108">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Npgsql ADO.NET data provider](http://www.npgsql.org/).</span></span> <span data-ttu-id="884b2-109">Используйте поставщик ADO.NET для подключения к базе данных и выполнения инструкций SQL непосредственно или через Entity Framework с поставщиками Npgsql [Entity Framework 6](http://www.npgsql.org/ef6/index.html) или [Entity Framework Core](http://www.npgsql.org/efcore/index.html).</span><span class="sxs-lookup"><span data-stu-id="884b2-109">Use the ADO.NET provider to connect to the database and execute SQL statements directly or through Entity Framework with the Npgsql's [Entity Framework 6](http://www.npgsql.org/ef6/index.html) or [Entity Framework Core](http://www.npgsql.org/efcore/index.html) providers.</span></span>

<span data-ttu-id="884b2-110">Установите [пакет NuGet](https://www.nuget.org/packages/Npgsql) непосредственно из [консоли диспетчера пакетов][PackageManager] или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="884b2-110">Install the [NuGet package](https://www.nuget.org/packages/Npgsql) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="884b2-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="884b2-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Npgsql
```

#### <a name="net-core-cli"></a><span data-ttu-id="884b2-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="884b2-112">.NET Core CLI</span></span>

```bash
dotnet add package Npgsql
```

### <a name="code-example"></a><span data-ttu-id="884b2-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="884b2-113">Code Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="884b2-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="884b2-114">Samples</span></span>

- <span data-ttu-id="884b2-115">[ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples) (Примеры кода ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="884b2-115">[ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples)</span></span>
- <span data-ttu-id="884b2-116">[Проектирование первой базы данных Azure для PostgreSQL с помощью Azure CLI](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli) [PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console [DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package</span><span class="sxs-lookup"><span data-stu-id="884b2-116">[Design a PostgreSQL database using the Azure CLI](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli) [PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console [DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package</span></span>