---
title: "Библиотеки Azure Key Vault для .NET"
description: "Справочник по библиотекам Azure Key Vault для .NET"
keywords: Azure, .NET, SDK, API, Key Vault
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 77a4e710e858bbeb98579a7b540b52b4cb9dd7b0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2017
---
# <a name="azure-key-vault-libraries-for-net"></a>Библиотеки Azure Key Vault для .NET

## <a name="overview"></a>Обзор

Хранилище ключей Azure помогает защитить криптографические ключи и секреты, используемые облачными приложениями и службами.

Дополнительные сведения см. в статьях [Что такое хранилище ключей Azure?](/azure/key-vault/key-vault-whatis), [Приступая к работе с хранилищем ключей Azure](/azure/key-vault/key-vault-get-started) и [Использование хранилища ключей Azure из веб-приложения](/azure/key-vault/key-vault-use-from-web-application).

## <a name="client-library"></a>Клиентская библиотека

Используйте клиентскую библиотеку для управление ключами и связанными с ними ресурсами, такими как сертификаты и секреты.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a>Пример

В следующем примере извлекается секрет для определенного ключа, который указан в параметрах приложения.

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a>Библиотека управления

Используйте библиотеку управления для создания и удаления хранилищ ключей, а также обращения к ним.

Установите [пакет NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a>Пример

В следующем примере показано, как создать хранилище ключей для определенной группы ресурсов и расположения.

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
> [Обзор API-интерфейсов управления](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a>Примеры

* [Загрузка примеров клиента Azure Key Vault](https://www.microsoft.com/download/details.aspx?id=45343)
* [Getting Started with Azure Client Side Encryption in .NET](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/) (Приступая к работе с шифрованием на стороне клиента Azure в .NET)


Ознакомьтесь с другими [примерами кода .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet), которые можно использовать в приложениях.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
