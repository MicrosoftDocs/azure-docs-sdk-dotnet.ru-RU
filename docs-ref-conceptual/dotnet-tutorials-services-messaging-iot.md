---
title: "Руководства по использованию службы сообщений и IoT с .NET в Azure | Документация Майкрософт"
description: "Отправка сообщений между облачными приложениями и между устройствами и облаком с использованием .NET и служб Azure."
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: a6c50af1678c785c6a3fcd3f4f3689171069b2ee
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="net-tutorials-for-enterprise-messaging-and-internet-of-things-iot"></a>Руководства по .NET для корпоративной службы сообщений и Интернета вещей (IoT)

В таблице ниже представлены ссылки на подробные руководства по отправке и чтению сообщений между приложениями и устройствами из кода .NET с помощью служб Azure.

Пример исходного кода см. в списке [примеров кода для служб Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).


| | |
|---|---|
| **Служебная шина** | |
| [Начало работы с очередями служебной шины][1] | Создание очередей, отправка и получение сообщений и удаление очередей. | 
| [Начало работы с разделами служебной шины][2] | Узнайте, как использовать модель публикации и подписки для взаимодействия со служебной шиной.
| [Использование служебной шины на платформе .NET с протоколом AMQP 1.0][3] | Сведения об использовании протокола AMQP с приложениями служебной шины.
|**Центр Интернета вещей**|
| [Подключение устройства к Центру Интернета вещей с помощью .NET][4] | Создание удостоверений устройств, отправка сообщений и обработка данных телеметрии из Центра Интернета вещей. |   
| [Обработка сообщений Центра Интернета вещей, отправляемых с устройства в облако, с использованием маршрутов (.NET)][5] | Отправка сообщений из виртуального устройства и их обработка в облаке. |
|**Концентратор событий**|
| [Приступая к отправке событий в концентраторы событий Azure на платформе .NET Standard][6] | Отправка событий из консольного приложения в концентратор событий.
| [Основные сведения о получении сообщений с помощью узла EventProcessorHost в .NET Standard][7] | Получение и параллельная обработка сообщений.


[1]: /azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues
[2]: /azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions
[3]: /azure/service-bus-messaging/service-bus-amqp-dotnet
[4]: /azure/iot-hub/iot-hub-csharp-csharp-getstarted
[5]: /azure/iot-hub/iot-hub-csharp-csharp-process-d2c
[6]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-send
[7]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph


