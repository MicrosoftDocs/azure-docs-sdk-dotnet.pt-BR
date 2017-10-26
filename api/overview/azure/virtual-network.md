---
title: Bibliotecas da Rede Virtual do Azure para .NET
description: "Referência para bibliotecas da Rede Virtual do Azure para .NET"
keywords: Azure, .NET, SDK, API, Rede Virtual
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: virtual-network
ms.custom: devcenter, svc-overview
ms.openlocfilehash: b67415344ef9cbf8af598a1fd43b6b47023bb071
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2017
---
# <a name="azure-virtual-network-libraries-for-net"></a><span data-ttu-id="9e436-104">Bibliotecas da Rede Virtual do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="9e436-104">Azure Virtual Network libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9e436-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9e436-105">Overview</span></span>
<span data-ttu-id="9e436-106">O serviço [Rede Virtual do Azure](/azure/virtual-network/virtual-networks-overview) permite que você conecte com segurança os recursos do Azure usando Vnets (redes virtuais).</span><span class="sxs-lookup"><span data-stu-id="9e436-106">The [Azure Virtual Network](/azure/virtual-network/virtual-networks-overview) service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="9e436-107">Uma VNet é uma representação da sua própria rede na nuvem.</span><span class="sxs-lookup"><span data-stu-id="9e436-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="9e436-108">Você também pode conectar as VNets entre si, permitindo que os recursos conectados a uma das VNets se comuniquem entre si.</span><span class="sxs-lookup"><span data-stu-id="9e436-108">You can also connect VNets to each other, enabling resources connected to either VNet to communicate with each other.</span></span> 

## <a name="management-library"></a><span data-ttu-id="9e436-109">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9e436-109">Management library</span></span>

<span data-ttu-id="9e436-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9e436-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9e436-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e436-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Network.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="9e436-112">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9e436-112">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Network.Fluent
```

### <a name="code-example"></a><span data-ttu-id="9e436-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="9e436-113">Code Example</span></span>
<span data-ttu-id="9e436-114">Este exemplo mostra como você pode criar uma rede virtual.</span><span class="sxs-lookup"><span data-stu-id="9e436-114">This example shows how you can create a virtual network.</span></span>

```csharp
/* 
  Include these "using" directives...
  
  using Microsoft.Azure.Management.Network.Fluent;
  using Microsoft.Azure.Management.Network.Fluent.Models;
*/
using (NetworkManagementClient client = new NetworkManagementClient(credentials))
{
    // Define VNet
    VirtualNetworkInner vnet = new VirtualNetworkInner()
    {
        Location = "West US",
        AddressSpace = new AddressSpace()
        {
            AddressPrefixes = new List<string>() { "0.0.0.0/16" }
        },

        DhcpOptions = new DhcpOptions()
        {
            DnsServers = new List<string>() { "1.1.1.1", "1.1.2.4" }
        },

        Subnets = new List<Subnet>()
        {
            new Subnet()
            {
                Name = subnet1Name,
                AddressPrefix = "1.0.1.0/24",
            },
            new Subnet()
            {
                Name = subnet2Name,
               AddressPrefix = "1.0.2.0/24",
            }
        }
    };
    
    await client.VirtualNetworks.CreateOrUpdateAsync(resourceGroupName, vNetName, vnet);
}

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e436-115">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9e436-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/network/management)

## <a name="samples"></a><span data-ttu-id="9e436-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e436-116">Samples</span></span>
- [<span data-ttu-id="9e436-117">Gerenciar Redes Virtuais com sub-redes</span><span class="sxs-lookup"><span data-stu-id="9e436-117">Managing Virtual Networks with subnets</span></span>](https://github.com/Azure-Samples/network-dotnet-manage-virtual-network)

<span data-ttu-id="9e436-118">Explorar mais [códigos de exemplo .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9e436-118">Explore more [.NET sample code](https://azure.microsoft.com/resources/samples/?platform=dotnet) that you can use in your apps.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console 
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package 

