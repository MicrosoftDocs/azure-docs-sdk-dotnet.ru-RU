---
title: Библиотеки службы "Экземпляры контейнеров Azure" для .NET
description: Справочник по библиотекам службы "Экземпляры контейнеров Azure" для .NET
keywords: Azure, .NET, SDK, API, Container Instances, ACI
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 05/25/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: dcontainer-instances
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 033f67a989b0ed6cfcb67a6212c0d5c46c485afa
ms.sourcegitcommit: 4ae9f77a9300a4fe54d0179055ae61191078f207
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34567190"
---
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="80a25-104">Библиотеки службы "Экземпляры контейнеров Azure" для .NET</span><span class="sxs-lookup"><span data-stu-id="80a25-104">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="80a25-105">Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки службы "Экземпляры контейнеров Azure" для .NET.</span><span class="sxs-lookup"><span data-stu-id="80a25-105">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="80a25-106">Дополнительные сведения см. в статье [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-overview).</span><span class="sxs-lookup"><span data-stu-id="80a25-106">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="80a25-107">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="80a25-107">Management library</span></span>

<span data-ttu-id="80a25-108">Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки управления.</span><span class="sxs-lookup"><span data-stu-id="80a25-108">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="80a25-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="80a25-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="80a25-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="80a25-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="examples"></a><span data-ttu-id="80a25-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="80a25-111">Examples</span></span>

### <a name="create-container-group---single-container"></a><span data-ttu-id="80a25-112">Создание группы контейнеров с одним контейнером</span><span class="sxs-lookup"><span data-stu-id="80a25-112">Create container group - single container</span></span>

<span data-ttu-id="80a25-113">В этом примере создается группа контейнеров с одним контейнером.</span><span class="sxs-lookup"><span data-stu-id="80a25-113">This example creates a container group with a single container.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]

### <a name="create-container-group---multiple-containers"></a><span data-ttu-id="80a25-114">Создание группы контейнеров с несколькими контейнерами</span><span class="sxs-lookup"><span data-stu-id="80a25-114">Create container group - multiple containers</span></span>

<span data-ttu-id="80a25-115">В этом примере создается группа контейнеров с двумя контейнерами: контейнером приложения и контейнером расширения.</span><span class="sxs-lookup"><span data-stu-id="80a25-115">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]

### <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="80a25-116">Асинхронное создание контейнера с использованием опроса</span><span class="sxs-lookup"><span data-stu-id="80a25-116">Asynchronous container create with polling</span></span>

<span data-ttu-id="80a25-117">В этом примере создается группа контейнеров с одним контейнером с использованием метода асинхронного создания.</span><span class="sxs-lookup"><span data-stu-id="80a25-117">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="80a25-118">Затем опрашивается служба Azure на наличие группы контейнеров и выводятся сведения о состоянии группы контейнеров, пока оно имеет значение "Running".</span><span class="sxs-lookup"><span data-stu-id="80a25-118">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]

### <a name="create-task-based-container-group"></a><span data-ttu-id="80a25-119">Создание группы контейнеров на основе задач</span><span class="sxs-lookup"><span data-stu-id="80a25-119">Create task-based container group</span></span>

<span data-ttu-id="80a25-120">В этом примере создается группа контейнеров с одним контейнером на основе задач.</span><span class="sxs-lookup"><span data-stu-id="80a25-120">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="80a25-121">Для контейнера настраивается [пользовательская командная строка](/azure/container-instances/container-instances-restart-policy#command-line-override), для [политики перезапуска](/azure/container-instances/container-instances-restart-policy) устанавливается значение "Never".</span><span class="sxs-lookup"><span data-stu-id="80a25-121">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="80a25-122">Чтобы выполнить одну команду с несколькими аргументами командной строки, например `echo FOO BAR`, укажите их в качестве массива строк для метода `WithStartingCommandLines`.</span><span class="sxs-lookup"><span data-stu-id="80a25-122">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="80a25-123">Например: </span><span class="sxs-lookup"><span data-stu-id="80a25-123">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="80a25-124">Если нужно использовать несколько команд (возможно) с несколькими аргументами, выполните сценарий оболочки и передайте связанные команды в виде аргумента.</span><span class="sxs-lookup"><span data-stu-id="80a25-124">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="80a25-125">Например, в этом случае выполняются команды `echo` и `tail`:</span><span class="sxs-lookup"><span data-stu-id="80a25-125">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]

### <a name="list-container-groups"></a><span data-ttu-id="80a25-126">Получение списка групп контейнеров</span><span class="sxs-lookup"><span data-stu-id="80a25-126">List container groups</span></span>

<span data-ttu-id="80a25-127">В этом примере выводится список групп контейнеров в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="80a25-127">This example lists the container groups in a resource group.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]

### <a name="get-an-existing-container-group"></a><span data-ttu-id="80a25-128">Получение сведений о существующей группе контейнеров</span><span class="sxs-lookup"><span data-stu-id="80a25-128">Get an existing container group</span></span>

<span data-ttu-id="80a25-129">В этом примере возвращаются данные определенной группы контейнеров в группе ресурсов и выводятся некоторые свойства группы контейнеров, а также их значения.</span><span class="sxs-lookup"><span data-stu-id="80a25-129">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]

### <a name="delete-a-container-group"></a><span data-ttu-id="80a25-130">Удаление группы контейнеров</span><span class="sxs-lookup"><span data-stu-id="80a25-130">Delete a container group</span></span>

<span data-ttu-id="80a25-131">В этом примере группа контейнеров удаляется из группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="80a25-131">This example deletes a container group from a resource group.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]

## <a name="api-reference"></a><span data-ttu-id="80a25-132">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="80a25-132">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="80a25-133">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="80a25-133">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="80a25-134">Примеры</span><span class="sxs-lookup"><span data-stu-id="80a25-134">Samples</span></span>

* <span data-ttu-id="80a25-135">Исходный код для приведенных выше примеров можно найти на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="80a25-135">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="80a25-136">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="80a25-136">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="80a25-137">Дополнительные примеры кода для службы "Экземпляры контейнеров Azure":</span><span class="sxs-lookup"><span data-stu-id="80a25-137">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="80a25-138">[Примеры кода Azure][samples]</span><span class="sxs-lookup"><span data-stu-id="80a25-138">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="80a25-139">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="80a25-139">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
