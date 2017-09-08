---
title: Bibliotecas do Azure CosmosDB para .NET
description: "Referência para bibliotecas do Azure CosmosDB para .NET"
keywords: Azure, .NET, SDK, API, CosmosDB
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: babf34e98dae439a2dc3d4c63bd638335428e935
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a><span data-ttu-id="01b5d-104">Bibliotecas do Azure CosmosDB para .NET</span><span class="sxs-lookup"><span data-stu-id="01b5d-104">Azure CosmosDB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="01b5d-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="01b5d-105">Overview</span></span>

<span data-ttu-id="01b5d-106">O [Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um armazenamento de dados distribuído e escalonável que dá suporte a vários tipos de bancos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="01b5d-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

## <a name="client-library"></a><span data-ttu-id="01b5d-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="01b5d-107">Client library</span></span>

<span data-ttu-id="01b5d-108">Use a biblioteca de cliente .NET do CosmosDB para acessar e armazenar dados em um armazenamento de dados do CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="01b5d-108">Use the CosmosDB .NET client library to access and store data in a CosmosDB data store.</span></span>

<span data-ttu-id="01b5d-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="01b5d-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="01b5d-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01b5d-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="01b5d-111">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="01b5d-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="01b5d-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="01b5d-112">Code Example</span></span>

<span data-ttu-id="01b5d-113">Este exemplo se conecta a um banco de dados da API DocumentDB do CosmosDB existente, lê um documento de uma coleção e desserializa-o como um objeto `Item`.</span><span class="sxs-lookup"><span data-stu-id="01b5d-113">This example connects to an existing CosmosDB DocumentDB API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
// "Item" is a class defined elsewhere...
Item item = client.ReadDocumentAsync<Item>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="01b5d-114">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="01b5d-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="01b5d-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="01b5d-115">Samples</span></span>

* [<span data-ttu-id="01b5d-116">Desenvolvendo um aplicativo .NET usando a API MongoDB do Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="01b5d-116">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="01b5d-117">Veja a [lista completa](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="01b5d-117">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
