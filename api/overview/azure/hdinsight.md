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
# <a name="azure-hdinsight-net-sdk"></a>Пакет SDK .NET для Azure HDInsight

## <a name="azure-hdinsight-libraries-for-net-2x"></a>Библиотеки Azure HDInsight для .NET 2.X

## <a name="overview"></a>Обзор

Пакет SDK для .NET для службы HDInsight предоставляет классы, связанные с созданием, настройкой, отправкой и мониторингом заданий Hadoop, которыми управляет служба Azure HDInsight. Помимо этого он предоставляет классы для управления подписками Azure с помощью службы HDInsight и настройки кластеров, учетных записей хранения и других ресурсов, связанных с кластерами HDInsight, управляемых с использованием подписки Azure.

## <a name="management-libraries"></a>Библиотеки управления

### <a name="jobs"></a>Задания

Используйте клиентский пакет SDK для Azure HDInsight, чтобы создавать и отслеживать задания, а также управлять ими в кластере Hadoop. 

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a>Пример кода

В этом примере выполняется задание Hive в кластере Hadoop.

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

### <a name="hdinsight"></a>HDInsight

Используйте пакет SDK управления для Azure HDInsight, чтобы создавать, запускать, останавливать и масштабировать кластеры Hadoop, а также управлять ими.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a>Пример кода

В этом примере в HDInsight создается кластер Hadoop под управлением Linux. Кластер содержит два узла и использует хранилище BLOB-объектов Azure.

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
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a>Примеры

- [Создание кластеров под управлением Linux в HDInsight с помощью пакета SDK для .NET](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [Управление кластерами Hadoop в HDInsight с помощью пакета SDK для .NET](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [Выполнение запросов Hive с помощью пакета SDK HDInsight для .NET](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [Выполнение заданий Pig с помощью пакета SDK для .NET для Hadoop в HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [Отправка заданий Hadoop в HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) примеров кода для базы данных SQL Azure.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package

## <a name="hdinsight-net-management-sdk-3x-preview"></a>Пакет Azure Management SDK .NET для HDInsight 3.X (предварительная версия)

## <a name="overview"></a>Обзор

Пакет SDK .NET для HDInsight предоставляет классы и методы для управления кластерами HDInsight. Пакет также поддерживает операции создания, удаления, обновления, получения списков, масштабирования, выполнения скриптов, мониторинга, получения свойства кластеров HDInsight и т. д.

## <a name="prerequisites"></a>Предварительные требования

* Учетная запись Azure. Если у вас ее нет, [получите бесплатную пробную версию](https://azure.microsoft.com/free/).
* [Visual Studio](https://visualstudio.microsoft.com/downloads/)

## <a name="sdk-installation"></a>Установка пакета SDK

В проекте Visual Studio откройте консоль диспетчера пакетов, выбрав **Средства**, **Диспетчер пакетов NuGet**, **Консоль диспетчера пакетов**.

В консоли диспетчера пакетов выполните такие команды:

```
  Install-Package Microsoft.Azure.Management.HDInsight -Version 3.1.0-preview
  Install-Package Microsoft.Azure.Management.Fluent
  Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

## <a name="authentication"></a>Authentication

Для использования пакета SDK нужно выполнить аутентификацию с помощью подписки Azure.  Ниже описано, как создать субъект-службу и использовать его для аутентификации. После этого вы получите экземпляр `HDInsightManagementClient`, в котором доступны различные методы (описанные далее) для операций управления.

> [!NOTE]
> Кроме описанного выше, есть и другие методы аутентификации, которые могут оказаться удобнее для вас. Дополнительные сведения см. в статье [Аутентификация с использованием библиотек Azure для .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)

### <a name="authentication-example-using-a-service-principal"></a>Пример аутентификации с помощью субъекта-службы

Сначала войдите в [Azure Cloud Shell](https://shell.azure.com/bash). Убедитесь, что вы используете подписку, в которой будет создан субъект-служба. 

```azurecli-interactive
az account show
```

Сведения о подписке отображаются в формате JSON.

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

Если вы вошли не в ту подписку, выполните такую команду, чтобы выбрать правильную подписку: 
```azurecli-interactive
az account set -s <name or ID of subscription>
```

> [!IMPORTANT]
> Если вы еще не зарегистрировали поставщик ресурсов HDInsight с помощью другого метода (например, создав кластер HDInsight на портале Azure), вам необходимо это сделать, прежде чем выполнять аутентификацию. Это можно сделать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:
>```azurecli-interactive
>az provider register --namespace Microsoft.HDInsight
>```

Создайте субъект-службу, выбрав имя и выполнив такую команду:

```azurecli-interactive
az ad sp create-for-rbac --name <Service Principal Name> --sdk-auth
```

Сведения о субъекте-службе отображаются в виде JSON.

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
Скопируйте фрагмент кода ниже и задайте в качестве значений `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET` и `SUBSCRIPTION_ID` строки из JSON-файла, возвращенного после выполнения команды для создания субъекта-службы.

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


## <a name="cluster-management"></a>Управление кластерами

> [!NOTE]
> В этом разделе предполагается, что вы уже выполнили аутентификацию, создали экземпляр `HDInsightManagementClient` и сохранили его в переменной с именем `client`. Инструкции по выполнению аутентификации и получению `HDInsightManagementClient` см. в предыдущем разделе.

### <a name="create-a-cluster"></a>Создание кластера

Кластер можно создать, вызвав `client.Clusters.Create()`. 

#### <a name="example"></a>Пример

В этом примере показано, как создать кластер Spark с двумя головными узлами и одним рабочим.

> [!NOTE]
> Сначала необходимо создать группу ресурсов и учетную запись хранения, как описано далее. Если они уже созданы, следующие шаги можно пропустить.

##### <a name="creating-a-resource-group"></a>Создание группы ресурсов

Группу ресурсов можно создать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:
```azurecli-interactive
az group create -l <Region Name (i.e. eastus)> --n <Resource Group Name>
```
##### <a name="creating-a-storage-account"></a>Создание учетной записи хранения

Учетную запись хранения можно создать с помощью [Azure Cloud Shell](https://shell.azure.com/bash), выполнив такую команду:
```azurecli-interactive
az storage account create -n <Storage Account Name> -g <Existing Resource Group Name> -l <Region Name (i.e. eastus)> --sku <SKU i.e. Standard_LRS>
```
Теперь выполните такую команду, чтобы получить ключ для учетной записи хранения (он потребуется для создания кластера):
```azurecli-interactive
az storage account keys list -n <Storage Account Name>
```
---
Показанный ниже фрагмент кода .NET создает кластер Spark с двумя головными узлами и одним рабочим. Задайте переменные, как описано в комментариях, и при необходимости измените другие параметры.

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

### <a name="get-cluster-details"></a>Получение сведений о кластере

Чтобы получить сведения о свойствах кластера, выполните такую команду:

```csharp
client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a>Пример

Чтобы убедиться в том, что вы создали кластер, можно использовать `get`.

```csharp
var myCluster = client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
Debug.WriteLine(myCluster.Name); //Prints the name of the cluster
Debug.WriteLine(myCluster.Id) //Prints the resource Id of the cluster
```

Выходные данные должны выглядеть так:

```
<Cluster Name>
/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/<Resource Group Name>/providers/Microsoft.HDInsight/clusters/<Cluster Name>
```
> [!NOTE]
> Возвращаемое значение `get`, хранимое в переменной `myCluster`, относится к типу `Microsoft.Azure.Management.HDInsight.ModelsCluster`. См. [полный список свойств этого объекта](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).


### <a name="list-clusters"></a>Получение списка кластеров

#### <a name="list-clusters-under-the-subscription"></a>Получение списка кластеров в пределах подписки

```csharp
client.Clusters.List();
```
#### <a name="list-clusters-by-resource-group"></a>Получение списка кластеров в пределах в группы ресурсов

```csharp
client.Clusters.ListByResourceGroup("<Resource Group Name>");
```
> [!NOTE]
> `List()` и `ListByResourceGroup()` возвращают объект `IPage<Cluster>`. Чтобы перейти на следующую страницу, можно вызвать `client.Clusters.ListNext("Next Page Link")`. Команду можно повторять, пока для `NextPageLink` не будет получено значение `null`, как показано ниже.

#### <a name="example"></a>Пример
В следующем примере выводятся свойства всех кластеров в пределах текущей подписки:

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

### <a name="delete-a-cluster"></a>Удаление кластера

Чтобы удалить кластер, выполните такую команду:

```csharp
client.Clusters.Delete("<Resource Group Name>", "<Cluster Name>");
```

### <a name="update-cluster-tags"></a>Обновление тегов кластера

Вы можете обновить теги кластера так:

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(<Dictionary of Tags>));
```
#### <a name="example"></a>Пример

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(new Dictionary<string, string> { { "tag1Name", "tag1Value" }, { "tag2Name", "tag2Value" } }));
```

### <a name="resize-cluster"></a>Изменение размера кластера

Вы можете изменить размер кластера, изменяя количество его рабочих узлов. Укажите новый размер, как показано ниже:

```csharp
client.Clusters.Resize("<Resource Group Name>", "<Cluster Name>", <Num of Worker Nodes (int)>)
```

## <a name="cluster-monitoring"></a>Мониторинг кластера

Пакет Azure Management SDK для HDInsight также позволяет управлять мониторингом кластеров с помощью Operations Management Suite (OMS).

### <a name="enable-oms-monitoring"></a>Включение мониторинга OMS

> [!NOTE]
> Чтобы включить мониторинг OMS, требуется рабочая область Log Analytics. Если вы не создавали такую рабочую область, см. статью [Создание рабочей области Log Analytics на портале Azure](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).

Чтобы включить мониторинг OMS в кластере, выполните такую команду:

```csharp
client.Extension.EnableMonitoring("<Resource Group Name", "Cluster Name", new ClusterMonitoringRequest(workspaceId: "<Workspace Id>"));
```

### <a name="view-status-of-oms-monitoring"></a>Просмотр состояния мониторинга OMS

Чтобы узнать состояние мониторинга OMS в кластере, выполните такую команду:

```csharp
client.Extension.GetMonitoringStatus("<Resource Group Name", "Cluster Name");
```

### <a name="disable-oms-monitoring"></a>Отключение мониторинга OMS

Чтобы отключить мониторинг OMS в кластере, выполните такую команду:

```csharp
client.Extension.DisableMonitoring("<Resource Group Name>", "<Cluster Name>");
```

## <a name="script-actions"></a>Элемент "Действия скрипта"

В кластерах HDInsight поддерживается метод конфигурации с использованием, действий скриптов, который вызывает пользовательские скрипты для настройки кластера.
> [!NOTE]
> Дополнительные сведения о действиях скриптов см. в статье [Настройка кластеров HDInsight под управлением Linux с помощью действий сценариев](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

### <a name="execute-script-actions"></a>Выполнение действий скриптов

Вы можете выполнить действия скриптов в кластере так:

```csharp
var scriptAction1 = new RuntimeScriptAction("<Script Name>", "<URL To Script>", <List<string> of roles>); //valid roles are "headnode", "workernode", "zookeepernode", and "edgenode"

client.Clusters.ExecuteScriptActions("<Resource Group Name>", "<Cluster Name>", new List<RuntimeScriptAction> { scriptAction1 }, <persistOnSuccess (bool)>); //add more RuntimeScriptActions to the list to execute multiple scripts
```

### <a name="delete-script-action"></a>Удаление действий скриптов

Чтобы удалить сохраненные действия скриптов в кластере, выполните такую команду:

```csharp
client.ScriptActions.Delete("<Resource Group Name>", "<Cluster Name>", "<Script Name>");
```

### <a name="list-persisted-script-actions"></a>Получение списка сохраненных действий скриптов

> [!NOTE]
> `ListPersistedScripts()` и `List()` возвращают объект `IPage<RuntimeScriptActionDetail>`. Чтобы перейти на следующую страницу, можно вызвать `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` или `client.ScriptExecutionHistory.ListNext("Next Page Link")`. Команду можно повторять, пока для `NextPageLink` не будет получено значение `null`, как показано ниже.

Чтобы получить список всех сохраненных действий скриптов в кластере, выполните такую команду:
```csharp
client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a>Пример

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

### <a name="list-all-scripts-execution-history"></a>Просмотр журнала выполнения всех скриптов

Чтобы получить журнал выполнения всех скриптов в кластере, выполните такую команду:

```csharp
client.script_execution_history.list("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a>Пример

В этом примере выводятся сведения обо всех выполнявшихся скриптах.

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
