---
title: Bibliotecas do Azure Data Lake Store para .NET
description: Referência para bibliotecas do Azure Data Lake Store para .NET
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
ms.openlocfilehash: e8380c4a9ebf86f03fe87fc800dffda10e48e60a
ms.sourcegitcommit: 3e904e6e4f04f1c92d729459434c85faff32e386
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
ms.locfileid: "26588469"
---
# <a name="azure-data-lake-store-libraries-for-net"></a><span data-ttu-id="3b118-104">Bibliotecas do Azure Data Lake Store para .NET</span><span class="sxs-lookup"><span data-stu-id="3b118-104">Azure Data Lake Store libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="3b118-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3b118-105">Overview</span></span>

<span data-ttu-id="3b118-106">O Repositório Azure Data Lake é um repositório em hiper-escala corporativo para cargas de trabalho de análise de big data.</span><span class="sxs-lookup"><span data-stu-id="3b118-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="3b118-107">O Azure Data Lake permite que você capture dados de qualquer tamanho, tipo e velocidade de ingestão em um único lugar para análises operacionais e exploratórias.</span><span class="sxs-lookup"><span data-stu-id="3b118-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

<span data-ttu-id="3b118-108">Para saber mais, confira [Visão geral do Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span><span class="sxs-lookup"><span data-stu-id="3b118-108">To learn more, see [Overview of Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span></span>

## <a name="client-library"></a><span data-ttu-id="3b118-109">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="3b118-109">Client library</span></span>

<span data-ttu-id="3b118-110">Use a biblioteca de clientes para executar operações de sistema de arquivos no Data Lake Store, como a criação de pastas em uma conta do Data Lake Store, o carregamento e o download de arquivos.</span><span class="sxs-lookup"><span data-stu-id="3b118-110">Use the client library to perform filesystem operations on Data Lake Store, such as creating folders in a Data Lake Store account, uploading files, and downloading files.</span></span>  <span data-ttu-id="3b118-111">Para obter um tutorial completo sobre como usar o Data Lake Store com o .NET, confira [Operações de sistema de arquivos no Azure Data Lake Store usando o SDK do .NET](/azure/data-lake-store/data-lake-store-data-operations-net-sdk).</span><span class="sxs-lookup"><span data-stu-id="3b118-111">For a full tutorial on using Data Lake Store with .NET, see [Filesystem operations on Azure Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-data-operations-net-sdk).</span></span>

<span data-ttu-id="3b118-112">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="3b118-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="3b118-113">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b118-113">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.DataLake.Store
```
### <a name="authentication"></a><span data-ttu-id="3b118-114">Autenticação</span><span class="sxs-lookup"><span data-stu-id="3b118-114">Authentication</span></span>

* <span data-ttu-id="3b118-115">Para saber sobre autenticação do usuário final em seu aplicativo, consulte [Autenticação do usuário final com Data Lake Store usando SDK do .NET](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk).</span><span class="sxs-lookup"><span data-stu-id="3b118-115">For end-user authentication for your application, see [End-user authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk).</span></span>
* <span data-ttu-id="3b118-116">Para saber sobre autenticação do usuário final em seu aplicativo, consulte [Autenticação de serviço para serviço com Data Lake Store usando o SDK do .NET](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk).</span><span class="sxs-lookup"><span data-stu-id="3b118-116">For service-to-service authentication for your application, see [Service-to-service authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk).</span></span>

### <a name="code-example"></a><span data-ttu-id="3b118-117">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3b118-117">Code Example</span></span>

<span data-ttu-id="3b118-118">O trecho de código a seguir cria o objeto de cliente de sistema de arquivos do Data Lake Store, que é usado para emitir solicitações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3b118-118">The following snippet creates the Data Lake Store filesystem client object, which is used to issue requests to the service.</span></span>

```csharp
// Create client objects
AdlsClient client = AdlsClient.CreateClient(_adlsAccountName, adlCreds);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b118-119">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="3b118-119">Explore the client APIs</span></span>](/dotnet/api/overview/azure/datalakestore/client)


## <a name="management-library"></a><span data-ttu-id="3b118-120">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="3b118-120">Management library</span></span>

<span data-ttu-id="3b118-121">Use a biblioteca de gerenciamento para se conectar e gerenciar seus grandes armazenamentos de dados.</span><span class="sxs-lookup"><span data-stu-id="3b118-121">Use the management library to connect to and manage your big data repositories.</span></span>

<span data-ttu-id="3b118-122">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="3b118-122">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="3b118-123">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b118-123">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b118-124">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="3b118-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/datalakestore/management)


## <a name="samples"></a><span data-ttu-id="3b118-125">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3b118-125">Samples</span></span>

* [<span data-ttu-id="3b118-126">Exemplo de cliente .NET do Azure Data Lake</span><span class="sxs-lookup"><span data-stu-id="3b118-126">Azure Data Lake .NET Client Example</span></span>](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)

<span data-ttu-id="3b118-127">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3b118-127">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
