---
title: API Azure .NET
description: Общие сведения об API Azure для .NET
keywords: Azure, .NET, SDK, API, NuGet, libraries, packages
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 26360a516220ca9d3e8901e60cb23ecbd02863cd
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
ms.locfileid: "29752696"
---
# <a name="azure-net-apis"></a>API Azure .NET

API Azure для .NET позволяют использовать службы Azure и управлять ресурсами Azure из кода приложения. API доступны в виде [пакетов NuGet](/dotnet/api/overview/azure/) для использования в проектах .NET. 

## <a name="manage-azure-resources"></a>Управление ресурсами Azure

Используя библиотеки Azure для .NET, можно создавать и администрировать ресурсы Azure из приложений .NET.

Многие пакеты для управления ресурсами Azure имеют [текучий](dotnet-sdk-azure-concepts.md) интерфейс для настройки ресурсов в соответствии с требованиями. Например, для создания виртуальной машины Windows можно написать следующий код:

```csharp
var windowsVM = azure.VirtualMachines.Define(windowsVmName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername(username)
    .WithAdminPassword(password)
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
 ```

См. [список служб .NET](/dotnet/api/overview/azure/), чтобы начать использовать библиотеки с проектами. Затем см. [статью с инструкциями по началу работы](dotnet-sdk-azure-get-started.md), чтобы настроить аутентификацию и запустить пример кода в своей подписке Azure.  [Статья с основными понятиями](dotnet-sdk-azure-concepts.md) содержит соглашения, которые использует пакет SDK, и объясняет, как их использовать, чтобы упростить код приложения. Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу см. в [заметках о выпуске](dotnet-sdk-azure-release-notes.md).

## <a name="consume-azure-services"></a>Использование служб Azure

Вы можете использовать API .NET не только для создания ресурсов в Azure и программного управления ими, но и для подключения приложений к этим ресурсам и использования в среде выполнения.  Например, вы можете подключиться к базе данных или хранилищу данных SQL в службе хранилища Azure.  Чтобы определить, какой пакет NuGet следует использовать для конкретной службы Azure, см. [полный список API служб](/dotnet/api/overview/azure/).  

## <a name="samples"></a>Примеры

Приведенные ниже примеры охватывают общие задачи автоматизации с помощью библиотек Azure для .NET:

- [Виртуальные машины](dotnet-sdk-azure-virtual-machine-samples.md)
- [Веб-приложения](dotnet-sdk-azure-web-apps-samples.md)
- [База данных SQL](dotnet-sdk-azure-sql-database-samples.md)

См. унифицированный [справочник](/dotnet/api/overview/azure/?view=azure-dotnet) по всем пакетам в библиотеках служб и библиотеках управления. Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу см. в [заметках о выпуске](dotnet-sdk-azure-release-notes.md).

[!include[Contribute and community](includes/contribute.md)]