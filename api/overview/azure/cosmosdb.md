---
title: Bibliotecas do Azure CosmosDB para .NET
description: "Referência para bibliotecas do Azure CosmosDB para .NET"
keywords: Azure, .NET, SDK, API, CosmosDB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 890c00caeca06bf863425c7159d7833c4db8df38
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a>Bibliotecas do Azure CosmosDB para .NET

## <a name="overview"></a>Visão geral

O [Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um armazenamento de dados distribuído e escalonável que dá suporte a vários tipos de bancos de dados diferentes.

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de cliente .NET do CosmosDB para acessar e armazenar dados em um armazenamento de dados do CosmosDB.

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

Este exemplo se conecta a um banco de dados da API DocumentDB do CosmosDB existente, lê um documento de uma coleção e desserializa-o como um objeto `Item`.

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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>Exemplos

* [Desenvolvendo um aplicativo .NET usando a API MongoDB do Azure CosmosDB](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

Veja a [lista completa](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) de exemplos do Azure Cosmos DB.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
