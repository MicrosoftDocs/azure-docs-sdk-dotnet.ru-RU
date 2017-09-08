---
title: "Библиотеки Azure DNS для .NET"
description: "Справочник по библиотекам Azure DNS для .NET"
keywords: Azure, .NET, SDK, API, DNS
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/31/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 57c578f12ea426dc5784658338473f0044d21e5c
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-dns-libraries-for-net"></a><span data-ttu-id="cee16-104">Библиотеки Azure DNS для .NET</span><span class="sxs-lookup"><span data-stu-id="cee16-104">Azure DNS libraries for .NET</span></span>

<span data-ttu-id="cee16-105">Библиотеки Microsoft Azure DNS для .NET позволяют создавать и изменять зоны и записи DNS, которые размещены в Azure.</span><span class="sxs-lookup"><span data-stu-id="cee16-105">Use the Microsoft Azure DNS libraries for .NET to create and modify DNS zones and records hosted within Azure.</span></span> <span data-ttu-id="cee16-106">Зонами и записи управляются как ресурсы Azure.</span><span class="sxs-lookup"><span data-stu-id="cee16-106">Zones and records are managed as Azure Resources.</span></span> <span data-ttu-id="cee16-107">Дополнительные сведения см. в статье [Обзор Azure DNS](/azure/dns/dns-overview).</span><span class="sxs-lookup"><span data-stu-id="cee16-107">Learn more by reading the [Azure DNS overview](/azure/dns/dns-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="cee16-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="cee16-108">Management library</span></span>

<span data-ttu-id="cee16-109">Библиотека управления предназначена для создания и изменения зон и записей DNS, которые размещены в Azure.</span><span class="sxs-lookup"><span data-stu-id="cee16-109">Use the management library to create and modify DNS zones and records that are hosted in Azure.</span></span>

<span data-ttu-id="cee16-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="cee16-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="cee16-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cee16-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a><span data-ttu-id="cee16-112">Пример</span><span class="sxs-lookup"><span data-stu-id="cee16-112">Example</span></span>

<span data-ttu-id="cee16-113">В примере ниже создается новый объект зоны DNS.</span><span class="sxs-lookup"><span data-stu-id="cee16-113">The following example creates a new DNS zone.</span></span>

```csharp
/*
using Microsoft.Rest.Azure.Authentication;
using Microsoft.Azure.Management.Dns;
using Microsoft.Azure.Management.Dns.Models;
*/
Microsoft.Rest.ServiceClientCredentials serviceCreds = await ApplicationTokenProvider.LoginSilentAsync(tenantId, clientId, secret);
DnsManagementClient dnsClient = new DnsManagementClient(serviceCreds);            
Zone dnsZoneParams = new Zone("global");
dnsZoneParams.Tags = new Dictionary<string, string>();
dnsZoneParams.Tags.Add("dept", "finance");
Zone dnsZone =
    await dnsClient.Zones.CreateOrUpdateAsync(resourceGroupName, zoneName, dnsZoneParams, null, "*");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="cee16-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="cee16-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a><span data-ttu-id="cee16-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="cee16-115">Samples</span></span>

* [<span data-ttu-id="cee16-116">Пример проекта для пакета Azure DNS SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="cee16-116">Azure DNS .NET SDK Sample Project</span></span>](https://www.microsoft.com/download/details.aspx?id=47268)

<span data-ttu-id="cee16-117">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="cee16-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
