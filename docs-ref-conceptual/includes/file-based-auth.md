Crie um arquivo de texto chamado `azureauth.properties` usando as credenciais da entidade de serviço:

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

- subscription: use o valor *SubscriptionId* de quando você executou `Login-AzureRmAccount`.
- client: use o valor *ApplicationId* da saída da entidade de serviço.
- key: use o parâmetro *-Password* atribuído quando você executou `New-AzureRmADServicePrincipal` (sem aspas).
- tenant: use o valor *TenantId* de quando você executou `Login-AzureRmAccount`.

Salve esse arquivo em um local seguro no sistema onde o seu código possa lê-lo. Use o PowerShell para definir uma variável de ambiente denominada `AZURE_AUTH_LOCATION` com o caminho completo para o arquivo, por exemplo:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.properties", "User")
```
