---
title: Bibliotecas do Azure Service Fabric para .NET
description: Referência para bibliotecas do Azure Service Fabric para .NET
keywords: Azure, .NET, SDK, API, Service Fabric
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: service-fabric
ms.custom: devcenter, svc-overview
ms.openlocfilehash: f4b54933d31a4e1fc4c390baa57469cc1c02783a
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566087"
---
# <a name="azure-service-fabric-libraries-for-net"></a>Bibliotecas do Azure Service Fabric para .NET

## <a name="overview"></a>Visão geral

O Azure Service Fabric é uma plataforma de sistemas distribuídos que facilita o empacotamento, implantação e gerenciamento de microsserviços e contêineres escalonáveis e confiáveis.  Para obter mais informações, consulte a [Documentação do Azure Service Fabric](/azure/service-fabric/).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de cliente do Service Fabric para interagir com um cluster Service Fabric existente.  A biblioteca contém três categorias de APIs:

* As APIs do **cliente** são usadas para gerenciar, dimensionar e reciclar o cluster, bem como implantar pacotes de aplicativos.
* As APIs de **execução** são usadas para o aplicativo em execução interagir com seu cluster de hospedagem.
* As APIs **comuns** contêm os tipos usados nas APIs do **cliente** e de  **execução**.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.ServiceFabric) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-examples"></a>Exemplos de código

O exemplo a seguir usa as APIs do **cliente** do Service Fabric para copiar um pacote de aplicativos para o repositório de imagens, provisionar o tipo de aplicativo e criar uma instância dele.

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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/servicefabric/client)

Este exemplo usa as APIs de **execução** e **comuns** do Service Fabric de dentro de um aplicativo hospedado para atualizar uma [Coleção Confiável](/azure/service-fabric/service-fabric-reliable-services-reliable-collections) durante a execução.

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
> [Explorar as APIs de execução](/dotnet/api/overview/azure/servicefabric/runtime)

> [!div class="nextstepaction"]
> [Explorar as APIs comuns](/dotnet/api/overview/azure/servicefabric/common)

## <a name="management-library"></a>Biblioteca de Gerenciamento

A biblioteca de gerenciamento é usada para criar, atualizar e excluir os clusters Service Fabric.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ServiceFabric
```

```bash
dotnet add package Microsoft.Azure.Management.ServiceFabric
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/servicefabric/management)

## <a name="samples"></a>Exemplos

* [Implantar e remover aplicativos usando o FabricClient](/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
