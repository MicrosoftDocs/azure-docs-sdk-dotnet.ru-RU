---
title: Библиотеки Azure HDInsight для .NET
description: Справочник по библиотекам Azure HDInsight для .NET
keywords: Azure, .NET, SDK, API, HDInsight
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: hd-insight
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 2cdb080b4d224a77a36318cefd13ebfae2e3e2e1
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065814"
---
# <a name="azure-hdinsight-libraries-for-net"></a><span data-ttu-id="a29a0-104">Библиотеки Azure HDInsight для .NET</span><span class="sxs-lookup"><span data-stu-id="a29a0-104">Azure HDInsight libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a29a0-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="a29a0-105">Overview</span></span>

<span data-ttu-id="a29a0-106">Пакет SDK для .NET для службы HDInsight предоставляет классы, связанные с созданием, настройкой, отправкой и мониторингом заданий Hadoop, которыми управляет служба Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="a29a0-106">The HDInsight Service .NET SDK provides classes that relate to the creation, configuration, submission, and monitoring of Hadoop jobs managed by an Azure HDInsight Service.</span></span> <span data-ttu-id="a29a0-107">Помимо этого он предоставляет классы для управления подписками Azure с помощью службы HDInsight и настройки кластеров, учетных записей хранения и других ресурсов, связанных с кластерами HDInsight, управляемых с использованием подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="a29a0-107">In addition, it provides classes to manage Azure subscriptions using the HDInsight Service and to configure the clusters, storage accounts, and other assets associated with the HDInsight clusters that are managed by an Azure subscription.</span></span>

## <a name="management-libraries"></a><span data-ttu-id="a29a0-108">Библиотеки управления</span><span class="sxs-lookup"><span data-stu-id="a29a0-108">Management libraries</span></span>

### <a name="jobs"></a><span data-ttu-id="a29a0-109">Задания</span><span class="sxs-lookup"><span data-stu-id="a29a0-109">Jobs</span></span>

<span data-ttu-id="a29a0-110">Используйте клиентский пакет SDK для Azure HDInsight, чтобы создавать и отслеживать задания, а также управлять ими в кластере Hadoop.</span><span class="sxs-lookup"><span data-stu-id="a29a0-110">Use the Azure HDInsight client SDK to create, manage, and monitor jobs on a Hadoop cluster.</span></span> 

<span data-ttu-id="a29a0-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="a29a0-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a29a0-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a29a0-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a><span data-ttu-id="a29a0-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="a29a0-113">Code Example</span></span>

<span data-ttu-id="a29a0-114">В этом примере выполняется задание Hive в кластере Hadoop.</span><span class="sxs-lookup"><span data-stu-id="a29a0-114">This example runs a Hive job in a Hadoop cluster.</span></span>

```csharp
HDInsightJobManagementClient managementClient = new HDInsightJobManagementClient(clusterUri, credentials);

Dictionary<string, string> defines = new Dictionary<string, string> {
    { "hive.execution.engine", "tez" },
    { "hive.exec.reducers.max", "1" }
};
List<string> arguments = new List<string> { { "argA" }, { "argB" } };
HiveJobSubmissionParameters parameters = new HiveJobSubmissionParameters
{
    Query = "SHOW TABLES",
    Defines = defines,
    Arguments = arguments
};

JobSubmissionResponse jobResponse = managementClient.JobManagement.SubmitHiveJob(parameters);
```

### <a name="hdinsight"></a><span data-ttu-id="a29a0-115">HDInsight</span><span class="sxs-lookup"><span data-stu-id="a29a0-115">HDInsight</span></span>

<span data-ttu-id="a29a0-116">Используйте пакет SDK управления для Azure HDInsight, чтобы создавать, запускать, останавливать и масштабировать кластеры Hadoop, а также управлять ими.</span><span class="sxs-lookup"><span data-stu-id="a29a0-116">Use the Azure HDInsight management SDK to create, manage, start, stop, and scale Hadoop clusters.</span></span>

<span data-ttu-id="a29a0-117">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="a29a0-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a29a0-118">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a29a0-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a><span data-ttu-id="a29a0-119">Пример кода</span><span class="sxs-lookup"><span data-stu-id="a29a0-119">Code Example</span></span>

<span data-ttu-id="a29a0-120">В этом примере в HDInsight создается кластер Hadoop под управлением Linux. Кластер содержит два узла и использует хранилище BLOB-объектов Azure.</span><span class="sxs-lookup"><span data-stu-id="a29a0-120">This example creates an HDInsight two node Linux Hadoop cluster with an existing Azure Blob Storage.</span></span>

```csharp
HDInsightManagementClient managementClient = new HDInsightManagementClient(authToken);
// Set parameters for the new cluster
ClusterCreateParameters parameters = new ClusterCreateParameters
{
    ClusterSizeInNodes = 2,
    UserName = "admin",
    Password = "<Enter HTTP User Password>",
    ClusterType = "Hadoop",
    OSType = OSType.Linux,
    Version = "3.5",
    // Use an Azure storage account as the default storage
    DefaultStorageInfo = new AzureStorageInfo("<StorageAccount>", "<StorageKey>", "<BlobContainerName>"),
    Location = "EAST US 2",
    SshUserName = "sshuser",
    SshPassword = "<Enter SSH User Password>",
};

// Create the cluster
managementClient.Clusters.Create("<ExistingResourceGroupName>", "<NewClusterName>", parameters);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a29a0-121">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="a29a0-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a><span data-ttu-id="a29a0-122">Примеры</span><span class="sxs-lookup"><span data-stu-id="a29a0-122">Samples</span></span>

- [<span data-ttu-id="a29a0-123">Создание кластеров под управлением Linux в HDInsight с помощью пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="a29a0-123">Cluster creation</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [<span data-ttu-id="a29a0-124">Управление кластерами Hadoop в HDInsight с помощью пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="a29a0-124">Cluster management</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [<span data-ttu-id="a29a0-125">Выполнение запросов Hive с помощью пакета SDK HDInsight для .NET</span><span class="sxs-lookup"><span data-stu-id="a29a0-125">Run Hive jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [<span data-ttu-id="a29a0-126">Выполнение заданий Pig с помощью пакета SDK для .NET для Hadoop в HDInsight</span><span class="sxs-lookup"><span data-stu-id="a29a0-126">Run Pig jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [<span data-ttu-id="a29a0-127">Отправка заданий Hadoop в HDInsight</span><span class="sxs-lookup"><span data-stu-id="a29a0-127">More jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

<span data-ttu-id="a29a0-128">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) примеров кода для базы данных SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="a29a0-128">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) of Azure SQL Database samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
