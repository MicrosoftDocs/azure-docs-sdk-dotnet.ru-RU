---
title: Примеры инструкций для библиотек управления Azure для .NET
description: Получите пример кода для создания и обновления ресурсов с помощью библиотек управления Azure для .NET.
keywords: Azure, .NET, SDK, API, sample, example
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: a931e623768e1fddad263c7da8eb864c37613379
ms.sourcegitcommit: 9dd801d659803f5efb16d65454cd09258e1cc7d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "29752477"
---
# <a name="azure-management-libraries-for-net-sample-instructions"></a><span data-ttu-id="22132-104">Примеры инструкций для библиотек управления Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="22132-104">Azure management libraries for .NET sample instructions</span></span>

<span data-ttu-id="22132-105">В этой статье описаны предварительные требования и процедуры проверки подлинности, необходимые для выполнения примеров для библиотек управления Azure для .NET.</span><span class="sxs-lookup"><span data-stu-id="22132-105">This article describes the prerequisites and authentication required for running the samples for the Azure management libraries for .NET.</span></span>

## <a name="prerequisties"></a><span data-ttu-id="22132-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="22132-106">Prerequisties</span></span> 

* <span data-ttu-id="22132-107">[Visual Studio 2017](https://www.visualstudio.com/vs/) или [пакет SDK для .NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="22132-107">[Visual Studio 2017](https://www.visualstudio.com/vs/) or [.NET Core SDK](https://www.microsoft.com/net/download/core)</span></span>
* <span data-ttu-id="22132-108">[Подписка Microsoft Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="22132-108">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>
* <span data-ttu-id="22132-109">[Клиент командной строки Git](https://git-scm.com/).</span><span class="sxs-lookup"><span data-stu-id="22132-109">[Git command line client](https://git-scm.com/)</span></span>
* [<span data-ttu-id="22132-110">Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="22132-110">Azure PowerShell</span></span>](/powershell/azure/install-azurerm-ps)

## <a name="authentication-for-all-samples"></a><span data-ttu-id="22132-111">Проверка подлинности для всех примеров</span><span class="sxs-lookup"><span data-stu-id="22132-111">Authentication for all samples</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="running-the-samples"></a><span data-ttu-id="22132-112">Выполнение примеров</span><span class="sxs-lookup"><span data-stu-id="22132-112">Running the samples</span></span>

<span data-ttu-id="22132-113">Как только пример будет клонирован с использованием Git, можно открыть его в Visual Studio и выполнить при помощи IDE.</span><span class="sxs-lookup"><span data-stu-id="22132-113">Once you have used Git to clone the sample, you can open the sample in Visual Studio and run the sample using the IDE.</span></span>  <span data-ttu-id="22132-114">Или можно использовать пакет SDK для .NET Core, чтобы собрать и выполнить пример из командной строки, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="22132-114">Alternatively, use the .NET Core SDK to build and run the sample from the command line, like this:</span></span>

```cmd
git clone https://github.com/Azure-Samples/app-service-dotnet-configure-deployment-sources-for-web-apps.git
cd app-service-dotnet-configure-deployment-sources-for-web-apps
dotnet restore
dotnet run
```