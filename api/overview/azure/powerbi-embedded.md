---
title: Библиотеки Power BI Embedded для .NET
description: Справочник по библиотекам Power BI Embedded для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: acb327b56e89522142e51016a6a9b279f995a674
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190377"
---
# <a name="power-bi-embedded-libraries-for-net"></a><span data-ttu-id="9875f-103">Библиотеки Power BI Embedded для .NET</span><span class="sxs-lookup"><span data-stu-id="9875f-103">Power BI Embedded libraries for .NET</span></span>

<span data-ttu-id="9875f-104">[Power BI](https://powerbi.microsoft.com/) — это облачная служба бизнес-аналитики, которая обеспечивает единое представление наиболее важных бизнес-данных.</span><span class="sxs-lookup"><span data-stu-id="9875f-104">[Power BI](https://powerbi.microsoft.com/) is a cloud-based business analytics service that gives you a single view of your most critical business data.</span></span>

<span data-ttu-id="9875f-105">Дополнительные сведения об использовании Power BI с .NET см. в статье [Внедрение в Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="9875f-105">To learn more about using Power BI with .NET, see [Embedding with Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).</span></span>

## <a name="client-library"></a><span data-ttu-id="9875f-106">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="9875f-106">Client library</span></span>

<span data-ttu-id="9875f-107">Клиентская библиотека используется для подключения к API Power BI, чтобы обеспечить доступ к наборам данных и отчетам и взаимодействие с ними.</span><span class="sxs-lookup"><span data-stu-id="9875f-107">Use the client library to connect with Power BI APIs to access and interact with data sets and reports.</span></span>

<span data-ttu-id="9875f-108">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.PowerBI.Api) непосредственно из [консоли диспетчера пакетов][PackageManager].</span><span class="sxs-lookup"><span data-stu-id="9875f-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.PowerBI.Api) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9875f-109">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9875f-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.PowerBI.Api
```

### <a name="example"></a><span data-ttu-id="9875f-110">Пример</span><span class="sxs-lookup"><span data-stu-id="9875f-110">Example</span></span>

<span data-ttu-id="9875f-111">В примере ниже извлекается и отображается список наборов данных и отчетов.</span><span class="sxs-lookup"><span data-stu-id="9875f-111">The following example retrieves and displays a list of datasets and reports.</span></span>

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
> [<span data-ttu-id="9875f-112">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="9875f-112">Explore the client APIs</span></span>](https://powerbi.microsoft.com/documentation/powerbi-developer-rest-api-reference/)

## <a name="samples"></a><span data-ttu-id="9875f-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="9875f-113">Samples</span></span>

* [<span data-ttu-id="9875f-114">Примеры разработки в Power BI</span><span class="sxs-lookup"><span data-stu-id="9875f-114">Power BI Developer Samples</span></span>](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [<span data-ttu-id="9875f-115">Репозиторий GitHub для Power BI .NET</span><span class="sxs-lookup"><span data-stu-id="9875f-115">Power BI .NET GitHub repo</span></span>](https://github.com/Microsoft/PowerBI-CSharp)

<span data-ttu-id="9875f-116">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="9875f-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
