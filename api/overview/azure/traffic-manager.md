---
title: "Библиотеки диспетчера трафика Azure для .NET"
description: "Справочник по библиотекам диспетчера трафика Azure для .NET"
keywords: Azure, .NET, SDK, API, Traffic Manager
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: traffic-manager
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 491a8b12146882b32f7fc6d85ad58cca1d00fd04
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
---
# <a name="azure-traffic-manager-libraries-for-net"></a><span data-ttu-id="fbb73-104">Библиотеки диспетчера трафика Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="fbb73-104">Azure Traffic Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="fbb73-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="fbb73-105">Overview</span></span>

<span data-ttu-id="fbb73-106">Диспетчер трафика Microsoft Azure позволяет управлять распределением пользовательского трафика между конечными точками службы в разных центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="fbb73-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="fbb73-107">К конечным точкам службы, поддерживаемым диспетчером трафика Azure, относятся виртуальные машины, веб-приложения и облачные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="fbb73-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="fbb73-108">Можно также использовать диспетчер трафика Azure для внешних конечных точек, не относящихся к среде Azure.</span><span class="sxs-lookup"><span data-stu-id="fbb73-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="fbb73-109">См. дополнительные сведения о [диспетчере трафика Azure](/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="fbb73-109">Learn more about [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview).</span></span>  

## <a name="management-library"></a><span data-ttu-id="fbb73-110">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="fbb73-110">Management library</span></span>

<span data-ttu-id="fbb73-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="fbb73-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="fbb73-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fbb73-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="fbb73-113">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="fbb73-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a><span data-ttu-id="fbb73-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="fbb73-114">Samples</span></span>

<span data-ttu-id="fbb73-115">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="fbb73-115">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package