---
title: "Библиотеки Azure Stream Analytics для .NET"
description: "Справочник по библиотекам Azure Stream Analytics для .NET"
keywords: Azure, .NET, SDK, API, Stream Analytics
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: stream-analytics
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 2a5e8b8481548d6cfebc5104eb459f8772f51462
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2017
---
# <a name="azure-stream-analytics-libraries-for-net"></a><span data-ttu-id="e2def-104">Библиотеки Azure Stream Analytics для .NET</span><span class="sxs-lookup"><span data-stu-id="e2def-104">Azure Stream Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="e2def-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="e2def-105">Overview</span></span>

<span data-ttu-id="e2def-106">[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction) — это полностью управляемый модуль обработки событий, который позволяет в режиме реального времени настраивать аналитические вычисления для потоковой передачи данных.</span><span class="sxs-lookup"><span data-stu-id="e2def-106">[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction) is a fully managed event-processing engine that lets you set up real-time analytic computations on streaming data.</span></span> <span data-ttu-id="e2def-107">Данные могут поступать от устройств, датчиков, веб-сайтов, каналов социальных сетей, приложений, систем инфраструктуры и других источников.</span><span class="sxs-lookup"><span data-stu-id="e2def-107">The data can come from devices, sensors, web sites, social media feeds, applications, infrastructure systems, and more.</span></span> 

<span data-ttu-id="e2def-108">Дополнительные сведения об Azure Stream Analytics см. в статье [Приступая к работе с Azure Stream Analytics: выявление мошенничества в режиме реального времени](/azure/stream-analytics/stream-analytics-real-time-fraud-detection).</span><span class="sxs-lookup"><span data-stu-id="e2def-108">To learn more about Azure Stream Analytics, see [Get started with Azure Stream Analytics Real-time fraud detection](/azure/stream-analytics/stream-analytics-real-time-fraud-detection).</span></span>


## <a name="management-library"></a><span data-ttu-id="e2def-109">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="e2def-109">Management library</span></span>

<span data-ttu-id="e2def-110">Библиотека управления Azure Stream Analytics позволяет создавать, запускать и останавливать задания Azure Stream Analytics.</span><span class="sxs-lookup"><span data-stu-id="e2def-110">Use the Azure Stream Analytics management library to create, start, and stop Azure Stream Analytics jobs.</span></span>

<span data-ttu-id="e2def-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="e2def-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="e2def-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e2def-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StreamAnalytics
```

```bash
dotnet add package Microsoft.Azure.Management.StreamAnalytics
```

### <a name="code-example"></a><span data-ttu-id="e2def-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="e2def-113">Code Example</span></span>

<span data-ttu-id="e2def-114">В этом примере создаются экземпляр клиента Stream Analytics и задание потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="e2def-114">This example instantiates a Stream Analytics client and creates a streaming job.</span></span>

```csharp
/* Include these 'using' directives:
using Microsoft.Azure.Management.StreamAnalytics;
*/
SynchronizationContext.SetSynchronizationContext(new SynchronizationContext());

// Get credentials
ServiceClientCredentials credentials = GetCredentials().Result;

// Create Stream Analytics management client
StreamAnalyticsManagementClient streamAnalyticsManagementClient = new StreamAnalyticsManagementClient(credentials)
{
    SubscriptionId = subscriptionId
};

// Create a streaming job
StreamingJob streamingJob = new StreamingJob()
{
    Tags = new Dictionary<string, string>()
    {
        { "Origin", ".NET SDK" },
        { "ReasonCreated", "Getting started tutorial" }
    },
    Location = "West US",
    EventsOutOfOrderPolicy = EventsOutOfOrderPolicy.Drop,
    EventsOutOfOrderMaxDelayInSeconds = 5,
    EventsLateArrivalMaxDelayInSeconds = 16,
    OutputErrorPolicy = OutputErrorPolicy.Drop,
    DataLocale = "en-US",
    CompatibilityLevel = CompatibilityLevel.OneFullStopZero,
    Sku = new Sku()
    {
        Name = SkuName.Standard
    }
};
StreamingJob createStreamingJobResult = streamAnalyticsManagementClient.StreamingJobs.CreateOrReplace(streamingJob, resourceGroupName, streamingJobName);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="e2def-115">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="e2def-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/streamanalytics/management)


## <a name="samples"></a><span data-ttu-id="e2def-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="e2def-116">Samples</span></span>

- [<span data-ttu-id="e2def-117">Управление SDK для .NET: настройка и запуск заданий аналитики с помощью API Azure Stream Analytics для .NET</span><span class="sxs-lookup"><span data-stu-id="e2def-117">Management .NET SDK: Set up and run analytics jobs using the Azure Stream Analytics API for .NET</span></span>](/azure/stream-analytics/stream-analytics-dotnet-management-sdk)

<span data-ttu-id="e2def-118">См. [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics) примеров для Azure Stream Analytics.</span><span class="sxs-lookup"><span data-stu-id="e2def-118">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics) of Azure Stream Analytics samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
