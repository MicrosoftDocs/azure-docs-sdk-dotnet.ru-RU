---
title: Библиотеки кэша Redis для Azure для .NET
description: Справочник по библиотекам кэша Redis для Azure для .NET
keywords: Azure, .NET, SDK, API, Redis Cache
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: redis-cache
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 879f42aa254103239fb0dceeb25cb99a7d5e9814
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065924"
---
# <a name="azure-redis-cache-libraries-for-net"></a><span data-ttu-id="8f421-104">Библиотеки кэша Redis для Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="8f421-104">Azure Redis Cache libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="8f421-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="8f421-105">Overview</span></span>

<span data-ttu-id="8f421-106">Кэш Redis для Azure — это защищенный кэш данных и брокер обмена сообщениями, который обеспечивает высокую пропускную способность и низкую задержку при обращении приложений к данным.</span><span class="sxs-lookup"><span data-stu-id="8f421-106">Azure Redis Cache is a secure data cache and messaging broker that provides high throughput and low-latency access to data for applications.</span></span>  <span data-ttu-id="8f421-107">Дополнительные сведения см. в разделе [Как использовать кэш Redis для Azure](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).</span><span class="sxs-lookup"><span data-stu-id="8f421-107">For more information, see [How to Use Redis Cache](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).</span></span>

## <a name="client-library"></a><span data-ttu-id="8f421-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="8f421-108">Client library</span></span>

<span data-ttu-id="8f421-109">Кэш Redis для Azure совместим с любым API клиента Redis, включая `StackExchange.Redis`.</span><span class="sxs-lookup"><span data-stu-id="8f421-109">Azure Redis Cache is compatible with any Redis client API, including `StackExchange.Redis`.</span></span>

<span data-ttu-id="8f421-110">Установите [пакет NuGet](https://www.nuget.org/packages/StackExchange.Redis) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8f421-110">Install the [NuGet package](https://www.nuget.org/packages/StackExchange.Redis) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8f421-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f421-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package StackExchange.Redis
```

```bash
dotnet add package StackExchange.Redis
```

### <a name="example"></a><span data-ttu-id="8f421-112">Пример</span><span class="sxs-lookup"><span data-stu-id="8f421-112">Example</span></span>

<span data-ttu-id="8f421-113">В этом примере устанавливается подключение к экземпляру базы данных кэша Redis, в кэш добавляются некоторые строки по имени, а затем они снова извлекаются.</span><span class="sxs-lookup"><span data-stu-id="8f421-113">This example connects to a Redis Cache database instance, adds some strings to the cache by name, and then retrieves them again.</span></span>

```csharp
/* Include this "using" directive.
using StackExchange.Redis;
*/

ConnectionMultiplexer connection = 
    ConnectionMultiplexer.Connect("contoso.redis.cache.windows.net,abortConnect=false,ssl=true,password=...");
    IDatabase cache = connection.GetDatabase();

// Perform cache operations using the cache object...
// Simple put of integral data types into the cache
cache.StringSet("key1", "value");
cache.StringSet("key2", 25);

// Simple get of data types from the cache
string key1 = cache.StringGet("key1");
int key2 = (int)cache.StringGet("key2");
```

## <a name="management-library"></a><span data-ttu-id="8f421-114">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="8f421-114">Management library</span></span>

<span data-ttu-id="8f421-115">Библиотека управления кэша Redis дает возможность управлять ресурсами кэша Redis и ключами доступа.</span><span class="sxs-lookup"><span data-stu-id="8f421-115">The Redis Cache management library allows you to manage Redis Cache resources and access keys.</span></span>

<span data-ttu-id="8f421-116">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8f421-116">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8f421-117">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f421-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Redis.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Redis.Fluent
```

### <a name="example"></a><span data-ttu-id="8f421-118">Пример</span><span class="sxs-lookup"><span data-stu-id="8f421-118">Example</span></span>

<span data-ttu-id="8f421-119">В этом примере создается новый кэш Redis.</span><span class="sxs-lookup"><span data-stu-id="8f421-119">This example creates a new Redis Cache.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.Redis.Fluent;
*/

IRedisCache redisCache1 = azure.RedisCaches.Define("RedisCacheName")
    .WithRegion(Region.USCentral)
    .WithNewResourceGroup("ResourceGroupName")
    .WithBasicSku()
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f421-120">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="8f421-120">Explore the management APIs</span></span>](/dotnet/api/overview/azure/rediscache/management)


## <a name="samples"></a><span data-ttu-id="8f421-121">Примеры</span><span class="sxs-lookup"><span data-stu-id="8f421-121">Samples</span></span>

* <span data-ttu-id="8f421-122">[Getting Started with Redis - Manage Redis - in .NET](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache) (Начало работы с кэшем Redis и управление им в .NET)</span><span class="sxs-lookup"><span data-stu-id="8f421-122">[Getting Started with Redis - Manage Redis - in .NET](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache)</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
