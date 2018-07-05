<span data-ttu-id="78a03-101">Seu aplicativo .NET precisa de permissões para ler e criar recursos na sua assinatura do Azure a fim de usar as bibliotecas de gerenciamento do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="78a03-101">Your .NET application needs permissions to read and create resources in your Azure subscription in order to use the Azure Management Libraries for .NET.</span></span> <span data-ttu-id="78a03-102">Crie uma entidade de serviço e configure seu aplicativo para ser executado com suas credenciais e obter acesso.</span><span class="sxs-lookup"><span data-stu-id="78a03-102">Create a service principal and configure your app to run with its credentials to grant this access.</span></span> <span data-ttu-id="78a03-103">As entidades de serviço fornecem uma maneira de criar uma conta não interativa associada à sua identidade para a qual você concede apenas os privilégios de que seu aplicativo precisa para ser executado.</span><span class="sxs-lookup"><span data-stu-id="78a03-103">Service principals provide a way to create a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="78a03-104">Primeiro, faça logon no Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="78a03-104">First, login to Azure PowerShell:</span></span>

```powershell
Login-AzureRmAccount
```

<span data-ttu-id="78a03-105">Observe as informações sobre seu locatário e assinatura:</span><span class="sxs-lookup"><span data-stu-id="78a03-105">Note the information displayed about your tenant and subscription:</span></span>

```plaintext
Environment           : AzureCloud
Account               : jane@contoso.com
TenantId              : 43413cc1-5886-4711-9804-8cfea3d1c3ee
SubscriptionId        : 15dbcfa8-4b93-4c9a-881c-6189d39f04d4
SubscriptionName      : my-subscription
CurrentStorageAccount : 
```

<span data-ttu-id="78a03-106">[Criar uma entidade de serviço usando o PowerShell](/powershell/azure/create-azure-service-principal-azureps), como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="78a03-106">[Create a service principal using PowerShell](/powershell/azure/create-azure-service-principal-azureps) as shown below.</span></span> 

> [!NOTE]
> <span data-ttu-id="78a03-107">Se o cmdlet `New-AzureRmADServicePrincipal` abaixo retornar "Outro objeto com o mesmo valor da propriedade identifierUris já existe", já haverá uma entidade de serviço com esse nome em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="78a03-107">If the `New-AzureRmADServicePrincipal` cmdlet below returns "Another object with the same value for property identifierUris already exists," there is already a service principal by that name in your tenant.</span></span> <span data-ttu-id="78a03-108">Use um valor diferente para o parâmetro **DisplayName**.</span><span class="sxs-lookup"><span data-stu-id="78a03-108">Use a different value for the **DisplayName** parameter.</span></span> 

```powershell
# Create the service principal (use a strong password)
$cred = Get-Credential
$sp = New-AzureRmADServicePrincipal -DisplayName "AzureDotNetTest" -Password $cred.Password

# Give it the permissions it needs...
New-AzureRmRoleAssignment -ServicePrincipalName $sp.ApplicationId -RoleDefinitionName Contributor

# Display the Application ID, because we'll need it later.
$sp | Select DisplayName, ApplicationId
```

<span data-ttu-id="78a03-109">Anote o ApplicationId:</span><span class="sxs-lookup"><span data-stu-id="78a03-109">Make sure to note the ApplicationId:</span></span>

```plaintext
DisplayName     ApplicationId
-----------     -------------
AzureDotNetTest a2ab11af-01aa-4759-8345-7803287dbd39
```
