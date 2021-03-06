---
title: Bibliotecas da Rede Virtual do Azure para .NET
description: Referência para bibliotecas da Rede Virtual do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: virtual-network
ms.openlocfilehash: 54dd79cf0f5bed1eab7b606b8a6e3b30c797ecd0
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190659"
---
# <a name="azure-virtual-network-libraries-for-net"></a>Bibliotecas da Rede Virtual do Azure para .NET

## <a name="overview"></a>Visão geral
O serviço [Rede Virtual do Azure](/azure/virtual-network/virtual-networks-overview) permite que você conecte com segurança os recursos do Azure usando Vnets (redes virtuais). Uma VNet é uma representação da sua própria rede na nuvem. Você também pode conectar as VNets entre si, permitindo que os recursos conectados a uma das VNets se comuniquem entre si. 

## <a name="management-library"></a>Biblioteca de gerenciamento

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Network.Fluent
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.Management.Network.Fluent
```

### <a name="code-example"></a>Exemplo de código
Este exemplo mostra como você pode criar uma rede virtual.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/network/management)

## <a name="samples"></a>Exemplos
- [Gerenciar Redes Virtuais com sub-redes](https://github.com/Azure-Samples/network-dotnet-manage-virtual-network)

Explorar mais [códigos de exemplo .NET](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console 
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package 

