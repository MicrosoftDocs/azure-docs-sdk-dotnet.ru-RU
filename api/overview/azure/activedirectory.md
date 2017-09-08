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
# <a name="azure-active-directory-libraries-for-net"></a><span data-ttu-id="feb77-104">Библиотеки Azure Active Directory для .NET</span><span class="sxs-lookup"><span data-stu-id="feb77-104">Azure Active Directory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="feb77-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="feb77-105">Overview</span></span>

<span data-ttu-id="feb77-106">Вход пользователей в приложения и управление доступом к приложениям и API-интерфейсам с помощью Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="feb77-106">Sign-on users and manage access to applications and APIs with Azure Active Directory.</span></span>

<span data-ttu-id="feb77-107">Чтобы приступить к работе с Azure Active Directory, ознакомьтесь со статьей [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span><span class="sxs-lookup"><span data-stu-id="feb77-107">To get started with Azure Active Directory, see [ASP.NET web app sign-in and sign-out with Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="feb77-108">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="feb77-108">Client library</span></span>

<span data-ttu-id="feb77-109">Подключение и аутентификация пользователей или приложений при помощи OAuth2, OpenID Connect, проверки подлинности API Active Directory Graph или [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span><span class="sxs-lookup"><span data-stu-id="feb77-109">Connect and authenticate users or applications over OAuth2, OpenID Connect, Active Directory Graph API authentication or [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span></span>

<span data-ttu-id="feb77-110">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="feb77-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="feb77-111">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="feb77-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a><span data-ttu-id="feb77-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="feb77-112">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a><span data-ttu-id="feb77-113">Пример кода</span><span class="sxs-lookup"><span data-stu-id="feb77-113">Code Example</span></span>

<span data-ttu-id="feb77-114">Получите маркер доступа для классического приложения.</span><span class="sxs-lookup"><span data-stu-id="feb77-114">Retrieve an access token for a desktop application.</span></span>

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
> [<span data-ttu-id="feb77-115">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="feb77-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a><span data-ttu-id="feb77-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="feb77-116">Samples</span></span>

* [<span data-ttu-id="feb77-117">Integrate Azure AD into a web application using OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="feb77-117">Use OpenID Connect to authenticate users from an Azure AD tenant</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect) (Интеграция Azure AD в веб-приложение с использованием OpenID Connect)
* [<span data-ttu-id="feb77-118">Calling a web api using an application identity</span><span class="sxs-lookup"><span data-stu-id="feb77-118">Use Oauth2 to call a web API with application permissions</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity) (Вызов веб-API с использованием удостоверения приложения)
* [<span data-ttu-id="feb77-119">Authorization in a web app using Azure AD application roles & role claims</span><span class="sxs-lookup"><span data-stu-id="feb77-119">Use role-based access control (RBAC) in an application</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims) (Авторизация в веб-приложении при помощи ролей приложений Azure AD и утверждения таких ролей)

<span data-ttu-id="feb77-120">Просмотрите всю коллекцию [примеров кода Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-code-samples).</span><span class="sxs-lookup"><span data-stu-id="feb77-120">Explore the full collection of [Azure Active Directory code samples](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-code-samples).</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
