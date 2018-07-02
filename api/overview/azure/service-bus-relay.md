---
title: Библиотеки ретранслятора служебной шины Azure для .NET
description: Справочник по библиотекам ретранслятора служебной Azure шины для .NET
keywords: Azure, .NET, SDK, API, Service Bus Relay
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: service-bus
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e0dd9c9b0a187fe6ca81d764e60afd00cbaab654
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065954"
---
# <a name="azure-service-bus-relay-libraries-for-net"></a>Библиотеки ретранслятора служебной шины Azure для .NET

## <a name="overview"></a>Обзор

Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети. Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.
          
См. дополнительные сведения о [ретрансляторе Azure](/azure/service-bus-relay/relay-what-is-it).

## <a name="client-library"></a>Клиентская библиотека

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a>Примеры

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package