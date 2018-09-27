---
title: Библиотеки Центров уведомлений Azure для .NET
description: Справочник по библиотекам Центров уведомлений Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: notification-hubs
ms.openlocfilehash: 197ca22527a475b43b45149a40e96e5a027739ad
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190267"
---
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="75b50-103">Библиотеки Центров уведомлений Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="75b50-103">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="75b50-104">Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ.</span><span class="sxs-lookup"><span data-stu-id="75b50-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="75b50-105">Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.</span><span class="sxs-lookup"><span data-stu-id="75b50-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="75b50-106">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="75b50-106">Client library</span></span>

<span data-ttu-id="75b50-107">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="75b50-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

> [!NOTE]
> <span data-ttu-id="75b50-108">[В новой предварительной версии пакета NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) теперь поддерживается спецификация .NET Standard, которая позволяет использовать .NET Core во внутренних операциях центров уведомлений.</span><span class="sxs-lookup"><span data-stu-id="75b50-108">A [new preview version of the NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) now supports .NET Standard, which allows using .NET core for backend use of Notifications Hubs</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="75b50-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="75b50-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="75b50-110">Пример кода</span><span class="sxs-lookup"><span data-stu-id="75b50-110">Code Example</span></span>

<span data-ttu-id="75b50-111">В этом примере реализовано подключение к концентратору уведомлений и отправка push-уведомления из службы WNS.</span><span class="sxs-lookup"><span data-stu-id="75b50-111">This example connects to a Notification Hub and sends a Windows Push Notification Service (WNS) message.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="75b50-112">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="75b50-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a><span data-ttu-id="75b50-113">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="75b50-113">Management library</span></span>

<span data-ttu-id="75b50-114">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="75b50-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="75b50-115">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="75b50-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="75b50-116">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="75b50-116">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="75b50-117">Примеры</span><span class="sxs-lookup"><span data-stu-id="75b50-117">Samples</span></span>

- [<span data-ttu-id="75b50-118">Начало работы с Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="75b50-118">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
