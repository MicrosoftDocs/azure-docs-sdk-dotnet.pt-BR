---
title: Bibliotecas do Azure Key Vault para .NET
description: "Referência para bibliotecas do Azure Key Vault para .NET"
keywords: Azure, .NET, SDK, API, Key Vault
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 77a4e710e858bbeb98579a7b540b52b4cb9dd7b0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-key-vault-libraries-for-net"></a><span data-ttu-id="26f7e-104">Bibliotecas do Azure Key Vault para .NET</span><span class="sxs-lookup"><span data-stu-id="26f7e-104">Azure Key Vault libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="26f7e-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="26f7e-105">Overview</span></span>

<span data-ttu-id="26f7e-106">O Cofre da Chave do Azure ajuda a proteger chaves criptográficas e segredos usados por aplicativos e serviços em nuvem.</span><span class="sxs-lookup"><span data-stu-id="26f7e-106">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span>

<span data-ttu-id="26f7e-107">Leia mais sobre [O que é o Key Vault?](/azure/key-vault/key-vault-whatis) e a [Introdução ao Azure Key Vault](/azure/key-vault/key-vault-get-started) ou aprenda como [Usar o Key Vault de um aplicativo Web](/azure/key-vault/key-vault-use-from-web-application).</span><span class="sxs-lookup"><span data-stu-id="26f7e-107">Read more about [What is Key Vault?](/azure/key-vault/key-vault-whatis) then [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started) or learn how to [Use Key Vault from a web app](/azure/key-vault/key-vault-use-from-web-application).</span></span>

## <a name="client-library"></a><span data-ttu-id="26f7e-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="26f7e-108">Client library</span></span>

<span data-ttu-id="26f7e-109">Use a biblioteca de cliente para gerenciar chaves e ativos relacionados, como certificados e segredos.</span><span class="sxs-lookup"><span data-stu-id="26f7e-109">Use the client library to manage keys and related assets such as certificates and secrets.</span></span>

<span data-ttu-id="26f7e-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="26f7e-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="26f7e-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26f7e-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a><span data-ttu-id="26f7e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26f7e-112">Example</span></span>

<span data-ttu-id="26f7e-113">O exemplo a seguir recupera o segredo para uma chave específica que é identificada nas configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26f7e-113">The following example retrieves the secret for a specific key that is identified in the application settings.</span></span>

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="26f7e-114">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="26f7e-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a><span data-ttu-id="26f7e-115">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="26f7e-115">Management library</span></span>

<span data-ttu-id="26f7e-116">Use a biblioteca de gerenciamento para criar, excluir e consultar os cofres de chaves.</span><span class="sxs-lookup"><span data-stu-id="26f7e-116">Use the management library to create, delete, and query key vaults.</span></span>

<span data-ttu-id="26f7e-117">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="26f7e-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="26f7e-118">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26f7e-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a><span data-ttu-id="26f7e-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26f7e-119">Example</span></span>

<span data-ttu-id="26f7e-120">O exemplo a seguir demonstra como criar um novo cofre de chaves para determinado grupo de recursos e local.</span><span class="sxs-lookup"><span data-stu-id="26f7e-120">The following example demonstrates how to create a new key vault for a given resource group and location.</span></span>

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
> [<span data-ttu-id="26f7e-121">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="26f7e-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a><span data-ttu-id="26f7e-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="26f7e-122">Samples</span></span>

* [<span data-ttu-id="26f7e-123">Baixar os exemplos de cliente Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="26f7e-123">Download the Azure Key Vault client samples</span></span>](https://www.microsoft.com/download/details.aspx?id=45343)
* [<span data-ttu-id="26f7e-124">Introdução à criptografia do lado cliente do Azure no .NET</span><span class="sxs-lookup"><span data-stu-id="26f7e-124">Getting Started with Azure Client Side Encryption in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/)


<span data-ttu-id="26f7e-125">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="26f7e-125">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
