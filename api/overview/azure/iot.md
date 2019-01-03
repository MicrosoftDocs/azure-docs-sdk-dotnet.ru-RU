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
# <a name="azure-iot-libraries-for-net"></a><span data-ttu-id="2b712-103">Библиотеки Azure IoT для .NET</span><span class="sxs-lookup"><span data-stu-id="2b712-103">Azure IoT libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="2b712-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="2b712-104">Overview</span></span>

<span data-ttu-id="2b712-105">[Центр Интернета вещей Azure](https://azure.microsoft.com/services/iot-hub/) — это полностью управляемая служба, которая обеспечивает надежный и защищенный двусторонний обмен данными между миллионами устройств Интернета вещей и серверной частью решения.</span><span class="sxs-lookup"><span data-stu-id="2b712-105">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is a fully managed service that enables reliable and secure bi-directional communications between millions of devices and a solution back end.</span></span>

<span data-ttu-id="2b712-106">Решение IoT поддерживает разные устройства и источники данных — от простого датчика с подключением к сети до изолированного вычислительного устройства с широкими возможностями.</span><span class="sxs-lookup"><span data-stu-id="2b712-106">Devices and data sources in an IoT solution can range from a simple network-connected sensor to a powerful, standalone computing device.</span></span> <span data-ttu-id="2b712-107">Ресурсы устройства, к которым относятся продуктивность обработки, объем памяти, пропускная способность для обмена данными и поддержка протокола обмена данными, могут быть ограниченными.</span><span class="sxs-lookup"><span data-stu-id="2b712-107">Devices may have limited processing capability, memory, communication bandwidth, and communication protocol support.</span></span> <span data-ttu-id="2b712-108">Благодаря [пакетам SDK для устройств](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) Центра Интернета вещей вы можете реализовать клиентские приложения для использования на разных устройствах и во внутренних приложениях.</span><span class="sxs-lookup"><span data-stu-id="2b712-108">The IoT [device SDKs](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) enable you to implement client applications for a wide variety of devices and back-end applications.</span></span>

<span data-ttu-id="2b712-109">Пакет SDK для устройств для .NET упрощает создание устройств на платформе .NET, подключаемых к Центру Интернета вещей Azure.</span><span class="sxs-lookup"><span data-stu-id="2b712-109">The device SDK for .NET facilitates building devices running .NET that connect to Azure IoT Hub.</span></span>

<span data-ttu-id="2b712-110">Пакет SDK для служб для .NET упрощает создание внутренних приложений с помощью .NET, которые управляют и позволяют управлять устройствами из облака.</span><span class="sxs-lookup"><span data-stu-id="2b712-110">The service SDK for .NET facilitates building back-end applications using .NET that manage and allow controlling devices from the Cloud.</span></span>

<span data-ttu-id="2b712-111">[Документация по Центру Интернета вещей](https://docs.microsoft.com/azure/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="2b712-111">[Learn more about Azure IoT](https://docs.microsoft.com/azure/iot-hub/).</span></span>


## <a name="client-library"></a><span data-ttu-id="2b712-112">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="2b712-112">Client library</span></span>

<span data-ttu-id="2b712-113">Используйте клиент для устройств Интернета вещей для .NET, чтобы подключаться к Центру Интернета вещей и отправлять сообщения в него.</span><span class="sxs-lookup"><span data-stu-id="2b712-113">Use the .NET IoT devices client to connect and send messages to your IoT Hub.</span></span>

<span data-ttu-id="2b712-114">Установите [пакет NuGet]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="2b712-114">Install the [NuGet package]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="2b712-115">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2b712-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Devices.Client
```

```bash
dotnet add package Microsoft.Azure.Devices.Client
```
### <a name="code-examples"></a><span data-ttu-id="2b712-116">Примеры кода</span><span class="sxs-lookup"><span data-stu-id="2b712-116">Code Examples</span></span> 

<span data-ttu-id="2b712-117">В этом примере устанавливается подключение к Центру Интернета вещей и отправляется одно сообщение в секунду.</span><span class="sxs-lookup"><span data-stu-id="2b712-117">This example connects to the IoT Hub and sends one message per second.</span></span>

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
> [<span data-ttu-id="2b712-118">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="2b712-118">Explore the client APIs</span></span>](/dotnet/api/overview/azure/iot/client)

## <a name="samples"></a><span data-ttu-id="2b712-119">Примеры</span><span class="sxs-lookup"><span data-stu-id="2b712-119">Samples</span></span>

- <span data-ttu-id="2b712-120">[Generic Web Service to Event Hub scenario](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/) (Сценарий отправки данных универсальной веб-службы в концентратор событий)</span><span class="sxs-lookup"><span data-stu-id="2b712-120">[Generic Web Service to Event Hub scenario](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/)</span></span>

<span data-ttu-id="2b712-121">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) примеров реализации кода для Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="2b712-121">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) of Azure IoT Upsamples.</span></span>

<span data-ttu-id="2b712-122">Дополнительные рекомендации см. в [руководстве разработчика для Центра Интернета вещей](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide).</span><span class="sxs-lookup"><span data-stu-id="2b712-122">View the [Azure IoT Hub developer guide](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide) for more guidance.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
