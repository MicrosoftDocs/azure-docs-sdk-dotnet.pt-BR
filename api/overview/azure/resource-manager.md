---
title: Biblioteca do Azure Resource Manager para .NET
description: "Referência para bibliotecas do Azure Resource Manager para .NET"
keywords: Azure, .NET, SDK, API, Gerenciador de Recursos
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/31/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 4dcfdb59e3cbe919053937a62602de6b602bbac1
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-resource-manager-libraries-for-net"></a><span data-ttu-id="6cb19-104">Biblioteca do Azure Resource Manager para .NET</span><span class="sxs-lookup"><span data-stu-id="6cb19-104">Azure Resource Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="6cb19-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="6cb19-105">Overview</span></span>

<span data-ttu-id="6cb19-106">O Azure Resource Manager permite trabalhar com os recursos da sua solução como um grupo.</span><span class="sxs-lookup"><span data-stu-id="6cb19-106">Azure Resource Manager enables you to work with the resources in your solution as a group.</span></span>  <span data-ttu-id="6cb19-107">Para obter mais informações sobre o Resource Manager, confira [Visão geral do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="6cb19-107">For more information about Resource Manager, see [Azure Resource Manager overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="6cb19-108">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="6cb19-108">Management library</span></span>

<span data-ttu-id="6cb19-109">A biblioteca do Azure Resource Manager para .NET permite que você crie, atualize, exclua e liste os recursos e grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="6cb19-109">The Azure Resource Manager library for .NET enables you to create, update, delete, and list resources and resource groups.</span></span>

<span data-ttu-id="6cb19-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="6cb19-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="6cb19-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6cb19-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a><span data-ttu-id="6cb19-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cb19-112">Example</span></span>

<span data-ttu-id="6cb19-113">Esse exemplo cria um novo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="6cb19-113">This example creates a new resource group.</span></span>

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.ResourceManager.Fluent
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IResourceGroup resourceGroup = azure.ResourceGroups
    .Define("ResourceGroupName")
    .WithRegion(Region.USWest)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="6cb19-114">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="6cb19-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a><span data-ttu-id="6cb19-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6cb19-115">Samples</span></span>

* [<span data-ttu-id="6cb19-116">Gerenciar grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="6cb19-116">Manage resource groups</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group)
* [<span data-ttu-id="6cb19-117">Gerenciar recursos</span><span class="sxs-lookup"><span data-stu-id="6cb19-117">Manage resources</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [<span data-ttu-id="6cb19-118">Implantar recursos com modelos do ARM</span><span class="sxs-lookup"><span data-stu-id="6cb19-118">Deploy resources with ARM templates</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template)
* [<span data-ttu-id="6cb19-119">Implantar recursos com modelos do ARM (com progresso)</span><span class="sxs-lookup"><span data-stu-id="6cb19-119">Deploy resources with ARM templates (with progress)</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
