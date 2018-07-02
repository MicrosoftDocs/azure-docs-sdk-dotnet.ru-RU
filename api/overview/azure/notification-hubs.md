---
title: Библиотеки Центров уведомлений Azure для .NET
description: Справочник по библиотекам Центров уведомлений Azure для .NET
keywords: Azure, .NET, SDK, API, Notification Hubs
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: notification-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 0cbbfbafd2d1900c00f08fd1ab2e0f1af80ae8ff
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065504"
---
# <a name="azure-notification-hubs-libraries-for-net"></a>Библиотеки Центров уведомлений Azure для .NET

Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ. Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.

## <a name="client-library"></a>Клиентская библиотека

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

> [!NOTE]
> [В новой предварительной версии пакета NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) теперь поддерживается спецификация .NET Standard, которая позволяет использовать .NET Core во внутренних операциях центров уведомлений.

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a>Пример кода

В этом примере реализовано подключение к концентратору уведомлений и отправка push-уведомления из службы WNS.

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a>Библиотека управления

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a>Примеры

- [Начало работы с Windows PowerShell](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
