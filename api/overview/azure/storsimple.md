---
title: Библиотеки Azure StorSimple для .NET
description: Справочник по библиотекам Azure StorSimple для .NET
keywords: Azure, .NET, SDK, API, StorSimple
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/27/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: storsimple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 818c48a0f45812841eb0e8c3928b59f6681892cf
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065904"
---
# <a name="azure-storsimple-libraries-for-net"></a>Библиотеки Azure StorSimple для .NET

## <a name="overview"></a>Обзор

Microsoft Azure StorSimple — это решение корпоративного хранилища, которое предоставляет физические интерфейсы iSCSI или SMB для облачного хранилища. 

Подробнее об [Azure StorSimple](/azure/storsimple/).    

## <a name="management-library"></a>Библиотека управления

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.StorSimple.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.StorSimple.Fluent
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a>Примеры

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package