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
# <a name="deploy-to-azure-from-visual-studio"></a>Развертывание в Azure из Visual Studio

Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью Visual Studio и .NET.  Вы создадите веб-приложение со списком дел на базе MVC ASP.NET Core, размещенное как веб-приложение Azure и использующее Azure Cosmos DB для хранения данных.

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2017](https://www.visualstudio.com/downloads/)
* [Подписка Microsoft Azure](https://azure.microsoft.com/free/).

## <a name="create-an-azure-cosmos-db-account"></a>создание учетной записи Azure Cosmos DB;

Azure Cosmos DB используется для хранения данных приложения, которое вы создадите в этом руководстве, поэтому вам необходимо создать учетную запись.  Запустите этот скрипт локально или в Cloud Shell, чтобы создать учетную запись API SQL для Azure Cosmos DB.  Нажмите кнопку **Попробовать** на блоке кода ниже, чтобы запустить [Azure Cloud Shell](/azure/cloud-shell/). Затем скопируйте и вставьте блок скрипта в оболочку.

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

Запишите отображаемые значения **authKey** и **endpoint**. 

## <a name="downloading-and-running-the-application"></a>Загрузка и запуск приложения

Для этого руководства вам нужно получить пример кода и подключить его к учетной записи Azure Cosmos DB.

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

Веб-приложение следует запускать локально в браузере.  Чтобы добавить новые элементы в список дел, нажмите кнопку **Создать**.  Обратите внимание, что данные, которые вы вводите в приложение, хранятся в учетной записи Azure Cosmos DB.  Просмотреть свои данные можно на [портале Azure](https://portal.azure.com). Для этого на портале в меню слева выберите Azure Cosmos DB, щелкните свою учетную запись и выберите пункт **Обозреватель данных**.

## <a name="deploying-the-application-as-an-azure-web-app"></a>Развертывание приложения как веб-приложения Azure

Вы успешно создали приложение, которое использует такие службы Azure, как Azure Cosmos DB.  Теперь вы развернете веб-приложение в облаке.

> [!IMPORTANT]
> Войдите в Visual Studio, используя учетную запись, с которой связана ваша подписка Azure.

1. В обозревателе решений Visual Studio щелкните правой кнопкой мыши имя проекта и выберите **Опубликовать**.

2. В диалоговом окне "Публикация" установите флажок **Служба приложений Microsoft Azure**, выберите **Создать** и нажмите кнопку **Опубликовать**.

3. Заполните значения в диалоговом окне "Создание службы приложений":

    * Введите уникальное **имя веб-приложения**.  Оно будет частью URL-адреса приложения.
    * Выберите **подписку** Azure, в которую вы развертываете приложение.  Используйте ту же подписку, с помощью которой вы вошли в Cloud Shell.
    * Выберите имя *DotNetAzureTutorial* для **группы ресурсов** веб-приложения.
    * Выберите или создайте **план службы приложений**, чтобы определить цену приложения.  Дополнительные сведения см. в статье [Подробный обзор планов службы приложений Azure](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

4. Нажмите кнопку **Создать**, чтобы развернуть приложение.  Когда развертывание завершится, браузер откроет развернутое приложение.

![Готовое приложение](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a>Очистка

Когда вы завершите тестировать приложение, а также проверять код и ресурсы, веб-приложение и учетную запись Azure Cosmos DB можно будет удалить. Для этого в Cloud Shell нужно удалить соответствующую группу ресурсов.

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a>Дополнительная информация

* [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [Создание веб-приложения ASP.NET в Azure](/azure/app-service-web/web-sites-dotnet-get-started)
* [Примеры для службы хранилища Azure с использованием .NET](/azure/storage/storage-samples-dotnet)


