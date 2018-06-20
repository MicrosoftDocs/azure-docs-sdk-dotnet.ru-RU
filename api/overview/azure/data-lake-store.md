---
title: Библиотеки Azure Data Lake Store для .NET
description: Справочник по библиотекам Azure Data Lake Store для .NET
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
ms.openlocfilehash: e8380c4a9ebf86f03fe87fc800dffda10e48e60a
ms.sourcegitcommit: 3e904e6e4f04f1c92d729459434c85faff32e386
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2017
ms.locfileid: "26588477"
---
# <a name="azure-data-lake-store-libraries-for-net"></a><span data-ttu-id="25e3a-104">Библиотеки Azure Data Lake Store для .NET</span><span class="sxs-lookup"><span data-stu-id="25e3a-104">Azure Data Lake Store libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="25e3a-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="25e3a-105">Overview</span></span>

<span data-ttu-id="25e3a-106">Хранилище озера данных Azure — это крупномасштабный репозиторий корпоративного уровня для рабочих нагрузок анализа больших данных.</span><span class="sxs-lookup"><span data-stu-id="25e3a-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="25e3a-107">Azure Data Lake позволяет сохранять данные с любым размером, типом и скоростью приема в одном месте для эксплуатационной и исследовательской аналитики.</span><span class="sxs-lookup"><span data-stu-id="25e3a-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

<span data-ttu-id="25e3a-108">Дополнительные сведения см. в [обзоре Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span><span class="sxs-lookup"><span data-stu-id="25e3a-108">To learn more, see [Overview of Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span></span>

## <a name="client-library"></a><span data-ttu-id="25e3a-109">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="25e3a-109">Client library</span></span>

<span data-ttu-id="25e3a-110">Клиентская библиотека используется для выполнения в Data Lake Store операций файловой системы, таких как создание папок в учетной записи Data Lake Store, отправка файлов и загрузка файлов.</span><span class="sxs-lookup"><span data-stu-id="25e3a-110">Use the client library to perform filesystem operations on Data Lake Store, such as creating folders in a Data Lake Store account, uploading files, and downloading files.</span></span>  <span data-ttu-id="25e3a-111">Полное руководство по использованию Data Lake Store с .NET см. в статье [Операции файловой системы в Azure Data Lake Store с использованием SDK для .NET](/azure/data-lake-store/data-lake-store-data-operations-net-sdk).</span><span class="sxs-lookup"><span data-stu-id="25e3a-111">For a full tutorial on using Data Lake Store with .NET, see [Filesystem operations on Azure Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-data-operations-net-sdk).</span></span>

<span data-ttu-id="25e3a-112">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="25e3a-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="25e3a-113">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="25e3a-113">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.DataLake.Store
```
### <a name="authentication"></a><span data-ttu-id="25e3a-114">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="25e3a-114">Authentication</span></span>

* <span data-ttu-id="25e3a-115">Дополнительные сведения о проверке подлинности пользователей в приложении см. в статье [End-user authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk) (Аутентификация пользователей в Data Lake Store с использованием пакета SDK для .NET).</span><span class="sxs-lookup"><span data-stu-id="25e3a-115">For end-user authentication for your application, see [End-user authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk).</span></span>
* <span data-ttu-id="25e3a-116">Дополнительные сведения о проверке подлинности между службами в приложении см. в статье [Service-to-service authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk) (Аутентификация между службами в Data Lake Store с использованием пакета SDK для .NET).</span><span class="sxs-lookup"><span data-stu-id="25e3a-116">For service-to-service authentication for your application, see [Service-to-service authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk).</span></span>

### <a name="code-example"></a><span data-ttu-id="25e3a-117">Пример кода</span><span class="sxs-lookup"><span data-stu-id="25e3a-117">Code Example</span></span>

<span data-ttu-id="25e3a-118">Следующий фрагмент кода создает клиентский объект файловой системы Data Lake Store, который используется для передачи запросов к службе.</span><span class="sxs-lookup"><span data-stu-id="25e3a-118">The following snippet creates the Data Lake Store filesystem client object, which is used to issue requests to the service.</span></span>

```csharp
// Create client objects
AdlsClient client = AdlsClient.CreateClient(_adlsAccountName, adlCreds);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="25e3a-119">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="25e3a-119">Explore the client APIs</span></span>](/dotnet/api/overview/azure/datalakestore/client)


## <a name="management-library"></a><span data-ttu-id="25e3a-120">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="25e3a-120">Management library</span></span>

<span data-ttu-id="25e3a-121">Библиотека управления позволяет подключаться к репозиториям больших данных и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="25e3a-121">Use the management library to connect to and manage your big data repositories.</span></span>

<span data-ttu-id="25e3a-122">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="25e3a-122">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="25e3a-123">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="25e3a-123">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="25e3a-124">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="25e3a-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/datalakestore/management)


## <a name="samples"></a><span data-ttu-id="25e3a-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="25e3a-125">Samples</span></span>

* <span data-ttu-id="25e3a-126">[Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)</span><span class="sxs-lookup"><span data-stu-id="25e3a-126">[Azure Data Lake .NET Client Example](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)</span></span>

<span data-ttu-id="25e3a-127">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="25e3a-127">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
