---
title: Библиотеки Azure DNS для .NET
description: Справочник по библиотекам Azure DNS для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: dns
ms.openlocfilehash: b9ab6359aaa1e4e9b6e99e7a7b007928d18f3453
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190197"
---
# <a name="azure-dns-libraries-for-net"></a><span data-ttu-id="1d36a-103">Библиотеки Azure DNS для .NET</span><span class="sxs-lookup"><span data-stu-id="1d36a-103">Azure DNS libraries for .NET</span></span>

<span data-ttu-id="1d36a-104">Библиотеки Microsoft Azure DNS для .NET позволяют создавать и изменять зоны и записи DNS, которые размещены в Azure.</span><span class="sxs-lookup"><span data-stu-id="1d36a-104">Use the Microsoft Azure DNS libraries for .NET to create and modify DNS zones and records hosted within Azure.</span></span> <span data-ttu-id="1d36a-105">Зонами и записи управляются как ресурсы Azure.</span><span class="sxs-lookup"><span data-stu-id="1d36a-105">Zones and records are managed as Azure Resources.</span></span> <span data-ttu-id="1d36a-106">Дополнительные сведения см. в статье [Обзор Azure DNS](/azure/dns/dns-overview).</span><span class="sxs-lookup"><span data-stu-id="1d36a-106">Learn more by reading the [Azure DNS overview](/azure/dns/dns-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="1d36a-107">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="1d36a-107">Management library</span></span>

<span data-ttu-id="1d36a-108">Библиотека управления предназначена для создания и изменения зон и записей DNS, которые размещены в Azure.</span><span class="sxs-lookup"><span data-stu-id="1d36a-108">Use the management library to create and modify DNS zones and records that are hosted in Azure.</span></span>

<span data-ttu-id="1d36a-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="1d36a-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1d36a-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1d36a-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a><span data-ttu-id="1d36a-111">Пример</span><span class="sxs-lookup"><span data-stu-id="1d36a-111">Example</span></span>

<span data-ttu-id="1d36a-112">В примере ниже создается новый объект зоны DNS.</span><span class="sxs-lookup"><span data-stu-id="1d36a-112">The following example creates a new DNS zone.</span></span>

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
> [<span data-ttu-id="1d36a-113">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="1d36a-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a><span data-ttu-id="1d36a-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="1d36a-114">Samples</span></span>

* [<span data-ttu-id="1d36a-115">Пример проекта для пакета Azure DNS SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="1d36a-115">Azure DNS .NET SDK Sample Project</span></span>](https://www.microsoft.com/download/details.aspx?id=47268)

<span data-ttu-id="1d36a-116">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="1d36a-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
