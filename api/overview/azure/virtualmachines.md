---
title: Библиотеки вычисления Azure для .NET
description: Справочник по библиотекам вычисления Azure для .NET
keywords: Azure, .NET, SDK, API, VM, virtual machines, compute
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: virtual-machines
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 96aabe0953a44b86da9cfd3202c43a4aa0f08a89
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065854"
---
# <a name="azure-virtual-machine-libraries-for-net"></a>Библиотеки виртуальных машин Azure для .NET

## <a name="overview"></a>Обзор

Выполняемые по запросу масштабируемые вычислительные ресурсы под управлением Windows или Linux.

Чтобы приступить к работе с виртуальными машинами Azure, см. инструкции по [созданию виртуальной машины Linux на портале Azure](https://review.docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal).

## <a name="management-apis"></a>API управления

Создавайте, настраивайте и масштабируйте виртуальные машины Windows и Linux в Azure с использованием кода и API управления.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Compute.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.Compute.Fluent
```

### <a name="code-example"></a>Пример кода

Создание виртуальной машины Windows.

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
> [Обзор API-интерфейсов управления](https://docs.microsoft.com/dotnet/api/overview/azure/virtualmachines/management?view=azure-dotnet)

### <a name="samples"></a>Примеры

* [Azure virtual machine management samples for .NET](/dotnet/azure/dotnet-sdk-azure-virtual-machine-samples) (Примеры управления виртуальными машинами Azure для .NET)
* [Deploy an SSH Enabled VM with a Template with .NET](https://azure.microsoft.com/resources/samples/resource-manager-dotnet-template-deployment/) (Развертывание виртуальной машины с включенным протоколом SSH на основе шаблона с помощью .NET)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=VM) примеров для виртуальных машин.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
