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
# <a name="azure-stream-analytics-libraries-for-net"></a>Библиотеки Azure Stream Analytics для .NET

## <a name="overview"></a>Обзор

[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction) — это полностью управляемый модуль обработки событий, который позволяет в режиме реального времени настраивать аналитические вычисления для потоковой передачи данных. Данные могут поступать от устройств, датчиков, веб-сайтов, каналов социальных сетей, приложений, систем инфраструктуры и других источников. 

Дополнительные сведения об Azure Stream Analytics см. в статье [Приступая к работе с Azure Stream Analytics: выявление мошенничества в режиме реального времени](/azure/stream-analytics/stream-analytics-real-time-fraud-detection).


## <a name="management-library"></a>Библиотека управления

Библиотека управления Azure Stream Analytics позволяет создавать, запускать и останавливать задания Azure Stream Analytics.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.StreamAnalytics
```

```bash
dotnet add package Microsoft.Azure.Management.StreamAnalytics
```

### <a name="code-example"></a>Пример кода

В этом примере создаются экземпляр клиента Stream Analytics и задание потоковой передачи.

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
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/streamanalytics/management)


## <a name="samples"></a>Примеры

- [Управление SDK для .NET: настройка и запуск заданий аналитики с помощью API Azure Stream Analytics для .NET](/azure/stream-analytics/stream-analytics-dotnet-management-sdk)

См. [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics) примеров для Azure Stream Analytics.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
