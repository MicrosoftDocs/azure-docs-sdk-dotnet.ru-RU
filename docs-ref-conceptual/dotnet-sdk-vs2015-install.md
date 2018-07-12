---
title: Средства Azure для Visual Studio 2015
description: Получите средства для использования библиотек Azure для .NET в Visual Studio 2015.
keywords: Azure .NET, SDK, VS2015, Visual Studio 2015
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 5046781a16b5b330b95c4ad36e8a8187126fef4e
ms.sourcegitcommit: 1c2e1fd031ad012d6888fcde3cd325f7e8e49e0f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2018
ms.locfileid: "29752816"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Средства Azure для Visual Studio 2015

Самый быстрый и простой способ установить **пакет Azure SDK для Visual Studio 2015** и **пакет SDK для Service Fabric и средства для Visual Studio 2015** — воспользоваться [установщиком веб-платформы](https://www.microsoft.com/web/downloads/platform.aspx).  Установщик веб-платформы Майкрософт — это бесплатное средство, которое упрощает скачивание, установку и обновление некоторых компонентов веб-платформы Майкрософт, в том числе средств Azure для Visual Studio 2015.  Эти пакеты SDK можно также скачать на [странице загрузок Azure](https://azure.microsoft.com/downloads/) и установить в качестве отдельных компонентов. 

## <a name="using-the-web-platform-installer"></a>Использование установщика веб-платформы

1. Скачайте и запустите этот [начальный загрузчик для установщика веб-платформы](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).  

2. Начальный загрузчик установит установщик веб-платформы (при необходимости) и автоматически поместит последние версии **пакета Azure SDK для Visual Studio 2015** и **пакета SDK для Service Fabric и средств для Visual Studio 2015** в список *Устанавливаемые элементы*.  Щелкните **Install**(Установить).

    ![Установщик веб-платформы](media/dotnet-sdk-vs2015-install/webpi.png)

3. На следующем экране нажмите кнопку **Я принимаю**.  Установщик веб-платформы начнет скачивание и установку выбранных компонентов.

4. Когда установка завершится, отобразится экран подтверждения.  Нажмите кнопку **Готово**  Теперь можете закрыть установщик веб-платформы.

## <a name="verifying-the-installation"></a>Проверка установки

1. В Visual Studio 2015 щелкните меню **Сервис** и выберите пункт **Расширения и обновления...**.

2. Отображаемый список будет содержать несколько средств Azure, например **средства службы приложений Microsoft Azure**, **подключенную службу хранилища Microsoft Azure** и **средства Service Fabric**.

    ![Расширения и обновления](media\dotnet-sdk-vs2015-install\ext-tools.png)

## <a name="next-steps"></a>Дополнительная информация

[Начало работы с API Azure для .NET](dotnet-sdk-azure-get-started.md).
