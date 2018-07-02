---
title: Библиотеки выставления счетов Azure для .NET
description: Справочник по библиотекам выставления счетов для .NET
keywords: Azure, .NET, SDK, API, Billing
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 97a4c642e8be03db7e31e8c9bc71dcf9c3fc1447
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065514"
---
# <a name="azure-billing-libraries-for-net"></a>Библиотеки выставления счетов Azure для .NET

## <a name="overview"></a>Обзор

API выставления счетов Azure (предварительная версия) предоставляет программный доступ к счетам и сведениям об их выставлении в Azure.

## <a name="management-library"></a>Библиотека управления

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a>Пример кода

Подключитесь к Azure и получите список счетов.

```csharp
/* Include these directives
using Microsoft.Rest.Azure.Authentication;
using Microsoft.Azure.Management.Billing;
using Microsoft.Azure.Management.Billing.Models;
*/

// Log into Azure
var serviceCreds = ApplicationTokenProvider.LoginSilentAsync(tenantId, clientId, secret);
var billingClient = new BillingClient(serviceCreds);
billingClient.SubscriptionId = subscriptionId;

// Get list of invoices
billingClient.Invoices.List();
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a>Примеры

* [Microsoft Azure Billing API Code Samples: Usage API](https://github.com/Azure-Samples/billing-dotnet-usage-api) (Примеры кода для API выставления счетов Microsoft Azure: API использования)
* [Microsoft Azure Billing API Code Samples: RateCard API](https://github.com/Azure-Samples/billing-dotnet-ratecard-api) (Примеры кода для API выставления счетов Microsoft Azure: API RateCard)
* [Microsoft Azure Billing API Code Samples: Multi-Tenant Web Application](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant) (Примеры кода для API выставления счетов Microsoft Azure: мультитенантное веб-приложение)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
