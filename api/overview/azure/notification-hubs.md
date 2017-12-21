---
title: "Библиотеки Центров уведомлений Azure для .NET"
description: "Справочник по библиотекам Центров уведомлений Azure для .NET"
keywords: Azure, .NET, SDK, API, Notification Hubs
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: notification-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 9fd49ccc8d02eff09a8a53e6f1b9baa6a7a59082
ms.sourcegitcommit: 33732307162ddf6f272b0e9cc7f74eb8e6fdda1b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="d8116-104">Библиотеки Центров уведомлений Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="d8116-104">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="d8116-105">Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ.</span><span class="sxs-lookup"><span data-stu-id="d8116-105">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="d8116-106">Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.</span><span class="sxs-lookup"><span data-stu-id="d8116-106">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="d8116-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="d8116-107">Client library</span></span>

<span data-ttu-id="d8116-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="d8116-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

> [!NOTE]
> <span data-ttu-id="d8116-109">[В новой предварительной версии пакета NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) теперь поддерживается спецификация .NET Standard, которая позволяет использовать .NET Core во внутренних операциях центров уведомлений.</span><span class="sxs-lookup"><span data-stu-id="d8116-109">A [new preview version of the NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) now supports .NET Standard, which allows using .NET core for backend use of Notifications Hubs</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="d8116-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8116-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="d8116-111">Пример кода</span><span class="sxs-lookup"><span data-stu-id="d8116-111">Code Example</span></span>

<span data-ttu-id="d8116-112">В этом примере устанавливается подключение к базе данных и считываются строки из таблицы.</span><span class="sxs-lookup"><span data-stu-id="d8116-112">This example connects to a database and reads rows from a table.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="d8116-113">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="d8116-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a><span data-ttu-id="d8116-114">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="d8116-114">Management library</span></span>

<span data-ttu-id="d8116-115">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="d8116-115">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="d8116-116">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8116-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="d8116-117">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="d8116-117">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="d8116-118">Примеры</span><span class="sxs-lookup"><span data-stu-id="d8116-118">Samples</span></span>

- [<span data-ttu-id="d8116-119">Начало работы с Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8116-119">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
