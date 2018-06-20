---
title: Библиотеки концентраторов событий Azure для .NET
description: Справочник по библиотекам концентраторов событий Azure для .NET
keywords: Azure, .NET, SDK, API, Event Hubs
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: event-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 2ec234959ffc46d2399d1c763e05f173a311b0d2
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2017
ms.locfileid: "23487297"
---
# <a name="azure-event-hubs-libraries-for-net"></a><span data-ttu-id="5cc0d-104">Библиотеки концентраторов событий Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="5cc0d-104">Azure Event Hubs libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="5cc0d-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="5cc0d-105">Overview</span></span>

<span data-ttu-id="5cc0d-106">Концентраторы событий Azure представляют собой платформу потоковой передачи с высокой степенью масштабируемости и службу приема событий.</span><span class="sxs-lookup"><span data-stu-id="5cc0d-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service.</span></span>

<span data-ttu-id="5cc0d-107">Дополнительные сведения о концентраторах событий Azure см. в статье [Что такое концентраторы событий?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span><span class="sxs-lookup"><span data-stu-id="5cc0d-107">To learn more about Azure Event Hubs, read the article [What is Event Hubs?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span></span>  <span data-ttu-id="5cc0d-108">Чтобы приступить к работе, ознакомьтесь со статьей [Руководство по программированию концентраторов событий](/azure/event-hubs/event-hubs-programming-guide).</span><span class="sxs-lookup"><span data-stu-id="5cc0d-108">To get started, check out the [Event Hubs Programming Guide](/azure/event-hubs/event-hubs-programming-guide).</span></span>

## <a name="client-library"></a><span data-ttu-id="5cc0d-109">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="5cc0d-109">Client library</span></span>

<span data-ttu-id="5cc0d-110">Используйте клиент концентраторов событий, чтобы отправлять сообщения в концентратор событий и получать их из него.</span><span class="sxs-lookup"><span data-stu-id="5cc0d-110">Use the Event Hubs client to send and receive messages to and from Event Hubs.</span></span>

<span data-ttu-id="5cc0d-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5cc0d-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5cc0d-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5cc0d-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a><span data-ttu-id="5cc0d-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="5cc0d-113">Code Example</span></span>

<span data-ttu-id="5cc0d-114">В коде ниже создается клиент концентраторов событий и в концентратор событий отправляется сообщение.</span><span class="sxs-lookup"><span data-stu-id="5cc0d-114">The following code creates an Event Hubs client and sends a message to the hub.</span></span>

```csharp
EventHubsConnectionStringBuilder connectionStringBuilder = new EventHubsConnectionStringBuilder(eventHubConnectionString)
{
    EntityPath = eventHubEntityPath
};

EventHubClient eventHubClient = EventHubClient.CreateFromConnectionString(connectionStringBuilder.ToString());
string message = $"Message {i}";
Console.WriteLine($"Sending message: {message}");
await eventHubClient.SendAsync(new EventData(Encoding.UTF8.GetBytes(message)));
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cc0d-115">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="5cc0d-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a><span data-ttu-id="5cc0d-116">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="5cc0d-116">Management library</span></span>

<span data-ttu-id="5cc0d-117">При помощи библиотеки управления концентраторов событий можно создавать, обновлять и удалять концентраторы и группы объектов-получателей.</span><span class="sxs-lookup"><span data-stu-id="5cc0d-117">Use the Event Hubs management library to create, update, and remove hubs and consumer groups.</span></span>

<span data-ttu-id="5cc0d-118">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5cc0d-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5cc0d-119">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5cc0d-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a><span data-ttu-id="5cc0d-120">Пример кода</span><span class="sxs-lookup"><span data-stu-id="5cc0d-120">Code Example</span></span>

<span data-ttu-id="5cc0d-121">В коде ниже создается концентратор событий.</span><span class="sxs-lookup"><span data-stu-id="5cc0d-121">The following code creates a new event hub.</span></span>

```csharp
TokenCredentials creds = new TokenCredentials(token);
EventHubManagementClient ehClient = new EventHubManagementClient(creds)
{
    SubscriptionId = subscriptionId
};

EventHubCreateOrUpdateParameters ehParams = new EventHubCreateOrUpdateParameters()
{
    Location = location
};

Console.WriteLine("Creating Event Hub...");
await ehClient.EventHubs.CreateOrUpdateAsync(resourceGroupName, namespaceName, EventHubName, ehParams);
Console.WriteLine("Created Event Hub successfully.");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cc0d-122">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="5cc0d-122">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a><span data-ttu-id="5cc0d-123">Учебники</span><span class="sxs-lookup"><span data-stu-id="5cc0d-123">Tutorials</span></span>

* [<span data-ttu-id="5cc0d-124">Отправка событий в концентраторы событий Azure с помощью платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5cc0d-124">Send events to Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [<span data-ttu-id="5cc0d-125">Получение событий от концентраторов событий Azure с помощью платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5cc0d-125">Receive events from Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a><span data-ttu-id="5cc0d-126">Примеры</span><span class="sxs-lookup"><span data-stu-id="5cc0d-126">Samples</span></span>

* [<span data-ttu-id="5cc0d-127">Примеры концентраторов событий Azure</span><span class="sxs-lookup"><span data-stu-id="5cc0d-127">Azure Event Hubs Samples</span></span>](https://github.com/Azure/azure-event-hubs/tree/master/samples)

<span data-ttu-id="5cc0d-128">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="5cc0d-128">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
