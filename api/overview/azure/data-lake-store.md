---
title: "Библиотеки Azure Data Lake Store для .NET"
description: "Справочник по библиотекам Azure Data Lake Store для .NET"
keywords: Azure, .NET, SDK, API, Data Lake Store
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/18/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 18746d745d64065a3d92215e704bce575130bdb0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-data-lake-store-libraries-for-net"></a>Библиотеки Azure Data Lake Store для .NET

## <a name="overview"></a>Обзор

Хранилище озера данных Azure — это крупномасштабный репозиторий корпоративного уровня для рабочих нагрузок анализа больших данных. Azure Data Lake позволяет сохранять данные с любым размером, типом и скоростью приема в одном месте для эксплуатационной и исследовательской аналитики.

Дополнительные сведения см. в [обзоре Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).

## <a name="management-library"></a>Библиотека управления

Библиотека управления позволяет подключаться к репозиториям больших данных и управлять ими.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

### <a name="code-example"></a>Пример кода

В этом примере выполняется проверка подлинности для учетной записи аналитики и хранилища, а также создаются необходимые для управления клиенты.

```csharp
/*
using AdlClient
using AdlClient.Models 
*/

// Setup authentication 
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
StoreAccountRef adls_account = new StoreAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
StoreClient adls = new StoreClient(auth, adls_account);
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/datalakestore/management)

## <a name="samples"></a>Примеры

* [Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package