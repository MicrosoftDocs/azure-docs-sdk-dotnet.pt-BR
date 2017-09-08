---
title: APIs de armazenamento do .NET do Azure
description: "Referência para bibliotecas do Armazenamento do Azure para .NET"
keywords: Azure, .NET, SDK, API, armazenamento, blob
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 4e494952b48bfbf3b10f9af9936648634353db78
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-storage-apis-for-net"></a><span data-ttu-id="77abb-104">APIs do Armazenamento do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="77abb-104">Azure Storage APIs for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="77abb-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="77abb-105">Overview</span></span>

<span data-ttu-id="77abb-106">Leia e grave arquivos, dados de blob (objeto), pares chave-valor e mensagens de aplicativos .NET com o [Armazenamento do Azure](https://review.docs.microsoft.com/en-us/azure/storage/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="77abb-106">Read and write files, blob (object) data, key-value pairs, and messages from your .NET applications with [Azure Storage](https://review.docs.microsoft.com/en-us/azure/storage/storage-introduction).</span></span>

<span data-ttu-id="77abb-107">Para trabalhar com o Armazenamento do Azure, confira a [Introdução ao Armazenamento de Blobs do Azure usando o .NET](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="77abb-107">To get started with Azure Storage, see [Get started with Azure Blob storage using .NET](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="client-library"></a><span data-ttu-id="77abb-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="77abb-108">Client library</span></span>

<span data-ttu-id="77abb-109">Use [cadeias de conexão](/azure/storage/storage-create-storage-account#manage-your-storage-account) para se conectar a uma conta do Armazenamento do Azure e use as classes e métodos das bibliotecas de cliente para trabalhar com armazenamento de blob, tabela, arquivo ou fila.</span><span class="sxs-lookup"><span data-stu-id="77abb-109">Use [connection strings](/azure/storage/storage-create-storage-account#manage-your-storage-account) to connect to an Azure Storage account, then use the client libraries' classes and methods to work with blob, table, file, or queue storage.</span></span>

<span data-ttu-id="77abb-110">Instale o [pacote NuGet](https://www.nuget.org/packages/WindowsAzure.Storage) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="77abb-110">Install the [NuGet package](https://www.nuget.org/packages/WindowsAzure.Storage) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="77abb-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77abb-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package WindowsAzure.Storage
```

### <a name="net-core-cli"></a><span data-ttu-id="77abb-112">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="77abb-112">.NET Core CLI</span></span>

```bash
dotnet add package WindowsAzure.Storage
```

### <a name="code-example"></a><span data-ttu-id="77abb-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="77abb-113">Code Example</span></span>

<span data-ttu-id="77abb-114">Este exemplo cria um novo blob em um novo contêiner em uma conta de armazenamento existente.</span><span class="sxs-lookup"><span data-stu-id="77abb-114">This example creates a new blob to a new container in an existing storage account.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Blob;
*/

string storageConnectionString = "DefaultEndpointsProtocol=https;"
    + "AccountName=[Storage Account Name]"
    + ";AccountKey=[Storage Account Key]"
    + ";EndpointSuffix=core.windows.net";

CloudStorageAccount account = CloudStorageAccount.Parse(storageConnectionString);
CloudBlobClient serviceClient = account.CreateCloudBlobClient();

// Create container. Name must be lower case.
Console.WriteLine("Creating container...");
var container = serviceClient.GetContainerReference("mycontainer");
container.CreateIfNotExistsAsync().Wait();

// write a blob to the container
CloudBlockBlob blob = container.GetBlockBlobReference("helloworld.txt");
blob.UploadTextAsync("Hello, World!").Wait();
```

> [!div class="nextstepactions"]
> [<span data-ttu-id="77abb-115">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="77abb-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/storage/client)

## <a name="management-apis"></a><span data-ttu-id="77abb-116">APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="77abb-116">Management APIs</span></span>

<span data-ttu-id="77abb-117">Crie e gerencie contas do Armazenamento do Azure e chaves de conexão com a API de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="77abb-117">Create and manage Azure Storage accounts and connection keys with the management API.</span></span>

<span data-ttu-id="77abb-118">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="77abb-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="77abb-119">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77abb-119">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Storage.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="77abb-120">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="77abb-120">.NET Core CLI</span></span>

````bash
dotnet add package Microsoft.Azure.Management.Storage.Fluent
````

### <a name="code-example"></a><span data-ttu-id="77abb-121">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="77abb-121">Code Example</span></span>

<span data-ttu-id="77abb-122">Este exemplo cria uma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="77abb-122">This example creates a storage account.</span></span>

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Management.Storage.Fluent
*/

IStorageAccount storage = azure.StorageAccounts.Define(storageAccountName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .Create();
```

> [!div class="nextstepactions"]
> [<span data-ttu-id="77abb-123">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="77abb-123">Explore the management APIs</span></span>](/dotnet/api/overview/azure/storage/management)

## <a name="samples"></a><span data-ttu-id="77abb-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="77abb-124">Samples</span></span>

* [<span data-ttu-id="77abb-125">Introdução ao Armazenamento de Blobs do Azure no .NET</span><span class="sxs-lookup"><span data-stu-id="77abb-125">Get started with Azure Blob Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/) 
* [<span data-ttu-id="77abb-126">Introdução ao Armazenamento de Filas do Azure no NET</span><span class="sxs-lookup"><span data-stu-id="77abb-126">Get started with Azure Queue Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/)

<span data-ttu-id="77abb-127">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) de exemplos do Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="77abb-127">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) of Azure Storage samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package