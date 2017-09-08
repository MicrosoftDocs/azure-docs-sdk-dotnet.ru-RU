---
title: "Библиотеки Power BI Embedded для .NET"
description: "Справочник по библиотекам Power BI Embedded для .NET"
keywords: Azure, .NET, SDK, API, Power BI Embedded
author: camsoper
ms.author: casoper
manager: douge
ms.date: 08/07/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: f9a6aac8dbb3c284948e9140ad87aff5e415d9fb
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="power-bi-embedded-libraries-for-net"></a><span data-ttu-id="dfc80-104">Библиотеки Power BI Embedded для .NET</span><span class="sxs-lookup"><span data-stu-id="dfc80-104">Power BI Embedded libraries for .NET</span></span>

<span data-ttu-id="dfc80-105">[Power BI](https://powerbi.microsoft.com/) — это облачная служба бизнес-аналитики, которая обеспечивает единое представление наиболее важных бизнес-данных.</span><span class="sxs-lookup"><span data-stu-id="dfc80-105">[Power BI](https://powerbi.microsoft.com/) is a cloud-based business analytics service that gives you a single view of your most critical business data.</span></span>

<span data-ttu-id="dfc80-106">Дополнительные сведения об использовании Power BI с .NET см. в статье [Внедрение в Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="dfc80-106">To learn more about using Power BI with .NET, see [Embedding with Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).</span></span>

## <a name="client-library"></a><span data-ttu-id="dfc80-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="dfc80-107">Client library</span></span>

<span data-ttu-id="dfc80-108">Клиентская библиотека используется для подключения к API Power BI, чтобы обеспечить доступ к наборам данных и отчетам и взаимодействие с ними.</span><span class="sxs-lookup"><span data-stu-id="dfc80-108">Use the client library to connect with Power BI APIs to access and interact with data sets and reports.</span></span>

<span data-ttu-id="dfc80-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.PowerBI.Api) непосредственно из [консоли диспетчера пакетов][PackageManager].</span><span class="sxs-lookup"><span data-stu-id="dfc80-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.PowerBI.Api) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="dfc80-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dfc80-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.PowerBI.Api
```

### <a name="example"></a><span data-ttu-id="dfc80-111">Пример</span><span class="sxs-lookup"><span data-stu-id="dfc80-111">Example</span></span>

<span data-ttu-id="dfc80-112">В примере ниже извлекается и отображается список наборов данных и отчетов.</span><span class="sxs-lookup"><span data-stu-id="dfc80-112">The following example retrieves and displays a list of datasets and reports.</span></span>

```csharp
/* Include these'using' directive:
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;
*/
using (PowerBIClient client = new PowerBIClient(new Uri(apiUrl), tokenCredentials))
{

    Console.WriteLine("\r*** DATASETS ***\r");

    // List of datasets in a group/app workspace
    ODataResponseListDataset datasetList = client.Datasets.GetDatasetsInGroup(groupId);

    foreach(Dataset ds in datasetList.Value)
    {
        Console.WriteLine(ds.Id + " | " + ds.Name);
    }

    Console.WriteLine("\r*** REPORTS ***\r");

    // List of reports in a group/app workspace
    ODataResponseListReport reportList = client.Reports.GetReportsInGroup(groupId);

    foreach (Report rpt in reportList.Value)
    {
        Console.WriteLine(rpt.Id + " | " + rpt.Name +  " | DatasetID = " + rpt.DatasetId);
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="dfc80-113">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="dfc80-113">Explore the client APIs</span></span>](https://powerbi.microsoft.com/documentation/powerbi-developer-rest-api-reference/)

## <a name="samples"></a><span data-ttu-id="dfc80-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="dfc80-114">Samples</span></span>

* [<span data-ttu-id="dfc80-115">Примеры разработки в Power BI</span><span class="sxs-lookup"><span data-stu-id="dfc80-115">Power BI Developer Samples</span></span>](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [<span data-ttu-id="dfc80-116">Репозиторий GitHub для Power BI .NET</span><span class="sxs-lookup"><span data-stu-id="dfc80-116">Power BI .NET GitHub repo</span></span>](https://github.com/Microsoft/PowerBI-CSharp)

<span data-ttu-id="dfc80-117">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="dfc80-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
