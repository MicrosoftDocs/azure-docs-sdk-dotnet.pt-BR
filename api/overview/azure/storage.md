---
title: APIs de armazenamento do .NET do Azure
description: Referência para bibliotecas do Armazenamento do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: storage
ms.openlocfilehash: 2f278f0e3cb10d11190d529f427fa64040ee8b1d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189969"
---
# <a name="azure-storage-apis-for-net"></a>APIs do Armazenamento do Azure para .NET

## <a name="overview"></a>Visão geral

Leia e grave arquivos, dados de blob (objeto), pares chave-valor e mensagens de aplicativos .NET com o [Armazenamento do Azure](https://docs.microsoft.com/azure/storage/storage-introduction).

Para trabalhar com o Armazenamento do Azure, confira a [Introdução ao Armazenamento de Blobs do Azure usando o .NET](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="client-library"></a>Biblioteca do cliente

Use [cadeias de conexão](/azure/storage/storage-create-storage-account#manage-your-storage-account) para se conectar a uma conta do Armazenamento do Azure e use as classes e métodos das bibliotecas de cliente para trabalhar com armazenamento de blob, tabela, arquivo ou fila.

Instale o [pacote NuGet](https://www.nuget.org/packages/WindowsAzure.Storage) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package WindowsAzure.Storage
```

### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package WindowsAzure.Storage
```

### <a name="code-example"></a>Exemplo de código

Este exemplo cria um novo blob em um novo contêiner em uma conta de armazenamento existente.

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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/storage/client)

## <a name="management-apis"></a>APIs de gerenciamento

Crie e gerencie contas do Armazenamento do Azure e chaves de conexão com a API de gerenciamento.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Storage.Fluent
```

#### <a name="net-core-cli"></a>CLI do .NET Core

````bash
dotnet add package Microsoft.Azure.Management.Storage.Fluent
````

### <a name="code-example"></a>Exemplo de código

Este exemplo cria uma conta de armazenamento.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/storage/management)

## <a name="samples"></a>Exemplos

* [Introdução ao Armazenamento de Blobs do Azure no .NET](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/) 
* [Introdução ao Armazenamento de Filas do Azure no NET](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) de exemplos do Armazenamento do Azure.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package