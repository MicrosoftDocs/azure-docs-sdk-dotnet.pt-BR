---
title: Bibliotecas do Azure Service Fabric para .NET
description: Referência para bibliotecas do Azure Service Fabric para .NET
keywords: Azure, .NET, SDK, API, Service Fabric
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: service-fabric
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e1b4d08c93ad44973359f46501aba198047b10e8
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065936"
---
# <a name="azure-service-fabric-libraries-for-net"></a><span data-ttu-id="5578c-104">Bibliotecas do Azure Service Fabric para .NET</span><span class="sxs-lookup"><span data-stu-id="5578c-104">Azure Service Fabric libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="5578c-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5578c-105">Overview</span></span>

<span data-ttu-id="5578c-106">O Azure Service Fabric é uma plataforma de sistemas distribuídos que facilita o empacotamento, implantação e gerenciamento de microsserviços e contêineres escalonáveis e confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5578c-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>  <span data-ttu-id="5578c-107">Para obter mais informações, consulte a [Documentação do Azure Service Fabric](/azure/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="5578c-107">For more information, see the [Azure Service Fabric Documentation](/azure/service-fabric/).</span></span>

## <a name="client-library"></a><span data-ttu-id="5578c-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="5578c-108">Client library</span></span>

<span data-ttu-id="5578c-109">Use a biblioteca de cliente do Service Fabric para interagir com um cluster Service Fabric existente.</span><span class="sxs-lookup"><span data-stu-id="5578c-109">Use the Service Fabric client library to interact with an existing Service Fabric cluster.</span></span>  <span data-ttu-id="5578c-110">A biblioteca contém três categorias de APIs:</span><span class="sxs-lookup"><span data-stu-id="5578c-110">The library contains three categories of APIs:</span></span>

* <span data-ttu-id="5578c-111">As APIs do **cliente** são usadas para gerenciar, dimensionar e reciclar o cluster, bem como implantar pacotes de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5578c-111">**Client** APIs are used to manage, scale, and recycle the cluster, as well as deploy application packages.</span></span>
* <span data-ttu-id="5578c-112">As APIs de **execução** são usadas para o aplicativo em execução interagir com seu cluster de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="5578c-112">**Runtime** APIs are used for the running application to interact with its hosting cluster.</span></span>
* <span data-ttu-id="5578c-113">As APIs **comuns** contêm os tipos usados nas APIs do **cliente** e de  **execução**.</span><span class="sxs-lookup"><span data-stu-id="5578c-113">**Common** APIs contain types used in both **client** and **runtime** APIs.</span></span>

<span data-ttu-id="5578c-114">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.ServiceFabric) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5578c-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5578c-115">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5578c-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-examples"></a><span data-ttu-id="5578c-116">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="5578c-116">Code Examples</span></span>

<span data-ttu-id="5578c-117">O exemplo a seguir usa as APIs do **cliente** do Service Fabric para copiar um pacote de aplicativos para o repositório de imagens, provisionar o tipo de aplicativo e criar uma instância dele.</span><span class="sxs-lookup"><span data-stu-id="5578c-117">The following example uses the Service Fabric **client** APIs to copy an application package to the image store, provisions the application type, and create an application instance.</span></span>

```csharp
/* Include these dependencies
using System.Fabric;
using System.Fabric.Description;
*/

// Connect to the cluster.
FabricClient fabricClient = new FabricClient(clusterConnection);

// Copy the application package to a location in the image store
fabricClient.ApplicationManager.CopyApplicationPackage(imageStoreConnectionString, packagePath, packagePathInImageStore);

// Provision the application.
fabricClient.ApplicationManager.ProvisionApplicationAsync(packagePathInImageStore).Wait();

//  Create the application instance.
ApplicationDescription appDesc = new ApplicationDescription(new Uri(appName), appType, appVersion);
fabricClient.ApplicationManager.CreateApplicationAsync(appDesc).Wait();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5578c-118">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="5578c-118">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicefabric/client)

<span data-ttu-id="5578c-119">Este exemplo usa as APIs de **execução** e **comuns** do Service Fabric de dentro de um aplicativo hospedado para atualizar uma [Coleção Confiável](/azure/service-fabric/service-fabric-reliable-services-reliable-collections) durante a execução.</span><span class="sxs-lookup"><span data-stu-id="5578c-119">This example uses the Service Fabric **runtime** and **common** APIs from within a hosted application to update a [Reliable Collection](/azure/service-fabric/service-fabric-reliable-services-reliable-collections) at runtime.</span></span>

```csharp
using System.Fabric;
using Microsoft.ServiceFabric.Data.Collections;
using Microsoft.ServiceFabric.Services.Communication.Runtime;
using Microsoft.ServiceFabric.Services.Runtime;

/// <summary>
/// This is the main entry point for your service replica.
/// This method executes when this replica of your service becomes primary and has write status.
/// </summary>
/// <param name="cancellationToken">Canceled when Service Fabric needs to shut down this service replica.</param>
protected override async Task RunAsync(CancellationToken cancellationToken)
{
    var myDictionary = await this.StateManager.GetOrAddAsync<IReliableDictionary<string, long>>("myDictionary");
    while (true)
    {
        cancellationToken.ThrowIfCancellationRequested();
        using (var tx = this.StateManager.CreateTransaction())
        {
            var result = await myDictionary.TryGetValueAsync(tx, "Counter");
            await myDictionary.AddOrUpdateAsync(tx, "Counter", 0, (key, value) => ++value);

            // If an exception is thrown before calling CommitAsync, the transaction aborts, all changes are
            // discarded, and nothing is saved to the secondary replicas.
            await tx.CommitAsync();
        }
        await Task.Delay(TimeSpan.FromSeconds(1), cancellationToken);
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5578c-120">Explorar as APIs de execução</span><span class="sxs-lookup"><span data-stu-id="5578c-120">Explore the runtime APIs</span></span>](/dotnet/api/overview/azure/servicefabric/runtime)

> [!div class="nextstepaction"]
> [<span data-ttu-id="5578c-121">Explorar as APIs comuns</span><span class="sxs-lookup"><span data-stu-id="5578c-121">Explore the common APIs</span></span>](/dotnet/api/overview/azure/servicefabric/common)

## <a name="management-library"></a><span data-ttu-id="5578c-122">Biblioteca de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5578c-122">Management Library</span></span>

<span data-ttu-id="5578c-123">A biblioteca de gerenciamento é usada para criar, atualizar e excluir os clusters Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="5578c-123">The management library is used to create, update, and delete Service Fabric clusters.</span></span>

<span data-ttu-id="5578c-124">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5578c-124">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5578c-125">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5578c-125">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceFabric
```

```bash
dotnet add package Microsoft.Azure.Management.ServiceFabric
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5578c-126">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5578c-126">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicefabric/management)

## <a name="samples"></a><span data-ttu-id="5578c-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5578c-127">Samples</span></span>

* [<span data-ttu-id="5578c-128">Implantar e remover aplicativos usando o FabricClient</span><span class="sxs-lookup"><span data-stu-id="5578c-128">Deploy and remove applications using FabricClient</span></span>](/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
