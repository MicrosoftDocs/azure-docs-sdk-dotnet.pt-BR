---
title: Biblioteca do Azure Resource Manager para .NET
description: Referência para bibliotecas do Azure Resource Manager para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: 6d3a27c5f7ba94f5579723cc4f798826c8bdefd6
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190830"
---
# <a name="azure-resource-manager-libraries-for-net"></a><span data-ttu-id="51597-103">Biblioteca do Azure Resource Manager para .NET</span><span class="sxs-lookup"><span data-stu-id="51597-103">Azure Resource Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="51597-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="51597-104">Overview</span></span>

<span data-ttu-id="51597-105">O Azure Resource Manager permite trabalhar com os recursos da sua solução como um grupo.</span><span class="sxs-lookup"><span data-stu-id="51597-105">Azure Resource Manager enables you to work with the resources in your solution as a group.</span></span>  <span data-ttu-id="51597-106">Para obter mais informações sobre o Resource Manager, confira [Visão geral do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="51597-106">For more information about Resource Manager, see [Azure Resource Manager overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="51597-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="51597-107">Management library</span></span>

<span data-ttu-id="51597-108">A biblioteca do Azure Resource Manager para .NET permite que você crie, atualize, exclua e liste os recursos e grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="51597-108">The Azure Resource Manager library for .NET enables you to create, update, delete, and list resources and resource groups.</span></span>

<span data-ttu-id="51597-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="51597-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="51597-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51597-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a><span data-ttu-id="51597-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51597-111">Example</span></span>

<span data-ttu-id="51597-112">Esse exemplo cria um novo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="51597-112">This example creates a new resource group.</span></span>

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.ResourceManager.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IResourceGroup resourceGroup = azure.ResourceGroups
    .Define("ResourceGroupName")
    .WithRegion(Region.USWest)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="51597-113">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="51597-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a><span data-ttu-id="51597-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="51597-114">Samples</span></span>

* [<span data-ttu-id="51597-115">Gerenciar grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="51597-115">Manage resource groups</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group)
* [<span data-ttu-id="51597-116">Gerenciar recursos</span><span class="sxs-lookup"><span data-stu-id="51597-116">Manage resources</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [<span data-ttu-id="51597-117">Implantar recursos com modelos do ARM</span><span class="sxs-lookup"><span data-stu-id="51597-117">Deploy resources with ARM templates</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template)
* [<span data-ttu-id="51597-118">Implantar recursos com modelos do ARM (com progresso)</span><span class="sxs-lookup"><span data-stu-id="51597-118">Deploy resources with ARM templates (with progress)</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
