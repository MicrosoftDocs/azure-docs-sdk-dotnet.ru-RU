---
title: "Библиотеки вычисления Azure для .NET"
description: "Справочник по библиотекам вычисления Azure для .NET"
keywords: Azure, .NET, SDK, API, VM, virtual machines, compute
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: virtual-machines
ms.custom: devcenter, svc-overview
ms.openlocfilehash: d3bad2e94ec8b08bad2a014fb25d400625a3590d
ms.sourcegitcommit: 2d08f2815fa7fab55e09d294fc4d74897df7951d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
# <a name="azure-virtual-machine-libraries-for-net"></a><span data-ttu-id="9d1ed-104">Библиотеки виртуальных машин Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="9d1ed-104">Azure virtual machine libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9d1ed-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="9d1ed-105">Overview</span></span>

<span data-ttu-id="9d1ed-106">Выполняемые по запросу масштабируемые вычислительные ресурсы под управлением Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="9d1ed-106">On-demand, scalable computing resources running Linux or Windows.</span></span>

<span data-ttu-id="9d1ed-107">Чтобы приступить к работе с виртуальными машинами Azure, см. инструкции по [созданию виртуальной машины Linux на портале Azure](https://review.docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal).</span><span class="sxs-lookup"><span data-stu-id="9d1ed-107">To get started with Azure virtual machines, see [Create a Linux virtual machine with the Azure portal](https://review.docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal).</span></span>

## <a name="management-apis"></a><span data-ttu-id="9d1ed-108">API управления</span><span class="sxs-lookup"><span data-stu-id="9d1ed-108">Management APIs</span></span>

<span data-ttu-id="9d1ed-109">Создавайте, настраивайте и масштабируйте виртуальные машины Windows и Linux в Azure с использованием кода и API управления.</span><span class="sxs-lookup"><span data-stu-id="9d1ed-109">Create, configure, and scale out Windows and Linux virtual machines in Azure from your code with the management API.</span></span>

<span data-ttu-id="9d1ed-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9d1ed-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9d1ed-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9d1ed-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Compute.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="9d1ed-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9d1ed-112">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Compute.Fluent
```

### <a name="code-example"></a><span data-ttu-id="9d1ed-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="9d1ed-113">Code Example</span></span>

<span data-ttu-id="9d1ed-114">Создание виртуальной машины Windows.</span><span class="sxs-lookup"><span data-stu-id="9d1ed-114">Create a Windows VM.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IVirtualMachine windowsVM = azure.VirtualMachines.Define("MyVirtualMachine")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress("MyIPAddressLabel")
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername("UserName")
    .WithAdminPassword("Password")
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d1ed-115">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="9d1ed-115">Explore the management APIs</span></span>](https://docs.microsoft.com/en-us/dotnet/api/overview/azure/virtualmachines/management?view=azure-dotnet)

### <a name="samples"></a><span data-ttu-id="9d1ed-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="9d1ed-116">Samples</span></span>

* <span data-ttu-id="9d1ed-117">[Azure virtual machine management samples for .NET](/dotnet/azure/dotnet-sdk-azure-virtual-machine-samples) (Примеры управления виртуальными машинами Azure для .NET)</span><span class="sxs-lookup"><span data-stu-id="9d1ed-117">[Create and manage virtual machines](/dotnet/azure/dotnet-sdk-azure-virtual-machine-samples)</span></span>
* <span data-ttu-id="9d1ed-118">[Deploy an SSH Enabled VM with a Template with .NET](https://azure.microsoft.com/en-us/resources/samples/resource-manager-dotnet-template-deployment/) (Развертывание виртуальной машины с включенным протоколом SSH на основе шаблона с помощью .NET)</span><span class="sxs-lookup"><span data-stu-id="9d1ed-118">[Deploy an SSH-enabled VM with a Template with .NET](https://azure.microsoft.com/en-us/resources/samples/resource-manager-dotnet-template-deployment/)</span></span>

<span data-ttu-id="9d1ed-119">Просмотрите [полный список](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=VM) примеров для виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="9d1ed-119">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=VM) of virtual machine samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
