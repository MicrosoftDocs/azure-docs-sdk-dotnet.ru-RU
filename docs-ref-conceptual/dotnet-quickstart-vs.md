---
title: "Развертывание в Azure из Visual Studio"
description: "Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET."
keywords: Azure .NET, SDK, Azure .NET API Reference, Azure .NET class library
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.openlocfilehash: d5c34dfc7e649e00e8ef458537f3f76410db61d4
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="deploy-to-azure-from-visual-studio"></a><span data-ttu-id="24422-104">Развертывание в Azure из Visual Studio</span><span class="sxs-lookup"><span data-stu-id="24422-104">Deploy to Azure from Visual Studio</span></span>

<span data-ttu-id="24422-105">Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET.</span><span class="sxs-lookup"><span data-stu-id="24422-105">This tutorial will walk you through building and deploying a Microsoft Azure application using Visual Studio and .NET.</span></span>  <span data-ttu-id="24422-106">Вы создадите веб-приложение со списком дел на базе MVC ASP.NET Core, размещенное как веб-приложение Azure и использующее Azure CosmosDB для хранения данных.</span><span class="sxs-lookup"><span data-stu-id="24422-106">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure CosmosDB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24422-107">предварительным требованиям</span><span class="sxs-lookup"><span data-stu-id="24422-107">Prerequisites</span></span>

* [<span data-ttu-id="24422-108">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="24422-108">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* <span data-ttu-id="24422-109">[Подписка Microsoft Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="24422-109">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>

## <a name="create-a-cosmosdb-account"></a><span data-ttu-id="24422-110">Создание учетной записи CosmosDB</span><span class="sxs-lookup"><span data-stu-id="24422-110">Create a CosmosDB account</span></span>

<span data-ttu-id="24422-111">CosmosDB используется для хранения данных приложения, которое вы создадите в этом руководстве, поэтому необходимо создать учетную запись.</span><span class="sxs-lookup"><span data-stu-id="24422-111">CosmosDB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="24422-112">Запустите этот скрипт локально или в Cloud Shell, чтобы создать учетную запись API Azure CosmosDB DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="24422-112">Run this script locally or in the Cloud Shell to create an Azure CosmosDB DocumentDB API account.</span></span>  <span data-ttu-id="24422-113">Нажмите кнопку **Попробовать** на блоке кода ниже, чтобы запустить [Azure Cloud Shell](/azure/cloud-shell/). Затем скопируйте и вставьте блок скрипта в оболочку.</span><span class="sxs-lookup"><span data-stu-id="24422-113">Click the **Try it** button on the code block below to launch the [Azure Cloud Shell](/azure/cloud-shell/) and copy/paste the script block into the shell.</span></span>

```azurecli-interactive
# Create the DotNetAzureTutorial resource group
az group create --name DotNetAzureTutorial --location EastUS

# Generate a unique name for the account
let randomNum=$RANDOM*$RANDOM
cosmosdbname=dotnettutorial$randomNum

# Create the CosmosDB account
az cosmosdb create --name $cosmosdbname --resource-group DotNetAzureTutorial

# Retrieve the endpoint and key (you'll need these later)
cosmosEndpoint=$(az cosmosdb show -n $cosmosdbname -g DotNetAzureTutorial --query [documentEndpoint] -o tsv)
cosmosAuthKey=$(az cosmosdb list-keys -n $cosmosdbname -g DotNetAzureTutorial --query [primaryMasterKey] -o tsv)
printf "\n\nauthKey: $cosmosAuthKey\nendpoint: $cosmosEndpoint\n\n"

# Done!

```

<span data-ttu-id="24422-114">Запишите отображаемые значения **authKey** и **endpoint**.</span><span class="sxs-lookup"><span data-stu-id="24422-114">Make a note of the displayed **authKey** and **endpoint**</span></span> 

## <a name="downloading-and-running-the-application"></a><span data-ttu-id="24422-115">Загрузка и запуск приложения</span><span class="sxs-lookup"><span data-stu-id="24422-115">Downloading and running the application</span></span>

<span data-ttu-id="24422-116">Вам нужно получить пример кода для этого пошагового руководства и подключить его к учетной записи CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="24422-116">Let's get the sample code for this walkthrough and hook it up to your CosmosDB account.</span></span>

1. <span data-ttu-id="24422-117">Скачайте пример кода.</span><span class="sxs-lookup"><span data-stu-id="24422-117">Download the sample code.</span></span>  <span data-ttu-id="24422-118">Вы можете [получить его в GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) или, если у вас есть [клиент командной строки git](https://git-scm.com/), клонировать на локальный компьютер с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="24422-118">You can [get it from GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), or if you have the [git command line client](https://git-scm.com/), clone it to your local machine with the following command:</span></span>

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. <span data-ttu-id="24422-119">Откройте **todo.csproj** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="24422-119">Open **todo.csproj** in Visual Studio.</span></span>

3. <span data-ttu-id="24422-120">Откройте **appsettings.json** в веб-проекте.</span><span class="sxs-lookup"><span data-stu-id="24422-120">Open **appsettings.json** in the web project.</span></span>  <span data-ttu-id="24422-121">Найдите эти строки:</span><span class="sxs-lookup"><span data-stu-id="24422-121">Look for the following lines:</span></span>

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    <span data-ttu-id="24422-122">Замените значения **AUTHKEYVALUE** и **ENDPOINTVALUE** записанными ранее значениями.</span><span class="sxs-lookup"><span data-stu-id="24422-122">Replace **AUTHKEYVALUE** and **ENDPOINTVALUE** with the values you noted earlier.</span></span>

4. <span data-ttu-id="24422-123">Нажмите клавишу **F5**, чтобы восстановить пакеты NuGet проекта, выполните сборку проекта и запустите его локально.</span><span class="sxs-lookup"><span data-stu-id="24422-123">Press **F5** to restore the project's NuGet packages, build the project, and run it locally.</span></span>

<span data-ttu-id="24422-124">Веб-приложение следует запускать локально в браузере.</span><span class="sxs-lookup"><span data-stu-id="24422-124">The web application should run locally in your browser.</span></span>  <span data-ttu-id="24422-125">Чтобы добавить новые элементы в список дел, нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="24422-125">You can add new items to the to-do list by clicking **Create New**.</span></span>  <span data-ttu-id="24422-126">Обратите внимание, что данные, которые вы вводите в приложение, хранятся в учетной записи CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="24422-126">Note the data you enter in the application is being stored in your CosmosDB account.</span></span>  <span data-ttu-id="24422-127">Вы можете [просмотреть данные на портале Azure](/azure/documentdb/documentdb-view-json-document-explorer).</span><span class="sxs-lookup"><span data-stu-id="24422-127">You can [view your data in the Azure portal](/azure/documentdb/documentdb-view-json-document-explorer).</span></span>

## <a name="deploying-the-application-as-an-azure-web-app"></a><span data-ttu-id="24422-128">Развертывание приложения как веб-приложения Azure</span><span class="sxs-lookup"><span data-stu-id="24422-128">Deploying the application as an Azure Web App</span></span>

<span data-ttu-id="24422-129">Вы создали приложение, которое использует такие службы Azure, как DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="24422-129">You've successfully built an application that uses Azure services like DocumentDB.</span></span>  <span data-ttu-id="24422-130">Теперь вы развернете веб-приложение в облаке.</span><span class="sxs-lookup"><span data-stu-id="24422-130">Next, we'll deploy our web application to the cloud.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24422-131">Войдите в Visual Studio, используя учетную запись, с которой связана ваша подписка Azure.</span><span class="sxs-lookup"><span data-stu-id="24422-131">Be sure you're signed into Visual Studio with the same account your Azure subscription is associated with.</span></span>

1. <span data-ttu-id="24422-132">В обозревателе решений Visual Studio щелкните правой кнопкой мыши имя проекта и выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="24422-132">In Visual Studio Solution Explorer, right-click on the project name and select **Publish...**</span></span>

2. <span data-ttu-id="24422-133">В диалоговом окне "Публикация" установите флажок **Служба приложений Microsoft Azure**, выберите **Создать** и нажмите кнопку **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="24422-133">Using the Publish dialog, select **Microsoft Azure App Service**, select **Create New**, and then click **Publish**</span></span>

3. <span data-ttu-id="24422-134">Заполните значения в диалоговом окне "Создание службы приложений":</span><span class="sxs-lookup"><span data-stu-id="24422-134">Complete the Create App Service dialog as follows:</span></span>

    * <span data-ttu-id="24422-135">Введите уникальное **имя веб-приложения**.</span><span class="sxs-lookup"><span data-stu-id="24422-135">Enter a unique **Web App Name**.</span></span>  <span data-ttu-id="24422-136">Оно будет частью URL-адреса приложения.</span><span class="sxs-lookup"><span data-stu-id="24422-136">This will be part of the URL for your app.</span></span>
    * <span data-ttu-id="24422-137">Выберите **подписку** Azure, в которую вы развертываете приложение.</span><span class="sxs-lookup"><span data-stu-id="24422-137">Select the Azure **Subscription** you're deploying to.</span></span>  <span data-ttu-id="24422-138">Используйте ту же подписку, с помощью которой вы вошли в Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="24422-138">Use same subscription with which you were logged into Cloud Shell earlier.</span></span>
    * <span data-ttu-id="24422-139">Выберите имя *DotNetAzureTutorial* для **группы ресурсов** веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="24422-139">Select *DotNetAzureTutorial* for the **Resource Group** for your web application.</span></span>
    * <span data-ttu-id="24422-140">Выберите или создайте **план службы приложений**, чтобы определить цену приложения.</span><span class="sxs-lookup"><span data-stu-id="24422-140">Select or create an **App Service Plan** to determine the pricing your your application.</span></span>  <span data-ttu-id="24422-141">Дополнительные сведения см. в статье [Подробный обзор планов службы приложений Azure](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="24422-141">Here's [more information about App Service Plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

4. <span data-ttu-id="24422-142">Нажмите кнопку **Создать**, чтобы развернуть приложение.</span><span class="sxs-lookup"><span data-stu-id="24422-142">Click **Create** to deploy the application.</span></span>  <span data-ttu-id="24422-143">Когда развертывание завершится, браузер откроет развернутое приложение.</span><span class="sxs-lookup"><span data-stu-id="24422-143">When deployment is complete, a browser will open with your deployed application.</span></span>

![Готовое приложение](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="24422-145">Очистка</span><span class="sxs-lookup"><span data-stu-id="24422-145">Clean up</span></span>

<span data-ttu-id="24422-146">Когда вы завершите тестировать приложение, а также проверять код и ресурсы, можно удалить веб-приложение и учетную запись CosmosDB. Для этого удалите соответствующую группу ресурсов</span><span class="sxs-lookup"><span data-stu-id="24422-146">When you're done testing the app and inspecting the code and resources, you can delete the Web App and CosmosDB account by deleting the resource group.</span></span> <span data-ttu-id="24422-147">в Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="24422-147">in the Cloud Shell.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="24422-148">Дополнительная информация</span><span class="sxs-lookup"><span data-stu-id="24422-148">Next steps</span></span>

* [<span data-ttu-id="24422-149">Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD</span><span class="sxs-lookup"><span data-stu-id="24422-149">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="24422-150">Создание веб-приложения ASP.NET в Azure</span><span class="sxs-lookup"><span data-stu-id="24422-150">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="24422-151">Примеры для службы хранилища Azure с использованием .NET</span><span class="sxs-lookup"><span data-stu-id="24422-151">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


