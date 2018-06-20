---
title: Перенос базы данных SQL Server в Azure
description: Узнайте, как перенести базу данных SQL Server из локальной среды в Azure.
keywords: Azure .NET, ASP.NET, SQL, SQL Server, SQL Database, migrate, migration
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: sql-database
ms.custom: devcenter
ms.openlocfilehash: d118d39e2168686c851f0daa6cb611f0a0c9d2fc
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
ms.locfileid: "29728495"
---
## <a name="migrate-a-sql-server-database-to-azure"></a><span data-ttu-id="0da50-104">Перенос базы данных SQL Server в Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-104">Migrate a SQL Server database to Azure</span></span>

<span data-ttu-id="0da50-105">В этой статье предоставлен краткий обзор двух вариантов миграции базы данных SQL Server в Azure.</span><span class="sxs-lookup"><span data-stu-id="0da50-105">This short article provides a brief outline of two options for migrating a SQL Server database to Azure.</span></span>

<span data-ttu-id="0da50-106">В Azure доступны два основных варианта переноса рабочей базы данных SQL Server:</span><span class="sxs-lookup"><span data-stu-id="0da50-106">Azure has two primary options for migrating a production SQL Server database:</span></span>

1. <span data-ttu-id="0da50-107">[SQL Server на виртуальных машинах Azure.](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview) Экземпляр SQL Server, установленный и размещенный на виртуальной машине в Azure. Также называется "инфраструктура как услуга" (IaaS).</span><span class="sxs-lookup"><span data-stu-id="0da50-107">[SQL Server on Azure VMs](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): A SQL Server instance installed and hosted on a Windows Virtual Machine running in Azure, also known as Infrastructure as a Service (IaaS).</span></span>
2. <span data-ttu-id="0da50-108">[База данных SQL Azure.](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) Полностью управляемая служба базы данных SQL в Azure. Также называется "платформа как услуга" (PaaS).</span><span class="sxs-lookup"><span data-stu-id="0da50-108">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): A fully managed SQL database Azure service, also known as Platform as a Service (PaaS).</span></span>

<span data-ttu-id="0da50-109">Оба варианта имеют свои преимущества и недостатки, которые вы должны оценить перед переносом.</span><span class="sxs-lookup"><span data-stu-id="0da50-109">Both come with pros and cons that you will need to evaluate before migrating.</span></span>

## <a name="get-started"></a><span data-ttu-id="0da50-110">Начало работы</span><span class="sxs-lookup"><span data-stu-id="0da50-110">Get started</span></span>

<span data-ttu-id="0da50-111">В зависимости от службы, которую вы используете, вам пригодятся следующие руководства по миграции:</span><span class="sxs-lookup"><span data-stu-id="0da50-111">The following migration guides will be useful, depending on which service you use:</span></span>

* [<span data-ttu-id="0da50-112">Миграция базы данных SQL Server в экземпляр SQL Server на виртуальной машине Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-112">Migrate a SQL Server database to SQL Server in an Azure VM</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [<span data-ttu-id="0da50-113">Перенос базы данных SQL Server в базу данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-113">Migrate your SQL Server database to Azure SQL Database</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

<span data-ttu-id="0da50-114">Следующие статьи содержат основные принципы работы виртуальных машин:</span><span class="sxs-lookup"><span data-stu-id="0da50-114">Additionally, the following links to conceptual content will help you understand VMs better:</span></span>

* [<span data-ttu-id="0da50-115">Высокий уровень доступности и аварийное восстановление для SQL Server на виртуальных машинах Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-115">High availability and disaster recovery for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [<span data-ttu-id="0da50-116">Рекомендации по оптимизации производительности SQL Server на виртуальных машинах Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-116">Performance best practices for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [<span data-ttu-id="0da50-117">Шаблоны приложений и стратегии разработки для SQL Server на виртуальных машинах Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-117">Application Patterns and Development Strategies for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

<span data-ttu-id="0da50-118">Следующие статьи содержат дополнительные сведения о Базе данных SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="0da50-118">And the following links will help you understand Azure SQL Database better:</span></span>

* [<span data-ttu-id="0da50-119">Создание серверов базы данных SQL Azure и баз данных SQL Azure и управление ими</span><span class="sxs-lookup"><span data-stu-id="0da50-119">Create and manage Azure SQL Database servers and databases</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [<span data-ttu-id="0da50-120">Единицы транзакций базы данных (DTU) и единицы транзакций эластичной базы данных (eDTU)</span><span class="sxs-lookup"><span data-stu-id="0da50-120">Database Transaction Units (DTUs) and elastic Database Transaction Units (eDTUs)</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [<span data-ttu-id="0da50-121">Ограничения ресурсов базы данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-121">Azure SQL Database resource limits</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a><span data-ttu-id="0da50-122">Выбор IaaS или PaaS</span><span class="sxs-lookup"><span data-stu-id="0da50-122">Choosing IaaS or PaaS</span></span>

<span data-ttu-id="0da50-123">Когда вы решаете, куда перенести базу данных, вам нужно выбрать между IaaS и PaaS.</span><span class="sxs-lookup"><span data-stu-id="0da50-123">When evaluating where to migrate your database, you should determine if IaaS or PaaS is more appropriate for you.</span></span>

<span data-ttu-id="0da50-124">**Выбирайте SQL Server на виртуальных машинах Azure при следующих условиях:**</span><span class="sxs-lookup"><span data-stu-id="0da50-124">**You should choose SQL Server in Azure VMs if:**</span></span>

* <span data-ttu-id="0da50-125">Вам нужен перенос базы данных и приложений по методике lift-and-shift с минимальными изменениями или без них.</span><span class="sxs-lookup"><span data-stu-id="0da50-125">You are looking to "lift and shift" your database and applications with minimal to no changes.</span></span>
* <span data-ttu-id="0da50-126">Вам нужен полный контроль над сервером базы данных и виртуальной машиной, на которой он работает.</span><span class="sxs-lookup"><span data-stu-id="0da50-126">You prefer having full control over your database server and the VM it runs on.</span></span>
* <span data-ttu-id="0da50-127">У вас есть лицензии SQL Server и Windows Server, которые вы собираетесь использовать.</span><span class="sxs-lookup"><span data-stu-id="0da50-127">You already have SQL Server and Windows Server licenses that you intend to use.</span></span>

<span data-ttu-id="0da50-128">**Выбирайте базу данных SQL Azure при следующих условиях:**</span><span class="sxs-lookup"><span data-stu-id="0da50-128">**You should choose Azure SQL Database if:**</span></span>

* <span data-ttu-id="0da50-129">Вы хотите модернизировать приложения и переносите базу данных, чтобы использовать другие службы PaaS в Azure.</span><span class="sxs-lookup"><span data-stu-id="0da50-129">You are looking to modernize your applications and are migrating to use other PaaS services in Azure.</span></span>
* <span data-ttu-id="0da50-130">Вы не хотите управлять сервером базы данных и виртуальной машиной, на которой он работает.</span><span class="sxs-lookup"><span data-stu-id="0da50-130">You do not wish to manage your database server and the VM it runs on.</span></span>
* <span data-ttu-id="0da50-131">У вас нет лицензий SQL Server или Windows Server, или вы не собираетесь продлевать срок действия своих лицензий.</span><span class="sxs-lookup"><span data-stu-id="0da50-131">You do not have SQL Server or Windows Server licenses, or you intend to let licenses you have expire.</span></span>

<span data-ttu-id="0da50-132">В следующей таблице описаны различия между службами на примере набора сценариев.</span><span class="sxs-lookup"><span data-stu-id="0da50-132">The following table describes differences between each service based on a set of scenarios.</span></span>

| <span data-ttu-id="0da50-133">Сценарий</span><span class="sxs-lookup"><span data-stu-id="0da50-133">Scenario</span></span> | <span data-ttu-id="0da50-134">SQL Server на виртуальных машинах Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-134">SQL Server in Azure VMs</span></span> | <span data-ttu-id="0da50-135">Базы данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-135">Azure SQL Database</span></span> |
|----------|-------------------------|--------------------|
| <span data-ttu-id="0da50-136">Миграция</span><span class="sxs-lookup"><span data-stu-id="0da50-136">Migration</span></span> | <span data-ttu-id="0da50-137">Требуются минимальные изменения в базе данных.</span><span class="sxs-lookup"><span data-stu-id="0da50-137">Requires minimal changes to your database.</span></span> | <span data-ttu-id="0da50-138">Могут потребоваться изменения в базе данных, если [помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595) определил, что вы используете недоступные в Azure SQL компоненты. Или при наличии других зависимостей, например локально установленных исполняемых файлов.</span><span class="sxs-lookup"><span data-stu-id="0da50-138">May require changes to your database if you use features unavailable in Azure SQL, as determined by the [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595), or if you have other dependencies such as locally installed executables.</span></span>|
| <span data-ttu-id="0da50-139">Управление доступностью, восстановлением и обновлениями</span><span class="sxs-lookup"><span data-stu-id="0da50-139">Managing availability, recovery, and upgrades</span></span> | <span data-ttu-id="0da50-140">Доступность и восстановление настраиваются вручную.</span><span class="sxs-lookup"><span data-stu-id="0da50-140">Availability and recovery is configured manually.</span></span> <span data-ttu-id="0da50-141">Обновления можно автоматизировать с помощью [масштабируемых наборов виртуальных машин](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade).</span><span class="sxs-lookup"><span data-stu-id="0da50-141">Upgrades can be automated with [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade).</span></span> | <span data-ttu-id="0da50-142">Автоматическое управление.</span><span class="sxs-lookup"><span data-stu-id="0da50-142">Automatically managed for you.</span></span> |
| <span data-ttu-id="0da50-143">Конфигурация базовой операционной системы</span><span class="sxs-lookup"><span data-stu-id="0da50-143">Underlying OS configuration</span></span> | <span data-ttu-id="0da50-144">Настройка вручную.</span><span class="sxs-lookup"><span data-stu-id="0da50-144">Manual configuration.</span></span> | <span data-ttu-id="0da50-145">Автоматическое управление.</span><span class="sxs-lookup"><span data-stu-id="0da50-145">Automatically managed for you.</span></span> |
| <span data-ttu-id="0da50-146">Управление размером базы данных</span><span class="sxs-lookup"><span data-stu-id="0da50-146">Managing database size</span></span> | <span data-ttu-id="0da50-147">Поддерживает до 64 ТБ хранилища на экземпляр SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0da50-147">Supports up to 64TB of storage per SQL Server instance.</span></span> | <span data-ttu-id="0da50-148">Поддерживает 4 ТБ хранилища, прежде чем понадобится горизонтальное секционирование.</span><span class="sxs-lookup"><span data-stu-id="0da50-148">Supports 4TB of storage before needing a horizontal partition.</span></span> |
| <span data-ttu-id="0da50-149">Управление затратами</span><span class="sxs-lookup"><span data-stu-id="0da50-149">Managing costs</span></span> | <span data-ttu-id="0da50-150">Необходимо управлять затратами на лицензию SQL Server, лицензию Windows Server и виртуальную машину (с учетом ядер, ОЗУ и объема хранилища).</span><span class="sxs-lookup"><span data-stu-id="0da50-150">You must manage SQL Server license costs, Windows Server license costs, and VM costs (based on cores, RAM, and storage).</span></span> | <span data-ttu-id="0da50-151">Необходимо управлять затратами на обслуживание (на основе [единиц eDTU или DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), объема хранилища и количества баз данных, если используется эластичный пул).</span><span class="sxs-lookup"><span data-stu-id="0da50-151">You must manage service costs (based on [eDTUs or DTUs](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), storage, and number of databases if using an elastic pool).</span></span>  <span data-ttu-id="0da50-152">Необходимо контролировать стоимость всех соглашений об уровне обслуживания.</span><span class="sxs-lookup"><span data-stu-id="0da50-152">You must also manage the cost of any SLA.</span></span> |

<span data-ttu-id="0da50-153">Дополнительные сведения о различиях между двумя вариантами см. в статье о [выборе между базой данных SQL Azure или SQL Server на виртуальных машинах Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).</span><span class="sxs-lookup"><span data-stu-id="0da50-153">To learn more about the differences between the two, read Choose a cloud SQL Server option: [Azure SQL Database or SQL Server on Azure VMs](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).</span></span>

## <a name="faq"></a><span data-ttu-id="0da50-154">Часто задаваемые вопросы</span><span class="sxs-lookup"><span data-stu-id="0da50-154">FAQ</span></span>

* <span data-ttu-id="0da50-155">**Можно ли продолжать использовать SQL Server Management Studio и службы SQL Server Reporting Services (SSRS) с SQL Server на виртуальных машинах Azure или с Базой данных SQL Azure?**</span><span class="sxs-lookup"><span data-stu-id="0da50-155">**Can I still use tools such as SQL Server Management Studio and SQL Server Reporting Services (SSRS) with SQL Server in Azure VMs or Azure SQL Database?**</span></span>

    <span data-ttu-id="0da50-156">Да!</span><span class="sxs-lookup"><span data-stu-id="0da50-156">Yes!</span></span> <span data-ttu-id="0da50-157">Все средства Microsoft SQL работают с обеими службами.</span><span class="sxs-lookup"><span data-stu-id="0da50-157">All Microsoft SQL tooling works with both services.</span></span> <span data-ttu-id="0da50-158">Но службы SSRS не являются частью Базы данных SQL Azure, поэтому рекомендуется запустить их на виртуальной машине Azure, а затем выбрать их в экземпляре базы данных.</span><span class="sxs-lookup"><span data-stu-id="0da50-158">SSRS is not part of Azure SQL Database, though, and it's recommended that you run it in an Azure VM and then point it to your database instance.</span></span>
    
* <span data-ttu-id="0da50-159">**Я хочу выбрать PaaS, но не знаю, совместима ли моя база данных с этим вариантом. Какие средства могут мне помочь?**</span><span class="sxs-lookup"><span data-stu-id="0da50-159">**I want to go PaaS but I'm not sure if my database is compatible. Are there tools to help?**</span></span>

    <span data-ttu-id="0da50-160">Да.</span><span class="sxs-lookup"><span data-stu-id="0da50-160">Yes.</span></span> <span data-ttu-id="0da50-161">[Помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595) — средство, которое используется при переносе в Базу данных SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="0da50-161">The [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) is a tool that is used as a part of migrating to Azure SQL Database.</span></span>  <span data-ttu-id="0da50-162">[Служба миграции базы данных Azure](https://azure.microsoft.com/campaigns/database-migration/) — это предварительная версия службы, которую можно использовать для IaaS или PaaS.</span><span class="sxs-lookup"><span data-stu-id="0da50-162">The [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) is a preview service which you can use for either IaaS or PaaS.</span></span>

* <span data-ttu-id="0da50-163">**Можно ли оценить затраты?**</span><span class="sxs-lookup"><span data-stu-id="0da50-163">**Can I estimate costs?**</span></span>

    <span data-ttu-id="0da50-164">Да.</span><span class="sxs-lookup"><span data-stu-id="0da50-164">Yes.</span></span>  <span data-ttu-id="0da50-165">[Калькулятор цен Azure](https://azure.microsoft.com/pricing/calculator/) поможет рассчитать стоимость всех служб Azure, в том числе виртуальных машин и служб баз данных.</span><span class="sxs-lookup"><span data-stu-id="0da50-165">The [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/) can be used for estimating costs for all Azure services, including VMs and database services.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="0da50-166">Дополнительная информация</span><span class="sxs-lookup"><span data-stu-id="0da50-166">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0da50-167">Выбор правильного размещения в Azure</span><span class="sxs-lookup"><span data-stu-id="0da50-167">Choose the right Azure hosting option</span></span>](dotnet-howto-choose-migration.md)
