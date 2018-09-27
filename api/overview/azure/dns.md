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
# <a name="azure-dns-libraries-for-net"></a>Библиотеки Azure DNS для .NET

Библиотеки Microsoft Azure DNS для .NET позволяют создавать и изменять зоны и записи DNS, которые размещены в Azure. Зонами и записи управляются как ресурсы Azure. Дополнительные сведения см. в статье [Обзор Azure DNS](/azure/dns/dns-overview).

## <a name="management-library"></a>Библиотека управления

Библиотека управления предназначена для создания и изменения зон и записей DNS, которые размещены в Azure.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a>Пример

В примере ниже создается новый объект зоны DNS.

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
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a>Примеры

* [Пример проекта для пакета Azure DNS SDK для .NET](https://www.microsoft.com/download/details.aspx?id=47268)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
