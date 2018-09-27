---
title: Библиотеки Azure Key Vault для .NET
description: Справочник по библиотекам Azure Key Vault для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: key-vault
ms.openlocfilehash: a42eb9684bcfb8e8d2209235f61bbf6962cf5e9e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190557"
---
# <a name="azure-key-vault-libraries-for-net"></a><span data-ttu-id="694dc-103">Библиотеки Azure Key Vault для .NET</span><span class="sxs-lookup"><span data-stu-id="694dc-103">Azure Key Vault libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="694dc-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="694dc-104">Overview</span></span>

<span data-ttu-id="694dc-105">Хранилище ключей Azure помогает защитить криптографические ключи и секреты, используемые облачными приложениями и службами.</span><span class="sxs-lookup"><span data-stu-id="694dc-105">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span>

<span data-ttu-id="694dc-106">Дополнительные сведения см. в статьях [Что такое хранилище ключей Azure?](/azure/key-vault/key-vault-whatis), [Приступая к работе с хранилищем ключей Azure](/azure/key-vault/key-vault-get-started) и [Использование хранилища ключей Azure из веб-приложения](/azure/key-vault/key-vault-use-from-web-application).</span><span class="sxs-lookup"><span data-stu-id="694dc-106">Read more about [What is Key Vault?](/azure/key-vault/key-vault-whatis) then [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started) or learn how to [Use Key Vault from a web app](/azure/key-vault/key-vault-use-from-web-application).</span></span>

## <a name="client-library"></a><span data-ttu-id="694dc-107">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="694dc-107">Client library</span></span>

<span data-ttu-id="694dc-108">Используйте клиентскую библиотеку для управление ключами и связанными с ними ресурсами, такими как сертификаты и секреты.</span><span class="sxs-lookup"><span data-stu-id="694dc-108">Use the client library to manage keys and related assets such as certificates and secrets.</span></span>

<span data-ttu-id="694dc-109">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="694dc-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="694dc-110">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="694dc-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a><span data-ttu-id="694dc-111">Пример</span><span class="sxs-lookup"><span data-stu-id="694dc-111">Example</span></span>

<span data-ttu-id="694dc-112">В следующем примере извлекается секрет для определенного ключа, который указан в параметрах приложения.</span><span class="sxs-lookup"><span data-stu-id="694dc-112">The following example retrieves the secret for a specific key that is identified in the application settings.</span></span>

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="694dc-113">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="694dc-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a><span data-ttu-id="694dc-114">Библиотека управления</span><span class="sxs-lookup"><span data-stu-id="694dc-114">Management library</span></span>

<span data-ttu-id="694dc-115">Используйте библиотеку управления для создания и удаления хранилищ ключей, а также обращения к ним.</span><span class="sxs-lookup"><span data-stu-id="694dc-115">Use the management library to create, delete, and query key vaults.</span></span>

<span data-ttu-id="694dc-116">Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="694dc-116">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="694dc-117">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="694dc-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a><span data-ttu-id="694dc-118">Пример</span><span class="sxs-lookup"><span data-stu-id="694dc-118">Example</span></span>

<span data-ttu-id="694dc-119">В следующем примере показано, как создать хранилище ключей для определенной группы ресурсов и расположения.</span><span class="sxs-lookup"><span data-stu-id="694dc-119">The following example demonstrates how to create a new key vault for a given resource group and location.</span></span>

```csharp
using (KeyVaultManagementClient client = new KeyVaultManagementClient(
    new TokenCloudCredentials(subscriptionId, accessToken)))
{
    client.Vaults.CreateOrUpdate(resourceGroupName, "myKeyVault", new VaultCreateOrUpdateParameters
    {
        Properties = new VaultProperties
        {
            EnabledForDeployment = true,
            EnabledForDiskEncryption = true,
            EnabledForTemplateDeployment = true,
            Location = resourceGroupLocation,
            // SKU level, access policies, tenants, etc.
        }
    });
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="694dc-120">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="694dc-120">Explore the management APIs</span></span>](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a><span data-ttu-id="694dc-121">Примеры</span><span class="sxs-lookup"><span data-stu-id="694dc-121">Samples</span></span>

* [<span data-ttu-id="694dc-122">Загрузка примеров клиента Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="694dc-122">Download the Azure Key Vault client samples</span></span>](https://www.microsoft.com/download/details.aspx?id=45343)
* <span data-ttu-id="694dc-123">[Getting Started with Azure Client Side Encryption in .NET](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/) (Приступая к работе с шифрованием на стороне клиента Azure в .NET)</span><span class="sxs-lookup"><span data-stu-id="694dc-123">[Getting Started with Azure Client Side Encryption in .NET](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/)</span></span>


<span data-ttu-id="694dc-124">Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="694dc-124">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
