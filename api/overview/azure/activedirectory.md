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
# <a name="azure-active-directory-libraries-for-net"></a>Bibliotecas do Azure Active Directory para .NET

## <a name="overview"></a>Visão geral

Conecte usuários e gerencie o acesso a aplicativos e APIs com o Azure Active Directory.

Para começar a usar o Azure Active Directory, confira [Conectar-se e desconectar-se de aplicativo Web ASP.NET com o Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).

## <a name="client-library"></a>Biblioteca do cliente

Conecte e autenticar usuários ou aplicativos por meio de OAuth2, OpenID Connect, autenticação da API do Graph do Active Directory ou [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a>Exemplo de código

Recupere um token de acesso para um aplicativo de área de trabalho.

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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a>Exemplos

* [Usar o OpenID Connect para autenticar os usuários de um locatário do Azure AD](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect)
* [Usar Oauth2 para chamar uma API Web com permissões de aplicativo](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity)
* [Usar RBAC (controle de acesso baseado em função) em um aplicativo](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims)

Explorar o conjunto completo de [exemplos de código do Azure Active Directory](/azure/active-directory/develop/active-directory-code-samples).

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
