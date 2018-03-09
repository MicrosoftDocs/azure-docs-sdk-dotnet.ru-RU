---
title: "Библиотеки Azure Data Lake Analytics для .NET"
description: "Справочник по библиотекам Azure Data Lake Analytics для .NET"
keywords: Azure, .NET, SDK, API, Data Lake Analytics
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-lake-analytics
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 063513d8c523330276cdfc222d3ca00a9629f63a
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a><span data-ttu-id="adb81-104">Библиотеки Azure Data Lake Analytics для .NET</span><span class="sxs-lookup"><span data-stu-id="adb81-104">Azure Data Lake Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="adb81-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="adb81-105">Overview</span></span>

<span data-ttu-id="adb81-106">Azure Data Lake Analytics — это служба обработки заданий аналитики по запросу, которая позволяет упростить анализ больших данных.</span><span class="sxs-lookup"><span data-stu-id="adb81-106">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span>

<span data-ttu-id="adb81-107">Дополнительные сведения см. в статье [Обзор аналитики озера данных Microsoft Azure](/azure/data-lake-analytics/data-lake-analytics-overview).</span><span class="sxs-lookup"><span data-stu-id="adb81-107">To learn more, see [Overview of Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="adb81-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="adb81-108">Management library</span></span>

<span data-ttu-id="adb81-109">Библиотека управления предназначена для подключения к службе и управления заданиями аналитики.</span><span class="sxs-lookup"><span data-stu-id="adb81-109">Use the management library to connect to the service and manage analytics jobs.</span></span>

<span data-ttu-id="adb81-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="adb81-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="adb81-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="adb81-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a><span data-ttu-id="adb81-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="adb81-112">Code Example</span></span>

<span data-ttu-id="adb81-113">В примере ниже создаются клиенты для подключения и управления учетной записью аналитики.</span><span class="sxs-lookup"><span data-stu-id="adb81-113">This example creates the clients to connect with and manage the analytics account.</span></span>

```csharp
/*
using AdlClient 
*/

// Setup authentication for this demo
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
AnalyticsAccountRef adla_account = new AnalyticsAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
AnalyticsClient adla = new AnalyticsClient(auth, adla_account);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="adb81-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="adb81-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a><span data-ttu-id="adb81-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="adb81-115">Samples</span></span>
* <span data-ttu-id="adb81-116">[Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)</span><span class="sxs-lookup"><span data-stu-id="adb81-116">[Azure Data Lake .NET Client Example](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)</span></span>

<span data-ttu-id="adb81-117">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="adb81-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
