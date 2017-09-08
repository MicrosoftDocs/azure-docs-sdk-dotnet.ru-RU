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
# <a name="azure-data-factory-libraries-for-net"></a>Библиотеки фабрики данных Azure для .NET

## <a name="overview"></a>Обзор

Фабрика данных Azure — это облачная служба интеграции данных. Она позволяет создавать рабочие процессы на основе данных в облаке, чтобы выполнять оркестрацию и автоматизацию для перемещения и преобразования данных.

Дополнительные сведения см. в статье [Введение в фабрику данных Azure](/azure/data-factory/data-factory-introduction).

## <a name="management-library"></a>Библиотека управления

Библиотека управления служит для создания и планирования рабочих процессов на основе данных (конвейеров).

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
