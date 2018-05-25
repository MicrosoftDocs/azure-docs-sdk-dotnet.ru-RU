---
title: Заметки о выпуске библиотек управления Azure для .NET | Документация Майкрософт
description: Узнайте о новых возможностях и критически важных изменениях в библиотеках управления Azure для .NET.
keywords: Azure, .NET, API, reference, notes,  updates, deprecate
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 48ff29507268f6b38acb24217801cf7b0227e444
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2018
---
# <a name="release-notes"></a><span data-ttu-id="f4e81-104">Заметки о выпуске</span><span class="sxs-lookup"><span data-stu-id="f4e81-104">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="f4e81-105">Доступность функций и план выпуска начиная с версии 1.0.0</span><span class="sxs-lookup"><span data-stu-id="f4e81-105">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="f4e81-106">26 апреля 2017 г.</span><span class="sxs-lookup"><span data-stu-id="f4e81-106">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="f4e81-107">Служба | функция</span><span class="sxs-lookup"><span data-stu-id="f4e81-107">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="f4e81-108">Доступны в общедоступной версии</span><span class="sxs-lookup"><span data-stu-id="f4e81-108">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="f4e81-109">Доступны в предварительной версии</span><span class="sxs-lookup"><span data-stu-id="f4e81-109">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="f4e81-110">Скоро</span><span class="sxs-lookup"><span data-stu-id="f4e81-110">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="f4e81-111">Среда выполнения приложений</span><span class="sxs-lookup"><span data-stu-id="f4e81-111">Compute</span></span></td>
    <td><span data-ttu-id="f4e81-112">Виртуальные машины и их расширения</span><span class="sxs-lookup"><span data-stu-id="f4e81-112">Virtual machines and VM extensions</span></span><br><span data-ttu-id="f4e81-113">наборы для масштабирования виртуальных машин</span><span class="sxs-lookup"><span data-stu-id="f4e81-113">Virtual machine scale sets</span></span><br><span data-ttu-id="f4e81-114">Управляемые диски</span><span class="sxs-lookup"><span data-stu-id="f4e81-114">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="f4e81-115">Службы контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="f4e81-115">Azure container services</span></span><br><span data-ttu-id="f4e81-116">Реестр контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="f4e81-116">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="f4e81-117">Хранилище</span><span class="sxs-lookup"><span data-stu-id="f4e81-117">Storage</span></span></td>
    <td><span data-ttu-id="f4e81-118">учетные записи хранения;</span><span class="sxs-lookup"><span data-stu-id="f4e81-118">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="f4e81-119">Шифрование</span><span class="sxs-lookup"><span data-stu-id="f4e81-119">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="f4e81-120">База данных SQL</span><span class="sxs-lookup"><span data-stu-id="f4e81-120">SQL Database</span></span></td>
    <td><span data-ttu-id="f4e81-121">Базы данных</span><span class="sxs-lookup"><span data-stu-id="f4e81-121">Databases</span></span><br><span data-ttu-id="f4e81-122">Брандмауэры</span><span class="sxs-lookup"><span data-stu-id="f4e81-122">Firewalls</span></span><br><span data-ttu-id="f4e81-123">Пулы эластичных БД</span><span class="sxs-lookup"><span data-stu-id="f4e81-123">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="f4e81-124">Сеть</span><span class="sxs-lookup"><span data-stu-id="f4e81-124">Networking</span></span></td>
    <td><span data-ttu-id="f4e81-125">виртуальные сети;</span><span class="sxs-lookup"><span data-stu-id="f4e81-125">Virtual networks</span></span><br><span data-ttu-id="f4e81-126">Сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="f4e81-126">Network interfaces</span></span><br><span data-ttu-id="f4e81-127">IP-адреса;</span><span class="sxs-lookup"><span data-stu-id="f4e81-127">IP addresses</span></span><br><span data-ttu-id="f4e81-128">Таблица маршрутизации</span><span class="sxs-lookup"><span data-stu-id="f4e81-128">Routing table</span></span><br><span data-ttu-id="f4e81-129">Группы безопасности сети</span><span class="sxs-lookup"><span data-stu-id="f4e81-129">Network security groups</span></span><br><span data-ttu-id="f4e81-130">DNS</span><span class="sxs-lookup"><span data-stu-id="f4e81-130">DNS</span></span><br><span data-ttu-id="f4e81-131">Диспетчеры трафика</span><span class="sxs-lookup"><span data-stu-id="f4e81-131">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="f4e81-132">Балансировщики нагрузки</span><span class="sxs-lookup"><span data-stu-id="f4e81-132">Load balancers</span></span><br><span data-ttu-id="f4e81-133">Шлюзы приложений</span><span class="sxs-lookup"><span data-stu-id="f4e81-133">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="f4e81-134">Другие службы</span><span class="sxs-lookup"><span data-stu-id="f4e81-134">More services</span></span></td>
    <td><span data-ttu-id="f4e81-135">Диспетчер ресурсов</span><span class="sxs-lookup"><span data-stu-id="f4e81-135">Resource Manager</span></span><br><span data-ttu-id="f4e81-136">хранилище ключей;</span><span class="sxs-lookup"><span data-stu-id="f4e81-136">Key Vault</span></span><br><span data-ttu-id="f4e81-137">Redis</span><span class="sxs-lookup"><span data-stu-id="f4e81-137">Redis</span></span><br><span data-ttu-id="f4e81-138">CDN</span><span class="sxs-lookup"><span data-stu-id="f4e81-138">CDN</span></span><br><span data-ttu-id="f4e81-139">пакетная служба;</span><span class="sxs-lookup"><span data-stu-id="f4e81-139">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="f4e81-140">Служба приложений — веб-приложения</span><span class="sxs-lookup"><span data-stu-id="f4e81-140">App service - Web apps</span></span><br><span data-ttu-id="f4e81-141">Functions</span><span class="sxs-lookup"><span data-stu-id="f4e81-141">Functions</span></span><br><span data-ttu-id="f4e81-142">Служебная шина</span><span class="sxs-lookup"><span data-stu-id="f4e81-142">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="f4e81-143">Мониторинг</span><span class="sxs-lookup"><span data-stu-id="f4e81-143">Monitor</span></span><br><span data-ttu-id="f4e81-144">RBAC графа</span><span class="sxs-lookup"><span data-stu-id="f4e81-144">Graph RBAC</span></span><br><span data-ttu-id="f4e81-145">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="f4e81-145">Azure Cosmos DB</span></span><br><span data-ttu-id="f4e81-146">Планировщик</span><span class="sxs-lookup"><span data-stu-id="f4e81-146">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="f4e81-147">Основы</span><span class="sxs-lookup"><span data-stu-id="f4e81-147">Fundamentals</span></span></td>
    <td><span data-ttu-id="f4e81-148">Проверка подлинности — базовая</span><span class="sxs-lookup"><span data-stu-id="f4e81-148">Authentication - core</span></span></td>
    <td><span data-ttu-id="f4e81-149">Асинхронные методы</span><span class="sxs-lookup"><span data-stu-id="f4e81-149">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="f4e81-150">Функции в *предварительной версии* отмечены в комментариях к документации в библиотеках.</span><span class="sxs-lookup"><span data-stu-id="f4e81-150">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="f4e81-151">Эти функции могут измениться.</span><span class="sxs-lookup"><span data-stu-id="f4e81-151">These features are subject to change.</span></span> <span data-ttu-id="f4e81-152">В будущем они могут быть модифицированы любым образом (или даже удалены).</span><span class="sxs-lookup"><span data-stu-id="f4e81-152">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
