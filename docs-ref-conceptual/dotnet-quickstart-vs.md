---
title: Развертывание в Azure из Visual Studio
description: Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET.
keywords: Azure .NET, SDK, Azure .NET API Reference, Azure .NET class library
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.openlocfilehash: 87f65d8b8b1b1a5184b9d71770c08be472c7e498
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2018
ms.locfileid: "31005891"
---
# <a name="deploy-to-azure-from-visual-studio"></a><span data-ttu-id="0e8d0-104">Развертывание в Azure из Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e8d0-104">Deploy to Azure from Visual Studio</span></span>

<span data-ttu-id="0e8d0-105">Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-105">This tutorial will walk you through building and deploying a Microsoft Azure application using Visual Studio and .NET.</span></span>  <span data-ttu-id="0e8d0-106">Вы создадите веб-приложение со списком дел на базе MVC ASP.NET Core, размещенное как веб-приложение Azure и использующее Azure Cosmos DB для хранения данных.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-106">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure Cosmos DB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e8d0-107">предварительным требованиям</span><span class="sxs-lookup"><span data-stu-id="0e8d0-107">Prerequisites</span></span>

* [<span data-ttu-id="0e8d0-108">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0e8d0-108">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* <span data-ttu-id="0e8d0-109">[Подписка Microsoft Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="0e8d0-109">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>

## <a name="create-an-azure-cosmos-db-account"></a><span data-ttu-id="0e8d0-110">создание учетной записи Azure Cosmos DB;</span><span class="sxs-lookup"><span data-stu-id="0e8d0-110">Create an Azure Cosmos DB account</span></span>

<span data-ttu-id="0e8d0-111">Azure Cosmos DB используется для хранения данных приложения, которое вы создадите в этом руководстве, поэтому вам необходимо создать учетную запись.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-111">Azure Cosmos DB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="0e8d0-112">Запустите этот скрипт локально или в Cloud Shell, чтобы создать учетную запись API SQL для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-112">Run this script locally or in the Cloud Shell to create an Azure Cosmos DB SQL API account.</span></span>  <span data-ttu-id="0e8d0-113">Нажмите кнопку **Попробовать** на блоке кода ниже, чтобы запустить [Azure Cloud Shell](/azure/cloud-shell/). Затем скопируйте и вставьте блок скрипта в оболочку.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-113">Click the **Try it** button on the code block below to launch the [Azure Cloud Shell](/azure/cloud-shell/) and copy/paste the script block into the shell.</span></span>

```azurecli-interactive
# Create the DotNetAzureTutorial resource group
az group create --name DotNetAzureTutorial --location EastUS

# Generate a unique name for the account
let randomNum=$RANDOM*$RANDOM
cosmosdbname=dotnettutorial$randomNum

# Create the Azure Cosmos DB account
az cosmosdb create --name $cosmosdbname --resource-group DotNetAzureTutorial

# Retrieve the endpoint and key (you'll need these later)
cosmosEndpoint=$(az cosmosdb show -n $cosmosdbname -g DotNetAzureTutorial --query [documentEndpoint] -o tsv)
cosmosAuthKey=$(az cosmosdb list-keys -n $cosmosdbname -g DotNetAzureTutorial --query [primaryMasterKey] -o tsv)
printf "\n\nauthKey: $cosmosAuthKey\nendpoint: $cosmosEndpoint\n\n"

# Done!

```

<span data-ttu-id="0e8d0-114">Запишите отображаемые значения **authKey** и **endpoint**.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-114">Make a note of the displayed **authKey** and **endpoint**</span></span> 

## <a name="downloading-and-running-the-application"></a><span data-ttu-id="0e8d0-115">Загрузка и запуск приложения</span><span class="sxs-lookup"><span data-stu-id="0e8d0-115">Downloading and running the application</span></span>

<span data-ttu-id="0e8d0-116">Для этого руководства вам нужно получить пример кода и подключить его к учетной записи Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-116">Let's get the sample code for this walkthrough and hook it up to your Azure Cosmos DB account.</span></span>

1. <span data-ttu-id="0e8d0-117">Скачайте пример кода.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-117">Download the sample code.</span></span>  <span data-ttu-id="0e8d0-118">Вы можете [получить его в GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) или, если у вас есть [клиент командной строки git](https://git-scm.com/), клонировать на локальный компьютер с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="0e8d0-118">You can [get it from GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), or if you have the [git command line client](https://git-scm.com/), clone it to your local machine with the following command:</span></span>

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. <span data-ttu-id="0e8d0-119">Откройте **todo.csproj** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-119">Open **todo.csproj** in Visual Studio.</span></span>

3. <span data-ttu-id="0e8d0-120">Откройте **appsettings.json** в веб-проекте.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-120">Open **appsettings.json** in the web project.</span></span>  <span data-ttu-id="0e8d0-121">Найдите эти строки:</span><span class="sxs-lookup"><span data-stu-id="0e8d0-121">Look for the following lines:</span></span>

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    <span data-ttu-id="0e8d0-122">Замените значения **AUTHKEYVALUE** и **ENDPOINTVALUE** записанными ранее значениями.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-122">Replace **AUTHKEYVALUE** and **ENDPOINTVALUE** with the values you noted earlier.</span></span>

4. <span data-ttu-id="0e8d0-123">Нажмите клавишу **F5**, чтобы восстановить пакеты NuGet проекта, выполните сборку проекта и запустите его локально.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-123">Press **F5** to restore the project's NuGet packages, build the project, and run it locally.</span></span>

<span data-ttu-id="0e8d0-124">Веб-приложение следует запускать локально в браузере.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-124">The web application should run locally in your browser.</span></span>  <span data-ttu-id="0e8d0-125">Чтобы добавить новые элементы в список дел, нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-125">You can add new items to the to-do list by clicking **Create New**.</span></span>  <span data-ttu-id="0e8d0-126">Обратите внимание, что данные, которые вы вводите в приложение, хранятся в учетной записи Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-126">Note the data you enter in the application is being stored in your Azure Cosmos DB account.</span></span>  <span data-ttu-id="0e8d0-127">Просмотреть свои данные можно на [портале Azure](https://portal.azure.com). Для этого на портале в меню слева выберите Azure Cosmos DB, щелкните свою учетную запись и выберите пункт **Обозреватель данных**.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-127">You can view your data in the [Azure portal](https://portal.azure.com) by selecting Azure Cosmos DB from the left menu, selecting your account, and then selecting **Data Explorer**.</span></span>

## <a name="deploying-the-application-as-an-azure-web-app"></a><span data-ttu-id="0e8d0-128">Развертывание приложения как веб-приложения Azure</span><span class="sxs-lookup"><span data-stu-id="0e8d0-128">Deploying the application as an Azure Web App</span></span>

<span data-ttu-id="0e8d0-129">Вы успешно создали приложение, которое использует такие службы Azure, как Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-129">You've successfully built an application that uses Azure services like Azure Cosmos DB.</span></span>  <span data-ttu-id="0e8d0-130">Теперь вы развернете веб-приложение в облаке.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-130">Next, we'll deploy our web application to the cloud.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e8d0-131">Войдите в Visual Studio, используя учетную запись, с которой связана ваша подписка Azure.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-131">Be sure you're signed into Visual Studio with the same account your Azure subscription is associated with.</span></span>

1. <span data-ttu-id="0e8d0-132">В обозревателе решений Visual Studio щелкните правой кнопкой мыши имя проекта и выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-132">In Visual Studio Solution Explorer, right-click on the project name and select **Publish...**</span></span>

2. <span data-ttu-id="0e8d0-133">В диалоговом окне "Публикация" установите флажок **Служба приложений Microsoft Azure**, выберите **Создать** и нажмите кнопку **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-133">Using the Publish dialog, select **Microsoft Azure App Service**, select **Create New**, and then click **Publish**</span></span>

3. <span data-ttu-id="0e8d0-134">Заполните значения в диалоговом окне "Создание службы приложений":</span><span class="sxs-lookup"><span data-stu-id="0e8d0-134">Complete the Create App Service dialog as follows:</span></span>

    * <span data-ttu-id="0e8d0-135">Введите уникальное **имя веб-приложения**.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-135">Enter a unique **Web App Name**.</span></span>  <span data-ttu-id="0e8d0-136">Оно будет частью URL-адреса приложения.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-136">This will be part of the URL for your app.</span></span>
    * <span data-ttu-id="0e8d0-137">Выберите **подписку** Azure, в которую вы развертываете приложение.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-137">Select the Azure **Subscription** you're deploying to.</span></span>  <span data-ttu-id="0e8d0-138">Используйте ту же подписку, с помощью которой вы вошли в Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-138">Use same subscription with which you were logged into Cloud Shell earlier.</span></span>
    * <span data-ttu-id="0e8d0-139">Выберите имя *DotNetAzureTutorial* для **группы ресурсов** веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-139">Select *DotNetAzureTutorial* for the **Resource Group** for your web application.</span></span>
    * <span data-ttu-id="0e8d0-140">Выберите или создайте **план службы приложений**, чтобы определить цену приложения.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-140">Select or create an **App Service Plan** to determine the pricing your your application.</span></span>  <span data-ttu-id="0e8d0-141">Дополнительные сведения см. в статье [Подробный обзор планов службы приложений Azure](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="0e8d0-141">Here's [more information about App Service Plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

4. <span data-ttu-id="0e8d0-142">Нажмите кнопку **Создать**, чтобы развернуть приложение.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-142">Click **Create** to deploy the application.</span></span>  <span data-ttu-id="0e8d0-143">Когда развертывание завершится, браузер откроет развернутое приложение.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-143">When deployment is complete, a browser will open with your deployed application.</span></span>

![Готовое приложение](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="0e8d0-145">Очистка</span><span class="sxs-lookup"><span data-stu-id="0e8d0-145">Clean up</span></span>

<span data-ttu-id="0e8d0-146">Когда вы завершите тестировать приложение, а также проверять код и ресурсы, веб-приложение и учетную запись Azure Cosmos DB можно будет удалить. Для этого в Cloud Shell нужно удалить соответствующую группу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0e8d0-146">When you're done testing the app and inspecting the code and resources, you can delete the Web App and Azure Cosmos DB account by deleting the resource group in the Cloud Shell.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="0e8d0-147">Дополнительная информация</span><span class="sxs-lookup"><span data-stu-id="0e8d0-147">Next steps</span></span>

* [<span data-ttu-id="0e8d0-148">Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD</span><span class="sxs-lookup"><span data-stu-id="0e8d0-148">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="0e8d0-149">Создание веб-приложения ASP.NET в Azure</span><span class="sxs-lookup"><span data-stu-id="0e8d0-149">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="0e8d0-150">Примеры для службы хранилища Azure с использованием .NET</span><span class="sxs-lookup"><span data-stu-id="0e8d0-150">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


