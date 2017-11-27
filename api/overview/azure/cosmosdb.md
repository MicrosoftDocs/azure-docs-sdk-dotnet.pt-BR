---
title: Bibliotecas do Azure CosmosDB para .NET
description: "Referência para bibliotecas do Azure CosmosDB para .NET"
keywords: Azure, .NET, SDK, API, CosmosDB
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
ms.openlocfilehash: 9f29e53e7f202e48ade12e28f08487bbacd2833c
ms.sourcegitcommit: 9cc5f8da9e9a15ba07fd67fe8b9a2d4ee6b57c73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a><span data-ttu-id="f0591-104">Bibliotecas do Azure CosmosDB para .NET</span><span class="sxs-lookup"><span data-stu-id="f0591-104">Azure CosmosDB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f0591-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f0591-105">Overview</span></span>

<span data-ttu-id="f0591-106">O [Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um armazenamento de dados distribuído e escalonável que dá suporte a vários tipos de bancos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="f0591-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

<span data-ttu-id="f0591-107">[Introdução ao CosmosDB](https://docs.microsoft.com/azure/cosmos-db/create-documentdb-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f0591-107">[Get started with CosmosDB](https://docs.microsoft.com/azure/cosmos-db/create-documentdb-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="f0591-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="f0591-108">Client library</span></span>

<span data-ttu-id="f0591-109">Use a biblioteca de cliente .NET do CosmosDB para acessar e armazenar dados em um armazenamento de dados do CosmosDB existente.</span><span class="sxs-lookup"><span data-stu-id="f0591-109">Use the CosmosDB .NET client library to access and store data in an existing CosmosDB data store.</span></span>  <span data-ttu-id="f0591-110">Para automatizar a criação de uma nova conta do CosmosDB, use o portal do Azure, a CLI ou o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0591-110">To automate creation of a new CosmosDB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="f0591-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f0591-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f0591-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f0591-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="f0591-113">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f0591-113">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="f0591-114">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f0591-114">Code Example</span></span>

<span data-ttu-id="f0591-115">Este exemplo se conecta a um banco de dados da API DocumentDB do CosmosDB existente, lê um documento de uma coleção e desserializa-o como um objeto `Item`.</span><span class="sxs-lookup"><span data-stu-id="f0591-115">This example connects to an existing CosmosDB DocumentDB API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f0591-116">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="f0591-116">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="f0591-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f0591-117">Samples</span></span>

* [<span data-ttu-id="f0591-118">Desenvolvendo um aplicativo .NET usando a API MongoDB do Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="f0591-118">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="f0591-119">Veja a [lista completa](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="f0591-119">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
