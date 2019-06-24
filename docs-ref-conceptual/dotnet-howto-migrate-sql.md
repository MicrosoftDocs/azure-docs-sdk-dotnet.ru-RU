---
title: Перенос базы данных SQL Server в Azure
description: Узнайте, как перенести базу данных SQL Server из локальной среды в Azure.
ms.date: 11/15/2017
ms.service: sql-database
ms.openlocfilehash: 49b03632b8ebe31439b3c39629fdaf751412fd5a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190517"
---
## <a name="migrate-a-sql-server-database-to-azure"></a>Перенос базы данных SQL Server в Azure

В этой статье предоставлен краткий обзор двух вариантов миграции базы данных SQL Server в Azure.

В Azure доступны два основных варианта переноса рабочей базы данных SQL Server:

1. [SQL Server на виртуальных машинах Azure.](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview) Экземпляр SQL Server, установленный и размещенный на виртуальной машине в Azure. Также называется "инфраструктура как услуга" (IaaS).
2. [База данных SQL Azure.](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) Полностью управляемая служба базы данных SQL в Azure. Также называется "платформа как услуга" (PaaS).

Оба варианта имеют свои преимущества и недостатки, которые вы должны оценить перед переносом.

## <a name="get-started"></a>Начало работы

В зависимости от службы, которую вы используете, вам пригодятся следующие руководства по миграции:

* [Миграция базы данных SQL Server в экземпляр SQL Server на виртуальной машине Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [Перенос базы данных SQL Server в базу данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Следующие статьи содержат основные принципы работы виртуальных машин:

* [Высокий уровень доступности и аварийное восстановление для SQL Server на виртуальных машинах Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Рекомендации по оптимизации производительности SQL Server на виртуальных машинах Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Шаблоны приложений и стратегии разработки для SQL Server на виртуальных машинах Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

Следующие статьи содержат дополнительные сведения о Базе данных SQL Azure.

* [Создание серверов базы данных SQL Azure и баз данных SQL Azure и управление ими](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [Единицы транзакций базы данных (DTU) и единицы транзакций эластичной базы данных (eDTU)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Ограничения ресурсов базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>Выбор IaaS или PaaS

Когда вы решаете, куда перенести базу данных, вам нужно выбрать между IaaS и PaaS.

**Выбирайте SQL Server на виртуальных машинах Azure при следующих условиях:**

* Вам нужен перенос базы данных и приложений по методике lift-and-shift с минимальными изменениями или без них.
* Вам нужен полный контроль над сервером базы данных и виртуальной машиной, на которой он работает.
* У вас есть лицензии SQL Server и Windows Server, которые вы собираетесь использовать.

**Выбирайте базу данных SQL Azure при следующих условиях:**

* Вы хотите модернизировать приложения и переносите базу данных, чтобы использовать другие службы PaaS в Azure.
* Вы не хотите управлять сервером базы данных и виртуальной машиной, на которой он работает.
* У вас нет лицензий SQL Server или Windows Server, или вы не собираетесь продлевать срок действия своих лицензий.

В следующей таблице описаны различия между службами на примере набора сценариев.

| Сценарий | SQL Server на виртуальных машинах Azure | Базы данных SQL Azure |
|----------|-------------------------|--------------------|
| Миграция | Требуются минимальные изменения в базе данных. | Могут потребоваться изменения в базе данных, если [помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595) определил, что вы используете недоступные в Azure SQL компоненты. Или при наличии других зависимостей, например локально установленных исполняемых файлов.|
| Управление доступностью, восстановлением и обновлениями | Доступность и восстановление настраиваются вручную. Обновления можно автоматизировать с помощью [масштабируемых наборов виртуальных машин](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade). | Автоматическое управление. |
| Конфигурация базовой операционной системы | Настройка вручную. | Автоматическое управление. |
| Управление размером базы данных | Поддерживает до 64 ТБ хранилища на экземпляр SQL Server. | Поддерживает 4 ТБ хранилища, прежде чем понадобится горизонтальное секционирование. |
| Управление затратами | Необходимо управлять затратами на лицензию SQL Server, лицензию Windows Server и виртуальную машину (с учетом ядер, ОЗУ и объема хранилища). | Необходимо управлять затратами на обслуживание (на основе [единиц eDTU или DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), объема хранилища и количества баз данных, если используется эластичный пул).  Необходимо контролировать стоимость всех соглашений об уровне обслуживания. |

Дополнительные сведения о различиях между двумя вариантами см. в статье о [выборе между Базой данных SQL Azure или SQL Server на виртуальных машинах Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).

## <a name="faq"></a>Часто задаваемые вопросы

* **Можно ли продолжать использовать SQL Server Management Studio и службы SQL Server Reporting Services (SSRS) с SQL Server на виртуальных машинах Azure или с Базой данных SQL Azure?**

    Да! Все средства Microsoft SQL работают с обеими службами. Но службы SSRS не являются частью Базы данных SQL Azure, поэтому рекомендуется запустить их на виртуальной машине Azure, а затем выбрать их в экземпляре базы данных.
    
* **Я хочу выбрать PaaS, но не знаю, совместима ли моя база данных с этим вариантом. Какие средства могут мне помочь?**

    Да. [Помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595) — средство, которое используется при переносе в Базу данных SQL Azure.  [Служба миграции базы данных Azure](https://azure.microsoft.com/campaigns/database-migration/) — это предварительная версия службы, которую можно использовать для IaaS или PaaS.

* **Можно ли оценить затраты?**

    Да.  [Калькулятор цен Azure](https://azure.microsoft.com/pricing/calculator/) поможет рассчитать стоимость всех служб Azure, в том числе виртуальных машин и служб баз данных.
    
## <a name="next-steps"></a>Дополнительная информация

> [!div class="nextstepaction"]
> [Выбор правильного размещения в Azure](dotnet-howto-choose-migration.md)
