---
title: Bibliotecas do Azure Cosmos DB para .NET
description: Referência para bibliotecas do Azure Cosmos DB para .NET
ms.date: 08/31/2018
ms.topic: reference
ms.service: cosmos-db
ms.openlocfilehash: 21a2f2168259528a0d27103783e34aa532d7e17a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190781"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="5affb-103">Bibliotecas do Azure Cosmos DB para .NET</span><span class="sxs-lookup"><span data-stu-id="5affb-103">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="5affb-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5affb-104">Overview</span></span>

<span data-ttu-id="5affb-105">O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um serviço de banco de dados multimodelo globalmente distribuído.</span><span class="sxs-lookup"><span data-stu-id="5affb-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a globally distributed, multi-model database service.</span></span> <span data-ttu-id="5affb-106">Ele é projetado para se dimensionar de modo elástico e independente, com armazenamento em quaisquer regiões geográficas e um SLA abrangente.</span><span class="sxs-lookup"><span data-stu-id="5affb-106">It is designed to elastically and independently scale throughput and storage across any number of geographical regions with a comprehensive SLA.</span></span> <span data-ttu-id="5affb-107">Com o Azure Cosmos DB, você pode armazenar e acessar bancos de dados de documentos, valores-chave, de toda a coluna e gráficos usando APIs e modelos de programação.</span><span class="sxs-lookup"><span data-stu-id="5affb-107">With Azure Cosmos DB, you can store and access document, key-value, wide-column, and graph databases by using APIs and programming models.</span></span> 

<span data-ttu-id="5affb-108">[Introdução ao Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5affb-108">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="5affb-109">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="5affb-109">Client library</span></span>

<span data-ttu-id="5affb-110">Use a biblioteca de clientes .NET do Azure Cosmos DB para acessar e armazenar dados em um armazenamento de dados do Azure Cosmos DB existente.</span><span class="sxs-lookup"><span data-stu-id="5affb-110">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span> <span data-ttu-id="5affb-111">Para automatizar a criação de uma nova conta do Azure Cosmos DB, use o Portal do Azure, a CLI ou o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5affb-111">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="5affb-112">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5affb-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5affb-113">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5affb-113">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="5affb-114">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5affb-114">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="5affb-115">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5affb-115">Code Example</span></span>

<span data-ttu-id="5affb-116">Este exemplo se conecta a um banco de dados da API do SQL do Azure Cosmos DB existente, lê um documento de uma coleção e desserializa-o como um objeto `Item`.</span><span class="sxs-lookup"><span data-stu-id="5affb-116">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5affb-117">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="5affb-117">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="5affb-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5affb-118">Samples</span></span>

* [<span data-ttu-id="5affb-119">Desenvolvendo um aplicativo .NET usando a API MongoDB do Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="5affb-119">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="5affb-120">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="5affb-120">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
