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
# <a name="azure-cosmos-db-libraries-for-net"></a>Bibliotecas do Azure Cosmos DB para .NET

## <a name="overview"></a>Visão geral

O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um serviço de banco de dados multimodelo globalmente distribuído. Ele é projetado para se dimensionar de modo elástico e independente, com armazenamento em quaisquer regiões geográficas e um SLA abrangente. Com o Azure Cosmos DB, você pode armazenar e acessar bancos de dados de documentos, valores-chave, de toda a coluna e gráficos usando APIs e modelos de programação. 

[Introdução ao Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de clientes .NET do Azure Cosmos DB para acessar e armazenar dados em um armazenamento de dados do Azure Cosmos DB existente. Para automatizar a criação de uma nova conta do Azure Cosmos DB, use o Portal do Azure, a CLI ou o PowerShell.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a>Exemplo de código

Este exemplo se conecta a um banco de dados da API do SQL do Azure Cosmos DB existente, lê um documento de uma coleção e desserializa-o como um objeto `Item`.   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>Exemplos

* [Desenvolvendo um aplicativo .NET usando a API MongoDB do Azure CosmosDB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
