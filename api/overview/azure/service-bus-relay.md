---
title: Библиотеки ретранслятора служебной шины Azure для .NET
description: Справочник по библиотекам ретранслятора служебной Azure шины для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: service-bus
ms.openlocfilehash: 75c481ab23e461c5194a9eeb0ca668af98f4d2d7
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189987"
---
# <a name="azure-service-bus-relay-libraries-for-net"></a><span data-ttu-id="b50dd-103">Библиотеки ретранслятора служебной шины Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="b50dd-103">Azure Service Bus Relay libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b50dd-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="b50dd-104">Overview</span></span>

<span data-ttu-id="b50dd-105">Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="b50dd-105">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="b50dd-106">Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="b50dd-106">Relay supports a variety of different transport protocols and web services standards.</span></span>
          
<span data-ttu-id="b50dd-107">См. дополнительные сведения о [ретрансляторе Azure](/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="b50dd-107">Learn more about [Azure Relay](/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="client-library"></a><span data-ttu-id="b50dd-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="b50dd-108">Client library</span></span>

<span data-ttu-id="b50dd-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="b50dd-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Relay) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b50dd-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b50dd-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b50dd-111">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="b50dd-111">Explore the client APIs</span></span>](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a><span data-ttu-id="b50dd-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="b50dd-112">Samples</span></span>

<span data-ttu-id="b50dd-113">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="b50dd-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package