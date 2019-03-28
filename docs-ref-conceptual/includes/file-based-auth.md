---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: 7f7c24957d2bc0574fc0b1bf2a8ae8fe8b4dfc64
ms.sourcegitcommit: e534dad2d96b72ab6a9bc4b5567508962bd7e05c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58343343"
---
<span data-ttu-id="9ff01-101">Создайте текстовый файл с именем `azureauth.json`.</span><span class="sxs-lookup"><span data-stu-id="9ff01-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="9ff01-102">При создании субъекта-службы вставьте выходные данные JSON.</span><span class="sxs-lookup"><span data-stu-id="9ff01-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="9ff01-103">Сохраните этот файл в безопасном расположении в вашей системе, доступном для кода.</span><span class="sxs-lookup"><span data-stu-id="9ff01-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="9ff01-104">При помощи PowerShell установите переменную среды с именем `AZURE_AUTH_LOCATION` и указанием полного пути к файлу, например:</span><span class="sxs-lookup"><span data-stu-id="9ff01-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
