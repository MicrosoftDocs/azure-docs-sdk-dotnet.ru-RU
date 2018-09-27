---
title: Библиотеки выставления счетов Azure для .NET
description: Справочник по библиотекам выставления счетов для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: 88b90c71d29eacf61e4da2099f8a054d74df4a83
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190257"
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
