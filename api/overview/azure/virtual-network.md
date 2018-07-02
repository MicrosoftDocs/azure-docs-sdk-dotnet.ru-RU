---
title: Библиотеки виртуальной сети Azure для .NET
description: Справочник по библиотекам виртуальной сети Azure для .NET
keywords: Azure, .NET, SDK, API, Virtual Network
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: virtual-network
ms.custom: devcenter, svc-overview
ms.openlocfilehash: eb2300522e63339386bf08b5dfac3b803a1e5efd
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065294"
---
# <a name="azure-virtual-network-libraries-for-net"></a><span data-ttu-id="6e272-104">Библиотеки виртуальной сети Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="6e272-104">Azure Virtual Network libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="6e272-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="6e272-105">Overview</span></span>
<span data-ttu-id="6e272-106">Служба [Виртуальная сеть Azure](/azure/virtual-network/virtual-networks-overview) позволяет безопасно подключать ресурсы Azure между собой с помощью виртуальных сетей.</span><span class="sxs-lookup"><span data-stu-id="6e272-106">The [Azure Virtual Network](/azure/virtual-network/virtual-networks-overview) service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="6e272-107">Виртуальная сеть — это представление вашей собственной сети в облаке.</span><span class="sxs-lookup"><span data-stu-id="6e272-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="6e272-108">Виртуальные сети также можно подключать между собой. Таким образом ресурсы в этих виртуальных сетях смогут взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="6e272-108">You can also connect VNets to each other, enabling resources connected to either VNet to communicate with each other.</span></span> 

## <a name="management-library"></a><span data-ttu-id="6e272-109">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="6e272-109">Management library</span></span>

<span data-ttu-id="6e272-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="6e272-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="6e272-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6e272-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Network.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="6e272-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="6e272-112">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Network.Fluent
```

### <a name="code-example"></a><span data-ttu-id="6e272-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="6e272-113">Code Example</span></span>
<span data-ttu-id="6e272-114">В этом примере показано, как создать виртуальную сеть.</span><span class="sxs-lookup"><span data-stu-id="6e272-114">This example shows how you can create a virtual network.</span></span>

```csharp
/* 
  Include these "using" directives...
  
  using Microsoft.Azure.Management.Network.Fluent;
  using Microsoft.Azure.Management.Network.Fluent.Models;
*/
using (NetworkManagementClient client = new NetworkManagementClient(credentials))
{
    // Define VNet
    VirtualNetworkInner vnet = new VirtualNetworkInner()
    {
        Location = "West US",
        AddressSpace = new AddressSpace()
        {
            AddressPrefixes = new List<string>() { "0.0.0.0/16" }
        },

        DhcpOptions = new DhcpOptions()
        {
            DnsServers = new List<string>() { "1.1.1.1", "1.1.2.4" }
        },

        Subnets = new List<Subnet>()
        {
            new Subnet()
            {
                Name = subnet1Name,
                AddressPrefix = "1.0.1.0/24",
            },
            new Subnet()
            {
                Name = subnet2Name,
               AddressPrefix = "1.0.2.0/24",
            }
        }
    };
    
    await client.VirtualNetworks.CreateOrUpdateAsync(resourceGroupName, vNetName, vnet);
}

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="6e272-115">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="6e272-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/network/management)

## <a name="samples"></a><span data-ttu-id="6e272-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="6e272-116">Samples</span></span>
- <span data-ttu-id="6e272-117">[Getting Started with Network - Manage Virtual Network - in .Net](https://github.com/Azure-Samples/network-dotnet-manage-virtual-network) (Начало работы с сетью: управление виртуальной сетью — .Net)</span><span class="sxs-lookup"><span data-stu-id="6e272-117">[Managing Virtual Networks with subnets](https://github.com/Azure-Samples/network-dotnet-manage-virtual-network)</span></span>

<span data-ttu-id="6e272-118">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="6e272-118">Explore more [.NET sample code](https://azure.microsoft.com/resources/samples/?platform=dotnet) that you can use in your apps.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console 
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package 

