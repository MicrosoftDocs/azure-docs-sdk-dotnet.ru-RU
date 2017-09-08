---
title: "Начало работы с API Azure для .NET"
description: "Базовое использование библиотек Azure для .NET с подпиской Azure."
keywords: Azure, .NET, SDK, API ,authenticate, get-started
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: get-started-article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.assetid: 
ms.openlocfilehash: 0379609e863c674de4518d5ed615b6b4f9c46a12
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="get-started-with-the-azure-net-apis"></a><span data-ttu-id="e56b0-104">Начало работы с API Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="e56b0-104">Get started with the Azure .NET APIs</span></span>

<span data-ttu-id="e56b0-105">В этом руководстве объясняется, как использовать [API Azure для .NET](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="e56b0-105">This tutorial demonstrates the usage of several [Azure APIs for .NET](/dotnet/api/overview/azure/).</span></span>  <span data-ttu-id="e56b0-106">Вы настроите проверку подлинности, создадите и будете использовать учетную запись хранения Azure и базу данных SQL Azure, а также развернете несколько виртуальных машин и веб-приложение службы приложений Azure из GitHub.</span><span class="sxs-lookup"><span data-stu-id="e56b0-106">You will set up authentication, create and use an Azure Storage account, create and use an Azure SQL Database, deploy some virtual machines, and deploy an Azure App Service Web App from GitHub.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e56b0-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="e56b0-107">Prerequisites</span></span>

- <span data-ttu-id="e56b0-108">Учетная запись Azure.</span><span class="sxs-lookup"><span data-stu-id="e56b0-108">An Azure account.</span></span> <span data-ttu-id="e56b0-109">Если у вас ее нет, [получите бесплатную пробную версию](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="e56b0-109">If you don't have one, [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="e56b0-110">Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e56b0-110">Azure PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)

## <a name="set-up-authentication"></a><span data-ttu-id="e56b0-111">Настройка проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="e56b0-111">Set up authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="create-a-new-project"></a><span data-ttu-id="e56b0-112">Создание нового проекта</span><span class="sxs-lookup"><span data-stu-id="e56b0-112">Create a new project</span></span> 

<span data-ttu-id="e56b0-113">Создайте новый проект консольного приложения.</span><span class="sxs-lookup"><span data-stu-id="e56b0-113">Create a new console application project.</span></span>  <span data-ttu-id="e56b0-114">Для этого в Visual Studio щелкните элементы **Файл**, **Создать** и выберите **Проект...**.  В списке шаблонов Visual C#, выберите **Console App (.NET Core)**, назовите свой проект и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="e56b0-114">In Visual Studio, do this by clicking **File**, **New**, and then clicking **Project...**.  Under the Visual C# templates, select **Console App (.NET Core)**, name your project, and then click **OK**.</span></span>

![Диалоговое окно "Новый проект"](media/dotnet-sdk-azure-get-started/new-project.png)

<span data-ttu-id="e56b0-116">Создав консольное приложение, откройте консоль диспетчера пакетов. Для этого выберите **Средства**, **Диспетчер пакетов NuGet**, а затем щелкните **Консоль диспетчера пакетов**.</span><span class="sxs-lookup"><span data-stu-id="e56b0-116">When the new console app is created, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>  <span data-ttu-id="e56b0-117">В консоли извлеките нужные вам пакеты, выполнив следующие три команды:</span><span class="sxs-lookup"><span data-stu-id="e56b0-117">In the console, get the packages you'll need by executing the following three commands:</span></span>

```powershell
# Azure Management Libraries for .NET (Fluent)
Install-Package Microsoft.Azure.Management.Fluent

# Azure Store client libraries
Install-Package WindowsAzure.Storage

# SQL Database client libraries
Install-Package System.Data.SqlClient
```

## <a name="directives"></a><span data-ttu-id="e56b0-118">Директивы</span><span class="sxs-lookup"><span data-stu-id="e56b0-118">Directives</span></span>

<span data-ttu-id="e56b0-119">Измените файл `Program.cs` приложения.</span><span class="sxs-lookup"><span data-stu-id="e56b0-119">Edit your application's `Program.cs` file.</span></span>  <span data-ttu-id="e56b0-120">Замените директивы `using` сверху следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="e56b0-120">Replace the `using` directives at the top with the following:</span></span>

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

## <a name="create-a-virtual-machine"></a><span data-ttu-id="e56b0-121">Создание виртуальной машины</span><span class="sxs-lookup"><span data-stu-id="e56b0-121">Create a virtual machine</span></span>

<span data-ttu-id="e56b0-122">Этот пример развертывает виртуальную машину.</span><span class="sxs-lookup"><span data-stu-id="e56b0-122">This example deploys a virtual machine.</span></span> 

<span data-ttu-id="e56b0-123">Замените метод `Main` следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="e56b0-123">Replace the `Main` method with the following.</span></span>  <span data-ttu-id="e56b0-124">Не забудьте указать фактические значения `username` и `password` для виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="e56b0-124">Be sure to provide an actual `username` and `password` for the virtual machine.</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string username = "MY_USERNAME";
    string password = "MY_PASSWORD";
    string rgName = "sampleResourceGroup";
    string windowsVmName = "sampleWindowsVM";
    string publicIpDnsLabel = "samplePublicIP";

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

<span data-ttu-id="e56b0-125">Нажмите клавишу **F5**, чтобы запустить пример.</span><span class="sxs-lookup"><span data-stu-id="e56b0-125">Press **F5** to run the sample.</span></span>

<span data-ttu-id="e56b0-126">Через несколько минут программа завершит задание и появится запрос на нажатие клавиши ВВОД.</span><span class="sxs-lookup"><span data-stu-id="e56b0-126">After several minutes, the program will finish, prompting you to press enter.</span></span> <span data-ttu-id="e56b0-127">Нажмите клавишу ВВОД и проверьте виртуальную машину в подписке с помощью PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e56b0-127">After pressing enter, verify the virtual machine in your subscription with PowerShell:</span></span>

```powershell
Get-AzureRmVm -ResourceGroupName sampleResourceGroup
```

## <a name="deploy-a-web-app-from-a-github-repo"></a><span data-ttu-id="e56b0-128">Развертывание веб-приложения из репозитория GitHub</span><span class="sxs-lookup"><span data-stu-id="e56b0-128">Deploy a web app from a GitHub repo</span></span>

<span data-ttu-id="e56b0-129">Теперь вы измените код, чтобы развернуть новое веб-приложение из существующего репозитория GitHub.</span><span class="sxs-lookup"><span data-stu-id="e56b0-129">Now you'll modify your code to create a deploy a new web app from an existing GitHub repository.</span></span> <span data-ttu-id="e56b0-130">Замените метод `Main` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="e56b0-130">Replace the `Main` method with the following code:</span></span>

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

<span data-ttu-id="e56b0-131">Запустите код, нажав клавишу **F5**.</span><span class="sxs-lookup"><span data-stu-id="e56b0-131">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="e56b0-132">Проверьте развертывание: откройте браузер и перейдите по URL-адресу, который отображается в консоли.</span><span class="sxs-lookup"><span data-stu-id="e56b0-132">Verify the deployment by opening a browser and navigating to URL displayed in the console.</span></span>

## <a name="connect-to-a-sql-database"></a><span data-ttu-id="e56b0-133">Подключение к базе данных SQL</span><span class="sxs-lookup"><span data-stu-id="e56b0-133">Connect to a SQL database</span></span>

<span data-ttu-id="e56b0-134">Этот пример создает базу данных SQL Azure и выполняет ряд операций SQL.</span><span class="sxs-lookup"><span data-stu-id="e56b0-134">This example creates a new Azure SQL Database and performs a few SQL operations.</span></span>

<span data-ttu-id="e56b0-135">Замените метод `Main` следующим кодом и укажите надежный пароль для значения `dbPassword`:</span><span class="sxs-lookup"><span data-stu-id="e56b0-135">Replace the `Main` method with the following, making sure to assign a strong password for `dbPassword`:</span></span>

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
<span data-ttu-id="e56b0-136">Запустите код, нажав клавишу **F5**.</span><span class="sxs-lookup"><span data-stu-id="e56b0-136">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="e56b0-137">Выходные данные в консоли должны подтверждать, что сервер создан и работает правильно. Вы можете подключиться к серверу непосредственно с помощью такого средства, как SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="e56b0-137">The console output should validate that the server was created and works as expected, but you can connect to it directly with a tool like SQL Server Management Studio if you like.</span></span>

## <a name="write-a-blob-into-a-new-storage-account"></a><span data-ttu-id="e56b0-138">Запись большого двоичного объекта в новую учетную запись хранения</span><span class="sxs-lookup"><span data-stu-id="e56b0-138">Write a blob into a new storage account</span></span>

<span data-ttu-id="e56b0-139">Этот пример создает учетную запись хранения и отправляет большой двоичный объект.</span><span class="sxs-lookup"><span data-stu-id="e56b0-139">This example will create a storage account and upload a blob.</span></span>  

<span data-ttu-id="e56b0-140">Замените метод `Main` следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="e56b0-140">Replace the `Main` method with the following.</span></span>

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

<span data-ttu-id="e56b0-141">Нажмите клавишу **F5**, чтобы запустить пример.</span><span class="sxs-lookup"><span data-stu-id="e56b0-141">Press **F5** to run the sample.</span></span>

<span data-ttu-id="e56b0-142">Программа будет выполняться несколько минут.</span><span class="sxs-lookup"><span data-stu-id="e56b0-142">After several minutes, the program will finish.</span></span> <span data-ttu-id="e56b0-143">Убедитесь, что большой двоичный объект передан. Для этого перейдите по URL-адресу, который отображается в консоли.</span><span class="sxs-lookup"><span data-stu-id="e56b0-143">Verify the blob was uploaded by browsing to the URL displayed in the console.</span></span>  <span data-ttu-id="e56b0-144">В браузере должен отображаться текст</span><span class="sxs-lookup"><span data-stu-id="e56b0-144">You should see the text "Hello, Azure!"</span></span> <span data-ttu-id="e56b0-145">Hello, Azure!</span><span class="sxs-lookup"><span data-stu-id="e56b0-145">in your browser.</span></span>

## <a name="clean-up"></a><span data-ttu-id="e56b0-146">Очистка</span><span class="sxs-lookup"><span data-stu-id="e56b0-146">Clean up</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e56b0-147">Если вы не очистите ресурсы, которые использовали для этого руководства, с вас будет взиматься плата за их использование.</span><span class="sxs-lookup"><span data-stu-id="e56b0-147">If you don't clean up your resources from this tutorial, you will continue to be charged for them.</span></span>  <span data-ttu-id="e56b0-148">Не забывайте об этом.</span><span class="sxs-lookup"><span data-stu-id="e56b0-148">Be sure to do this step.</span></span>

<span data-ttu-id="e56b0-149">Чтобы удалить все созданные ресурсы, введите следующую команду в PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e56b0-149">Delete all the resources you created by entering the following in PowerShell:</span></span>

```powershell
Remove-AzureRmResourceGroup -ResourceGroupName sampleResourceGroup
```
## <a name="explore-more-samples"></a><span data-ttu-id="e56b0-150">Другие примеры</span><span class="sxs-lookup"><span data-stu-id="e56b0-150">Explore more samples</span></span>

<span data-ttu-id="e56b0-151">Чтобы узнать, как использовать библиотеки Azure для .NET для управления ресурсами и автоматизации задач, см. примеры кода для [виртуальных машин](dotnet-sdk-azure-virtual-machine-samples.md), [веб-приложений](dotnet-sdk-azure-web-apps-samples.md) и [базы данных SQL](dotnet-sdk-azure-sql-database-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e56b0-151">To learn more about how to use the Azure libraries for .NET to manage resources and automate tasks, see our sample code for [virtual machines](dotnet-sdk-azure-virtual-machine-samples.md), [web apps](dotnet-sdk-azure-web-apps-samples.md) and [SQL database](dotnet-sdk-azure-sql-database-samples.md).</span></span>

## <a name="reference"></a><span data-ttu-id="e56b0-152">Справочные материалы</span><span class="sxs-lookup"><span data-stu-id="e56b0-152">Reference</span></span>

<span data-ttu-id="e56b0-153">[Справочник](http://docs.microsoft.com/dotnet/api) по всем пакетам.</span><span class="sxs-lookup"><span data-stu-id="e56b0-153">A [reference](http://docs.microsoft.com/dotnet/api) is available for all packages.</span></span>

[!include[Contribute and community](includes/contribute.md)]
