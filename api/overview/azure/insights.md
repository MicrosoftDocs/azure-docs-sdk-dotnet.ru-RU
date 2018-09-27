---
title: Библиотеки Azure Application Insights для .NET
description: Справочник по библиотекам Azure Application Insights для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: application-insights
ms.openlocfilehash: 10b65f536c6461959b0be9b8f9bd3ec56a307bea
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190843"
---
# <a name="azure-application-insights-libraries-for-net"></a><span data-ttu-id="62f41-103">Библиотеки Azure Application Insights для .NET</span><span class="sxs-lookup"><span data-stu-id="62f41-103">Azure Application Insights libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="62f41-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="62f41-104">Overview</span></span>

<span data-ttu-id="62f41-105">Application Insights — это расширяемая служба мониторинга и диагностики для веб-разработчиков, предоставляющая мощные возможности ad-hoc-аналитики.</span><span class="sxs-lookup"><span data-stu-id="62f41-105">Application Insights is an extensible monitoring & diagnostics service for web developers with powerful ad-hoc analytics capabilities.</span></span> <span data-ttu-id="62f41-106">Вы можете использовать классы в пространстве имен ApplicationInsights, чтобы настроить сбор данных телеметрии и отправлять любые данные настроенной телеметрии из приложения, для которого нужно выполнять мониторинг.</span><span class="sxs-lookup"><span data-stu-id="62f41-106">You can use the classes in the ApplicationInsights namespace to configure telemetry collection and send any custom telemetry from your applications that you want to monitor.</span></span>

## <a name="client-library"></a><span data-ttu-id="62f41-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="62f41-107">Client library</span></span>

<span data-ttu-id="62f41-108">Клиентский пакет SDK Application Insights для .NET позволяет регистрировать события, статистические данные, исключения, зависимости и метрики в Azure для последующего анализа.</span><span class="sxs-lookup"><span data-stu-id="62f41-108">The Application Insights client SDK for .NET allows you to log event, aggregated data, exceptions, dependency, and metrics to Azure for future analysis.</span></span>

<span data-ttu-id="62f41-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="62f41-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="62f41-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="62f41-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a><span data-ttu-id="62f41-111">Пример</span><span class="sxs-lookup"><span data-stu-id="62f41-111">Example</span></span>

<span data-ttu-id="62f41-112">В этом примере отслеживается пользовательское событие в Application Insights.</span><span class="sxs-lookup"><span data-stu-id="62f41-112">This example tracks a custom event to Application Insights.</span></span>

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="62f41-113">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="62f41-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a><span data-ttu-id="62f41-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="62f41-114">Samples</span></span>

- <span data-ttu-id="62f41-115">[Application Insights Analytics with OpenSchema](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/) (Аналитика Application Insights с OpenSchema)</span><span class="sxs-lookup"><span data-stu-id="62f41-115">[Application Insights Analytics with OpenSchema](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)</span></span>

<span data-ttu-id="62f41-116">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) примеров Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="62f41-116">View the [complete list](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) of Azure Application Insights samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
