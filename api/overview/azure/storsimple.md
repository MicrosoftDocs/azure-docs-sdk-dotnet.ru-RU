---
title: Библиотеки Azure StorSimple для .NET
description: Справочник по библиотекам Azure StorSimple для .NET
ms.date: 10/27/2017
ms.topic: reference
ms.service: storsimple
ms.openlocfilehash: ecaa1acb0d988f7312645c2e6ed8f3289e51237c
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190367"
---
# <a name="azure-storsimple-libraries-for-net"></a><span data-ttu-id="2cc24-103">Библиотеки Azure StorSimple для .NET</span><span class="sxs-lookup"><span data-stu-id="2cc24-103">Azure StorSimple libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="2cc24-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="2cc24-104">Overview</span></span>

<span data-ttu-id="2cc24-105">Microsoft Azure StorSimple — это решение корпоративного хранилища, которое предоставляет физические интерфейсы iSCSI или SMB для облачного хранилища.</span><span class="sxs-lookup"><span data-stu-id="2cc24-105">Microsoft Azure StorSimple is an enterprise storage solution that provides physical iSCSI or SMB interfaces to cloud-based storage.</span></span> 

<span data-ttu-id="2cc24-106">Подробнее об [Azure StorSimple](/azure/storsimple/).</span><span class="sxs-lookup"><span data-stu-id="2cc24-106">Learn more about [Azure StorSimple](/azure/storsimple/).</span></span>    

## <a name="management-library"></a><span data-ttu-id="2cc24-107">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="2cc24-107">Management library</span></span>

<span data-ttu-id="2cc24-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="2cc24-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="2cc24-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2cc24-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StorSimple.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.StorSimple.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="2cc24-110">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="2cc24-110">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="2cc24-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="2cc24-111">Samples</span></span>

<span data-ttu-id="2cc24-112">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="2cc24-112">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package