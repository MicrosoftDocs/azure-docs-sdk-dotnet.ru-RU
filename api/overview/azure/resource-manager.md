---
title: "Библиотеки Azure Resource Manager для .NET"
description: "Справочник по библиотекам Azure Resource Manager для .NET"
keywords: Azure, .NET, SDK, API, Resource Manager
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/31/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 4dcfdb59e3cbe919053937a62602de6b602bbac1
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-resource-manager-libraries-for-net"></a><span data-ttu-id="c1737-104">Библиотеки Azure Resource Manager для .NET</span><span class="sxs-lookup"><span data-stu-id="c1737-104">Azure Resource Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="c1737-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c1737-105">Overview</span></span>

<span data-ttu-id="c1737-106">Azure Resource Manager позволяет работать с ресурсами решения как с группой.</span><span class="sxs-lookup"><span data-stu-id="c1737-106">Azure Resource Manager enables you to work with the resources in your solution as a group.</span></span>  <span data-ttu-id="c1737-107">Дополнительные сведения о Resource Manager вы найдете в статье [Общие сведения об Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="c1737-107">For more information about Resource Manager, see [Azure Resource Manager overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="c1737-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="c1737-108">Management library</span></span>

<span data-ttu-id="c1737-109">Библиотека Azure Resource Manager для .NET позволяет создавать, обновлять, удалять и перечислять ресурсы и группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c1737-109">The Azure Resource Manager library for .NET enables you to create, update, delete, and list resources and resource groups.</span></span>

<span data-ttu-id="c1737-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="c1737-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="c1737-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c1737-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a><span data-ttu-id="c1737-112">Пример</span><span class="sxs-lookup"><span data-stu-id="c1737-112">Example</span></span>

<span data-ttu-id="c1737-113">В этом примере создается группа ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c1737-113">This example creates a new resource group.</span></span>

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.ResourceManager.Fluent
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IResourceGroup resourceGroup = azure.ResourceGroups
    .Define("ResourceGroupName")
    .WithRegion(Region.USWest)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1737-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="c1737-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a><span data-ttu-id="c1737-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="c1737-115">Samples</span></span>

* [<span data-ttu-id="c1737-116">Getting Started with Resources - Manage Resource Group - in .Net</span><span class="sxs-lookup"><span data-stu-id="c1737-116">Manage resource groups</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group) (Начало работы с ресурсами: управление группами ресурсов — .Net)
* [<span data-ttu-id="c1737-117">Управление ресурсами</span><span class="sxs-lookup"><span data-stu-id="c1737-117">Manage resources</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [<span data-ttu-id="c1737-118">Getting Started with Resources - Deploy Using A R M Template - in .Net</span><span class="sxs-lookup"><span data-stu-id="c1737-118">Deploy resources with ARM templates</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template) (Начало работы с ресурсами: развертывание с использованием шаблона ARM — .Net)
* [<span data-ttu-id="c1737-119">Getting Started with Resources - Deploy Using A R M Template With Progress - in .Net</span><span class="sxs-lookup"><span data-stu-id="c1737-119">Deploy resources with ARM templates (with progress)</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress) (Начало работы с ресурсами: развертывание с использованием шаблона ARM (с описанием хода выполнения) — .Net)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
