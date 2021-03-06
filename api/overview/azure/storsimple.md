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