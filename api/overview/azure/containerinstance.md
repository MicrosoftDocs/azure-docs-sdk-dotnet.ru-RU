---
title: Библиотеки службы "Экземпляры контейнеров Azure" для .NET
description: Справочник по библиотекам службы "Экземпляры контейнеров Azure" для .NET
ms.date: 06/11/2018
ms.topic: reference
ms.service: dcontainer-instances
ms.openlocfilehash: 93f537058e0ed11f51cc6cb6cece01da80559822
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190727"
---
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="e8025-103">Библиотеки службы "Экземпляры контейнеров Azure" для .NET</span><span class="sxs-lookup"><span data-stu-id="e8025-103">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="e8025-104">Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки службы "Экземпляры контейнеров Azure" для .NET.</span><span class="sxs-lookup"><span data-stu-id="e8025-104">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="e8025-105">Дополнительные сведения см. в статье [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-overview).</span><span class="sxs-lookup"><span data-stu-id="e8025-105">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="e8025-106">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="e8025-106">Management library</span></span>

<span data-ttu-id="e8025-107">Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки управления.</span><span class="sxs-lookup"><span data-stu-id="e8025-107">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="e8025-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="e8025-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="e8025-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e8025-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="example-source"></a><span data-ttu-id="e8025-110">Пример исходного кода</span><span class="sxs-lookup"><span data-stu-id="e8025-110">Example source</span></span>

<span data-ttu-id="e8025-111">Чтобы просмотреть приведенные ниже примеры кода в контексте, перейдите к следующему репозиторию GitHub:</span><span class="sxs-lookup"><span data-stu-id="e8025-111">If you'd like to see the following code examples in context, you can find them in the following GitHub repository:</span></span>

[<span data-ttu-id="e8025-112">Azure-Samples/aci-docs-sample-dotnet</span><span class="sxs-lookup"><span data-stu-id="e8025-112">Azure-Samples/aci-docs-sample-dotnet</span></span>](https://github.com/Azure-Samples/aci-docs-sample-dotnet)

## <a name="authentication"></a><span data-ttu-id="e8025-113">Authentication</span><span class="sxs-lookup"><span data-stu-id="e8025-113">Authentication</span></span>

<span data-ttu-id="e8025-114">[Аутентификация с использованием файла][sdk-auth] — самый простой способ аутентификации клиентов SDK.</span><span class="sxs-lookup"><span data-stu-id="e8025-114">One of the easiest ways to authenticate SDK clients is with [file-based authentication][sdk-auth].</span></span> <span data-ttu-id="e8025-115">Во время создания экземпляра клиентского объекта [IAzure][iazure] функция файловой аутентификации анализирует файл учетных данных, после чего объект использует эти учетные данные для аутентификации в Azure.</span><span class="sxs-lookup"><span data-stu-id="e8025-115">File-based authentication parses a credentials file when instantiating the [IAzure][iazure] client object, which then uses those credentials when authenticating with Azure.</span></span> <span data-ttu-id="e8025-116">Использование аутентификации на основе файла</span><span class="sxs-lookup"><span data-stu-id="e8025-116">To use file-based authentication:</span></span>

1. <span data-ttu-id="e8025-117">Создайте файл учетных данных с помощью [Azure CLI](/cli/azure) или [Cloud Shell](https://shell.azure.com/):</span><span class="sxs-lookup"><span data-stu-id="e8025-117">Create a credentials file with the [Azure CLI](/cli/azure) or [Cloud Shell](https://shell.azure.com/):</span></span>

   `az ad sp create-for-rbac --sdk-auth > my.azureauth`

   <span data-ttu-id="e8025-118">Если файл учетных данных создается с помощью [Cloud Shell](https://shell.azure.com/), скопируйте содержимое этого файла в локальный файл, к которому у приложения .NET есть доступ.</span><span class="sxs-lookup"><span data-stu-id="e8025-118">If you use the [Cloud Shell](https://shell.azure.com/) to generate the credentials file, copy its contents into a local file that your .NET application can access.</span></span>

2. <span data-ttu-id="e8025-119">Задайте для переменной среды `AZURE_AUTH_LOCATION` полный путь к созданному файлу учетных данных.</span><span class="sxs-lookup"><span data-stu-id="e8025-119">Set the `AZURE_AUTH_LOCATION` environment variable to the full path of the generated credentials file.</span></span> <span data-ttu-id="e8025-120">Например (оболочка Bash):</span><span class="sxs-lookup"><span data-stu-id="e8025-120">For example (in the Bash shell):</span></span>

   ```bash
   export AZURE_AUTH_LOCATION=/home/yourusername/my.azureauth
   ```

<span data-ttu-id="e8025-121">Создав файл учетных данных и указав значение для переменной среды `AZURE_AUTH_LOCATION`, инициализируйте клиентский объект [IAzure][iazure] с помощью метода [Azure.Authenticate][iazure-authenticate].</span><span class="sxs-lookup"><span data-stu-id="e8025-121">Once you've created the credentials file and populated the `AZURE_AUTH_LOCATION` environment variable, use the [Azure.Authenticate][iazure-authenticate] method to initialize the [IAzure][iazure] client object.</span></span> <span data-ttu-id="e8025-122">В примере проекта сначала получается значение `AZURE_AUTH_LOCATION`, а затем вызывается метод, возвращающий инициализированный клиентский объект `IAzure`.</span><span class="sxs-lookup"><span data-stu-id="e8025-122">The example project first obtains the `AZURE_AUTH_LOCATION` value, then calls a method that returns an initialized `IAzure` client object:</span></span>

<span data-ttu-id="e8025-123"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span><span class="sxs-lookup"><span data-stu-id="e8025-123"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span></span>

<span data-ttu-id="e8025-124">Этот метод из примера приложения возвращает инициализированный экземпляр [IAzure][iazure], который затем передается в первом параметре во все другие методы в примере.</span><span class="sxs-lookup"><span data-stu-id="e8025-124">This method from the sample application returns the initialized [IAzure][iazure] instance, which is then passed as the first parameter to all other methods in the sample:</span></span>

<span data-ttu-id="e8025-125"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span><span class="sxs-lookup"><span data-stu-id="e8025-125"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span></span>

<span data-ttu-id="e8025-126">Дополнительные сведения о доступных способах аутентификации в библиотеках управления .NET для Azure см. в [этой статье][sdk-auth].</span><span class="sxs-lookup"><span data-stu-id="e8025-126">For more details about the available authentication methods in the .NET management libraries for Azure, see [Authentication in Azure Management Libraries for .NET][sdk-auth].</span></span>

## <a name="create-container-group---single-container"></a><span data-ttu-id="e8025-127">Создание группы контейнеров с одним контейнером</span><span class="sxs-lookup"><span data-stu-id="e8025-127">Create container group - single container</span></span>

<span data-ttu-id="e8025-128">В этом примере создается группа контейнеров с одним контейнером.</span><span class="sxs-lookup"><span data-stu-id="e8025-128">This example creates a container group with a single container.</span></span>

<span data-ttu-id="e8025-129"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span><span class="sxs-lookup"><span data-stu-id="e8025-129"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span></span>

## <a name="create-container-group---multiple-containers"></a><span data-ttu-id="e8025-130">Создание группы контейнеров с несколькими контейнерами</span><span class="sxs-lookup"><span data-stu-id="e8025-130">Create container group - multiple containers</span></span>

<span data-ttu-id="e8025-131">В этом примере создается группа контейнеров с двумя контейнерами: контейнером приложения и контейнером расширения.</span><span class="sxs-lookup"><span data-stu-id="e8025-131">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<span data-ttu-id="e8025-132"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span><span class="sxs-lookup"><span data-stu-id="e8025-132"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span></span>

## <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="e8025-133">Асинхронное создание контейнера с использованием опроса</span><span class="sxs-lookup"><span data-stu-id="e8025-133">Asynchronous container create with polling</span></span>

<span data-ttu-id="e8025-134">В этом примере создается группа контейнеров с одним контейнером с использованием метода асинхронного создания.</span><span class="sxs-lookup"><span data-stu-id="e8025-134">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="e8025-135">Затем опрашивается служба Azure на наличие группы контейнеров и выводятся сведения о состоянии группы контейнеров, пока оно имеет значение "Running".</span><span class="sxs-lookup"><span data-stu-id="e8025-135">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<span data-ttu-id="e8025-136"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span><span class="sxs-lookup"><span data-stu-id="e8025-136"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span></span>

## <a name="create-task-based-container-group"></a><span data-ttu-id="e8025-137">Создание группы контейнеров на основе задач</span><span class="sxs-lookup"><span data-stu-id="e8025-137">Create task-based container group</span></span>

<span data-ttu-id="e8025-138">В этом примере создается группа контейнеров с одним контейнером на основе задач.</span><span class="sxs-lookup"><span data-stu-id="e8025-138">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="e8025-139">Для контейнера настраивается [пользовательская командная строка](/azure/container-instances/container-instances-restart-policy#command-line-override), для [политики перезапуска](/azure/container-instances/container-instances-restart-policy) устанавливается значение "Never".</span><span class="sxs-lookup"><span data-stu-id="e8025-139">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="e8025-140">Чтобы выполнить одну команду с несколькими аргументами командной строки, например `echo FOO BAR`, укажите их в качестве массива строк для метода `WithStartingCommandLines`.</span><span class="sxs-lookup"><span data-stu-id="e8025-140">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="e8025-141">Например: </span><span class="sxs-lookup"><span data-stu-id="e8025-141">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="e8025-142">Если нужно использовать несколько команд (возможно) с несколькими аргументами, выполните сценарий оболочки и передайте связанные команды в виде аргумента.</span><span class="sxs-lookup"><span data-stu-id="e8025-142">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="e8025-143">Например, в этом случае выполняются команды `echo` и `tail`:</span><span class="sxs-lookup"><span data-stu-id="e8025-143">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<span data-ttu-id="e8025-144"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span><span class="sxs-lookup"><span data-stu-id="e8025-144"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span></span>

## <a name="list-container-groups"></a><span data-ttu-id="e8025-145">Получение списка групп контейнеров</span><span class="sxs-lookup"><span data-stu-id="e8025-145">List container groups</span></span>

<span data-ttu-id="e8025-146">В этом примере выводится список групп контейнеров в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e8025-146">This example lists the container groups in a resource group.</span></span>

<span data-ttu-id="e8025-147"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span><span class="sxs-lookup"><span data-stu-id="e8025-147"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span></span>

## <a name="get-an-existing-container-group"></a><span data-ttu-id="e8025-148">Получение сведений о существующей группе контейнеров</span><span class="sxs-lookup"><span data-stu-id="e8025-148">Get an existing container group</span></span>

<span data-ttu-id="e8025-149">В этом примере возвращаются данные определенной группы контейнеров в группе ресурсов и выводятся некоторые свойства группы контейнеров, а также их значения.</span><span class="sxs-lookup"><span data-stu-id="e8025-149">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<span data-ttu-id="e8025-150"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span><span class="sxs-lookup"><span data-stu-id="e8025-150"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span></span>

## <a name="delete-a-container-group"></a><span data-ttu-id="e8025-151">Удаление группы контейнеров</span><span class="sxs-lookup"><span data-stu-id="e8025-151">Delete a container group</span></span>

<span data-ttu-id="e8025-152">В этом примере группа контейнеров удаляется из группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e8025-152">This example deletes a container group from a resource group.</span></span>

<span data-ttu-id="e8025-153"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span><span class="sxs-lookup"><span data-stu-id="e8025-153"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span></span>

## <a name="api-reference"></a><span data-ttu-id="e8025-154">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="e8025-154">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8025-155">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="e8025-155">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="e8025-156">Примеры</span><span class="sxs-lookup"><span data-stu-id="e8025-156">Samples</span></span>

* <span data-ttu-id="e8025-157">Исходный код для приведенных выше примеров можно найти на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="e8025-157">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="e8025-158">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="e8025-158">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="e8025-159">Дополнительные примеры кода для службы "Экземпляры контейнеров Azure":</span><span class="sxs-lookup"><span data-stu-id="e8025-159">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="e8025-160">[Примеры кода Azure][samples]</span><span class="sxs-lookup"><span data-stu-id="e8025-160">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="e8025-161">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="e8025-161">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

<!-- LINKS - External -->
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[sdk-auth]: https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md

<!-- LINKS - Internal -->
[DotNetCLI]: /dotnet/core/tools/dotnet-add-package
[PackageManager]: /nuget/tools/package-manager-console
[iazure]: /dotnet/api/microsoft.azure.management.fluent.azure
[iazure-authenticate]: /dotnet/api/microsoft.azure.management.fluent.azure.authenticate
