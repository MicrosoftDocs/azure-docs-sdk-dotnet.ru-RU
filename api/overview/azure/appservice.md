---
title: "Библиотеки службы приложений Azure для .NET"
description: "Справочник по библиотекам службы приложений Azure для .NET"
keywords: Azure, .NET, SDK, API, web apps, app service, mobile, asp.net
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: e81a296ea5f5dadf7086439c88a347c20ec2abee
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-app-service-libraries-for-net"></a>Библиотеки службы приложений Azure для .NET

## <a name="overview"></a>Обзор

[Служба приложений Azure](/azure/app-service/app-service-value-prop-what-is) позволяет развертывать и масштабировать веб-сайты, веб-приложения, службы и интерфейсы REST API.

## <a name="management-api"></a>API управления

Развертывайте и масштабируйте элементы, размещенные в службе приложений Azure, а также управляйте ими с помощью API управления.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].


#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a>Пример кода

Создание веб-приложения.

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.AppService.Fluent;
*/

IWebApp app1 = azure.WebApps
    .Define("MyUniqueWebAddress")
    .WithRegion(Region.USWest)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewWindowsPlan(PricingTier.StandardS1)
    .Create();
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a>Примеры

* [Manage your web apps with the .NET SDK for Azure](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-manage/) (Управление веб-приложениями с помощью пакета SDK .NET для Azure)
* [ASP.NET sample for Azure App Service](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-get-started/) (Пример ASP.NET для службы приложений Azure)

Просмотрите [полный список](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=app%20service) примеров кода для службы приложений Azure.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package