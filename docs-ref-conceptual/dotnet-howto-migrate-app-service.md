---
title: Перенос веб-приложения ASP.NET в службу приложений Azure
description: Узнайте, как перенести веб-приложение ASP.NET из локальной среды в службу приложений Azure.
keywords: Azure .NET, ASP.NET, App Service, Web App, migrate, migration
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter
ms.openlocfilehash: 050782871c3fe4ccb0d15bf9933c3b11c88ce661
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="migrate-an-aspnet-web-application-to-azure-app-service"></a>Перенос веб-приложения ASP.NET в службу приложений Azure

[Служба приложений](https://docs.microsoft.com/azure/app-service/app-service-web-overview#why-use-web-apps) — это полностью управляемая вычислительная платформа, оптимизированная для размещения масштабируемых веб-сайтов и веб-приложений. В этом документе содержатся сведения о переносе существующего приложения в службу приложений Azure методом lift-and-shift, рекомендуемых изменениях и дополнительных ресурсах для перемещения в облако.

Готовы начать работу? [Опубликуйте свое приложение ASP.NET + SQL в службе приложений Azure](https://go.microsoft.com/fwlink/?linkid=863214).

# <a name="preparation"></a>Подготовка   
* [Как определить, соответствует ли ваше приложение требованиям службы приложений?](https://azure.microsoft.com/downloads/migration-assistant/)
* [Перенос базы данных в облако.](https://go.microsoft.com/fwlink/?linkid=863217)

# <a name="considerations"></a>Рекомендации
Существует несколько факторов, которые следует учесть перед переносом приложения. Ниже приводится список потенциальных изменений, которые может потребоваться внести в приложение, и объясняется, как это сделать.

## <a name="sql-database-configuration"></a>Конфигурация базы данных SQL
Для веб-приложения, в котором используется локальная база данных, есть несколько вариантов конфигурации. [Дополнительные сведения о переносе баз данных SQL в Azure](https://go.microsoft.com/fwlink/?linkid=863217).

## <a name="iis"></a>IIS
Теперь все параметры приложения, которые традиционно настраиваются с помощью файла applicationHost.config, можно настроить на портале Azure. Это касается разрядности пула приложений, включения и отключения протокола WebSocket, версии управляемого конвейера, версии платформы .NET Framework (2.0 или 4.0) и других параметров. Чтобы изменить [параметры приложения](https://docs.microsoft.com/azure/app-service/web-sites-configure), перейдите на [портал Azure](https://portal.azure.com), откройте колонку нужного веб-приложения и выберите вкладку **Параметры приложения**.

## <a name="authentication"></a>Authentication
Если в приложении настроена проверка подлинности пользователей в любой момент, необходимо внести изменения в эту функцию, чтобы она работала после развертывания в службе веб-приложений Azure. Это можно сделать, например, путем интеграции локальных каталогов с Azure Active Directory при помощи Azure AD Connect. [Подробнее об интеграции локальных каталогов с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

## <a name="virtual-network-modification"></a>Изменения в виртуальной сети
Если вы работаете с несколькими службами Azure, для безопасного взаимодействия между этими службами можно использовать виртуальную сеть. Подключение из локальной сети к [виртуальной сети Azure](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet) можно настроить с помощью VPN или ExpressRoute.

## <a name="monitoring-and-diagnostics"></a>Мониторинг и диагностика
Решения для мониторинга и диагностики, которые вы используете сейчас в локальной среде, вряд ли будут работать в облаке. Но Azure предоставляет средства для ведения журнала, мониторинга и диагностики, позволяющие определять и устранять проблемы, связанные с веб-приложениями. Диагностику веб-приложения можно без труда включить в его конфигурации, а записи журналов доступны для просмотра в Azure Application Insights. [Подробнее о включении ведения журнала диагностики для веб-приложений](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

## <a name="connection-strings-and-application-settings"></a>Строки подключения и параметры приложения
Один из вариантов безопасного хранения данных — [Azure KeyVault](https://docs.microsoft.com/azure/key-vault/), служба, в которой надежно хранятся конфиденциальные сведения, используемые в вашем приложении. Кроме того, эти данные можно хранить в настройках службы приложений.

## <a name="dns"></a>DNS
Возможно, вам понадобится обновить конфигурацию DNS в соответствии с требованиями приложения. Эти параметры DNS можно настроить в [параметрах личного домена](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain) службы приложений. Также можно [привязать существующий пользовательский SSL-сертификат](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl).

## <a name="file-system-and-storage"></a>Файловая система и хранилище
Если в вашем приложении сохраняются данные, необходимо настроить его так, чтобы вместо этого использовать хранилище Azure. Служба хранилища Azure предоставляет общие файловые ресурсы для совместного использования по протоколу SMB, хранилище BLOB-объектов, простые очереди и нереляционные таблицы. [Подробнее об общих файловых ресурсах службы хранилища Azure](https://docs.microsoft.com/azure/storage/files/storage-files-introduction).

## <a name="next-steps"></a>Дополнительная информация

> [!div class="nextstepaction"]
> [Перенос веб-приложения ASP.NET в службу приложений Azure](https://aka.ms/azure-webapp-migrate)
