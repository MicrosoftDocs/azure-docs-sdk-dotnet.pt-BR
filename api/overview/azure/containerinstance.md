---
title: Bibliotecas de Instâncias de Contêiner do Azure para .NET
description: Referência para bibliotecas de Instâncias de Contêiner do Azure para .NET
keywords: Azure, .NET, SDK, API, Instâncias de Contêiner, ACI
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 05/25/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: dcontainer-instances
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 033f67a989b0ed6cfcb67a6212c0d5c46c485afa
ms.sourcegitcommit: 4ae9f77a9300a4fe54d0179055ae61191078f207
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34567175"
---
# <a name="azure-container-instances-libraries-for-net"></a>Bibliotecas de Instâncias de Contêiner do Azure para .NET

Use as bibliotecas de Instâncias de Contêiner do Microsoft Azure para .NET para criar e gerenciar as instâncias de contêiner do Azure. Saiba mais lendo a [Visão geral das Instâncias de Contêiner do Azure](/azure/container-instances/container-instances-overview).

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para criar e gerenciar instâncias de contêiner do Azure no Azure.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="examples"></a>Exemplos

### <a name="create-container-group---single-container"></a>Criar grupo de contêineres - contêiner único

Este exemplo cria um grupo de contêineres com um único contêiner.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]

### <a name="create-container-group---multiple-containers"></a>Criar grupo de contêineres - vários contêineres

Este exemplo cria um grupo de contêineres com dois contêineres: um contêiner do aplicativo e um secundário.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]

### <a name="asynchronous-container-create-with-polling"></a>Criar contêiner assíncrono com a sondagem

Este exemplo cria um grupo de contêineres com um único contêiner usando o método para criar assíncrono. Então, ele pesquisa o Azure para obter o grupo de contêineres e gera o status do grupo de contêineres até que seu estado seja "Em execução".

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]

### <a name="create-task-based-container-group"></a>Criar grupo de contêineres baseado em tarefas

Este exemplo cria um grupo de contêineres com um único contêiner baseado em tarefas. O contêiner é configurado com uma [política de reiniciar](/azure/container-instances/container-instances-restart-policy) "Nunca" e uma [linha de comando personalizada](/azure/container-instances/container-instances-restart-policy#command-line-override).

Se você quiser executar um único comando com vários argumentos da linha de comando, por exemplo `echo FOO BAR`, deve fornecê-los como uma matriz de caracteres para o método `WithStartingCommandLines`. Por exemplo: 

`WithStartingCommandLines("echo", "FOO", "BAR")`

Se, no entanto, quiser executar vários comandos (potencialmente) vários argumentos, deve executar um shell e passar os comandos em cadeia como um argumento. Por exemplo, isso executa os comandos `echo` e `tail`:

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]

### <a name="list-container-groups"></a>Listar grupos de contêineres

Este exemplo lista os grupos de contêineres em um grupo de recursos.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]

### <a name="get-an-existing-container-group"></a>Obter um grupo de contêineres existente

Este exemplo obtém um grupo de contêineres específico que reside em um grupo de recursos, em seguida, imprime algumas de suas propriedades e valores.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]

### <a name="delete-a-container-group"></a>Excluir um grupo de contêineres

Este exemplo exclui um grupo de contêineres de um grupo de recursos.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]

## <a name="api-reference"></a>Referência de API

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a>Exemplos

* O código-fonte para os exemplos anteriores pode ser encontrado no GitHub:

  [Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]

* Mais exemplos de código das Instâncias de Contêiner do Azure:

  [Exemplos de Código do Azure][samples]

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
