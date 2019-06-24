---
title: API-интерфейсы Базы данных Azure SQL для .NET
description: Справочник по библиотекам Базы данных SQL Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: sql-database
ms.openlocfilehash: e4c1620ddf488952c6720b9bedf2521c6512b9a3
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190637"
---
# <a name="azure-sql-database-apis-for-net"></a>API-интерфейсы Базы данных Azure SQL для .NET

## <a name="overview"></a>Обзор

[База данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) — это служба базы данных на базе ядра Microsoft SQL Server, которая поддерживает реляционные, пространственные, JSON- и XML-данные. 

Дополнительные сведения об использовании базы данных SQL с .NET см. в статье [Использование .NET (C#) с Visual Studio для подключения и создания запросов к базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="client-library"></a>Клиентская библиотека

Используйте клиентскую библиотеку .NET SQL, чтобы подключиться к базе данных и выполнить проверку подлинности в ней, а также выполнять нерегламентированные инструкции T-SQL и хранимые процедуры.

Установите [пакет NuGet]( https://www.nuget.org/packages/System.Data.SqlClient) непосредственно из [консоли диспетчера пакетов](https://docs.microsoft.com/nuget/tools/package-manager-console) Visual Studio или с помощью [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package System.Data.SqlClient
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package System.Data.SqlClient
```

### <a name="code-example"></a>Пример кода

В этом примере устанавливается подключение к базе данных и считываются строки из таблицы.

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
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/sql/client)

## <a name="management-library"></a>Библиотека управления

Используйте библиотеку управления базами данных SQL Azure, чтобы создавать и масштабировать экземпляры сервера Базы данных SQL Azure, а также управлять ими.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/) непосредственно из [консоли диспетчера пакетов](https://docs.microsoft.com/nuget/tools/package-manager-console) Visual Studio или с помощью [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Sql.Fluent
``` 

#### <a name="net-core-command-line"></a>Командная строка .NET Core

```bash
dotnet add package Microsoft.Azure.Management.Sql.Fluent
```

### <a name="code-example"></a>Пример кода

В этом примере создается экземпляр сервера Базы данных SQL, а также новая база данных на основе этого экземпляра.

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
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/sql/management)

## <a name="samples"></a>Примеры

- [ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples) (Примеры кода ADO.NET)
- [Sample code for using Azure databases with .NET](/dotnet/azure/dotnet-sdk-azure-sql-database-samples) (Пример кода для использования баз данных Azure с .NET)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=sql+database) примеров кода для Базы данных SQL Azure.

