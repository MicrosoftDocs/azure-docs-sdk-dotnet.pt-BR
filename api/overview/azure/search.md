---
title: Bibliotecas do Azure Search para .NET
description: "Referência para bibliotecas do Azure Search para .NET"
keywords: Azure, .NET, SDK, API, Search
author: spboyer
ms.author: casoper
manager: douge
ms.date: 07/10/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 5330e0642bc27c97c4acc0857d4b92e6fc2a027c
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-search-libraries-for-net"></a><span data-ttu-id="3185f-104">Bibliotecas do Azure Search para .NET</span><span class="sxs-lookup"><span data-stu-id="3185f-104">Azure Search libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="3185f-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3185f-105">Overview</span></span>

<span data-ttu-id="3185f-106">O [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) é um serviço de pesquisa na nuvem totalmente gerenciado que fornece uma experiência de pesquisa avançada em dados de aplicativos Web, móveis e empresariais.</span><span class="sxs-lookup"><span data-stu-id="3185f-106">[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) is a fully managed cloud search service that provides a rich search experience over data in web, mobile, and enterprise applications.</span></span>

## <a name="client-library"></a><span data-ttu-id="3185f-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="3185f-107">Client library</span></span>

<span data-ttu-id="3185f-108">Use a biblioteca de cliente do Azure Search para acessar e executar operações de indexação e pesquisa em um serviço de pesquisa, índice, documentos ou outro objeto.</span><span class="sxs-lookup"><span data-stu-id="3185f-108">Use the Azure Search client library to access and execute indexing and search operations on a search service, index, documents, or other object.</span></span> <span data-ttu-id="3185f-109">Para obter uma introdução passo a passo, confira [Como usar o Azure Search em um aplicativo .NET](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="3185f-109">For a step-by-step introduction, see [How to use Azure Search from a .NET application](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).</span></span>

<span data-ttu-id="3185f-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Search) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="3185f-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="3185f-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3185f-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Search
```

```bash
dotnet add package Microsoft.Azure.Search
```

### <a name="code-example"></a><span data-ttu-id="3185f-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3185f-112">Code Example</span></span>

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
> [<span data-ttu-id="3185f-113">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="3185f-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/search/client)


## <a name="management-library"></a><span data-ttu-id="3185f-114">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="3185f-114">Management library</span></span>

<span data-ttu-id="3185f-115">Use a biblioteca de gerenciamento do Azure Search para provisionar um serviço, gerenciar chaves de API e ajustar os recursos.</span><span class="sxs-lookup"><span data-stu-id="3185f-115">Use the Azure Search management library to provision a service, manage api-keys, and adjust resources.</span></span> <span data-ttu-id="3185f-116">O gerenciamento de serviço tem uma dependência no Azure Resource Manager para identificação de locatário e assinante.</span><span class="sxs-lookup"><span data-stu-id="3185f-116">Service management has a dependency on Azure Resource Manager for subscriber and tenant identification.</span></span> <span data-ttu-id="3185f-117">Normalmente, a autenticação e o registro de aplicativo com o Azure Active Directory também são necessários para dar suporte ao fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3185f-117">Typically, authentication and application registration with Azure Active Directory is also necessary to support the workflow.</span></span> <span data-ttu-id="3185f-118">Para obter uma introdução sobre o provisionamento do serviço Azure Search, confira [Como usar a API REST de gerenciamento](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).</span><span class="sxs-lookup"><span data-stu-id="3185f-118">For an introduction to Azure Search service provisioning, see [How to use the Management REST API](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).</span></span>

<span data-ttu-id="3185f-119">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="3185f-119">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="3185f-120">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3185f-120">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Search
```

```bash
dotnet add package Microsoft.Azure.Management.Search
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="3185f-121">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="3185f-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/search/management)

## <a name="samples"></a><span data-ttu-id="3185f-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3185f-122">Samples</span></span>

 + [<span data-ttu-id="3185f-123">Exemplos do Azure/search-dotnet-getting-started</span><span class="sxs-lookup"><span data-stu-id="3185f-123">Azure Samples / search-dotnet-getting-started</span></span>](https://github.com/Azure-Samples/search-dotnet-getting-started)
 + [<span data-ttu-id="3185f-124">Exemplos do Azure/search-dotnet-management-api</span><span class="sxs-lookup"><span data-stu-id="3185f-124">Azure Samples / search-dotnet-management-api</span></span>](https://github.com/Azure-Samples/search-dotnet-management-api)

<span data-ttu-id="3185f-125">Encontre mais amostras de pesquisa no [repositório de exemplos do Azure](https://github.com/Azure-Samples/) no Github.</span><span class="sxs-lookup"><span data-stu-id="3185f-125">Find more search samples in the [Azure samples repository](https://github.com/Azure-Samples/) on Github.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
