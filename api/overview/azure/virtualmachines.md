---
title: "Bibliotecas de computação do Azure para .NET"
description: "Referência para bibliotecas de computação do Azure para .NET"
keywords: "Azure, .NET, SDK, API, VM, máquinas virtuais, computação"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: b30c1433b8f25941fc1d4ea4718aa07c0a870580
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-virtual-machine-libraries-for-net"></a>Bibliotecas de máquina virtual do Azure para .NET

## <a name="overview"></a>Visão geral

Recursos de computação escalonáveis, sob demanda que executam Linux ou Windows.

Para começar a usar máquinas virtuais do Azure, consulte [Criar uma máquina virtual Linux com o portal do Azure](https://review.docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal).

## <a name="management-apis"></a>APIs de gerenciamento

Criar, configurar e expandir máquinas virtuais Windows e Linux no Azure a partir do seu código com a API de gerenciamento.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Compute.Fluent
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.Management.Compute.Fluent
```

### <a name="code-example"></a>Exemplo de código

CriE uma VM Windows.

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
> [Explorar as APIs de gerenciamento](https://review.docs.microsoft.com/en-us/dotnet/api/overview/azure/virtualmachines/management?view=azure-dotnet)

### <a name="samples"></a>Exemplos

* [Criar e gerenciar máquinas virtuais](/dotnet/azure/dotnet-sdk-azure-virtual-machine-samples)
* [Implantar uma VM habilitada para SSH com um modelo com o .NET](https://azure.microsoft.com/en-us/resources/samples/resource-manager-dotnet-template-deployment/)

Veja a [lista completa](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=VM) de exemplos de máquina virtual.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
