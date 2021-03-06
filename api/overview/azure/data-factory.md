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
# <a name="azure-data-factory-libraries-for-net"></a>Bibliotecas do Azure Data Factory para .NET

## <a name="overview"></a>Visão geral

O Azure Data Factory é um serviço de integração de dados baseado em nuvem. Ele permite que você crie fluxos de trabalho gerados por dados na nuvem para orquestrar e automatizar a movimentação e a transformação de dados.

Para saber mais, leia a [Introdução ao Azure Data Factory](/azure/data-factory/data-factory-introduction).

## <a name="management-library---data-factory-v2-preview"></a>Biblioteca de gerenciamento - Data Factory V2 (Versão prévia)

Use a biblioteca de gerenciamento para criar e agendar os fluxos de trabalho gerados por dados (pipelines) no Data Factory V2 (Versão prévia).  Para obter mais informações, confira [Criar um data factory e pipeline usando o SDK do .NET](/azure/data-factory/quickstart-create-data-factory-dot-net).

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
# Get the most recent prerelease package
Install-Package Microsoft.Azure.Management.DataFactory -Prerelease
```

```bash
# Be sure to include the most recent version from the NuGet package page
dotnet add package Microsoft.Azure.Management.DataFactory --version 0.2.0-preview
```

### <a name="code-example"></a>Exemplo de código

O exemplo a seguir usa a biblioteca de gerenciamento para criar um data factory.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/microsoft.azure.management.datafactory)

## <a name="management-library---data-factory-v1"></a>Biblioteca de gerenciamento - Data Factory V1

Use a biblioteca de gerenciamento para criar e agendar os fluxos de trabalho gerados por dados (pipelines) no Data Factory Versão 1.  Para obter mais informações, consulte a documentação para [Data Factory Versão 1](/azure/data-factory/v1/data-factory-introduction).

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a>Exemplo de código

O exemplo a seguir usa a biblioteca de gerenciamento para criar um data factory.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a>Exemplos

* [MyDriving - Um aplicativo de exemplo móvel e de IoT do Azure](https://azure.microsoft.com/resources/samples/mydriving/) que usa o Data Factory para gerar informações.

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
