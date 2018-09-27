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
# <a name="azure-billing-libraries-for-net"></a><span data-ttu-id="4baf0-103">Библиотеки выставления счетов Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="4baf0-103">Azure Billing libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="4baf0-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="4baf0-104">Overview</span></span>

<span data-ttu-id="4baf0-105">API выставления счетов Azure (предварительная версия) предоставляет программный доступ к счетам и сведениям об их выставлении в Azure.</span><span class="sxs-lookup"><span data-stu-id="4baf0-105">Azure Billing API (preview) provides programmatic access to your Azure billing information and invoices.</span></span>

## <a name="management-library"></a><span data-ttu-id="4baf0-106">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="4baf0-106">Management library</span></span>

<span data-ttu-id="4baf0-107">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4baf0-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4baf0-108">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4baf0-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a><span data-ttu-id="4baf0-109">Пример кода</span><span class="sxs-lookup"><span data-stu-id="4baf0-109">Code Example</span></span>

<span data-ttu-id="4baf0-110">Подключитесь к Azure и получите список счетов.</span><span class="sxs-lookup"><span data-stu-id="4baf0-110">Connect to Azure and get a list of invoices.</span></span>

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
> [<span data-ttu-id="4baf0-111">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="4baf0-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a><span data-ttu-id="4baf0-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="4baf0-112">Samples</span></span>

* <span data-ttu-id="4baf0-113">[Microsoft Azure Billing API Code Samples: Usage API](https://github.com/Azure-Samples/billing-dotnet-usage-api) (Примеры кода для API выставления счетов Microsoft Azure: API использования)</span><span class="sxs-lookup"><span data-stu-id="4baf0-113">[Usage API](https://github.com/Azure-Samples/billing-dotnet-usage-api)</span></span>
* <span data-ttu-id="4baf0-114">[Microsoft Azure Billing API Code Samples: RateCard API](https://github.com/Azure-Samples/billing-dotnet-ratecard-api) (Примеры кода для API выставления счетов Microsoft Azure: API RateCard)</span><span class="sxs-lookup"><span data-stu-id="4baf0-114">[RateCard API](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)</span></span>
* <span data-ttu-id="4baf0-115">[Microsoft Azure Billing API Code Samples: Multi-Tenant Web Application](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant) (Примеры кода для API выставления счетов Microsoft Azure: мультитенантное веб-приложение)</span><span class="sxs-lookup"><span data-stu-id="4baf0-115">[Multi-Tenant Web Application](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
