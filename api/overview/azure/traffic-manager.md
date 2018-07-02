---
title: Библиотеки диспетчера трафика Azure для .NET
description: Справочник по библиотекам диспетчера трафика Azure для .NET
keywords: Azure, .NET, SDK, API, Traffic Manager
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: traffic-manager
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 05856cbe48a5cf5f0c9ebf43609a029928f490f9
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065874"
---
# <a name="azure-traffic-manager-libraries-for-net"></a>Библиотеки диспетчера трафика Azure для .NET

## <a name="overview"></a>Обзор

Диспетчер трафика Microsoft Azure позволяет управлять распределением пользовательского трафика между конечными точками службы в разных центрах обработки данных. К конечным точкам службы, поддерживаемым диспетчером трафика Azure, относятся виртуальные машины, веб-приложения и облачные службы Azure. Можно также использовать диспетчер трафика Azure для внешних конечных точек, не относящихся к среде Azure.

См. дополнительные сведения о [диспетчере трафика Azure](/azure/traffic-manager/traffic-manager-overview).  

## <a name="management-library"></a>Библиотека управления

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a>Примеры

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package