---
title: Bibliotecas de computação do Azure para .NET
description: Referência para bibliotecas de computação do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: virtual-machines
ms.openlocfilehash: ee481e0f2448a874629bec36a719e7682407d320
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190689"
---
# <a name="azure-virtual-machine-libraries-for-net"></a><span data-ttu-id="f21d0-103">Bibliotecas de máquina virtual do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="f21d0-103">Azure virtual machine libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f21d0-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f21d0-104">Overview</span></span>

<span data-ttu-id="f21d0-105">Recursos de computação escalonáveis, sob demanda que executam Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="f21d0-105">On-demand, scalable computing resources running Linux or Windows.</span></span>

<span data-ttu-id="f21d0-106">Para começar a usar máquinas virtuais do Azure, consulte [Criar uma máquina virtual Linux com o portal do Azure](https://review.docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal).</span><span class="sxs-lookup"><span data-stu-id="f21d0-106">To get started with Azure virtual machines, see [Create a Linux virtual machine with the Azure portal](https://review.docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal).</span></span>

## <a name="management-apis"></a><span data-ttu-id="f21d0-107">APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f21d0-107">Management APIs</span></span>

<span data-ttu-id="f21d0-108">Criar, configurar e expandir máquinas virtuais Windows e Linux no Azure a partir do seu código com a API de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="f21d0-108">Create, configure, and scale out Windows and Linux virtual machines in Azure from your code with the management API.</span></span>

<span data-ttu-id="f21d0-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f21d0-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f21d0-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f21d0-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Compute.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="f21d0-111">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f21d0-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Compute.Fluent
```

### <a name="code-example"></a><span data-ttu-id="f21d0-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f21d0-112">Code Example</span></span>

<span data-ttu-id="f21d0-113">CriE uma VM Windows.</span><span class="sxs-lookup"><span data-stu-id="f21d0-113">Create a Windows VM.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IVirtualMachine windowsVM = azure.VirtualMachines.Define("MyVirtualMachine")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress("MyIPAddressLabel")
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername("UserName")
    .WithAdminPassword("Password")
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f21d0-114">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f21d0-114">Explore the management APIs</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/virtualmachines/management?view=azure-dotnet)

### <a name="samples"></a><span data-ttu-id="f21d0-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f21d0-115">Samples</span></span>

* [<span data-ttu-id="f21d0-116">Criar e gerenciar máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="f21d0-116">Create and manage virtual machines</span></span>](/dotnet/azure/dotnet-sdk-azure-virtual-machine-samples)
* [<span data-ttu-id="f21d0-117">Implantar uma VM habilitada para SSH com um modelo com o .NET</span><span class="sxs-lookup"><span data-stu-id="f21d0-117">Deploy an SSH-enabled VM with a Template with .NET</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-dotnet-template-deployment/)

<span data-ttu-id="f21d0-118">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=VM) de exemplos de máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="f21d0-118">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=VM) of virtual machine samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
