---
title: Bibliotecas do Azure Active Directory para .NET
description: "Referência para bibliotecas do Azure Active Directory para .NET"
keywords: Azure, .NET SDK, API, AAD, Active Directory
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: adbe907888e49066b6d67a4fb26410a6f6b3b095
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-active-directory-libraries-for-net"></a><span data-ttu-id="1a22c-104">Bibliotecas do Azure Active Directory para .NET</span><span class="sxs-lookup"><span data-stu-id="1a22c-104">Azure Active Directory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="1a22c-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="1a22c-105">Overview</span></span>

<span data-ttu-id="1a22c-106">Conecte usuários e gerencie o acesso a aplicativos e APIs com o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1a22c-106">Sign-on users and manage access to applications and APIs with Azure Active Directory.</span></span>

<span data-ttu-id="1a22c-107">Para começar a usar o Azure Active Directory, confira [Conectar-se e desconectar-se de aplicativo Web ASP.NET com o Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span><span class="sxs-lookup"><span data-stu-id="1a22c-107">To get started with Azure Active Directory, see [ASP.NET web app sign-in and sign-out with Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="1a22c-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="1a22c-108">Client library</span></span>

<span data-ttu-id="1a22c-109">Conecte e autenticar usuários ou aplicativos por meio de OAuth2, OpenID Connect, autenticação da API do Graph do Active Directory ou [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span><span class="sxs-lookup"><span data-stu-id="1a22c-109">Connect and authenticate users or applications over OAuth2, OpenID Connect, Active Directory Graph API authentication or [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span></span>

<span data-ttu-id="1a22c-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="1a22c-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1a22c-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1a22c-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a><span data-ttu-id="1a22c-112">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1a22c-112">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a><span data-ttu-id="1a22c-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="1a22c-113">Code Example</span></span>

<span data-ttu-id="1a22c-114">Recupere um token de acesso para um aplicativo de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1a22c-114">Retrieve an access token for a desktop application.</span></span>

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
> [<span data-ttu-id="1a22c-115">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="1a22c-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a><span data-ttu-id="1a22c-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1a22c-116">Samples</span></span>

* [<span data-ttu-id="1a22c-117">Usar o OpenID Connect para autenticar os usuários de um locatário do Azure AD</span><span class="sxs-lookup"><span data-stu-id="1a22c-117">Use OpenID Connect to authenticate users from an Azure AD tenant</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect)
* [<span data-ttu-id="1a22c-118">Usar Oauth2 para chamar uma API Web com permissões de aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a22c-118">Use Oauth2 to call a web API with application permissions</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity)
* [<span data-ttu-id="1a22c-119">Usar RBAC (controle de acesso baseado em função) em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a22c-119">Use role-based access control (RBAC) in an application</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims)

<span data-ttu-id="1a22c-120">Explorar o conjunto completo de [exemplos de código do Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-code-samples).</span><span class="sxs-lookup"><span data-stu-id="1a22c-120">Explore the full collection of [Azure Active Directory code samples](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-code-samples).</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
