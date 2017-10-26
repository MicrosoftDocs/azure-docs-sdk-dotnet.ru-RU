---
title: "Библиотеки службы приложений Azure для .NET"
description: "Справочник по библиотекам службы приложений Azure для .NET"
keywords: Azure, .NET, SDK, API, web apps, app service, mobile, asp.net
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 9f54fb6aca934f07c6ae23a4ae40dc29fa48ec8b
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
---
# <a name="azure-app-service-libraries-for-net"></a><span data-ttu-id="c8e2f-104">Библиотеки службы приложений Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="c8e2f-104">Azure App Service libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="c8e2f-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c8e2f-105">Overview</span></span>

<span data-ttu-id="c8e2f-106">[Служба приложений Azure](/azure/app-service/app-service-value-prop-what-is) позволяет развертывать и масштабировать веб-сайты, веб-приложения, службы и интерфейсы REST API.</span><span class="sxs-lookup"><span data-stu-id="c8e2f-106">[Azure App Service](/azure/app-service/app-service-value-prop-what-is) allows you to deploy and scale websites, web applications, services, and REST APIs.</span></span>

## <a name="management-api"></a><span data-ttu-id="c8e2f-107">API управления</span><span class="sxs-lookup"><span data-stu-id="c8e2f-107">Management API</span></span>

<span data-ttu-id="c8e2f-108">Развертывайте и масштабируйте элементы, размещенные в службе приложений Azure, а также управляйте ими с помощью API управления.</span><span class="sxs-lookup"><span data-stu-id="c8e2f-108">Deploy, manage, and scale elements hosted in Azure App Service with the management API.</span></span>

<span data-ttu-id="c8e2f-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="c8e2f-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="c8e2f-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8e2f-110">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="c8e2f-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="c8e2f-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a><span data-ttu-id="c8e2f-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="c8e2f-112">Code Example</span></span>

<span data-ttu-id="c8e2f-113">Создание веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="c8e2f-113">Create a new web app.</span></span>

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
> [<span data-ttu-id="c8e2f-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="c8e2f-114">Explore the Management APIs</span></span>](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a><span data-ttu-id="c8e2f-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="c8e2f-115">Samples</span></span>

* <span data-ttu-id="c8e2f-116">[Manage your web apps with the .NET SDK for Azure](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-manage/) (Управление веб-приложениями с помощью пакета SDK .NET для Azure)</span><span class="sxs-lookup"><span data-stu-id="c8e2f-116">[Manage your web apps with the .NET SDK for Azure](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-manage/)</span></span>
* <span data-ttu-id="c8e2f-117">[ASP.NET sample for Azure App Service](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-get-started/) (Пример ASP.NET для службы приложений Azure)</span><span class="sxs-lookup"><span data-stu-id="c8e2f-117">[ASP.NET sample for Azure App Service](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-get-started/)</span></span>

<span data-ttu-id="c8e2f-118">Просмотрите [полный список](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=app%20service) примеров кода для службы приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="c8e2f-118">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=app%20service) of Azure App Service samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package