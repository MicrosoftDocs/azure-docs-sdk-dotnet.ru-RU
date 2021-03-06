---
title: Библиотеки Azure IoT для .NET
description: Справочник по библиотекам Azure IoT для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: iot-hub
ms.openlocfilehash: 667663c5f5e3452fcc5ec0c4f3ded997370c5852
ms.sourcegitcommit: 7f1a1bf275d8489f8df266b746baa33d66fcb2c8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737079"
---
# <a name="azure-iot-libraries-for-net"></a>Библиотеки Azure IoT для .NET

## <a name="overview"></a>Обзор

[Центр Интернета вещей Azure](https://azure.microsoft.com/services/iot-hub/) — это полностью управляемая служба, которая обеспечивает надежный и защищенный двусторонний обмен данными между миллионами устройств Интернета вещей и серверной частью решения.

Решение IoT поддерживает разные устройства и источники данных — от простого датчика с подключением к сети до изолированного вычислительного устройства с широкими возможностями. Ресурсы устройства, к которым относятся продуктивность обработки, объем памяти, пропускная способность для обмена данными и поддержка протокола обмена данными, могут быть ограниченными. Благодаря [пакетам SDK для устройств](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) Центра Интернета вещей вы можете реализовать клиентские приложения для использования на разных устройствах и во внутренних приложениях.

Пакет SDK для устройств для .NET упрощает создание устройств на платформе .NET, подключаемых к Центру Интернета вещей Azure.

Пакет SDK для служб для .NET упрощает создание внутренних приложений с помощью .NET, которые управляют и позволяют управлять устройствами из облака.

[Документация по Центру Интернета вещей](https://docs.microsoft.com/azure/iot-hub/).


## <a name="client-library"></a>Клиентская библиотека

Используйте клиент для устройств Интернета вещей для .NET, чтобы подключаться к Центру Интернета вещей и отправлять сообщения в него.

Установите [пакет NuGet]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Devices.Client
```

```bash
dotnet add package Microsoft.Azure.Devices.Client
```
### <a name="code-examples"></a>Примеры кода 

В этом примере устанавливается подключение к Центру Интернета вещей и отправляется одно сообщение в секунду.

```csharp
string deviceKey = "<deviceKey>";
string deviceId = "<deviceId>";
string iotHubHostName = "<IoTHubHostname>";
var deviceAuthentication = new DeviceAuthenticationWithRegistrySymmetricKey(deviceId, deviceKey);

DeviceClient deviceClient = DeviceClient.Create(iotHubHostName, deviceAuthentication, TransportType.Mqtt);

while (true)
{
    double currentTemperature = 20 + Rand.NextDouble() * 15;
    double currentHumidity = 60 + Rand.NextDouble() * 20;

    var telemetryDataPoint = new
    {
        messageId = _messageId++,
        deviceId = deviceId,
        temperature = currentTemperature,
        humidity = currentHumidity
    };
    string messageString = JsonConvert.SerializeObject(telemetryDataPoint);
    Message message = new Message(Encoding.ASCII.GetBytes(messageString));
    message.Properties.Add("temperatureAlert", (currentTemperature > 30) ? "true" : "false");

    await deviceClient.SendEventAsync(message);
    Console.WriteLine("{0} > Sending message: {1}", DateTime.Now, messageString);

    await Task.Delay(1000);
}
```


> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/iot/client)

## <a name="samples"></a>Примеры

- [Generic Web Service to Event Hub scenario](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/) (Сценарий отправки данных универсальной веб-службы в концентратор событий)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) примеров реализации кода для Azure IoT.

Дополнительные рекомендации см. в [руководстве разработчика для Центра Интернета вещей](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide).

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
