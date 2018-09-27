---
title: Развертывание в Azure из Visual Studio
description: Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET.
ms.date: 06/20/2017
ms.openlocfilehash: a4ddaa0dbf1cd71a0de031cc89b299baa381992c
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190428"
---
# <a name="deploy-to-azure-from-visual-studio"></a><span data-ttu-id="14a8a-103">Развертывание в Azure из Visual Studio</span><span class="sxs-lookup"><span data-stu-id="14a8a-103">Deploy to Azure from Visual Studio</span></span>

<span data-ttu-id="14a8a-104">Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET.</span><span class="sxs-lookup"><span data-stu-id="14a8a-104">This tutorial will walk you through building and deploying a Microsoft Azure application using Visual Studio and .NET.</span></span>  <span data-ttu-id="14a8a-105">Вы создадите веб-приложение со списком дел на базе MVC ASP.NET Core, размещенное как веб-приложение Azure и использующее Azure Cosmos DB для хранения данных.</span><span class="sxs-lookup"><span data-stu-id="14a8a-105">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure Cosmos DB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14a8a-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="14a8a-106">Prerequisites</span></span>

* [<span data-ttu-id="14a8a-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="14a8a-107">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* <span data-ttu-id="14a8a-108">[Подписка Microsoft Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="14a8a-108">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>

## <a name="create-an-azure-cosmos-db-account"></a><span data-ttu-id="14a8a-109">создание учетной записи Azure Cosmos DB;</span><span class="sxs-lookup"><span data-stu-id="14a8a-109">Create an Azure Cosmos DB account</span></span>

<span data-ttu-id="14a8a-110">Azure Cosmos DB используется для хранения данных приложения, которое вы создадите в этом руководстве, поэтому вам необходимо создать учетную запись.</span><span class="sxs-lookup"><span data-stu-id="14a8a-110">Azure Cosmos DB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="14a8a-111">Запустите этот скрипт локально или в Cloud Shell, чтобы создать учетную запись API SQL для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="14a8a-111">Run this script locally or in the Cloud Shell to create an Azure Cosmos DB SQL API account.</span></span>  <span data-ttu-id="14a8a-112">Нажмите кнопку **Попробовать** на блоке кода ниже, чтобы запустить [Azure Cloud Shell](/azure/cloud-shell/). Затем скопируйте и вставьте блок скрипта в оболочку.</span><span class="sxs-lookup"><span data-stu-id="14a8a-112">Click the **Try it** button on the code block below to launch the [Azure Cloud Shell](/azure/cloud-shell/) and copy/paste the script block into the shell.</span></span>

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

<span data-ttu-id="14a8a-113">Запишите отображаемые значения **authKey** и **endpoint**.</span><span class="sxs-lookup"><span data-stu-id="14a8a-113">Make a note of the displayed **authKey** and **endpoint**</span></span> 

## <a name="downloading-and-running-the-application"></a><span data-ttu-id="14a8a-114">Загрузка и запуск приложения</span><span class="sxs-lookup"><span data-stu-id="14a8a-114">Downloading and running the application</span></span>

<span data-ttu-id="14a8a-115">Для этого руководства вам нужно получить пример кода и подключить его к учетной записи Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="14a8a-115">Let's get the sample code for this walkthrough and hook it up to your Azure Cosmos DB account.</span></span>

1. <span data-ttu-id="14a8a-116">Скачайте пример кода.</span><span class="sxs-lookup"><span data-stu-id="14a8a-116">Download the sample code.</span></span>  <span data-ttu-id="14a8a-117">Вы можете [получить его в GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) или, если у вас есть [клиент командной строки git](https://git-scm.com/), клонировать на локальный компьютер с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="14a8a-117">You can [get it from GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), or if you have the [git command line client](https://git-scm.com/), clone it to your local machine with the following command:</span></span>

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. <span data-ttu-id="14a8a-118">Откройте **todo.csproj** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14a8a-118">Open **todo.csproj** in Visual Studio.</span></span>

3. <span data-ttu-id="14a8a-119">Откройте **appsettings.json** в веб-проекте.</span><span class="sxs-lookup"><span data-stu-id="14a8a-119">Open **appsettings.json** in the web project.</span></span>  <span data-ttu-id="14a8a-120">Найдите эти строки:</span><span class="sxs-lookup"><span data-stu-id="14a8a-120">Look for the following lines:</span></span>

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    <span data-ttu-id="14a8a-121">Замените значения **AUTHKEYVALUE** и **ENDPOINTVALUE** записанными ранее значениями.</span><span class="sxs-lookup"><span data-stu-id="14a8a-121">Replace **AUTHKEYVALUE** and **ENDPOINTVALUE** with the values you noted earlier.</span></span>

4. <span data-ttu-id="14a8a-122">Нажмите клавишу **F5**, чтобы восстановить пакеты NuGet проекта, выполните сборку проекта и запустите его локально.</span><span class="sxs-lookup"><span data-stu-id="14a8a-122">Press **F5** to restore the project's NuGet packages, build the project, and run it locally.</span></span>

<span data-ttu-id="14a8a-123">Веб-приложение следует запускать локально в браузере.</span><span class="sxs-lookup"><span data-stu-id="14a8a-123">The web application should run locally in your browser.</span></span>  <span data-ttu-id="14a8a-124">Чтобы добавить новые элементы в список дел, нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="14a8a-124">You can add new items to the to-do list by clicking **Create New**.</span></span>  <span data-ttu-id="14a8a-125">Обратите внимание, что данные, которые вы вводите в приложение, хранятся в учетной записи Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="14a8a-125">Note the data you enter in the application is being stored in your Azure Cosmos DB account.</span></span>  <span data-ttu-id="14a8a-126">Просмотреть свои данные можно на [портале Azure](https://portal.azure.com). Для этого на портале в меню слева выберите Azure Cosmos DB, щелкните свою учетную запись и выберите пункт **Обозреватель данных**.</span><span class="sxs-lookup"><span data-stu-id="14a8a-126">You can view your data in the [Azure portal](https://portal.azure.com) by selecting Azure Cosmos DB from the left menu, selecting your account, and then selecting **Data Explorer**.</span></span>

## <a name="deploying-the-application-as-an-azure-web-app"></a><span data-ttu-id="14a8a-127">Развертывание приложения как веб-приложения Azure</span><span class="sxs-lookup"><span data-stu-id="14a8a-127">Deploying the application as an Azure Web App</span></span>

<span data-ttu-id="14a8a-128">Вы успешно создали приложение, которое использует такие службы Azure, как Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="14a8a-128">You've successfully built an application that uses Azure services like Azure Cosmos DB.</span></span>  <span data-ttu-id="14a8a-129">Теперь вы развернете веб-приложение в облаке.</span><span class="sxs-lookup"><span data-stu-id="14a8a-129">Next, we'll deploy our web application to the cloud.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14a8a-130">Войдите в Visual Studio, используя учетную запись, с которой связана ваша подписка Azure.</span><span class="sxs-lookup"><span data-stu-id="14a8a-130">Be sure you're signed into Visual Studio with the same account your Azure subscription is associated with.</span></span>

1. <span data-ttu-id="14a8a-131">В обозревателе решений Visual Studio щелкните правой кнопкой мыши имя проекта и выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="14a8a-131">In Visual Studio Solution Explorer, right-click on the project name and select **Publish...**</span></span>

2. <span data-ttu-id="14a8a-132">В диалоговом окне "Публикация" установите флажок **Служба приложений Microsoft Azure**, выберите **Создать** и нажмите кнопку **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="14a8a-132">Using the Publish dialog, select **Microsoft Azure App Service**, select **Create New**, and then click **Publish**</span></span>

3. <span data-ttu-id="14a8a-133">Заполните значения в диалоговом окне "Создание службы приложений":</span><span class="sxs-lookup"><span data-stu-id="14a8a-133">Complete the Create App Service dialog as follows:</span></span>

    * <span data-ttu-id="14a8a-134">Введите уникальное **имя веб-приложения**.</span><span class="sxs-lookup"><span data-stu-id="14a8a-134">Enter a unique **Web App Name**.</span></span>  <span data-ttu-id="14a8a-135">Оно будет частью URL-адреса приложения.</span><span class="sxs-lookup"><span data-stu-id="14a8a-135">This will be part of the URL for your app.</span></span>
    * <span data-ttu-id="14a8a-136">Выберите **подписку** Azure, в которую вы развертываете приложение.</span><span class="sxs-lookup"><span data-stu-id="14a8a-136">Select the Azure **Subscription** you're deploying to.</span></span>  <span data-ttu-id="14a8a-137">Используйте ту же подписку, с помощью которой вы вошли в Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="14a8a-137">Use same subscription with which you were logged into Cloud Shell earlier.</span></span>
    * <span data-ttu-id="14a8a-138">Выберите имя *DotNetAzureTutorial* для **группы ресурсов** веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="14a8a-138">Select *DotNetAzureTutorial* for the **Resource Group** for your web application.</span></span>
    * <span data-ttu-id="14a8a-139">Выберите или создайте **план службы приложений**, чтобы определить цену приложения.</span><span class="sxs-lookup"><span data-stu-id="14a8a-139">Select or create an **App Service Plan** to determine the pricing your your application.</span></span>  <span data-ttu-id="14a8a-140">Дополнительные сведения см. в статье [Подробный обзор планов службы приложений Azure](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="14a8a-140">Here's [more information about App Service Plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

4. <span data-ttu-id="14a8a-141">Нажмите кнопку **Создать**, чтобы развернуть приложение.</span><span class="sxs-lookup"><span data-stu-id="14a8a-141">Click **Create** to deploy the application.</span></span>  <span data-ttu-id="14a8a-142">Когда развертывание завершится, браузер откроет развернутое приложение.</span><span class="sxs-lookup"><span data-stu-id="14a8a-142">When deployment is complete, a browser will open with your deployed application.</span></span>

![Готовое приложение](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="14a8a-144">Очистка</span><span class="sxs-lookup"><span data-stu-id="14a8a-144">Clean up</span></span>

<span data-ttu-id="14a8a-145">Когда вы завершите тестировать приложение, а также проверять код и ресурсы, веб-приложение и учетную запись Azure Cosmos DB можно будет удалить. Для этого в Cloud Shell нужно удалить соответствующую группу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="14a8a-145">When you're done testing the app and inspecting the code and resources, you can delete the Web App and Azure Cosmos DB account by deleting the resource group in the Cloud Shell.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="14a8a-146">Дополнительная информация</span><span class="sxs-lookup"><span data-stu-id="14a8a-146">Next steps</span></span>

* [<span data-ttu-id="14a8a-147">Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD</span><span class="sxs-lookup"><span data-stu-id="14a8a-147">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="14a8a-148">Создание веб-приложения ASP.NET в Azure</span><span class="sxs-lookup"><span data-stu-id="14a8a-148">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="14a8a-149">Примеры для службы хранилища Azure с использованием .NET</span><span class="sxs-lookup"><span data-stu-id="14a8a-149">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


