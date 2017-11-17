---
title: "Заметки о выпуске библиотек управления Azure для .NET | Документация Майкрософт"
description: "Узнайте о новых возможностях и критически важных изменениях в библиотеках управления Azure для .NET."
keywords: Azure, .NET, API, reference, notes,  updates, deprecate
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 714bd05653c6b41b21b95581b1115b0bfa1956ed
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2017
---
# <a name="release-notes"></a><span data-ttu-id="0ac66-104">Заметки о выпуске</span><span class="sxs-lookup"><span data-stu-id="0ac66-104">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="0ac66-105">Доступность функций и план выпуска начиная с версии 1.0.0</span><span class="sxs-lookup"><span data-stu-id="0ac66-105">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="0ac66-106">26 апреля 2017 г.</span><span class="sxs-lookup"><span data-stu-id="0ac66-106">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="0ac66-107">Служба | функция</span><span class="sxs-lookup"><span data-stu-id="0ac66-107">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="0ac66-108">Доступны в общедоступной версии</span><span class="sxs-lookup"><span data-stu-id="0ac66-108">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="0ac66-109">Доступны в предварительной версии</span><span class="sxs-lookup"><span data-stu-id="0ac66-109">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="0ac66-110">Скоро</span><span class="sxs-lookup"><span data-stu-id="0ac66-110">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="0ac66-111">Среда выполнения приложений</span><span class="sxs-lookup"><span data-stu-id="0ac66-111">Compute</span></span></td>
    <td><span data-ttu-id="0ac66-112">Виртуальные машины и их расширения</span><span class="sxs-lookup"><span data-stu-id="0ac66-112">Virtual machines and VM extensions</span></span><br><span data-ttu-id="0ac66-113">наборы для масштабирования виртуальных машин</span><span class="sxs-lookup"><span data-stu-id="0ac66-113">Virtual machine scale sets</span></span><br><span data-ttu-id="0ac66-114">Управляемые диски</span><span class="sxs-lookup"><span data-stu-id="0ac66-114">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="0ac66-115">Службы контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="0ac66-115">Azure container services</span></span><br><span data-ttu-id="0ac66-116">Реестр контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="0ac66-116">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="0ac66-117">Хранилище</span><span class="sxs-lookup"><span data-stu-id="0ac66-117">Storage</span></span></td>
    <td><span data-ttu-id="0ac66-118">учетные записи хранения;</span><span class="sxs-lookup"><span data-stu-id="0ac66-118">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="0ac66-119">Шифрование</span><span class="sxs-lookup"><span data-stu-id="0ac66-119">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="0ac66-120">База данных SQL</span><span class="sxs-lookup"><span data-stu-id="0ac66-120">SQL Database</span></span></td>
    <td><span data-ttu-id="0ac66-121">Базы данных</span><span class="sxs-lookup"><span data-stu-id="0ac66-121">Databases</span></span><br><span data-ttu-id="0ac66-122">Брандмауэры</span><span class="sxs-lookup"><span data-stu-id="0ac66-122">Firewalls</span></span><br><span data-ttu-id="0ac66-123">Пулы эластичных БД</span><span class="sxs-lookup"><span data-stu-id="0ac66-123">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="0ac66-124">Сеть</span><span class="sxs-lookup"><span data-stu-id="0ac66-124">Networking</span></span></td>
    <td><span data-ttu-id="0ac66-125">виртуальные сети;</span><span class="sxs-lookup"><span data-stu-id="0ac66-125">Virtual networks</span></span><br><span data-ttu-id="0ac66-126">Сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="0ac66-126">Network interfaces</span></span><br><span data-ttu-id="0ac66-127">IP-адреса;</span><span class="sxs-lookup"><span data-stu-id="0ac66-127">IP addresses</span></span><br><span data-ttu-id="0ac66-128">Таблица маршрутизации</span><span class="sxs-lookup"><span data-stu-id="0ac66-128">Routing table</span></span><br><span data-ttu-id="0ac66-129">Группы безопасности сети</span><span class="sxs-lookup"><span data-stu-id="0ac66-129">Network security groups</span></span><br><span data-ttu-id="0ac66-130">DNS</span><span class="sxs-lookup"><span data-stu-id="0ac66-130">DNS</span></span><br><span data-ttu-id="0ac66-131">Диспетчеры трафика</span><span class="sxs-lookup"><span data-stu-id="0ac66-131">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="0ac66-132">Балансировщики нагрузки</span><span class="sxs-lookup"><span data-stu-id="0ac66-132">Load balancers</span></span><br><span data-ttu-id="0ac66-133">Шлюзы приложений</span><span class="sxs-lookup"><span data-stu-id="0ac66-133">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="0ac66-134">Другие службы</span><span class="sxs-lookup"><span data-stu-id="0ac66-134">More services</span></span></td>
    <td><span data-ttu-id="0ac66-135">Диспетчер ресурсов</span><span class="sxs-lookup"><span data-stu-id="0ac66-135">Resource Manager</span></span><br><span data-ttu-id="0ac66-136">Хранилище ключей</span><span class="sxs-lookup"><span data-stu-id="0ac66-136">Key Vault</span></span><br><span data-ttu-id="0ac66-137">Redis</span><span class="sxs-lookup"><span data-stu-id="0ac66-137">Redis</span></span><br><span data-ttu-id="0ac66-138">CDN</span><span class="sxs-lookup"><span data-stu-id="0ac66-138">CDN</span></span><br><span data-ttu-id="0ac66-139">Пакетная служба</span><span class="sxs-lookup"><span data-stu-id="0ac66-139">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="0ac66-140">Служба приложений — веб-приложения</span><span class="sxs-lookup"><span data-stu-id="0ac66-140">App service - Web apps</span></span><br><span data-ttu-id="0ac66-141">Функции</span><span class="sxs-lookup"><span data-stu-id="0ac66-141">Functions</span></span><br><span data-ttu-id="0ac66-142">Служебная шина</span><span class="sxs-lookup"><span data-stu-id="0ac66-142">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="0ac66-143">Монитор</span><span class="sxs-lookup"><span data-stu-id="0ac66-143">Monitor</span></span><br><span data-ttu-id="0ac66-144">RBAC графа</span><span class="sxs-lookup"><span data-stu-id="0ac66-144">Graph RBAC</span></span><br><span data-ttu-id="0ac66-145">DocumentDB</span><span class="sxs-lookup"><span data-stu-id="0ac66-145">DocumentDB</span></span><br><span data-ttu-id="0ac66-146">Планировщик</span><span class="sxs-lookup"><span data-stu-id="0ac66-146">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="0ac66-147">Основы</span><span class="sxs-lookup"><span data-stu-id="0ac66-147">Fundamentals</span></span></td>
    <td><span data-ttu-id="0ac66-148">Проверка подлинности — базовая</span><span class="sxs-lookup"><span data-stu-id="0ac66-148">Authentication - core</span></span></td>
    <td><span data-ttu-id="0ac66-149">Асинхронные методы</span><span class="sxs-lookup"><span data-stu-id="0ac66-149">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="0ac66-150">Функции в *предварительной версии* отмечены в комментариях к документации в библиотеках.</span><span class="sxs-lookup"><span data-stu-id="0ac66-150">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="0ac66-151">Эти функции могут измениться.</span><span class="sxs-lookup"><span data-stu-id="0ac66-151">These features are subject to change.</span></span> <span data-ttu-id="0ac66-152">В будущем они могут быть модифицированы любым образом (или даже удалены).</span><span class="sxs-lookup"><span data-stu-id="0ac66-152">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
