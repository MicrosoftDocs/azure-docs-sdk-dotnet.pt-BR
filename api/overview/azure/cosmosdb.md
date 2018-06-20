---
title: Bibliotecas do Azure Cosmos DB para .NET
description: Referência para bibliotecas do Azure Cosmos DB para .NET
keywords: Azure, .NET, SDK, API, Cosmos DB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 11/17/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: fa9bc7497ac189f18ee0ba14d72d4cdb23a05f0b
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2018
ms.locfileid: "31005803"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="20663-104">Bibliotecas do Azure Cosmos DB para .NET</span><span class="sxs-lookup"><span data-stu-id="20663-104">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="20663-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="20663-105">Overview</span></span>

<span data-ttu-id="20663-106">O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um armazenamento de dados distribuído e escalonável que dá suporte a vários tipos de bancos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="20663-106">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

<span data-ttu-id="20663-107">[Introdução ao Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span><span class="sxs-lookup"><span data-stu-id="20663-107">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="20663-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="20663-108">Client library</span></span>

<span data-ttu-id="20663-109">Use a biblioteca de clientes .NET do Azure Cosmos DB para acessar e armazenar dados em um armazenamento de dados do Azure Cosmos DB existente.</span><span class="sxs-lookup"><span data-stu-id="20663-109">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span>  <span data-ttu-id="20663-110">Para automatizar a criação de uma nova conta do Azure Cosmos DB, use o Portal do Azure, a CLI ou o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20663-110">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="20663-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="20663-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="20663-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20663-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="20663-113">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="20663-113">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="20663-114">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="20663-114">Code Example</span></span>

<span data-ttu-id="20663-115">Este exemplo se conecta a um banco de dados da API do SQL do Azure Cosmos DB existente, lê um documento de uma coleção e desserializa-o como um objeto `Item`.</span><span class="sxs-lookup"><span data-stu-id="20663-115">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="20663-116">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="20663-116">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="20663-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="20663-117">Samples</span></span>

* [<span data-ttu-id="20663-118">Desenvolvendo um aplicativo .NET usando a API MongoDB do Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="20663-118">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="20663-119">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="20663-119">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
