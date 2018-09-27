---
title: Библиотеки служебной шины Azure для .NET
description: Справочник по библиотекам служебной Azure шины для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: service-bus
ms.openlocfilehash: 506be9a669a2418f2437271d128a963e351442e7
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190877"
---
# <a name="azure-service-bus-libraries-for-net"></a><span data-ttu-id="38dcc-103">Библиотеки служебной шины Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="38dcc-103">Azure Service Bus libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="38dcc-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="38dcc-104">Overview</span></span>

<span data-ttu-id="38dcc-105">[Служебная шина Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) — это инфраструктура обмена сообщениями, которая размещается между приложениями и позволяет им обмениваться сообщениями для улучшения масштабирования и устойчивости.</span><span class="sxs-lookup"><span data-stu-id="38dcc-105">[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) is a messaging infrastructure that sits between applications allowing them to exchange messages for improved scale and resiliency.</span></span>

## <a name="client-library"></a><span data-ttu-id="38dcc-106">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="38dcc-106">Client library</span></span>

<span data-ttu-id="38dcc-107">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.ServiceBus) непосредственно из [консоли диспетчера пакетов][PackageManager].</span><span class="sxs-lookup"><span data-stu-id="38dcc-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.ServiceBus) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="38dcc-108">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38dcc-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.ServiceBus
```

### <a name="code-example"></a><span data-ttu-id="38dcc-109">Пример кода</span><span class="sxs-lookup"><span data-stu-id="38dcc-109">Code Example</span></span>

<span data-ttu-id="38dcc-110">В этом примере в очередь служебной шины отправляется сообщение.</span><span class="sxs-lookup"><span data-stu-id="38dcc-110">This example sends a message to a Service Bus queue.</span></span>

```csharp
// using Microsoft.Azure.ServiceBus;
// Microsoft.Azure.ServiceBus 2.0.0 (stable)

byte[] messageBody = System.Text.Encoding.Unicode.GetBytes("Hello, world!");
ServiceBusConnectionStringBuilder builder = new ServiceBusConnectionStringBuilder(connectionString);
QueueClient client = new QueueClient(builder, ReceiveMode.PeekLock);
client.SendAsync(new Message(messageBody));
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="38dcc-111">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="38dcc-111">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a><span data-ttu-id="38dcc-112">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="38dcc-112">Management library</span></span>

<span data-ttu-id="38dcc-113">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="38dcc-113">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="38dcc-114">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38dcc-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="38dcc-115">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="38dcc-115">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a><span data-ttu-id="38dcc-116">Пример кода</span><span class="sxs-lookup"><span data-stu-id="38dcc-116">Code Example</span></span>

<span data-ttu-id="38dcc-117">В этом примере создается очередь служебной шины с максимальным размером 1024 МБ.</span><span class="sxs-lookup"><span data-stu-id="38dcc-117">This example creates a Service Bus queue with a maximum size of 1024 MB.</span></span>

```csharp
// using Microsoft.Azure.Management.ServiceBus.Fluent;
// using Microsoft.Azure.Management.ServiceBus.Fluent.Models;

using (ServiceBusManagementClient client = new ServiceBusManagementClient(credentials))
{
    client.SubscriptionId = subscriptionId;
    QueueInner parameters = new QueueInner
    {
        MaxSizeInMegabytes = 1024
    };
    await client.Queues.CreateOrUpdateAsync(resourceGroupName, namespaceName, queueName, parameters);
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="38dcc-118">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="38dcc-118">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a><span data-ttu-id="38dcc-119">Примеры</span><span class="sxs-lookup"><span data-stu-id="38dcc-119">Samples</span></span>

- <span data-ttu-id="38dcc-120">[Getting Started with Service - Service Bus Queue Basic - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/) (Начало работы со службой: основные сведения об очереди служебной шины — .Net)</span><span class="sxs-lookup"><span data-stu-id="38dcc-120">[Service Bus Queue Basics - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/)</span></span>
- <span data-ttu-id="38dcc-121">[Getting Started with Service - Service Bus Queue Advance Features - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/) (Начало работы со службой: расширенные функции очереди служебной шины — .Net)</span><span class="sxs-lookup"><span data-stu-id="38dcc-121">[Service Bus Queue Advanced Features - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/)</span></span>
- <span data-ttu-id="38dcc-122">[Getting Started with Service - Service Bus Publish Subscribe Basic - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/) (Начало работы со службой: основные сведения о публикации и подписке для служебной шины — .Net)</span><span class="sxs-lookup"><span data-stu-id="38dcc-122">[Service Bus Publish/Subscribe Basics - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/)</span></span>
- <span data-ttu-id="38dcc-123">[Getting Started with Service - Service Bus Publish Subscribe Advance Features - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/) (Начало работы со службой: расширенные функции публикации и подписки для служебной шины — .Net)</span><span class="sxs-lookup"><span data-stu-id="38dcc-123">[Service Bus Publish/Subscribe Advanced Features - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/)</span></span>
- <span data-ttu-id="38dcc-124">[Getting Started with Service - Service Bus With Claim Based Authorization - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/) (Начало работы со службой: служебная шина с авторизацией на основе утверждения — .Net)</span><span class="sxs-lookup"><span data-stu-id="38dcc-124">[Service Bus with Claims-Based Authorization - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/)</span></span>

<span data-ttu-id="38dcc-125">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?term=service+bus) примеров кода для служебной шины Azure.</span><span class="sxs-lookup"><span data-stu-id="38dcc-125">View the [complete list](https://azure.microsoft.com/resources/samples/?term=service+bus) of Azure Service Bus samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
