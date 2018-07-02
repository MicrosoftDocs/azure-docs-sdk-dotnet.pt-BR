---
title: Bibliotecas da CDN do Azure para .NET
description: Referência para bibliotecas da CDN do Azure para .NET
keywords: Azure, .NET, SDK, API, CDN
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: cdn
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 4e5b56ca7e316f3a53d8c6d37fdd90c5d7130e1e
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065816"
---
# <a name="azure-cdn-libraries-for-net"></a>Bibliotecas da CDN do Azure para .NET

## <a name="overview"></a>Visão geral

A CDN (Rede de Distribuição de Conteúdo) do Azure armazena em cache conteúdo Web estático em locais estrategicamente posicionados para fornecer taxa de transferência máxima para o fornecimento de conteúdo aos usuários. A CDN oferece aos desenvolvedores uma solução global de fornecimento de conteúdo de alta largura de banda armazenando em cache o conteúdo em nós físicos em todo o mundo.

Para saber mais sobre a CDN do Azure, confira [Visão geral da Rede de Distribuição de Conteúdo do Azure](https://docs.microsoft.com/azure/cdn/cdn-overview).


## <a name="management-library"></a>Biblioteca de gerenciamento

Você pode usar a Biblioteca da CDN do Azure para .NET a fim de automatizar a criação e o gerenciamento de perfis e pontos de extremidade da CDN. 

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a>Exemplo

Este exemplo cria um novo perfil de CDN com um novo ponto de extremidade apontado para `www.contoso.com`.

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.Cdn.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

ICdnProfile profileDefinition = azure.CdnProfiles.Define("CdnProfileName")
    .WithRegion(Region.USCentral)
    .WithExistingResourceGroup("ResourceGroupName")
    .WithStandardVerizonSku()
    .WithNewEndpoint("www.contoso.com")
    .Create();

```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a>Exemplos

* [Introdução à CDN - Gerenciar CDN - no .NET](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
