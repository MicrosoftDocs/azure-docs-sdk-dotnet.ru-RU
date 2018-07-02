---
title: Библиотеки служб резервного копирования и восстановления Azure для .NET
description: Справочник по библиотекам служб резервного копирования и восстановления Azure для .NET
keywords: Azure, .NET, SDK, API, Recovery Services, Backup
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: recovery-services
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 6186411b668d0950328b49bb826e5b05c5ee0304
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065434"
---
# <a name="azure-recovery-services-and-backup-libraries-for-net"></a>Библиотеки служб резервного копирования и восстановления Azure для .NET

## <a name="overview"></a>Обзор

Службы восстановления Azure — это набор служб для восстановления данных, который включает [Azure Backup](/azure/backup/) и [Azure Site Recovery](/azure/site-recovery/).

## <a name="management-library"></a>Библиотека управления

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/recoveryservices/management)


## <a name="code-example"></a>Пример кода

В примере кода ниже библиотека управления используется для активации резервного копирования.

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
