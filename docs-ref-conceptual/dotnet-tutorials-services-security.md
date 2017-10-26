---
title: "Руководства по .NET для защиты приложения Azure"
description: "Руководства по управлению безопасностью и удостоверениями в приложениях .NET, которые выполняются в Azure."
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 0cd530ef5f70778571e2f702aebc4a8b43c40e93
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2017
---
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a><span data-ttu-id="087a4-103">Руководства по аутентификации пользователей в приложениях .NET, которые выполняются в Azure.</span><span class="sxs-lookup"><span data-stu-id="087a4-103">Tutorials for authenticating users in your .NET apps running on Azure</span></span>

<span data-ttu-id="087a4-104">В таблице ниже представлены ссылки на подробные руководства по аутентификации пользователей и защите приложений .NET, которые выполняются в Azure.</span><span class="sxs-lookup"><span data-stu-id="087a4-104">The following table links to in-depth tutorials for authenticating users and securing .NET applications running on Azure.</span></span>

<span data-ttu-id="087a4-105">Пример исходного кода см. в списке [примеров кода для служб Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span><span class="sxs-lookup"><span data-stu-id="087a4-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>

| | |
|---|---|
|<span data-ttu-id="087a4-106">**Active Directory**</span><span class="sxs-lookup"><span data-stu-id="087a4-106">**Active Directory**</span></span>||
| <span data-ttu-id="087a4-107">[Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD][1]</span><span class="sxs-lookup"><span data-stu-id="087a4-107">[Web app sign-in and sign-out with Azure AD][1]</span></span> | <span data-ttu-id="087a4-108">Вход пользователей в ваше приложение ASP.NET с использованием библиотеки ADAL и выход из него.</span><span class="sxs-lookup"><span data-stu-id="087a4-108">Sign users in and out of your ASP.NET with the ADAL library.</span></span>
| <span data-ttu-id="087a4-109">[Интеграция Azure AD в классическое приложение Windows WPF][2]</span><span class="sxs-lookup"><span data-stu-id="087a4-109">[Desktop application authentication with Azure AD][2]</span></span>| <span data-ttu-id="087a4-110">Интеграция Azure AD в классическое приложение Windows WPF с использованием ADAL.</span><span class="sxs-lookup"><span data-stu-id="087a4-110">Integrate Azure AD into a Windows Desktop WPF app using ADAL.</span></span> | 
| <span data-ttu-id="087a4-111">[Защита веб-API с помощью токенов носителя из Azure AD][3]</span><span class="sxs-lookup"><span data-stu-id="087a4-111">[Web API authentication with Azure AD][3]</span></span> | <span data-ttu-id="087a4-112">Защита веб-интерфейса API с помощью токенов носителя из Azure AD.</span><span class="sxs-lookup"><span data-stu-id="087a4-112">Protect a web API using bearer tokens from Azure AD.</span></span> |
|<span data-ttu-id="087a4-113">**хранилище ключей;**</span><span class="sxs-lookup"><span data-stu-id="087a4-113">**Key Vault**</span></span>||
| <span data-ttu-id="087a4-114">[Использование хранилища ключей Azure из веб-приложения][4]</span><span class="sxs-lookup"><span data-stu-id="087a4-114">[Use Azure Key Vault from a Web Application][4]</span></span> | <span data-ttu-id="087a4-115">Осуществление доступа к секрету в Azure Key Vault для его использования в веб-приложении.</span><span class="sxs-lookup"><span data-stu-id="087a4-115">Access a secret from an Azure Key Vault so that it can be used in your web application.</span></span> | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application