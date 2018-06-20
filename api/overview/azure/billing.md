---
title: Библиотеки выставления счетов Azure для .NET
description: Справочник по библиотекам выставления счетов для .NET
keywords: Azure, .NET, SDK, API, Billing
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 8df15d55a80991f29b694f4af06a20514bf20b32
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566085"
---
# <a name="azure-billing-libraries-for-net"></a><span data-ttu-id="5703e-104">Библиотеки выставления счетов Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="5703e-104">Azure Billing libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="5703e-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="5703e-105">Overview</span></span>

<span data-ttu-id="5703e-106">API выставления счетов Azure (предварительная версия) предоставляет программный доступ к счетам и сведениям об их выставлении в Azure.</span><span class="sxs-lookup"><span data-stu-id="5703e-106">Azure Billing API (preview) provides programmatic access to your Azure billing information and invoices.</span></span>

## <a name="management-library"></a><span data-ttu-id="5703e-107">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="5703e-107">Management library</span></span>

<span data-ttu-id="5703e-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5703e-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5703e-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5703e-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a><span data-ttu-id="5703e-110">Пример кода</span><span class="sxs-lookup"><span data-stu-id="5703e-110">Code Example</span></span>

<span data-ttu-id="5703e-111">Подключитесь к Azure и получите список счетов.</span><span class="sxs-lookup"><span data-stu-id="5703e-111">Connect to Azure and get a list of invoices.</span></span>

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
> [<span data-ttu-id="5703e-112">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="5703e-112">Explore the management APIs</span></span>](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a><span data-ttu-id="5703e-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="5703e-113">Samples</span></span>

* <span data-ttu-id="5703e-114">[Microsoft Azure Billing API Code Samples: Usage API](https://github.com/Azure-Samples/billing-dotnet-usage-api) (Примеры кода для API выставления счетов Microsoft Azure: API использования)</span><span class="sxs-lookup"><span data-stu-id="5703e-114">[Usage API](https://github.com/Azure-Samples/billing-dotnet-usage-api)</span></span>
* <span data-ttu-id="5703e-115">[Microsoft Azure Billing API Code Samples: RateCard API](https://github.com/Azure-Samples/billing-dotnet-ratecard-api) (Примеры кода для API выставления счетов Microsoft Azure: API RateCard)</span><span class="sxs-lookup"><span data-stu-id="5703e-115">[RateCard API](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)</span></span>
* <span data-ttu-id="5703e-116">[Microsoft Azure Billing API Code Samples: Multi-Tenant Web Application](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant) (Примеры кода для API выставления счетов Microsoft Azure: мультитенантное веб-приложение)</span><span class="sxs-lookup"><span data-stu-id="5703e-116">[Multi-Tenant Web Application](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
