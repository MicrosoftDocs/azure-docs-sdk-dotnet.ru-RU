---
title: Библиотеки службы автоматизации Azure для .NET
description: Справочник по библиотекам службы автоматизации Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: automation
ms.openlocfilehash: 4890faab86d1319fe802a30e3735419ac65e8d64
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190287"
---
# <a name="azure-automation-libraries-for-net"></a>Библиотеки службы автоматизации Azure для .NET

## <a name="overview"></a>Обзор

Служба автоматизации Microsoft Azure позволяет пользователям автоматизировать стандартные задачи, которые выполняются в облачной среде и среде предприятия. 

Дополнительные сведения см. в статье [Обзор службы автоматизации Azure](/azure/automation/automation-intro).

## <a name="management-library"></a>Библиотека управления

Использование библиотеки управления для управления модулями Runbook, заданиями и параметрами настройки требуемого состояния.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Automation
```

```bash
dotnet add package Microsoft.Azure.Management.Automation
```

### <a name="code-example"></a>Пример кода

В примере ниже показано, как запустить новое задание на основе существующего модуля Runbook.

```csharp
/*
  using Microsoft.Azure.Management.Automation;
*/
AutomationManagementClient client =
    new AutomationManagementClient(new CertificateCloudCredentials(subscriptionId, cert));

// Create job create parameters
JobCreateParameters jcParam = new JobCreateParameters
{
    Properties = new JobCreateProperties
    {
        Runbook = new RunbookAssociationProperty
        {
            Name = runbookName
        },
        Parameters = null // optional parameters here
    }
};

// create runbook job. This gives back the Job
Job job = automationManagementClient.Jobs.Create(automationAccountName, jcParam).Job;
```

> [!div class="nextstepaction"]
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/automation/management)

## <a name="samples"></a>Примеры

* [AzureBot](https://github.com/Microsoft/AzureBot) использует библиотеку службы автоматизации с [Bot Framework](https://docs.microsoft.com/bot-framework/) и [Cognitive Services](/cognitive-services), чтобы повысить производительность разработки в Azure.

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
