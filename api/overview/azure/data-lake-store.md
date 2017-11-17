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
# <a name="azure-data-lake-store-libraries-for-net"></a><span data-ttu-id="4fd9c-104">Bibliotecas do Azure Data Lake Store para .NET</span><span class="sxs-lookup"><span data-stu-id="4fd9c-104">Azure Data Lake Store libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="4fd9c-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="4fd9c-105">Overview</span></span>

<span data-ttu-id="4fd9c-106">O Repositório Azure Data Lake é um repositório em hiper-escala corporativo para cargas de trabalho de análise de big data.</span><span class="sxs-lookup"><span data-stu-id="4fd9c-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="4fd9c-107">O Azure Data Lake permite que você capture dados de qualquer tamanho, tipo e velocidade de ingestão em um único lugar para análises operacionais e exploratórias.</span><span class="sxs-lookup"><span data-stu-id="4fd9c-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

<span data-ttu-id="4fd9c-108">Para saber mais, confira [Visão geral do Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span><span class="sxs-lookup"><span data-stu-id="4fd9c-108">To learn more, see [Overview of Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="4fd9c-109">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4fd9c-109">Management library</span></span>

<span data-ttu-id="4fd9c-110">Use a biblioteca de gerenciamento para se conectar e gerenciar seus grandes armazenamentos de dados.</span><span class="sxs-lookup"><span data-stu-id="4fd9c-110">Use the management library to connect to and manage your big data repositories.</span></span>

<span data-ttu-id="4fd9c-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4fd9c-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4fd9c-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4fd9c-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

### <a name="code-example"></a><span data-ttu-id="4fd9c-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4fd9c-113">Code Example</span></span>

<span data-ttu-id="4fd9c-114">Este exemplo faz a autenticação em uma conta de análise, armazena e cria os clientes necessários para o gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="4fd9c-114">This example authenticates to an analytics account and store and creates the clients necessary for management.</span></span>

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
> [<span data-ttu-id="4fd9c-115">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4fd9c-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakestore/management)

## <a name="samples"></a><span data-ttu-id="4fd9c-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4fd9c-116">Samples</span></span>

* [<span data-ttu-id="4fd9c-117">Exemplo de cliente .NET do Azure Data Lake</span><span class="sxs-lookup"><span data-stu-id="4fd9c-117">Azure Data Lake .NET Client Example</span></span>](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)

<span data-ttu-id="4fd9c-118">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4fd9c-118">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
