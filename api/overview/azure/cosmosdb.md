---
title: Bibliotecas do Azure Cosmos DB para .NET
description: Referência para bibliotecas do Azure Cosmos DB para .NET
keywords: Azure, .NET, SDK, API, Cosmos DB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 08/31/2018
ms.topic: reference
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 4928c1dfdb7a5bb50ca4f5023cbfec71e05e9061
ms.sourcegitcommit: 299aa7bdbb9cec1b56e42e25550999e53e23de2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43839492"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="ca9c1-104">Bibliotecas do Azure Cosmos DB para .NET</span><span class="sxs-lookup"><span data-stu-id="ca9c1-104">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="ca9c1-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ca9c1-105">Overview</span></span>

<span data-ttu-id="ca9c1-106">O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um serviço de banco de dados multimodelo globalmente distribuído.</span><span class="sxs-lookup"><span data-stu-id="ca9c1-106">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a globally distributed, multi-model database service.</span></span> <span data-ttu-id="ca9c1-107">Ele é projetado para se dimensionar de modo elástico e independente, com armazenamento em quaisquer regiões geográficas e um SLA abrangente.</span><span class="sxs-lookup"><span data-stu-id="ca9c1-107">It is designed to elastically and independently scale throughput and storage across any number of geographical regions with a comprehensive SLA.</span></span> <span data-ttu-id="ca9c1-108">Com o Azure Cosmos DB, você pode armazenar e acessar bancos de dados de documentos, valores-chave, de toda a coluna e gráficos usando APIs e modelos de programação.</span><span class="sxs-lookup"><span data-stu-id="ca9c1-108">With Azure Cosmos DB, you can store and access document, key-value, wide-column, and graph databases by using APIs and programming models.</span></span> 

<span data-ttu-id="ca9c1-109">[Introdução ao Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ca9c1-109">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="ca9c1-110">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="ca9c1-110">Client library</span></span>

<span data-ttu-id="ca9c1-111">Use a biblioteca de clientes .NET do Azure Cosmos DB para acessar e armazenar dados em um armazenamento de dados do Azure Cosmos DB existente.</span><span class="sxs-lookup"><span data-stu-id="ca9c1-111">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span> <span data-ttu-id="ca9c1-112">Para automatizar a criação de uma nova conta do Azure Cosmos DB, use o Portal do Azure, a CLI ou o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca9c1-112">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="ca9c1-113">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="ca9c1-113">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="ca9c1-114">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca9c1-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="ca9c1-115">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ca9c1-115">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="ca9c1-116">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="ca9c1-116">Code Example</span></span>

<span data-ttu-id="ca9c1-117">Este exemplo se conecta a um banco de dados da API do SQL do Azure Cosmos DB existente, lê um documento de uma coleção e desserializa-o como um objeto `Item`.</span><span class="sxs-lookup"><span data-stu-id="ca9c1-117">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca9c1-118">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="ca9c1-118">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="ca9c1-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ca9c1-119">Samples</span></span>

* [<span data-ttu-id="ca9c1-120">Desenvolvendo um aplicativo .NET usando a API MongoDB do Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="ca9c1-120">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="ca9c1-121">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="ca9c1-121">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
