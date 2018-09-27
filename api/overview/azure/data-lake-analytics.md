---
title: Библиотеки Azure Data Lake Analytics для .NET
description: Справочник по библиотекам Azure Data Lake Analytics для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-lake-analytics
ms.openlocfilehash: 829f9245ae06c64c4ad9a175fd25c742533a284e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189797"
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a><span data-ttu-id="ed497-103">Библиотеки Azure Data Lake Analytics для .NET</span><span class="sxs-lookup"><span data-stu-id="ed497-103">Azure Data Lake Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="ed497-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="ed497-104">Overview</span></span>

<span data-ttu-id="ed497-105">Azure Data Lake Analytics — это служба обработки заданий аналитики по запросу, которая позволяет упростить анализ больших данных.</span><span class="sxs-lookup"><span data-stu-id="ed497-105">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span>

<span data-ttu-id="ed497-106">Дополнительные сведения см. в статье [Обзор аналитики озера данных Microsoft Azure](/azure/data-lake-analytics/data-lake-analytics-overview).</span><span class="sxs-lookup"><span data-stu-id="ed497-106">To learn more, see [Overview of Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="ed497-107">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="ed497-107">Management library</span></span>

<span data-ttu-id="ed497-108">Библиотека управления предназначена для подключения к службе и управления заданиями аналитики.</span><span class="sxs-lookup"><span data-stu-id="ed497-108">Use the management library to connect to the service and manage analytics jobs.</span></span>

<span data-ttu-id="ed497-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="ed497-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="ed497-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed497-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a><span data-ttu-id="ed497-111">Пример кода</span><span class="sxs-lookup"><span data-stu-id="ed497-111">Code Example</span></span>

<span data-ttu-id="ed497-112">В примере ниже создаются клиенты для подключения и управления учетной записью аналитики.</span><span class="sxs-lookup"><span data-stu-id="ed497-112">This example creates the clients to connect with and manage the analytics account.</span></span>

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
> [<span data-ttu-id="ed497-113">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="ed497-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a><span data-ttu-id="ed497-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="ed497-114">Samples</span></span>
* <span data-ttu-id="ed497-115">[Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)</span><span class="sxs-lookup"><span data-stu-id="ed497-115">[Azure Data Lake .NET Client Example](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)</span></span>

<span data-ttu-id="ed497-116">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="ed497-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
