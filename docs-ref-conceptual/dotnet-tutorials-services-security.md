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
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a>Руководства по аутентификации пользователей в приложениях .NET, которые выполняются в Azure.

В таблице ниже представлены ссылки на подробные руководства по аутентификации пользователей и защите приложений .NET, которые выполняются в Azure.

Пример исходного кода см. в списке [примеров кода для служб Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).

| | |
|---|---|
|**Active Directory**||
| [Добавление Azure Active Directory в веб-приложение с помощью Подключенных служб Visual Studio][5] | Подключение веб-приложения к Azure AD в Visual Studio |
| [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD][1] | Вход пользователей в ваше приложение ASP.NET с использованием библиотеки ADAL и выход из него. |
| [Интеграция Azure AD в классическое приложение Windows WPF][2]| Интеграция Azure AD в классическое приложение Windows WPF с использованием ADAL. | 
| [Защита веб-API с помощью токенов носителя из Azure AD][3] | Защита веб-интерфейса API с помощью токенов носителя из Azure AD. |
|**хранилище ключей;**||
| [Добавление Azure Key Vault в веб-приложение с помощью Подключенных служб Visual Studio][6] | Подключение веб-приложения к Azure Key Vault в Visual Studio |
| [Использование хранилища ключей Azure из веб-приложения][4] | Осуществление доступа к секрету в Azure Key Vault для его использования в веб-приложении. | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application
[5]: /azure/active-directory/develop/vs-active-directory-add-connected-service
[6]: /azure/key-vault/vs-key-vault-add-connected-service