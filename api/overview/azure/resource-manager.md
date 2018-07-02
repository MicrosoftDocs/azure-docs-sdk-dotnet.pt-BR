---
title: Biblioteca do Azure Resource Manager para .NET
description: Referência para bibliotecas do Azure Resource Manager para .NET
keywords: Azure, .NET, SDK, API, Gerenciador de Recursos
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 5f36b826861071b263fac8bc22f8802ebb6505d1
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065316"
---
# <a name="azure-resource-manager-libraries-for-net"></a>Biblioteca do Azure Resource Manager para .NET

## <a name="overview"></a>Visão geral

O Azure Resource Manager permite trabalhar com os recursos da sua solução como um grupo.  Para obter mais informações sobre o Resource Manager, confira [Visão geral do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## <a name="management-library"></a>Biblioteca de gerenciamento

A biblioteca do Azure Resource Manager para .NET permite que você crie, atualize, exclua e liste os recursos e grupos de recursos.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a>Exemplo

Esse exemplo cria um novo grupo de recursos.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a>Exemplos

* [Gerenciar grupos de recursos](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group)
* [Gerenciar recursos](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [Implantar recursos com modelos do ARM](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template)
* [Implantar recursos com modelos do ARM (com progresso)](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
