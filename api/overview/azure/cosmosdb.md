---
title: Bibliotecas do Azure Cosmos DB para .NET
description: Referência para bibliotecas do Azure Cosmos DB para .NET
ms.date: 08/31/2018
ms.topic: reference
ms.service: cosmos-db
ms.openlocfilehash: 95fcd8468c3d472cfcadeaae3b56ae789c3b1e7a
ms.sourcegitcommit: 55ee51501678d1575e5159f0ac0e475b5bf9daf3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2019
ms.locfileid: "54453990"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="bb905-103">Bibliotecas do Azure Cosmos DB para .NET</span><span class="sxs-lookup"><span data-stu-id="bb905-103">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="bb905-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="bb905-104">Overview</span></span>

<span data-ttu-id="bb905-105">O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um serviço de banco de dados multimodelo globalmente distribuído.</span><span class="sxs-lookup"><span data-stu-id="bb905-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a globally distributed, multi-model database service.</span></span> <span data-ttu-id="bb905-106">Ele é projetado para se dimensionar de modo elástico e independente, com armazenamento em quaisquer regiões geográficas e um SLA abrangente.</span><span class="sxs-lookup"><span data-stu-id="bb905-106">It is designed to elastically and independently scale throughput and storage across any number of geographical regions with a comprehensive SLA.</span></span> <span data-ttu-id="bb905-107">Com o Azure Cosmos DB, você pode armazenar e acessar bancos de dados de documentos, valores-chave, de toda a coluna e gráficos usando APIs e modelos de programação.</span><span class="sxs-lookup"><span data-stu-id="bb905-107">With Azure Cosmos DB, you can store and access document, key-value, wide-column, and graph databases by using APIs and programming models.</span></span> 

<span data-ttu-id="bb905-108">[Introdução ao Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span><span class="sxs-lookup"><span data-stu-id="bb905-108">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="bb905-109">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="bb905-109">Client library</span></span>

<span data-ttu-id="bb905-110">Use a biblioteca de clientes .NET do Azure Cosmos DB para acessar e armazenar dados em um armazenamento de dados do Azure Cosmos DB existente.</span><span class="sxs-lookup"><span data-stu-id="bb905-110">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span> <span data-ttu-id="bb905-111">Para automatizar a criação de uma nova conta do Azure Cosmos DB, use o Portal do Azure, a CLI ou o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bb905-111">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="bb905-112">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="bb905-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

<span data-ttu-id="bb905-113">Para instalar a versão 2.x:</span><span class="sxs-lookup"><span data-stu-id="bb905-113">To install version 2.x:</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="bb905-114">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb905-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="bb905-115">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb905-115">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

<span data-ttu-id="bb905-116">Para instalar a pré-visualização da versão 3.0, que tem como alvo o padrão .NET:</span><span class="sxs-lookup"><span data-stu-id="bb905-116">To install the preview of version 3.0, which targets .NET standard:</span></span> 

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="bb905-117">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb905-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Cosmos -prerelease
```

#### <a name="net-core-cli"></a><span data-ttu-id="bb905-118">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb905-118">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Cosmos
```


### <a name="code-example"></a><span data-ttu-id="bb905-119">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="bb905-119">Code Example</span></span>

<span data-ttu-id="bb905-120">Este exemplo se conecta a um banco de dados da API do SQL do Azure Cosmos DB existente, lê um documento de uma coleção e desserializa-o como um objeto `TodoItem`.</span><span class="sxs-lookup"><span data-stu-id="bb905-120">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `TodoItem` object.</span></span> <span data-ttu-id="bb905-121">Este exemplo usa a versão 2.x do SDK do .NET.</span><span class="sxs-lookup"><span data-stu-id="bb905-121">This example uses version 2.x of the .NET SDK.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
var todoItem = client.ReadDocumentAsync<TodoItem>(documentUri);
```

<span data-ttu-id="bb905-122">Este exemplo conecta-se ao banco de dados API de SQL do Azure Cosmos DB existente, cria um novo banco de dados e um contêiner, lê um item do contêiner e desserializa-o para um objeto `TodoItem`.</span><span class="sxs-lookup"><span data-stu-id="bb905-122">This example connects to an existing Azure Cosmos DB SQL API database, creates a new database and container, reads an item from the container, and deserializes it to a `TodoItem` object.</span></span> <span data-ttu-id="bb905-123">Este exemplo usa a versão 3.x do SDK do .NET.</span><span class="sxs-lookup"><span data-stu-id="bb905-123">This example uses version 3.x of the .NET SDK.</span></span>   

```csharp
using (CosmosClient cosmosClient = new CosmosClient("endpoint", "primaryKey"))
{
    // Read item from container
    CosmosItemResponse<TodoItem> todoItemResponse = await cosmosClient.Databases["DatabaseId"].Containers["ContainerId"].Items.ReadItemAsync<TodoItem>("partitionKeyValue", "ItemId");
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="bb905-124">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="bb905-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="bb905-125">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bb905-125">Samples</span></span>

* [<span data-ttu-id="bb905-126">Desenvolver um aplicativo .NET usando a API SQL do Azure CosmosDB (versão 2.x)</span><span class="sxs-lookup"><span data-stu-id="bb905-126">Developing a .NET app using Azure Cosmos DB's SQL API (Version 2.x)</span></span>](https://github.com/Azure-Samples/documentdb-dotnet-todo-app/)
* [<span data-ttu-id="bb905-127">Desenvolver um aplicativo .NET usando a API SQL do Azure CosmosDB (pré-visualização da versão 3.x)</span><span class="sxs-lookup"><span data-stu-id="bb905-127">Developing a .NET app using Azure Cosmos DB's SQL API (Version 3.x Preview)</span></span>](https://github.com/Azure-Samples/cosmos-dotnet-todo-app/)
* [<span data-ttu-id="bb905-128">Desenvolver um aplicativo .NET Core usando a API SQL do Azure CosmosDB (pré-visualização da versão 3.x)</span><span class="sxs-lookup"><span data-stu-id="bb905-128">Developing a .NET Core app using Azure Cosmos DB's SQL API (Version 3.x Preview)</span></span>](https://github.com/Azure-Samples/cosmos-dotnet-core-getting-started)

<span data-ttu-id="bb905-129">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="bb905-129">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
