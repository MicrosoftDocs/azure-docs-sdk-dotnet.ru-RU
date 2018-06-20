---
title: Библиотеки Azure Resource Manager для .NET
description: Справочник по библиотекам Azure Resource Manager для .NET
keywords: Azure, .NET, SDK, API, Resource Manager
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: f9fe96fcdc94d3d27445f462c5220def9f2966da
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566375"
---
# <a name="azure-resource-manager-libraries-for-net"></a>Библиотеки Azure Resource Manager для .NET

## <a name="overview"></a>Обзор

Azure Resource Manager позволяет работать с ресурсами решения как с группой.  Дополнительные сведения о Resource Manager вы найдете в статье [Общие сведения об Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## <a name="management-library"></a>Библиотека управления

Библиотека Azure Resource Manager для .NET позволяет создавать, обновлять, удалять и перечислять ресурсы и группы ресурсов.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a>Пример

В этом примере создается группа ресурсов.

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.ResourceManager.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IResourceGroup resourceGroup = azure.ResourceGroups
    .Define("ResourceGroupName")
    .WithRegion(Region.USWest)
    .Create();
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a>Примеры

* [Getting Started with Resources - Manage Resource Group - in .Net](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group) (Начало работы с ресурсами: управление группами ресурсов — .Net)
* [Управление ресурсами](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [Getting Started with Resources - Deploy Using A R M Template - in .Net](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template) (Начало работы с ресурсами: развертывание с использованием шаблона ARM — .Net)
* [Getting Started with Resources - Deploy Using A R M Template With Progress - in .Net](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress) (Начало работы с ресурсами: развертывание с использованием шаблона ARM (с описанием хода выполнения) — .Net)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
