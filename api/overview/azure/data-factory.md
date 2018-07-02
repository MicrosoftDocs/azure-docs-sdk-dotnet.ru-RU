---
title: Библиотеки фабрики данных Azure для .NET
description: Справочник по библиотекам фабрики данных Azure для .NET
keywords: Azure, .NET, SDK, API, Data Factory
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: data-factory
ms.custom: devcenter, svc-overview
ms.openlocfilehash: b3c492fbfe4a4afa6f06f8c48a370c554a01719c
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065794"
---
# <a name="azure-data-factory-libraries-for-net"></a><span data-ttu-id="874c6-104">Библиотеки фабрики данных Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="874c6-104">Azure Data Factory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="874c6-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="874c6-105">Overview</span></span>

<span data-ttu-id="874c6-106">Фабрика данных Azure — это облачная служба интеграции данных.</span><span class="sxs-lookup"><span data-stu-id="874c6-106">Azure Data Factory is a cloud-based data integration service.</span></span> <span data-ttu-id="874c6-107">Она позволяет создавать рабочие процессы на основе данных в облаке, чтобы выполнять оркестрацию и автоматизацию для перемещения и преобразования данных.</span><span class="sxs-lookup"><span data-stu-id="874c6-107">It enables you to create data-driven workflows in the cloud to orchestrate and automate data movement and data transformation.</span></span>

<span data-ttu-id="874c6-108">Дополнительные сведения см. в статье [Введение в фабрику данных Azure](/azure/data-factory/data-factory-introduction).</span><span class="sxs-lookup"><span data-stu-id="874c6-108">To learn more, read the [Introduction to Azure Data Factory](/azure/data-factory/data-factory-introduction).</span></span>

## <a name="management-library---data-factory-v2-preview"></a><span data-ttu-id="874c6-109">Библиотека управления: фабрика данных версии 2 (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="874c6-109">Management library - Data Factory V2 (Preview)</span></span>

<span data-ttu-id="874c6-110">Библиотека управления служит для создания и планирования рабочих процессов на основе данных (конвейеров) в фабрике данных версии 2 (предварительная версия).</span><span class="sxs-lookup"><span data-stu-id="874c6-110">Use the management library to create and schedule data-driven workflows (pipelines) in Data Factory V2 (Preview).</span></span>  <span data-ttu-id="874c6-111">Дополнительные сведения см. в статье [Создание фабрики данных и конвейера с помощью пакета SDK .NET](/azure/data-factory/quickstart-create-data-factory-dot-net).</span><span class="sxs-lookup"><span data-stu-id="874c6-111">For more information, see [Create a data factory and pipeline using .NET SDK](/azure/data-factory/quickstart-create-data-factory-dot-net).</span></span>

<span data-ttu-id="874c6-112">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="874c6-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="874c6-113">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="874c6-113">Visual Studio Package Manager</span></span>

```powershell
# Get the most recent prerelease package
Install-Package Microsoft.Azure.Management.DataFactory -Prerelease
```

```bash
# Be sure to include the most recent version from the NuGet package page
dotnet add package Microsoft.Azure.Management.DataFactory --version 0.2.0-preview
```

### <a name="code-example"></a><span data-ttu-id="874c6-114">Пример кода</span><span class="sxs-lookup"><span data-stu-id="874c6-114">Code Example</span></span>

<span data-ttu-id="874c6-115">В примере ниже библиотека управления используется для создания фабрики данных.</span><span class="sxs-lookup"><span data-stu-id="874c6-115">The following example uses the management library to create a data factory.</span></span>

```csharp
/*
using Microsoft.Azure.Management.ResourceManager;
using Microsoft.Azure.Management.DataFactory;
using Microsoft.Azure.Management.DataFactory.Models;
*/

DataFactoryManagementClient client = new DataFactoryManagementClient(tokenCredentials) { SubscriptionId = subscriptionId };
Factory dataFactory = new Factory
{
    Location = region,
    Identity = new FactoryIdentity()
};
client.Factories.CreateOrUpdate(resourceGroup, dataFactoryName, dataFactory);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="874c6-116">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="874c6-116">Explore the management APIs</span></span>](/dotnet/api/microsoft.azure.management.datafactory)

## <a name="management-library---data-factory-v1"></a><span data-ttu-id="874c6-117">Библиотека управления: фабрика данных версии 1</span><span class="sxs-lookup"><span data-stu-id="874c6-117">Management library - Data Factory V1</span></span>

<span data-ttu-id="874c6-118">Библиотека управления служит для создания и планирования рабочих процессов на основе данных (конвейеров) в фабрике данных версии 1.</span><span class="sxs-lookup"><span data-stu-id="874c6-118">Use the management library to create and schedule data-driven workflows (pipelines) in Data Factory Version 1.</span></span>  <span data-ttu-id="874c6-119">Дополнительные сведения см. в документации по [фабрике данных версии 1](/azure/data-factory/v1/data-factory-introduction).</span><span class="sxs-lookup"><span data-stu-id="874c6-119">For more information, review the documentation for [Data Factory Version 1](/azure/data-factory/v1/data-factory-introduction).</span></span>

<span data-ttu-id="874c6-120">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="874c6-120">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="874c6-121">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="874c6-121">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a><span data-ttu-id="874c6-122">Пример кода</span><span class="sxs-lookup"><span data-stu-id="874c6-122">Code Example</span></span>

<span data-ttu-id="874c6-123">В примере ниже библиотека управления используется для создания фабрики данных.</span><span class="sxs-lookup"><span data-stu-id="874c6-123">The following example uses the management library to create a data factory.</span></span>

```csharp
DataFactoryManagementClient client = new DataFactoryManagementClient(aadTokenCredentials, resourceManagerUri);
client.DataFactories.CreateOrUpdate(resourceGroupName,
    new DataFactoryCreateOrUpdateParameters()
    {
        DataFactory = new DataFactory()
        {
            Name = dataFactoryName,
            Location = "westus",
            Properties = new DataFactoryProperties()
        }
    }
);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="874c6-124">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="874c6-124">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a><span data-ttu-id="874c6-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="874c6-125">Samples</span></span>

* <span data-ttu-id="874c6-126">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) (MyDriving — пример приложения для Интернета вещей и мобильных устройств). В примере для предоставления данных используется фабрика данных.</span><span class="sxs-lookup"><span data-stu-id="874c6-126">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) that uses Data Factory to drive insights.</span></span>

<span data-ttu-id="874c6-127">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="874c6-127">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
