---
title: "Библиотеки Azure Active Directory для .NET"
description: "Справочник по библиотекам Azure Active Directory для .NET"
keywords: Azure, .NET, SDK, API, AAD, Active Directory
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: adbe907888e49066b6d67a4fb26410a6f6b3b095
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-active-directory-libraries-for-net"></a>Библиотеки Azure Active Directory для .NET

## <a name="overview"></a>Обзор

Вход пользователей в приложения и управление доступом к приложениям и API-интерфейсам с помощью Azure Active Directory.

Чтобы приступить к работе с Azure Active Directory, ознакомьтесь со статьей [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).

## <a name="client-library"></a>Клиентская библиотека

Подключение и аутентификация пользователей или приложений при помощи OAuth2, OpenID Connect, проверки подлинности API Active Directory Graph или [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a>Пример кода

Получите маркер доступа для классического приложения.

```csharp
/* Include this "using" directive...
using Microsoft.IdentityModel.Clients.ActiveDirectory;
*/

AuthenticationResult result = null;
AuthenticationContext authContext = new AuthenticationContext("https://someauthority.com");
try
{
    result = await authContext.AcquireTokenAsync(graphResourceId, clientId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
}
catch (AdalException ex)
{
    // An unexpected error occurred, or user canceled the sign in.
    if (ex.ErrorCode != "access_denied")
        MessageBox.Show(ex.Message);

    return;
}
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a>Примеры

* [Integrate Azure AD into a web application using OpenID Connect](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect) (Интеграция Azure AD в веб-приложение с использованием OpenID Connect)
* [Calling a web api using an application identity](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity) (Вызов веб-API с использованием удостоверения приложения)
* [Authorization in a web app using Azure AD application roles & role claims](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims) (Авторизация в веб-приложении при помощи ролей приложений Azure AD и утверждения таких ролей)

Просмотрите всю коллекцию [примеров кода Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-code-samples).

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
