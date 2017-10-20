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
# <a name="azure-active-directory-libraries-for-net"></a>Bibliotecas do Azure Active Directory para .NET

## <a name="overview"></a>Visão geral

Conecte usuários e gerencie o acesso a aplicativos e APIs com o Azure Active Directory.

Para começar a usar o Azure Active Directory, confira [Conectar-se e desconectar-se de aplicativo Web ASP.NET com o Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).

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

Explorar o conjunto completo de [exemplos de código do Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-code-samples).

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
