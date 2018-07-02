---
title: Библиотеки Power BI Embedded для .NET
description: Справочник по библиотекам Power BI Embedded для .NET
keywords: Azure, .NET, SDK, API, Power BI Embedded
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 3e28525f61ca8b4f8347b7a7e8994f9e479749ea
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065964"
---
# <a name="power-bi-embedded-libraries-for-net"></a>Библиотеки Power BI Embedded для .NET

[Power BI](https://powerbi.microsoft.com/) — это облачная служба бизнес-аналитики, которая обеспечивает единое представление наиболее важных бизнес-данных.

Дополнительные сведения об использовании Power BI с .NET см. в статье [Внедрение в Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).

## <a name="client-library"></a>Клиентская библиотека

Клиентская библиотека используется для подключения к API Power BI, чтобы обеспечить доступ к наборам данных и отчетам и взаимодействие с ними.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.PowerBI.Api) непосредственно из [консоли диспетчера пакетов][PackageManager].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.PowerBI.Api
```

### <a name="example"></a>Пример

В примере ниже извлекается и отображается список наборов данных и отчетов.

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
> [Обзор клиентских API-интерфейсов](https://powerbi.microsoft.com/documentation/powerbi-developer-rest-api-reference/)

## <a name="samples"></a>Примеры

* [Примеры разработки в Power BI](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [Репозиторий GitHub для Power BI .NET](https://github.com/Microsoft/PowerBI-CSharp)

Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
