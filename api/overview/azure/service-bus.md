---
title: "Библиотеки служебной шины Azure для .NET"
description: "Справочник по библиотекам служебной Azure шины для .NET"
keywords: Azure, .NET, SDK, API, Service Bus
author: camsoper
ms.author: casoper
manager: douge
ms.date: 08/01/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: d4d3ac982794fc7533b97fe8c053730b4b39ff58
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-service-bus-libraries-for-net"></a><span data-ttu-id="8c2f8-104">Библиотеки служебной шины Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="8c2f8-104">Azure Service Bus libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="8c2f8-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="8c2f8-105">Overview</span></span>

<span data-ttu-id="8c2f8-106">[Служебная шина Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) — это инфраструктура обмена сообщениями, которая размещается между приложениями и позволяет им обмениваться сообщениями для улучшения масштабирования и устойчивости.</span><span class="sxs-lookup"><span data-stu-id="8c2f8-106">[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) is a messaging infrastructure that sits between applications allowing them to exchange messages for improved scale and resiliency.</span></span>

## <a name="client-library"></a><span data-ttu-id="8c2f8-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="8c2f8-107">Client library</span></span>

<span data-ttu-id="8c2f8-108">Установите [пакет NuGet](https://www.nuget.org/packages/WindowsAzure.ServiceBus) непосредственно из [консоли диспетчера пакетов][PackageManager].</span><span class="sxs-lookup"><span data-stu-id="8c2f8-108">Install the [NuGet package](https://www.nuget.org/packages/WindowsAzure.ServiceBus) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8c2f8-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8c2f8-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package WindowsAzure.ServiceBus
```

### <a name="code-example"></a><span data-ttu-id="8c2f8-110">Пример кода</span><span class="sxs-lookup"><span data-stu-id="8c2f8-110">Code Example</span></span>

<span data-ttu-id="8c2f8-111">В этом примере в очередь служебной шины отправляется сообщение.</span><span class="sxs-lookup"><span data-stu-id="8c2f8-111">This example sends a message to a Service Bus queue.</span></span>

```csharp
// using Microsoft.ServiceBus.Messaging;

QueueClient client = QueueClient.CreateFromConnectionString(connectionString, queueName);
BrokeredMessage message = new BrokeredMessage("This is a test message!");
client.Send(message);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c2f8-112">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="8c2f8-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a><span data-ttu-id="8c2f8-113">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="8c2f8-113">Management library</span></span>

<span data-ttu-id="8c2f8-114">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8c2f8-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8c2f8-115">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8c2f8-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="8c2f8-116">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="8c2f8-116">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a><span data-ttu-id="8c2f8-117">Пример кода</span><span class="sxs-lookup"><span data-stu-id="8c2f8-117">Code Example</span></span>

<span data-ttu-id="8c2f8-118">В этом примере создается очередь служебной шины с максимальным размером 1024 МБ.</span><span class="sxs-lookup"><span data-stu-id="8c2f8-118">This example creates a Service Bus queue with a maximum size of 1024 MB.</span></span>

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
> [<span data-ttu-id="8c2f8-119">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="8c2f8-119">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a><span data-ttu-id="8c2f8-120">Примеры</span><span class="sxs-lookup"><span data-stu-id="8c2f8-120">Samples</span></span>

- [<span data-ttu-id="8c2f8-121">Getting Started with Service - Service Bus Queue Basic - in .Net</span><span class="sxs-lookup"><span data-stu-id="8c2f8-121">Service Bus Queue Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/) (Начало работы со службой: основные сведения об очереди служебной шины — .Net)
- [<span data-ttu-id="8c2f8-122">Getting Started with Service - Service Bus Queue Advance Features - in .Net</span><span class="sxs-lookup"><span data-stu-id="8c2f8-122">Service Bus Queue Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/) (Начало работы со службой: расширенные функции очереди служебной шины — .Net)
- [<span data-ttu-id="8c2f8-123">Getting Started with Service - Service Bus Publish Subscribe Basic - in .Net</span><span class="sxs-lookup"><span data-stu-id="8c2f8-123">Service Bus Publish/Subscribe Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/) (Начало работы со службой: основные сведения о публикации и подписке для служебной шины — .Net)
- [<span data-ttu-id="8c2f8-124">Getting Started with Service - Service Bus Publish Subscribe Advance Features - in .Net</span><span class="sxs-lookup"><span data-stu-id="8c2f8-124">Service Bus Publish/Subscribe Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/) (Начало работы со службой: расширенные функции публикации и подписки для служебной шины — .Net)
- [<span data-ttu-id="8c2f8-125">Getting Started with Service - Service Bus With Claim Based Authorization - in .Net</span><span class="sxs-lookup"><span data-stu-id="8c2f8-125">Service Bus with Claims-Based Authorization - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/) (Начало работы со службой: служебная шина с авторизацией на основе утверждения — .Net)

<span data-ttu-id="8c2f8-126">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?term=service+bus) примеров кода для служебной шины Azure.</span><span class="sxs-lookup"><span data-stu-id="8c2f8-126">View the [complete list](https://azure.microsoft.com/resources/samples/?term=service+bus) of Azure Service Bus samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
