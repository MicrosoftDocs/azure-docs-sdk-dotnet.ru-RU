---
title: Начало работы с API-интерфейсами Azure для .NET и .NET Core
description: Сведения о начале работы с библиотеками Azure для .NET и .NET Core в подписке Azure.
keywords: Azure, .NET, .NET Core, ASP.NET, ASP.NET Core SDK, API, authenticate, get-started
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 08/22/2018
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: ad894e47704fcccc83f7d02acb8e418b167993f9
ms.sourcegitcommit: b2a53a3aea9de6720bd975fb7fe4e722e9d182a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2018
ms.locfileid: "42703057"
---
# <a name="get-started-with-the-azure-net-and-net-core-apis"></a><span data-ttu-id="96052-104">Начало работы с API-интерфейсами Azure для .NET и .NET Core</span><span class="sxs-lookup"><span data-stu-id="96052-104">Get started with the Azure .NET and .NET Core APIs</span></span>

<span data-ttu-id="96052-105">В этом руководстве объясняется, как использовать [API Azure для .NET](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="96052-105">This tutorial demonstrates the usage of several [Azure APIs for .NET](/dotnet/api/overview/azure/).</span></span>  <span data-ttu-id="96052-106">Вы настроите проверку подлинности, создадите и будете использовать учетную запись хранения Azure и базу данных SQL Azure, а также развернете несколько виртуальных машин и веб-приложение службы приложений Azure из GitHub.</span><span class="sxs-lookup"><span data-stu-id="96052-106">You will set up authentication, create and use an Azure Storage account, create and use an Azure SQL Database, deploy some virtual machines, and deploy an Azure App Service Web App from GitHub.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96052-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="96052-107">Prerequisites</span></span>

- <span data-ttu-id="96052-108">Учетная запись Azure.</span><span class="sxs-lookup"><span data-stu-id="96052-108">An Azure account.</span></span> <span data-ttu-id="96052-109">Если у вас ее нет, [получите бесплатную пробную версию](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="96052-109">If you don't have one, [get a free trial](https://azure.microsoft.com/free/)</span></span>

## <a name="set-up-authentication"></a><span data-ttu-id="96052-110">Настройка проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="96052-110">Set up authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="create-a-new-project"></a><span data-ttu-id="96052-111">Создание нового проекта</span><span class="sxs-lookup"><span data-stu-id="96052-111">Create a new project</span></span> 

<span data-ttu-id="96052-112">Создайте новый проект консольного приложения.</span><span class="sxs-lookup"><span data-stu-id="96052-112">Create a new console application project.</span></span>  <span data-ttu-id="96052-113">Для этого в Visual Studio щелкните элементы **Файл**, **Создать** и выберите **Проект...**.  В списке шаблонов Visual C#, выберите **Console App (.NET Core)**, назовите свой проект и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="96052-113">In Visual Studio, do this by clicking **File**, **New**, and then clicking **Project...**.  Under the Visual C# templates, select **Console App (.NET Core)**, name your project, and then click **OK**.</span></span>

![Диалоговое окно "Новый проект"](media/dotnet-sdk-azure-get-started/new-project.png)

<span data-ttu-id="96052-115">Создав консольное приложение, откройте консоль диспетчера пакетов. Для этого выберите **Средства**, **Диспетчер пакетов NuGet**, а затем щелкните **Консоль диспетчера пакетов**.</span><span class="sxs-lookup"><span data-stu-id="96052-115">When the new console app is created, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>  <span data-ttu-id="96052-116">В консоли извлеките нужные вам пакеты, выполнив следующие три команды:</span><span class="sxs-lookup"><span data-stu-id="96052-116">In the console, get the packages you'll need by executing the following three commands:</span></span>

```powershell
# Azure Management Libraries for .NET (Fluent)
Install-Package Microsoft.Azure.Management.Fluent

# Azure Store client libraries
Install-Package WindowsAzure.Storage

# SQL Database client libraries
Install-Package System.Data.SqlClient
```

## <a name="directives"></a><span data-ttu-id="96052-117">Директивы</span><span class="sxs-lookup"><span data-stu-id="96052-117">Directives</span></span>

<span data-ttu-id="96052-118">Измените файл `Program.cs` приложения.</span><span class="sxs-lookup"><span data-stu-id="96052-118">Edit your application's `Program.cs` file.</span></span>  <span data-ttu-id="96052-119">Замените директивы `using` сверху следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="96052-119">Replace the `using` directives at the top with the following:</span></span>

```csharp
using System;
using System.Linq;
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Blob;
using System.Data.SqlClient;
```

## <a name="create-a-virtual-machine"></a><span data-ttu-id="96052-120">Создание виртуальной машины</span><span class="sxs-lookup"><span data-stu-id="96052-120">Create a virtual machine</span></span>

<span data-ttu-id="96052-121">Этот пример развертывает виртуальную машину.</span><span class="sxs-lookup"><span data-stu-id="96052-121">This example deploys a virtual machine.</span></span> 

<span data-ttu-id="96052-122">Замените метод `Main` следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="96052-122">Replace the `Main` method with the following.</span></span>  <span data-ttu-id="96052-123">Не забудьте указать фактические значения `username` и `password` для виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="96052-123">Be sure to provide an actual `username` and `password` for the virtual machine.</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string username = "MY_USERNAME";
    string password = "MY_PASSWORD";
    string rgName = "sampleResourceGroup";
    string windowsVmName = "sampleWindowsVM";
    string publicIpDnsLabel = "samplePublicIP" + (new Random().Next(0,100000)).ToString();

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .WithLogLevel(HttpLoggingDelegatingHandler.Level.Basic)
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the VM
    Console.WriteLine("Creating VM...");
    var windowsVM = azure.VirtualMachines.Define(windowsVmName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithNewPrimaryNetwork("10.0.0.0/28")
        .WithPrimaryPrivateIPAddressDynamic()
        .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
        .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
        .WithAdminUsername(username)
        .WithAdminPassword(password)
        .WithSize(VirtualMachineSizeTypes.StandardD2V2)
        .Create();

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

<span data-ttu-id="96052-124">Нажмите клавишу **F5**, чтобы запустить пример.</span><span class="sxs-lookup"><span data-stu-id="96052-124">Press **F5** to run the sample.</span></span>

<span data-ttu-id="96052-125">Через несколько минут программа завершит задание и появится запрос на нажатие клавиши ВВОД.</span><span class="sxs-lookup"><span data-stu-id="96052-125">After several minutes, the program will finish, prompting you to press enter.</span></span> <span data-ttu-id="96052-126">Нажмите клавишу ВВОД и проверьте виртуальную машину в подписке с помощью Cloud Shell:</span><span class="sxs-lookup"><span data-stu-id="96052-126">After pressing enter, verify the virtual machine in your subscription with the Cloud Shell:</span></span>

```azurecli-interactive
az vm list
```

## <a name="deploy-a-web-app-from-a-github-repo"></a><span data-ttu-id="96052-127">Развертывание веб-приложения из репозитория GitHub</span><span class="sxs-lookup"><span data-stu-id="96052-127">Deploy a web app from a GitHub repo</span></span>

<span data-ttu-id="96052-128">Теперь вы измените код, чтобы развернуть новое веб-приложение из существующего репозитория GitHub.</span><span class="sxs-lookup"><span data-stu-id="96052-128">Now you'll modify your code to create a deploy a new web app from an existing GitHub repository.</span></span> <span data-ttu-id="96052-129">Замените метод `Main` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="96052-129">Replace the `Main` method with the following code:</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string appName = SdkContext.RandomResourceName("WebApp", 20);

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the web app
    Console.WriteLine("Creating Web App...");
    var app = azure.WebApps.Define(appName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithNewFreeAppServicePlan()
        .DefineSourceControl()
        .WithPublicGitRepository("https://github.com/Azure-Samples/app-service-web-dotnet-get-started")
        .WithBranch("master")
        .Attach()
        .Create();
    Console.WriteLine("Your web app is live at: https://{0}", app.HostNames.First());

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

<span data-ttu-id="96052-130">Запустите код, нажав клавишу **F5**.</span><span class="sxs-lookup"><span data-stu-id="96052-130">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="96052-131">Проверьте развертывание: откройте браузер и перейдите по URL-адресу, который отображается в консоли.</span><span class="sxs-lookup"><span data-stu-id="96052-131">Verify the deployment by opening a browser and navigating to URL displayed in the console.</span></span>

## <a name="connect-to-a-sql-database"></a><span data-ttu-id="96052-132">Подключение к базе данных SQL</span><span class="sxs-lookup"><span data-stu-id="96052-132">Connect to a SQL database</span></span>

<span data-ttu-id="96052-133">Этот пример создает базу данных SQL Azure и выполняет ряд операций SQL.</span><span class="sxs-lookup"><span data-stu-id="96052-133">This example creates a new Azure SQL Database and performs a few SQL operations.</span></span>

<span data-ttu-id="96052-134">Замените метод `Main` следующим кодом и укажите надежный пароль для значения `dbPassword`:</span><span class="sxs-lookup"><span data-stu-id="96052-134">Replace the `Main` method with the following, making sure to assign a strong password for `dbPassword`:</span></span>

```csharp
 static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string adminUser = SdkContext.RandomResourceName("db", 8);
    string sqlServerName = SdkContext.RandomResourceName("sql", 10);
    string sqlDbName = SdkContext.RandomResourceName("dbname", 8);
    string dbPassword = "YOUR_PASSWORD_HERE";

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the SQL server and database
    Console.WriteLine("Creating server...");
    var sqlServer = azure.SqlServers.Define(sqlServerName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithAdministratorLogin(adminUser)
        .WithAdministratorPassword(dbPassword)
        .WithNewFirewallRule("0.0.0.0", "255.255.255.255")
        .Create();

    Console.WriteLine("Creating database...");
    var sqlDb = sqlServer.Databases.Define(sqlDbName).Create();

    // Display information for connecting later...
    Console.WriteLine("Created database {0} in server {1}.", sqlDbName, sqlServer.FullyQualifiedDomainName);
    Console.WriteLine("Your user name is {0}.", adminUser + "@" + sqlServer.Name);

    // Build the connection string
    var builder = new SqlConnectionStringBuilder();
    builder.DataSource = sqlServer.FullyQualifiedDomainName;
    builder.InitialCatalog = sqlDbName;
    builder.UserID = adminUser + "@" + sqlServer.Name; // Format user ID as "user@server"
    builder.Password = dbPassword;
    builder.Encrypt = true;
    builder.TrustServerCertificate = true;

    // connect to the database, create a table and insert an entry into it
    using (var conn = new SqlConnection(builder.ConnectionString))
    {
        conn.Open();

        Console.WriteLine("Populating database...");
        var createCommand = new SqlCommand("CREATE TABLE CLOUD (name varchar(255), code int);", conn);
        createCommand.ExecuteNonQuery();

        var insertCommand = new SqlCommand("INSERT INTO CLOUD (name, code ) VALUES ('Azure', 1);", conn);
        insertCommand.ExecuteNonQuery();

        Console.WriteLine("Reading from database...");
        var selectCommand = new SqlCommand("SELECT * FROM CLOUD", conn);
        var results = selectCommand.ExecuteReader();
        while(results.Read())
        {
            Console.WriteLine("Name: {0} Code: {1}", results[0], results[1]);
        }
    }

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

<span data-ttu-id="96052-135">Запустите код, нажав клавишу **F5**.</span><span class="sxs-lookup"><span data-stu-id="96052-135">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="96052-136">Выходные данные в консоли должны подтверждать, что сервер создан и работает правильно. Вы можете подключиться к серверу непосредственно с помощью такого средства, как SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="96052-136">The console output should validate that the server was created and works as expected, but you can connect to it directly with a tool like SQL Server Management Studio if you like.</span></span>

## <a name="write-a-blob-into-a-new-storage-account"></a><span data-ttu-id="96052-137">Запись большого двоичного объекта в новую учетную запись хранения</span><span class="sxs-lookup"><span data-stu-id="96052-137">Write a blob into a new storage account</span></span>

<span data-ttu-id="96052-138">Этот пример создает учетную запись хранения и передает большой двоичный объект.</span><span class="sxs-lookup"><span data-stu-id="96052-138">This example creates a storage account and upload a blob.</span></span>  

<span data-ttu-id="96052-139">Замените метод `Main` следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="96052-139">Replace the `Main` method with the following.</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string storageAccountName = SdkContext.RandomResourceName("st", 10);

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the storage account
    Console.WriteLine("Creating storage account...");
    var storage = azure.StorageAccounts.Define(storageAccountName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .Create();

    var storageKeys = storage.GetKeys();
    string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

    var account = CloudStorageAccount.Parse(storageConnectionString);
    var serviceClient = account.CreateCloudBlobClient();

    // Create container. Name must be lower case.
    Console.WriteLine("Creating container...");
    var container = serviceClient.GetContainerReference("helloazure");
    container.CreateIfNotExistsAsync().Wait();

    // Make the container public
    var containerPermissions = new BlobContainerPermissions()
        { PublicAccess = BlobContainerPublicAccessType.Container };
    container.SetPermissionsAsync(containerPermissions).Wait();

    // write a blob to the container
    Console.WriteLine("Uploading blob...");
    var blob = container.GetBlockBlobReference("helloazure.txt");
    blob.UploadTextAsync("Hello, Azure!").Wait();
    Console.WriteLine("Your blob is located at {0}", blob.StorageUri.PrimaryUri);

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

<span data-ttu-id="96052-140">Нажмите клавишу **F5**, чтобы запустить пример.</span><span class="sxs-lookup"><span data-stu-id="96052-140">Press **F5** to run the sample.</span></span>

<span data-ttu-id="96052-141">Программа будет выполняться несколько минут.</span><span class="sxs-lookup"><span data-stu-id="96052-141">After several minutes, the program finishes.</span></span> <span data-ttu-id="96052-142">Убедитесь, что большой двоичный объект передан. Для этого перейдите по URL-адресу, который отображается в консоли.</span><span class="sxs-lookup"><span data-stu-id="96052-142">Verify the blob was uploaded by browsing to the URL displayed in the console.</span></span>  <span data-ttu-id="96052-143">В браузере должен отображаться текст</span><span class="sxs-lookup"><span data-stu-id="96052-143">You should see the text "Hello, Azure!"</span></span> <span data-ttu-id="96052-144">Hello, Azure!</span><span class="sxs-lookup"><span data-stu-id="96052-144">in your browser.</span></span>

## <a name="clean-up"></a><span data-ttu-id="96052-145">Очистка</span><span class="sxs-lookup"><span data-stu-id="96052-145">Clean up</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96052-146">Если вы не очистите ресурсы, которые использовали для этого руководства, с вас будет взиматься плата за их использование.</span><span class="sxs-lookup"><span data-stu-id="96052-146">If you don't clean up your resources from this tutorial, you will continue to be charged for them.</span></span>  <span data-ttu-id="96052-147">Не забывайте об этом.</span><span class="sxs-lookup"><span data-stu-id="96052-147">Be sure to do this step.</span></span>

<span data-ttu-id="96052-148">Чтобы удалить все созданные ресурсы, введите следующую команду в Cloud Shell:</span><span class="sxs-lookup"><span data-stu-id="96052-148">Delete all the resources you created by entering the following in the Cloud Shell:</span></span>

```azurecli-interactive
az group delete --name sampleResourceGroup
```

## <a name="explore-more-samples"></a><span data-ttu-id="96052-149">Другие примеры</span><span class="sxs-lookup"><span data-stu-id="96052-149">Explore more samples</span></span>

<span data-ttu-id="96052-150">Чтобы узнать, как использовать библиотеки Azure для .NET для управления ресурсами и автоматизации задач, см. примеры кода для [виртуальных машин](dotnet-sdk-azure-virtual-machine-samples.md), [веб-приложений](dotnet-sdk-azure-web-apps-samples.md) и [базы данных SQL](dotnet-sdk-azure-sql-database-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96052-150">To learn more about how to use the Azure libraries for .NET to manage resources and automate tasks, see our sample code for [virtual machines](dotnet-sdk-azure-virtual-machine-samples.md), [web apps](dotnet-sdk-azure-web-apps-samples.md) and [SQL database](dotnet-sdk-azure-sql-database-samples.md).</span></span>

## <a name="reference"></a><span data-ttu-id="96052-151">Справочные материалы</span><span class="sxs-lookup"><span data-stu-id="96052-151">Reference</span></span>

<span data-ttu-id="96052-152">[Справочник](http://docs.microsoft.com/dotnet/api) по всем пакетам.</span><span class="sxs-lookup"><span data-stu-id="96052-152">A [reference](http://docs.microsoft.com/dotnet/api) is available for all packages.</span></span>

[!include[Contribute and community](includes/contribute.md)]
