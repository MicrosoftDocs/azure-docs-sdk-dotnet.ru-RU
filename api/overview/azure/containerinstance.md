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
# <a name="azure-container-instances-libraries-for-net"></a>Библиотеки службы "Экземпляры контейнеров Azure" для .NET

Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки службы "Экземпляры контейнеров Azure" для .NET. Дополнительные сведения см. в статье [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-overview).

## <a name="management-library"></a>Библиотека управления

Создавайте и администрируйте экземпляры контейнеров Azure с помощью библиотеки управления.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="examples"></a>Примеры

### <a name="create-container-group---single-container"></a>Создание группы контейнеров с одним контейнером

В этом примере создается группа контейнеров с одним контейнером.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]

### <a name="create-container-group---multiple-containers"></a>Создание группы контейнеров с несколькими контейнерами

В этом примере создается группа контейнеров с двумя контейнерами: контейнером приложения и контейнером расширения.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]

### <a name="asynchronous-container-create-with-polling"></a>Асинхронное создание контейнера с использованием опроса

В этом примере создается группа контейнеров с одним контейнером с использованием метода асинхронного создания. Затем опрашивается служба Azure на наличие группы контейнеров и выводятся сведения о состоянии группы контейнеров, пока оно имеет значение "Running".

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]

### <a name="create-task-based-container-group"></a>Создание группы контейнеров на основе задач

В этом примере создается группа контейнеров с одним контейнером на основе задач. Для контейнера настраивается [пользовательская командная строка](/azure/container-instances/container-instances-restart-policy#command-line-override), для [политики перезапуска](/azure/container-instances/container-instances-restart-policy) устанавливается значение "Never".

Чтобы выполнить одну команду с несколькими аргументами командной строки, например `echo FOO BAR`, укажите их в качестве массива строк для метода `WithStartingCommandLines`. Например: 

`WithStartingCommandLines("echo", "FOO", "BAR")`

Если нужно использовать несколько команд (возможно) с несколькими аргументами, выполните сценарий оболочки и передайте связанные команды в виде аргумента. Например, в этом случае выполняются команды `echo` и `tail`:

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]

### <a name="list-container-groups"></a>Получение списка групп контейнеров

В этом примере выводится список групп контейнеров в группе ресурсов.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]

### <a name="get-an-existing-container-group"></a>Получение сведений о существующей группе контейнеров

В этом примере возвращаются данные определенной группы контейнеров в группе ресурсов и выводятся некоторые свойства группы контейнеров, а также их значения.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]

### <a name="delete-a-container-group"></a>Удаление группы контейнеров

В этом примере группа контейнеров удаляется из группы ресурсов.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]

## <a name="api-reference"></a>Справочник по API

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a>Примеры

* Исходный код для приведенных выше примеров можно найти на сайте GitHub:

  [Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]

* Дополнительные примеры кода для службы "Экземпляры контейнеров Azure":

  [Примеры кода Azure][samples]

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
