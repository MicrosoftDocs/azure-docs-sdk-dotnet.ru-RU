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
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="97bef-104">Библиотеки Центров уведомлений Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="97bef-104">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="97bef-105">Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ.</span><span class="sxs-lookup"><span data-stu-id="97bef-105">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="97bef-106">Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.</span><span class="sxs-lookup"><span data-stu-id="97bef-106">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="97bef-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="97bef-107">Client library</span></span>

<span data-ttu-id="97bef-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="97bef-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

> [!NOTE]
> <span data-ttu-id="97bef-109">[В новой предварительной версии пакета NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) теперь поддерживается спецификация .NET Standard, которая позволяет использовать .NET Core во внутренних операциях центров уведомлений.</span><span class="sxs-lookup"><span data-stu-id="97bef-109">A [new preview version of the NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) now supports .NET Standard, which allows using .NET core for backend use of Notifications Hubs</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="97bef-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="97bef-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="97bef-111">Пример кода</span><span class="sxs-lookup"><span data-stu-id="97bef-111">Code Example</span></span>

<span data-ttu-id="97bef-112">В этом примере реализовано подключение к концентратору уведомлений и отправка push-уведомления из службы WNS.</span><span class="sxs-lookup"><span data-stu-id="97bef-112">This example connects to a Notification Hub and sends a Windows Push Notification Service (WNS) message.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="97bef-113">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="97bef-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a><span data-ttu-id="97bef-114">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="97bef-114">Management library</span></span>

<span data-ttu-id="97bef-115">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="97bef-115">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="97bef-116">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="97bef-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="97bef-117">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="97bef-117">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="97bef-118">Примеры</span><span class="sxs-lookup"><span data-stu-id="97bef-118">Samples</span></span>

- [<span data-ttu-id="97bef-119">Начало работы с Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97bef-119">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
