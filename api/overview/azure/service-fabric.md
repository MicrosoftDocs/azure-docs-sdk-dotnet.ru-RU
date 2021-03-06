---
title: Библиотеки Azure Service Fabric для .NET
description: Справочник по библиотекам Azure Service Fabric для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: service-fabric
ms.openlocfilehash: 064f95a4eae3182c4ac5b31779a5d22b592a75b2
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190767"
---
# <a name="azure-service-fabric-libraries-for-net"></a>Библиотеки Azure Service Fabric для .NET

## <a name="overview"></a>Обзор

Azure Service Fabric — это платформа распределенных систем, которая дает возможность не только легко упаковывать и развертывать масштабируемые надежные микрослужбы и контейнеры, но и управлять ими.  Дополнительные сведения см. в [документации по Azure Service Fabric](/azure/service-fabric/).

## <a name="client-library"></a>Клиентская библиотека

Для взаимодействия с существующим кластером Service Fabric используйте клиентскую библиотеку Service Fabric.  Библиотека содержит три категории API-интерфейсов:

* API **клиента** позволяют администрировать, масштабировать и перезапускать кластер, а также развертывать пакеты приложений.
* API **среды выполнения** используются для взаимодействия запущенного приложения с кластером, в котором оно размещено.
* **Общие** API-интерфейсы содержат типы, используемые как в API **клиента**, так и в API **среды выполнения**.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.ServiceFabric) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-examples"></a>Примеры кода

Следующий пример копирует пакет приложения в хранилище образов, подготавливает тип приложения и создает экземпляр приложения с помощью API-интерфейсов **клиента** Service Fabric.

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
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/servicefabric/client)

В этом примере для обновления [надежной коллекции](/azure/service-fabric/service-fabric-reliable-services-reliable-collections) в среде выполнения используется API **среды выполнения** и **общий** API Service Fabric из размещенного приложения.

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
> [Ознакомление с API среды выполнения](/dotnet/api/overview/azure/servicefabric/runtime)

> [!div class="nextstepaction"]
> [Ознакомление с общими API](/dotnet/api/overview/azure/servicefabric/common)

## <a name="management-library"></a>Библиотека управления

Библиотека управления используется для создания, обновления и удаления кластеров Service Fabric.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ServiceFabric
```

```bash
dotnet add package Microsoft.Azure.Management.ServiceFabric
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/servicefabric/management)

## <a name="samples"></a>Примеры

* [Развертывание и удаление приложений с помощью FabricClient](/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
