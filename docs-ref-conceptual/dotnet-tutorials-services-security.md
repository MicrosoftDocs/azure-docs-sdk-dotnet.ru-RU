---
title: Руководства по .NET для защиты приложения Azure
description: Руководства по управлению безопасностью и удостоверениями в приложениях .NET, которые выполняются в Azure.
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 88ecfc69fbd57becf1adf1163a063c0d2bb086a8
ms.sourcegitcommit: 61638b504b6c4d96b357894835c80c2680a99fe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750592"
---
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a><span data-ttu-id="65415-103">Руководства по аутентификации пользователей в приложениях .NET, которые выполняются в Azure.</span><span class="sxs-lookup"><span data-stu-id="65415-103">Tutorials for authenticating users in your .NET apps running on Azure</span></span>

<span data-ttu-id="65415-104">В таблице ниже представлены ссылки на подробные руководства по аутентификации пользователей и защите приложений .NET, которые выполняются в Azure.</span><span class="sxs-lookup"><span data-stu-id="65415-104">The following table links to in-depth tutorials for authenticating users and securing .NET applications running on Azure.</span></span>

<span data-ttu-id="65415-105">Пример исходного кода см. в списке [примеров кода для служб Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span><span class="sxs-lookup"><span data-stu-id="65415-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>

| | |
|---|---|
|<span data-ttu-id="65415-106">**Active Directory**</span><span class="sxs-lookup"><span data-stu-id="65415-106">**Active Directory**</span></span>||
| <span data-ttu-id="65415-107">[Добавление Azure Active Directory в веб-приложение с помощью Подключенных служб Visual Studio][5]</span><span class="sxs-lookup"><span data-stu-id="65415-107">[Add Azure Active Directory to your web application by using Visual Studio Connected Services][5]</span></span> | <span data-ttu-id="65415-108">Подключение веб-приложения к Azure AD в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="65415-108">Connect a web app to Azure AD in Visual Studio</span></span> |
| <span data-ttu-id="65415-109">[Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD][1]</span><span class="sxs-lookup"><span data-stu-id="65415-109">[Web app sign-in and sign-out with Azure AD][1]</span></span> | <span data-ttu-id="65415-110">Вход пользователей в ваше приложение ASP.NET с использованием библиотеки ADAL и выход из него.</span><span class="sxs-lookup"><span data-stu-id="65415-110">Sign users in and out of your ASP.NET with the ADAL library.</span></span> |
| <span data-ttu-id="65415-111">[Интеграция Azure AD в классическое приложение Windows WPF][2]</span><span class="sxs-lookup"><span data-stu-id="65415-111">[Desktop application authentication with Azure AD][2]</span></span>| <span data-ttu-id="65415-112">Интеграция Azure AD в классическое приложение Windows WPF с использованием ADAL.</span><span class="sxs-lookup"><span data-stu-id="65415-112">Integrate Azure AD into a Windows Desktop WPF app using ADAL.</span></span> | 
| <span data-ttu-id="65415-113">[Защита веб-API с помощью токенов носителя из Azure AD][3]</span><span class="sxs-lookup"><span data-stu-id="65415-113">[Web API authentication with Azure AD][3]</span></span> | <span data-ttu-id="65415-114">Защита веб-интерфейса API с помощью токенов носителя из Azure AD.</span><span class="sxs-lookup"><span data-stu-id="65415-114">Protect a web API using bearer tokens from Azure AD.</span></span> |
|<span data-ttu-id="65415-115">**хранилище ключей;**</span><span class="sxs-lookup"><span data-stu-id="65415-115">**Key Vault**</span></span>||
| <span data-ttu-id="65415-116">[Добавление Azure Key Vault в веб-приложение с помощью Подключенных служб Visual Studio][6]</span><span class="sxs-lookup"><span data-stu-id="65415-116">[Add Key Vault to your web application by using Visual Studio Connected Services][6]</span></span> | <span data-ttu-id="65415-117">Подключение веб-приложения к Azure Key Vault в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="65415-117">Connect a web app to Azure Key Vault in Visual Studio</span></span> |
| <span data-ttu-id="65415-118">[Использование хранилища ключей Azure из веб-приложения][4]</span><span class="sxs-lookup"><span data-stu-id="65415-118">[Use Azure Key Vault from a Web Application][4]</span></span> | <span data-ttu-id="65415-119">Осуществление доступа к секрету в Azure Key Vault для его использования в веб-приложении.</span><span class="sxs-lookup"><span data-stu-id="65415-119">Access a secret from an Azure Key Vault so that it can be used in your web application.</span></span> | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application
[5]: /azure/active-directory/develop/vs-active-directory-add-connected-service
[6]: /azure/key-vault/vs-key-vault-add-connected-service