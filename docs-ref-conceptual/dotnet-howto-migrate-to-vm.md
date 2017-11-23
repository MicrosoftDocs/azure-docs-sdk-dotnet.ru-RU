---
title: "Перенос веб-приложения ASP.NET на виртуальную машину Azure"
description: "Узнайте, как перенести веб-приложение ASP.NET из локальной среды на виртуальную машину Azure."
keywords: Azure .NET, ASP.NET, VM, virtual machine, migrate, migration
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: virtual-machines
ms.custom: devcenter
ms.openlocfilehash: 718d91b98180a7584f78a2383d430c4700743306
ms.sourcegitcommit: c360a22d5bff6eedd714b28b847d2f26b06665f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2017
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="49bb7-104">Перенос веб-приложения ASP.NET на виртуальную машину Azure</span><span class="sxs-lookup"><span data-stu-id="49bb7-104">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="49bb7-105">В этом документе приводятся общие сведения о том, как перенести веб-приложение ASP.NET из локальной среды на виртуальную машину Azure.</span><span class="sxs-lookup"><span data-stu-id="49bb7-105">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="get-started"></a><span data-ttu-id="49bb7-106">Начало работы</span><span class="sxs-lookup"><span data-stu-id="49bb7-106">Get Started</span></span>

<span data-ttu-id="49bb7-107">В этих руководствах показано, как создать (перенести) виртуальную машину и опубликовать на ней веб-приложение, а также как выполнить другие задачи, которые могут потребоваться для поддержки приложения в Azure.</span><span class="sxs-lookup"><span data-stu-id="49bb7-107">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="49bb7-108">Создайте виртуальную машину в Azure для приложения ASP.NET, используя один из следующих двух вариантов:</span><span class="sxs-lookup"><span data-stu-id="49bb7-108">Create a virtual machine for your ASP.NET application in Azure using one of the following two options:</span></span>
    - <span data-ttu-id="49bb7-109">[Создание виртуальной машины для приложений ASP.NET](https://go.microsoft.com/fwlink/?linkid=863237).</span><span class="sxs-lookup"><span data-stu-id="49bb7-109">[Create a new virtual machine for ASP.NET Applications](https://go.microsoft.com/fwlink/?linkid=863237)</span></span>
    - <span data-ttu-id="49bb7-110">[Перенос существующей локальной виртуальной машины](https://docs.microsoft.com/azure/site-recovery/tutorial-migrate-on-premises-to-azure).</span><span class="sxs-lookup"><span data-stu-id="49bb7-110">[Migrate an existing on-premises virtual machine](https://docs.microsoft.com/azure/site-recovery/tutorial-migrate-on-premises-to-azure)</span></span>
- <span data-ttu-id="49bb7-111">[Опубликуйте свое приложение с помощью Visual Studio](https://go.microsoft.com/fwlink/?linkid=863240).</span><span class="sxs-lookup"><span data-stu-id="49bb7-111">[Publish your app using Visual Studio](https://go.microsoft.com/fwlink/?linkid=863240)</span></span>
- <span data-ttu-id="49bb7-112">[Создайте защищенную виртуальную сеть для виртуальных машин](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet).</span><span class="sxs-lookup"><span data-stu-id="49bb7-112">[Create a secure virtual network for your VMs](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)</span></span>
- <span data-ttu-id="49bb7-113">[Создайте конвейер непрерывной интеграции или непрерывного развертывания для приложения](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups).</span><span class="sxs-lookup"><span data-stu-id="49bb7-113">[Create a CI/CD pipeline for your application](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)</span></span>
- <span data-ttu-id="49bb7-114">[Перенесите приложение в масштабируемый набор виртуальных машин, чтобы обеспечить высокий уровень доступности и масштабируемость](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="49bb7-114">[Move to a VM scale set for high availability and scalability](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)</span></span>

## <a name="considerations"></a><span data-ttu-id="49bb7-115">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="49bb7-115">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="49bb7-116">Преимущества</span><span class="sxs-lookup"><span data-stu-id="49bb7-116">Benefits</span></span>

<span data-ttu-id="49bb7-117">Виртуальные машины предоставляют самый простой способ переноса приложения из локальной среды в облако.</span><span class="sxs-lookup"><span data-stu-id="49bb7-117">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span>  <span data-ttu-id="49bb7-118">Они позволяют реплицировать ту среду, которую приложение использует локально, устраняя необходимость в обслуживании собственных центров обработки данных.</span><span class="sxs-lookup"><span data-stu-id="49bb7-118">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span>  <span data-ttu-id="49bb7-119">Масштабируемые наборы виртуальных машин обеспечивают высокий уровень доступности и масштабируемость для приложений, выполняемых на виртуальных машинах.</span><span class="sxs-lookup"><span data-stu-id="49bb7-119">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="49bb7-120">Размер виртуальной машины</span><span class="sxs-lookup"><span data-stu-id="49bb7-120">Virtual Machine Size</span></span>

<span data-ttu-id="49bb7-121">Выберите размер и тип виртуальной машины, которые лучше всего оптимизированы для вашей рабочей нагрузки.</span><span class="sxs-lookup"><span data-stu-id="49bb7-121">Choose the virtual machine size and type that is best optimized for your workload.</span></span>  <span data-ttu-id="49bb7-122">Дополнительные сведения см. в статье [Размеры виртуальных машин Windows в Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).</span><span class="sxs-lookup"><span data-stu-id="49bb7-122">See [sizes for Windows virtual machines in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) for more information.</span></span>

### <a name="maintenance"></a><span data-ttu-id="49bb7-123">Обслуживание, </span><span class="sxs-lookup"><span data-stu-id="49bb7-123">Maintenance</span></span>

<span data-ttu-id="49bb7-124">Как и с локальными компьютерами, вы несете ответственность за обслуживание и обновление виртуальной машины<sup>&#42;</sup>.</span><span class="sxs-lookup"><span data-stu-id="49bb7-124">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span>  <span data-ttu-id="49bb7-125">Если приложение может выполняться в среде PaaS (платформа как услуга), например в [службе приложений Azure](https://docs.microsoft.com/azure/app-service/) или в [контейнере](https://docs.microsoft.com/azure/app-service/containers/), то необходимость в обслуживании устраняется.</span><span class="sxs-lookup"><span data-stu-id="49bb7-125">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](https://docs.microsoft.com/azure/app-service/) or in a [container](https://docs.microsoft.com/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="49bb7-126">*<sup>&#42;</sup>[Автоматическое обновление ОС для масштабируемых наборов виртуальных машин](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) сейчас доступно в виде предварительной версии.*</span><span class="sxs-lookup"><span data-stu-id="49bb7-126">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="49bb7-127">Виртуальные сети</span><span class="sxs-lookup"><span data-stu-id="49bb7-127">Virtual Networks</span></span>

<span data-ttu-id="49bb7-128">Виртуальные сети Azure позволяют выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="49bb7-128">Azure Virtual Networks enable you to:</span></span>
- <span data-ttu-id="49bb7-129">Создание управляемой гибридной инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="49bb7-129">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="49bb7-130">Использование собственных IP-адресов и DNS-серверов.</span><span class="sxs-lookup"><span data-stu-id="49bb7-130">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="49bb7-131">Создание изолированной и надежно защищенной среды для ваших приложений.</span><span class="sxs-lookup"><span data-stu-id="49bb7-131">Create an isolated and highly-secure environment for your applications</span></span>
- <span data-ttu-id="49bb7-132">Подключение виртуальной машины к локальной сети с использованием одного из нескольких [вариантов подключения](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti).</span><span class="sxs-lookup"><span data-stu-id="49bb7-132">Connect your VM to your on-premises network using one of several [connectivity options](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="49bb7-133">Интеграция виртуальной машины с локальной сетью с помощью [ExpressRoute](https://azure.microsoft.com/services/expressroute/).</span><span class="sxs-lookup"><span data-stu-id="49bb7-133">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="49bb7-134">Чтобы начать работу, ознакомьтесь с [документацией по виртуальным сетям](https://docs.microsoft.com/azure/virtual-network/).</span><span class="sxs-lookup"><span data-stu-id="49bb7-134">To get started, see the [Virtual Network documentation](https://docs.microsoft.com/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="49bb7-135">Active Directory</span><span class="sxs-lookup"><span data-stu-id="49bb7-135">Active Directory</span></span>
<span data-ttu-id="49bb7-136">Многие приложения используют Active Directory для проверки подлинности и управления удостоверениями.</span><span class="sxs-lookup"><span data-stu-id="49bb7-136">Many applications use Active Directory for authentication and identity management.</span></span>  
- <span data-ttu-id="49bb7-137">Azure AD Connect позволяет интегрировать локальные каталоги с Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="49bb7-137">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span>  <span data-ttu-id="49bb7-138">Чтобы приступить к работе, изучите статью [Интеграция локальных каталогов с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="49bb7-138">To get started, see [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span></span>  
- <span data-ttu-id="49bb7-139">Также и [ExpressRoute](https://azure.microsoft.com/services/expressroute/) позволяет приложению получить доступ к локальной службе Active Directory.</span><span class="sxs-lookup"><span data-stu-id="49bb7-139">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="49bb7-140">Базы данных SQL</span><span class="sxs-lookup"><span data-stu-id="49bb7-140">SQL Databases</span></span>

<span data-ttu-id="49bb7-141">Если приложение использует локальную базу данных, оно не сможет обращаться к ней по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="49bb7-141">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="49bb7-142">Вы можете выбрать один из таких вариантов:</span><span class="sxs-lookup"><span data-stu-id="49bb7-142">You can either:</span></span>
- <span data-ttu-id="49bb7-143">Настройте гибридную сеть, которая позволит вашему приложению получать доступ к базе данных, работающей локально.</span><span class="sxs-lookup"><span data-stu-id="49bb7-143">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>  
- <span data-ttu-id="49bb7-144">Перенесите базу данных в Azure.</span><span class="sxs-lookup"><span data-stu-id="49bb7-144">Migrate your database to the Azure.</span></span>  <span data-ttu-id="49bb7-145">Дополнительные сведения см. в статье [Перенос базы данных SQL Server в Azure](dotnet-howto-migrate-sql.md).</span><span class="sxs-lookup"><span data-stu-id="49bb7-145">See [Migrate your SQL Server database to Azure](dotnet-howto-migrate-sql.md) for more information.</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="49bb7-146">Высокий уровень доступности и масштабируемости</span><span class="sxs-lookup"><span data-stu-id="49bb7-146">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="49bb7-147">Наборы для масштабирования виртуальных машин</span><span class="sxs-lookup"><span data-stu-id="49bb7-147">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="49bb7-148">Если вам нужно обеспечить высокий уровень доступности и возможность масштабирования для приложения, перенесите образ виртуальной машины в масштабируемый набор виртуальных машин Azure, чтобы повысить уровень доступности и улучшить возможность масштабирования приложения.</span><span class="sxs-lookup"><span data-stu-id="49bb7-148">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span>  <span data-ttu-id="49bb7-149">Масштабируемые наборы виртуальных машин позволяют использовать уже настроенную виртуальную машину или настроить конвейер сборки, чтобы создать образ с вашим приложением.</span><span class="sxs-lookup"><span data-stu-id="49bb7-149">VM Scale Sets provide the ability to use an existing VM you’ve already configured or set up a build pipeline to build an image with your application.</span></span>  

<span data-ttu-id="49bb7-150">Чтобы приступить к работе, изучите статью [Развертывание приложения в масштабируемых наборах виртуальных машин](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="49bb7-150">To get started, see [Deploy your application on virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="49bb7-151">Централизованное ведение журналов</span><span class="sxs-lookup"><span data-stu-id="49bb7-151">Centralized Logging</span></span>
<span data-ttu-id="49bb7-152">Если приложение выполняется на нескольких экземплярах, рассмотрите возможность хранения журналов в централизованном расположении, например в [хранилище Azure](https://docs.microsoft.com/azure/storage/).</span><span class="sxs-lookup"><span data-stu-id="49bb7-152">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](https://docs.microsoft.com/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="49bb7-153">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="49bb7-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49bb7-154">Перенос базы данных SQL Server в Azure</span><span class="sxs-lookup"><span data-stu-id="49bb7-154">Migrate a SQL Server database to Azure</span></span>](dotnet-howto-migrate-sql.md)