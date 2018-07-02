---
title: Библиотеки ретранслятора служебной шины Azure для .NET
description: Справочник по библиотекам ретранслятора служебной Azure шины для .NET
keywords: Azure, .NET, SDK, API, Service Bus Relay
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: service-bus
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e0dd9c9b0a187fe6ca81d764e60afd00cbaab654
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065954"
---
# <a name="azure-service-bus-relay-libraries-for-net"></a><span data-ttu-id="3a1eb-104">Библиотеки ретранслятора служебной шины Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="3a1eb-104">Azure Service Bus Relay libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="3a1eb-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="3a1eb-105">Overview</span></span>

<span data-ttu-id="3a1eb-106">Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="3a1eb-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="3a1eb-107">Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="3a1eb-107">Relay supports a variety of different transport protocols and web services standards.</span></span>
          
<span data-ttu-id="3a1eb-108">См. дополнительные сведения о [ретрансляторе Azure](/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="3a1eb-108">Learn more about [Azure Relay](/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="client-library"></a><span data-ttu-id="3a1eb-109">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="3a1eb-109">Client library</span></span>

<span data-ttu-id="3a1eb-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="3a1eb-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Relay) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="3a1eb-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3a1eb-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a1eb-112">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="3a1eb-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a><span data-ttu-id="3a1eb-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="3a1eb-113">Samples</span></span>

<span data-ttu-id="3a1eb-114">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="3a1eb-114">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package