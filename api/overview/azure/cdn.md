---
title: Библиотеки Azure CDN для .NET
description: Справочник по библиотекам Azure CDN для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: azure-cdn
ms.openlocfilehash: b06b886531510d442c415fdc483d8083b6622c8e
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348066"
---
# <a name="azure-cdn-libraries-for-net"></a><span data-ttu-id="2e00f-103">Библиотеки Azure CDN для .NET</span><span class="sxs-lookup"><span data-stu-id="2e00f-103">Azure CDN libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="2e00f-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="2e00f-104">Overview</span></span>

<span data-ttu-id="2e00f-105">Сеть доставки содержимого (CDN) Azure кэширует статическое веб-содержимое в стратегически расположенных точках. Это позволяет обеспечить максимальную пропускную способность для доставки содержимого пользователям.</span><span class="sxs-lookup"><span data-stu-id="2e00f-105">The Azure Content Delivery Network (CDN) caches static web content at strategically placed locations to provide maximum throughput for delivering content to users.</span></span> <span data-ttu-id="2e00f-106">CDN предлагает разработчикам глобальное решение для доставки содержимого с высокой пропускной способностью путем кэширования содержимого на физических узлах по всему миру.</span><span class="sxs-lookup"><span data-stu-id="2e00f-106">The CDN offers developers a global solution for delivering high-bandwidth content by caching the content at physical nodes across the world.</span></span>

<span data-ttu-id="2e00f-107">Дополнительную информацию по Azure CDN см. в статье [Общие сведения о сети доставки содержимого (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview).</span><span class="sxs-lookup"><span data-stu-id="2e00f-107">To learn more about Azure CDN, see [Overview of the Azure Content Delivery Network](https://docs.microsoft.com/azure/cdn/cdn-overview).</span></span>


## <a name="management-library"></a><span data-ttu-id="2e00f-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="2e00f-108">Management library</span></span>

<span data-ttu-id="2e00f-109">С помощью библиотеки Azure CDN для .NET можно автоматизировать создание профилей и конечных точек CDN и управление ими.</span><span class="sxs-lookup"><span data-stu-id="2e00f-109">You can use the Azure CDN Library for .NET to automate creation and management of CDN profiles and endpoints.</span></span> 

<span data-ttu-id="2e00f-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="2e00f-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="2e00f-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2e00f-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a><span data-ttu-id="2e00f-112">Пример</span><span class="sxs-lookup"><span data-stu-id="2e00f-112">Example</span></span>

<span data-ttu-id="2e00f-113">В этом примере создается профиль CDN с новой конечной точкой, которая указывает на `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2e00f-113">This example creates a new CDN profile with a new endpoint pointed to `www.contoso.com`.</span></span>

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
> [<span data-ttu-id="2e00f-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="2e00f-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a><span data-ttu-id="2e00f-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="2e00f-115">Samples</span></span>

* <span data-ttu-id="2e00f-116">[Getting Started with Cdn - Manage Cdn - in .Net](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn) (Начало работы с CDN: управление CDN — .NET)</span><span class="sxs-lookup"><span data-stu-id="2e00f-116">[Getting started with CDN - Manage CDN - in .NET](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn)</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
