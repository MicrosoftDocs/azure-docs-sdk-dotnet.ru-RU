---
title: "Заметки о выпуске библиотек управления Azure для .NET | Документация Майкрософт"
description: "Узнайте о новых возможностях и критически важных изменениях в библиотеках управления Azure для .NET."
keywords: Azure, .NET, API, reference, notes,  updates, deprecate
author: camsoper
ms.author: casoper
manager: douge
ms.assetid: 
ms.service: Azure
ms.devlang: dotnet
ms.topic: reference
ms.technology: Azure
ms.date: 06/20/2017
ms.openlocfilehash: b4a66eb2860673f63a0d11c3cf31486337f36131
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="release-notes"></a><span data-ttu-id="02dbc-104">Заметки о выпуске</span><span class="sxs-lookup"><span data-stu-id="02dbc-104">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="02dbc-105">Доступность функций и план выпуска начиная с версии 1.0.0</span><span class="sxs-lookup"><span data-stu-id="02dbc-105">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="02dbc-106">26 апреля 2017 г.</span><span class="sxs-lookup"><span data-stu-id="02dbc-106">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="02dbc-107">Служба | функция</span><span class="sxs-lookup"><span data-stu-id="02dbc-107">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="02dbc-108">Доступны в общедоступной версии</span><span class="sxs-lookup"><span data-stu-id="02dbc-108">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="02dbc-109">Доступны в предварительной версии</span><span class="sxs-lookup"><span data-stu-id="02dbc-109">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="02dbc-110">Скоро</span><span class="sxs-lookup"><span data-stu-id="02dbc-110">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="02dbc-111">Среда выполнения приложений</span><span class="sxs-lookup"><span data-stu-id="02dbc-111">Compute</span></span></td>
    <td><span data-ttu-id="02dbc-112">Виртуальные машины и их расширения</span><span class="sxs-lookup"><span data-stu-id="02dbc-112">Virtual machines and VM extensions</span></span><br><span data-ttu-id="02dbc-113">наборы для масштабирования виртуальных машин</span><span class="sxs-lookup"><span data-stu-id="02dbc-113">Virtual machine scale sets</span></span><br><span data-ttu-id="02dbc-114">Управляемые диски</span><span class="sxs-lookup"><span data-stu-id="02dbc-114">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="02dbc-115">Службы контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="02dbc-115">Azure container services</span></span><br><span data-ttu-id="02dbc-116">Реестр контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="02dbc-116">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="02dbc-117">Хранилище</span><span class="sxs-lookup"><span data-stu-id="02dbc-117">Storage</span></span></td>
    <td><span data-ttu-id="02dbc-118">учетные записи хранения;</span><span class="sxs-lookup"><span data-stu-id="02dbc-118">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="02dbc-119">Шифрование</span><span class="sxs-lookup"><span data-stu-id="02dbc-119">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="02dbc-120">База данных SQL</span><span class="sxs-lookup"><span data-stu-id="02dbc-120">SQL Database</span></span></td>
    <td><span data-ttu-id="02dbc-121">Базы данных</span><span class="sxs-lookup"><span data-stu-id="02dbc-121">Databases</span></span><br><span data-ttu-id="02dbc-122">Брандмауэры</span><span class="sxs-lookup"><span data-stu-id="02dbc-122">Firewalls</span></span><br><span data-ttu-id="02dbc-123">Пулы эластичных БД</span><span class="sxs-lookup"><span data-stu-id="02dbc-123">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="02dbc-124">Сеть</span><span class="sxs-lookup"><span data-stu-id="02dbc-124">Networking</span></span></td>
    <td><span data-ttu-id="02dbc-125">виртуальные сети;</span><span class="sxs-lookup"><span data-stu-id="02dbc-125">Virtual networks</span></span><br><span data-ttu-id="02dbc-126">Сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="02dbc-126">Network interfaces</span></span><br><span data-ttu-id="02dbc-127">IP-адреса;</span><span class="sxs-lookup"><span data-stu-id="02dbc-127">IP addresses</span></span><br><span data-ttu-id="02dbc-128">Таблица маршрутизации</span><span class="sxs-lookup"><span data-stu-id="02dbc-128">Routing table</span></span><br><span data-ttu-id="02dbc-129">Группы безопасности сети</span><span class="sxs-lookup"><span data-stu-id="02dbc-129">Network security groups</span></span><br><span data-ttu-id="02dbc-130">DNS</span><span class="sxs-lookup"><span data-stu-id="02dbc-130">DNS</span></span><br><span data-ttu-id="02dbc-131">Диспетчеры трафика</span><span class="sxs-lookup"><span data-stu-id="02dbc-131">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="02dbc-132">Балансировщики нагрузки</span><span class="sxs-lookup"><span data-stu-id="02dbc-132">Load balancers</span></span><br><span data-ttu-id="02dbc-133">Шлюзы приложений</span><span class="sxs-lookup"><span data-stu-id="02dbc-133">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="02dbc-134">Другие службы</span><span class="sxs-lookup"><span data-stu-id="02dbc-134">More services</span></span></td>
    <td><span data-ttu-id="02dbc-135">Диспетчер ресурсов</span><span class="sxs-lookup"><span data-stu-id="02dbc-135">Resource Manager</span></span><br><span data-ttu-id="02dbc-136">Хранилище ключей</span><span class="sxs-lookup"><span data-stu-id="02dbc-136">Key Vault</span></span><br><span data-ttu-id="02dbc-137">Redis</span><span class="sxs-lookup"><span data-stu-id="02dbc-137">Redis</span></span><br><span data-ttu-id="02dbc-138">CDN</span><span class="sxs-lookup"><span data-stu-id="02dbc-138">CDN</span></span><br><span data-ttu-id="02dbc-139">Пакетная служба</span><span class="sxs-lookup"><span data-stu-id="02dbc-139">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="02dbc-140">Служба приложений — веб-приложения</span><span class="sxs-lookup"><span data-stu-id="02dbc-140">App service - Web apps</span></span><br><span data-ttu-id="02dbc-141">Функции</span><span class="sxs-lookup"><span data-stu-id="02dbc-141">Functions</span></span><br><span data-ttu-id="02dbc-142">Служебная шина</span><span class="sxs-lookup"><span data-stu-id="02dbc-142">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="02dbc-143">Монитор</span><span class="sxs-lookup"><span data-stu-id="02dbc-143">Monitor</span></span><br><span data-ttu-id="02dbc-144">RBAC графа</span><span class="sxs-lookup"><span data-stu-id="02dbc-144">Graph RBAC</span></span><br><span data-ttu-id="02dbc-145">DocumentDB</span><span class="sxs-lookup"><span data-stu-id="02dbc-145">DocumentDB</span></span><br><span data-ttu-id="02dbc-146">Планировщик</span><span class="sxs-lookup"><span data-stu-id="02dbc-146">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="02dbc-147">Основы</span><span class="sxs-lookup"><span data-stu-id="02dbc-147">Fundamentals</span></span></td>
    <td><span data-ttu-id="02dbc-148">Проверка подлинности — базовая</span><span class="sxs-lookup"><span data-stu-id="02dbc-148">Authentication - core</span></span></td>
    <td><span data-ttu-id="02dbc-149">Асинхронные методы</span><span class="sxs-lookup"><span data-stu-id="02dbc-149">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="02dbc-150">Функции в *предварительной версии* отмечены в комментариях к документации в библиотеках.</span><span class="sxs-lookup"><span data-stu-id="02dbc-150">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="02dbc-151">Эти функции могут измениться.</span><span class="sxs-lookup"><span data-stu-id="02dbc-151">These features are subject to change.</span></span> <span data-ttu-id="02dbc-152">В будущем они могут быть модифицированы любым образом (или даже удалены).</span><span class="sxs-lookup"><span data-stu-id="02dbc-152">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
