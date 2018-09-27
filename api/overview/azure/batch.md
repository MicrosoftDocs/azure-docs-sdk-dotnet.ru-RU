---
title: Библиотеки пакетной службы Azure для .NET
description: Справочник по библиотекам пакетной службы для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: batch
ms.openlocfilehash: 4220faacc9b8cbe394f98eaccd1e71aaf4ab8f0d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190117"
---
# <a name="azure-batch-libraries-for-net"></a><span data-ttu-id="8408b-103">Библиотеки пакетной службы Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="8408b-103">Azure Batch libraries for .NET</span></span>

<span data-ttu-id="8408b-104">Пакетная служба Azure — это служба платформы, которая позволяет эффективно работать с приложениями для крупномасштабных параллельных и высокопроизводительных вычислений (HPC) в облаке.</span><span class="sxs-lookup"><span data-stu-id="8408b-104">Azure Batch is a platform service for running large-scale parallel and high-performance computing (HPC) applications efficiently in the cloud.</span></span> <span data-ttu-id="8408b-105">Пакетная служба Azure планирует запуск ресурсоемких вычислительных задач в управляемой коллекции виртуальных машин и автоматически масштабирует вычислительные ресурсы, учитывая требования заданий.</span><span class="sxs-lookup"><span data-stu-id="8408b-105">Azure Batch schedules compute-intensive work to run on a managed collection of virtual machines, and can automatically scale compute resources to meet the needs of your jobs.</span></span>

<span data-ttu-id="8408b-106">С помощью пакетной службы Azure вы можете легко определять вычислительные ресурсы Azure, необходимые для параллельного выполнения приложений в нужном масштабе.</span><span class="sxs-lookup"><span data-stu-id="8408b-106">With Azure Batch, you can easily define Azure compute resources to execute your applications in parallel, and at scale.</span></span> <span data-ttu-id="8408b-107">Вам не нужно вручную создавать и настраивать кластер высокопроизводительных вычислений (HPC), отдельные виртуальные машины, виртуальные сети или сложную инфраструктуру планировщика задач и заданий, а также управлять всеми этими ресурсами.</span><span class="sxs-lookup"><span data-stu-id="8408b-107">There's no need to manually create, configure, and manage an HPC cluster, individual virtual machines, virtual networks, or a complex job and task scheduling infrastructure.</span></span> <span data-ttu-id="8408b-108">Пакетная служба Azure автоматизирует или упрощает выполнение этих задач.</span><span class="sxs-lookup"><span data-stu-id="8408b-108">Azure Batch automates or simplifies these tasks for you.</span></span>

<span data-ttu-id="8408b-109">Узнайте больше о том, как [выполнять реальные параллельные рабочие нагрузки с использованием пакетной службы](/azure/batch/batch-technical-overview).</span><span class="sxs-lookup"><span data-stu-id="8408b-109">Read more about how to [run intrinsically parallel workloads with Batch](/azure/batch/batch-technical-overview).</span></span> <span data-ttu-id="8408b-110">Также ознакомьтесь со статьей [Приступая к созданию решений с помощью клиентской библиотеки пакетной службы для .NET](/azure/batch/batch-dotnet-get-started).</span><span class="sxs-lookup"><span data-stu-id="8408b-110">You can also learn how to [get started building solutions with the Batch client library for .NET](/azure/batch/batch-dotnet-get-started).</span></span> <span data-ttu-id="8408b-111">Узнайте, как [управлять учетными записями и квотами пакетной службы с помощью клиентской библиотеки .NET для управления пакетной службой](/azure/batch/batch-management-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8408b-111">Discover how to [manage Batch accounts and quotas with the Batch Management library for .NET](/azure/batch/batch-management-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="8408b-112">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="8408b-112">Client library</span></span>

<span data-ttu-id="8408b-113">Используйте клиентскую библиотеку для выполнения параллельных рабочих нагрузок с использованием пакетной службы.</span><span class="sxs-lookup"><span data-stu-id="8408b-113">Use the client library to run parallel workloads with Batch.</span></span>

<span data-ttu-id="8408b-114">Установите [пакет NuGet](https://www.nuget.org/packages/Azure.Batch) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8408b-114">Install the [NuGet package](https://www.nuget.org/packages/Azure.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8408b-115">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8408b-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Azure.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="8408b-116">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="8408b-116">.NET Core CLI</span></span>

```bash
dotnet add package Azure.Batch
```

### <a name="example"></a><span data-ttu-id="8408b-117">Пример</span><span class="sxs-lookup"><span data-stu-id="8408b-117">Example</span></span>

<span data-ttu-id="8408b-118">В примере ниже клиентский пакет SDK используется для создания задания, выполняющегося в пакетной службе Azure.</span><span class="sxs-lookup"><span data-stu-id="8408b-118">The following example uses the client SDK to create a job to run in Azure Batch.</span></span>

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
> [<span data-ttu-id="8408b-119">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="8408b-119">Explore the client APIs</span></span>](/dotnet/api/overview/azure/batch/client)

## <a name="management-library"></a><span data-ttu-id="8408b-120">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="8408b-120">Management library</span></span>

<span data-ttu-id="8408b-121">С помощью этих библиотек управления можно программно управлять учетными записями пакетной службы, квотами и пакетами приложений.</span><span class="sxs-lookup"><span data-stu-id="8408b-121">Use the management library to programmatically manage Batch accounts, quotas, and application packages.</span></span>

<span data-ttu-id="8408b-122">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8408b-122">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8408b-123">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8408b-123">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="8408b-124">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="8408b-124">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Batch
```

### <a name="example"></a><span data-ttu-id="8408b-125">Пример</span><span class="sxs-lookup"><span data-stu-id="8408b-125">Example</span></span>

<span data-ttu-id="8408b-126">В примере ниже извлекается квота для подписки, создается учетная запись и повторно создается первичный ключ учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8408b-126">The following example retrieves the quota for the subscription, creates an account, and regenerates the primary account key.</span></span>

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
> [<span data-ttu-id="8408b-127">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="8408b-127">Explore the management APIs</span></span>](/dotnet/api/overview/azure/batch/management)

## <a name="samples"></a><span data-ttu-id="8408b-128">Примеры</span><span class="sxs-lookup"><span data-stu-id="8408b-128">Samples</span></span>

* [<span data-ttu-id="8408b-129">Примеры клиента пакетной службы и управляющего пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="8408b-129">Azure Batch Client and Management SDK for .NET Samples</span></span>](https://github.com/Azure/azure-batch-samples/tree/master/CSharp)

<span data-ttu-id="8408b-130">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="8408b-130">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
