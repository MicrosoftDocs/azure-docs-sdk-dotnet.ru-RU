---
title: "Руководства по .NET для защиты приложения Azure"
description: "Руководства по управлению безопасностью и удостоверениями в приложениях .NET, которые выполняются в Azure."
author: camsoper
manager: douge
ms.devlang: dotnet
ms.topic: article
ms.service: Azure
ms.technology: Azure
ms.date: 06/09/2017
ms.author: casoper
ms.openlocfilehash: 1ac3b8168f8c2b11082536b635fc32b607354711
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a>Руководства по аутентификации пользователей в приложениях .NET, которые выполняются в Azure.

В таблице ниже представлены ссылки на подробные руководства по аутентификации пользователей и защите приложений .NET, которые выполняются в Azure.

Пример исходного кода см. в списке [примеров кода для служб Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).

| | |
|---|---|
|**Active Directory**||
| [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD][1] | Вход пользователей в ваше приложение ASP.NET с использованием библиотеки ADAL и выход из него.
| [Интеграция Azure AD в классическое приложение Windows WPF][2]| Интеграция Azure AD в классическое приложение Windows WPF с использованием ADAL. | 
| [Защита веб-API с помощью токенов носителя из Azure AD][3] | Защита веб-интерфейса API с помощью токенов носителя из Azure AD. |
|**хранилище ключей;**||
| [Использование хранилища ключей Azure из веб-приложения][4] | Осуществление доступа к секрету в Azure Key Vault для его использования в веб-приложении. | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application