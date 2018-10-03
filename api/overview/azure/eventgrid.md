---
title: Библиотеки службы "Сетка событий Azure" для .NET
description: Справочник по библиотекам службы "Сетка событий Azure" для .NET
ms.date: 04/16/2018
ms.topic: reference
ms.service: event-grid
ms.openlocfilehash: 5b19f8aa8b28b3e4aef528da051b6e7d177f1a2f
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190397"
---
# <a name="azure-event-grid-libraries-for-net"></a><span data-ttu-id="e111d-103">Библиотеки службы "Сетка событий Azure" для .NET</span><span class="sxs-lookup"><span data-stu-id="e111d-103">Azure Event Grid libraries for .NET</span></span>

<span data-ttu-id="e111d-104">Создавайте управляемые событиями приложения, которые прослушивают события от служб Azure и пользовательских источников и реагируют на них, с помощью службы "Сетка событий Azure" и простых средств обработки событий на основе HTTP.</span><span class="sxs-lookup"><span data-stu-id="e111d-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="e111d-105">См. дополнительные сведения о [службе "Сетка событий Azure"](/azure/event-grid/overview) и начните работу с помощью [краткого руководства по событиям хранилища BLOB-объектов Azure](/azure/storage/blobs/storage-blob-event-quickstart-powershell).</span><span class="sxs-lookup"><span data-stu-id="e111d-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart-powershell).</span></span> 

## <a name="client-sdk"></a><span data-ttu-id="e111d-106">Клиентский пакет SDK</span><span class="sxs-lookup"><span data-stu-id="e111d-106">Client SDK</span></span>

<span data-ttu-id="e111d-107">Создавайте события, выполняйте аутентификацию и публикацию в разделы с помощью клиентского пакета SDK для службы "Сетка событий Azure".</span><span class="sxs-lookup"><span data-stu-id="e111d-107">Create events, authenticate, and post to topics using the Azure Event Grid Client SDK.</span></span>

<span data-ttu-id="e111d-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="e111d-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="e111d-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e111d-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="e111d-110">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e111d-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.EventGrid 
```

### <a name="publish-events"></a><span data-ttu-id="e111d-111">Публикация событий</span><span class="sxs-lookup"><span data-stu-id="e111d-111">Publish events</span></span>

<span data-ttu-id="e111d-112">Следующий код выполняет аутентификацию с помощью Azure и публикует `List` из событий `EventGridEvent` пользовательского типа (в этом примере — `Contoso.Items.ItemsReceivedEvent`) в раздел.</span><span class="sxs-lookup"><span data-stu-id="e111d-112">The following code authenticates with Azure and publishes a `List` of  `EventGridEvent` events of a custom type (in this example, `Contoso.Items.ItemsReceivedEvent` ) to a topic.</span></span> <span data-ttu-id="e111d-113">Раздел ключа и адрес конечной точки, используемые в примере, можно получить с помощью Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e111d-113">The topic key and endpoint address used in the sample can be retrieved from Azure PowerShell:</span></span>

```powershell
$endpoint = (Get-AzureRmEventGridTopic -ResourceGroupName gridResourceGroup -Name <topic-name>).Endpoint
$keys = Get-AzureRmEventGridTopicKey -ResourceGroupName gridResourceGroup -Name <topic-name>
```

```csharp
string topicEndpoint = "https://<topic-name>.<region>-1.eventgrid.azure.net/api/events";
string topicKey = "<topic-key>";
string topicHostname = new Uri(topicEndpoint).Host;

TopicCredentials topicCredentials = new TopicCredentials(topicKey);
EventGridClient client = new EventGridClient(topicCredentials);

client.PublishEventsAsync(topicHostname, GetEventsList()).GetAwaiter().GetResult();
Console.Write("Published events to Event Grid.");

static IList<EventGridEvent> GetEventsList()
{
    List<EventGridEvent> eventsList = new List<EventGridEvent>();
    for (int i = 0; i < 1; i++)
    {
        eventsList.Add(new EventGridEvent()
        {
            Id = Guid.NewGuid().ToString(),
            EventType = "Contoso.Items.ItemReceivedEvent",
            Data = new ContosoItemReceivedEventData()
            {
                ItemUri = "ContosoSuperItemUri"
            },

            EventTime = DateTime.Now,
            Subject = "Door1",
            DataVersion = "2.0"
        });
    }
    return eventsList;
}
```

### <a name="consume-events"></a><span data-ttu-id="e111d-114">Получение событий</span><span class="sxs-lookup"><span data-stu-id="e111d-114">Consume events</span></span>

<span data-ttu-id="e111d-115">Этот фрагмент получает события, включая пользовательское событие `Contoso.Items.ItemsReceived`, а также события, вызываемые из других служб Azure, таких как хранилище BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="e111d-115">This snippet consumes events, including a custom event `Contoso.Items.ItemsReceived` as well as events triggered from other Azure services, such as Blob Storage.</span></span>

```csharp
string response = string.Empty;
string requestContent = await req.Content.ReadAsStringAsync();

EventGridSubscriber eventGridSubscriber = new EventGridSubscriber();

// Optionally add one or more custom event type mappings
eventGridSubscriber.AddOrUpdateCustomEventMapping("Contoso.Items.ItemReceived", typeof(ContosoItemReceivedEventData));

var events = eventGridSubscriber.DeserializeEventGridEvents(requestContent);            
 
foreach (EventGridEvent receivedEvent in events)
{
    if (receivedEvent.Data is SubscriptionValidationEventData)
    {
        SubscriptionValidationEventData eventData = (SubscriptionValidationEventData)receivedEvent.Data;
        log.Info($"Got SubscriptionValidation event data, validationCode: {eventData.ValidationCode},  validationUrl: {eventData.ValidationUrl}, topic: {eventGridEvent.Topic}");
        // Handle subscription validation
    }
    else if (receivedEvent.Data is StorageBlobCreatedEventData)
    {
        StorageBlobCreatedEventData eventData = (StorageBlobCreatedEventData)receivedEvent.Data;
        log.Info($"Got BlobCreated event data, blob URI {eventData.Url}");
        // Handle StorageBlobCreatedEventData
    }
    else if (receivedEvent.Data is ContosoItemReceivedEventData)
    {
        ContosoItemReceivedEventData eventData = (ContosoItemReceivedEventData)receivedEvent.Data;
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="e111d-116">Подробнее об осуществляющих публикацию API</span><span class="sxs-lookup"><span data-stu-id="e111d-116">Explore the publishing APIs</span></span>](/dotnet/api/overview/azure/eventgrid/publish)

## <a name="management-sdk"></a><span data-ttu-id="e111d-117">Пакет SDK для управления</span><span class="sxs-lookup"><span data-stu-id="e111d-117">Management SDK</span></span>

<span data-ttu-id="e111d-118">Создавайте, обновляйте и удаляйте экземпляры, разделы и подписки службы "Сетка событий" с помощью пакета SDK для управления.</span><span class="sxs-lookup"><span data-stu-id="e111d-118">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

<span data-ttu-id="e111d-119">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="e111d-119">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="e111d-120">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e111d-120">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="e111d-121">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e111d-121">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.EventGrid
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="e111d-122">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="e111d-122">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="e111d-123">Подробнее</span><span class="sxs-lookup"><span data-stu-id="e111d-123">Learn more</span></span>

- [<span data-ttu-id="e111d-124">Получение событий с помощью пакета SDK службы "Сетка событий"</span><span class="sxs-lookup"><span data-stu-id="e111d-124">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
