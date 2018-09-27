---
title: Библиотеки Azure Data Lake Store для .NET
description: Справочник по библиотекам Azure Data Lake Store для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-lake-store
ms.openlocfilehash: 8e55a21d84eae2ef4104c8253adec2cbc4b008e5
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190567"
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
### <a name="authentication"></a>Authentication

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

* [Azure Data Lake DotNet Client Sample](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/) (Пример клиента DotNet для Azure Data Lake)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
