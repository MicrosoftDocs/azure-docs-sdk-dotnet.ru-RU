---
title: Аутентификация с использованием библиотек Azure для .NET
description: Аутентификация в библиотеках Azure для .NET
ms.date: 08/22/2018
ms.openlocfilehash: d0d8db89816a887fa23490a213917a3c554ecdb4
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190867"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a>Аутентификация с использованием библиотек Azure для .NET

## <a name="connect-to-services-with-connection-strings"></a>Подключение к службам с помощью строк подключения

Большинство библиотек службы Azure требуют строку подключения или ключ для аутентификации. Например, база данных SQL использует стандартную строку подключения SQL:

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;
                
using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

Служба хранилища Azure использует ключ к хранилищу данных:

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

Строки подключения службы используются в других службах Azure, например [CosmosDB](/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [кэш Redis](/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache) и [служебная шина](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Эти строки можно получить с помощью портала Azure, CLI или PowerShell.  Также с помощью библиотек управления Azure для .NET можно выполнять запросы к ресурсам для создания строк подключения в коде. 

В этом фрагменте кода используются библиотеки управления для создания строки подключения учетной записи хранения:

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

Для других библиотек требуется, чтобы приложение работало с [субъектом-службой](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects), который разрешает приложению работать с предоставленными учетными данными. Эта конфигурация похожа на действия аутентификации на основе объекта для библиотеки управления, перечисленные ниже.

## <a name="mgmt-auth"></a>Библиотеки управления Azure для аутентификации .NET

[!include[Create service principal](includes/create-sp.md)]

После создания субъекта-службы выполнить аутентификацию субъекта-службы для создания и администрирования ресурсов можно двумя способами.

Для обоих вариантов необходимо добавить следующие пакеты NuGet в проект.

```
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>Аутентификация с использованием учетных данных токена

Первый способ — создание объекта учетных данных токена в коде.  Учетные данные следует безопасно хранить в файле конфигурации, реестре или Azure Key Vault.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId, 
    AzureEnvironment.AzureGlobalCloud);
```

При создании субъекта-службы используйте значения *clientId*, *clientSecret* и *tenantId* из выходных данных JSON.

Затем создайте точку входа объекта `Azure`, чтобы приступить к работе с API:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="mgmt-file"></a>Аутентификация на основе файла

Аутентификация на основе файла позволяет поместить учетные данные субъекта-службы в текстовый файл и защитить его в файловой системе.

[!include[File-based authentication](includes/file-based-auth.md)]

Прочтите содержимое файла и создайте точку входа объекта `Azure`, чтобы приступить к работе с API:

```csharp
// pull in the location of the authentication properties file from the environment 
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
