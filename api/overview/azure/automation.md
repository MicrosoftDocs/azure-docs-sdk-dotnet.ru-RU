---
title: Библиотеки службы автоматизации Azure для .NET
description: Справочник по библиотекам службы автоматизации Azure для .NET
keywords: Azure, .NET, SDK, API, Automation
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: automation
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e45db49fa71e5ad16ab1e4f26d76cd9b0146ac5f
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065764"
---
# <a name="azure-automation-libraries-for-net"></a><span data-ttu-id="1c76d-104">Библиотеки службы автоматизации Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="1c76d-104">Azure Automation libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="1c76d-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="1c76d-105">Overview</span></span>

<span data-ttu-id="1c76d-106">Служба автоматизации Microsoft Azure позволяет пользователям автоматизировать стандартные задачи, которые выполняются в облачной среде и среде предприятия.</span><span class="sxs-lookup"><span data-stu-id="1c76d-106">Microsoft Azure Automation provides a way for users to automate the tasks that are commonly performed in a cloud and enterprise environment.</span></span> 

<span data-ttu-id="1c76d-107">Дополнительные сведения см. в статье [Обзор службы автоматизации Azure](/azure/automation/automation-intro).</span><span class="sxs-lookup"><span data-stu-id="1c76d-107">Learn more by reading the [Azure Automation Overview](/azure/automation/automation-intro).</span></span>

## <a name="management-library"></a><span data-ttu-id="1c76d-108">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="1c76d-108">Management library</span></span>

<span data-ttu-id="1c76d-109">Использование библиотеки управления для управления модулями Runbook, заданиями и параметрами настройки требуемого состояния.</span><span class="sxs-lookup"><span data-stu-id="1c76d-109">Using the management library to manage runbooks and jobs and manage Desired State Configuration settings.</span></span>

<span data-ttu-id="1c76d-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="1c76d-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1c76d-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1c76d-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Automation
```

```bash
dotnet add package Microsoft.Azure.Management.Automation
```

### <a name="code-example"></a><span data-ttu-id="1c76d-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="1c76d-112">Code Example</span></span>

<span data-ttu-id="1c76d-113">В примере ниже показано, как запустить новое задание на основе существующего модуля Runbook.</span><span class="sxs-lookup"><span data-stu-id="1c76d-113">The following example illustrates how to start a new job based on an existing runbook.</span></span>

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
> [<span data-ttu-id="1c76d-114">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="1c76d-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/automation/management)

## <a name="samples"></a><span data-ttu-id="1c76d-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="1c76d-115">Samples</span></span>

* <span data-ttu-id="1c76d-116">[AzureBot](https://github.com/Microsoft/AzureBot) использует библиотеку службы автоматизации с [Bot Framework](https://docs.microsoft.com/bot-framework/) и [Cognitive Services](/cognitive-services), чтобы повысить производительность разработки в Azure.</span><span class="sxs-lookup"><span data-stu-id="1c76d-116">[AzureBot](https://github.com/Microsoft/AzureBot) uses the automation library with the [Bot Framework](https://docs.microsoft.com/bot-framework/) and [Cognitive Services](/cognitive-services) to improve developer productivity on Azure</span></span>

<span data-ttu-id="1c76d-117">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="1c76d-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
