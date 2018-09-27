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
# <a name="azure-application-insights-libraries-for-net"></a>Библиотеки Azure Application Insights для .NET

## <a name="overview"></a>Обзор

Application Insights — это расширяемая служба мониторинга и диагностики для веб-разработчиков, предоставляющая мощные возможности ad-hoc-аналитики. Вы можете использовать классы в пространстве имен ApplicationInsights, чтобы настроить сбор данных телеметрии и отправлять любые данные настроенной телеметрии из приложения, для которого нужно выполнять мониторинг.

## <a name="client-library"></a>Клиентская библиотека

Клиентский пакет SDK Application Insights для .NET позволяет регистрировать события, статистические данные, исключения, зависимости и метрики в Azure для последующего анализа.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a>Пример

В этом примере отслеживается пользовательское событие в Application Insights.

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a>Примеры

- [Application Insights Analytics with OpenSchema](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/) (Аналитика Application Insights с OpenSchema)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) примеров Azure Application Insights.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
