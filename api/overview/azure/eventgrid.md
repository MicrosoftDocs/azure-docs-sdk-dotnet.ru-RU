---
title: Библиотеки службы "Сетка событий Azure" для .NET
description: Справочник по библиотекам службы "Сетка событий Azure" для .NET
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 04/16/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: aa25f76f041e890de512c67d9380903f81216f62
ms.sourcegitcommit: 9f54e3334fc35c1066d0c591ff85b16d46416aa8
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="azure-event-grid-libraries-for-net"></a><span data-ttu-id="4ead4-103">Библиотеки службы "Сетка событий Azure" для .NET</span><span class="sxs-lookup"><span data-stu-id="4ead4-103">Azure Event Grid libraries for .NET</span></span>

<span data-ttu-id="4ead4-104">Создавайте управляемые событиями приложения, которые прослушивают события от служб Azure и пользовательских источников и реагируют на них, с помощью службы "Сетка событий Azure" и простых средств обработки событий на основе HTTP.</span><span class="sxs-lookup"><span data-stu-id="4ead4-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="4ead4-105">См. дополнительные сведения о [службе "Сетка событий Azure"](/azure/event-grid/overview) и начните работу с помощью [краткого руководства по событиям хранилища BLOB-объектов Azure](/azure/storage/blobs/storage-blob-event-quickstart-powershell).</span><span class="sxs-lookup"><span data-stu-id="4ead4-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart-powershell).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="4ead4-106">Пакет SDK для публикации</span><span class="sxs-lookup"><span data-stu-id="4ead4-106">Publish SDK</span></span>

<span data-ttu-id="4ead4-107">Создавайте события, выполняйте аутентификацию и публикацию в разделы с помощью пакета SDK для публикации службы "Сетка событий Azure".</span><span class="sxs-lookup"><span data-stu-id="4ead4-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

<span data-ttu-id="4ead4-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4ead4-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4ead4-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ead4-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="4ead4-110">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="4ead4-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.EventGrid 
```

### <a name="sample-usage"></a><span data-ttu-id="4ead4-111">Пример использования</span><span class="sxs-lookup"><span data-stu-id="4ead4-111">Sample usage</span></span>

<span data-ttu-id="4ead4-112">Следующий код выполняет аутентификацию с помощью Azure и публикует `List` из событий `EventGridEvent` пользовательского типа (в этом примере — `Contoso.Items.ItemsReceivedEvent`) в раздел.</span><span class="sxs-lookup"><span data-stu-id="4ead4-112">The following code authenticates with Azure and publishes a `List` of  `EventGridEvent` events of a custom type (in this example, `Contoso.Items.ItemsReceivedEvent` ) to a topic.</span></span> <span data-ttu-id="4ead4-113">Раздел ключа и адрес конечной точки, используемые в примере, можно получить с помощью Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4ead4-113">The topic key and endpoint address used in the sample can be retrieved from Azure PowerShell:</span></span>

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

<span data-ttu-id="4ead4-114">Этот фрагмент обрабатывает события, опубликованные при создании большого двоичного объекта в [службе хранилища Azure](/azure/storage/blobs/storage-blob-event-overview).</span><span class="sxs-lookup"><span data-stu-id="4ead4-114">This snippet handles events published when creating a new blob in [Azure Storage](/azure/storage/blobs/storage-blob-event-overview).</span></span>

```csharp
string response = string.Empty;
const string SubscriptionValidationEvent = "Microsoft.EventGrid.SubscriptionValidationEvent";
const string StorageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

string requestContent = await req.Content.ReadAsStringAsync();
EventGridEvent[] eventGridEvents = JsonConvert.DeserializeObject<EventGridEvent[]>(requestContent);

foreach (EventGridEvent eventGridEvent in eventGridEvents)
{
    JObject dataObject = eventGridEvent.Data as JObject;

    // Deserialize the event data into the appropriate type based on event type 
    if (string.Equals(eventGridEvent.EventType, SubscriptionValidationEvent, StringComparison.OrdinalIgnoreCase))
    {
        var eventData = dataObject.ToObject<SubscriptionValidationEventData>();
        log.Info($"Got SubscriptionValidation event data, validation code: {eventData.ValidationCode}, topic: {eventGridEvent.Topic}");

        // Do any additional validation (as required) and then return back the below response
        var responseData = new SubscriptionValidationResponseData();
        responseData.ValidationResponse = eventData.ValidationCode;
        return req.CreateResponse(HttpStatusCode.OK, responseData);
    }

    else if (string.Equals(eventGridEvent.EventType, StorageBlobCreatedEvent, StringComparison.OrdinalIgnoreCase))
    {
        var eventData = dataObject.ToObject<StorageBlobCreatedEventData>();
        log.Info($"Got BlobCreated event data, blob URI {eventData.Url}");
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ead4-115">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="4ead4-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="4ead4-116">Пакет SDK для управления</span><span class="sxs-lookup"><span data-stu-id="4ead4-116">Management SDK</span></span>

<span data-ttu-id="4ead4-117">Создавайте, обновляйте и удаляйте экземпляры, разделы и подписки службы "Сетка событий" с помощью пакета SDK для управления.</span><span class="sxs-lookup"><span data-stu-id="4ead4-117">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

<span data-ttu-id="4ead4-118">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4ead4-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4ead4-119">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ead4-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="4ead4-120">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="4ead4-120">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.EventGrid
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ead4-121">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="4ead4-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="4ead4-122">Подробнее</span><span class="sxs-lookup"><span data-stu-id="4ead4-122">Learn more</span></span>

- [<span data-ttu-id="4ead4-123">Получение событий с помощью пакета SDK службы "Сетка событий"</span><span class="sxs-lookup"><span data-stu-id="4ead4-123">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
