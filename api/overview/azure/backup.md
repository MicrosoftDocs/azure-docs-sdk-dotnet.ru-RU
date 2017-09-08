---
title: "Библиотеки службы Azure Backup для .NET"
description: "Справочник по библиотекам службы Azure Backup для .NET"
keywords: Azure, .NET, SDK, API, Backup
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/24/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 93eeaeda1860e3b7190dfb0ae917b4b85b5a3609
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-backup-libraries-for-net"></a><span data-ttu-id="0dc9e-104">Библиотеки службы Azure Backup для .NET</span><span class="sxs-lookup"><span data-stu-id="0dc9e-104">Azure Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="0dc9e-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="0dc9e-105">Overview</span></span>

<span data-ttu-id="0dc9e-106">Служба Azure Backup — это облачная служба для резервного копирования, защиты и восстановления данных.</span><span class="sxs-lookup"><span data-stu-id="0dc9e-106">Azure Backup is the cloud service you can use to back up, protect, and restore your data.</span></span>

<span data-ttu-id="0dc9e-107">Дополнительные сведения о службе Azure Backup см. в статье [Общие сведения о возможностях в службе архивации Azure](/azure/backup/backup-introduction-to-azure-backup).</span><span class="sxs-lookup"><span data-stu-id="0dc9e-107">Learn more about Azure Backup by reading [What is Azure Backup?](/azure/backup/backup-introduction-to-azure-backup).</span></span>

## <a name="management-library"></a><span data-ttu-id="0dc9e-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="0dc9e-108">Management library</span></span>

<span data-ttu-id="0dc9e-109">Библиотека управления резервным копированием предназначена для управления резервными копиями и настройки хранилищ для служб восстановления.</span><span class="sxs-lookup"><span data-stu-id="0dc9e-109">Use the backup management library to manage backups and set up Recovery Services vaults.</span></span>

<span data-ttu-id="0dc9e-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="0dc9e-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="0dc9e-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0dc9e-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

<span data-ttu-id="0dc9e-112">В примере кода ниже библиотека управления используется для активации резервного копирования.</span><span class="sxs-lookup"><span data-stu-id="0dc9e-112">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="0dc9e-113">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="0dc9e-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/backup/management)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
