Чтобы использовать библиотеки управления Azure для .NET, приложению .NET требуются разрешения на чтение и создание ресурсов в подписке Azure. Создайте субъект-службу и настройте приложение для выполнения с ее учетными данными, чтобы предоставить ему такие права доступа. Субъект-служба позволяет создать неинтерактивную учетную запись, связанную с вашим идентификатором, которой предоставляются только разрешения, необходимые для запуска приложения.

Сначала войдите в Azure PowerShell:

```powershell
Login-AzureRmAccount
```

Обратите внимание на отображающиеся сведения о клиенте и подписке:

```plaintext
Environment           : AzureCloud
Account               : jane@contoso.com
TenantId              : 43413cc1-5886-4711-9804-8cfea3d1c3ee
SubscriptionId        : 15dbcfa8-4b93-4c9a-881c-6189d39f04d4
SubscriptionName      : my-subscription
CurrentStorageAccount : 
```

[Создайте в PowerShell субъект-службу](/powershell/azure/create-azure-service-principal-azureps), как показано ниже. 

> [!NOTE]
> Если командлет `New-AzureRmADServicePrincipal` возвращает сообщение "Объект с таким же значением свойства identifierUris уже существует", в вашем клиенте уже есть субъект-служба с таким именем. Задайте для параметра **DisplayName** другое значение. 

```powershell
# Create the service principal (use a strong password)
$cred = Get-Credential
$sp = New-AzureRmADServicePrincipal -DisplayName "AzureDotNetTest" -Password $cred.Password

# Give it the permissions it needs...
New-AzureRmRoleAssignment -ServicePrincipalName $sp.ApplicationId -RoleDefinitionName Contributor

# Display the Application ID, because we'll need it later.
$sp | Select DisplayName, ApplicationId
```

Обязательно запишите ApplicationId:

```plaintext
DisplayName     ApplicationId
-----------     -------------
AzureDotNetTest a2ab11af-01aa-4759-8345-7803287dbd39
```
