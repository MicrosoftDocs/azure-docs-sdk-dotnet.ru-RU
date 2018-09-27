---
title: Библиотеки диспетчера трафика Azure для .NET
description: Справочник по библиотекам диспетчера трафика Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: traffic-manager
ms.openlocfilehash: a75b5c566496f73475d24d62288a00c7d5775168
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190827"
---
# <a name="azure-traffic-manager-libraries-for-net"></a><span data-ttu-id="b6beb-103">Библиотеки диспетчера трафика Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="b6beb-103">Azure Traffic Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b6beb-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="b6beb-104">Overview</span></span>

<span data-ttu-id="b6beb-105">Диспетчер трафика Microsoft Azure позволяет управлять распределением пользовательского трафика между конечными точками службы в разных центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="b6beb-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="b6beb-106">К конечным точкам службы, поддерживаемым диспетчером трафика Azure, относятся виртуальные машины, веб-приложения и облачные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="b6beb-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="b6beb-107">Можно также использовать диспетчер трафика Azure для внешних конечных точек, не относящихся к среде Azure.</span><span class="sxs-lookup"><span data-stu-id="b6beb-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="b6beb-108">См. дополнительные сведения о [диспетчере трафика Azure](/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="b6beb-108">Learn more about [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview).</span></span>  

## <a name="management-library"></a><span data-ttu-id="b6beb-109">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="b6beb-109">Management library</span></span>

<span data-ttu-id="b6beb-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="b6beb-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b6beb-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b6beb-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6beb-112">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="b6beb-112">Explore the management APIs</span></span>](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a><span data-ttu-id="b6beb-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="b6beb-113">Samples</span></span>

<span data-ttu-id="b6beb-114">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="b6beb-114">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package