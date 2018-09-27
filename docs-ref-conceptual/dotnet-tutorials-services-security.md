---
title: Руководства по .NET для защиты приложения Azure
description: Руководства по управлению безопасностью и удостоверениями в приложениях .NET, которые выполняются в Azure.
ms.date: 10/19/2017
ms.openlocfilehash: 19960efa8faa762f0cde657d702f09a8dcb66e99
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190647"
---
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a><span data-ttu-id="8938b-103">Руководства по аутентификации пользователей в приложениях .NET, которые выполняются в Azure.</span><span class="sxs-lookup"><span data-stu-id="8938b-103">Tutorials for authenticating users in your .NET apps running on Azure</span></span>

<span data-ttu-id="8938b-104">В таблице ниже представлены ссылки на подробные руководства по аутентификации пользователей и защите приложений .NET, которые выполняются в Azure.</span><span class="sxs-lookup"><span data-stu-id="8938b-104">The following table links to in-depth tutorials for authenticating users and securing .NET applications running on Azure.</span></span>

<span data-ttu-id="8938b-105">Пример исходного кода см. в списке [примеров кода для служб Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span><span class="sxs-lookup"><span data-stu-id="8938b-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>

| | |
|---|---|
|<span data-ttu-id="8938b-106">**Active Directory**</span><span class="sxs-lookup"><span data-stu-id="8938b-106">**Active Directory**</span></span>||
| <span data-ttu-id="8938b-107">[Добавление Azure Active Directory в веб-приложение с помощью Подключенных служб Visual Studio][5]</span><span class="sxs-lookup"><span data-stu-id="8938b-107">[Add Azure Active Directory to your web application by using Visual Studio Connected Services][5]</span></span> | <span data-ttu-id="8938b-108">Подключение веб-приложения к Azure AD в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8938b-108">Connect a web app to Azure AD in Visual Studio</span></span> |
| <span data-ttu-id="8938b-109">[Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD][1]</span><span class="sxs-lookup"><span data-stu-id="8938b-109">[Web app sign-in and sign-out with Azure AD][1]</span></span> | <span data-ttu-id="8938b-110">Вход пользователей в ваше приложение ASP.NET с использованием библиотеки ADAL и выход из него.</span><span class="sxs-lookup"><span data-stu-id="8938b-110">Sign users in and out of your ASP.NET with the ADAL library.</span></span> |
| <span data-ttu-id="8938b-111">[Интеграция Azure AD в классическое приложение Windows WPF][2]</span><span class="sxs-lookup"><span data-stu-id="8938b-111">[Desktop application authentication with Azure AD][2]</span></span>| <span data-ttu-id="8938b-112">Интеграция Azure AD в классическое приложение Windows WPF с использованием ADAL.</span><span class="sxs-lookup"><span data-stu-id="8938b-112">Integrate Azure AD into a Windows Desktop WPF app using ADAL.</span></span> | 
| <span data-ttu-id="8938b-113">[Защита веб-API с помощью токенов носителя из Azure AD][3]</span><span class="sxs-lookup"><span data-stu-id="8938b-113">[Web API authentication with Azure AD][3]</span></span> | <span data-ttu-id="8938b-114">Защита веб-интерфейса API с помощью токенов носителя из Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8938b-114">Protect a web API using bearer tokens from Azure AD.</span></span> |
|<span data-ttu-id="8938b-115">**хранилище ключей;**</span><span class="sxs-lookup"><span data-stu-id="8938b-115">**Key Vault**</span></span>||
| <span data-ttu-id="8938b-116">[Добавление Azure Key Vault в веб-приложение с помощью Подключенных служб Visual Studio][6]</span><span class="sxs-lookup"><span data-stu-id="8938b-116">[Add Key Vault to your web application by using Visual Studio Connected Services][6]</span></span> | <span data-ttu-id="8938b-117">Подключение веб-приложения к Azure Key Vault в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8938b-117">Connect a web app to Azure Key Vault in Visual Studio</span></span> |
| <span data-ttu-id="8938b-118">[Использование хранилища ключей Azure из веб-приложения][4]</span><span class="sxs-lookup"><span data-stu-id="8938b-118">[Use Azure Key Vault from a Web Application][4]</span></span> | <span data-ttu-id="8938b-119">Осуществление доступа к секрету в Azure Key Vault для его использования в веб-приложении.</span><span class="sxs-lookup"><span data-stu-id="8938b-119">Access a secret from an Azure Key Vault so that it can be used in your web application.</span></span> | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application
[5]: /azure/active-directory/develop/vs-active-directory-add-connected-service
[6]: /azure/key-vault/vs-key-vault-add-connected-service