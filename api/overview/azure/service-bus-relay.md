---
title: "Библиотеки ретранслятора служебной шины Azure для .NET"
description: "Справочник по библиотекам ретранслятора служебной Azure шины для .NET"
keywords: Azure, .NET, SDK, API, Service Bus Relay
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/14/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 13a875b837648a05401453e975c9cd70d5e203a1
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-service-bus-relay-libraries-for-net"></a><span data-ttu-id="b4a87-104">Библиотеки ретранслятора служебной шины Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="b4a87-104">Azure Service Bus Relay libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b4a87-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="b4a87-105">Overview</span></span>

<span data-ttu-id="b4a87-106">Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="b4a87-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="b4a87-107">Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="b4a87-107">Relay supports a variety of different transport protocols and web services standards.</span></span>
          
<span data-ttu-id="b4a87-108">См. дополнительные сведения о [ретрансляторе Azure](https://docs.microsoft.com/en-us/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="b4a87-108">Learn more about [Azure Relay](https://docs.microsoft.com/en-us/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="client-library"></a><span data-ttu-id="b4a87-109">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="b4a87-109">Client library</span></span>

<span data-ttu-id="b4a87-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="b4a87-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Relay) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b4a87-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4a87-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4a87-112">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="b4a87-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a><span data-ttu-id="b4a87-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="b4a87-113">Samples</span></span>

<span data-ttu-id="b4a87-114">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="b4a87-114">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package