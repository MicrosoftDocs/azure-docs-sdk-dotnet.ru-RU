---
title: Библиотеки служб резервного копирования и восстановления Azure для .NET
description: Справочник по библиотекам служб резервного копирования и восстановления Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: recovery-services
ms.openlocfilehash: c0381ce9a566b5371faca24307edc7b26174e785
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190802"
---
# <a name="azure-recovery-services-and-backup-libraries-for-net"></a><span data-ttu-id="9b343-103">Библиотеки служб резервного копирования и восстановления Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="9b343-103">Azure Recovery Services and Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9b343-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="9b343-104">Overview</span></span>

<span data-ttu-id="9b343-105">Службы восстановления Azure — это набор служб для восстановления данных, который включает [Azure Backup](/azure/backup/) и [Azure Site Recovery](/azure/site-recovery/).</span><span class="sxs-lookup"><span data-stu-id="9b343-105">Azure Recovery Services is a suite of services for data recovery, including [Azure Backup](/azure/backup/) and [Azure Site Recovery](/azure/site-recovery/).</span></span>

## <a name="management-library"></a><span data-ttu-id="9b343-106">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="9b343-106">Management library</span></span>

<span data-ttu-id="9b343-107">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9b343-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9b343-108">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b343-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

#### <a name="net-core-cli"></a><span data-ttu-id="9b343-109">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9b343-109">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9b343-110">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="9b343-110">Explore the management APIs</span></span>](/dotnet/api/overview/azure/recoveryservices/management)


## <a name="code-example"></a><span data-ttu-id="9b343-111">Пример кода</span><span class="sxs-lookup"><span data-stu-id="9b343-111">Code Example</span></span>

<span data-ttu-id="9b343-112">В примере кода ниже библиотека управления используется для активации резервного копирования.</span><span class="sxs-lookup"><span data-stu-id="9b343-112">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
