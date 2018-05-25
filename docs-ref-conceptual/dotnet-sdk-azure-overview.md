---
title: API Azure .NET
description: Общие сведения об API Azure для .NET
keywords: Azure, .NET, SDK, API, NuGet, libraries, packages
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 26360a516220ca9d3e8901e60cb23ecbd02863cd
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="azure-net-apis"></a><span data-ttu-id="b0044-104">API Azure .NET</span><span class="sxs-lookup"><span data-stu-id="b0044-104">Azure .NET APIs</span></span>

<span data-ttu-id="b0044-105">API Azure для .NET позволяют использовать службы Azure и управлять ресурсами Azure из кода приложения.</span><span class="sxs-lookup"><span data-stu-id="b0044-105">The Azure .NET APIs let you use Azure services and manage Azure resources from your application code.</span></span> <span data-ttu-id="b0044-106">API доступны в виде [пакетов NuGet](/dotnet/api/overview/azure/) для использования в проектах .NET.</span><span class="sxs-lookup"><span data-stu-id="b0044-106">The APIs are available as [NuGet packages](/dotnet/api/overview/azure/) for use in your .NET projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="b0044-107">Управление ресурсами Azure</span><span class="sxs-lookup"><span data-stu-id="b0044-107">Manage Azure resources</span></span>

<span data-ttu-id="b0044-108">Используя библиотеки Azure для .NET, можно создавать и администрировать ресурсы Azure из приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="b0044-108">The Azure libraries for .NET let you create and manage Azure resources from your .NET applications.</span></span>

<span data-ttu-id="b0044-109">Многие пакеты для управления ресурсами Azure имеют [текучий](dotnet-sdk-azure-concepts.md) интерфейс для настройки ресурсов в соответствии с требованиями.</span><span class="sxs-lookup"><span data-stu-id="b0044-109">Many of the packages for managing Azure resources have a [fluent](dotnet-sdk-azure-concepts.md) interface to configure resources exactly to your specifications.</span></span> <span data-ttu-id="b0044-110">Например, для создания виртуальной машины Windows можно написать следующий код:</span><span class="sxs-lookup"><span data-stu-id="b0044-110">For example, to create a Windows VM you would write the following code:</span></span>

```csharp
var windowsVM = azure.VirtualMachines.Define(windowsVmName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername(username)
    .WithAdminPassword(password)
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
 ```

<span data-ttu-id="b0044-111">См. [список служб .NET](/dotnet/api/overview/azure/), чтобы начать использовать библиотеки с проектами.</span><span class="sxs-lookup"><span data-stu-id="b0044-111">Review the [.NET service list](/dotnet/api/overview/azure/) to start using the libraries immediately with your projects.</span></span> <span data-ttu-id="b0044-112">Затем см. [статью с инструкциями по началу работы](dotnet-sdk-azure-get-started.md), чтобы настроить аутентификацию и запустить пример кода в своей подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="b0044-112">Then read the [get started article](dotnet-sdk-azure-get-started.md) to set up authentication and run sample code against your own Azure subscription.</span></span>  <span data-ttu-id="b0044-113">[Статья с основными понятиями](dotnet-sdk-azure-concepts.md) содержит соглашения, которые использует пакет SDK, и объясняет, как их использовать, чтобы упростить код приложения.</span><span class="sxs-lookup"><span data-stu-id="b0044-113">The [concepts article](dotnet-sdk-azure-concepts.md) goes into the conventions the SDK uses and how to leverage them to simplify your application code.</span></span> <span data-ttu-id="b0044-114">Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу см. в [заметках о выпуске](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="b0044-114">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

## <a name="consume-azure-services"></a><span data-ttu-id="b0044-115">Использование служб Azure</span><span class="sxs-lookup"><span data-stu-id="b0044-115">Consume Azure services</span></span>

<span data-ttu-id="b0044-116">Вы можете использовать API .NET не только для создания ресурсов в Azure и программного управления ими, но и для подключения приложений к этим ресурсам и использования в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="b0044-116">In addition to using .NET APIs to create and programmatically manage resources within Azure, you can also then use .NET APIs to connect your applications to these resources and use them at runtime.</span></span>  <span data-ttu-id="b0044-117">Например, вы можете подключиться к базе данных или хранилищу данных SQL в службе хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="b0044-117">For example, you might connect to a SQL Database or store data within Azure Storage.</span></span>  <span data-ttu-id="b0044-118">Чтобы определить, какой пакет NuGet следует использовать для конкретной службы Azure, см. [полный список API служб](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="b0044-118">You can identify which NuGet package to use for a particular Azure service by browsing our [full list of service APIs](/dotnet/api/overview/azure/).</span></span>  

## <a name="samples"></a><span data-ttu-id="b0044-119">Примеры</span><span class="sxs-lookup"><span data-stu-id="b0044-119">Samples</span></span>

<span data-ttu-id="b0044-120">Приведенные ниже примеры охватывают общие задачи автоматизации с помощью библиотек Azure для .NET:</span><span class="sxs-lookup"><span data-stu-id="b0044-120">The following samples cover common automation tasks with the Azure libraries for .NET:</span></span>

- [<span data-ttu-id="b0044-121">Виртуальные машины</span><span class="sxs-lookup"><span data-stu-id="b0044-121">Virtual machines</span></span>](dotnet-sdk-azure-virtual-machine-samples.md)
- [<span data-ttu-id="b0044-122">Веб-приложения</span><span class="sxs-lookup"><span data-stu-id="b0044-122">Web apps</span></span>](dotnet-sdk-azure-web-apps-samples.md)
- [<span data-ttu-id="b0044-123">База данных SQL</span><span class="sxs-lookup"><span data-stu-id="b0044-123">SQL Database</span></span>](dotnet-sdk-azure-sql-database-samples.md)

<span data-ttu-id="b0044-124">См. унифицированный [справочник](/dotnet/api/overview/azure/?view=azure-dotnet) по всем пакетам в библиотеках служб и библиотеках управления.</span><span class="sxs-lookup"><span data-stu-id="b0044-124">A unified [reference](/dotnet/api/overview/azure/?view=azure-dotnet) is available for all packages in both the service and management libraries.</span></span> <span data-ttu-id="b0044-125">Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу см. в [заметках о выпуске](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="b0044-125">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

[!include[Contribute and community](includes/contribute.md)]