---
title: "Примеры инструкций для библиотек управления Azure для .NET"
description: "Получите пример кода для создания и обновления ресурсов с помощью библиотек управления Azure для .NET."
keywords: Azure, .NET, SDK, API, sample, example
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.assetid: 
ms.openlocfilehash: ffda7cca724962e6f953432c5cab04485ddabb03
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-management-libraries-for-net-sample-instructions"></a>Примеры инструкций для библиотек управления Azure для .NET

В этой статье описаны предварительные требования и процедуры проверки подлинности, необходимые для выполнения примеров для библиотек управления Azure для .NET.

## <a name="prerequisties"></a>Предварительные требования 

* [Visual Studio 2017](https://www.visualstudio.com/vs/) или [пакет SDK для .NET Core](https://www.microsoft.com/net/download/core).
* [Подписка Microsoft Azure](https://azure.microsoft.com/free/).
* [Клиент командной строки Git](https://git-scm.com/).
* [Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)

## <a name="authentication-for-all-samples"></a>Проверка подлинности для всех примеров

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="running-the-samples"></a>Выполнение примеров

Как только пример будет клонирован с использованием Git, можно открыть его в Visual Studio и выполнить при помощи IDE.  Или можно использовать пакет SDK для .NET Core, чтобы собрать и выполнить пример из командной строки, как показано ниже:

```cmd
git clone https://github.com/Azure-Samples/app-service-dotnet-configure-deployment-sources-for-web-apps.git
cd app-service-dotnet-configure-deployment-sources-for-web-apps
dotnet restore
dotnet run
```