---
title: "API-интерфейсы базы данных Azure SQL для .NET"
description: "Справочник по библиотекам базы данных SQL Azure для .NET"
keywords: Azure, .NET, SDK, API, SQL, database
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: sql
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 61b98b3096123b509b5c9f08bfc654aa37cf2149
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
---
# <a name="azure-sql-database-apis-for-net"></a><span data-ttu-id="ef1b2-104">API-интерфейсы базы данных Azure SQL для .NET</span><span class="sxs-lookup"><span data-stu-id="ef1b2-104">Azure SQL Database APIs for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="ef1b2-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="ef1b2-105">Overview</span></span>

<span data-ttu-id="ef1b2-106">[База данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) — это служба базы данных на базе ядра Microsoft SQL Server, которая поддерживает реляционные, пространственные, JSON- и XML-данные.</span><span class="sxs-lookup"><span data-stu-id="ef1b2-106">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) is a database service using the Microsoft SQL Server engine that supports relational, JSON, spatial, and XML data.</span></span> 

<span data-ttu-id="ef1b2-107">Дополнительные сведения об использовании базы данных SQL с .NET см. в статье [Использование .NET (C#) с Visual Studio для подключения и создания запросов к базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ef1b2-107">To learn more about the using SQL Database with .NET, see [Use .NET with Visual Studio to connect and query an Azure SQL database](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).</span></span>

## <a name="client-library"></a><span data-ttu-id="ef1b2-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="ef1b2-108">Client library</span></span>

<span data-ttu-id="ef1b2-109">Используйте клиентскую библиотеку .NET SQL, чтобы подключиться к базе данных и выполнить проверку подлинности в ней, а также выполнять нерегламентированные инструкции T-SQL и хранимые процедуры.</span><span class="sxs-lookup"><span data-stu-id="ef1b2-109">Use the .NET SQL client library to connect and authenticate with your database and execute ad-hoc T-SQL statements and stored procedures.</span></span>

<span data-ttu-id="ef1b2-110">Установите [пакет NuGet]( https://www.nuget.org/packages/System.Data.SqlClient) непосредственно из [консоли диспетчера пакетов](https://docs.microsoft.com/nuget/tools/package-manager-console) Visual Studio или с помощью [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span><span class="sxs-lookup"><span data-stu-id="ef1b2-110">Install the [NuGet package]( https://www.nuget.org/packages/System.Data.SqlClient) directly from the Visual Studio [Package Manager console](https://docs.microsoft.com/nuget/tools/package-manager-console) or with the [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="ef1b2-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef1b2-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package System.Data.SqlClient
```

#### <a name="net-core-cli"></a><span data-ttu-id="ef1b2-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="ef1b2-112">.NET Core CLI</span></span>

```bash
dotnet add package System.Data.SqlClient
```

### <a name="code-example"></a><span data-ttu-id="ef1b2-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="ef1b2-113">Code Example</span></span>

<span data-ttu-id="ef1b2-114">В этом примере устанавливается подключение к базе данных и считываются строки из таблицы.</span><span class="sxs-lookup"><span data-stu-id="ef1b2-114">This example connects to a database and reads rows from a table.</span></span>

```csharp
/* Include this 'using' directive...
using System.Data.SqlClient;
*/

// Always store connection strings securely. 
string connectionString = "Server=tcp:[serverName].database.windows.net;" 
    + "Database=myDataBase;User ID=[loginname]@[serverName];Password=myPassword;"
    + "Trusted_Connection=False;Encrypt=True;";

// Best practice is to scope the SqlConnection to a "using" block
using (SqlConnection conn = new SqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    SqlCommand selectCommand = new SqlCommand("SELECT * FROM MyTable", conn);
    SqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="ef1b2-115">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="ef1b2-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/sql/client)

## <a name="management-library"></a><span data-ttu-id="ef1b2-116">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="ef1b2-116">Management library</span></span>

<span data-ttu-id="ef1b2-117">Используйте библиотеку управления базами данных SQL Azure, чтобы создавать и масштабировать экземпляры сервера базы данных SQL Azure, а также управлять ими.</span><span class="sxs-lookup"><span data-stu-id="ef1b2-117">Use the Azure SQL Database management library to create, manage, and scale Azure SQL Database server instances.</span></span>

<span data-ttu-id="ef1b2-118">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/) непосредственно из [консоли диспетчера пакетов](https://docs.microsoft.com/nuget/tools/package-manager-console) Visual Studio или с помощью [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span><span class="sxs-lookup"><span data-stu-id="ef1b2-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/) directly from the Visual Studio [Package Manager console](https://docs.microsoft.com/nuget/tools/package-manager-console) or with the [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="ef1b2-119">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef1b2-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Sql.Fluent
``` 

#### <a name="net-core-command-line"></a><span data-ttu-id="ef1b2-120">Командная строка .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef1b2-120">.NET Core command line</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Sql.Fluent
```

### <a name="code-example"></a><span data-ttu-id="ef1b2-121">Пример кода</span><span class="sxs-lookup"><span data-stu-id="ef1b2-121">Code Example</span></span>

<span data-ttu-id="ef1b2-122">В этом примере создается экземпляр сервера базы данных SQL, а также новая база данных на основе этого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="ef1b2-122">This example creates a new SQL Database server instance and then creates a new database on that instance.</span></span>

```csharp
/* Include these 'using' directives...
using Microsoft.Azure.Management.Sql.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

string startAddress = "0.0.0.0";
string endAddress = "255.255.255.255";

// Create the SQL server instance
ISqlServer sqlServer = azure.SqlServers.Define("UniqueServerName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup("ResourceGroupName")
    .WithAdministratorLogin("UserName")
    .WithAdministratorPassword("Password")
    .WithNewFirewallRule(startAddress, endAddress)
    .Create();

// Create the database
ISqlDatabase sqlDb = sqlServer.Databases.Define("DatabaseName").Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="ef1b2-123">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="ef1b2-123">Explore the management APIs</span></span>](/dotnet/api/overview/azure/sql/management)

## <a name="samples"></a><span data-ttu-id="ef1b2-124">Примеры</span><span class="sxs-lookup"><span data-stu-id="ef1b2-124">Samples</span></span>

- <span data-ttu-id="ef1b2-125">[ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples) (Примеры кода ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ef1b2-125">[ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples)</span></span>
- <span data-ttu-id="ef1b2-126">[Sample code for using Azure databases with .NET](/dotnet/azure/dotnet-sdk-azure-sql-database-samples) (Пример кода для использования баз данных Azure с .NET)</span><span class="sxs-lookup"><span data-stu-id="ef1b2-126">[Azure management libraries for .NET samples for SQL Database](/dotnet/azure/dotnet-sdk-azure-sql-database-samples)</span></span>

<span data-ttu-id="ef1b2-127">Просмотрите [полный список](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=sql+database) примеров кода для базы данных SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="ef1b2-127">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=sql+database) of Azure SQL Database samples.</span></span>

