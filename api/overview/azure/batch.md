---
title: "Библиотеки пакетной службы Azure для .NET"
description: "Справочник по библиотекам пакетной службы для .NET"
keywords: Azure, .NET, SDK, API, Batch
author: camsoper
ms.author: casoper
manager: douge
ms.date: 08/01/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 753721d430de0577c0bc1dd3774d728783a3bfee
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-batch-libraries-for-net"></a><span data-ttu-id="5d7fc-104">Библиотеки пакетной службы Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="5d7fc-104">Azure Batch libraries for .NET</span></span>

<span data-ttu-id="5d7fc-105">Пакетная служба Azure — это служба платформы, которая позволяет эффективно работать с приложениями для крупномасштабных параллельных и высокопроизводительных вычислений (HPC) в облаке.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-105">Azure Batch is a platform service for running large-scale parallel and high-performance computing (HPC) applications efficiently in the cloud.</span></span> <span data-ttu-id="5d7fc-106">Пакетная служба Azure планирует запуск ресурсоемких вычислительных задач в управляемой коллекции виртуальных машин и автоматически масштабирует вычислительные ресурсы, учитывая требования заданий.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-106">Azure Batch schedules compute-intensive work to run on a managed collection of virtual machines, and can automatically scale compute resources to meet the needs of your jobs.</span></span>

<span data-ttu-id="5d7fc-107">С помощью пакетной службы Azure вы можете легко определять вычислительные ресурсы Azure, необходимые для параллельного выполнения приложений в нужном масштабе.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-107">With Azure Batch, you can easily define Azure compute resources to execute your applications in parallel, and at scale.</span></span> <span data-ttu-id="5d7fc-108">Вам не нужно вручную создавать и настраивать кластер высокопроизводительных вычислений (HPC), отдельные виртуальные машины, виртуальные сети или сложную инфраструктуру планировщика задач и заданий, а также управлять всеми этими ресурсами.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-108">There's no need to manually create, configure, and manage an HPC cluster, individual virtual machines, virtual networks, or a complex job and task scheduling infrastructure.</span></span> <span data-ttu-id="5d7fc-109">Пакетная служба Azure автоматизирует или упрощает выполнение этих задач.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-109">Azure Batch automates or simplifies these tasks for you.</span></span>

<span data-ttu-id="5d7fc-110">Узнайте больше о том, как [выполнять реальные параллельные рабочие нагрузки с использованием пакетной службы](/azure/batch/batch-technical-overview).</span><span class="sxs-lookup"><span data-stu-id="5d7fc-110">Read more about how to [run intrinsically parallel workloads with Batch](/azure/batch/batch-technical-overview).</span></span> <span data-ttu-id="5d7fc-111">Также ознакомьтесь со статьей [Приступая к созданию решений с помощью клиентской библиотеки пакетной службы для .NET](/azure/batch/batch-dotnet-get-started).</span><span class="sxs-lookup"><span data-stu-id="5d7fc-111">You can also learn how to [get started building solutions with the Batch client library for .NET](/azure/batch/batch-dotnet-get-started).</span></span> <span data-ttu-id="5d7fc-112">Узнайте, как [управлять учетными записями и квотами пакетной службы с помощью клиентской библиотеки .NET для управления пакетной службой](/azure/batch/batch-management-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5d7fc-112">Discover how to [manage Batch accounts and quotas with the Batch Management library for .NET](/azure/batch/batch-management-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="5d7fc-113">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="5d7fc-113">Client library</span></span>

<span data-ttu-id="5d7fc-114">Используйте клиентскую библиотеку для выполнения параллельных рабочих нагрузок с использованием пакетной службы.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-114">Use the client library to run parallel workloads with Batch.</span></span>

<span data-ttu-id="5d7fc-115">Установите [пакет NuGet](https://www.nuget.org/packages/Azure.Batch) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5d7fc-115">Install the [NuGet package](https://www.nuget.org/packages/Azure.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5d7fc-116">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5d7fc-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Azure.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="5d7fc-117">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="5d7fc-117">.NET Core CLI</span></span>

```bash
dotnet add package Azure.Batch
```

### <a name="example"></a><span data-ttu-id="5d7fc-118">Пример</span><span class="sxs-lookup"><span data-stu-id="5d7fc-118">Example</span></span>

<span data-ttu-id="5d7fc-119">В примере ниже клиентский пакет SDK используется для создания задания, выполняющегося в пакетной службе Azure.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-119">The following example uses the client SDK to create a job to run in Azure Batch.</span></span>

```csharp
/*
using Microsoft.Azure.Batch.Auth;
using Microsoft.Azure.Batch;
*/
BatchSharedKeyCredentials credentials = new BatchSharedKeyCredentials(batchUrl, accountName, accountKey);
using (BatchClient batchClient = await BatchClient.OpenAsync(credentials))
{
    //set up pool specification and information along with resource files here
    JobManagerTask jobManagerTask = new JobManagerTask()
    {
        ResourceFiles = jobManagerResourceFiles,
        CommandLine = Constants.JobManagerExecutable,

        //Determines if the job should terminate when the job manager process exits.
        KillJobOnCompletion = true,
        Id = jobManagerTaskId
    };

    string jobId = Environment.GetEnvironmentVariable("USERNAME") + DateTime.UtcNow.ToString("yyyyMMdd-HHmmss");

    CloudJob unboundJob = batchClient.JobOperations.CreateJob(jobId, poolInformation);
    unboundJob.JobManagerTask = jobManagerTask;

    // now interact with the job ...
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d7fc-120">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="5d7fc-120">Explore the client APIs</span></span>](/dotnet/api/overview/azure/batch/client)

## <a name="management-library"></a><span data-ttu-id="5d7fc-121">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="5d7fc-121">Management library</span></span>

<span data-ttu-id="5d7fc-122">С помощью этих библиотек управления можно программно управлять учетными записями пакетной службы, квотами и пакетами приложений.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-122">Use the management library to programmatically manage Batch accounts, quotas, and application packages.</span></span>

<span data-ttu-id="5d7fc-123">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5d7fc-123">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5d7fc-124">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5d7fc-124">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="5d7fc-125">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="5d7fc-125">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Batch
```

### <a name="example"></a><span data-ttu-id="5d7fc-126">Пример</span><span class="sxs-lookup"><span data-stu-id="5d7fc-126">Example</span></span>

<span data-ttu-id="5d7fc-127">В примере ниже извлекается квота для подписки, создается учетная запись и повторно создается первичный ключ учетной записи.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-127">The following example retrieves the quota for the subscription, creates an account, and regenerates the primary account key.</span></span>

```csharp
/*
using Microsoft.Azure.Management.Batch;
using Microsoft.Azure.Management.Batch.Models;
using Microsoft.Rest;
*/
using (BatchManagementClient batchManagementClient = new BatchManagementClient(new TokenCredentials(accessToken)))
{
    batchManagementClient.SubscriptionId = subscriptionId;

    // Get the account quota for the subscription
    BatchLocationQuota quotaResponse = await batchManagementClient.Location.GetQuotasAsync(location);
    Console.WriteLine("Your subscription can create {0} account(s) in the {1} region.", quotaResponse.AccountQuota, location);

    // Create account
    await batchManagementClient.BatchAccount.CreateAsync(ResourceGroupName, accountName, 
        new BatchAccountCreateParameters() { Location = location });

    // Regenerate primary account key
    BatchAccountKeys newKeys = await batchManagementClient.BatchAccount.RegenerateKeyAsync(
        ResourceGroupName, account.Name, AccountKeyType.Primary);
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d7fc-128">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="5d7fc-128">Explore the management APIs</span></span>](/dotnet/api/overview/azure/batch/management)

## <a name="samples"></a><span data-ttu-id="5d7fc-129">Примеры</span><span class="sxs-lookup"><span data-stu-id="5d7fc-129">Samples</span></span>

* [<span data-ttu-id="5d7fc-130">Примеры клиента пакетной службы и управляющего пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="5d7fc-130">Azure Batch Client and Management SDK for .NET Samples</span></span>](https://github.com/Azure/azure-batch-samples/tree/master/CSharp)

<span data-ttu-id="5d7fc-131">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-131">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
