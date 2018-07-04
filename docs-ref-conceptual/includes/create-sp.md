<span data-ttu-id="85838-101">Чтобы использовать библиотеки управления Azure для .NET, приложению .NET требуются разрешения на чтение и создание ресурсов в подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="85838-101">Your .NET application needs permissions to read and create resources in your Azure subscription in order to use the Azure Management Libraries for .NET.</span></span> <span data-ttu-id="85838-102">Создайте субъект-службу и настройте приложение для выполнения с ее учетными данными, чтобы предоставить ему такие права доступа.</span><span class="sxs-lookup"><span data-stu-id="85838-102">Create a service principal and configure your app to run with its credentials to grant this access.</span></span> <span data-ttu-id="85838-103">Субъект-служба позволяет создать неинтерактивную учетную запись, связанную с вашим идентификатором, которой предоставляются только разрешения, необходимые для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="85838-103">Service principals provide a way to create a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="85838-104">Сначала войдите в Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85838-104">First, login to Azure PowerShell:</span></span>

```powershell
Login-AzureRmAccount
```

<span data-ttu-id="85838-105">Обратите внимание на отображающиеся сведения о клиенте и подписке:</span><span class="sxs-lookup"><span data-stu-id="85838-105">Note the information displayed about your tenant and subscription:</span></span>

```plaintext
Environment           : AzureCloud
Account               : jane@contoso.com
TenantId              : 43413cc1-5886-4711-9804-8cfea3d1c3ee
SubscriptionId        : 15dbcfa8-4b93-4c9a-881c-6189d39f04d4
SubscriptionName      : my-subscription
CurrentStorageAccount : 
```

<span data-ttu-id="85838-106">[Создайте в PowerShell субъект-службу](/powershell/azure/create-azure-service-principal-azureps), как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="85838-106">[Create a service principal using PowerShell](/powershell/azure/create-azure-service-principal-azureps) as shown below.</span></span> 

> [!NOTE]
> <span data-ttu-id="85838-107">Если командлет `New-AzureRmADServicePrincipal` возвращает сообщение "Объект с таким же значением свойства identifierUris уже существует", в вашем клиенте уже есть субъект-служба с таким именем.</span><span class="sxs-lookup"><span data-stu-id="85838-107">If the `New-AzureRmADServicePrincipal` cmdlet below returns "Another object with the same value for property identifierUris already exists," there is already a service principal by that name in your tenant.</span></span> <span data-ttu-id="85838-108">Задайте для параметра **DisplayName** другое значение.</span><span class="sxs-lookup"><span data-stu-id="85838-108">Use a different value for the **DisplayName** parameter.</span></span> 

```powershell
# Create the service principal (use a strong password)
$cred = Get-Credential
$sp = New-AzureRmADServicePrincipal -DisplayName "AzureDotNetTest" -Password $cred.Password

# Give it the permissions it needs...
New-AzureRmRoleAssignment -ServicePrincipalName $sp.ApplicationId -RoleDefinitionName Contributor

# Display the Application ID, because we'll need it later.
$sp | Select DisplayName, ApplicationId
```

<span data-ttu-id="85838-109">Обязательно запишите ApplicationId:</span><span class="sxs-lookup"><span data-stu-id="85838-109">Make sure to note the ApplicationId:</span></span>

```plaintext
DisplayName     ApplicationId
-----------     -------------
AzureDotNetTest a2ab11af-01aa-4759-8345-7803287dbd39
```
