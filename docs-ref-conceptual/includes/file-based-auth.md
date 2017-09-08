Создайте текстовый файл с именем `azureauth.properties`, использовав учетные данные субъекта-службы:

```plaintext
# sample management library properties file
subscription=15dbcfa8-4b93-4c9a-881c-6189d39f04d4
client=a2ab11af-01aa-4759-8345-7803287dbd39
key=password
tenant=43413cc1-5886-4711-9804-8cfea3d1c3ee
managementURI=https://management.core.windows.net/
baseURL=https://management.azure.com/
authURL=https://login.windows.net/
graphURL=https://graph.windows.net/
```

- subscription: задайте значение *SubscriptionId*, которое использовалось при запуске `Login-AzureRmAccount`.
- client: используйте значение *ApplicationId* из выходных данных субъекта-службы.
- key: используйте параметр *-Password*, который вы назначили при запуске `New-AzureRmADServicePrincipal` (без кавычек).
- tenant: задайте значение *TenantId*, которое использовалось при запуске `Login-AzureRmAccount`.

Сохраните этот файл в безопасном расположении, доступном для кода. При помощи PowerShell установите переменную среды с именем `AZURE_AUTH_LOCATION` и указанием полного пути к файлу, например:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.properties", "User")
```
