---
title: Библиотеки Центров событий Azure для .NET
description: Справочник по библиотекам Центров событий Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: event-hubs
ms.openlocfilehash: 74c533bef598b90369009d68a759d35d122a368d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190277"
---
# <a name="azure-event-hubs-libraries-for-net"></a><span data-ttu-id="df70e-103">Библиотеки Центров событий Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="df70e-103">Azure Event Hubs libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="df70e-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="df70e-104">Overview</span></span>

<span data-ttu-id="df70e-105">Центры событий Azure представляют собой платформу потоковой передачи с высокой степенью масштабируемости и службу приема событий.</span><span class="sxs-lookup"><span data-stu-id="df70e-105">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service.</span></span>

<span data-ttu-id="df70e-106">Дополнительные сведения о Центрах событий Azure см. в статье [Что такое Центры событий?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span><span class="sxs-lookup"><span data-stu-id="df70e-106">To learn more about Azure Event Hubs, read the article [What is Event Hubs?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span></span>  <span data-ttu-id="df70e-107">Чтобы приступить к работе, ознакомьтесь со статьей [Руководство по программированию Центров событий](/azure/event-hubs/event-hubs-programming-guide).</span><span class="sxs-lookup"><span data-stu-id="df70e-107">To get started, check out the [Event Hubs Programming Guide](/azure/event-hubs/event-hubs-programming-guide).</span></span>

## <a name="client-library"></a><span data-ttu-id="df70e-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="df70e-108">Client library</span></span>

<span data-ttu-id="df70e-109">Используйте клиент Центров событий, чтобы отправлять сообщения в Центры событий и получать их из Центров событий.</span><span class="sxs-lookup"><span data-stu-id="df70e-109">Use the Event Hubs client to send and receive messages to and from Event Hubs.</span></span>

<span data-ttu-id="df70e-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="df70e-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="df70e-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df70e-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a><span data-ttu-id="df70e-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="df70e-112">Code Example</span></span>

<span data-ttu-id="df70e-113">В коде ниже создается клиент Центров событий и в концентратор событий отправляется сообщение.</span><span class="sxs-lookup"><span data-stu-id="df70e-113">The following code creates an Event Hubs client and sends a message to the hub.</span></span>

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
> [<span data-ttu-id="df70e-114">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="df70e-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a><span data-ttu-id="df70e-115">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="df70e-115">Management library</span></span>

<span data-ttu-id="df70e-116">При помощи библиотеки управления Центров событий можно создавать, обновлять и удалять концентраторы и группы объектов-получателей.</span><span class="sxs-lookup"><span data-stu-id="df70e-116">Use the Event Hubs management library to create, update, and remove hubs and consumer groups.</span></span>

<span data-ttu-id="df70e-117">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="df70e-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="df70e-118">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df70e-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a><span data-ttu-id="df70e-119">Пример кода</span><span class="sxs-lookup"><span data-stu-id="df70e-119">Code Example</span></span>

<span data-ttu-id="df70e-120">В коде ниже создается концентратор событий.</span><span class="sxs-lookup"><span data-stu-id="df70e-120">The following code creates a new event hub.</span></span>

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
> [<span data-ttu-id="df70e-121">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="df70e-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a><span data-ttu-id="df70e-122">Учебники</span><span class="sxs-lookup"><span data-stu-id="df70e-122">Tutorials</span></span>

* [<span data-ttu-id="df70e-123">Отправка событий в Центры событий Azure с помощью платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df70e-123">Send events to Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [<span data-ttu-id="df70e-124">Получение событий от Центров событий Azure с помощью платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df70e-124">Receive events from Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a><span data-ttu-id="df70e-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="df70e-125">Samples</span></span>

* [<span data-ttu-id="df70e-126">Примеры Центров событий Azure</span><span class="sxs-lookup"><span data-stu-id="df70e-126">Azure Event Hubs Samples</span></span>](https://github.com/Azure/azure-event-hubs/tree/master/samples)

<span data-ttu-id="df70e-127">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="df70e-127">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
