---
title: "Библиотеки Azure StorSimple для .NET"
description: "Справочник по библиотекам Azure StorSimple для .NET"
keywords: Azure, .NET, SDK, API, StorSimple
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/27/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: storsimple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: dcb6732bf1eded6852a3185546a09c96cfe84eca
ms.sourcegitcommit: 64c9e16e42894e8db8ed088487e55c5e0edd6861
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="azure-storsimple-libraries-for-net"></a><span data-ttu-id="4a6e4-104">Библиотеки Azure StorSimple для .NET</span><span class="sxs-lookup"><span data-stu-id="4a6e4-104">Azure StorSimple libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="4a6e4-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="4a6e4-105">Overview</span></span>

<span data-ttu-id="4a6e4-106">Microsoft Azure StorSimple — это решение корпоративного хранилища, которое предоставляет физические интерфейсы iSCSI или SMB для облачного хранилища.</span><span class="sxs-lookup"><span data-stu-id="4a6e4-106">Microsoft Azure StorSimple is an enterprise storage solution that provides physical iSCSI or SMB interfaces to cloud-based storage.</span></span> 

<span data-ttu-id="4a6e4-107">Подробнее об [Azure StorSimple](/azure/storsimple/).</span><span class="sxs-lookup"><span data-stu-id="4a6e4-107">Learn more about [Azure StorSimple](/azure/storsimple/).</span></span>    

## <a name="management-library"></a><span data-ttu-id="4a6e4-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="4a6e4-108">Management library</span></span>

<span data-ttu-id="4a6e4-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4a6e4-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4a6e4-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4a6e4-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StorSimple.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.StorSimple.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a6e4-111">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="4a6e4-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="4a6e4-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="4a6e4-112">Samples</span></span>

<span data-ttu-id="4a6e4-113">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="4a6e4-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package