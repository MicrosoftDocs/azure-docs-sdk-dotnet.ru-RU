---
title: Библиотеки службы приложений Azure для .NET
description: Справочник по библиотекам службы приложений Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: app-service
ms.openlocfilehash: 82f8eccfafd2f7b1cf1df1ce0f40212509ccddd3
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189997"
---
# <a name="azure-app-service-libraries-for-net"></a><span data-ttu-id="7e64a-103">Библиотеки службы приложений Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="7e64a-103">Azure App Service libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="7e64a-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="7e64a-104">Overview</span></span>

<span data-ttu-id="7e64a-105">[Служба приложений Azure](/azure/app-service/app-service-value-prop-what-is) позволяет развертывать и масштабировать веб-сайты, веб-приложения, службы и интерфейсы REST API.</span><span class="sxs-lookup"><span data-stu-id="7e64a-105">[Azure App Service](/azure/app-service/app-service-value-prop-what-is) allows you to deploy and scale websites, web applications, services, and REST APIs.</span></span>

## <a name="management-api"></a><span data-ttu-id="7e64a-106">API управления</span><span class="sxs-lookup"><span data-stu-id="7e64a-106">Management API</span></span>

<span data-ttu-id="7e64a-107">Развертывайте и масштабируйте элементы, размещенные в службе приложений Azure, а также управляйте ими с помощью API управления.</span><span class="sxs-lookup"><span data-stu-id="7e64a-107">Deploy, manage, and scale elements hosted in Azure App Service with the management API.</span></span>

<span data-ttu-id="7e64a-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="7e64a-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="7e64a-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e64a-109">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="7e64a-110">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="7e64a-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a><span data-ttu-id="7e64a-111">Пример кода</span><span class="sxs-lookup"><span data-stu-id="7e64a-111">Code Example</span></span>

<span data-ttu-id="7e64a-112">Создание веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="7e64a-112">Create a new web app.</span></span>

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
> [<span data-ttu-id="7e64a-113">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="7e64a-113">Explore the Management APIs</span></span>](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a><span data-ttu-id="7e64a-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="7e64a-114">Samples</span></span>

* <span data-ttu-id="7e64a-115">[Manage your web apps with the .NET SDK for Azure](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-manage/) (Управление веб-приложениями с помощью пакета SDK .NET для Azure)</span><span class="sxs-lookup"><span data-stu-id="7e64a-115">[Manage your web apps with the .NET SDK for Azure](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-manage/)</span></span>
* <span data-ttu-id="7e64a-116">[ASP.NET sample for Azure App Service](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-get-started/) (Пример ASP.NET для службы приложений Azure)</span><span class="sxs-lookup"><span data-stu-id="7e64a-116">[ASP.NET sample for Azure App Service](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-get-started/)</span></span>

<span data-ttu-id="7e64a-117">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) примеров кода для службы приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="7e64a-117">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) of Azure App Service samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package