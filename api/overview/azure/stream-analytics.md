---
title: Библиотеки Azure Stream Analytics для .NET
description: Справочник по библиотекам Azure Stream Analytics для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: stream-analytics
ms.openlocfilehash: c04a5c8a7b1d7e0f283d4fb81bd772de24f195eb
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190457"
---
# <a name="azure-stream-analytics-libraries-for-net"></a><span data-ttu-id="9bc5e-103">Библиотеки Azure Stream Analytics для .NET</span><span class="sxs-lookup"><span data-stu-id="9bc5e-103">Azure Stream Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9bc5e-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="9bc5e-104">Overview</span></span>

<span data-ttu-id="9bc5e-105">[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction) — это полностью управляемый модуль обработки событий, который позволяет в режиме реального времени настраивать аналитические вычисления для потоковой передачи данных.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-105">[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction) is a fully managed event-processing engine that lets you set up real-time analytic computations on streaming data.</span></span> <span data-ttu-id="9bc5e-106">Данные могут поступать от устройств, датчиков, веб-сайтов, каналов социальных сетей, приложений, систем инфраструктуры и других источников.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-106">The data can come from devices, sensors, web sites, social media feeds, applications, infrastructure systems, and more.</span></span> 

<span data-ttu-id="9bc5e-107">Дополнительные сведения об Azure Stream Analytics см. в статье [Приступая к работе с Azure Stream Analytics: выявление мошенничества в режиме реального времени](/azure/stream-analytics/stream-analytics-real-time-fraud-detection).</span><span class="sxs-lookup"><span data-stu-id="9bc5e-107">To learn more about Azure Stream Analytics, see [Get started with Azure Stream Analytics Real-time fraud detection](/azure/stream-analytics/stream-analytics-real-time-fraud-detection).</span></span>


## <a name="management-library"></a><span data-ttu-id="9bc5e-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="9bc5e-108">Management library</span></span>

<span data-ttu-id="9bc5e-109">Библиотека управления Azure Stream Analytics позволяет создавать, запускать и останавливать задания Azure Stream Analytics.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-109">Use the Azure Stream Analytics management library to create, start, and stop Azure Stream Analytics jobs.</span></span>

<span data-ttu-id="9bc5e-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9bc5e-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9bc5e-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9bc5e-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StreamAnalytics
```

```bash
dotnet add package Microsoft.Azure.Management.StreamAnalytics
```

### <a name="code-example"></a><span data-ttu-id="9bc5e-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="9bc5e-112">Code Example</span></span>

<span data-ttu-id="9bc5e-113">В этом примере создаются экземпляр клиента Stream Analytics и задание потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-113">This example instantiates a Stream Analytics client and creates a streaming job.</span></span>

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
> [<span data-ttu-id="9bc5e-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="9bc5e-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/streamanalytics/management)


## <a name="samples"></a><span data-ttu-id="9bc5e-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="9bc5e-115">Samples</span></span>

- [<span data-ttu-id="9bc5e-116">Управление SDK для .NET: настройка и запуск заданий аналитики с помощью API Azure Stream Analytics для .NET</span><span class="sxs-lookup"><span data-stu-id="9bc5e-116">Management .NET SDK: Set up and run analytics jobs using the Azure Stream Analytics API for .NET</span></span>](/azure/stream-analytics/stream-analytics-dotnet-management-sdk)

<span data-ttu-id="9bc5e-117">См. [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics) примеров для Azure Stream Analytics.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-117">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics) of Azure Stream Analytics samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
