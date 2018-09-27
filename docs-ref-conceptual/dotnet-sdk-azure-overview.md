---
title: API Azure .NET
description: Общие сведения об API Azure для .NET
ms.date: 10/19/2017
ms.openlocfilehash: 04997caa99ed60db6ad98cabbc72b36bfbf99f4d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190137"
---
# <a name="azure-net-apis"></a><span data-ttu-id="dcd62-103">API Azure .NET</span><span class="sxs-lookup"><span data-stu-id="dcd62-103">Azure .NET APIs</span></span>

<span data-ttu-id="dcd62-104">API Azure для .NET позволяют использовать службы Azure и управлять ресурсами Azure из кода приложения.</span><span class="sxs-lookup"><span data-stu-id="dcd62-104">The Azure .NET APIs let you use Azure services and manage Azure resources from your application code.</span></span> <span data-ttu-id="dcd62-105">API доступны в виде [пакетов NuGet](/dotnet/api/overview/azure/) для использования в проектах .NET.</span><span class="sxs-lookup"><span data-stu-id="dcd62-105">The APIs are available as [NuGet packages](/dotnet/api/overview/azure/) for use in your .NET projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="dcd62-106">Управление ресурсами Azure</span><span class="sxs-lookup"><span data-stu-id="dcd62-106">Manage Azure resources</span></span>

<span data-ttu-id="dcd62-107">Используя библиотеки Azure для .NET, можно создавать и администрировать ресурсы Azure из приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="dcd62-107">The Azure libraries for .NET let you create and manage Azure resources from your .NET applications.</span></span>

<span data-ttu-id="dcd62-108">Многие пакеты для управления ресурсами Azure имеют [текучий](dotnet-sdk-azure-concepts.md) интерфейс для настройки ресурсов в соответствии с требованиями.</span><span class="sxs-lookup"><span data-stu-id="dcd62-108">Many of the packages for managing Azure resources have a [fluent](dotnet-sdk-azure-concepts.md) interface to configure resources exactly to your specifications.</span></span> <span data-ttu-id="dcd62-109">Например, для создания виртуальной машины Windows можно написать следующий код:</span><span class="sxs-lookup"><span data-stu-id="dcd62-109">For example, to create a Windows VM you would write the following code:</span></span>

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

<span data-ttu-id="dcd62-110">См. [список служб .NET](/dotnet/api/overview/azure/), чтобы начать использовать библиотеки с проектами.</span><span class="sxs-lookup"><span data-stu-id="dcd62-110">Review the [.NET service list](/dotnet/api/overview/azure/) to start using the libraries immediately with your projects.</span></span> <span data-ttu-id="dcd62-111">Затем см. [статью с инструкциями по началу работы](dotnet-sdk-azure-get-started.md), чтобы настроить аутентификацию и запустить пример кода в своей подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="dcd62-111">Then read the [get started article](dotnet-sdk-azure-get-started.md) to set up authentication and run sample code against your own Azure subscription.</span></span>  <span data-ttu-id="dcd62-112">[Статья с основными понятиями](dotnet-sdk-azure-concepts.md) содержит соглашения, которые использует пакет SDK, и объясняет, как их использовать, чтобы упростить код приложения.</span><span class="sxs-lookup"><span data-stu-id="dcd62-112">The [concepts article](dotnet-sdk-azure-concepts.md) goes into the conventions the SDK uses and how to leverage them to simplify your application code.</span></span> <span data-ttu-id="dcd62-113">Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу см. в [заметках о выпуске](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="dcd62-113">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

## <a name="consume-azure-services"></a><span data-ttu-id="dcd62-114">Использование служб Azure</span><span class="sxs-lookup"><span data-stu-id="dcd62-114">Consume Azure services</span></span>

<span data-ttu-id="dcd62-115">Вы можете использовать API .NET не только для создания ресурсов в Azure и программного управления ими, но и для подключения приложений к этим ресурсам и использования в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="dcd62-115">In addition to using .NET APIs to create and programmatically manage resources within Azure, you can also then use .NET APIs to connect your applications to these resources and use them at runtime.</span></span>  <span data-ttu-id="dcd62-116">Например, вы можете подключиться к базе данных или хранилищу данных SQL в службе хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="dcd62-116">For example, you might connect to a SQL Database or store data within Azure Storage.</span></span>  <span data-ttu-id="dcd62-117">Чтобы определить, какой пакет NuGet следует использовать для конкретной службы Azure, см. [полный список API служб](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="dcd62-117">You can identify which NuGet package to use for a particular Azure service by browsing our [full list of service APIs](/dotnet/api/overview/azure/).</span></span>  

## <a name="samples"></a><span data-ttu-id="dcd62-118">Примеры</span><span class="sxs-lookup"><span data-stu-id="dcd62-118">Samples</span></span>

<span data-ttu-id="dcd62-119">Приведенные ниже примеры охватывают общие задачи автоматизации с помощью библиотек Azure для .NET:</span><span class="sxs-lookup"><span data-stu-id="dcd62-119">The following samples cover common automation tasks with the Azure libraries for .NET:</span></span>

- [<span data-ttu-id="dcd62-120">Виртуальные машины</span><span class="sxs-lookup"><span data-stu-id="dcd62-120">Virtual machines</span></span>](dotnet-sdk-azure-virtual-machine-samples.md)
- [<span data-ttu-id="dcd62-121">Веб-приложения</span><span class="sxs-lookup"><span data-stu-id="dcd62-121">Web apps</span></span>](dotnet-sdk-azure-web-apps-samples.md)
- [<span data-ttu-id="dcd62-122">База данных SQL</span><span class="sxs-lookup"><span data-stu-id="dcd62-122">SQL Database</span></span>](dotnet-sdk-azure-sql-database-samples.md)

<span data-ttu-id="dcd62-123">См. унифицированный [справочник](/dotnet/api/overview/azure/?view=azure-dotnet) по всем пакетам в библиотеках служб и библиотеках управления.</span><span class="sxs-lookup"><span data-stu-id="dcd62-123">A unified [reference](/dotnet/api/overview/azure/?view=azure-dotnet) is available for all packages in both the service and management libraries.</span></span> <span data-ttu-id="dcd62-124">Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу см. в [заметках о выпуске](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="dcd62-124">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

[!include[Contribute and community](includes/contribute.md)]