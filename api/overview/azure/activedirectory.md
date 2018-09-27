---
title: Bibliotecas do Azure Active Directory para .NET
description: Referência para bibliotecas do Azure Active Directory para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: active-directory
ms.openlocfilehash: 0226f06546f7dc14b9ab3392008744754d47a19a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190219"
---
# <a name="azure-active-directory-libraries-for-net"></a><span data-ttu-id="74c32-103">Bibliotecas do Azure Active Directory para .NET</span><span class="sxs-lookup"><span data-stu-id="74c32-103">Azure Active Directory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="74c32-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="74c32-104">Overview</span></span>

<span data-ttu-id="74c32-105">Conecte usuários e gerencie o acesso a aplicativos e APIs com o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="74c32-105">Sign-on users and manage access to applications and APIs with Azure Active Directory.</span></span>

<span data-ttu-id="74c32-106">Para começar a usar o Azure Active Directory, confira [Conectar-se e desconectar-se de aplicativo Web ASP.NET com o Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span><span class="sxs-lookup"><span data-stu-id="74c32-106">To get started with Azure Active Directory, see [ASP.NET web app sign-in and sign-out with Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="74c32-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="74c32-107">Client library</span></span>

<span data-ttu-id="74c32-108">Conecte e autenticar usuários ou aplicativos por meio de OAuth2, OpenID Connect, autenticação da API do Graph do Active Directory ou [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span><span class="sxs-lookup"><span data-stu-id="74c32-108">Connect and authenticate users or applications over OAuth2, OpenID Connect, Active Directory Graph API authentication or [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span></span>

<span data-ttu-id="74c32-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="74c32-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="74c32-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="74c32-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a><span data-ttu-id="74c32-111">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="74c32-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a><span data-ttu-id="74c32-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="74c32-112">Code Example</span></span>

<span data-ttu-id="74c32-113">Recupere um token de acesso para um aplicativo de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="74c32-113">Retrieve an access token for a desktop application.</span></span>

```csharp
/* Include this "using" directive...
using Microsoft.IdentityModel.Clients.ActiveDirectory;
*/

AuthenticationResult result = null;
AuthenticationContext authContext = new AuthenticationContext("https://someauthority.com");
try
{
    result = await authContext.AcquireTokenAsync(graphResourceId, clientId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
}
catch (AdalException ex)
{
    // An unexpected error occurred, or user canceled the sign in.
    if (ex.ErrorCode != "access_denied")
        MessageBox.Show(ex.Message);

    return;
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="74c32-114">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="74c32-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a><span data-ttu-id="74c32-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="74c32-115">Samples</span></span>

* [<span data-ttu-id="74c32-116">Usar o OpenID Connect para autenticar os usuários de um locatário do Azure AD</span><span class="sxs-lookup"><span data-stu-id="74c32-116">Use OpenID Connect to authenticate users from an Azure AD tenant</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect)
* [<span data-ttu-id="74c32-117">Usar Oauth2 para chamar uma API Web com permissões de aplicativo</span><span class="sxs-lookup"><span data-stu-id="74c32-117">Use Oauth2 to call a web API with application permissions</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity)
* [<span data-ttu-id="74c32-118">Usar RBAC (controle de acesso baseado em função) em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="74c32-118">Use role-based access control (RBAC) in an application</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims)

<span data-ttu-id="74c32-119">Explorar o conjunto completo de [exemplos de código do Azure Active Directory](/azure/active-directory/develop/active-directory-code-samples).</span><span class="sxs-lookup"><span data-stu-id="74c32-119">Explore the full collection of [Azure Active Directory code samples](/azure/active-directory/develop/active-directory-code-samples).</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
