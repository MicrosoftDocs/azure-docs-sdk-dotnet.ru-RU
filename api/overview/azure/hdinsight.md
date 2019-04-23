---
title: Пакет SDK Azure HDInsight для .NET
description: Справочник по пакету SDK Azure HDInsight для .NET.
ms.date: 04/10/2019
ms.topic: reference
ms.service: hdinsight
ms.openlocfilehash: 2282a302b269a52c71ed88c26e021344cdca4382
ms.sourcegitcommit: 4328168172ac1b1a448e16988f75199262bc5c2d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59700262"
---
# <a name="azure-hdinsight-sdk-for-net"></a><span data-ttu-id="da2dc-103">Пакет SDK Azure HDInsight для .NET</span><span class="sxs-lookup"><span data-stu-id="da2dc-103">Azure HDInsight SDK for .NET</span></span>

<span data-ttu-id="da2dc-104">Azure HDInsight предлагает пакеты SDK с заданиями и средствами управления для .NET с возможностью использовать классы для управления кластером HDInsight, а также отправки и мониторинга заданий Hadoop.</span><span class="sxs-lookup"><span data-stu-id="da2dc-104">Azure HDInsight offers management and job SDKs for .NET that provide classes for managing your HDInsight cluster and submitting and monitoring Hadoop jobs.</span></span>

## <a name="management"></a><span data-ttu-id="da2dc-105">управления</span><span class="sxs-lookup"><span data-stu-id="da2dc-105">Management</span></span>

<span data-ttu-id="da2dc-106">Пакет SDK HDInsight для .NET предоставляет классы и методы для управления кластерами HDInsight.</span><span class="sxs-lookup"><span data-stu-id="da2dc-106">The HDInsight management SDK for .NET provides classes and methods that allow you to manage your HDInsight clusters.</span></span> <span data-ttu-id="da2dc-107">Пакет также поддерживает операции создания, удаления, обновления, получения списков, масштабирования, выполнения скриптов, мониторинга, получения свойства кластеров HDInsight и т. д.</span><span class="sxs-lookup"><span data-stu-id="da2dc-107">It includes operations to create, delete, update, list, resize, execute script actions, monitor, get properties of HDInsight clusters, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da2dc-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="da2dc-108">Prerequisites</span></span>

* <span data-ttu-id="da2dc-109">Учетная запись Azure.</span><span class="sxs-lookup"><span data-stu-id="da2dc-109">An Azure account.</span></span> <span data-ttu-id="da2dc-110">Если у вас ее нет, [получите бесплатную пробную версию](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="da2dc-110">If you don't have one, [get a free trial](https://azure.microsoft.com/free/).</span></span>
* [<span data-ttu-id="da2dc-111">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da2dc-111">Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/)

## <a name="sdk-installation"></a><span data-ttu-id="da2dc-112">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="da2dc-112">SDK Installation</span></span>

<span data-ttu-id="da2dc-113">В проекте Visual Studio откройте консоль диспетчера пакетов, выбрав **Средства**, **Диспетчер пакетов NuGet**, **Консоль диспетчера пакетов**.</span><span class="sxs-lookup"><span data-stu-id="da2dc-113">From your Visual Studio project, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>

<span data-ttu-id="da2dc-114">В консоли диспетчера пакетов выполните такие команды:</span><span class="sxs-lookup"><span data-stu-id="da2dc-114">In the Package Manager Console, execute the following commands:</span></span>

```
  Install-Package Microsoft.Azure.Management.HDInsight
  Install-Package Microsoft.Azure.Management.Fluent
  Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

## <a name="authentication"></a><span data-ttu-id="da2dc-115">Authentication</span><span class="sxs-lookup"><span data-stu-id="da2dc-115">Authentication</span></span>

<span data-ttu-id="da2dc-116">Для использования пакета SDK нужно выполнить аутентификацию с помощью подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="da2dc-116">The SDK first needs to be authenticated with your Azure subscription.</span></span>  <span data-ttu-id="da2dc-117">Ниже описано, как создать субъект-службу и использовать его для аутентификации.</span><span class="sxs-lookup"><span data-stu-id="da2dc-117">Follow the example below to create a service principal and use it to authenticate.</span></span> <span data-ttu-id="da2dc-118">После этого вы получите экземпляр `HDInsightManagementClient`, в котором доступны различные методы (описанные далее) для операций управления.</span><span class="sxs-lookup"><span data-stu-id="da2dc-118">After this is done, you will have an instance of an `HDInsightManagementClient`, which contains many methods (outlined in below sections) that can be used to perform management operations.</span></span>

> [!NOTE]
> <span data-ttu-id="da2dc-119">Кроме описанного выше, есть и другие методы аутентификации, которые могут оказаться удобнее для вас.</span><span class="sxs-lookup"><span data-stu-id="da2dc-119">There are other ways to authenticate besides the below example that could potentially be better suited for your needs.</span></span> <span data-ttu-id="da2dc-120">Все способы описаны в статье [Аутентификация с использованием библиотек Azure для .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span><span class="sxs-lookup"><span data-stu-id="da2dc-120">All methods are outlined here: [Authenticate with the Azure Libraries for .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span></span>

### <a name="authentication-example-using-a-service-principal"></a><span data-ttu-id="da2dc-121">Пример аутентификации с помощью субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="da2dc-121">Authentication Example Using a Service Principal</span></span>

<span data-ttu-id="da2dc-122">Сначала войдите в [Azure Cloud Shell](https://shell.azure.com/bash).</span><span class="sxs-lookup"><span data-stu-id="da2dc-122">First, login to [Azure Cloud Shell](https://shell.azure.com/bash).</span></span> <span data-ttu-id="da2dc-123">Убедитесь, что вы используете подписку, в которой будет создан субъект-служба.</span><span class="sxs-lookup"><span data-stu-id="da2dc-123">Verify you are currently using the subscription in which you want the service principal created.</span></span> 

```azurecli-interactive
az account show
```

<span data-ttu-id="da2dc-124">Сведения о подписке отображаются в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="da2dc-124">Your subscription information is displayed as JSON.</span></span>

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

<span data-ttu-id="da2dc-125">Если вы вошли не в ту подписку, выполните такую команду, чтобы выбрать правильную подписку:</span><span class="sxs-lookup"><span data-stu-id="da2dc-125">If you're not logged into the correct subscription, select the correct one by running:</span></span> 
```azurecli-interactive
az account set -s <name or ID of subscription>
```

> [!IMPORTANT]
> <span data-ttu-id="da2dc-126">Если вы еще не зарегистрировали поставщик ресурсов HDInsight с помощью другого метода (например, создав кластер HDInsight на портале Azure), вам необходимо это сделать, прежде чем выполнять аутентификацию.</span><span class="sxs-lookup"><span data-stu-id="da2dc-126">If you have not already registered the HDInsight Resource Provider by another method (such as by creating an HDInsight Cluster through the Azure Portal), you need to do this once before you can authenticate.</span></span> <span data-ttu-id="da2dc-127">Это можно сделать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-127">This can be done from the [Azure Cloud Shell](https://shell.azure.com/bash) by running the following command:</span></span>
>```azurecli-interactive
>az provider register --namespace Microsoft.HDInsight
>```

<span data-ttu-id="da2dc-128">Создайте субъект-службу, выбрав имя и выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-128">Next, choose a name for your service principal and create it with the following command:</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name <Service Principal Name> --sdk-auth
```

<span data-ttu-id="da2dc-129">Сведения о субъекте-службе отображаются в виде JSON.</span><span class="sxs-lookup"><span data-stu-id="da2dc-129">The service principal information is displayed as JSON.</span></span>

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
<span data-ttu-id="da2dc-130">Скопируйте фрагмент кода ниже и задайте в качестве значений `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET` и `SUBSCRIPTION_ID` строки из JSON-файла, возвращенного после выполнения команды для создания субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="da2dc-130">Copy the below snippet and fill in `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET`, and `SUBSCRIPTION_ID` with the strings from the JSON that was returned after running the command to create the service principal.</span></span>

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

## <a name="cluster-management"></a><span data-ttu-id="da2dc-131">Управление кластерами</span><span class="sxs-lookup"><span data-stu-id="da2dc-131">Cluster Management</span></span>

> [!NOTE]
> <span data-ttu-id="da2dc-132">В этом разделе предполагается, что вы уже выполнили аутентификацию, создали экземпляр `HDInsightManagementClient` и сохранили его в переменной с именем `client`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-132">This section assumes you have already authenticated and constructed an `HDInsightManagementClient` instance and store it in a variable called `client`.</span></span> <span data-ttu-id="da2dc-133">Инструкции по выполнению аутентификации и получению `HDInsightManagementClient` см. в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="da2dc-133">Instructions for authenticating and obtaining an `HDInsightManagementClient` can be found in the Authentication section above.</span></span>

### <a name="create-a-cluster"></a><span data-ttu-id="da2dc-134">Создание кластера</span><span class="sxs-lookup"><span data-stu-id="da2dc-134">Create a Cluster</span></span>

<span data-ttu-id="da2dc-135">Кластер можно создать, вызвав `client.Clusters.Create()`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-135">A new cluster can be created by calling `client.Clusters.Create()`.</span></span>

#### <a name="samples"></a><span data-ttu-id="da2dc-136">Примеры</span><span class="sxs-lookup"><span data-stu-id="da2dc-136">Samples</span></span>

<span data-ttu-id="da2dc-137">Для создания нескольких распространенных типов кластеров HDInsight доступны примеры кода: [Примеры .NET для HDInsight](https://github.com/Azure-Samples/hdinsight-dotnet-sdk-samples).</span><span class="sxs-lookup"><span data-stu-id="da2dc-137">Code samples for creating several common types of HDInsight clusters are available: [HDInsight .NET Samples](https://github.com/Azure-Samples/hdinsight-dotnet-sdk-samples).</span></span>

#### <a name="example"></a><span data-ttu-id="da2dc-138">Пример</span><span class="sxs-lookup"><span data-stu-id="da2dc-138">Example</span></span>

<span data-ttu-id="da2dc-139">В этом примере показано, как создать кластер Spark с двумя головными узлами и одним рабочим.</span><span class="sxs-lookup"><span data-stu-id="da2dc-139">This example demonstrates how to create a Spark cluster with 2 head nodes and 1 worker node.</span></span>

> [!NOTE]
> <span data-ttu-id="da2dc-140">Сначала необходимо создать группу ресурсов и учетную запись хранения, как описано далее.</span><span class="sxs-lookup"><span data-stu-id="da2dc-140">You first need to create a Resource Group and Storage Account, as explained below.</span></span> <span data-ttu-id="da2dc-141">Если они уже созданы, следующие шаги можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="da2dc-141">If you have already created these, you can skip these steps.</span></span>

##### <a name="creating-a-resource-group"></a><span data-ttu-id="da2dc-142">Создание группы ресурсов</span><span class="sxs-lookup"><span data-stu-id="da2dc-142">Creating a Resource Group</span></span>

<span data-ttu-id="da2dc-143">Группу ресурсов можно создать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-143">You can create a resource group using the [Azure Cloud Shell](https://shell.azure.com/bash) by running</span></span>
```azurecli-interactive
az group create -l <Region Name (i.e. eastus)> --n <Resource Group Name>
```
##### <a name="creating-a-storage-account"></a><span data-ttu-id="da2dc-144">Создание учетной записи хранения</span><span class="sxs-lookup"><span data-stu-id="da2dc-144">Creating a Storage Account</span></span>

<span data-ttu-id="da2dc-145">Учетную запись хранения можно создать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-145">You can create a storage account using the [Azure Cloud Shell](https://shell.azure.com/bash) by running:</span></span>
```azurecli-interactive
az storage account create -n <Storage Account Name> -g <Existing Resource Group Name> -l <Region Name (i.e. eastus)> --sku <SKU i.e. Standard_LRS>
```
<span data-ttu-id="da2dc-146">Теперь выполните такую команду, чтобы получить ключ для учетной записи хранения (он потребуется для создания кластера):</span><span class="sxs-lookup"><span data-stu-id="da2dc-146">Now run the following command to get the key for your storage account (you will need this to create a cluster):</span></span>
```azurecli-interactive
az storage account keys list -n <Storage Account Name>
```
---
<span data-ttu-id="da2dc-147">Показанный ниже фрагмент кода .NET создает кластер Spark с двумя головными узлами и одним рабочим.</span><span class="sxs-lookup"><span data-stu-id="da2dc-147">The below .NET snippet creates a Spark cluster with 2 head nodes and 1 worker node.</span></span> <span data-ttu-id="da2dc-148">Задайте переменные, как описано в комментариях, и при необходимости измените другие параметры.</span><span class="sxs-lookup"><span data-stu-id="da2dc-148">Fill in the blank variables as explained in the comments and feel free to change other parameters to suit your specific needs.</span></span>

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

### <a name="get-cluster-details"></a><span data-ttu-id="da2dc-149">Получение сведений о кластере</span><span class="sxs-lookup"><span data-stu-id="da2dc-149">Get Cluster Details</span></span>

<span data-ttu-id="da2dc-150">Чтобы получить сведения о свойствах кластера, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-150">To get properties for a given cluster:</span></span>

```csharp
client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="da2dc-151">Пример</span><span class="sxs-lookup"><span data-stu-id="da2dc-151">Example</span></span>

<span data-ttu-id="da2dc-152">Чтобы убедиться в том, что вы создали кластер, можно использовать `get`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-152">You can use `get` to confirm that you have successfully created your cluster.</span></span>

```csharp
var myCluster = client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
Debug.WriteLine(myCluster.Name); //Prints the name of the cluster
Debug.WriteLine(myCluster.Id) //Prints the resource Id of the cluster
```

<span data-ttu-id="da2dc-153">Выходные данные должны выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="da2dc-153">The output should look like:</span></span>

```
<Cluster Name>
/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/<Resource Group Name>/providers/Microsoft.HDInsight/clusters/<Cluster Name>
```
> [!NOTE]
> <span data-ttu-id="da2dc-154">Возвращаемое значение `get`, хранимое в переменной `myCluster`, относится к типу `Microsoft.Azure.Management.HDInsight.ModelsCluster`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-154">The return value of `get`, stored in variable `myCluster`, is of type `Microsoft.Azure.Management.HDInsight.ModelsCluster`.</span></span> <span data-ttu-id="da2dc-155">См. [полный список свойств этого объекта](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).</span><span class="sxs-lookup"><span data-stu-id="da2dc-155">A full list of this object's properties can be found [here](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).</span></span>


### <a name="list-clusters"></a><span data-ttu-id="da2dc-156">Получение списка кластеров</span><span class="sxs-lookup"><span data-stu-id="da2dc-156">List Clusters</span></span>

#### <a name="list-clusters-under-the-subscription"></a><span data-ttu-id="da2dc-157">Получение списка кластеров в пределах подписки</span><span class="sxs-lookup"><span data-stu-id="da2dc-157">List Clusters Under The Subscription</span></span>

```csharp
client.Clusters.List();
```
#### <a name="list-clusters-by-resource-group"></a><span data-ttu-id="da2dc-158">Получение списка кластеров в пределах в группы ресурсов</span><span class="sxs-lookup"><span data-stu-id="da2dc-158">List Clusters By Resource Group</span></span>

```csharp
client.Clusters.ListByResourceGroup("<Resource Group Name>");
```
> [!NOTE]
> <span data-ttu-id="da2dc-159">`List()` и `ListByResourceGroup()` возвращают объект `IPage<Cluster>`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-159">Both `List()` and `ListByResourceGroup()` return an `IPage<Cluster>` object.</span></span> <span data-ttu-id="da2dc-160">Чтобы перейти на следующую страницу, можно вызвать `client.Clusters.ListNext("Next Page Link")`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-160">To get the next page, you can call `client.Clusters.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="da2dc-161">Команду можно повторять, пока для `NextPageLink` не будет получено значение `null`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="da2dc-161">This can be repeated until `NextPageLink` is `null`, as shown in the example below.</span></span>

#### <a name="example"></a><span data-ttu-id="da2dc-162">Пример</span><span class="sxs-lookup"><span data-stu-id="da2dc-162">Example</span></span>
<span data-ttu-id="da2dc-163">В следующем примере выводятся свойства всех кластеров в пределах текущей подписки:</span><span class="sxs-lookup"><span data-stu-id="da2dc-163">The following example prints the properties of all clusters for the current subscription:</span></span>

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

### <a name="delete-a-cluster"></a><span data-ttu-id="da2dc-164">Удаление кластера</span><span class="sxs-lookup"><span data-stu-id="da2dc-164">Delete a Cluster</span></span>

<span data-ttu-id="da2dc-165">Чтобы удалить кластер, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-165">To delete a cluster:</span></span>

```csharp
client.Clusters.Delete("<Resource Group Name>", "<Cluster Name>");
```

### <a name="update-cluster-tags"></a><span data-ttu-id="da2dc-166">Обновление тегов кластера</span><span class="sxs-lookup"><span data-stu-id="da2dc-166">Update Cluster Tags</span></span>

<span data-ttu-id="da2dc-167">Вы можете обновить теги кластера так:</span><span class="sxs-lookup"><span data-stu-id="da2dc-167">You can update the tags of a given cluster like so:</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(<Dictionary of Tags>));
```
#### <a name="example"></a><span data-ttu-id="da2dc-168">Пример</span><span class="sxs-lookup"><span data-stu-id="da2dc-168">Example</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(new Dictionary<string, string> { { "tag1Name", "tag1Value" }, { "tag2Name", "tag2Value" } }));
```

### <a name="resize-cluster"></a><span data-ttu-id="da2dc-169">Изменение размера кластера</span><span class="sxs-lookup"><span data-stu-id="da2dc-169">Resize Cluster</span></span>

<span data-ttu-id="da2dc-170">Вы можете изменить размер кластера, изменяя количество его рабочих узлов. Укажите новый размер, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="da2dc-170">You can resize a given cluster's number of worker nodes by specifying a new size like so:</span></span>

```csharp
client.Clusters.Resize("<Resource Group Name>", "<Cluster Name>", <Num of Worker Nodes (int)>)
```

## <a name="cluster-monitoring"></a><span data-ttu-id="da2dc-171">Мониторинг кластера</span><span class="sxs-lookup"><span data-stu-id="da2dc-171">Cluster Monitoring</span></span>

<span data-ttu-id="da2dc-172">Пакет Azure Management SDK для HDInsight также позволяет управлять мониторингом кластеров с помощью Operations Management Suite (OMS).</span><span class="sxs-lookup"><span data-stu-id="da2dc-172">The HDInsight Management SDK can also be used to manage monitoring on your clusters via the Operations Management Suite (OMS).</span></span>

### <a name="enable-oms-monitoring"></a><span data-ttu-id="da2dc-173">Включение мониторинга OMS</span><span class="sxs-lookup"><span data-stu-id="da2dc-173">Enable OMS Monitoring</span></span>

> [!NOTE]
> <span data-ttu-id="da2dc-174">Чтобы включить мониторинг OMS, требуется рабочая область Log Analytics.</span><span class="sxs-lookup"><span data-stu-id="da2dc-174">To enable OMS Monitoring, you must have an existing Log Analytics workspace.</span></span> <span data-ttu-id="da2dc-175">Если вы не создавали такую рабочую область, см. статью [Создание рабочей области Log Analytics на портале Azure](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).</span><span class="sxs-lookup"><span data-stu-id="da2dc-175">If you have not already created one, you can learn how to do that here: [Create a Log Analytics workspace in the Azure portal](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).</span></span>

<span data-ttu-id="da2dc-176">Чтобы включить мониторинг OMS в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-176">To enable OMS Monitoring on your cluster:</span></span>

```csharp
client.Extension.EnableMonitoring("<Resource Group Name", "Cluster Name", new ClusterMonitoringRequest(workspaceId: "<Workspace Id>"));
```

### <a name="view-status-of-oms-monitoring"></a><span data-ttu-id="da2dc-177">Просмотр состояния мониторинга OMS</span><span class="sxs-lookup"><span data-stu-id="da2dc-177">View Status Of OMS Monitoring</span></span>

<span data-ttu-id="da2dc-178">Чтобы узнать состояние мониторинга OMS в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-178">To get the status of OMS on your cluster:</span></span>

```csharp
client.Extension.GetMonitoringStatus("<Resource Group Name", "Cluster Name");
```

### <a name="disable-oms-monitoring"></a><span data-ttu-id="da2dc-179">Отключение мониторинга OMS</span><span class="sxs-lookup"><span data-stu-id="da2dc-179">Disable OMS Monitoring</span></span>

<span data-ttu-id="da2dc-180">Чтобы отключить мониторинг OMS в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-180">To disable OMS on your cluster:</span></span>

```csharp
client.Extension.DisableMonitoring("<Resource Group Name>", "<Cluster Name>");
```

## <a name="script-actions"></a><span data-ttu-id="da2dc-181">Элемент "Действия скрипта"</span><span class="sxs-lookup"><span data-stu-id="da2dc-181">Script Actions</span></span>

<span data-ttu-id="da2dc-182">В кластерах HDInsight поддерживается метод конфигурации с использованием, действий скриптов, который вызывает пользовательские скрипты для настройки кластера.</span><span class="sxs-lookup"><span data-stu-id="da2dc-182">HDInsight provides a configuration method called script actions that invokes custom scripts to customize the cluster.</span></span>
> [!NOTE]
> <span data-ttu-id="da2dc-183">Дополнительные сведения о действиях скриптов см. в статье [Настройка кластеров HDInsight под управлением Linux с помощью действий сценариев](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="da2dc-183">More information on how to use script actions can be found here: [Customize Linux-based HDInsight clusters using script actions](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)</span></span>

### <a name="execute-script-actions"></a><span data-ttu-id="da2dc-184">Выполнение действий скриптов</span><span class="sxs-lookup"><span data-stu-id="da2dc-184">Execute Script Actions</span></span>

<span data-ttu-id="da2dc-185">Вы можете выполнить действия скриптов в кластере так:</span><span class="sxs-lookup"><span data-stu-id="da2dc-185">You can execute script actions on a given cluster like so:</span></span>

```csharp
var scriptAction1 = new RuntimeScriptAction("<Script Name>", "<URL To Script>", <List<string> of roles>); //valid roles are "headnode", "workernode", "zookeepernode", and "edgenode"

client.Clusters.ExecuteScriptActions("<Resource Group Name>", "<Cluster Name>", new List<RuntimeScriptAction> { scriptAction1 }, <persistOnSuccess (bool)>); //add more RuntimeScriptActions to the list to execute multiple scripts
```

### <a name="delete-script-action"></a><span data-ttu-id="da2dc-186">Удаление действий скриптов</span><span class="sxs-lookup"><span data-stu-id="da2dc-186">Delete Script Action</span></span>

<span data-ttu-id="da2dc-187">Чтобы удалить сохраненные действия скриптов в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-187">To delete a specified persisted script action on a given cluster:</span></span>

```csharp
client.ScriptActions.Delete("<Resource Group Name>", "<Cluster Name>", "<Script Name>");
```

### <a name="list-persisted-script-actions"></a><span data-ttu-id="da2dc-188">Получение списка сохраненных действий скриптов</span><span class="sxs-lookup"><span data-stu-id="da2dc-188">List Persisted Script Actions</span></span>

> [!NOTE]
> <span data-ttu-id="da2dc-189">`ListPersistedScripts()` и `List()` возвращают объект `IPage<RuntimeScriptActionDetail>`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-189">`ListPersistedScripts()` and `List()` return an `IPage<RuntimeScriptActionDetail>` object.</span></span> <span data-ttu-id="da2dc-190">Чтобы перейти на следующую страницу, можно вызвать `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` или `client.ScriptExecutionHistory.ListNext("Next Page Link")`.</span><span class="sxs-lookup"><span data-stu-id="da2dc-190">To get the next page, you can call `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` or `client.ScriptExecutionHistory.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="da2dc-191">Команду можно повторять, пока для `NextPageLink` не будет получено значение `null`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="da2dc-191">This can be repeated until `NextPageLink` is `null`, as shown in the examples below.</span></span>

<span data-ttu-id="da2dc-192">Чтобы получить список всех сохраненных действий скриптов в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-192">To list all persisted script actions for the specified cluster:</span></span>
```csharp
client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="da2dc-193">Пример</span><span class="sxs-lookup"><span data-stu-id="da2dc-193">Example</span></span>

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

### <a name="list-all-scripts-execution-history"></a><span data-ttu-id="da2dc-194">Просмотр журнала выполнения всех скриптов</span><span class="sxs-lookup"><span data-stu-id="da2dc-194">List All Scripts' Execution History</span></span>

<span data-ttu-id="da2dc-195">Чтобы получить журнал выполнения всех скриптов в кластере, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="da2dc-195">To list all scripts' execution history for the specified cluster:</span></span>

```csharp
client.script_execution_history.list("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="da2dc-196">Пример</span><span class="sxs-lookup"><span data-stu-id="da2dc-196">Example</span></span>

<span data-ttu-id="da2dc-197">В этом примере выводятся сведения обо всех выполнявшихся скриптах.</span><span class="sxs-lookup"><span data-stu-id="da2dc-197">This example prints all the details for all past script executions.</span></span>

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

## <a name="jobs"></a><span data-ttu-id="da2dc-198">Задания</span><span class="sxs-lookup"><span data-stu-id="da2dc-198">Jobs</span></span>

<span data-ttu-id="da2dc-199">Используйте пакет SDK Azure HDInsight для .NET, чтобы создавать и отслеживать задания, а также управлять ими в кластере Hadoop.</span><span class="sxs-lookup"><span data-stu-id="da2dc-199">Use the Azure HDInsight job SDK for .NET to create, manage, and monitor jobs on a Hadoop cluster.</span></span>

### <a name="sdk-installation"></a><span data-ttu-id="da2dc-200">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="da2dc-200">SDK Installation</span></span>

<span data-ttu-id="da2dc-201">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) непосредственно из [консоли диспетчера пакетов][PackageManager] или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="da2dc-201">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="da2dc-202">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da2dc-202">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

### <a name="code-example"></a><span data-ttu-id="da2dc-203">Пример кода</span><span class="sxs-lookup"><span data-stu-id="da2dc-203">Code Example</span></span>

<span data-ttu-id="da2dc-204">В этом примере выполняется задание Hive в кластере Hadoop.</span><span class="sxs-lookup"><span data-stu-id="da2dc-204">This example runs a Hive job in a Hadoop cluster.</span></span>

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

### <a name="samples"></a><span data-ttu-id="da2dc-205">Примеры</span><span class="sxs-lookup"><span data-stu-id="da2dc-205">Samples</span></span>

- [<span data-ttu-id="da2dc-206">Выполнение запросов Hive с помощью пакета SDK HDInsight для .NET</span><span class="sxs-lookup"><span data-stu-id="da2dc-206">Run Hive jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [<span data-ttu-id="da2dc-207">Выполнение заданий Pig с помощью пакета SDK для .NET для Hadoop в HDInsight</span><span class="sxs-lookup"><span data-stu-id="da2dc-207">Run Pig jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [<span data-ttu-id="da2dc-208">Отправка заданий Hadoop в HDInsight</span><span class="sxs-lookup"><span data-stu-id="da2dc-208">More jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)
