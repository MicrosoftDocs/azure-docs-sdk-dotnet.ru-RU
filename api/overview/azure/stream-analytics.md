---
title: "Библиотеки Azure Stream Analytics для .NET"
description: "Справочник по библиотекам Azure Stream Analytics для .NET"
keywords: Azure, .NET, SDK, API, Stream Analytics
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: b812f0948b2153d717987fbc6912ed4665154b3f
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
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