---
title: Библиотеки службы "Поиск Azure" для .NET
description: Справочник по библиотекам службы "Поиск Azure" для .NET
keywords: Azure, .NET, SDK, API, Search
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: search
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 5062d444b859711d7f87a0ecbd65e6b204c04b16
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065284"
---
# <a name="azure-search-libraries-for-net"></a><span data-ttu-id="15748-104">Библиотеки службы "Поиск Azure" для .NET</span><span class="sxs-lookup"><span data-stu-id="15748-104">Azure Search libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="15748-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="15748-105">Overview</span></span>

<span data-ttu-id="15748-106">[Поиск Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search) — это полностью управляемая облачная служба поиска, которая предоставляет широкие возможности поиска по данным в мобильных, корпоративных и веб-приложениях.</span><span class="sxs-lookup"><span data-stu-id="15748-106">[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) is a fully managed cloud search service that provides a rich search experience over data in web, mobile, and enterprise applications.</span></span>

## <a name="client-library"></a><span data-ttu-id="15748-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="15748-107">Client library</span></span>

<span data-ttu-id="15748-108">Используйте клиентскую библиотеку службы "Поиск Azure", чтобы получать доступ к операциям индексирования и поиска и выполнять их со службами поиска, индексами, документами или другими объектами.</span><span class="sxs-lookup"><span data-stu-id="15748-108">Use the Azure Search client library to access and execute indexing and search operations on a search service, index, documents, or other object.</span></span> <span data-ttu-id="15748-109">Пошаговое описание см. в статье [Использование службы поиска Azure в приложении .NET](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="15748-109">For a step-by-step introduction, see [How to use Azure Search from a .NET application](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).</span></span>

<span data-ttu-id="15748-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Search) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="15748-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="15748-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15748-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Search
```

```bash
dotnet add package Microsoft.Azure.Search
```

### <a name="code-example"></a><span data-ttu-id="15748-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="15748-112">Code Example</span></span>

```csharp
/* Include these 'using' directives:
   using Microsoft.Azure.Search;
   using Microsoft.Azure.Search.Models;
*/

// A service endpoint and an api-key are required on a connection.
// Set them in a config file (not shown) and then connect to the client.
IConfigurationBuilder builder = new ConfigurationBuilder().AddJsonFile("appsettings.json");
IConfigurationRoot configuration = builder.Build();

SearchServiceClient serviceClient = CreateSearchServiceClient(configuration);

// Create an index named hotels
ISearchIndexClient indexClient = serviceClient.Indexes.GetClient("hotels");

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="15748-113">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="15748-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/search/client)


## <a name="management-library"></a><span data-ttu-id="15748-114">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="15748-114">Management library</span></span>

<span data-ttu-id="15748-115">Используйте библиотеку управления для службы "Поиск Azure", чтобы подготавливать службы, управлять ключами API и настраивать ресурсы.</span><span class="sxs-lookup"><span data-stu-id="15748-115">Use the Azure Search management library to provision a service, manage api-keys, and adjust resources.</span></span> <span data-ttu-id="15748-116">Управление службами зависит от Azure Resource Manager для идентификации подписчиков и клиентов.</span><span class="sxs-lookup"><span data-stu-id="15748-116">Service management has a dependency on Azure Resource Manager for subscriber and tenant identification.</span></span> <span data-ttu-id="15748-117">Как правило, регистрация приложений и проверка подлинности с помощью Azure Active Directory также требуется для поддержки рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="15748-117">Typically, authentication and application registration with Azure Active Directory is also necessary to support the workflow.</span></span> <span data-ttu-id="15748-118">Общие сведения о подготовке службы "Поиск Azure" см. в статье [об использовании REST API управления](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).</span><span class="sxs-lookup"><span data-stu-id="15748-118">For an introduction to Azure Search service provisioning, see [How to use the Management REST API](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).</span></span>

<span data-ttu-id="15748-119">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="15748-119">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="15748-120">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15748-120">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Search
```

```bash
dotnet add package Microsoft.Azure.Management.Search
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="15748-121">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="15748-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/search/management)

## <a name="samples"></a><span data-ttu-id="15748-122">Примеры</span><span class="sxs-lookup"><span data-stu-id="15748-122">Samples</span></span>

 + [<span data-ttu-id="15748-123">Azure-Samples/search-dotnet-getting-started</span><span class="sxs-lookup"><span data-stu-id="15748-123">Azure Samples / search-dotnet-getting-started</span></span>](https://github.com/Azure-Samples/search-dotnet-getting-started)
 + [<span data-ttu-id="15748-124">Azure-Samples/search-dotnet-management-api</span><span class="sxs-lookup"><span data-stu-id="15748-124">Azure Samples / search-dotnet-management-api</span></span>](https://github.com/Azure-Samples/search-dotnet-management-api)

<span data-ttu-id="15748-125">Другие примеры для службы "Поиск" см. в [репозитории примеров Azure](https://github.com/Azure-Samples/) на сайте Github.</span><span class="sxs-lookup"><span data-stu-id="15748-125">Find more search samples in the [Azure samples repository](https://github.com/Azure-Samples/) on Github.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
