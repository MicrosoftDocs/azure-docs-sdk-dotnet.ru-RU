---
title: Развертывание приложения в Azure из командной строки с помощью .NET Core
description: В этой статье описывается развертывание приложения ASP.NET Core в службе приложений Azure с помощью программы командной строки.
ms.date: 06/20/2017
ms.openlocfilehash: a29f5474dcfedc6f8d044f09ad4d54c5be6a371f
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190497"
---
# <a name="deploy-to-azure-from-the-command-line-with-net-core"></a>Развертывание приложения в Azure из командной строки с помощью .NET Core

Из этого руководства вы узнаете, как создать и развернуть приложение Microsoft Azure с помощью .NET Core.  Вы создадите веб-приложение со списком дел на базе MVC ASP.NET Core, размещенное как веб-приложение Azure и использующее Azure Cosmos DB для хранения данных.

## <a name="prerequisites"></a>Предварительные требования

* [Подписка Microsoft Azure](https://azure.microsoft.com/free/).
* [.NET Core](https://www.microsoft.com/net/download/core) (необязательно).
* [Azure CLI 2.0](/cli/azure/install-az-cli2) (необязательно).
* Клиент командной строки [Git](https://www.git-scm.com/) (необязательно).

В [Azure Cloud Shell](/azure/cloud-shell/) есть все необязательные компоненты, необходимые для этого руководства.  Вам нужно установить необязательные компоненты, только если вы собираетесь выполнять инструкции из руководства локально.  Для быстрого запуска Cloud Shell нажмите кнопку **Попробовать** в правом верхнем углу любого окна с блоком кода ниже.

## <a name="create-an-azure-cosmos-db-account"></a>создание учетной записи Azure Cosmos DB;

Azure Cosmos DB используется для хранения данных приложения, которое вы создадите в этом руководстве, поэтому вам необходимо создать учетную запись.  Запустите этот скрипт локально или в Cloud Shell, чтобы создать учетную запись API SQL для Azure Cosmos DB.

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

```

## <a name="download-and-configure-the-application"></a>Скачивание и настройка приложения

Приложение, которое вы собираетесь развернуть, — это [простое приложение со списком задач](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), написанное с использованием ASP.NET MVC Core и клиентских библиотек Azure Cosmos DB.  Вам нужно получить код для этого руководства и настроить его, используя свои данные Azure Cosmos DB.

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
> Если вы никогда не запускали `git commit` в этой среде, может появиться запрос на настройку удостоверения. Следуйте инструкциям на экране, а затем повторно запустите команду `git commit`.

Восстановите пакеты NuGet и выполните сборку приложения.

```azurecli-interactive
dotnet restore
dotnet build
```

> [!TIP]
> Если сборка приложения происходит на вашем компьютере, для проверки приложения выполните команду `dotnet run` и перейдите по адресу `localhost`, который отобразится.  В Cloud Shell невозможно открыть этот адрес.  

## <a name="configure-azure-app-service-and-deploy-the-web-app"></a>Настройка службы приложений Azure и развертывание веб-приложения

Вы выполнили скачивание и сборку веб-приложения. Теперь его можно развернуть как веб-приложение Azure.  Начните с создания ресурса веб-приложения.

```azurecli-interactive
# Generate a unique Web App name
let randomNum=$RANDOM*$RANDOM
webappname=todoApp$randomNum

# Create an App Service plan.
az appservice plan create --name $webappname --resource-group DotNetAzureTutorial --sku FREE

# Create the Web App
az webapp create --name $webappname --resource-group DotNetAzureTutorial --plan $webappname

```

Перед развертыванием необходимо настроить учетные данные развертывания в учетной записи.  Используйте приведенный ниже скрипт, указав собственные значения имени пользователя и пароля.

```azurecli-interactive
az webapp deployment user set --user-name <desired user name> --password <desired password>
```

Теперь разверните приложение в Azure.  Появится запрос на ввод ранее созданного пароля.

```azurecli-interactive
# Get the Git deployment URL
giturl=$(az webapp deployment source config-local-git -n $webappname -g DotNetAzureTutorial --query [url] -o tsv)

# Add the URL as a Git remote repository
git remote add azure $giturl

# Push the local repository to the remote
git push azure master
```

Приложение будет удаленно создано и развернуто.  Чтобы протестировать приложение, перейдите по адресу `https://<web app name>.azurewebsites.net`.  Чтобы отобразить адрес в консоли, выполните эту команду:

```azurecli-interactive
az webapp show -n $webappname -g DotNetAzureTutorial --query defaultHostName -o tsv
```

Чтобы добавить новые элементы в список дел, нажмите кнопку **Создать**.

![Готовое приложение](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a>Очистка

Когда вы завершите тестировать приложение, а также проверять код и ресурсы, веб-приложение и учетную запись Azure Cosmos DB можно будет удалить. Для этого нужно удалить соответствующую группу ресурсов.

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a>Дополнительная информация

* [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [Создание веб-приложения ASP.NET в Azure](/azure/app-service-web/web-sites-dotnet-get-started)
* [Примеры для службы хранилища Azure с использованием .NET](/azure/storage/storage-samples-dotnet)


