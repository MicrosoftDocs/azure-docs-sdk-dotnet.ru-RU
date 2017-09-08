---
title: "Аутентификация с использованием библиотек Azure для .NET"
description: "Аутентификация в библиотеках Azure для .NET"
keywords: Azure, .NET, SDK, API, authentication, active directory, service principal
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.assetid: 
ms.openlocfilehash: 5bc1f4a576ae3bb38e9d29c890ea79bc0871cd01
ms.sourcegitcommit: fa02d34afbf981f809661ab842b3b93242a38f68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2017
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a><span data-ttu-id="e89e1-104">Аутентификация с использованием библиотек Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="e89e1-104">Authenticate with the Azure Libraries for .NET</span></span>

## <a name="connect-to-services-with-connection-strings"></a><span data-ttu-id="e89e1-105">Подключение к службам с помощью строк подключения</span><span class="sxs-lookup"><span data-stu-id="e89e1-105">Connect to services with connection strings</span></span>

<span data-ttu-id="e89e1-106">Большинство библиотек службы Azure требуют строку подключения или ключ для аутентификации.</span><span class="sxs-lookup"><span data-stu-id="e89e1-106">Most Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="e89e1-107">Например, база данных SQL использует стандартную строку подключения SQL:</span><span class="sxs-lookup"><span data-stu-id="e89e1-107">For example, SQL Database uses a standard SQL connection string:</span></span>

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

<span data-ttu-id="e89e1-108">Служба хранилища Azure использует ключ к хранилищу данных:</span><span class="sxs-lookup"><span data-stu-id="e89e1-108">Azure Storage uses a storage key:</span></span>

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

<span data-ttu-id="e89e1-109">Строки подключения службы используются в других службах Azure, например [CosmosDB](https://docs.microsoft.com/en-us/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [кэш Redis](https://docs.microsoft.com/en-us/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache) и [служебная шина](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Эти строки можно получить с помощью портала Azure, CLI или PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e89e1-109">Service connection strings are used in other Azure services like [CosmosDB](https://docs.microsoft.com/en-us/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [Redis Cache](https://docs.microsoft.com/en-us/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues) and you can get those strings using the Azure portal, CLI, or PowerShell.</span></span>  <span data-ttu-id="e89e1-110">Также с помощью библиотек управления Azure для .NET можно выполнять запросы к ресурсам для создания строк подключения в коде.</span><span class="sxs-lookup"><span data-stu-id="e89e1-110">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span> 

<span data-ttu-id="e89e1-111">В этом фрагменте кода используются библиотеки управления для создания строки подключения учетной записи хранения:</span><span class="sxs-lookup"><span data-stu-id="e89e1-111">This snippet uses the management libraries to create a storage account connection string:</span></span>

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

<span data-ttu-id="e89e1-112">Для других библиотек требуется, чтобы приложение работало с [субъектом-службой](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects), который разрешает приложению работать с предоставленными учетными данными.</span><span class="sxs-lookup"><span data-stu-id="e89e1-112">Other libraries require your application to run with a [service principal](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) authorizing the application to run with granted credentials.</span></span> <span data-ttu-id="e89e1-113">Эта конфигурация похожа на действия аутентификации на основе объекта для библиотеки управления, перечисленные ниже.</span><span class="sxs-lookup"><span data-stu-id="e89e1-113">This configuration is similar to the object-based authentication steps for the management library listed below.</span></span>

## <span data-ttu-id="e89e1-114"><a name="mgmt-auth"></a>Библиотеки управления Azure для аутентификации .NET</span><span class="sxs-lookup"><span data-stu-id="e89e1-114"><a name="mgmt-auth"></a>Azure management libraries for .NET authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="e89e1-115">После создания субъекта-службы выполнить аутентификацию субъекта-службы для создания и администрирования ресурсов можно двумя способами.</span><span class="sxs-lookup"><span data-stu-id="e89e1-115">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="e89e1-116">Для обоих вариантов необходимо добавить следующие пакеты NuGet в проект.</span><span class="sxs-lookup"><span data-stu-id="e89e1-116">For both options you will need to add the following nuget packages to your project.</span></span>

```
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="e89e1-117">Аутентификация с использованием учетных данных токена</span><span class="sxs-lookup"><span data-stu-id="e89e1-117">Authenticate with token credentials</span></span>

<span data-ttu-id="e89e1-118">Первый способ — создание объекта учетных данных токена в коде.</span><span class="sxs-lookup"><span data-stu-id="e89e1-118">The first method is to build the token credential object in code.</span></span>  <span data-ttu-id="e89e1-119">Учетные данные следует безопасно хранить в файле конфигурации, реестре или Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="e89e1-119">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId, 
    AzureEnvironment.AzureGlobalCloud);
```

- <span data-ttu-id="e89e1-120">clientId — используйте значение *ApplicationId* из выходных данных субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="e89e1-120">clientId: use the *ApplicationId* value from the service principal output.</span></span>
- <span data-ttu-id="e89e1-121">clientSecret — используйте параметр *-Password*, который вы назначили при запуске `New-AzureRmADServicePrincipal` (без кавычек).</span><span class="sxs-lookup"><span data-stu-id="e89e1-121">clientSecret: use the *-Password* parameter you assigned when you ran `New-AzureRmADServicePrincipal` (without quotes).</span></span>
- <span data-ttu-id="e89e1-122">tenantId — используйте значение *TenantId*, которое использовалось при запуске `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="e89e1-122">tenantId: use the *TenantId* value from when you ran `Login-AzureRmAccount`.</span></span>

<span data-ttu-id="e89e1-123">Затем создайте точку входа объекта `Azure`, чтобы приступить к работе с API:</span><span class="sxs-lookup"><span data-stu-id="e89e1-123">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <span data-ttu-id="e89e1-124"><a name="mgmt-file"></a>Аутентификация на основе файла</span><span class="sxs-lookup"><span data-stu-id="e89e1-124"><a name="mgmt-file"></a>File-based authentication</span></span>

<span data-ttu-id="e89e1-125">Аутентификация на основе файла позволяет поместить учетные данные субъекта-службы в текстовый файл и защитить его в файловой системе.</span><span class="sxs-lookup"><span data-stu-id="e89e1-125">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="e89e1-126">Прочтите содержимое файла и создайте точку входа объекта `Azure`, чтобы приступить к работе с API:</span><span class="sxs-lookup"><span data-stu-id="e89e1-126">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment 
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
