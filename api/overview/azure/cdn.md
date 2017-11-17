---
title: Bibliotecas da CDN do Azure para .NET
description: "Referência para bibliotecas da CDN do Azure para .NET"
keywords: Azure, .NET, SDK, API, CDN
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cdn
ms.custom: devcenter, svc-overview
ms.openlocfilehash: afc63f943fcac3afd9afb7d85f6e699079829244
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-cdn-libraries-for-net"></a><span data-ttu-id="59530-104">Bibliotecas da CDN do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="59530-104">Azure CDN libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="59530-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="59530-105">Overview</span></span>

<span data-ttu-id="59530-106">A CDN (Rede de Distribuição de Conteúdo) do Azure armazena em cache conteúdo Web estático em locais estrategicamente posicionados para fornecer taxa de transferência máxima para o fornecimento de conteúdo aos usuários.</span><span class="sxs-lookup"><span data-stu-id="59530-106">The Azure Content Delivery Network (CDN) caches static web content at strategically placed locations to provide maximum throughput for delivering content to users.</span></span> <span data-ttu-id="59530-107">A CDN oferece aos desenvolvedores uma solução global de fornecimento de conteúdo de alta largura de banda armazenando em cache o conteúdo em nós físicos em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="59530-107">The CDN offers developers a global solution for delivering high-bandwidth content by caching the content at physical nodes across the world.</span></span>

<span data-ttu-id="59530-108">Para saber mais sobre a CDN do Azure, confira [Visão geral da Rede de Distribuição de Conteúdo do Azure](https://docs.microsoft.com/azure/cdn/cdn-overview).</span><span class="sxs-lookup"><span data-stu-id="59530-108">To learn more about Azure CDN, see [Overview of the Azure Content Delivery Network](https://docs.microsoft.com/azure/cdn/cdn-overview).</span></span>


## <a name="management-library"></a><span data-ttu-id="59530-109">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="59530-109">Management library</span></span>

<span data-ttu-id="59530-110">Você pode usar a Biblioteca da CDN do Azure para .NET a fim de automatizar a criação e o gerenciamento de perfis e pontos de extremidade da CDN.</span><span class="sxs-lookup"><span data-stu-id="59530-110">You can use the Azure CDN Library for .NET to automate creation and management of CDN profiles and endpoints.</span></span> 

<span data-ttu-id="59530-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="59530-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="59530-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59530-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a><span data-ttu-id="59530-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59530-113">Example</span></span>

<span data-ttu-id="59530-114">Este exemplo cria um novo perfil de CDN com um novo ponto de extremidade apontado para `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="59530-114">This example creates a new CDN profile with a new endpoint pointed to `www.contoso.com`.</span></span>

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
> [<span data-ttu-id="59530-115">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="59530-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a><span data-ttu-id="59530-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="59530-116">Samples</span></span>

* [<span data-ttu-id="59530-117">Introdução à CDN - Gerenciar CDN - no .NET</span><span class="sxs-lookup"><span data-stu-id="59530-117">Getting started with CDN - Manage CDN - in .NET</span></span>](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
