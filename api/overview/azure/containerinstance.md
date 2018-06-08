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
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="8b444-104">Bibliotecas de Instâncias de Contêiner do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="8b444-104">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="8b444-105">Use as bibliotecas de Instâncias de Contêiner do Microsoft Azure para .NET para criar e gerenciar as instâncias de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="8b444-105">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="8b444-106">Saiba mais lendo a [Visão geral das Instâncias de Contêiner do Azure](/azure/container-instances/container-instances-overview).</span><span class="sxs-lookup"><span data-stu-id="8b444-106">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="8b444-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="8b444-107">Management library</span></span>

<span data-ttu-id="8b444-108">Use a biblioteca de gerenciamento para criar e gerenciar instâncias de contêiner do Azure no Azure.</span><span class="sxs-lookup"><span data-stu-id="8b444-108">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="8b444-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8b444-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="8b444-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b444-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="examples"></a><span data-ttu-id="8b444-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8b444-111">Examples</span></span>

### <a name="create-container-group---single-container"></a><span data-ttu-id="8b444-112">Criar grupo de contêineres - contêiner único</span><span class="sxs-lookup"><span data-stu-id="8b444-112">Create container group - single container</span></span>

<span data-ttu-id="8b444-113">Este exemplo cria um grupo de contêineres com um único contêiner.</span><span class="sxs-lookup"><span data-stu-id="8b444-113">This example creates a container group with a single container.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]

### <a name="create-container-group---multiple-containers"></a><span data-ttu-id="8b444-114">Criar grupo de contêineres - vários contêineres</span><span class="sxs-lookup"><span data-stu-id="8b444-114">Create container group - multiple containers</span></span>

<span data-ttu-id="8b444-115">Este exemplo cria um grupo de contêineres com dois contêineres: um contêiner do aplicativo e um secundário.</span><span class="sxs-lookup"><span data-stu-id="8b444-115">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]

### <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="8b444-116">Criar contêiner assíncrono com a sondagem</span><span class="sxs-lookup"><span data-stu-id="8b444-116">Asynchronous container create with polling</span></span>

<span data-ttu-id="8b444-117">Este exemplo cria um grupo de contêineres com um único contêiner usando o método para criar assíncrono.</span><span class="sxs-lookup"><span data-stu-id="8b444-117">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="8b444-118">Então, ele pesquisa o Azure para obter o grupo de contêineres e gera o status do grupo de contêineres até que seu estado seja "Em execução".</span><span class="sxs-lookup"><span data-stu-id="8b444-118">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]

### <a name="create-task-based-container-group"></a><span data-ttu-id="8b444-119">Criar grupo de contêineres baseado em tarefas</span><span class="sxs-lookup"><span data-stu-id="8b444-119">Create task-based container group</span></span>

<span data-ttu-id="8b444-120">Este exemplo cria um grupo de contêineres com um único contêiner baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="8b444-120">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="8b444-121">O contêiner é configurado com uma [política de reiniciar](/azure/container-instances/container-instances-restart-policy) "Nunca" e uma [linha de comando personalizada](/azure/container-instances/container-instances-restart-policy#command-line-override).</span><span class="sxs-lookup"><span data-stu-id="8b444-121">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="8b444-122">Se você quiser executar um único comando com vários argumentos da linha de comando, por exemplo `echo FOO BAR`, deve fornecê-los como uma matriz de caracteres para o método `WithStartingCommandLines`.</span><span class="sxs-lookup"><span data-stu-id="8b444-122">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="8b444-123">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="8b444-123">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="8b444-124">Se, no entanto, quiser executar vários comandos (potencialmente) vários argumentos, deve executar um shell e passar os comandos em cadeia como um argumento.</span><span class="sxs-lookup"><span data-stu-id="8b444-124">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="8b444-125">Por exemplo, isso executa os comandos `echo` e `tail`:</span><span class="sxs-lookup"><span data-stu-id="8b444-125">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]

### <a name="list-container-groups"></a><span data-ttu-id="8b444-126">Listar grupos de contêineres</span><span class="sxs-lookup"><span data-stu-id="8b444-126">List container groups</span></span>

<span data-ttu-id="8b444-127">Este exemplo lista os grupos de contêineres em um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="8b444-127">This example lists the container groups in a resource group.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]

### <a name="get-an-existing-container-group"></a><span data-ttu-id="8b444-128">Obter um grupo de contêineres existente</span><span class="sxs-lookup"><span data-stu-id="8b444-128">Get an existing container group</span></span>

<span data-ttu-id="8b444-129">Este exemplo obtém um grupo de contêineres específico que reside em um grupo de recursos, em seguida, imprime algumas de suas propriedades e valores.</span><span class="sxs-lookup"><span data-stu-id="8b444-129">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]

### <a name="delete-a-container-group"></a><span data-ttu-id="8b444-130">Excluir um grupo de contêineres</span><span class="sxs-lookup"><span data-stu-id="8b444-130">Delete a container group</span></span>

<span data-ttu-id="8b444-131">Este exemplo exclui um grupo de contêineres de um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="8b444-131">This example deletes a container group from a resource group.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]

## <a name="api-reference"></a><span data-ttu-id="8b444-132">Referência de API</span><span class="sxs-lookup"><span data-stu-id="8b444-132">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8b444-133">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="8b444-133">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="8b444-134">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8b444-134">Samples</span></span>

* <span data-ttu-id="8b444-135">O código-fonte para os exemplos anteriores pode ser encontrado no GitHub:</span><span class="sxs-lookup"><span data-stu-id="8b444-135">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="8b444-136">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="8b444-136">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="8b444-137">Mais exemplos de código das Instâncias de Contêiner do Azure:</span><span class="sxs-lookup"><span data-stu-id="8b444-137">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="8b444-138">[Exemplos de Código do Azure][samples]</span><span class="sxs-lookup"><span data-stu-id="8b444-138">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="8b444-139">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8b444-139">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
