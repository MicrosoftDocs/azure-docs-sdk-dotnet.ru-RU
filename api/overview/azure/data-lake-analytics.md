---
title: Библиотеки Azure Data Lake Analytics для .NET
description: Справочник по библиотекам Azure Data Lake Analytics для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-lake-analytics
ms.openlocfilehash: 829f9245ae06c64c4ad9a175fd25c742533a284e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189797"
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a>Библиотеки Azure Data Lake Analytics для .NET

## <a name="overview"></a>Обзор

Azure Data Lake Analytics — это служба обработки заданий аналитики по запросу, которая позволяет упростить анализ больших данных.

Дополнительные сведения см. в статье [Обзор аналитики озера данных Microsoft Azure](/azure/data-lake-analytics/data-lake-analytics-overview).

## <a name="management-library"></a>Библиотека управления

Библиотека управления предназначена для подключения к службе и управления заданиями аналитики.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a>Пример кода

В примере ниже создаются клиенты для подключения и управления учетной записью аналитики.

```csharp
/*
using AdlClient 
*/

// Setup authentication for this demo
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
AnalyticsAccountRef adla_account = new AnalyticsAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
AnalyticsClient adla = new AnalyticsClient(auth, adla_account);
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a>Примеры
* [Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
