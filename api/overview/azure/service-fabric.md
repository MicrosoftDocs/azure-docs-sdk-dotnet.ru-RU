---
title: "Библиотеки Azure Service Fabric для .NET"
description: "Справочник по библиотекам Azure Service Fabric для .NET"
keywords: Azure, .NET, SDK, API, Service Fabric
author: spboyer
ms.author: casoper
manager: douge
ms.date: 07/07/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: c708ae06fa4b5165e3f615abf636b11bfd95cd3b
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-service-fabric-libraries-for-net"></a><span data-ttu-id="4ca8c-104">Библиотеки Azure Service Fabric для .NET</span><span class="sxs-lookup"><span data-stu-id="4ca8c-104">Azure Service Fabric libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="4ca8c-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="4ca8c-105">Overview</span></span>

<span data-ttu-id="4ca8c-106">Azure Service Fabric — это платформа распределенных систем, которая дает возможность не только легко упаковывать и развертывать масштабируемые надежные микрослужбы и контейнеры, но и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

## <a name="client-library"></a><span data-ttu-id="4ca8c-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="4ca8c-107">Client library</span></span>

<span data-ttu-id="4ca8c-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.ServiceFabric) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4ca8c-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4ca8c-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ca8c-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-example"></a><span data-ttu-id="4ca8c-110">Пример кода</span><span class="sxs-lookup"><span data-stu-id="4ca8c-110">Code Example</span></span>

<span data-ttu-id="4ca8c-111">Следующий пример копирует пакет приложения в хранилище образов, подготавливает тип приложения и создает экземпляр приложения.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-111">The following example copies an application package to the image store, provisions the application type, and creates an application instance.</span></span>

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
> [<span data-ttu-id="4ca8c-112">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="4ca8c-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicefabric/client)

## <a name="samples"></a><span data-ttu-id="4ca8c-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="4ca8c-113">Samples</span></span>

* [<span data-ttu-id="4ca8c-114">Развертывание и удаление приложений с помощью FabricClient</span><span class="sxs-lookup"><span data-stu-id="4ca8c-114">Deploy and remove applications using FabricClient</span></span>](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
