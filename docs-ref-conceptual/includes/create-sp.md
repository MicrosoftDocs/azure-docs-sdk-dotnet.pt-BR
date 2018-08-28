Seu aplicativo .NET precisa de permissões para ler e criar recursos na sua assinatura do Azure a fim de usar as bibliotecas de gerenciamento do Azure para .NET. Crie uma entidade de serviço e configure seu aplicativo para ser executado com suas credenciais e obter acesso. As entidades de serviço fornecem uma maneira de criar uma conta não interativa associada à sua identidade para a qual você concede apenas os privilégios de que seu aplicativo precisa para ser executado.

Primeiro, faça logon no [Azure Cloud Shell](https://shell.azure.com/bash). Verifique se você está usando atualmente a assinatura na qual deseja a entidade de serviço criada. 

```azurecli-interactive
az account show
```

As informações da assinatura são exibidas.

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

Se você não estiver conectado à assinatura correta, selecione a correta digitando `az account set -s <name or ID of subscription>`.

Crie a entidade de serviço com o seguinte comando:

```azurecli-interactive
az ad sp create-for-rbac --sdk-auth
```

As informações da entidade de serviço são exibidas como JSON.

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

Copie e cole a saída JSON em um editor de texto para usar posteriormente.
