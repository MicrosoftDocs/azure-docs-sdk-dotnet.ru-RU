---
title: "Развертывание приложения в Azure из командной строки с помощью .NET Core"
description: "В этой статье описывается развертывание приложения ASP.NET Core в службе приложений Azure с помощью программы командной строки."
keywords: Azure .NET, SDK, Azure .NET API Reference, Azure .NET class library
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.openlocfilehash: bb5d4958fb4398192d8427391695da1a7b8cc3c8
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="deploy-to-azure-from-the-command-line-with-net-core"></a><span data-ttu-id="82f69-104">Развертывание приложения в Azure из командной строки с помощью .NET Core</span><span class="sxs-lookup"><span data-stu-id="82f69-104">Deploy to Azure from the command line with .NET Core</span></span>

<span data-ttu-id="82f69-105">Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью .NET Core.</span><span class="sxs-lookup"><span data-stu-id="82f69-105">This tutorial will walk you through building and deploying a Microsoft Azure application using .NET Core.</span></span>  <span data-ttu-id="82f69-106">Вы создадите веб-приложение со списком дел на базе MVC ASP.NET Core, размещенное как веб-приложение Azure и использующее Azure CosmosDB для хранения данных.</span><span class="sxs-lookup"><span data-stu-id="82f69-106">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure CosmosDB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82f69-107">предварительным требованиям</span><span class="sxs-lookup"><span data-stu-id="82f69-107">Prerequisites</span></span>

* <span data-ttu-id="82f69-108">[Подписка Microsoft Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="82f69-108">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>
* <span data-ttu-id="82f69-109">[.NET Core](https://www.microsoft.com/net/download/core) (необязательно).</span><span class="sxs-lookup"><span data-stu-id="82f69-109">[.NET Core](https://www.microsoft.com/net/download/core) (optional)</span></span>
* <span data-ttu-id="82f69-110">[Azure CLI 2.0](/cli/azure/install-az-cli2) (необязательно).</span><span class="sxs-lookup"><span data-stu-id="82f69-110">[Azure CLI 2.0](/cli/azure/install-az-cli2) (optional)</span></span>
* <span data-ttu-id="82f69-111">Клиент командной строки [Git](https://www.git-scm.com/) (необязательно).</span><span class="sxs-lookup"><span data-stu-id="82f69-111">[Git](https://www.git-scm.com/) command line client (optional)</span></span>

<span data-ttu-id="82f69-112">В [Azure Cloud Shell](/azure/cloud-shell/) есть все необязательные компоненты, необходимые для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="82f69-112">The [Azure Cloud Shell](/azure/cloud-shell/) has all of the optional prerequisites for this tutorial preinstalled.</span></span>  <span data-ttu-id="82f69-113">Вам нужно установить необязательные компоненты, только если вы собираетесь выполнять инструкции из руководства локально.</span><span class="sxs-lookup"><span data-stu-id="82f69-113">You only need to install the optional components above if you wish to run the tutorial locally.</span></span>  <span data-ttu-id="82f69-114">Для быстрого запуска Cloud Shell нажмите кнопку **Попробовать** в правом верхнем углу любого окна с блоком кода ниже.</span><span class="sxs-lookup"><span data-stu-id="82f69-114">To quickly launch the Cloud Shell, just click the **Try it** button in the top-right of any of the below code blocks.</span></span>

## <a name="create-a-cosmosdb-account"></a><span data-ttu-id="82f69-115">Создание учетной записи CosmosDB</span><span class="sxs-lookup"><span data-stu-id="82f69-115">Create a CosmosDB account</span></span>

<span data-ttu-id="82f69-116">CosmosDB используется для хранения данных приложения, которое вы создадите в этом руководстве, поэтому необходимо создать учетную запись.</span><span class="sxs-lookup"><span data-stu-id="82f69-116">CosmosDB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="82f69-117">Запустите этот скрипт локально или в Cloud Shell, чтобы создать учетную запись API Azure CosmosDB DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="82f69-117">Run this script locally or in the Cloud Shell to create an Azure CosmosDB DocumentDB API account.</span></span>

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

```

## <a name="download-and-configure-the-application"></a><span data-ttu-id="82f69-118">Скачивание и настройка приложения</span><span class="sxs-lookup"><span data-stu-id="82f69-118">Download and configure the application</span></span>

<span data-ttu-id="82f69-119">Приложение, которые вы собираетесь развернуть, это [простое приложение со списком задач](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), написанное с использованием ASP.NET MVC Core и клиентских библиотек CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="82f69-119">The application you're going to deploy is a [simple to-do app](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) written using ASP.NET MVC Core using the CosmosDB client libraries.</span></span>  <span data-ttu-id="82f69-120">Вам нужно получить код для этого руководства и настроить его, используя свои данные CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="82f69-120">Now you'll get the code for this tutorial and configure it with your CosmosDB information.</span></span>

```azurecli-interactive
# Get the code from GitHub
git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart

# Change the working directory
cd dotnet-cosmosdb-quickstart

# Replace authKey and endpoint values in appsettings.json
sed -i "s|AUTHKEYVALUE|$cosmosAuthKey|g" appsettings.json
sed -i "s|ENDPOINTVALUE|$cosmosEndpoint|g" appsettings.json

# Now commit your changes to the local Git repository.
git commit -a -m "Modified settings"

```

> [!NOTE]
> <span data-ttu-id="82f69-121">Если вы никогда не запускали `git commit` в этой среде, может появиться запрос на настройку удостоверения.</span><span class="sxs-lookup"><span data-stu-id="82f69-121">If you've never run `git commit` in this environment before, you may be prompted to set your identity.</span></span> <span data-ttu-id="82f69-122">Следуйте инструкциям на экране, а затем повторно запустите команду `git commit`.</span><span class="sxs-lookup"><span data-stu-id="82f69-122">Follow the on-screen instructions and then re-run the `git commit` command.</span></span>

<span data-ttu-id="82f69-123">Восстановите пакеты NuGet и выполните сборку приложения.</span><span class="sxs-lookup"><span data-stu-id="82f69-123">Restore the NuGet packages and build the application.</span></span>

```azurecli-interactive
dotnet restore
dotnet build
```

> [!TIP]
> <span data-ttu-id="82f69-124">Если сборка приложения происходит на вашем компьютере, для проверки приложения выполните команду `dotnet run` и перейдите по адресу `localhost`, который отобразится.</span><span class="sxs-lookup"><span data-stu-id="82f69-124">If you are using the tools on your own machine, you can test the application by running `dotnet run` and browsing to the displayed `localhost` address.</span></span>  <span data-ttu-id="82f69-125">В Cloud Shell невозможно открыть этот адрес.</span><span class="sxs-lookup"><span data-stu-id="82f69-125">You are not able to browse to this address in the Cloud Shell, however.</span></span>  

## <a name="configure-azure-app-service-and-deploy-the-web-app"></a><span data-ttu-id="82f69-126">Настройка службы приложений Azure и развертывание веб-приложения</span><span class="sxs-lookup"><span data-stu-id="82f69-126">Configure Azure App Service and deploy the web app</span></span>

<span data-ttu-id="82f69-127">Вы выполнили скачивание и сборку веб-приложения. Теперь его можно развернуть как веб-приложение Azure.</span><span class="sxs-lookup"><span data-stu-id="82f69-127">You've successfully downloaded and built the web application, and you're ready to deploy it as an Azure Web App.</span></span>  <span data-ttu-id="82f69-128">Начните с создания ресурса веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="82f69-128">You'll start by creating the Web App resource.</span></span>

```azurecli-interactive
# Generate a unique Web App name
let randomNum=$RANDOM*$RANDOM
webappname=todoApp$randomNum

# Create an App Service plan.
az appservice plan create --name $webappname --resource-group DotNetAzureTutorial --sku FREE

# Create the Web App
az webapp create --name $webappname --resource-group DotNetAzureTutorial --plan $webappname

```

<span data-ttu-id="82f69-129">Перед развертыванием необходимо настроить учетные данные развертывания в учетной записи.</span><span class="sxs-lookup"><span data-stu-id="82f69-129">Before you deploy, you need to set the account-level deployment credentials.</span></span>  <span data-ttu-id="82f69-130">Используйте приведенный ниже скрипт, указав собственные значения имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="82f69-130">Use the script below, making sure to include your own values for the user name and password.</span></span>

```azurecli-interactive
az webapp deployment user set --user-name <desired user name> --password <desired password>
```

<span data-ttu-id="82f69-131">Теперь разверните приложение в Azure.</span><span class="sxs-lookup"><span data-stu-id="82f69-131">Finally, deploy the application to Azure.</span></span>  <span data-ttu-id="82f69-132">Появится запрос на ввод ранее созданного пароля.</span><span class="sxs-lookup"><span data-stu-id="82f69-132">You will be prompted for the password you created above.</span></span>

```azurecli-interactive
# Get the Git deployment URL
giturl=$(az webapp deployment source config-local-git -n $webappname -g DotNetAzureTutorial --query [url] -o tsv)

# Add the URL as a Git remote repository
git remote add azure $giturl

# Push the local repository to the remote
git push azure master
```

<span data-ttu-id="82f69-133">Приложение будет удаленно создано и развернуто.</span><span class="sxs-lookup"><span data-stu-id="82f69-133">The application will be built remotely and deployed.</span></span>  <span data-ttu-id="82f69-134">Чтобы протестировать приложение, перейдите по адресу `https://<web app name>.azurewebsites.net`.</span><span class="sxs-lookup"><span data-stu-id="82f69-134">Test the application by browsing to `https://<web app name>.azurewebsites.net`.</span></span>  <span data-ttu-id="82f69-135">Чтобы отобразить адрес в консоли, выполните эту команду:</span><span class="sxs-lookup"><span data-stu-id="82f69-135">To display the address in the console, use the following:</span></span>

```azurecli-interactive
az webapp show -n $webappname -g DotNetAzureTutorial --query defaultHostName -o tsv
```

<span data-ttu-id="82f69-136">Чтобы добавить новые элементы в список дел, нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="82f69-136">You can add new items to the to-do list by clicking **Create New**.</span></span>

![Готовое приложение](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="82f69-138">Очистка</span><span class="sxs-lookup"><span data-stu-id="82f69-138">Clean up</span></span>

<span data-ttu-id="82f69-139">Когда вы завершите тестировать приложение, а также проверять код и ресурсы, можно удалить веб-приложение и учетную запись CosmosDB. Для этого удалите соответствующую группу ресурсов</span><span class="sxs-lookup"><span data-stu-id="82f69-139">When you're done testing the app and inspecting the code and resources, you can delete the Web App and CosmosDB account by deleting the resource group.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="82f69-140">Дополнительная информация</span><span class="sxs-lookup"><span data-stu-id="82f69-140">Next steps</span></span>

* [<span data-ttu-id="82f69-141">Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD</span><span class="sxs-lookup"><span data-stu-id="82f69-141">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="82f69-142">Создание веб-приложения ASP.NET в Azure</span><span class="sxs-lookup"><span data-stu-id="82f69-142">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="82f69-143">Примеры для службы хранилища Azure с использованием .NET</span><span class="sxs-lookup"><span data-stu-id="82f69-143">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


