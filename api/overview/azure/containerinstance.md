---
title: Библиотеки службы "Экземпляры контейнеров Azure" для .NET
description: Справочник по библиотекам службы "Экземпляры контейнеров Azure" для .NET
keywords: Azure, .NET, SDK, API, Container Instances, ACI
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 06/11/2018
ms.topic: reference
ms.devlang: dotnet
ms.service: dcontainer-instances
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 85fe5485c04193b336d10e8c387719e2ad1e6910
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37066152"
---
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="2902f-104">Библиотеки службы "Экземпляры контейнеров Azure" для .NET</span><span class="sxs-lookup"><span data-stu-id="2902f-104">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="2902f-105">Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки службы "Экземпляры контейнеров Azure" для .NET.</span><span class="sxs-lookup"><span data-stu-id="2902f-105">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="2902f-106">Дополнительные сведения см. в статье [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-overview).</span><span class="sxs-lookup"><span data-stu-id="2902f-106">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="2902f-107">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="2902f-107">Management library</span></span>

<span data-ttu-id="2902f-108">Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки управления.</span><span class="sxs-lookup"><span data-stu-id="2902f-108">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="2902f-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="2902f-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="2902f-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2902f-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="example-source"></a><span data-ttu-id="2902f-111">Пример исходного кода</span><span class="sxs-lookup"><span data-stu-id="2902f-111">Example source</span></span>

<span data-ttu-id="2902f-112">Чтобы просмотреть приведенные ниже примеры кода в контексте, перейдите к следующему репозиторию GitHub:</span><span class="sxs-lookup"><span data-stu-id="2902f-112">If you'd like to see the following code examples in context, you can find them in the following GitHub repository:</span></span>

[<span data-ttu-id="2902f-113">Azure-Samples/aci-docs-sample-dotnet</span><span class="sxs-lookup"><span data-stu-id="2902f-113">Azure-Samples/aci-docs-sample-dotnet</span></span>](https://github.com/Azure-Samples/aci-docs-sample-dotnet)

## <a name="authentication"></a><span data-ttu-id="2902f-114">Authentication</span><span class="sxs-lookup"><span data-stu-id="2902f-114">Authentication</span></span>

<span data-ttu-id="2902f-115">[Аутентификация с использованием файла][sdk-auth] — самый простой способ аутентификации клиентов SDK.</span><span class="sxs-lookup"><span data-stu-id="2902f-115">One of the easiest ways to authenticate SDK clients is with [file-based authentication][sdk-auth].</span></span> <span data-ttu-id="2902f-116">Во время создания экземпляра клиентского объекта [IAzure][iazure] функция файловой аутентификации анализирует файл учетных данных, после чего объект использует эти учетные данные для аутентификации в Azure.</span><span class="sxs-lookup"><span data-stu-id="2902f-116">File-based authentication parses a credentials file when instantiating the [IAzure][iazure] client object, which then uses those credentials when authenticating with Azure.</span></span> <span data-ttu-id="2902f-117">Использование аутентификации на основе файла</span><span class="sxs-lookup"><span data-stu-id="2902f-117">To use file-based authentication:</span></span>

1. <span data-ttu-id="2902f-118">Создайте файл учетных данных с помощью [Azure CLI](/cli/azure) или [Cloud Shell](https://shell.azure.com/):</span><span class="sxs-lookup"><span data-stu-id="2902f-118">Create a credentials file with the [Azure CLI](/cli/azure) or [Cloud Shell](https://shell.azure.com/):</span></span>

   `az ad sp create-for-rbac --sdk-auth > my.azureauth`

   <span data-ttu-id="2902f-119">Если файл учетных данных создается с помощью [Cloud Shell](https://shell.azure.com/), скопируйте содержимое этого файла в локальный файл, к которому у приложения .NET есть доступ.</span><span class="sxs-lookup"><span data-stu-id="2902f-119">If you use the [Cloud Shell](https://shell.azure.com/) to generate the credentials file, copy its contents into a local file that your .NET application can access.</span></span>

2. <span data-ttu-id="2902f-120">Задайте для переменной среды `AZURE_AUTH_LOCATION` полный путь к созданному файлу учетных данных.</span><span class="sxs-lookup"><span data-stu-id="2902f-120">Set the `AZURE_AUTH_LOCATION` environment variable to the full path of the generated credentials file.</span></span> <span data-ttu-id="2902f-121">Например (оболочка Bash):</span><span class="sxs-lookup"><span data-stu-id="2902f-121">For example (in the Bash shell):</span></span>

   ```bash
   export AZURE_AUTH_LOCATION=/home/yourusername/my.azureauth
   ```

<span data-ttu-id="2902f-122">Создав файл учетных данных и указав значение для переменной среды `AZURE_AUTH_LOCATION`, инициализируйте клиентский объект [IAzure][iazure] с помощью метода [Azure.Authenticate][iazure-authenticate].</span><span class="sxs-lookup"><span data-stu-id="2902f-122">Once you've created the credentials file and populated the `AZURE_AUTH_LOCATION` environment variable, use the [Azure.Authenticate][iazure-authenticate] method to initialize the [IAzure][iazure] client object.</span></span> <span data-ttu-id="2902f-123">В примере проекта сначала получается значение `AZURE_AUTH_LOCATION`, а затем вызывается метод, возвращающий инициализированный клиентский объект `IAzure`.</span><span class="sxs-lookup"><span data-stu-id="2902f-123">The example project first obtains the `AZURE_AUTH_LOCATION` value, then calls a method that returns an initialized `IAzure` client object:</span></span>

<span data-ttu-id="2902f-124"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span><span class="sxs-lookup"><span data-stu-id="2902f-124"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span></span>

<span data-ttu-id="2902f-125">Этот метод из примера приложения возвращает инициализированный экземпляр [IAzure][iazure], который затем передается в первом параметре во все другие методы в примере.</span><span class="sxs-lookup"><span data-stu-id="2902f-125">This method from the sample application returns the initialized [IAzure][iazure] instance, which is then passed as the first parameter to all other methods in the sample:</span></span>

<span data-ttu-id="2902f-126"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span><span class="sxs-lookup"><span data-stu-id="2902f-126"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span></span>

<span data-ttu-id="2902f-127">Дополнительные сведения о доступных способах аутентификации в библиотеках управления .NET для Azure см. в [этой статье][sdk-auth].</span><span class="sxs-lookup"><span data-stu-id="2902f-127">For more details about the available authentication methods in the .NET management libraries for Azure, see [Authentication in Azure Management Libraries for .NET][sdk-auth].</span></span>

## <a name="create-container-group---single-container"></a><span data-ttu-id="2902f-128">Создание группы контейнеров с одним контейнером</span><span class="sxs-lookup"><span data-stu-id="2902f-128">Create container group - single container</span></span>

<span data-ttu-id="2902f-129">В этом примере создается группа контейнеров с одним контейнером.</span><span class="sxs-lookup"><span data-stu-id="2902f-129">This example creates a container group with a single container.</span></span>

<span data-ttu-id="2902f-130"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span><span class="sxs-lookup"><span data-stu-id="2902f-130"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span></span>

## <a name="create-container-group---multiple-containers"></a><span data-ttu-id="2902f-131">Создание группы контейнеров с несколькими контейнерами</span><span class="sxs-lookup"><span data-stu-id="2902f-131">Create container group - multiple containers</span></span>

<span data-ttu-id="2902f-132">В этом примере создается группа контейнеров с двумя контейнерами: контейнером приложения и контейнером расширения.</span><span class="sxs-lookup"><span data-stu-id="2902f-132">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<span data-ttu-id="2902f-133"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span><span class="sxs-lookup"><span data-stu-id="2902f-133"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span></span>

## <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="2902f-134">Асинхронное создание контейнера с использованием опроса</span><span class="sxs-lookup"><span data-stu-id="2902f-134">Asynchronous container create with polling</span></span>

<span data-ttu-id="2902f-135">В этом примере создается группа контейнеров с одним контейнером с использованием метода асинхронного создания.</span><span class="sxs-lookup"><span data-stu-id="2902f-135">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="2902f-136">Затем опрашивается служба Azure на наличие группы контейнеров и выводятся сведения о состоянии группы контейнеров, пока оно имеет значение "Running".</span><span class="sxs-lookup"><span data-stu-id="2902f-136">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<span data-ttu-id="2902f-137"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span><span class="sxs-lookup"><span data-stu-id="2902f-137"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span></span>

## <a name="create-task-based-container-group"></a><span data-ttu-id="2902f-138">Создание группы контейнеров на основе задач</span><span class="sxs-lookup"><span data-stu-id="2902f-138">Create task-based container group</span></span>

<span data-ttu-id="2902f-139">В этом примере создается группа контейнеров с одним контейнером на основе задач.</span><span class="sxs-lookup"><span data-stu-id="2902f-139">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="2902f-140">Для контейнера настраивается [пользовательская командная строка](/azure/container-instances/container-instances-restart-policy#command-line-override), для [политики перезапуска](/azure/container-instances/container-instances-restart-policy) устанавливается значение "Never".</span><span class="sxs-lookup"><span data-stu-id="2902f-140">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="2902f-141">Чтобы выполнить одну команду с несколькими аргументами командной строки, например `echo FOO BAR`, укажите их в качестве массива строк для метода `WithStartingCommandLines`.</span><span class="sxs-lookup"><span data-stu-id="2902f-141">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="2902f-142">Например: </span><span class="sxs-lookup"><span data-stu-id="2902f-142">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="2902f-143">Если нужно использовать несколько команд (возможно) с несколькими аргументами, выполните сценарий оболочки и передайте связанные команды в виде аргумента.</span><span class="sxs-lookup"><span data-stu-id="2902f-143">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="2902f-144">Например, в этом случае выполняются команды `echo` и `tail`:</span><span class="sxs-lookup"><span data-stu-id="2902f-144">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<span data-ttu-id="2902f-145"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span><span class="sxs-lookup"><span data-stu-id="2902f-145"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span></span>

## <a name="list-container-groups"></a><span data-ttu-id="2902f-146">Получение списка групп контейнеров</span><span class="sxs-lookup"><span data-stu-id="2902f-146">List container groups</span></span>

<span data-ttu-id="2902f-147">В этом примере выводится список групп контейнеров в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="2902f-147">This example lists the container groups in a resource group.</span></span>

<span data-ttu-id="2902f-148"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span><span class="sxs-lookup"><span data-stu-id="2902f-148"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span></span>

## <a name="get-an-existing-container-group"></a><span data-ttu-id="2902f-149">Получение сведений о существующей группе контейнеров</span><span class="sxs-lookup"><span data-stu-id="2902f-149">Get an existing container group</span></span>

<span data-ttu-id="2902f-150">В этом примере возвращаются данные определенной группы контейнеров в группе ресурсов и выводятся некоторые свойства группы контейнеров, а также их значения.</span><span class="sxs-lookup"><span data-stu-id="2902f-150">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<span data-ttu-id="2902f-151"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span><span class="sxs-lookup"><span data-stu-id="2902f-151"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span></span>

## <a name="delete-a-container-group"></a><span data-ttu-id="2902f-152">Удаление группы контейнеров</span><span class="sxs-lookup"><span data-stu-id="2902f-152">Delete a container group</span></span>

<span data-ttu-id="2902f-153">В этом примере группа контейнеров удаляется из группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="2902f-153">This example deletes a container group from a resource group.</span></span>

<span data-ttu-id="2902f-154"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span><span class="sxs-lookup"><span data-stu-id="2902f-154"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span></span>

## <a name="api-reference"></a><span data-ttu-id="2902f-155">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="2902f-155">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2902f-156">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="2902f-156">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="2902f-157">Примеры</span><span class="sxs-lookup"><span data-stu-id="2902f-157">Samples</span></span>

* <span data-ttu-id="2902f-158">Исходный код для приведенных выше примеров можно найти на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="2902f-158">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="2902f-159">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="2902f-159">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="2902f-160">Дополнительные примеры кода для службы "Экземпляры контейнеров Azure":</span><span class="sxs-lookup"><span data-stu-id="2902f-160">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="2902f-161">[Примеры кода Azure][samples]</span><span class="sxs-lookup"><span data-stu-id="2902f-161">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="2902f-162">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="2902f-162">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

<!-- LINKS - External -->
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[sdk-auth]: https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md

<!-- LINKS - Internal -->
[DotNetCLI]: /dotnet/core/tools/dotnet-add-package
[PackageManager]: /nuget/tools/package-manager-console
[iazure]: /dotnet/api/microsoft.azure.management.fluent.azure
[iazure-authenticate]: /dotnet/api/microsoft.azure.management.fluent.azure.authenticate
