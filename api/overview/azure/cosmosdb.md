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
# <a name="azure-cosmos-db-libraries-for-net"></a>Bibliotecas do Azure Cosmos DB para .NET

## <a name="overview"></a>Visão geral

O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um serviço de banco de dados multimodelo globalmente distribuído. Ele é projetado para se dimensionar de modo elástico e independente, com armazenamento em quaisquer regiões geográficas e um SLA abrangente. Com o Azure Cosmos DB, você pode armazenar e acessar bancos de dados de documentos, valores-chave, de toda a coluna e gráficos usando APIs e modelos de programação. 

[Introdução ao Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de clientes .NET do Azure Cosmos DB para acessar e armazenar dados em um armazenamento de dados do Azure Cosmos DB existente. Para automatizar a criação de uma nova conta do Azure Cosmos DB, use o Portal do Azure, a CLI ou o PowerShell.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

Para instalar a versão 2.x:

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

Para instalar a pré-visualização da versão 3.0, que tem como alvo o padrão .NET: 

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Cosmos -prerelease
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.Cosmos
```


### <a name="code-example"></a>Exemplo de código

Este exemplo se conecta a um banco de dados da API do SQL do Azure Cosmos DB existente, lê um documento de uma coleção e desserializa-o como um objeto `TodoItem`. Este exemplo usa a versão 2.x do SDK do .NET.   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
var todoItem = client.ReadDocumentAsync<TodoItem>(documentUri);
```

Este exemplo conecta-se ao banco de dados API de SQL do Azure Cosmos DB existente, cria um novo banco de dados e um contêiner, lê um item do contêiner e desserializa-o para um objeto `TodoItem`. Este exemplo usa a versão 3.x do SDK do .NET.   

```csharp
using (CosmosClient cosmosClient = new CosmosClient("endpoint", "primaryKey"))
{
    // Read item from container
    CosmosItemResponse<TodoItem> todoItemResponse = await cosmosClient.Databases["DatabaseId"].Containers["ContainerId"].Items.ReadItemAsync<TodoItem>("partitionKeyValue", "ItemId");
}
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>Exemplos

* [Desenvolver um aplicativo .NET usando a API SQL do Azure CosmosDB (versão 2.x)](https://github.com/Azure-Samples/documentdb-dotnet-todo-app/)
* [Desenvolver um aplicativo .NET usando a API SQL do Azure CosmosDB (pré-visualização da versão 3.x)](https://github.com/Azure-Samples/cosmos-dotnet-todo-app/)
* [Desenvolver um aplicativo .NET Core usando a API SQL do Azure CosmosDB (pré-visualização da versão 3.x)](https://github.com/Azure-Samples/cosmos-dotnet-core-getting-started)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
