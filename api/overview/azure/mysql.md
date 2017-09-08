---
title: "Библиотеки базы данных Azure для MySQL для .NET"
description: "Справочная документация по клиентским библиотекам .NET для базы данных Azure для MySQL"
keywords: Azure, .NET, SDK, API, SQL, database, MySQL
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: mysql
ms.openlocfilehash: 1bc373d63b0172fd554277a6ef30fa09772a395b
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-database-for-mysql-libraries-for-net"></a>Библиотеки базы данных Azure для MySQL для .NET

## <a name="overview"></a>Обзор

Работа с данными и ресурсами, хранящимися в [базе данных Azure для MySQL](/azure/mysql/overview).

## <a name="client-apis"></a>Интерфейсы API клиента

Рекомендуемой клиентской библиотекой для доступа к базе данных Azure для MySQL является MySQL [Connector/Net](https://dev.mysql.com/doc/connector-net/en). Подключитесь к базе данных при помощи пакета и напрямую выполните инструкции SQL. 

Установите [пакет NuGet](https://www.nuget.org/packages/MySql.Data) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package MySql.Data
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package MySql.Data
```

### <a name="code-example"></a>Пример кода

Подключение к базе данных MySQL и выполнение запроса:

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

## <a name="samples"></a>Примеры

- [ADO.NET code examples](/dotnet/framework/data/adonet/ado-net-code-examples) (Примеры кода ADO.NET)
- [Проектирование первой базы данных Azure для MySQL](https://docs.microsoft.com/azure/mysql/tutorial-design-database-using-cli) 

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package