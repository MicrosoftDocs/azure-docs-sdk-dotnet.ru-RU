<span data-ttu-id="240fb-101">Чтобы использовать библиотеки управления Azure для .NET, приложению .NET требуются разрешения на чтение и создание ресурсов в подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="240fb-101">Your .NET application needs permissions to read and create resources in your Azure subscription in order to use the Azure Management Libraries for .NET.</span></span> <span data-ttu-id="240fb-102">Создайте субъект-службу и настройте приложение для выполнения с ее учетными данными, чтобы предоставить ему такие права доступа.</span><span class="sxs-lookup"><span data-stu-id="240fb-102">Create a service principal and configure your app to run with its credentials to grant this access.</span></span> <span data-ttu-id="240fb-103">Субъект-служба позволяет создать неинтерактивную учетную запись, связанную с вашим идентификатором, которой предоставляются только разрешения, необходимые для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="240fb-103">Service principals provide a way to create a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="240fb-104">Сначала войдите в Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="240fb-104">First, login to Azure PowerShell:</span></span>

```powershell
Login-AzureRmAccount
```

<span data-ttu-id="240fb-105">Обратите внимание на отображающиеся сведения о клиенте и подписке:</span><span class="sxs-lookup"><span data-stu-id="240fb-105">Note the information displayed about your tenant and subscription:</span></span>

```plaintext
Environment           : AzureCloud
Account               : jane@contoso.com
TenantId              : 43413cc1-5886-4711-9804-8cfea3d1c3ee
SubscriptionId        : 15dbcfa8-4b93-4c9a-881c-6189d39f04d4
SubscriptionName      : my-subscription
CurrentStorageAccount : 
```

<span data-ttu-id="240fb-106">[Создайте субъект-службу с использованием PowerShell](/powershell/azure/create-azure-service-principal-azureps), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="240fb-106">[Create a service principal using PowerShell](/powershell/azure/create-azure-service-principal-azureps), like this:</span></span>

```powershell
# Create the service principal (use a strong password)
$sp = New-AzureRmADServicePrincipal -DisplayName "AzureDotNetTest" -Password "password"

# Give it the permissions it needs...
New-AzureRmRoleAssignment -ServicePrincipalName $sp.ApplicationId -RoleDefinitionName Contributor

# Display the Application ID, because we'll need it later.
$sp | Select DisplayName, ApplicationId
```

<span data-ttu-id="240fb-107">Обязательно запишите ApplicationId:</span><span class="sxs-lookup"><span data-stu-id="240fb-107">Make sure to note the ApplicationId:</span></span>

```plaintext
DisplayName     ApplicationId
-----------     -------------
AzureDotNetTest a2ab11af-01aa-4759-8345-7803287dbd39
```
