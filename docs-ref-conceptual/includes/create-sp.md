Seu aplicativo .NET precisa de permissões para ler e criar recursos na sua assinatura do Azure a fim de usar as bibliotecas de gerenciamento do Azure para .NET. Crie uma entidade de serviço e configure seu aplicativo para ser executado com suas credenciais e obter acesso. As entidades de serviço fornecem uma maneira de criar uma conta não interativa associada à sua identidade para a qual você concede apenas os privilégios de que seu aplicativo precisa para ser executado.

Primeiro, faça logon no Azure PowerShell:

```powershell
Login-AzureRmAccount
```

Observe as informações sobre seu locatário e assinatura:

```plaintext
Environment           : AzureCloud
Account               : jane@contoso.com
TenantId              : 43413cc1-5886-4711-9804-8cfea3d1c3ee
SubscriptionId        : 15dbcfa8-4b93-4c9a-881c-6189d39f04d4
SubscriptionName      : my-subscription
CurrentStorageAccount : 
```

[Criar uma entidade de serviço usando o PowerShell](/powershell/azure/create-azure-service-principal-azureps), da seguinte maneira:

```powershell
# Create the service principal (use a strong password)
$sp = New-AzureRmADServicePrincipal -DisplayName "AzureDotNetTest" -Password "password"

# Give it the permissions it needs...
New-AzureRmRoleAssignment -ServicePrincipalName $sp.ApplicationId -RoleDefinitionName Contributor

# Display the Application ID, because we'll need it later.
$sp | Select DisplayName, ApplicationId
```

Anote o ApplicationId:

```plaintext
DisplayName     ApplicationId
-----------     -------------
AzureDotNetTest a2ab11af-01aa-4759-8345-7803287dbd39
```
