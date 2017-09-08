---
title: "Библиотеки Azure CDN для .NET"
description: "Справочник по библиотекам Azure CDN для .NET"
keywords: Azure, .NET, SDK, API, CDN
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/31/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cdn
ms.openlocfilehash: 1582f85c6e25a973fdf0294afb4393e6622e92a0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-cdn-libraries-for-net"></a><span data-ttu-id="cbf3a-104">Библиотеки Azure CDN для .NET</span><span class="sxs-lookup"><span data-stu-id="cbf3a-104">Azure CDN libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="cbf3a-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="cbf3a-105">Overview</span></span>

<span data-ttu-id="cbf3a-106">Сеть доставки содержимого (CDN) Azure кэширует статическое веб-содержимое в стратегически расположенных точках. Это позволяет обеспечить максимальную пропускную способность для доставки содержимого пользователям.</span><span class="sxs-lookup"><span data-stu-id="cbf3a-106">The Azure Content Delivery Network (CDN) caches static web content at strategically placed locations to provide maximum throughput for delivering content to users.</span></span> <span data-ttu-id="cbf3a-107">CDN предлагает разработчикам глобальное решение для доставки содержимого с высокой пропускной способностью путем кэширования содержимого на физических узлах по всему миру.</span><span class="sxs-lookup"><span data-stu-id="cbf3a-107">The CDN offers developers a global solution for delivering high-bandwidth content by caching the content at physical nodes across the world.</span></span>

<span data-ttu-id="cbf3a-108">Дополнительную информацию по Azure CDN см. в статье [Общие сведения о сети доставки содержимого (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview).</span><span class="sxs-lookup"><span data-stu-id="cbf3a-108">To learn more about Azure CDN, see [Overview of the Azure Content Delivery Network](https://docs.microsoft.com/azure/cdn/cdn-overview).</span></span>


## <a name="management-library"></a><span data-ttu-id="cbf3a-109">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="cbf3a-109">Management library</span></span>

<span data-ttu-id="cbf3a-110">С помощью библиотеки Azure CDN для .NET можно автоматизировать создание профилей и конечных точек CDN и управление ими.</span><span class="sxs-lookup"><span data-stu-id="cbf3a-110">You can use the Azure CDN Library for .NET to automate creation and management of CDN profiles and endpoints.</span></span> 

<span data-ttu-id="cbf3a-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="cbf3a-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="cbf3a-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cbf3a-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a><span data-ttu-id="cbf3a-113">Пример</span><span class="sxs-lookup"><span data-stu-id="cbf3a-113">Example</span></span>

<span data-ttu-id="cbf3a-114">В этом примере создается профиль CDN с новой конечной точкой, которая указывает на `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="cbf3a-114">This example creates a new CDN profile with a new endpoint pointed to `www.contoso.com`.</span></span>

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.Cdn.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

ICdnProfile profileDefinition = azure.CdnProfiles.Define("CdnProfileName")
    .WithRegion(Region.USCentral)
    .WithExistingResourceGroup("ResourceGroupName")
    .WithStandardVerizonSku()
    .WithNewEndpoint("www.contoso.com")
    .Create();

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="cbf3a-115">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="cbf3a-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a><span data-ttu-id="cbf3a-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="cbf3a-116">Samples</span></span>

* [<span data-ttu-id="cbf3a-117">Getting Started with Cdn - Manage Cdn - in .Net</span><span class="sxs-lookup"><span data-stu-id="cbf3a-117">Getting started with CDN - Manage CDN - in .NET</span></span>](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn) (Начало работы с CDN: управление CDN — .NET)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
