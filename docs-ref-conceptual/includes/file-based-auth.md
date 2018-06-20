<span data-ttu-id="97787-101">Crie um arquivo de texto chamado `azureauth.properties` usando as credenciais da entidade de serviço:</span><span class="sxs-lookup"><span data-stu-id="97787-101">Create a text file named `azureauth.properties` using the service principal credentials:</span></span>

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

- <span data-ttu-id="97787-102">subscription: use o valor *SubscriptionId* de quando você executou `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="97787-102">subscription: use the *SubscriptionId* value from when you ran `Login-AzureRmAccount`.</span></span>
- <span data-ttu-id="97787-103">client: use o valor *ApplicationId* da saída da entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="97787-103">client: use the *ApplicationId* value from the service principal output.</span></span>
- <span data-ttu-id="97787-104">key: use o parâmetro *-Password* atribuído quando você executou `New-AzureRmADServicePrincipal` (sem aspas).</span><span class="sxs-lookup"><span data-stu-id="97787-104">key: use the *-Password* parameter you assigned when you ran `New-AzureRmADServicePrincipal` (without quotes).</span></span>
- <span data-ttu-id="97787-105">tenant: use o valor *TenantId* de quando você executou `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="97787-105">tenant: use the *TenantId* value from when you ran `Login-AzureRmAccount`.</span></span>

<span data-ttu-id="97787-106">Salve esse arquivo em um local seguro no sistema onde o seu código possa lê-lo.</span><span class="sxs-lookup"><span data-stu-id="97787-106">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="97787-107">Use o PowerShell para definir uma variável de ambiente denominada `AZURE_AUTH_LOCATION` com o caminho completo para o arquivo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="97787-107">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.properties", "User")
```
