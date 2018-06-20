---
title: Перенос веб-приложения ASP.NET на виртуальную машину Azure
description: Узнайте, как перенести веб-приложение ASP.NET из локальной среды на виртуальную машину Azure.
keywords: Azure .NET, ASP.NET, VM, virtual machine, migrate, migration
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
layout: LandingPage
ms.topic: landing-page
ms.technology: azure
ms.devlang: dotnet
ms.service: virtual-machines
ms.custom: devcenter
ms.openlocfilehash: 98f24553961793623f8a6aba10dcf45b930101fe
ms.sourcegitcommit: 3e904e6e4f04f1c92d729459434c85faff32e386
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2017
ms.locfileid: "26588487"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Перенос веб-приложения ASP.NET на виртуальную машину Azure

В этом документе приводятся общие сведения о том, как перенести веб-приложение ASP.NET из локальной среды на виртуальную машину Azure.

## <a name="quickstart"></a>Быстрый запуск

Узнайте, как создать виртуальную машину и опубликовать на ней приложение:

<div class="ico48Case">
    <div class="ico48Link">
        <a href="https://tutorials.visualstudio.com/aspnet-vm/intro">
            <img width="48" height="48" alt="Publish to an Azure VM" src="https://docs.microsoft.com/azure/media/index/virtualmachine.svg">
            <span>Публикация на виртуальной машине Azure</span>
        </a>
    </div>
</div>

## <a name="get-started"></a>Начало работы

В этих руководствах показано, как создать (перенести) виртуальную машину и опубликовать на ней веб-приложение, а также как выполнить другие задачи, которые могут потребоваться для поддержки приложения в Azure.

- Создайте виртуальную машину в Azure для приложения ASP.NET, используя один из следующих двух вариантов:
    - [Создание виртуальной машины для приложений ASP.NET](https://go.microsoft.com/fwlink/?linkid=863237).
    - [Перенос существующей локальной виртуальной машины](https://docs.microsoft.com/azure/site-recovery/tutorial-migrate-on-premises-to-azure).
- [Опубликуйте свое приложение с помощью Visual Studio](https://go.microsoft.com/fwlink/?linkid=863240).
- [Создайте защищенную виртуальную сеть для виртуальных машин](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet).
- [Создайте конвейер непрерывной интеграции или непрерывного развертывания для приложения](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups).
- [Перенесите приложение в масштабируемый набор виртуальных машин, чтобы обеспечить высокий уровень доступности и масштабируемость](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).

## <a name="considerations"></a>Рекомендации

### <a name="benefits"></a>Преимущества

Виртуальные машины предоставляют самый простой способ переноса приложения из локальной среды в облако.  Они позволяют реплицировать ту среду, которую приложение использует локально, устраняя необходимость в обслуживании собственных центров обработки данных.  Масштабируемые наборы виртуальных машин обеспечивают высокий уровень доступности и масштабируемость для приложений, выполняемых на виртуальных машинах.

### <a name="virtual-machine-size"></a>Размер виртуальной машины

Выберите размер и тип виртуальной машины, которые лучше всего оптимизированы для вашей рабочей нагрузки.  Дополнительные сведения см. в статье [Размеры виртуальных машин Windows в Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).

### <a name="maintenance"></a>Обслуживание, 

Как и в случае с локальными компьютерами, вы несете ответственность за обслуживание и обновление виртуальной машины <sup>&#42;</sup>.  Если приложение может выполняться в среде PaaS (платформа как услуга), например в [службе приложений Azure](https://docs.microsoft.com/azure/app-service/) или в [контейнере](https://docs.microsoft.com/azure/app-service/containers/), то необходимость в обслуживании устраняется.

*<sup>&#42;</sup>[Автоматическое обновление ОС для масштабируемых наборов виртуальных машин](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) сейчас доступно в виде службы в предварительной версии.*

### <a name="virtual-networks"></a>Виртуальные сети

Виртуальные сети Azure позволяют выполнять следующие задачи:
- Создание управляемой гибридной инфраструктуры.
- Использование собственных IP-адресов и DNS-серверов.
- Создание изолированной и надежно защищенной среды для ваших приложений.
- Подключение виртуальной машины к локальной сети с использованием одного из нескольких [вариантов подключения](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti).
- Интеграция виртуальной машины с локальной сетью с помощью [ExpressRoute](https://azure.microsoft.com/services/expressroute/).

Чтобы начать работу, ознакомьтесь с [документацией по виртуальным сетям](https://docs.microsoft.com/azure/virtual-network/).

### <a name="active-directory"></a>Active Directory
Многие приложения используют Active Directory для проверки подлинности и управления удостоверениями.  
- Azure AD Connect позволяет интегрировать локальные каталоги с Azure Active Directory.  Чтобы приступить к работе, изучите статью [Интеграция локальных каталогов с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).  
- Также и [ExpressRoute](https://azure.microsoft.com/services/expressroute/) позволяет приложению получить доступ к локальной службе Active Directory.

### <a name="sql-databases"></a>Базы данных SQL

Если приложение использует локальную базу данных, оно не сможет обращаться к ней по умолчанию. Вы можете выбрать один из таких вариантов:
- Настройте гибридную сеть, которая позволит вашему приложению получать доступ к базе данных, работающей локально.  
- Перенесите базу данных в Azure.  Дополнительные сведения см. в статье [Перенос базы данных SQL Server в Azure](dotnet-howto-migrate-sql.md).

### <a name="high-availability-and-scalability"></a>Высокий уровень доступности и масштабируемости

#### <a name="virtual-machine-scale-sets"></a>Наборы для масштабирования виртуальных машин
Если вам нужно обеспечить высокий уровень доступности и возможность масштабирования для приложения, перенесите образ виртуальной машины в масштабируемый набор виртуальных машин Azure, чтобы повысить уровень доступности и улучшить возможность масштабирования приложения.  Масштабируемые наборы виртуальных машин позволяют использовать уже настроенную виртуальную машину или настроить конвейер сборки, чтобы создать образ с вашим приложением.  

Чтобы приступить к работе, изучите статью [Развертывание приложения в масштабируемых наборах виртуальных машин](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).

#### <a name="centralized-logging"></a>Централизованное ведение журналов
Если приложение выполняется на нескольких экземплярах, рассмотрите возможность хранения журналов в централизованном расположении, например в [хранилище Azure](https://docs.microsoft.com/azure/storage/).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Перенос базы данных SQL Server в Azure](dotnet-howto-migrate-sql.md)