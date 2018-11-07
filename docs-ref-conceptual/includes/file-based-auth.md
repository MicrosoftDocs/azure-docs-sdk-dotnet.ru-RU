---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: 7f7c24957d2bc0574fc0b1bf2a8ae8fe8b4dfc64
ms.sourcegitcommit: 70982e900bd4adfbc121eba55d94544f17c6b495
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51196050"
---
Создайте текстовый файл с именем `azureauth.json`. При создании субъекта-службы вставьте выходные данные JSON.

Сохраните этот файл в безопасном расположении в вашей системе, доступном для кода. При помощи PowerShell установите переменную среды с именем `AZURE_AUTH_LOCATION` и указанием полного пути к файлу, например:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
