---
title: "Выбор правильного размещения в Azure"
description: "Узнайте, какой способ переноса в Azure подходит для вашего веб-приложения ASP.NET."
keywords: Azure .NET, ASP.NET, App Service, VM, virtual machine, Web App, migrate, migration
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 01c321e164901253286add632f2301260245245b
ms.sourcegitcommit: c360a22d5bff6eedd714b28b847d2f26b06665f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2017
---
# <a name="choose-the-right-azure-hosting-option"></a>Выбор правильного размещения в Azure

В этом документе приводится ряд рекомендаций и сравнение вариантов, предлагаемых в Azure при переносе существующих приложений .NET Framework из локальной среды в Azure.

При переносе существующих приложений .NET Framework в Azure следует учитывать следующие важные аспекты:

1.  Варианты вычислительных сред.
2.  Варианты баз данных.
3.  Сетевые подключения и безопасность.
4.  Проверка подлинности и авторизация.

## <a name="compute-choices"></a>Варианты вычислительных сред

Для переноса существующих приложений .NET Framework в Azure существует несколько вариантов.  Но так как платформа .NET Framework работает только с ОС Windows, эти варианты ограничиваются службами вычислений на базе Windows.

В таблице ниже приводится несколько сравнений и рекомендаций, которые помогут вам выбрать правильную вычислительную среду при переносе существующего приложения .NET.

|                 | Виртуальные машины Azure | Служба приложений Azure | Контейнеры Windows |
|-----------------|-----------|-------------------|--------------------|
|Сценарии использования      |<ul><li>Приложение в значительной степени зависит от сервера и локально хранящихся MSI-файлов установки.</li><li>Вам нужен самый простой способ переноса приложения.</li></ul>|Приложение не зависит от сервера, это просто "чистое" веб-приложение ASP.NET (MVC, WebForm) или n-уровневое приложение (Web API, WCF) с доступом к серверу базы данных. |<ul><li>Приложение зависит от сервера-источника, но эти зависимости можно включить в образ Docker Windows.</li><li>Необходимо модернизировать приложение, чтобы подготовить его к процессам [DevOps в облаке](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-devops/reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications).</li></ul>|
|Преимущества  |<ul><li>Самый простой способ переноса.</li><li>Знакомая среда. В качестве среды развертывания используется виртуальная машина, которая очень похожа на локальные серверы.</li></ul> |Текущее обслуживание PaaS — простой способ масштабирования приложений и управления ими в Azure. |<ul><li>Подготовлены к новым возможностям и процессам DevOps в облаке с зависимостями, включенными в контейнеры приложений.</li><li>Практически нет необходимости в рефакторинге кода .NET или C#.</li></ul> |
|Недостатки             |Это инфраструктура как услуга (IaaS). Обслуживание обходится дорого. Вам придется управлять такими элементами инфраструктуры виртуальных машин, как сеть, подсистема балансировки нагрузки, горизонтальное масштабирование, службы IIS и т. д. |<ul><li>[Поддерживаются](http://www.migratetoazure.net/ReadinessAssessment) не все приложения.</li><li>Для некоторых приложений потребуется выполнить рефакторинг и даже незначительно изменить архитектуру, чтобы они поддерживали службу приложений Azure.</li></ul> |<ul><li>Потребуется освоить навыки работы с Docker.</li><li>Требуется изменить некоторые параметры конфигурации приложения и код.</li></ul>|
|Требования |Виртуальная машина Windows Server с такими же требованиями, как и для приложения в локальной среде. | Требования службы приложений Azure см. на странице [анализа совместимости для службы приложений Azure](https://www.migratetoazure.net/Resources). |<ul><li>[Windows Server 2016 с контейнерами — виртуальная машина Azure](https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.WindowsServer?tab=Overview)<br />или</li><li>[Служба контейнеров Azure (AKS)](https://azure.microsoft.com/services/container-service/) (то есть оркестратор Kubernetes)<br />или<li>оркестратор [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)</li></ul> |
|Как осуществить перенос |См. статью [Перенос веб-приложения ASP.NET на виртуальную машину Azure](https://go.microsoft.com/fwlink/?linkid=862531). | См. статью [Перенос веб-приложения ASP.NET в службу приложений Azure](https://go.microsoft.com/fwlink/?linkid=862532). | Следуйте рекомендациям, сценариям и пошаговым инструкциям, которые приводятся в электронной книге [Modernize existing .NET applications with Azure cloud and Windows Containers](https://aka.ms/liftandshiftwithcontainersebook) (Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows). |

 На следующей блок-схеме показано дерево принятия решений при планировании переноса существующих приложений .NET Framework в Azure. Вариант A — это первый вариант, который нужно опробовать и реализовать, если он подходит, а вариант B — это самый простой способ.

![Блок-схема, на которой показано дерево принятия решений по размещению](media/dotnet-howto-choose-migration/decision-tree.png)

## <a name="database-choices"></a>Варианты баз данных

Для переноса реляционных баз данных в Azure существует несколько вариантов. Чтобы выбрать правильный способ переноса для существующего приложения .NET, см. статью [Перенос базы данных SQL Server в Azure](https://go.microsoft.com/fwlink/?linkid=862533).

## <a name="networking-and-security-considerations"></a>Сетевые подключения и безопасность

При развертывании приложений в общедоступном облаке, таком как Microsoft Azure, может потребоваться изолировать и защитить некоторые сети. Для этого можно [создать сети периметра](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/), например [сеть периметра между Azure и локальным центром обработки данных](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) или [сеть периметра между Azure и Интернетом](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz). Вы можете реализовать сети периметра, используя [виртуальные сети Microsoft Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).
Виртуальные сети Azure позволяют выполнять следующие задачи:

- Создание управляемой гибридной инфраструктуры.
- Использование собственных IP-адресов и DNS-серверов.
- Обеспечение безопасности подключений с помощью VPN-соединения IPsec или ExpressRoute.
- Детальный контроль над трафиком между подсетями.
- Создание сложных сетевых топологий с виртуальными модулями.
- Создание изолированной и безопасной среды для ваших приложений.
 
Чтобы приступить к созданию собственной виртуальной сети, изучите [документацию по виртуальным сетям Azure](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Проверка подлинности и авторизация при переносе в Azure

Безопасность — самый важный вопрос для любой организации, которая переносит свои данные в облако. Большинство компаний потратили много времени, денег и усилий разработчиков на создание и разработку модели безопасности. Поэтому важно, чтобы компании могли использовать существующие ресурсы, например хранилища удостоверений и решения единого входа.

Большинство существующих корпоративных приложений .NET B2E, которые выполняются в локальной среде, используют Active Directory для проверки подлинности и управления удостоверениями.  Azure AD Connect позволяет интегрировать локальные каталоги с Azure Active Directory.  Чтобы приступить к работе, изучите статью [Интеграция локальных каталогов с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

При планировании дальнейших действий с Azure Active Directory ознакомьтесь со статьей [Определение требований к идентификации для решений гибридной идентификации](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs).

Другие варианты связаны с протоколами проверки подлинности [OAuth](https://en.wikipedia.org/wiki/OAuth) и [OpenID](https://en.wikipedia.org/wiki/OpenID), которые часто используются в клиентских приложениях.  Как правило, когда применяются автономные базы данных удостоверений, например базы данных SQL удостоверений ASP.NET с программой-оболочкой IdentityServer4, использующей OAuth, подключение к локальным базам данных или каталогам не требуется.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Перенос веб-приложения ASP.NET в службу приложений Azure](dotnet-howto-migrate-app-service.md)