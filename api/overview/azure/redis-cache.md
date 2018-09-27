---
title: Библиотеки кэша Redis для Azure для .NET
description: Справочник по библиотекам кэша Redis для Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: redis-cache
ms.openlocfilehash: cc043bbc6ea5915f7b6c2265b606210efb72d9d0
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190527"
---
# <a name="azure-redis-cache-libraries-for-net"></a><span data-ttu-id="42c37-103">Библиотеки кэша Redis для Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="42c37-103">Azure Redis Cache libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="42c37-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="42c37-104">Overview</span></span>

<span data-ttu-id="42c37-105">Кэш Redis для Azure — это защищенный кэш данных и брокер обмена сообщениями, который обеспечивает высокую пропускную способность и низкую задержку при обращении приложений к данным.</span><span class="sxs-lookup"><span data-stu-id="42c37-105">Azure Redis Cache is a secure data cache and messaging broker that provides high throughput and low-latency access to data for applications.</span></span>  <span data-ttu-id="42c37-106">Дополнительные сведения см. в разделе [Как использовать кэш Redis для Azure](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).</span><span class="sxs-lookup"><span data-stu-id="42c37-106">For more information, see [How to Use Redis Cache](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).</span></span>

## <a name="client-library"></a><span data-ttu-id="42c37-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="42c37-107">Client library</span></span>

<span data-ttu-id="42c37-108">Кэш Redis для Azure совместим с любым API клиента Redis, включая `StackExchange.Redis`.</span><span class="sxs-lookup"><span data-stu-id="42c37-108">Azure Redis Cache is compatible with any Redis client API, including `StackExchange.Redis`.</span></span>

<span data-ttu-id="42c37-109">Установите [пакет NuGet](https://www.nuget.org/packages/StackExchange.Redis) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="42c37-109">Install the [NuGet package](https://www.nuget.org/packages/StackExchange.Redis) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="42c37-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42c37-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package StackExchange.Redis
```

```bash
dotnet add package StackExchange.Redis
```

### <a name="example"></a><span data-ttu-id="42c37-111">Пример</span><span class="sxs-lookup"><span data-stu-id="42c37-111">Example</span></span>

<span data-ttu-id="42c37-112">В этом примере устанавливается подключение к экземпляру базы данных кэша Redis, в кэш добавляются некоторые строки по имени, а затем они снова извлекаются.</span><span class="sxs-lookup"><span data-stu-id="42c37-112">This example connects to a Redis Cache database instance, adds some strings to the cache by name, and then retrieves them again.</span></span>

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

## <a name="management-library"></a><span data-ttu-id="42c37-113">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="42c37-113">Management library</span></span>

<span data-ttu-id="42c37-114">Библиотека управления кэша Redis дает возможность управлять ресурсами кэша Redis и ключами доступа.</span><span class="sxs-lookup"><span data-stu-id="42c37-114">The Redis Cache management library allows you to manage Redis Cache resources and access keys.</span></span>

<span data-ttu-id="42c37-115">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="42c37-115">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="42c37-116">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42c37-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Redis.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Redis.Fluent
```

### <a name="example"></a><span data-ttu-id="42c37-117">Пример</span><span class="sxs-lookup"><span data-stu-id="42c37-117">Example</span></span>

<span data-ttu-id="42c37-118">В этом примере создается новый кэш Redis.</span><span class="sxs-lookup"><span data-stu-id="42c37-118">This example creates a new Redis Cache.</span></span>

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
> [<span data-ttu-id="42c37-119">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="42c37-119">Explore the management APIs</span></span>](/dotnet/api/overview/azure/rediscache/management)


## <a name="samples"></a><span data-ttu-id="42c37-120">Примеры</span><span class="sxs-lookup"><span data-stu-id="42c37-120">Samples</span></span>

* <span data-ttu-id="42c37-121">[Getting Started with Redis - Manage Redis - in .NET](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache) (Начало работы с кэшем Redis и управление им в .NET)</span><span class="sxs-lookup"><span data-stu-id="42c37-121">[Getting Started with Redis - Manage Redis - in .NET](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache)</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
