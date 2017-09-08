---
title: "Руководства по использованию службы сообщений и IoT с .NET в Azure | Документация Майкрософт"
description: "Отправка сообщений между облачными приложениями и между устройствами и облаком с использованием .NET и служб Azure."
author: camsoper
manager: douge
ms.assetid: 2ce6ea06-7b0b-45e6-8ca0-44e4e4030b82
ms.devlang: dotnet
ms.topic: article
ms.service: Azure
ms.technology: Azure
ms.date: 4/10/2017
ms.author: casoper
ms.openlocfilehash: 0c3e81231ac88b2418778b83ecabcbb553608e24
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="net-tutorials-for-enterprise-messaging-and-internet-of-things-iot"></a><span data-ttu-id="8e870-103">Руководства по .NET для корпоративной службы сообщений и Интернета вещей (IoT)</span><span class="sxs-lookup"><span data-stu-id="8e870-103">.NET tutorials for enterprise messaging and Internet of Things (IoT)</span></span>

<span data-ttu-id="8e870-104">В таблице ниже представлены ссылки на подробные руководства по отправке и чтению сообщений между приложениями и устройствами из кода .NET с помощью служб Azure.</span><span class="sxs-lookup"><span data-stu-id="8e870-104">The following table links to in-depth tutorials for sending and reading messages between applications and devices in from your .NET code using Azure services.</span></span>

<span data-ttu-id="8e870-105">Пример исходного кода см. в списке [примеров кода для служб Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span><span class="sxs-lookup"><span data-stu-id="8e870-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>


| | |
|---|---|
| <span data-ttu-id="8e870-106">**Служебная шина**</span><span class="sxs-lookup"><span data-stu-id="8e870-106">**Service Bus**</span></span> | |
| <span data-ttu-id="8e870-107">[Начало работы с очередями служебной шины][1]</span><span class="sxs-lookup"><span data-stu-id="8e870-107">[How to use Service Bus queues][1]</span></span> | <span data-ttu-id="8e870-108">Создание очередей, отправка и получение сообщений и удаление очередей.</span><span class="sxs-lookup"><span data-stu-id="8e870-108">Create queues, send and receive messages, and delete queues.</span></span> | 
| <span data-ttu-id="8e870-109">[Начало работы с разделами служебной шины][2]</span><span class="sxs-lookup"><span data-stu-id="8e870-109">[How to use Service Bus topics and subscriptions][2]</span></span> | <span data-ttu-id="8e870-110">Узнайте, как использовать модель публикации и подписки для взаимодействия со служебной шиной.</span><span class="sxs-lookup"><span data-stu-id="8e870-110">Learn how to use publish/subscribe communication model with Service Bus.</span></span>
| <span data-ttu-id="8e870-111">[Использование служебной шины на платформе .NET с протоколом AMQP 1.0][3]</span><span class="sxs-lookup"><span data-stu-id="8e870-111">[Using Service Bus from .NET with AMQP 1.0][3]</span></span> | <span data-ttu-id="8e870-112">Сведения об использовании протокола AMQP с приложениями служебной шины.</span><span class="sxs-lookup"><span data-stu-id="8e870-112">Learn how to use AMQP in you Service Bus applications.</span></span>
|<span data-ttu-id="8e870-113">**Центр Интернета вещей**</span><span class="sxs-lookup"><span data-stu-id="8e870-113">**IoT Hub**</span></span>|
| <span data-ttu-id="8e870-114">[Подключение устройства к Центру Интернета вещей с помощью .NET][4]</span><span class="sxs-lookup"><span data-stu-id="8e870-114">[Connect a simulated device to your IoT Hub][4]</span></span> | <span data-ttu-id="8e870-115">Создание удостоверений устройств, отправка сообщений и обработка данных телеметрии из Центра Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="8e870-115">Create a device identity, send messages, and process telemetry from your IoT Hub.</span></span> |   
| <span data-ttu-id="8e870-116">[Обработка сообщений Центра Интернета вещей, отправляемых с устройства в облако, с использованием маршрутов (.NET)][5]</span><span class="sxs-lookup"><span data-stu-id="8e870-116">[Process device-to-cloud messages][5]</span></span> | <span data-ttu-id="8e870-117">Отправка сообщений из виртуального устройства и их обработка в облаке.</span><span class="sxs-lookup"><span data-stu-id="8e870-117">Send messages from a simulated device and process them in the cloud.</span></span> |
|<span data-ttu-id="8e870-118">**Концентратор событий**</span><span class="sxs-lookup"><span data-stu-id="8e870-118">**Event Hub**</span></span>|
| <span data-ttu-id="8e870-119">[Приступая к отправке событий в концентраторы событий Azure на платформе .NET Standard][6]</span><span class="sxs-lookup"><span data-stu-id="8e870-119">[Send events to an Event Hub][6]</span></span> | <span data-ttu-id="8e870-120">Отправка событий из консольного приложения в концентратор событий.</span><span class="sxs-lookup"><span data-stu-id="8e870-120">Send events to Event hub from a console application.</span></span>
| <span data-ttu-id="8e870-121">[Основные сведения о получении сообщений с помощью узла EventProcessorHost в .NET Standard][7]</span><span class="sxs-lookup"><span data-stu-id="8e870-121">[Receive events from Event Hubs][7]</span></span> | <span data-ttu-id="8e870-122">Получение и параллельная обработка сообщений.</span><span class="sxs-lookup"><span data-stu-id="8e870-122">Receive messages and process them in parallel.</span></span>


[1]: /azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues
[2]: /azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions
[3]: /azure/service-bus-messaging/service-bus-amqp-dotnet
[4]: /azure/iot-hub/iot-hub-csharp-csharp-getstarted
[5]: /azure/iot-hub/iot-hub-csharp-csharp-process-d2c
[6]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-send
[7]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph


