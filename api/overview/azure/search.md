---
title: Bibliotecas do Azure Search para .NET
description: Referência para bibliotecas do Azure Search para .NET
keywords: Azure, .NET, SDK, API, Search
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: search
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 5062d444b859711d7f87a0ecbd65e6b204c04b16
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065276"
---
# <a name="azure-search-libraries-for-net"></a><span data-ttu-id="f5dc2-104">Bibliotecas do Azure Search para .NET</span><span class="sxs-lookup"><span data-stu-id="f5dc2-104">Azure Search libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f5dc2-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f5dc2-105">Overview</span></span>

<span data-ttu-id="f5dc2-106">O [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) é um serviço de pesquisa na nuvem totalmente gerenciado que fornece uma experiência de pesquisa avançada em dados de aplicativos Web, móveis e empresariais.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-106">[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) is a fully managed cloud search service that provides a rich search experience over data in web, mobile, and enterprise applications.</span></span>

## <a name="client-library"></a><span data-ttu-id="f5dc2-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="f5dc2-107">Client library</span></span>

<span data-ttu-id="f5dc2-108">Use a biblioteca de cliente do Azure Search para acessar e executar operações de indexação e pesquisa em um serviço de pesquisa, índice, documentos ou outro objeto.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-108">Use the Azure Search client library to access and execute indexing and search operations on a search service, index, documents, or other object.</span></span> <span data-ttu-id="f5dc2-109">Para obter uma introdução passo a passo, confira [Como usar o Azure Search em um aplicativo .NET](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="f5dc2-109">For a step-by-step introduction, see [How to use Azure Search from a .NET application](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).</span></span>

<span data-ttu-id="f5dc2-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Search) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f5dc2-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f5dc2-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5dc2-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Search
```

```bash
dotnet add package Microsoft.Azure.Search
```

### <a name="code-example"></a><span data-ttu-id="f5dc2-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f5dc2-112">Code Example</span></span>

```csharp
/* Include these 'using' directives:
   using Microsoft.Azure.Search;
   using Microsoft.Azure.Search.Models;
*/

// A service endpoint and an api-key are required on a connection.
// Set them in a config file (not shown) and then connect to the client.
IConfigurationBuilder builder = new ConfigurationBuilder().AddJsonFile("appsettings.json");
IConfigurationRoot configuration = builder.Build();

SearchServiceClient serviceClient = CreateSearchServiceClient(configuration);

// Create an index named hotels
ISearchIndexClient indexClient = serviceClient.Indexes.GetClient("hotels");

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f5dc2-113">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="f5dc2-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/search/client)


## <a name="management-library"></a><span data-ttu-id="f5dc2-114">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f5dc2-114">Management library</span></span>

<span data-ttu-id="f5dc2-115">Use a biblioteca de gerenciamento do Azure Search para provisionar um serviço, gerenciar chaves de API e ajustar os recursos.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-115">Use the Azure Search management library to provision a service, manage api-keys, and adjust resources.</span></span> <span data-ttu-id="f5dc2-116">O gerenciamento de serviço tem uma dependência no Azure Resource Manager para identificação de locatário e assinante.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-116">Service management has a dependency on Azure Resource Manager for subscriber and tenant identification.</span></span> <span data-ttu-id="f5dc2-117">Normalmente, a autenticação e o registro de aplicativo com o Azure Active Directory também são necessários para dar suporte ao fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-117">Typically, authentication and application registration with Azure Active Directory is also necessary to support the workflow.</span></span> <span data-ttu-id="f5dc2-118">Para obter uma introdução sobre o provisionamento do serviço Azure Search, confira [Como usar a API REST de gerenciamento](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).</span><span class="sxs-lookup"><span data-stu-id="f5dc2-118">For an introduction to Azure Search service provisioning, see [How to use the Management REST API](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).</span></span>

<span data-ttu-id="f5dc2-119">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f5dc2-119">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f5dc2-120">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5dc2-120">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Search
```

```bash
dotnet add package Microsoft.Azure.Management.Search
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f5dc2-121">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f5dc2-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/search/management)

## <a name="samples"></a><span data-ttu-id="f5dc2-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f5dc2-122">Samples</span></span>

 + [<span data-ttu-id="f5dc2-123">Exemplos do Azure/search-dotnet-getting-started</span><span class="sxs-lookup"><span data-stu-id="f5dc2-123">Azure Samples / search-dotnet-getting-started</span></span>](https://github.com/Azure-Samples/search-dotnet-getting-started)
 + [<span data-ttu-id="f5dc2-124">Exemplos do Azure/search-dotnet-management-api</span><span class="sxs-lookup"><span data-stu-id="f5dc2-124">Azure Samples / search-dotnet-management-api</span></span>](https://github.com/Azure-Samples/search-dotnet-management-api)

<span data-ttu-id="f5dc2-125">Encontre mais amostras de pesquisa no [repositório de exemplos do Azure](https://github.com/Azure-Samples/) no Github.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-125">Find more search samples in the [Azure samples repository](https://github.com/Azure-Samples/) on Github.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
