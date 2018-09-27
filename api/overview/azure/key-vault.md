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
# <a name="azure-key-vault-libraries-for-net"></a><span data-ttu-id="c2bab-103">Bibliotecas do Azure Key Vault para .NET</span><span class="sxs-lookup"><span data-stu-id="c2bab-103">Azure Key Vault libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="c2bab-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="c2bab-104">Overview</span></span>

<span data-ttu-id="c2bab-105">O Cofre da Chave do Azure ajuda a proteger chaves criptográficas e segredos usados por aplicativos e serviços em nuvem.</span><span class="sxs-lookup"><span data-stu-id="c2bab-105">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span>

<span data-ttu-id="c2bab-106">Leia mais sobre [O que é o Key Vault?](/azure/key-vault/key-vault-whatis) e a [Introdução ao Azure Key Vault](/azure/key-vault/key-vault-get-started) ou aprenda como [Usar o Key Vault de um aplicativo Web](/azure/key-vault/key-vault-use-from-web-application).</span><span class="sxs-lookup"><span data-stu-id="c2bab-106">Read more about [What is Key Vault?](/azure/key-vault/key-vault-whatis) then [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started) or learn how to [Use Key Vault from a web app](/azure/key-vault/key-vault-use-from-web-application).</span></span>

## <a name="client-library"></a><span data-ttu-id="c2bab-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="c2bab-107">Client library</span></span>

<span data-ttu-id="c2bab-108">Use a biblioteca de cliente para gerenciar chaves e ativos relacionados, como certificados e segredos.</span><span class="sxs-lookup"><span data-stu-id="c2bab-108">Use the client library to manage keys and related assets such as certificates and secrets.</span></span>

<span data-ttu-id="c2bab-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="c2bab-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="c2bab-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2bab-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a><span data-ttu-id="c2bab-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2bab-111">Example</span></span>

<span data-ttu-id="c2bab-112">O exemplo a seguir recupera o segredo para uma chave específica que é identificada nas configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2bab-112">The following example retrieves the secret for a specific key that is identified in the application settings.</span></span>

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="c2bab-113">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="c2bab-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a><span data-ttu-id="c2bab-114">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c2bab-114">Management library</span></span>

<span data-ttu-id="c2bab-115">Use a biblioteca de gerenciamento para criar, excluir e consultar os cofres de chaves.</span><span class="sxs-lookup"><span data-stu-id="c2bab-115">Use the management library to create, delete, and query key vaults.</span></span>

<span data-ttu-id="c2bab-116">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="c2bab-116">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="c2bab-117">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2bab-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a><span data-ttu-id="c2bab-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2bab-118">Example</span></span>

<span data-ttu-id="c2bab-119">O exemplo a seguir demonstra como criar um novo cofre de chaves para determinado grupo de recursos e local.</span><span class="sxs-lookup"><span data-stu-id="c2bab-119">The following example demonstrates how to create a new key vault for a given resource group and location.</span></span>

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
> [<span data-ttu-id="c2bab-120">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c2bab-120">Explore the management APIs</span></span>](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a><span data-ttu-id="c2bab-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c2bab-121">Samples</span></span>

* [<span data-ttu-id="c2bab-122">Baixar os exemplos de cliente Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="c2bab-122">Download the Azure Key Vault client samples</span></span>](https://www.microsoft.com/download/details.aspx?id=45343)
* [<span data-ttu-id="c2bab-123">Introdução à criptografia do lado cliente do Azure no .NET</span><span class="sxs-lookup"><span data-stu-id="c2bab-123">Getting Started with Azure Client Side Encryption in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/)


<span data-ttu-id="c2bab-124">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c2bab-124">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
