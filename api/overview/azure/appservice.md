---
title: Библиотеки службы приложений Azure для .NET
description: Справочник по библиотекам службы приложений Azure для .NET
keywords: Azure, .NET, SDK, API, web apps, app service, mobile, asp.net
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 0fee28930dff5075cdd84fe3cb88850e07bc6ccb
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065804"
---
# <a name="azure-app-service-libraries-for-net"></a><span data-ttu-id="dae82-104">Библиотеки службы приложений Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="dae82-104">Azure App Service libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="dae82-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="dae82-105">Overview</span></span>

<span data-ttu-id="dae82-106">[Служба приложений Azure](/azure/app-service/app-service-value-prop-what-is) позволяет развертывать и масштабировать веб-сайты, веб-приложения, службы и интерфейсы REST API.</span><span class="sxs-lookup"><span data-stu-id="dae82-106">[Azure App Service](/azure/app-service/app-service-value-prop-what-is) allows you to deploy and scale websites, web applications, services, and REST APIs.</span></span>

## <a name="management-api"></a><span data-ttu-id="dae82-107">API управления</span><span class="sxs-lookup"><span data-stu-id="dae82-107">Management API</span></span>

<span data-ttu-id="dae82-108">Развертывайте и масштабируйте элементы, размещенные в службе приложений Azure, а также управляйте ими с помощью API управления.</span><span class="sxs-lookup"><span data-stu-id="dae82-108">Deploy, manage, and scale elements hosted in Azure App Service with the management API.</span></span>

<span data-ttu-id="dae82-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="dae82-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="dae82-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dae82-110">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="dae82-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="dae82-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a><span data-ttu-id="dae82-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="dae82-112">Code Example</span></span>

<span data-ttu-id="dae82-113">Создание веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="dae82-113">Create a new web app.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.AppService.Fluent;
*/

IWebApp app1 = azure.WebApps
    .Define("MyUniqueWebAddress")
    .WithRegion(Region.USWest)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewWindowsPlan(PricingTier.StandardS1)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="dae82-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="dae82-114">Explore the Management APIs</span></span>](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a><span data-ttu-id="dae82-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="dae82-115">Samples</span></span>

* <span data-ttu-id="dae82-116">[Manage your web apps with the .NET SDK for Azure](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-manage/) (Управление веб-приложениями с помощью пакета SDK .NET для Azure)</span><span class="sxs-lookup"><span data-stu-id="dae82-116">[Manage your web apps with the .NET SDK for Azure](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-manage/)</span></span>
* <span data-ttu-id="dae82-117">[ASP.NET sample for Azure App Service](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-get-started/) (Пример ASP.NET для службы приложений Azure)</span><span class="sxs-lookup"><span data-stu-id="dae82-117">[ASP.NET sample for Azure App Service](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-get-started/)</span></span>

<span data-ttu-id="dae82-118">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) примеров кода для службы приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="dae82-118">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) of Azure App Service samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package