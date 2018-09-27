---
title: Библиотеки Azure Active Directory для .NET
description: Справочник по библиотекам Azure Active Directory для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: active-directory
ms.openlocfilehash: 0226f06546f7dc14b9ab3392008744754d47a19a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190227"
---
# <a name="azure-active-directory-libraries-for-net"></a><span data-ttu-id="62b48-103">Библиотеки Azure Active Directory для .NET</span><span class="sxs-lookup"><span data-stu-id="62b48-103">Azure Active Directory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="62b48-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="62b48-104">Overview</span></span>

<span data-ttu-id="62b48-105">Вход пользователей в приложения и управление доступом к приложениям и API-интерфейсам с помощью Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="62b48-105">Sign-on users and manage access to applications and APIs with Azure Active Directory.</span></span>

<span data-ttu-id="62b48-106">Чтобы приступить к работе с Azure Active Directory, ознакомьтесь со статьей [Вход в веб-приложение ASP.NET и выход из него с помощью Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span><span class="sxs-lookup"><span data-stu-id="62b48-106">To get started with Azure Active Directory, see [ASP.NET web app sign-in and sign-out with Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="62b48-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="62b48-107">Client library</span></span>

<span data-ttu-id="62b48-108">Подключение и аутентификация пользователей или приложений при помощи OAuth2, OpenID Connect, проверки подлинности API Active Directory Graph или [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span><span class="sxs-lookup"><span data-stu-id="62b48-108">Connect and authenticate users or applications over OAuth2, OpenID Connect, Active Directory Graph API authentication or [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span></span>

<span data-ttu-id="62b48-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="62b48-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="62b48-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="62b48-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a><span data-ttu-id="62b48-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="62b48-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a><span data-ttu-id="62b48-112">Пример кода</span><span class="sxs-lookup"><span data-stu-id="62b48-112">Code Example</span></span>

<span data-ttu-id="62b48-113">Получите маркер доступа для классического приложения.</span><span class="sxs-lookup"><span data-stu-id="62b48-113">Retrieve an access token for a desktop application.</span></span>

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
> [<span data-ttu-id="62b48-114">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="62b48-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a><span data-ttu-id="62b48-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="62b48-115">Samples</span></span>

* <span data-ttu-id="62b48-116">[Integrate Azure AD into a web application using OpenID Connect](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect) (Интеграция Azure AD в веб-приложение с использованием OpenID Connect)</span><span class="sxs-lookup"><span data-stu-id="62b48-116">[Use OpenID Connect to authenticate users from an Azure AD tenant](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect)</span></span>
* <span data-ttu-id="62b48-117">[Calling a web api using an application identity](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity) (Вызов веб-API с использованием удостоверения приложения)</span><span class="sxs-lookup"><span data-stu-id="62b48-117">[Use Oauth2 to call a web API with application permissions](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity)</span></span>
* <span data-ttu-id="62b48-118">[Authorization in a web app using Azure AD application roles & role claims](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims) (Авторизация в веб-приложении при помощи ролей приложений Azure AD и утверждения таких ролей)</span><span class="sxs-lookup"><span data-stu-id="62b48-118">[Use role-based access control (RBAC) in an application](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims)</span></span>

<span data-ttu-id="62b48-119">Просмотрите всю коллекцию [примеров кода Azure Active Directory](/azure/active-directory/develop/active-directory-code-samples).</span><span class="sxs-lookup"><span data-stu-id="62b48-119">Explore the full collection of [Azure Active Directory code samples](/azure/active-directory/develop/active-directory-code-samples).</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
