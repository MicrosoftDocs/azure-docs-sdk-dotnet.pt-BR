---
title: Bibliotecas do Azure Data Lake Store para .NET
description: "Referência para bibliotecas do Azure Data Lake Store para .NET"
keywords: Azure, .NET, SDK, API, Data Lake Store
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-lake-store
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 2b1c51575872b12a94eb44c7c082996bb879bcc9
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-data-lake-store-libraries-for-net"></a>Bibliotecas do Azure Data Lake Store para .NET

## <a name="overview"></a>Visão geral

O Repositório Azure Data Lake é um repositório em hiper-escala corporativo para cargas de trabalho de análise de big data. O Azure Data Lake permite que você capture dados de qualquer tamanho, tipo e velocidade de ingestão em um único lugar para análises operacionais e exploratórias.

Para saber mais, confira [Visão geral do Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para se conectar e gerenciar seus grandes armazenamentos de dados.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

### <a name="code-example"></a>Exemplo de código

Este exemplo faz a autenticação em uma conta de análise, armazena e cria os clientes necessários para o gerenciamento.

```csharp
/*
using AdlClient
using AdlClient.Models 
*/

// Setup authentication 
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
StoreAccountRef adls_account = new StoreAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
StoreClient adls = new StoreClient(auth, adls_account);
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/datalakestore/management)

## <a name="samples"></a>Exemplos

* [Exemplo de cliente .NET do Azure Data Lake](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
