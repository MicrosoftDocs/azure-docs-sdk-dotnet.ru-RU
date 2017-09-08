---
title: ".NET для разработчиков Azure"
description: ".NET для разработчиков Azure"
keywords: Azure .NET, SDK, Azure .NET API Reference, Azure .NET class library
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.assetid: 
ms.openlocfilehash: 1defed888972ae2f9d60d57bc34c518df9b5867c
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="get-started-with-net-for-azure-developers"></a>Руководство по началу работы .NET для разработчиков Azure

Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET.  Вы создадите веб-приложение со списком дел на базе MVC ASP.NET Core, размещенное как веб-приложение Azure и использующее Azure CosmosDB для хранения данных.

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2017](https://www.visualstudio.com/downloads/)
* [Подписка Microsoft Azure](https://azure.microsoft.com/free/).

## <a name="create-a-cosmosdb-account"></a>Создание учетной записи CosmosDB

CosmosDB используется для хранения данных приложения, которое вы создадите в этом руководстве, поэтому необходимо создать учетную запись.  Запустите этот скрипт локально или в Cloud Shell, чтобы создать учетную запись API Azure CosmosDB DocumentDB.  Нажмите кнопку **Попробовать** на блоке кода ниже, чтобы запустить [Azure Cloud Shell](/azure/cloud-shell/). Затем скопируйте и вставьте блок скрипта в оболочку.

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

Запишите отображаемые значения **authKey** и **endpoint**. 

## <a name="downloading-and-running-the-application"></a>Загрузка и запуск приложения

Вам нужно получить пример кода для этого пошагового руководства и подключить его к учетной записи CosmosDB.

1. Скачайте пример кода.  Вы можете [получить его в GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) или, если у вас есть [клиент командной строки git](https://git-scm.com/), клонировать на локальный компьютер с помощью следующей команды:

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. Откройте **todo.csproj** в Visual Studio.

3. Откройте **appsettings.json** в веб-проекте.  Найдите эти строки:

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    Замените значения **AUTHKEYVALUE** и **ENDPOINTVALUE** записанными ранее значениями.

4. Нажмите клавишу **F5**, чтобы восстановить пакеты NuGet проекта, выполните сборку проекта и запустите его локально.

Веб-приложение следует запускать локально в браузере.  Чтобы добавить новые элементы в список дел, нажмите кнопку **Создать**.  Обратите внимание, что данные, которые вы вводите в приложение, хранятся в учетной записи CosmosDB.  Вы можете [просмотреть данные на портале Azure](https://docs.microsoft.com/en-us/azure/documentdb/documentdb-view-json-document-explorer).

## <a name="deploying-the-application-as-an-azure-web-app"></a>Развертывание приложения как веб-приложения Azure

Вы создали приложение, которое использует такие службы Azure, как DocumentDB.  Теперь вы развернете веб-приложение в облаке.

> [!IMPORTANT]
> Войдите в Visual Studio, используя учетную запись, с которой связана ваша подписка Azure.

1. В обозревателе решений Visual Studio щелкните правой кнопкой мыши имя проекта и выберите **Опубликовать**.

2. В диалоговом окне "Публикация" установите флажок **Служба приложений Microsoft Azure**, выберите **Создать** и нажмите кнопку **Опубликовать**.

3. Заполните значения в диалоговом окне "Создание службы приложений":

    * Введите уникальное **имя веб-приложения**.  Оно будет частью URL-адреса приложения.
    * Выберите **подписку** Azure, в которую вы развертываете приложение.  Используйте ту же подписку, с помощью которой вы вошли в Cloud Shell.
    * Выберите имя *DotNetAzureTutorial* для **группы ресурсов** веб-приложения.
    * Выберите или создайте **план служб приложений**, чтобы определить цену приложения.  Дополнительные сведения см. в статье [Подробный обзор планов службы приложений Azure](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

4. Нажмите кнопку **Создать**, чтобы развернуть приложение.  Когда развертывание завершится, браузер откроет развернутое приложение.

![Готовое приложение](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a>Очистка

Когда вы завершите тестировать приложение, а также проверять код и ресурсы, можно удалить веб-приложение и учетную запись CosmosDB. Для этого удалите соответствующую группу ресурсов в Cloud Shell.

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a>Дальнейшие действия

* [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [Создание веб-приложения ASP.NET в Azure](/azure/app-service-web/web-sites-dotnet-get-started)
* [Примеры для службы хранилища Azure с использованием .NET](/azure/storage/storage-samples-dotnet)


