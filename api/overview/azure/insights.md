---
title: "Библиотеки Azure Application Insights для .NET"
description: "Справочник по библиотекам Azure Application Insights для .NET"
keywords: Azure, .NET, SDK, API, Application AppInsights
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/24/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 2eef8d322d905679e8aceaed77ba44726c14dd94
ms.sourcegitcommit: fa02d34afbf981f809661ab842b3b93242a38f68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2017
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
