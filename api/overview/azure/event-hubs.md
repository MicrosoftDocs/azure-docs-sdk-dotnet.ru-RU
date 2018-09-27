---
title: Библиотеки Центров событий Azure для .NET
description: Справочник по библиотекам Центров событий Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: event-hubs
ms.openlocfilehash: 74c533bef598b90369009d68a759d35d122a368d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190277"
---
# <a name="azure-event-hubs-libraries-for-net"></a>Библиотеки Центров событий Azure для .NET

## <a name="overview"></a>Обзор

Центры событий Azure представляют собой платформу потоковой передачи с высокой степенью масштабируемости и службу приема событий.

Дополнительные сведения о Центрах событий Azure см. в статье [Что такое Центры событий?](/azure/event-hubs/event-hubs-what-is-event-hubs).  Чтобы приступить к работе, ознакомьтесь со статьей [Руководство по программированию Центров событий](/azure/event-hubs/event-hubs-programming-guide).

## <a name="client-library"></a>Клиентская библиотека

Используйте клиент Центров событий, чтобы отправлять сообщения в Центры событий и получать их из Центров событий.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a>Пример кода

В коде ниже создается клиент Центров событий и в концентратор событий отправляется сообщение.

```csharp
EventHubsConnectionStringBuilder connectionStringBuilder = new EventHubsConnectionStringBuilder(eventHubConnectionString)
{
    EntityPath = eventHubEntityPath
};

EventHubClient eventHubClient = EventHubClient.CreateFromConnectionString(connectionStringBuilder.ToString());
string message = $"Message {i}";
Console.WriteLine($"Sending message: {message}");
await eventHubClient.SendAsync(new EventData(Encoding.UTF8.GetBytes(message)));
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a>Библиотека управления

При помощи библиотеки управления Центров событий можно создавать, обновлять и удалять концентраторы и группы объектов-получателей.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a>Пример кода

В коде ниже создается концентратор событий.

```csharp
TokenCredentials creds = new TokenCredentials(token);
EventHubManagementClient ehClient = new EventHubManagementClient(creds)
{
    SubscriptionId = subscriptionId
};

EventHubCreateOrUpdateParameters ehParams = new EventHubCreateOrUpdateParameters()
{
    Location = location
};

Console.WriteLine("Creating Event Hub...");
await ehClient.EventHubs.CreateOrUpdateAsync(resourceGroupName, namespaceName, EventHubName, ehParams);
Console.WriteLine("Created Event Hub successfully.");
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a>Учебники

* [Отправка событий в Центры событий Azure с помощью платформы .NET Framework](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [Получение событий от Центров событий Azure с помощью платформы .NET Framework](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a>Примеры

* [Примеры Центров событий Azure](https://github.com/Azure/azure-event-hubs/tree/master/samples)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
