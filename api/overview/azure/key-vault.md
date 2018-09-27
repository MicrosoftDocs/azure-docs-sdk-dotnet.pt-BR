---
title: Bibliotecas do Azure Key Vault para .NET
description: Referência para bibliotecas do Azure Key Vault para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: key-vault
ms.openlocfilehash: a42eb9684bcfb8e8d2209235f61bbf6962cf5e9e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190549"
---
# <a name="azure-key-vault-libraries-for-net"></a>Bibliotecas do Azure Key Vault para .NET

## <a name="overview"></a>Visão geral

O Cofre da Chave do Azure ajuda a proteger chaves criptográficas e segredos usados por aplicativos e serviços em nuvem.

Leia mais sobre [O que é o Key Vault?](/azure/key-vault/key-vault-whatis) e a [Introdução ao Azure Key Vault](/azure/key-vault/key-vault-get-started) ou aprenda como [Usar o Key Vault de um aplicativo Web](/azure/key-vault/key-vault-use-from-web-application).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de cliente para gerenciar chaves e ativos relacionados, como certificados e segredos.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a>Exemplo

O exemplo a seguir recupera o segredo para uma chave específica que é identificada nas configurações do aplicativo.

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para criar, excluir e consultar os cofres de chaves.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a>Exemplo

O exemplo a seguir demonstra como criar um novo cofre de chaves para determinado grupo de recursos e local.

```csharp
using (KeyVaultManagementClient client = new KeyVaultManagementClient(
    new TokenCloudCredentials(subscriptionId, accessToken)))
{
    client.Vaults.CreateOrUpdate(resourceGroupName, "myKeyVault", new VaultCreateOrUpdateParameters
    {
        Properties = new VaultProperties
        {
            EnabledForDeployment = true,
            EnabledForDiskEncryption = true,
            EnabledForTemplateDeployment = true,
            Location = resourceGroupLocation,
            // SKU level, access policies, tenants, etc.
        }
    });
}
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a>Exemplos

* [Baixar os exemplos de cliente Azure Key Vault](https://www.microsoft.com/download/details.aspx?id=45343)
* [Introdução à criptografia do lado cliente do Azure no .NET](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/)


Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
