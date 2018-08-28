<span data-ttu-id="f0a7f-101">Seu aplicativo .NET precisa de permissões para ler e criar recursos na sua assinatura do Azure a fim de usar as bibliotecas de gerenciamento do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-101">Your .NET application needs permissions to read and create resources in your Azure subscription in order to use the Azure Management Libraries for .NET.</span></span> <span data-ttu-id="f0a7f-102">Crie uma entidade de serviço e configure seu aplicativo para ser executado com suas credenciais e obter acesso.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-102">Create a service principal and configure your app to run with its credentials to grant this access.</span></span> <span data-ttu-id="f0a7f-103">As entidades de serviço fornecem uma maneira de criar uma conta não interativa associada à sua identidade para a qual você concede apenas os privilégios de que seu aplicativo precisa para ser executado.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-103">Service principals provide a way to create a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="f0a7f-104">Primeiro, faça logon no [Azure Cloud Shell](https://shell.azure.com/bash).</span><span class="sxs-lookup"><span data-stu-id="f0a7f-104">First, login to [Azure Cloud Shell](https://shell.azure.com/bash).</span></span> <span data-ttu-id="f0a7f-105">Verifique se você está usando atualmente a assinatura na qual deseja a entidade de serviço criada.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-105">Verify you are currently using the subscription in which you want the service principal created.</span></span> 

```azurecli-interactive
az account show
```

<span data-ttu-id="f0a7f-106">As informações da assinatura são exibidas.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-106">Your subscription information is displayed.</span></span>

```json
{
  "environmentName": "AzureCloud",
  "id": "15dbcfa8-4b93-4c9a-881c-6189d39f04d4",
  "isDefault": true,
  "name": "my-subscription",
  "state": "Enabled",
  "tenantId": "43413cc1-5886-4711-9804-8cfea3d1c3ee",
  "user": {
    "cloudShellID": true,
    "name": "jane@contoso.com",
    "type": "user"
  }
}
```

<span data-ttu-id="f0a7f-107">Se você não estiver conectado à assinatura correta, selecione a correta digitando `az account set -s <name or ID of subscription>`.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-107">If you're not logged into the correct subscription, select the correct one by typing `az account set -s <name or ID of subscription>`.</span></span>

<span data-ttu-id="f0a7f-108">Crie a entidade de serviço com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f0a7f-108">Create the service principal with the following command:</span></span>

```azurecli-interactive
az ad sp create-for-rbac --sdk-auth
```

<span data-ttu-id="f0a7f-109">As informações da entidade de serviço são exibidas como JSON.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-109">The service principal information is displayed as JSON.</span></span>

```json
{
  "clientId": "b52dd125-9272-4b21-9862-0be667bdf6dc",
  "clientSecret": "ebc6e170-72b2-4b6f-9de2-99410964d2d0",
  "subscriptionId": "ffa52f27-be12-4cad-b1ea-c2c241b6cceb",
  "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```

<span data-ttu-id="f0a7f-110">Copie e cole a saída JSON em um editor de texto para usar posteriormente.</span><span class="sxs-lookup"><span data-stu-id="f0a7f-110">Copy and paste the JSON output to a text editor for use later.</span></span>
