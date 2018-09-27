---
title: Bibliotecas do Azure Data Factory para .NET
description: Referência para bibliotecas do Azure Data Factory para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-factory
ms.openlocfilehash: 9a779f223cd0e158e99afcf1ee011d121f2fe838
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190319"
---
# <a name="azure-data-factory-libraries-for-net"></a><span data-ttu-id="4540f-103">Bibliotecas do Azure Data Factory para .NET</span><span class="sxs-lookup"><span data-stu-id="4540f-103">Azure Data Factory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="4540f-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="4540f-104">Overview</span></span>

<span data-ttu-id="4540f-105">O Azure Data Factory é um serviço de integração de dados baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="4540f-105">Azure Data Factory is a cloud-based data integration service.</span></span> <span data-ttu-id="4540f-106">Ele permite que você crie fluxos de trabalho gerados por dados na nuvem para orquestrar e automatizar a movimentação e a transformação de dados.</span><span class="sxs-lookup"><span data-stu-id="4540f-106">It enables you to create data-driven workflows in the cloud to orchestrate and automate data movement and data transformation.</span></span>

<span data-ttu-id="4540f-107">Para saber mais, leia a [Introdução ao Azure Data Factory](/azure/data-factory/data-factory-introduction).</span><span class="sxs-lookup"><span data-stu-id="4540f-107">To learn more, read the [Introduction to Azure Data Factory](/azure/data-factory/data-factory-introduction).</span></span>

## <a name="management-library---data-factory-v2-preview"></a><span data-ttu-id="4540f-108">Biblioteca de gerenciamento - Data Factory V2 (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="4540f-108">Management library - Data Factory V2 (Preview)</span></span>

<span data-ttu-id="4540f-109">Use a biblioteca de gerenciamento para criar e agendar os fluxos de trabalho gerados por dados (pipelines) no Data Factory V2 (Versão prévia).</span><span class="sxs-lookup"><span data-stu-id="4540f-109">Use the management library to create and schedule data-driven workflows (pipelines) in Data Factory V2 (Preview).</span></span>  <span data-ttu-id="4540f-110">Para obter mais informações, confira [Criar um data factory e pipeline usando o SDK do .NET](/azure/data-factory/quickstart-create-data-factory-dot-net).</span><span class="sxs-lookup"><span data-stu-id="4540f-110">For more information, see [Create a data factory and pipeline using .NET SDK](/azure/data-factory/quickstart-create-data-factory-dot-net).</span></span>

<span data-ttu-id="4540f-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4540f-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4540f-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4540f-112">Visual Studio Package Manager</span></span>

```powershell
# Get the most recent prerelease package
Install-Package Microsoft.Azure.Management.DataFactory -Prerelease
```

```bash
# Be sure to include the most recent version from the NuGet package page
dotnet add package Microsoft.Azure.Management.DataFactory --version 0.2.0-preview
```

### <a name="code-example"></a><span data-ttu-id="4540f-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4540f-113">Code Example</span></span>

<span data-ttu-id="4540f-114">O exemplo a seguir usa a biblioteca de gerenciamento para criar um data factory.</span><span class="sxs-lookup"><span data-stu-id="4540f-114">The following example uses the management library to create a data factory.</span></span>

```csharp
/*
using Microsoft.Azure.Management.ResourceManager;
using Microsoft.Azure.Management.DataFactory;
using Microsoft.Azure.Management.DataFactory.Models;
*/

DataFactoryManagementClient client = new DataFactoryManagementClient(tokenCredentials) { SubscriptionId = subscriptionId };
Factory dataFactory = new Factory
{
    Location = region,
    Identity = new FactoryIdentity()
};
client.Factories.CreateOrUpdate(resourceGroup, dataFactoryName, dataFactory);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="4540f-115">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4540f-115">Explore the management APIs</span></span>](/dotnet/api/microsoft.azure.management.datafactory)

## <a name="management-library---data-factory-v1"></a><span data-ttu-id="4540f-116">Biblioteca de gerenciamento - Data Factory V1</span><span class="sxs-lookup"><span data-stu-id="4540f-116">Management library - Data Factory V1</span></span>

<span data-ttu-id="4540f-117">Use a biblioteca de gerenciamento para criar e agendar os fluxos de trabalho gerados por dados (pipelines) no Data Factory Versão 1.</span><span class="sxs-lookup"><span data-stu-id="4540f-117">Use the management library to create and schedule data-driven workflows (pipelines) in Data Factory Version 1.</span></span>  <span data-ttu-id="4540f-118">Para obter mais informações, consulte a documentação para [Data Factory Versão 1](/azure/data-factory/v1/data-factory-introduction).</span><span class="sxs-lookup"><span data-stu-id="4540f-118">For more information, review the documentation for [Data Factory Version 1](/azure/data-factory/v1/data-factory-introduction).</span></span>

<span data-ttu-id="4540f-119">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="4540f-119">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4540f-120">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4540f-120">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a><span data-ttu-id="4540f-121">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4540f-121">Code Example</span></span>

<span data-ttu-id="4540f-122">O exemplo a seguir usa a biblioteca de gerenciamento para criar um data factory.</span><span class="sxs-lookup"><span data-stu-id="4540f-122">The following example uses the management library to create a data factory.</span></span>

```csharp
DataFactoryManagementClient client = new DataFactoryManagementClient(aadTokenCredentials, resourceManagerUri);
client.DataFactories.CreateOrUpdate(resourceGroupName,
    new DataFactoryCreateOrUpdateParameters()
    {
        DataFactory = new DataFactory()
        {
            Name = dataFactoryName,
            Location = "westus",
            Properties = new DataFactoryProperties()
        }
    }
);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="4540f-123">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4540f-123">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a><span data-ttu-id="4540f-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4540f-124">Samples</span></span>

* <span data-ttu-id="4540f-125">[MyDriving - Um aplicativo de exemplo móvel e de IoT do Azure](https://azure.microsoft.com/resources/samples/mydriving/) que usa o Data Factory para gerar informações.</span><span class="sxs-lookup"><span data-stu-id="4540f-125">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) that uses Data Factory to drive insights.</span></span>

<span data-ttu-id="4540f-126">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4540f-126">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
