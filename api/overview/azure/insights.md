---
title: Библиотеки Azure Application Insights для .NET
description: Справочник по библиотекам Azure Application Insights для .NET
keywords: Azure, .NET, SDK, API, Application AppInsights
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: application-insights
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 3cbd4a874edfa6de26d3edf4d151d2c4006ab9c3
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065844"
---
# <a name="azure-application-insights-libraries-for-net"></a><span data-ttu-id="b74aa-104">Библиотеки Azure Application Insights для .NET</span><span class="sxs-lookup"><span data-stu-id="b74aa-104">Azure Application Insights libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b74aa-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="b74aa-105">Overview</span></span>

<span data-ttu-id="b74aa-106">Application Insights — это расширяемая служба мониторинга и диагностики для веб-разработчиков, предоставляющая мощные возможности ad-hoc-аналитики.</span><span class="sxs-lookup"><span data-stu-id="b74aa-106">Application Insights is an extensible monitoring & diagnostics service for web developers with powerful ad-hoc analytics capabilities.</span></span> <span data-ttu-id="b74aa-107">Вы можете использовать классы в пространстве имен ApplicationInsights, чтобы настроить сбор данных телеметрии и отправлять любые данные настроенной телеметрии из приложения, для которого нужно выполнять мониторинг.</span><span class="sxs-lookup"><span data-stu-id="b74aa-107">You can use the classes in the ApplicationInsights namespace to configure telemetry collection and send any custom telemetry from your applications that you want to monitor.</span></span>

## <a name="client-library"></a><span data-ttu-id="b74aa-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="b74aa-108">Client library</span></span>

<span data-ttu-id="b74aa-109">Клиентский пакет SDK Application Insights для .NET позволяет регистрировать события, статистические данные, исключения, зависимости и метрики в Azure для последующего анализа.</span><span class="sxs-lookup"><span data-stu-id="b74aa-109">The Application Insights client SDK for .NET allows you to log event, aggregated data, exceptions, dependency, and metrics to Azure for future analysis.</span></span>

<span data-ttu-id="b74aa-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="b74aa-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b74aa-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b74aa-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a><span data-ttu-id="b74aa-112">Пример</span><span class="sxs-lookup"><span data-stu-id="b74aa-112">Example</span></span>

<span data-ttu-id="b74aa-113">В этом примере отслеживается пользовательское событие в Application Insights.</span><span class="sxs-lookup"><span data-stu-id="b74aa-113">This example tracks a custom event to Application Insights.</span></span>

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b74aa-114">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="b74aa-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a><span data-ttu-id="b74aa-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="b74aa-115">Samples</span></span>

- <span data-ttu-id="b74aa-116">[Application Insights Analytics with OpenSchema](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/) (Аналитика Application Insights с OpenSchema)</span><span class="sxs-lookup"><span data-stu-id="b74aa-116">[Application Insights Analytics with OpenSchema](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)</span></span>

<span data-ttu-id="b74aa-117">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) примеров Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="b74aa-117">View the [complete list](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) of Azure Application Insights samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
