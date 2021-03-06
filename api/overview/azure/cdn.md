---
title: Библиотеки Azure CDN для .NET
description: Справочник по библиотекам Azure CDN для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: azure-cdn
ms.openlocfilehash: b06b886531510d442c415fdc483d8083b6622c8e
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348066"
---
# <a name="azure-cdn-libraries-for-net"></a>Библиотеки Azure CDN для .NET

## <a name="overview"></a>Обзор

Сеть доставки содержимого (CDN) Azure кэширует статическое веб-содержимое в стратегически расположенных точках. Это позволяет обеспечить максимальную пропускную способность для доставки содержимого пользователям. CDN предлагает разработчикам глобальное решение для доставки содержимого с высокой пропускной способностью путем кэширования содержимого на физических узлах по всему миру.

Дополнительную информацию по Azure CDN см. в статье [Общие сведения о сети доставки содержимого (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview).


## <a name="management-library"></a>Библиотека управления

С помощью библиотеки Azure CDN для .NET можно автоматизировать создание профилей и конечных точек CDN и управление ими. 

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a>Пример

В этом примере создается профиль CDN с новой конечной точкой, которая указывает на `www.contoso.com`.

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.Cdn.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

ICdnProfile profileDefinition = azure.CdnProfiles.Define("CdnProfileName")
    .WithRegion(Region.USCentral)
    .WithExistingResourceGroup("ResourceGroupName")
    .WithStandardVerizonSku()
    .WithNewEndpoint("www.contoso.com")
    .Create();

```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a>Примеры

* [Getting Started with Cdn - Manage Cdn - in .Net](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn) (Начало работы с CDN: управление CDN — .NET)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
