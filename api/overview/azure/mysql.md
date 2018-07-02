---
title: Библиотеки базы данных Azure для MySQL для .NET
description: Справочная документация по клиентским библиотекам .NET для базы данных Azure для MySQL
keywords: Azure, .NET, SDK, API, SQL, database, MySQL
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: mysql
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 6cf9d819b437a4524c71cdb2265455ef49efaea5
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065784"
---
# <a name="azure-database-for-mysql-libraries-for-net"></a><span data-ttu-id="840ab-104">Библиотеки базы данных Azure для MySQL для .NET</span><span class="sxs-lookup"><span data-stu-id="840ab-104">Azure Database for MySQL libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="840ab-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="840ab-105">Overview</span></span>

<span data-ttu-id="840ab-106">Работа с данными и ресурсами, хранящимися в [базе данных Azure для MySQL](/azure/mysql/overview).</span><span class="sxs-lookup"><span data-stu-id="840ab-106">Work with data and resources stored in [Azure Database for MySQL](/azure/mysql/overview).</span></span>

## <a name="client-apis"></a><span data-ttu-id="840ab-107">Интерфейсы API клиента</span><span class="sxs-lookup"><span data-stu-id="840ab-107">Client APIs</span></span>

<span data-ttu-id="840ab-108">Рекомендуемой клиентской библиотекой для доступа к базе данных Azure для MySQL является MySQL [Connector/Net](https://dev.mysql.com/doc/connector-net/en).</span><span class="sxs-lookup"><span data-stu-id="840ab-108">The recommended client library for accessing Azure Database for MySQL is MySQL's [Connector/Net](https://dev.mysql.com/doc/connector-net/en).</span></span> <span data-ttu-id="840ab-109">Подключитесь к базе данных при помощи пакета и напрямую выполните инструкции SQL.</span><span class="sxs-lookup"><span data-stu-id="840ab-109">Use the package to connect to the database and execute SQL statements directly.</span></span> 

<span data-ttu-id="840ab-110">Установите [пакет NuGet](https://www.nuget.org/packages/MySql.Data) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="840ab-110">Install the [NuGet package](https://www.nuget.org/packages/MySql.Data) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="840ab-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="840ab-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package MySql.Data
```

#### <a name="net-core-cli"></a><span data-ttu-id="840ab-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="840ab-112">.NET Core CLI</span></span>

```bash
dotnet add package MySql.Data
```

### <a name="code-example"></a><span data-ttu-id="840ab-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="840ab-113">Code Example</span></span>

<span data-ttu-id="840ab-114">Подключение к базе данных MySQL и выполнение запроса:</span><span class="sxs-lookup"><span data-stu-id="840ab-114">Connect to a MySQL database and execute a query:</span></span>

```csharp
/* Include this "using" directive...
using MySql.Data.MySqlClient;
*/

string connectionString = "Server=[servername].mysql.database.azure.com; " +
    "Database=myDataBase; Uid=[userid]@[servername]; Pwd=myPassword;";

// Best practice is to scope the MySqlConnection to a "using" block
using (MySqlConnection conn = new MySqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    MySqlCommand selectCommand = new MySqlCommand("SELECT * FROM MyTable", conn);
    MySqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

## <a name="samples"></a><span data-ttu-id="840ab-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="840ab-115">Samples</span></span>

- <span data-ttu-id="840ab-116">[ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples) (Примеры кода ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="840ab-116">[ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples)</span></span>
- [<span data-ttu-id="840ab-117">Проектирование первой базы данных Azure для MySQL</span><span class="sxs-lookup"><span data-stu-id="840ab-117">Design a MySQL database using the Azure CLI</span></span>](https://docs.microsoft.com/azure/mysql/tutorial-design-database-using-cli) 

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
