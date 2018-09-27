---
title: Заметки о выпуске библиотек управления Azure для .NET | Документация Майкрософт
description: Узнайте о новых возможностях и критически важных изменениях в библиотеках управления Azure для .NET.
ms.date: 10/19/2017
ms.openlocfilehash: dac9dee9c25fc349dedd50d6007f25c7d15b0928
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190677"
---
# <a name="release-notes"></a><span data-ttu-id="08ca7-103">Заметки о выпуске</span><span class="sxs-lookup"><span data-stu-id="08ca7-103">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="08ca7-104">Доступность функций и план выпуска начиная с версии 1.0.0</span><span class="sxs-lookup"><span data-stu-id="08ca7-104">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="08ca7-105">26 апреля 2017 г.</span><span class="sxs-lookup"><span data-stu-id="08ca7-105">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="08ca7-106">Служба | функция</span><span class="sxs-lookup"><span data-stu-id="08ca7-106">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="08ca7-107">Доступны в общедоступной версии</span><span class="sxs-lookup"><span data-stu-id="08ca7-107">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="08ca7-108">Доступны в предварительной версии</span><span class="sxs-lookup"><span data-stu-id="08ca7-108">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="08ca7-109">Скоро</span><span class="sxs-lookup"><span data-stu-id="08ca7-109">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="08ca7-110">Службы вычислений</span><span class="sxs-lookup"><span data-stu-id="08ca7-110">Compute</span></span></td>
    <td><span data-ttu-id="08ca7-111">Виртуальные машины и их расширения</span><span class="sxs-lookup"><span data-stu-id="08ca7-111">Virtual machines and VM extensions</span></span><br><span data-ttu-id="08ca7-112">наборы для масштабирования виртуальных машин</span><span class="sxs-lookup"><span data-stu-id="08ca7-112">Virtual machine scale sets</span></span><br><span data-ttu-id="08ca7-113">Управляемые диски</span><span class="sxs-lookup"><span data-stu-id="08ca7-113">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="08ca7-114">Службы контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="08ca7-114">Azure container services</span></span><br><span data-ttu-id="08ca7-115">Реестр контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="08ca7-115">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="08ca7-116">Хранилище</span><span class="sxs-lookup"><span data-stu-id="08ca7-116">Storage</span></span></td>
    <td><span data-ttu-id="08ca7-117">учетные записи хранения;</span><span class="sxs-lookup"><span data-stu-id="08ca7-117">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="08ca7-118">Шифрование</span><span class="sxs-lookup"><span data-stu-id="08ca7-118">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="08ca7-119">База данных SQL</span><span class="sxs-lookup"><span data-stu-id="08ca7-119">SQL Database</span></span></td>
    <td><span data-ttu-id="08ca7-120">Базы данных</span><span class="sxs-lookup"><span data-stu-id="08ca7-120">Databases</span></span><br><span data-ttu-id="08ca7-121">Брандмауэры</span><span class="sxs-lookup"><span data-stu-id="08ca7-121">Firewalls</span></span><br><span data-ttu-id="08ca7-122">Пулы эластичных БД</span><span class="sxs-lookup"><span data-stu-id="08ca7-122">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="08ca7-123">Сеть</span><span class="sxs-lookup"><span data-stu-id="08ca7-123">Networking</span></span></td>
    <td><span data-ttu-id="08ca7-124">виртуальные сети;</span><span class="sxs-lookup"><span data-stu-id="08ca7-124">Virtual networks</span></span><br><span data-ttu-id="08ca7-125">Сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="08ca7-125">Network interfaces</span></span><br><span data-ttu-id="08ca7-126">IP-адреса;</span><span class="sxs-lookup"><span data-stu-id="08ca7-126">IP addresses</span></span><br><span data-ttu-id="08ca7-127">Таблица маршрутизации</span><span class="sxs-lookup"><span data-stu-id="08ca7-127">Routing table</span></span><br><span data-ttu-id="08ca7-128">Группы безопасности сети</span><span class="sxs-lookup"><span data-stu-id="08ca7-128">Network security groups</span></span><br><span data-ttu-id="08ca7-129">DNS</span><span class="sxs-lookup"><span data-stu-id="08ca7-129">DNS</span></span><br><span data-ttu-id="08ca7-130">Диспетчеры трафика</span><span class="sxs-lookup"><span data-stu-id="08ca7-130">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="08ca7-131">Балансировщики нагрузки</span><span class="sxs-lookup"><span data-stu-id="08ca7-131">Load balancers</span></span><br><span data-ttu-id="08ca7-132">Шлюзы приложений</span><span class="sxs-lookup"><span data-stu-id="08ca7-132">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="08ca7-133">Другие службы</span><span class="sxs-lookup"><span data-stu-id="08ca7-133">More services</span></span></td>
    <td><span data-ttu-id="08ca7-134">Диспетчер ресурсов</span><span class="sxs-lookup"><span data-stu-id="08ca7-134">Resource Manager</span></span><br><span data-ttu-id="08ca7-135">Key Vault</span><span class="sxs-lookup"><span data-stu-id="08ca7-135">Key Vault</span></span><br><span data-ttu-id="08ca7-136">Redis</span><span class="sxs-lookup"><span data-stu-id="08ca7-136">Redis</span></span><br><span data-ttu-id="08ca7-137">CDN</span><span class="sxs-lookup"><span data-stu-id="08ca7-137">CDN</span></span><br><span data-ttu-id="08ca7-138">Пакетная служба Azure</span><span class="sxs-lookup"><span data-stu-id="08ca7-138">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="08ca7-139">Служба приложений — веб-приложения</span><span class="sxs-lookup"><span data-stu-id="08ca7-139">App service - Web apps</span></span><br><span data-ttu-id="08ca7-140">Функции Azure</span><span class="sxs-lookup"><span data-stu-id="08ca7-140">Functions</span></span><br><span data-ttu-id="08ca7-141">Служебная шина</span><span class="sxs-lookup"><span data-stu-id="08ca7-141">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="08ca7-142">Мониторинг</span><span class="sxs-lookup"><span data-stu-id="08ca7-142">Monitor</span></span><br><span data-ttu-id="08ca7-143">RBAC графа</span><span class="sxs-lookup"><span data-stu-id="08ca7-143">Graph RBAC</span></span><br><span data-ttu-id="08ca7-144">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="08ca7-144">Azure Cosmos DB</span></span><br><span data-ttu-id="08ca7-145">Планировщик</span><span class="sxs-lookup"><span data-stu-id="08ca7-145">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="08ca7-146">Основы</span><span class="sxs-lookup"><span data-stu-id="08ca7-146">Fundamentals</span></span></td>
    <td><span data-ttu-id="08ca7-147">Проверка подлинности — базовая</span><span class="sxs-lookup"><span data-stu-id="08ca7-147">Authentication - core</span></span></td>
    <td><span data-ttu-id="08ca7-148">Асинхронные методы</span><span class="sxs-lookup"><span data-stu-id="08ca7-148">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="08ca7-149">Функции в *предварительной версии* отмечены в комментариях к документации в библиотеках.</span><span class="sxs-lookup"><span data-stu-id="08ca7-149">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="08ca7-150">Эти функции могут измениться.</span><span class="sxs-lookup"><span data-stu-id="08ca7-150">These features are subject to change.</span></span> <span data-ttu-id="08ca7-151">В будущем они могут быть модифицированы любым образом (или даже удалены).</span><span class="sxs-lookup"><span data-stu-id="08ca7-151">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
