---
title: "Библиотеки фабрики данных Azure для .NET"
description: "Справочник по библиотекам фабрики данных Azure для .NET"
keywords: Azure, .NET, SDK, API, Data Factory
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/20/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: e0b85d7d3988febca6dce7f4038825d74e4b8d2e
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-data-factory-libraries-for-net"></a><span data-ttu-id="451f9-104">Библиотеки фабрики данных Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="451f9-104">Azure Data Factory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="451f9-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="451f9-105">Overview</span></span>

<span data-ttu-id="451f9-106">Фабрика данных Azure — это облачная служба интеграции данных.</span><span class="sxs-lookup"><span data-stu-id="451f9-106">Azure Data Factory is a cloud-based data integration service.</span></span> <span data-ttu-id="451f9-107">Она позволяет создавать рабочие процессы на основе данных в облаке, чтобы выполнять оркестрацию и автоматизацию для перемещения и преобразования данных.</span><span class="sxs-lookup"><span data-stu-id="451f9-107">It enables you to create data-driven workflows in the cloud to orchestrate and automate data movement and data transformation.</span></span>

<span data-ttu-id="451f9-108">Дополнительные сведения см. в статье [Введение в фабрику данных Azure](/azure/data-factory/data-factory-introduction).</span><span class="sxs-lookup"><span data-stu-id="451f9-108">To learn more, read the [Introduction to Azure Data Factory](/azure/data-factory/data-factory-introduction).</span></span>

## <a name="management-library"></a><span data-ttu-id="451f9-109">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="451f9-109">Management library</span></span>

<span data-ttu-id="451f9-110">Библиотека управления служит для создания и планирования рабочих процессов на основе данных (конвейеров).</span><span class="sxs-lookup"><span data-stu-id="451f9-110">Use the management library to create and schedule data-driven workflows (pipelines).</span></span>

<span data-ttu-id="451f9-111">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="451f9-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="451f9-112">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="451f9-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a><span data-ttu-id="451f9-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="451f9-113">Code Example</span></span>

<span data-ttu-id="451f9-114">В примере ниже библиотека управления используется для создания фабрики данных.</span><span class="sxs-lookup"><span data-stu-id="451f9-114">The following example uses the management library to create a data factory.</span></span>

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
> [<span data-ttu-id="451f9-115">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="451f9-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a><span data-ttu-id="451f9-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="451f9-116">Samples</span></span>

* <span data-ttu-id="451f9-117">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) (MyDriving — пример приложения для Интернета вещей и мобильных устройств). В примере для предоставления данных используется фабрика данных.</span><span class="sxs-lookup"><span data-stu-id="451f9-117">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) that uses Data Factory to drive insights.</span></span>

<span data-ttu-id="451f9-118">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="451f9-118">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
