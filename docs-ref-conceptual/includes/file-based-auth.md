<span data-ttu-id="dfd4d-101">Создайте текстовый файл с именем `azureauth.properties`, использовав учетные данные субъекта-службы:</span><span class="sxs-lookup"><span data-stu-id="dfd4d-101">Create a text file named `azureauth.properties` using the service principal credentials:</span></span>

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

- <span data-ttu-id="dfd4d-102">subscription: задайте значение *SubscriptionId*, которое использовалось при запуске `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-102">subscription: use the *SubscriptionId* value from when you ran `Login-AzureRmAccount`.</span></span>
- <span data-ttu-id="dfd4d-103">client: используйте значение *ApplicationId* из выходных данных субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-103">client: use the *ApplicationId* value from the service principal output.</span></span>
- <span data-ttu-id="dfd4d-104">key: используйте параметр *-Password*, который вы назначили при запуске `New-AzureRmADServicePrincipal` (без кавычек).</span><span class="sxs-lookup"><span data-stu-id="dfd4d-104">key: use the *-Password* parameter you assigned when you ran `New-AzureRmADServicePrincipal` (without quotes).</span></span>
- <span data-ttu-id="dfd4d-105">tenant: задайте значение *TenantId*, которое использовалось при запуске `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-105">tenant: use the *TenantId* value from when you ran `Login-AzureRmAccount`.</span></span>

<span data-ttu-id="dfd4d-106">Сохраните этот файл в безопасном расположении, доступном для кода.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-106">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="dfd4d-107">При помощи PowerShell установите переменную среды с именем `AZURE_AUTH_LOCATION` и указанием полного пути к файлу, например:</span><span class="sxs-lookup"><span data-stu-id="dfd4d-107">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.properties", "User")
```
