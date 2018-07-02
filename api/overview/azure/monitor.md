---
title: Библиотеки Azure Monitor для .NET
description: Справочник по библиотекам Azure Monitor для .NET
keywords: Azure, .NET, SDK, API, Monitor
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/27/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 7b86b752a354b5ab6f8482b81ecba3b08b8a9442
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065884"
---
# <a name="azure-monitor-libraries-for-net"></a><span data-ttu-id="1bdc6-104">Библиотеки Azure Monitor для .NET</span><span class="sxs-lookup"><span data-stu-id="1bdc6-104">Azure Monitor libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="1bdc6-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="1bdc6-105">Overview</span></span>

<span data-ttu-id="1bdc6-106">Azure Monitor помогает отслеживать производительность, обеспечивать безопасность и определять тенденции.</span><span class="sxs-lookup"><span data-stu-id="1bdc6-106">Azure Monitor helps you track performance, maintain security, and identify trends.</span></span>

<span data-ttu-id="1bdc6-107">Узнайте подробнее о службе [Azure Monitor](/azure/monitoring-and-diagnostics/).</span><span class="sxs-lookup"><span data-stu-id="1bdc6-107">Learn more about [Azure Monitor](/azure/monitoring-and-diagnostics/).</span></span>   

## <a name="management-library"></a><span data-ttu-id="1bdc6-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="1bdc6-108">Management library</span></span>

<span data-ttu-id="1bdc6-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Monitor.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="1bdc6-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Monitor.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1bdc6-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1bdc6-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Monitor.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Monitor.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="1bdc6-111">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="1bdc6-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="1bdc6-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="1bdc6-112">Samples</span></span>

<span data-ttu-id="1bdc6-113">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="1bdc6-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package