---
title: "Библиотеки Azure Service Fabric для .NET"
description: "Справочник по библиотекам Azure Service Fabric для .NET"
keywords: Azure, .NET, SDK, API, Service Fabric
author: camsoper
ms.author: casoper
manager: douge
ms.date: 10/13/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: service-fabric
ms.openlocfilehash: c15da57ef44663ad0463ba76ffa3b6832774240f
ms.sourcegitcommit: a235826f194e938b094be3ed03d86f7e85bb4da6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="azure-service-fabric-libraries-for-net"></a><span data-ttu-id="a8f1b-104">Библиотеки Azure Service Fabric для .NET</span><span class="sxs-lookup"><span data-stu-id="a8f1b-104">Azure Service Fabric libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a8f1b-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="a8f1b-105">Overview</span></span>

<span data-ttu-id="a8f1b-106">Azure Service Fabric — это платформа распределенных систем, которая дает возможность не только легко упаковывать и развертывать масштабируемые надежные микрослужбы и контейнеры, но и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>  <span data-ttu-id="a8f1b-107">Дополнительные сведения см. в [документации по Azure Service Fabric](/azure/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="a8f1b-107">For more information, see the [Azure Service Fabric Documentation](/azure/service-fabric/).</span></span>

## <a name="client-library"></a><span data-ttu-id="a8f1b-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="a8f1b-108">Client library</span></span>

<span data-ttu-id="a8f1b-109">Для взаимодействия с существующим кластером Service Fabric используйте клиентскую библиотеку Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-109">Use the Service Fabric client library to interact with an existing Service Fabric cluster.</span></span>  <span data-ttu-id="a8f1b-110">Библиотека содержит три категории API-интерфейсов:</span><span class="sxs-lookup"><span data-stu-id="a8f1b-110">The library contains three categories of APIs:</span></span>

* <span data-ttu-id="a8f1b-111">API **клиента** позволяют администрировать, масштабировать и перезапускать кластер, а также развертывать пакеты приложений.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-111">**Client** APIs are used to manage, scale, and recycle the cluster, as well as deploy application packages.</span></span>
* <span data-ttu-id="a8f1b-112">API **среды выполнения** используются для взаимодействия запущенного приложения с кластером, в котором оно размещено.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-112">**Runtime** APIs are used for the running application to interact with its hosting cluster.</span></span>
* <span data-ttu-id="a8f1b-113">**Общие** API-интерфейсы содержат типы, используемые как в API **клиента**, так и в API **среды выполнения**.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-113">**Common** APIs contain types used in both **client** and **runtime** APIs.</span></span>

<span data-ttu-id="a8f1b-114">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.ServiceFabric) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="a8f1b-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a8f1b-115">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a8f1b-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-examples"></a><span data-ttu-id="a8f1b-116">Примеры кода</span><span class="sxs-lookup"><span data-stu-id="a8f1b-116">Code Examples</span></span>

<span data-ttu-id="a8f1b-117">Следующий пример копирует пакет приложения в хранилище образов, подготавливает тип приложения и создает экземпляр приложения с помощью API-интерфейсов **клиента** Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-117">The following example uses the Service Fabric **client** APIs to copy an application package to the image store, provisions the application type, and create an application instance.</span></span>

```csharp
/* Include these dependencies
using System.Fabric;
using System.Fabric.Description;
*/

// Connect to the cluster.
FabricClient fabricClient = new FabricClient(clusterConnection);

// Copy the application package to a location in the image store
fabricClient.ApplicationManager.CopyApplicationPackage(imageStoreConnectionString, packagePath, packagePathInImageStore);

// Provision the application.
fabricClient.ApplicationManager.ProvisionApplicationAsync(packagePathInImageStore).Wait();

//  Create the application instance.
ApplicationDescription appDesc = new ApplicationDescription(new Uri(appName), appType, appVersion);
fabricClient.ApplicationManager.CreateApplicationAsync(appDesc).Wait();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8f1b-118">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="a8f1b-118">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicefabric/client)

<span data-ttu-id="a8f1b-119">В этом примере для обновления [надежной коллекции](/azure/service-fabric/service-fabric-reliable-services-reliable-collections) в среде выполнения используется API **среды выполнения** и **общий** API Service Fabric из размещенного приложения.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-119">This example uses the Service Fabric **runtime** and **common** APIs from within a hosted application to update a [Reliable Collection](/azure/service-fabric/service-fabric-reliable-services-reliable-collections) at runtime.</span></span>

```csharp
using System.Fabric;
using Microsoft.ServiceFabric.Data.Collections;
using Microsoft.ServiceFabric.Services.Communication.Runtime;
using Microsoft.ServiceFabric.Services.Runtime;

/// <summary>
/// This is the main entry point for your service replica.
/// This method executes when this replica of your service becomes primary and has write status.
/// </summary>
/// <param name="cancellationToken">Canceled when Service Fabric needs to shut down this service replica.</param>
protected override async Task RunAsync(CancellationToken cancellationToken)
{
    var myDictionary = await this.StateManager.GetOrAddAsync<IReliableDictionary<string, long>>("myDictionary");
    while (true)
    {
        cancellationToken.ThrowIfCancellationRequested();
        using (var tx = this.StateManager.CreateTransaction())
        {
            var result = await myDictionary.TryGetValueAsync(tx, "Counter");
            await myDictionary.AddOrUpdateAsync(tx, "Counter", 0, (key, value) => ++value);

            // If an exception is thrown before calling CommitAsync, the transaction aborts, all changes are
            // discarded, and nothing is saved to the secondary replicas.
            await tx.CommitAsync();
        }
        await Task.Delay(TimeSpan.FromSeconds(1), cancellationToken);
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8f1b-120">Ознакомление с API среды выполнения</span><span class="sxs-lookup"><span data-stu-id="a8f1b-120">Explore the runtime APIs</span></span>](/dotnet/api/overview/azure/servicefabric/runtime)

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8f1b-121">Ознакомление с общими API</span><span class="sxs-lookup"><span data-stu-id="a8f1b-121">Explore the common APIs</span></span>](/dotnet/api/overview/azure/servicefabric/common)

## <a name="management-library"></a><span data-ttu-id="a8f1b-122">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="a8f1b-122">Management Library</span></span>

<span data-ttu-id="a8f1b-123">Библиотека управления используется для создания, обновления и удаления кластеров Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="a8f1b-123">The management library is used to create, update, and delete Service Fabric clusters.</span></span>

<span data-ttu-id="a8f1b-124">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="a8f1b-124">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a8f1b-125">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a8f1b-125">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceFabric
```

```bash
dotnet add package Microsoft.Azure.Management.ServiceFabric
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8f1b-126">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="a8f1b-126">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicefabric/management)

## <a name="samples"></a><span data-ttu-id="a8f1b-127">Примеры</span><span class="sxs-lookup"><span data-stu-id="a8f1b-127">Samples</span></span>

* [<span data-ttu-id="a8f1b-128">Развертывание и удаление приложений с помощью FabricClient</span><span class="sxs-lookup"><span data-stu-id="a8f1b-128">Deploy and remove applications using FabricClient</span></span>](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
