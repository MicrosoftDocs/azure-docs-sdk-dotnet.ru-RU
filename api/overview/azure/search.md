---
title: Библиотеки службы "Поиск Azure" для .NET
description: Справочник по библиотекам службы "Поиск Azure" для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: search
ms.openlocfilehash: cf622ccb59f10a5270c02fa76d7396345fbb1a9b
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190247"
---
# <a name="azure-search-libraries-for-net"></a>Библиотеки службы "Поиск Azure" для .NET

## <a name="overview"></a>Обзор

[Поиск Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search) — это полностью управляемая облачная служба поиска, которая предоставляет широкие возможности поиска по данным в мобильных, корпоративных и веб-приложениях.

## <a name="client-library"></a>Клиентская библиотека

Используйте клиентскую библиотеку службы "Поиск Azure", чтобы получать доступ к операциям индексирования и поиска и выполнять их со службами поиска, индексами, документами или другими объектами. Пошаговое описание см. в статье [Использование службы поиска Azure в приложении .NET](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Search) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Search
```

```bash
dotnet add package Microsoft.Azure.Search
```

### <a name="code-example"></a>Пример кода

```csharp
/* Include these 'using' directives:
   using Microsoft.Azure.Search;
   using Microsoft.Azure.Search.Models;
*/

// A service endpoint and an api-key are required on a connection.
// Set them in a config file (not shown) and then connect to the client.
IConfigurationBuilder builder = new ConfigurationBuilder().AddJsonFile("appsettings.json");
IConfigurationRoot configuration = builder.Build();

SearchServiceClient serviceClient = CreateSearchServiceClient(configuration);

// Create an index named hotels
ISearchIndexClient indexClient = serviceClient.Indexes.GetClient("hotels");

```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/search/client)


## <a name="management-library"></a>Библиотека управления

Используйте библиотеку управления для службы "Поиск Azure", чтобы подготавливать службы, управлять ключами API и настраивать ресурсы. Управление службами зависит от Azure Resource Manager для идентификации подписчиков и клиентов. Как правило, регистрация приложений и проверка подлинности с помощью Azure Active Directory также требуется для поддержки рабочего процесса. Общие сведения о подготовке службы "Поиск Azure" см. в статье [об использовании REST API управления](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Search
```

```bash
dotnet add package Microsoft.Azure.Management.Search
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/search/management)

## <a name="samples"></a>Примеры

 + [Azure-Samples/search-dotnet-getting-started](https://github.com/Azure-Samples/search-dotnet-getting-started)
 + [Azure-Samples/search-dotnet-management-api](https://github.com/Azure-Samples/search-dotnet-management-api)

Другие примеры для службы "Поиск" см. в [репозитории примеров Azure](https://github.com/Azure-Samples/) на сайте Github.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
