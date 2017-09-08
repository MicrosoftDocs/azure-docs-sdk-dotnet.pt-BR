---
title: Bibliotecas do Azure Data Factory para .NET
description: "Referência para bibliotecas do Azure Data Factory para .NET"
keywords: Azure, .NET, SDK, API, Data Factory
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/20/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: e0b85d7d3988febca6dce7f4038825d74e4b8d2e
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-data-factory-libraries-for-net"></a><span data-ttu-id="bfbfe-104">Bibliotecas do Azure Data Factory para .NET</span><span class="sxs-lookup"><span data-stu-id="bfbfe-104">Azure Data Factory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="bfbfe-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="bfbfe-105">Overview</span></span>

<span data-ttu-id="bfbfe-106">O Azure Data Factory é um serviço de integração de dados baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="bfbfe-106">Azure Data Factory is a cloud-based data integration service.</span></span> <span data-ttu-id="bfbfe-107">Ele permite que você crie fluxos de trabalho gerados por dados na nuvem para orquestrar e automatizar a movimentação e a transformação de dados.</span><span class="sxs-lookup"><span data-stu-id="bfbfe-107">It enables you to create data-driven workflows in the cloud to orchestrate and automate data movement and data transformation.</span></span>

<span data-ttu-id="bfbfe-108">Para saber mais, leia a [Introdução ao Azure Data Factory](/azure/data-factory/data-factory-introduction).</span><span class="sxs-lookup"><span data-stu-id="bfbfe-108">To learn more, read the [Introduction to Azure Data Factory](/azure/data-factory/data-factory-introduction).</span></span>

## <a name="management-library"></a><span data-ttu-id="bfbfe-109">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bfbfe-109">Management library</span></span>

<span data-ttu-id="bfbfe-110">Use a biblioteca de gerenciamento para criar e agendar os fluxos de trabalho gerados por dados (pipelines).</span><span class="sxs-lookup"><span data-stu-id="bfbfe-110">Use the management library to create and schedule data-driven workflows (pipelines).</span></span>

<span data-ttu-id="bfbfe-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="bfbfe-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="bfbfe-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bfbfe-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a><span data-ttu-id="bfbfe-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="bfbfe-113">Code Example</span></span>

<span data-ttu-id="bfbfe-114">O exemplo a seguir usa a biblioteca de gerenciamento para criar um data factory.</span><span class="sxs-lookup"><span data-stu-id="bfbfe-114">The following example uses the management library to create a data factory.</span></span>

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
> [<span data-ttu-id="bfbfe-115">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bfbfe-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a><span data-ttu-id="bfbfe-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bfbfe-116">Samples</span></span>

* <span data-ttu-id="bfbfe-117">[MyDriving - Um aplicativo de exemplo móvel e de IoT do Azure](https://azure.microsoft.com/resources/samples/mydriving/) que usa o Data Factory para gerar informações.</span><span class="sxs-lookup"><span data-stu-id="bfbfe-117">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) that uses Data Factory to drive insights.</span></span>

<span data-ttu-id="bfbfe-118">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bfbfe-118">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
