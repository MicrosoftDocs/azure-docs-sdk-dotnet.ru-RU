---
title: "Средства Azure для Visual Studio 2015"
description: "Получите средства для использования библиотек Azure для .NET в Visual Studio 2015."
keywords: Azure .NET, SDK, VS2015, Visual Studio 2015
author: camsoper
manager: douge
ms.author: casoper
ms.date: 07/25/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.openlocfilehash: bee09801efd4f7291981bc85cd9c6a5d0b795b6e
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="135db-104">Средства Azure для Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="135db-104">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="135db-105">Самый быстрый и простой способ установить **пакет Azure SDK для Visual Studio 2015** и **пакет SDK для Service Fabric и средства для Visual Studio 2015** — воспользоваться [установщиком веб-платформы](https://www.microsoft.com/web/downloads/platform.aspx).</span><span class="sxs-lookup"><span data-stu-id="135db-105">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span>  <span data-ttu-id="135db-106">Установщик веб-платформы Майкрософт — это бесплатное средство, которое упрощает скачивание, установку и обновление некоторых компонентов веб-платформы Майкрософт, в том числе средств Azure для Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="135db-106">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span>  <span data-ttu-id="135db-107">Эти пакеты SDK можно также скачать на [странице загрузок Azure](https://azure.microsoft.com/downloads/) и установить в качестве отдельных компонентов.</span><span class="sxs-lookup"><span data-stu-id="135db-107">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span> 

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="135db-108">Использование установщика веб-платформы</span><span class="sxs-lookup"><span data-stu-id="135db-108">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="135db-109">Скачайте и запустите этот [начальный загрузчик для установщика веб-платформы](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span><span class="sxs-lookup"><span data-stu-id="135db-109">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>  

2. <span data-ttu-id="135db-110">Начальный загрузчик установит установщик веб-платформы (при необходимости) и автоматически поместит последние версии **пакета Azure SDK для Visual Studio 2015** и **пакета SDK для Service Fabric и средств для Visual Studio 2015** в список *Устанавливаемые элементы*.</span><span class="sxs-lookup"><span data-stu-id="135db-110">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span>  <span data-ttu-id="135db-111">Щелкните **Install**(Установить).</span><span class="sxs-lookup"><span data-stu-id="135db-111">Click **Install**.</span></span>

    ![Установщик веб-платформы](media/dotnet-sdk-vs2015-install/webpi.png)

3. <span data-ttu-id="135db-113">На следующем экране нажмите кнопку **Я принимаю**.</span><span class="sxs-lookup"><span data-stu-id="135db-113">On the next screen, click **I Accept**.</span></span>  <span data-ttu-id="135db-114">Установщик веб-платформы начнет скачивание и установку выбранных компонентов.</span><span class="sxs-lookup"><span data-stu-id="135db-114">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="135db-115">Когда установка завершится, отобразится экран подтверждения.</span><span class="sxs-lookup"><span data-stu-id="135db-115">After the installation is finished, it will display a confirmation screen.</span></span>  <span data-ttu-id="135db-116">Нажмите кнопку **Готово**</span><span class="sxs-lookup"><span data-stu-id="135db-116">Click **Finish**.</span></span>  <span data-ttu-id="135db-117">Теперь можете закрыть установщик веб-платформы.</span><span class="sxs-lookup"><span data-stu-id="135db-117">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="135db-118">Проверка установки</span><span class="sxs-lookup"><span data-stu-id="135db-118">Verifying the installation</span></span>

1. <span data-ttu-id="135db-119">В Visual Studio 2015 щелкните меню **Сервис** и выберите пункт **Расширения и обновления...**.</span><span class="sxs-lookup"><span data-stu-id="135db-119">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="135db-120">Отображаемый список будет содержать несколько средств Azure, например **средства службы приложений Microsoft Azure**, **подключенную службу хранилища Microsoft Azure** и **средства Service Fabric**.</span><span class="sxs-lookup"><span data-stu-id="135db-120">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![Расширения и обновления](media\dotnet-sdk-vs2015-install\ext-tools.png)

## <a name="next-steps"></a><span data-ttu-id="135db-122">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="135db-122">Next steps</span></span>

<span data-ttu-id="135db-123">[Начало работы с API Azure для .NET](dotnet-sdk-azure-get-started.md).</span><span class="sxs-lookup"><span data-stu-id="135db-123">[Get started with Azure libraries for .NET](dotnet-sdk-azure-get-started.md).</span></span>
