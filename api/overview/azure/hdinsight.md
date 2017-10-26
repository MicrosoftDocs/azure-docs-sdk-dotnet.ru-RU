---
title: "Библиотеки Azure HDInsight для .NET"
description: "Справочник по библиотекам Azure HDInsight для .NET"
keywords: Azure, .NET, SDK, API, HDInsight
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: hd-insight
ms.custom: devcenter, svc-overview
ms.openlocfilehash: da9023ab4e6106754d48acb31cda58cdb358f5cb
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2017
---
# <a name="azure-hdinsight-libraries-for-net"></a>Библиотеки Azure HDInsight для .NET

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
