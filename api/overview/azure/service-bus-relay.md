---
title: Библиотеки ретранслятора служебной шины Azure для .NET
description: Справочник по библиотекам ретранслятора служебной Azure шины для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: service-bus-relay
ms.openlocfilehash: 9190e8efdebe1c352b4fb2c98be189089b0975d2
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348126"
---
# <a name="azure-service-bus-relay-libraries-for-net"></a><span data-ttu-id="9eded-103">Библиотеки ретранслятора служебной шины Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="9eded-103">Azure Service Bus Relay libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9eded-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="9eded-104">Overview</span></span>

<span data-ttu-id="9eded-105">Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="9eded-105">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="9eded-106">Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="9eded-106">Relay supports a variety of different transport protocols and web services standards.</span></span>
          
<span data-ttu-id="9eded-107">См. дополнительные сведения о [ретрансляторе Azure](/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="9eded-107">Learn more about [Azure Relay](/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="client-library"></a><span data-ttu-id="9eded-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="9eded-108">Client library</span></span>

<span data-ttu-id="9eded-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9eded-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Relay) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9eded-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9eded-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9eded-111">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="9eded-111">Explore the client APIs</span></span>](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a><span data-ttu-id="9eded-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="9eded-112">Samples</span></span>

<span data-ttu-id="9eded-113">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="9eded-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package