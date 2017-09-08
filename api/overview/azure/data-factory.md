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
# <a name="azure-data-factory-libraries-for-net"></a>Bibliotecas do Azure Data Factory para .NET

## <a name="overview"></a>Visão geral

O Azure Data Factory é um serviço de integração de dados baseado em nuvem. Ele permite que você crie fluxos de trabalho gerados por dados na nuvem para orquestrar e automatizar a movimentação e a transformação de dados.

Para saber mais, leia a [Introdução ao Azure Data Factory](/azure/data-factory/data-factory-introduction).

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para criar e agendar os fluxos de trabalho gerados por dados (pipelines).

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].

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
