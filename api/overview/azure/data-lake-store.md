---
title: Библиотеки Azure Data Lake Store для .NET
description: Справочник по библиотекам Azure Data Lake Store для .NET
keywords: Azure, .NET, SDK, API, Data Lake Store
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-lake-store
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e8380c4a9ebf86f03fe87fc800dffda10e48e60a
ms.sourcegitcommit: 3e904e6e4f04f1c92d729459434c85faff32e386
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2017
ms.locfileid: "26588477"
---
# <a name="azure-data-lake-store-libraries-for-net"></a>Библиотеки Azure Data Lake Store для .NET

## <a name="overview"></a>Обзор

Хранилище озера данных Azure — это крупномасштабный репозиторий корпоративного уровня для рабочих нагрузок анализа больших данных. Azure Data Lake позволяет сохранять данные с любым размером, типом и скоростью приема в одном месте для эксплуатационной и исследовательской аналитики.

Дополнительные сведения см. в [обзоре Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).

## <a name="client-library"></a>Клиентская библиотека

Клиентская библиотека используется для выполнения в Data Lake Store операций файловой системы, таких как создание папок в учетной записи Data Lake Store, отправка файлов и загрузка файлов.  Полное руководство по использованию Data Lake Store с .NET см. в статье [Операции файловой системы в Azure Data Lake Store с использованием SDK для .NET](/azure/data-lake-store/data-lake-store-data-operations-net-sdk).

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.DataLake.Store
```
### <a name="authentication"></a>Аутентификация

* Дополнительные сведения о проверке подлинности пользователей в приложении см. в статье [End-user authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk) (Аутентификация пользователей в Data Lake Store с использованием пакета SDK для .NET).
* Дополнительные сведения о проверке подлинности между службами в приложении см. в статье [Service-to-service authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk) (Аутентификация между службами в Data Lake Store с использованием пакета SDK для .NET).

### <a name="code-example"></a>Пример кода

Следующий фрагмент кода создает клиентский объект файловой системы Data Lake Store, который используется для передачи запросов к службе.

```csharp
// Create client objects
AdlsClient client = AdlsClient.CreateClient(_adlsAccountName, adlCreds);
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/datalakestore/client)


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

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/datalakestore/management)


## <a name="samples"></a>Примеры

* [Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
