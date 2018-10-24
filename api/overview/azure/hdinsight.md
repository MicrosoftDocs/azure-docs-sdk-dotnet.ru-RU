---
title: Пакет SDK .NET для Azure HDInsight
description: Справочник по пакету SDK .NET для HDInsight
ms.date: 9/19/2018
ms.topic: reference
ms.service: hdinsight
ms.openlocfilehash: 35e2c8c07fb2b86b2d0ae9be4f855e369c1aa86d
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348206"
---
# <a name="azure-hdinsight-net-sdk"></a><span data-ttu-id="088fd-103">Пакет SDK .NET для Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="088fd-103">Azure HDInsight .NET SDK</span></span>

## <a name="azure-hdinsight-libraries-for-net-2x"></a><span data-ttu-id="088fd-104">Библиотеки Azure HDInsight для .NET 2.X</span><span class="sxs-lookup"><span data-stu-id="088fd-104">Azure HDInsight libraries for .NET 2.X</span></span>

## <a name="overview"></a><span data-ttu-id="088fd-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="088fd-105">Overview</span></span>

<span data-ttu-id="088fd-106">Пакет SDK для .NET для службы HDInsight предоставляет классы, связанные с созданием, настройкой, отправкой и мониторингом заданий Hadoop, которыми управляет служба Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="088fd-106">The HDInsight Service .NET SDK provides classes that relate to the creation, configuration, submission, and monitoring of Hadoop jobs managed by an Azure HDInsight Service.</span></span> <span data-ttu-id="088fd-107">Помимо этого он предоставляет классы для управления подписками Azure с помощью службы HDInsight и настройки кластеров, учетных записей хранения и других ресурсов, связанных с кластерами HDInsight, управляемых с использованием подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="088fd-107">In addition, it provides classes to manage Azure subscriptions using the HDInsight Service and to configure the clusters, storage accounts, and other assets associated with the HDInsight clusters that are managed by an Azure subscription.</span></span>

## <a name="management-libraries"></a><span data-ttu-id="088fd-108">Библиотеки управления</span><span class="sxs-lookup"><span data-stu-id="088fd-108">Management libraries</span></span>

### <a name="jobs"></a><span data-ttu-id="088fd-109">Задания</span><span class="sxs-lookup"><span data-stu-id="088fd-109">Jobs</span></span>

<span data-ttu-id="088fd-110">Используйте клиентский пакет SDK для Azure HDInsight, чтобы создавать и отслеживать задания, а также управлять ими в кластере Hadoop.</span><span class="sxs-lookup"><span data-stu-id="088fd-110">Use the Azure HDInsight client SDK to create, manage, and monitor jobs on a Hadoop cluster.</span></span> 

<span data-ttu-id="088fd-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="088fd-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="088fd-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="088fd-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a><span data-ttu-id="088fd-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="088fd-113">Code Example</span></span>

<span data-ttu-id="088fd-114">В этом примере выполняется задание Hive в кластере Hadoop.</span><span class="sxs-lookup"><span data-stu-id="088fd-114">This example runs a Hive job in a Hadoop cluster.</span></span>

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

### <a name="hdinsight"></a><span data-ttu-id="088fd-115">HDInsight</span><span class="sxs-lookup"><span data-stu-id="088fd-115">HDInsight</span></span>

<span data-ttu-id="088fd-116">Используйте пакет SDK управления для Azure HDInsight, чтобы создавать, запускать, останавливать и масштабировать кластеры Hadoop, а также управлять ими.</span><span class="sxs-lookup"><span data-stu-id="088fd-116">Use the Azure HDInsight management SDK to create, manage, start, stop, and scale Hadoop clusters.</span></span>

<span data-ttu-id="088fd-117">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="088fd-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="088fd-118">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="088fd-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a><span data-ttu-id="088fd-119">Пример кода</span><span class="sxs-lookup"><span data-stu-id="088fd-119">Code Example</span></span>

<span data-ttu-id="088fd-120">В этом примере в HDInsight создается кластер Hadoop под управлением Linux. Кластер содержит два узла и использует хранилище BLOB-объектов Azure.</span><span class="sxs-lookup"><span data-stu-id="088fd-120">This example creates an HDInsight two node Linux Hadoop cluster with an existing Azure Blob Storage.</span></span>

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
> [<span data-ttu-id="088fd-121">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="088fd-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a><span data-ttu-id="088fd-122">Примеры</span><span class="sxs-lookup"><span data-stu-id="088fd-122">Samples</span></span>

- [<span data-ttu-id="088fd-123">Создание кластеров под управлением Linux в HDInsight с помощью пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="088fd-123">Cluster creation</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [<span data-ttu-id="088fd-124">Управление кластерами Hadoop в HDInsight с помощью пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="088fd-124">Cluster management</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [<span data-ttu-id="088fd-125">Выполнение запросов Hive с помощью пакета SDK HDInsight для .NET</span><span class="sxs-lookup"><span data-stu-id="088fd-125">Run Hive jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [<span data-ttu-id="088fd-126">Выполнение заданий Pig с помощью пакета SDK для .NET для Hadoop в HDInsight</span><span class="sxs-lookup"><span data-stu-id="088fd-126">Run Pig jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [<span data-ttu-id="088fd-127">Отправка заданий Hadoop в HDInsight</span><span class="sxs-lookup"><span data-stu-id="088fd-127">More jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

<span data-ttu-id="088fd-128">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) примеров кода для базы данных SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="088fd-128">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) of Azure SQL Database samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package

## <a name="hdinsight-net-management-sdk-3x-preview"></a><span data-ttu-id="088fd-129">Пакет Azure Management SDK .NET для HDInsight 3.X (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="088fd-129">HDInsight .NET Management SDK 3.X Preview</span></span>

## <a name="overview"></a><span data-ttu-id="088fd-130">Обзор</span><span class="sxs-lookup"><span data-stu-id="088fd-130">Overview</span></span>

<span data-ttu-id="088fd-131">Пакет SDK .NET для HDInsight предоставляет классы и методы для управления кластерами HDInsight.</span><span class="sxs-lookup"><span data-stu-id="088fd-131">The HDInsight .NET SDK provides classes and methods that allow you to manage your HDInsight clusters.</span></span> <span data-ttu-id="088fd-132">Пакет также поддерживает операции создания, удаления, обновления, получения списков, масштабирования, выполнения скриптов, мониторинга, получения свойства кластеров HDInsight и т. д.</span><span class="sxs-lookup"><span data-stu-id="088fd-132">It includes operations to create, delete, update, list, resize, execute script actions, monitor, get properties of HDInsight clusters, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="088fd-133">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="088fd-133">Prerequisites</span></span>

* <span data-ttu-id="088fd-134">Учетная запись Azure.</span><span class="sxs-lookup"><span data-stu-id="088fd-134">An Azure account.</span></span> <span data-ttu-id="088fd-135">Если у вас ее нет, [получите бесплатную пробную версию](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="088fd-135">If you don't have one, [get a free trial](https://azure.microsoft.com/free/).</span></span>
* [<span data-ttu-id="088fd-136">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="088fd-136">Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/)

## <a name="sdk-installation"></a><span data-ttu-id="088fd-137">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="088fd-137">SDK Installation</span></span>

<span data-ttu-id="088fd-138">В проекте Visual Studio откройте консоль диспетчера пакетов, выбрав **Средства**, **Диспетчер пакетов NuGet**, **Консоль диспетчера пакетов**.</span><span class="sxs-lookup"><span data-stu-id="088fd-138">From your Visual Studio project, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>

<span data-ttu-id="088fd-139">В консоли диспетчера пакетов выполните такие команды:</span><span class="sxs-lookup"><span data-stu-id="088fd-139">In the Package Manager Console, execute the following commands:</span></span>

```
  Install-Package Microsoft.Azure.Management.HDInsight -Version 3.1.0-preview
  Install-Package Microsoft.Azure.Management.Fluent
  Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

## <a name="authentication"></a><span data-ttu-id="088fd-140">Authentication</span><span class="sxs-lookup"><span data-stu-id="088fd-140">Authentication</span></span>

<span data-ttu-id="088fd-141">Для использования пакета SDK нужно выполнить аутентификацию с помощью подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="088fd-141">The SDK first needs to be authenticated with your Azure subscription.</span></span>  <span data-ttu-id="088fd-142">Ниже описано, как создать субъект-службу и использовать его для аутентификации.</span><span class="sxs-lookup"><span data-stu-id="088fd-142">Follow the example below to create a service principal and use it to authenticate.</span></span> <span data-ttu-id="088fd-143">После этого вы получите экземпляр `HDInsightManagementClient`, в котором доступны различные методы (описанные далее) для операций управления.</span><span class="sxs-lookup"><span data-stu-id="088fd-143">After this is done, you will have an instance of an `HDInsightManagementClient`, which contains many methods (outlined in below sections) that can be used to perform management operations.</span></span>

> [!NOTE]
> <span data-ttu-id="088fd-144">Кроме описанного выше, есть и другие методы аутентификации, которые могут оказаться удобнее для вас.</span><span class="sxs-lookup"><span data-stu-id="088fd-144">There are other ways to authenticate besides the below example that could potentially be better suited for your needs.</span></span> <span data-ttu-id="088fd-145">Дополнительные сведения см. в статье [Аутентификация с использованием библиотек Azure для .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span><span class="sxs-lookup"><span data-stu-id="088fd-145">All methods are outlined here: [Authenticate with the Azure Libraries for .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span></span>

### <a name="authentication-example-using-a-service-principal"></a><span data-ttu-id="088fd-146">Пример аутентификации с помощью субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="088fd-146">Authentication Example Using a Service Principal</span></span>

<span data-ttu-id="088fd-147">Сначала войдите в [Azure Cloud Shell](https://shell.azure.com/bash).</span><span class="sxs-lookup"><span data-stu-id="088fd-147">First, login to [Azure Cloud Shell](https://shell.azure.com/bash).</span></span> <span data-ttu-id="088fd-148">Убедитесь, что вы используете подписку, в которой будет создан субъект-служба.</span><span class="sxs-lookup"><span data-stu-id="088fd-148">Verify you are currently using the subscription in which you want the service principal created.</span></span> 

```azurecli-interactive
az account show
```

<span data-ttu-id="088fd-149">Сведения о подписке отображаются в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="088fd-149">Your subscription information is displayed as JSON.</span></span>

```json
{
  "environmentName": "AzureCloud",
  "id": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "isDefault": true,
  "name": "XXXXXXX",
  "state": "Enabled",
  "tenantId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "user": {
    "cloudShellID": true,
    "name": "XXX@XXX.XXX",
    "type": "user"
  }
}
```

<span data-ttu-id="088fd-150">Если вы вошли не в ту подписку, выполните такую команду, чтобы выбрать правильную подписку:</span><span class="sxs-lookup"><span data-stu-id="088fd-150">If you're not logged into the correct subscription, select the correct one by running:</span></span> 
```azurecli-interactive
az account set -s <name or ID of subscription>
```

> [!IMPORTANT]
> <span data-ttu-id="088fd-151">Если вы еще не зарегистрировали поставщик ресурсов HDInsight с помощью другого метода (например, создав кластер HDInsight на портале Azure), вам необходимо это сделать, прежде чем выполнять аутентификацию.</span><span class="sxs-lookup"><span data-stu-id="088fd-151">If you have not already registered the HDInsight Resource Provider by another method (such as by creating an HDInsight Cluster through the Azure Portal), you need to do this once before you can authenticate.</span></span> <span data-ttu-id="088fd-152">Это можно сделать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-152">This can be done from the [Azure Cloud Shell](https://shell.azure.com/bash) by running the following command:</span></span>
>```azurecli-interactive
>az provider register --namespace Microsoft.HDInsight
>```

<span data-ttu-id="088fd-153">Создайте субъект-службу, выбрав имя и выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-153">Next, choose a name for your service principal and create it with the following command:</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name <Service Principal Name> --sdk-auth
```

<span data-ttu-id="088fd-154">Сведения о субъекте-службе отображаются в виде JSON.</span><span class="sxs-lookup"><span data-stu-id="088fd-154">The service principal information is displayed as JSON.</span></span>

```json
{
  "clientId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "clientSecret": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "subscriptionId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "tenantId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```
<span data-ttu-id="088fd-155">Скопируйте фрагмент кода ниже и задайте в качестве значений `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET` и `SUBSCRIPTION_ID` строки из JSON-файла, возвращенного после выполнения команды для создания субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="088fd-155">Copy the below snippet and fill in `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET`, and `SUBSCRIPTION_ID` with the strings from the JSON that was returned after running the command to create the service principal.</span></span>

```csharp
using Microsoft.Azure.Management.HDInsight;
using Microsoft.Azure.Management.HDInsight.Models;
using Microsoft.Azure.Management.ResourceManager.Fluent;

namespace HDI_SDK_Test
{
    class Program
    {
        static void Main(string[] args)
        {
            // Tenant ID for your Azure Subscription
            var TENANT_ID = "";
            // Your Service Principal App Client ID
            var CLIENT_ID = "";
            // Your Service Principal Client Secret
            var CLIENT_SECRET = "";
            // Azure Subscription ID
            var SUBSCRIPTION_ID = "";

            var credentials = SdkContext.AzureCredentialsFactory
                .FromServicePrincipal(
                CLIENT_ID,
                CLIENT_SECRET,
                TENANT_ID,
                AzureEnvironment.AzureGlobalCloud);

            var client = new HDInsightManagementClient(credentials);
            client.SubscriptionId = SUBSCRIPTION_ID;
        }
    }
}
```


## <a name="cluster-management"></a><span data-ttu-id="088fd-156">Управление кластерами</span><span class="sxs-lookup"><span data-stu-id="088fd-156">Cluster Management</span></span>

> [!NOTE]
> <span data-ttu-id="088fd-157">В этом разделе предполагается, что вы уже выполнили аутентификацию, создали экземпляр `HDInsightManagementClient` и сохранили его в переменной с именем `client`.</span><span class="sxs-lookup"><span data-stu-id="088fd-157">This section assumes you have already authenticated and constructed an `HDInsightManagementClient` instance and store it in a variable called `client`.</span></span> <span data-ttu-id="088fd-158">Инструкции по выполнению аутентификации и получению `HDInsightManagementClient` см. в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="088fd-158">Instructions for authenticating and obtaining an `HDInsightManagementClient` can be found in the Authentication section above.</span></span>

### <a name="create-a-cluster"></a><span data-ttu-id="088fd-159">Создание кластера</span><span class="sxs-lookup"><span data-stu-id="088fd-159">Create a Cluster</span></span>

<span data-ttu-id="088fd-160">Кластер можно создать, вызвав `client.Clusters.Create()`.</span><span class="sxs-lookup"><span data-stu-id="088fd-160">A new cluster can be created by calling `client.Clusters.Create()`.</span></span> 

#### <a name="example"></a><span data-ttu-id="088fd-161">Пример</span><span class="sxs-lookup"><span data-stu-id="088fd-161">Example</span></span>

<span data-ttu-id="088fd-162">В этом примере показано, как создать кластер Spark с двумя головными узлами и одним рабочим.</span><span class="sxs-lookup"><span data-stu-id="088fd-162">This example demonstrates how to create a Spark cluster with 2 head nodes and 1 worker node.</span></span>

> [!NOTE]
> <span data-ttu-id="088fd-163">Сначала необходимо создать группу ресурсов и учетную запись хранения, как описано далее.</span><span class="sxs-lookup"><span data-stu-id="088fd-163">You first need to create a Resource Group and Storage Account, as explained below.</span></span> <span data-ttu-id="088fd-164">Если они уже созданы, следующие шаги можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="088fd-164">If you have already created these, you can skip these steps.</span></span>

##### <a name="creating-a-resource-group"></a><span data-ttu-id="088fd-165">Создание группы ресурсов</span><span class="sxs-lookup"><span data-stu-id="088fd-165">Creating a Resource Group</span></span>

<span data-ttu-id="088fd-166">Группу ресурсов можно создать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-166">You can create a resource group using the [Azure Cloud Shell](https://shell.azure.com/bash) by running</span></span>
```azurecli-interactive
az group create -l <Region Name (i.e. eastus)> --n <Resource Group Name>
```
##### <a name="creating-a-storage-account"></a><span data-ttu-id="088fd-167">Создание учетной записи хранения</span><span class="sxs-lookup"><span data-stu-id="088fd-167">Creating a Storage Account</span></span>

<span data-ttu-id="088fd-168">Учетную запись хранения можно создать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-168">You can create a storage account using the [Azure Cloud Shell](https://shell.azure.com/bash) by running:</span></span>
```azurecli-interactive
az storage account create -n <Storage Account Name> -g <Existing Resource Group Name> -l <Region Name (i.e. eastus)> --sku <SKU i.e. Standard_LRS>
```
<span data-ttu-id="088fd-169">Теперь выполните такую команду, чтобы получить ключ для учетной записи хранения (он потребуется для создания кластера):</span><span class="sxs-lookup"><span data-stu-id="088fd-169">Now run the following command to get the key for your storage account (you will need this to create a cluster):</span></span>
```azurecli-interactive
az storage account keys list -n <Storage Account Name>
```
---
<span data-ttu-id="088fd-170">Показанный ниже фрагмент кода .NET создает кластер Spark с двумя головными узлами и одним рабочим.</span><span class="sxs-lookup"><span data-stu-id="088fd-170">The below .NET snippet creates a Spark cluster with 2 head nodes and 1 worker node.</span></span> <span data-ttu-id="088fd-171">Задайте переменные, как описано в комментариях, и при необходимости измените другие параметры.</span><span class="sxs-lookup"><span data-stu-id="088fd-171">Fill in the blank variables as explained in the comments and feel free to change other parameters to suit your specific needs.</span></span>

```csharp
// The name for the cluster you are creating
var clusterName = "";
// The name of your existing Resource Group
var resourceGroupName = "";
// Choose a username
var username = "";
// Choose a password
var password = "";
// Replace <> with the name of your storage account
var storageAccount = "<>.blob.core.windows.net";
// Storage account key you obtained above
var storageAccountKey = "";
// Choose a region
var location = "";
var container = "default";

var parameters = new ClusterCreateParametersExtended
{
    Location = location,
    Tags = new Dictionary<string, string>(),
    Properties = new ClusterCreateProperties
    {
        ClusterVersion = "3.6",
        OsType = OSType.Linux,
        ClusterDefinition = new ClusterDefinition
        {
            Kind = "Hadoop",            
            Configurations = new Dictionary<string, Dictionary<string, string>>()
            {                
                { "gateway", new Dictionary<string, string>
                    {
                        { "restAuthCredential.isEnabled", "true" },
                        { "restAuthCredential.username", username},
                        { "restAuthCredential.password", password}
                    }
                }
            }
        },
        Tier = Tier.Standard,
        ComputeProfile = new ComputeProfile
        {
            Roles = new List<Role>{
                new Role
                {
                    Name = "headnode",
                    TargetInstanceCount = 2,
                    HardwareProfile = new HardwareProfile
                    {
                        VmSize = "Large"
                    },
                    OsProfile = new OsProfile
                    {
                        LinuxOperatingSystemProfile = new LinuxOperatingSystemProfile
                        {
                            Username = username,
                            Password = password
                        }
                    }
                },
                new Role
                {
                    Name = "workernode",
                    TargetInstanceCount = 1,
                    HardwareProfile = new HardwareProfile
                    {
                        VmSize = "Large"
                    },
                    OsProfile = new OsProfile
                    {
                        LinuxOperatingSystemProfile = new LinuxOperatingSystemProfile
                        {
                            Username = username,
                            Password = password
                        }
                    }
                },
            }
        },
        StorageProfile = new StorageProfile
        {
            Storageaccounts = new[]
            {
                new StorageAccount
                {
                    Name = storageAccount,
                    Key = storageAccountKey,
                    Container = container,
                    IsDefault = true
                }
            }
        }
    }
};
client.Clusters.Create(
    resourceGroupName,
    clusterName,
    parameters
);
```

### <a name="get-cluster-details"></a><span data-ttu-id="088fd-172">Получение сведений о кластере</span><span class="sxs-lookup"><span data-stu-id="088fd-172">Get Cluster Details</span></span>

<span data-ttu-id="088fd-173">Чтобы получить сведения о свойствах кластера, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-173">To get properties for a given cluster:</span></span>

```csharp
client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="088fd-174">Пример</span><span class="sxs-lookup"><span data-stu-id="088fd-174">Example</span></span>

<span data-ttu-id="088fd-175">Чтобы убедиться в том, что вы создали кластер, можно использовать `get`.</span><span class="sxs-lookup"><span data-stu-id="088fd-175">You can use `get` to confirm that you have successfully created your cluster.</span></span>

```csharp
var myCluster = client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
Debug.WriteLine(myCluster.Name); //Prints the name of the cluster
Debug.WriteLine(myCluster.Id) //Prints the resource Id of the cluster
```

<span data-ttu-id="088fd-176">Выходные данные должны выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="088fd-176">The output should look like:</span></span>

```
<Cluster Name>
/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/<Resource Group Name>/providers/Microsoft.HDInsight/clusters/<Cluster Name>
```
> [!NOTE]
> <span data-ttu-id="088fd-177">Возвращаемое значение `get`, хранимое в переменной `myCluster`, относится к типу `Microsoft.Azure.Management.HDInsight.ModelsCluster`.</span><span class="sxs-lookup"><span data-stu-id="088fd-177">The return value of `get`, stored in variable `myCluster`, is of type `Microsoft.Azure.Management.HDInsight.ModelsCluster`.</span></span> <span data-ttu-id="088fd-178">См. [полный список свойств этого объекта](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).</span><span class="sxs-lookup"><span data-stu-id="088fd-178">A full list of this object's properties can be found [here](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).</span></span>


### <a name="list-clusters"></a><span data-ttu-id="088fd-179">Получение списка кластеров</span><span class="sxs-lookup"><span data-stu-id="088fd-179">List Clusters</span></span>

#### <a name="list-clusters-under-the-subscription"></a><span data-ttu-id="088fd-180">Получение списка кластеров в пределах подписки</span><span class="sxs-lookup"><span data-stu-id="088fd-180">List Clusters Under The Subscription</span></span>

```csharp
client.Clusters.List();
```
#### <a name="list-clusters-by-resource-group"></a><span data-ttu-id="088fd-181">Получение списка кластеров в пределах в группы ресурсов</span><span class="sxs-lookup"><span data-stu-id="088fd-181">List Clusters By Resource Group</span></span>

```csharp
client.Clusters.ListByResourceGroup("<Resource Group Name>");
```
> [!NOTE]
> <span data-ttu-id="088fd-182">`List()` и `ListByResourceGroup()` возвращают объект `IPage<Cluster>`.</span><span class="sxs-lookup"><span data-stu-id="088fd-182">Both `List()` and `ListByResourceGroup()` return an `IPage<Cluster>` object.</span></span> <span data-ttu-id="088fd-183">Чтобы перейти на следующую страницу, можно вызвать `client.Clusters.ListNext("Next Page Link")`.</span><span class="sxs-lookup"><span data-stu-id="088fd-183">To get the next page, you can call `client.Clusters.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="088fd-184">Команду можно повторять, пока для `NextPageLink` не будет получено значение `null`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="088fd-184">This can be repeated until `NextPageLink` is `null`, as shown in the example below.</span></span>

#### <a name="example"></a><span data-ttu-id="088fd-185">Пример</span><span class="sxs-lookup"><span data-stu-id="088fd-185">Example</span></span>
<span data-ttu-id="088fd-186">В следующем примере выводятся свойства всех кластеров в пределах текущей подписки:</span><span class="sxs-lookup"><span data-stu-id="088fd-186">The following example prints the properties of all clusters for the current subscription:</span></span>

```csharp
var clustersPaged = client.Clusters.List();
while (true)
{
  foreach (var cluster in clustersPaged)
  {
    Debug.WriteLine(cluster.Name);
  
}  if (clustersPaged.NextPageLink == null)
  {
    break;
  }
  clustersPaged = client.Clusters.ListNext(clustersPaged.NextPageLink);
}
```

### <a name="delete-a-cluster"></a><span data-ttu-id="088fd-187">Удаление кластера</span><span class="sxs-lookup"><span data-stu-id="088fd-187">Delete a Cluster</span></span>

<span data-ttu-id="088fd-188">Чтобы удалить кластер, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-188">To delete a cluster:</span></span>

```csharp
client.Clusters.Delete("<Resource Group Name>", "<Cluster Name>");
```

### <a name="update-cluster-tags"></a><span data-ttu-id="088fd-189">Обновление тегов кластера</span><span class="sxs-lookup"><span data-stu-id="088fd-189">Update Cluster Tags</span></span>

<span data-ttu-id="088fd-190">Вы можете обновить теги кластера так:</span><span class="sxs-lookup"><span data-stu-id="088fd-190">You can update the tags of a given cluster like so:</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(<Dictionary of Tags>));
```
#### <a name="example"></a><span data-ttu-id="088fd-191">Пример</span><span class="sxs-lookup"><span data-stu-id="088fd-191">Example</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(new Dictionary<string, string> { { "tag1Name", "tag1Value" }, { "tag2Name", "tag2Value" } }));
```

### <a name="resize-cluster"></a><span data-ttu-id="088fd-192">Изменение размера кластера</span><span class="sxs-lookup"><span data-stu-id="088fd-192">Resize Cluster</span></span>

<span data-ttu-id="088fd-193">Вы можете изменить размер кластера, изменяя количество его рабочих узлов. Укажите новый размер, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="088fd-193">You can resize a given cluster's number of worker nodes by specifying a new size like so:</span></span>

```csharp
client.Clusters.Resize("<Resource Group Name>", "<Cluster Name>", <Num of Worker Nodes (int)>)
```

## <a name="cluster-monitoring"></a><span data-ttu-id="088fd-194">Мониторинг кластера</span><span class="sxs-lookup"><span data-stu-id="088fd-194">Cluster Monitoring</span></span>

<span data-ttu-id="088fd-195">Пакет Azure Management SDK для HDInsight также позволяет управлять мониторингом кластеров с помощью Operations Management Suite (OMS).</span><span class="sxs-lookup"><span data-stu-id="088fd-195">The HDInsight Management SDK can also be used to manage monitoring on your clusters via the Operations Management Suite (OMS).</span></span>

### <a name="enable-oms-monitoring"></a><span data-ttu-id="088fd-196">Включение мониторинга OMS</span><span class="sxs-lookup"><span data-stu-id="088fd-196">Enable OMS Monitoring</span></span>

> [!NOTE]
> <span data-ttu-id="088fd-197">Чтобы включить мониторинг OMS, требуется рабочая область Log Analytics.</span><span class="sxs-lookup"><span data-stu-id="088fd-197">To enable OMS Monitoring, you must have an existing Log Analytics workspace.</span></span> <span data-ttu-id="088fd-198">Если вы не создавали такую рабочую область, см. статью [Создание рабочей области Log Analytics на портале Azure](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).</span><span class="sxs-lookup"><span data-stu-id="088fd-198">If you have not already created one, you can learn how to do that here: [Create a Log Analytics workspace in the Azure portal](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).</span></span>

<span data-ttu-id="088fd-199">Чтобы включить мониторинг OMS в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-199">To enable OMS Monitoring on your cluster:</span></span>

```csharp
client.Extension.EnableMonitoring("<Resource Group Name", "Cluster Name", new ClusterMonitoringRequest(workspaceId: "<Workspace Id>"));
```

### <a name="view-status-of-oms-monitoring"></a><span data-ttu-id="088fd-200">Просмотр состояния мониторинга OMS</span><span class="sxs-lookup"><span data-stu-id="088fd-200">View Status Of OMS Monitoring</span></span>

<span data-ttu-id="088fd-201">Чтобы узнать состояние мониторинга OMS в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-201">To get the status of OMS on your cluster:</span></span>

```csharp
client.Extension.GetMonitoringStatus("<Resource Group Name", "Cluster Name");
```

### <a name="disable-oms-monitoring"></a><span data-ttu-id="088fd-202">Отключение мониторинга OMS</span><span class="sxs-lookup"><span data-stu-id="088fd-202">Disable OMS Monitoring</span></span>

<span data-ttu-id="088fd-203">Чтобы отключить мониторинг OMS в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-203">To disable OMS on your cluster:</span></span>

```csharp
client.Extension.DisableMonitoring("<Resource Group Name>", "<Cluster Name>");
```

## <a name="script-actions"></a><span data-ttu-id="088fd-204">Элемент "Действия скрипта"</span><span class="sxs-lookup"><span data-stu-id="088fd-204">Script Actions</span></span>

<span data-ttu-id="088fd-205">В кластерах HDInsight поддерживается метод конфигурации с использованием, действий скриптов, который вызывает пользовательские скрипты для настройки кластера.</span><span class="sxs-lookup"><span data-stu-id="088fd-205">HDInsight provides a configuration method called script actions that invokes custom scripts to customize the cluster.</span></span>
> [!NOTE]
> <span data-ttu-id="088fd-206">Дополнительные сведения о действиях скриптов см. в статье [Настройка кластеров HDInsight под управлением Linux с помощью действий сценариев](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="088fd-206">More information on how to use script actions can be found here: [Customize Linux-based HDInsight clusters using script actions](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)</span></span>

### <a name="execute-script-actions"></a><span data-ttu-id="088fd-207">Выполнение действий скриптов</span><span class="sxs-lookup"><span data-stu-id="088fd-207">Execute Script Actions</span></span>

<span data-ttu-id="088fd-208">Вы можете выполнить действия скриптов в кластере так:</span><span class="sxs-lookup"><span data-stu-id="088fd-208">You can execute script actions on a given cluster like so:</span></span>

```csharp
var scriptAction1 = new RuntimeScriptAction("<Script Name>", "<URL To Script>", <List<string> of roles>); //valid roles are "headnode", "workernode", "zookeepernode", and "edgenode"

client.Clusters.ExecuteScriptActions("<Resource Group Name>", "<Cluster Name>", new List<RuntimeScriptAction> { scriptAction1 }, <persistOnSuccess (bool)>); //add more RuntimeScriptActions to the list to execute multiple scripts
```

### <a name="delete-script-action"></a><span data-ttu-id="088fd-209">Удаление действий скриптов</span><span class="sxs-lookup"><span data-stu-id="088fd-209">Delete Script Action</span></span>

<span data-ttu-id="088fd-210">Чтобы удалить сохраненные действия скриптов в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-210">To delete a specified persisted script action on a given cluster:</span></span>

```csharp
client.ScriptActions.Delete("<Resource Group Name>", "<Cluster Name>", "<Script Name>");
```

### <a name="list-persisted-script-actions"></a><span data-ttu-id="088fd-211">Получение списка сохраненных действий скриптов</span><span class="sxs-lookup"><span data-stu-id="088fd-211">List Persisted Script Actions</span></span>

> [!NOTE]
> <span data-ttu-id="088fd-212">`ListPersistedScripts()` и `List()` возвращают объект `IPage<RuntimeScriptActionDetail>`.</span><span class="sxs-lookup"><span data-stu-id="088fd-212">`ListPersistedScripts()` and `List()` return an `IPage<RuntimeScriptActionDetail>` object.</span></span> <span data-ttu-id="088fd-213">Чтобы перейти на следующую страницу, можно вызвать `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` или `client.ScriptExecutionHistory.ListNext("Next Page Link")`.</span><span class="sxs-lookup"><span data-stu-id="088fd-213">To get the next page, you can call `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` or `client.ScriptExecutionHistory.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="088fd-214">Команду можно повторять, пока для `NextPageLink` не будет получено значение `null`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="088fd-214">This can be repeated until `NextPageLink` is `null`, as shown in the examples below.</span></span>

<span data-ttu-id="088fd-215">Чтобы получить список всех сохраненных действий скриптов в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-215">To list all persisted script actions for the specified cluster:</span></span>
```csharp
client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="088fd-216">Пример</span><span class="sxs-lookup"><span data-stu-id="088fd-216">Example</span></span>

```csharp
var scriptsPaged = client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
while (true)
{
    foreach (var script in scriptsPaged)
    {
        Debug.WriteLine(script.Name); //There are other properties of RuntimeScriptActionDetail besides Name, such as Status, Operation, StartTime, EndTime, etc. See reference documentation.
    }
    if (scriptsPaged.NextPageLink == null)
    {
        break;
    }
    scriptsPaged = client.ScriptActions.ListPersistedScriptsNext(scriptsPaged.NextPageLink);
}
```

### <a name="list-all-scripts-execution-history"></a><span data-ttu-id="088fd-217">Просмотр журнала выполнения всех скриптов</span><span class="sxs-lookup"><span data-stu-id="088fd-217">List All Scripts' Execution History</span></span>

<span data-ttu-id="088fd-218">Чтобы получить журнал выполнения всех скриптов в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="088fd-218">To list all scripts' execution history for the specified cluster:</span></span>

```csharp
client.script_execution_history.list("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="088fd-219">Пример</span><span class="sxs-lookup"><span data-stu-id="088fd-219">Example</span></span>

<span data-ttu-id="088fd-220">В этом примере выводятся сведения обо всех выполнявшихся скриптах.</span><span class="sxs-lookup"><span data-stu-id="088fd-220">This example prints all the details for all past script executions.</span></span>

```csharp
var scriptExecutionsPaged = client.ScriptExecutionHistory.List("<Resource Group Name>", "<Cluster Name>");
while (true)
{
    foreach (var script in scriptExecutionsPaged)
    {
        Debug.WriteLine(script.Name); //There are other properties of RuntimeScriptActionDetail besides Name, such as Status, Operation, StartTime, EndTime, etc. See reference documentation.

    }
    if (scriptExecutionsPaged.NextPageLink == null)
    {
        break;
    }
    scriptExecutionsPaged = client.ScriptExecutionHistory.ListNext(scriptExecutionsPaged.NextPageLink);
}
```
