---
title: Библиотеки пакетной службы Azure для .NET
description: Справочник по библиотекам пакетной службы для .NET
keywords: Azure, .NET, SDK, API, Batch
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: batch
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 79ca70e5d0f3d5555c8a691da6dbcc1e6a55ab0b
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2017
ms.locfileid: "23487267"
---
# <a name="azure-batch-libraries-for-net"></a>Библиотеки пакетной службы Azure для .NET

Пакетная служба Azure — это служба платформы, которая позволяет эффективно работать с приложениями для крупномасштабных параллельных и высокопроизводительных вычислений (HPC) в облаке. Пакетная служба Azure планирует запуск ресурсоемких вычислительных задач в управляемой коллекции виртуальных машин и автоматически масштабирует вычислительные ресурсы, учитывая требования заданий.

С помощью пакетной службы Azure вы можете легко определять вычислительные ресурсы Azure, необходимые для параллельного выполнения приложений в нужном масштабе. Вам не нужно вручную создавать и настраивать кластер высокопроизводительных вычислений (HPC), отдельные виртуальные машины, виртуальные сети или сложную инфраструктуру планировщика задач и заданий, а также управлять всеми этими ресурсами. Пакетная служба Azure автоматизирует или упрощает выполнение этих задач.

Узнайте больше о том, как [выполнять реальные параллельные рабочие нагрузки с использованием пакетной службы](/azure/batch/batch-technical-overview). Также ознакомьтесь со статьей [Приступая к созданию решений с помощью клиентской библиотеки пакетной службы для .NET](/azure/batch/batch-dotnet-get-started). Узнайте, как [управлять учетными записями и квотами пакетной службы с помощью клиентской библиотеки .NET для управления пакетной службой](/azure/batch/batch-management-dotnet).

## <a name="client-library"></a>Клиентская библиотека

Используйте клиентскую библиотеку для выполнения параллельных рабочих нагрузок с использованием пакетной службы.

Установите [пакет NuGet](https://www.nuget.org/packages/Azure.Batch) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Azure.Batch
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Azure.Batch
```

### <a name="example"></a>Пример

В примере ниже клиентский пакет SDK используется для создания задания, выполняющегося в пакетной службе Azure.

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
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/batch/client)

## <a name="management-library"></a>Библиотека управления

С помощью этих библиотек управления можно программно управлять учетными записями пакетной службы, квотами и пакетами приложений.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Batch
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.Batch
```

### <a name="example"></a>Пример

В примере ниже извлекается квота для подписки, создается учетная запись и повторно создается первичный ключ учетной записи.

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
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/batch/management)

## <a name="samples"></a>Примеры

* [Примеры клиента пакетной службы и управляющего пакета SDK для .NET](https://github.com/Azure/azure-batch-samples/tree/master/CSharp)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
