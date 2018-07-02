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
# <a name="azure-data-factory-libraries-for-net"></a>Библиотеки фабрики данных Azure для .NET

## <a name="overview"></a>Обзор

Фабрика данных Azure — это облачная служба интеграции данных. Она позволяет создавать рабочие процессы на основе данных в облаке, чтобы выполнять оркестрацию и автоматизацию для перемещения и преобразования данных.

Дополнительные сведения см. в статье [Введение в фабрику данных Azure](/azure/data-factory/data-factory-introduction).

## <a name="management-library---data-factory-v2-preview"></a>Библиотека управления: фабрика данных версии 2 (предварительная версия)

Библиотека управления служит для создания и планирования рабочих процессов на основе данных (конвейеров) в фабрике данных версии 2 (предварительная версия).  Дополнительные сведения см. в статье [Создание фабрики данных и конвейера с помощью пакета SDK .NET](/azure/data-factory/quickstart-create-data-factory-dot-net).

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
# Get the most recent prerelease package
Install-Package Microsoft.Azure.Management.DataFactory -Prerelease
```

```bash
# Be sure to include the most recent version from the NuGet package page
dotnet add package Microsoft.Azure.Management.DataFactory --version 0.2.0-preview
```

### <a name="code-example"></a>Пример кода

В примере ниже библиотека управления используется для создания фабрики данных.

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
> [Обзор API-интерфейсов управления](/dotnet/api/microsoft.azure.management.datafactory)

## <a name="management-library---data-factory-v1"></a>Библиотека управления: фабрика данных версии 1

Библиотека управления служит для создания и планирования рабочих процессов на основе данных (конвейеров) в фабрике данных версии 1.  Дополнительные сведения см. в документации по [фабрике данных версии 1](/azure/data-factory/v1/data-factory-introduction).

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a>Пример кода

В примере ниже библиотека управления используется для создания фабрики данных.

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
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a>Примеры

* [MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) (MyDriving — пример приложения для Интернета вещей и мобильных устройств). В примере для предоставления данных используется фабрика данных.

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
