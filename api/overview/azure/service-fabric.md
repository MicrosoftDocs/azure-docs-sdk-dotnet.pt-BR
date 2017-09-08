---
title: Bibliotecas do Azure Service Fabric para .NET
description: "Referência para bibliotecas do Azure Service Fabric para .NET"
keywords: Azure, .NET, SDK, API, Service Fabric
author: spboyer
ms.author: casoper
manager: douge
ms.date: 07/07/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: c708ae06fa4b5165e3f615abf636b11bfd95cd3b
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-service-fabric-libraries-for-net"></a><span data-ttu-id="4f416-104">Bibliotecas do Azure Service Fabric para .NET</span><span class="sxs-lookup"><span data-stu-id="4f416-104">Azure Service Fabric libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="4f416-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="4f416-105">Overview</span></span>

<span data-ttu-id="4f416-106">O Azure Service Fabric é uma plataforma de sistemas distribuídos que facilita o empacotamento, implantação e gerenciamento de microsserviços e contêineres escalonáveis e confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4f416-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

## <a name="client-library"></a><span data-ttu-id="4f416-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="4f416-107">Client library</span></span>

<span data-ttu-id="4f416-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.ServiceFabric) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4f416-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4f416-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4f416-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-example"></a><span data-ttu-id="4f416-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4f416-110">Code Example</span></span>

<span data-ttu-id="4f416-111">O exemplo a seguir copia um pacote de aplicativos para o repositório de imagens, provisiona o tipo de aplicativo e cria uma instância de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f416-111">The following example copies an application package to the image store, provisions the application type, and creates an application instance.</span></span>

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
> [<span data-ttu-id="4f416-112">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="4f416-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicefabric/client)

## <a name="samples"></a><span data-ttu-id="4f416-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4f416-113">Samples</span></span>

* [<span data-ttu-id="4f416-114">Implantar e remover aplicativos usando o FabricClient</span><span class="sxs-lookup"><span data-stu-id="4f416-114">Deploy and remove applications using FabricClient</span></span>](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
