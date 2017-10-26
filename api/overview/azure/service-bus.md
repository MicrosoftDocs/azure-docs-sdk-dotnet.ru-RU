---
title: "Библиотеки служебной шины Azure для .NET"
description: "Справочник по библиотекам служебной Azure шины для .NET"
keywords: Azure, .NET, SDK, API, Service Bus
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: service-bus
ms.custom: devcenter, svc-overview
ms.openlocfilehash: c2019fd39f42f9bc4a39dd4e642db9f90b7a917c
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2017
---
# <a name="azure-service-bus-libraries-for-net"></a>Библиотеки служебной шины Azure для .NET

## <a name="overview"></a>Обзор

[Служебная шина Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) — это инфраструктура обмена сообщениями, которая размещается между приложениями и позволяет им обмениваться сообщениями для улучшения масштабирования и устойчивости.

## <a name="client-library"></a>Клиентская библиотека

Установите [пакет NuGet](https://www.nuget.org/packages/WindowsAzure.ServiceBus) непосредственно из [консоли диспетчера пакетов][PackageManager].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package WindowsAzure.ServiceBus
```

### <a name="code-example"></a>Пример кода

В этом примере в очередь служебной шины отправляется сообщение.

```csharp
// using Microsoft.ServiceBus.Messaging;

QueueClient client = QueueClient.CreateFromConnectionString(connectionString, queueName);
BrokeredMessage message = new BrokeredMessage("This is a test message!");
client.Send(message);
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a>Библиотека управления

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a>Пример кода

В этом примере создается очередь служебной шины с максимальным размером 1024 МБ.

```csharp
// using Microsoft.Azure.Management.ServiceBus.Fluent;
// using Microsoft.Azure.Management.ServiceBus.Fluent.Models;

using (ServiceBusManagementClient client = new ServiceBusManagementClient(credentials))
{
    client.SubscriptionId = subscriptionId;
    QueueInner parameters = new QueueInner
    {
        MaxSizeInMegabytes = 1024
    };
    await client.Queues.CreateOrUpdateAsync(resourceGroupName, namespaceName, queueName, parameters);
}
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a>Примеры

- [Getting Started with Service - Service Bus Queue Basic - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/) (Начало работы со службой: основные сведения об очереди служебной шины — .Net)
- [Getting Started with Service - Service Bus Queue Advance Features - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/) (Начало работы со службой: расширенные функции очереди служебной шины — .Net)
- [Getting Started with Service - Service Bus Publish Subscribe Basic - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/) (Начало работы со службой: основные сведения о публикации и подписке для служебной шины — .Net)
- [Getting Started with Service - Service Bus Publish Subscribe Advance Features - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/) (Начало работы со службой: расширенные функции публикации и подписки для служебной шины — .Net)
- [Getting Started with Service - Service Bus With Claim Based Authorization - in .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/) (Начало работы со службой: служебная шина с авторизацией на основе утверждения — .Net)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?term=service+bus) примеров кода для служебной шины Azure.


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
