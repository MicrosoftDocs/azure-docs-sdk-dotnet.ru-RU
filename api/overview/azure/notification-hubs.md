---
title: Библиотеки Центров уведомлений Azure для .NET
description: Справочник по библиотекам Центров уведомлений Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: notification-hubs
ms.openlocfilehash: 750a51e8dfa7323f6afb54735b4bfc517f9ec15f
ms.sourcegitcommit: 4b68c73652cb7e44cf4db36f70cb33a17dd863ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58085841"
---
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="0b9e5-103">Библиотеки Центров уведомлений Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="0b9e5-103">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="0b9e5-104">Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ.</span><span class="sxs-lookup"><span data-stu-id="0b9e5-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="0b9e5-105">Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.</span><span class="sxs-lookup"><span data-stu-id="0b9e5-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="0b9e5-106">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="0b9e5-106">Client library</span></span>

<span data-ttu-id="0b9e5-107">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="0b9e5-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

> [!NOTE]
> <span data-ttu-id="0b9e5-108">[В пакете NuGet для Центров уведомлений Azure](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) теперь поддерживается спецификация .NET Standard, которая позволяет использовать .NET Core во внутренних операциях Центров уведомлений.</span><span class="sxs-lookup"><span data-stu-id="0b9e5-108">The [Azure Notification Hubs NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) now supports .NET Standard, which allows using .NET core for backend use of Notifications Hubs</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="0b9e5-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b9e5-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="0b9e5-110">Пример кода</span><span class="sxs-lookup"><span data-stu-id="0b9e5-110">Code Example</span></span>

<span data-ttu-id="0b9e5-111">В этом примере реализовано подключение к концентратору уведомлений и отправка push-уведомления из службы WNS.</span><span class="sxs-lookup"><span data-stu-id="0b9e5-111">This example connects to a Notification Hub and sends a Windows Push Notification Service (WNS) message.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b9e5-112">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="0b9e5-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)

## <a name="management-library"></a><span data-ttu-id="0b9e5-113">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="0b9e5-113">Management library</span></span>

<span data-ttu-id="0b9e5-114">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="0b9e5-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="0b9e5-115">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b9e5-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b9e5-116">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="0b9e5-116">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="0b9e5-117">Примеры</span><span class="sxs-lookup"><span data-stu-id="0b9e5-117">Samples</span></span>

- [<span data-ttu-id="0b9e5-118">Начало работы с Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b9e5-118">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
