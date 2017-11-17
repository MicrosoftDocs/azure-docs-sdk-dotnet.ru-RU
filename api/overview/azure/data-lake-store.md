---
title: "Библиотеки Azure Data Lake Store для .NET"
description: "Справочник по библиотекам Azure Data Lake Store для .NET"
keywords: Azure, .NET, SDK, API, Data Lake Store
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-lake-store
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 2b1c51575872b12a94eb44c7c082996bb879bcc9
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
---
# <a name="azure-data-lake-store-libraries-for-net"></a><span data-ttu-id="b7bde-104">Библиотеки Azure Data Lake Store для .NET</span><span class="sxs-lookup"><span data-stu-id="b7bde-104">Azure Data Lake Store libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b7bde-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="b7bde-105">Overview</span></span>

<span data-ttu-id="b7bde-106">Хранилище озера данных Azure — это крупномасштабный репозиторий корпоративного уровня для рабочих нагрузок анализа больших данных.</span><span class="sxs-lookup"><span data-stu-id="b7bde-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="b7bde-107">Azure Data Lake позволяет сохранять данные с любым размером, типом и скоростью приема в одном месте для эксплуатационной и исследовательской аналитики.</span><span class="sxs-lookup"><span data-stu-id="b7bde-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

<span data-ttu-id="b7bde-108">Дополнительные сведения см. в [обзоре Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span><span class="sxs-lookup"><span data-stu-id="b7bde-108">To learn more, see [Overview of Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="b7bde-109">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="b7bde-109">Management library</span></span>

<span data-ttu-id="b7bde-110">Библиотека управления позволяет подключаться к репозиториям больших данных и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="b7bde-110">Use the management library to connect to and manage your big data repositories.</span></span>

<span data-ttu-id="b7bde-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="b7bde-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b7bde-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b7bde-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

### <a name="code-example"></a><span data-ttu-id="b7bde-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="b7bde-113">Code Example</span></span>

<span data-ttu-id="b7bde-114">В этом примере выполняется проверка подлинности для учетной записи аналитики и хранилища, а также создаются необходимые для управления клиенты.</span><span class="sxs-lookup"><span data-stu-id="b7bde-114">This example authenticates to an analytics account and store and creates the clients necessary for management.</span></span>

```csharp
/*
using AdlClient
using AdlClient.Models 
*/

// Setup authentication 
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
StoreAccountRef adls_account = new StoreAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
StoreClient adls = new StoreClient(auth, adls_account);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7bde-115">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="b7bde-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakestore/management)

## <a name="samples"></a><span data-ttu-id="b7bde-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="b7bde-116">Samples</span></span>

* <span data-ttu-id="b7bde-117">[Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)</span><span class="sxs-lookup"><span data-stu-id="b7bde-117">[Azure Data Lake .NET Client Example](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)</span></span>

<span data-ttu-id="b7bde-118">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="b7bde-118">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
