---
title: Bibliotecas de Instâncias de Contêiner do Azure para .NET
description: Referência para bibliotecas de Instâncias de Contêiner do Azure para .NET
keywords: Azure, .NET, SDK, API, Instâncias de Contêiner, ACI
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 06/11/2018
ms.topic: reference
ms.devlang: dotnet
ms.service: dcontainer-instances
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 85fe5485c04193b336d10e8c387719e2ad1e6910
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37066137"
---
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="bee4b-104">Bibliotecas de Instâncias de Contêiner do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="bee4b-104">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="bee4b-105">Use as bibliotecas de Instâncias de Contêiner do Microsoft Azure para .NET para criar e gerenciar as instâncias de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="bee4b-105">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="bee4b-106">Saiba mais lendo a [Visão geral das Instâncias de Contêiner do Azure](/azure/container-instances/container-instances-overview).</span><span class="sxs-lookup"><span data-stu-id="bee4b-106">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="bee4b-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bee4b-107">Management library</span></span>

<span data-ttu-id="bee4b-108">Use a biblioteca de gerenciamento para criar e gerenciar instâncias de contêiner do Azure no Azure.</span><span class="sxs-lookup"><span data-stu-id="bee4b-108">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="bee4b-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="bee4b-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="bee4b-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bee4b-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="example-source"></a><span data-ttu-id="bee4b-111">Fonte de exemplo</span><span class="sxs-lookup"><span data-stu-id="bee4b-111">Example source</span></span>

<span data-ttu-id="bee4b-112">Se quiser ver os seguintes exemplos de código em contexto, você pode encontrá-los no repositório do GitHub a seguir:</span><span class="sxs-lookup"><span data-stu-id="bee4b-112">If you'd like to see the following code examples in context, you can find them in the following GitHub repository:</span></span>

[<span data-ttu-id="bee4b-113">Azure-Samples/aci-docs-sample-dotnet</span><span class="sxs-lookup"><span data-stu-id="bee4b-113">Azure-Samples/aci-docs-sample-dotnet</span></span>](https://github.com/Azure-Samples/aci-docs-sample-dotnet)

## <a name="authentication"></a><span data-ttu-id="bee4b-114">Autenticação</span><span class="sxs-lookup"><span data-stu-id="bee4b-114">Authentication</span></span>

<span data-ttu-id="bee4b-115">Uma das maneiras mais fáceis de autenticar clientes de SDK é com a [autenticação baseada em arquivo][sdk-auth].</span><span class="sxs-lookup"><span data-stu-id="bee4b-115">One of the easiest ways to authenticate SDK clients is with [file-based authentication][sdk-auth].</span></span> <span data-ttu-id="bee4b-116">A autenticação baseada em arquivo analisa um arquivo de credenciais ao criar uma instância do objeto de cliente [IAzure][iazure], que, depois, usa essas credenciais ao autenticar com o Azure.</span><span class="sxs-lookup"><span data-stu-id="bee4b-116">File-based authentication parses a credentials file when instantiating the [IAzure][iazure] client object, which then uses those credentials when authenticating with Azure.</span></span> <span data-ttu-id="bee4b-117">Para usar a autenticação baseada em arquivo:</span><span class="sxs-lookup"><span data-stu-id="bee4b-117">To use file-based authentication:</span></span>

1. <span data-ttu-id="bee4b-118">Criar um arquivo de credenciais com a [CLI do Azure](/cli/azure) ou o [Cloud Shell](https://shell.azure.com/):</span><span class="sxs-lookup"><span data-stu-id="bee4b-118">Create a credentials file with the [Azure CLI](/cli/azure) or [Cloud Shell](https://shell.azure.com/):</span></span>

   `az ad sp create-for-rbac --sdk-auth > my.azureauth`

   <span data-ttu-id="bee4b-119">Se você usar o [Cloud Shell](https://shell.azure.com/) para gerar o arquivo de credenciais, copie o conteúdo em um arquivo local onde seu aplicativo .NET possa acessar.</span><span class="sxs-lookup"><span data-stu-id="bee4b-119">If you use the [Cloud Shell](https://shell.azure.com/) to generate the credentials file, copy its contents into a local file that your .NET application can access.</span></span>

2. <span data-ttu-id="bee4b-120">Defina a variável de ambiente `AZURE_AUTH_LOCATION` para o caminho completo do arquivo de credenciais gerado.</span><span class="sxs-lookup"><span data-stu-id="bee4b-120">Set the `AZURE_AUTH_LOCATION` environment variable to the full path of the generated credentials file.</span></span> <span data-ttu-id="bee4b-121">Por exemplo (no shell Bash):</span><span class="sxs-lookup"><span data-stu-id="bee4b-121">For example (in the Bash shell):</span></span>

   ```bash
   export AZURE_AUTH_LOCATION=/home/yourusername/my.azureauth
   ```

<span data-ttu-id="bee4b-122">Depois de criar o arquivo de credenciais e preencher a variável de ambiente `AZURE_AUTH_LOCATION`, use o método [Azure.Authenticate][iazure-authenticate] para inicializar o objeto de cliente [IAzure][iazure].</span><span class="sxs-lookup"><span data-stu-id="bee4b-122">Once you've created the credentials file and populated the `AZURE_AUTH_LOCATION` environment variable, use the [Azure.Authenticate][iazure-authenticate] method to initialize the [IAzure][iazure] client object.</span></span> <span data-ttu-id="bee4b-123">O projeto de exemplo obtém primeiro o valor de `AZURE_AUTH_LOCATION` e, em seguida, chama um método que retorna um objeto de cliente `IAzure` inicializado:</span><span class="sxs-lookup"><span data-stu-id="bee4b-123">The example project first obtains the `AZURE_AUTH_LOCATION` value, then calls a method that returns an initialized `IAzure` client object:</span></span>

<span data-ttu-id="bee4b-124"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-124"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span></span>

<span data-ttu-id="bee4b-125">Esse método do aplicativo de exemplo retorna a instância [IAzure][iazure] inicializada, que é passada como o primeiro parâmetro para todos os outros métodos no exemplo:</span><span class="sxs-lookup"><span data-stu-id="bee4b-125">This method from the sample application returns the initialized [IAzure][iazure] instance, which is then passed as the first parameter to all other methods in the sample:</span></span>

<span data-ttu-id="bee4b-126"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-126"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span></span>

<span data-ttu-id="bee4b-127">Para obter mais detalhes sobre os métodos de autenticação disponíveis nas bibliotecas de gerenciamento do .NET para Azure, confira [Autenticar em Bibliotecas de Gerenciamento do Azure para .NET][sdk-auth].</span><span class="sxs-lookup"><span data-stu-id="bee4b-127">For more details about the available authentication methods in the .NET management libraries for Azure, see [Authentication in Azure Management Libraries for .NET][sdk-auth].</span></span>

## <a name="create-container-group---single-container"></a><span data-ttu-id="bee4b-128">Criar grupo de contêineres - contêiner único</span><span class="sxs-lookup"><span data-stu-id="bee4b-128">Create container group - single container</span></span>

<span data-ttu-id="bee4b-129">Este exemplo cria um grupo de contêineres com um único contêiner.</span><span class="sxs-lookup"><span data-stu-id="bee4b-129">This example creates a container group with a single container.</span></span>

<span data-ttu-id="bee4b-130"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-130"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span></span>

## <a name="create-container-group---multiple-containers"></a><span data-ttu-id="bee4b-131">Criar grupo de contêineres - vários contêineres</span><span class="sxs-lookup"><span data-stu-id="bee4b-131">Create container group - multiple containers</span></span>

<span data-ttu-id="bee4b-132">Este exemplo cria um grupo de contêineres com dois contêineres: um contêiner do aplicativo e um secundário.</span><span class="sxs-lookup"><span data-stu-id="bee4b-132">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<span data-ttu-id="bee4b-133"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-133"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span></span>

## <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="bee4b-134">Criar contêiner assíncrono com a sondagem</span><span class="sxs-lookup"><span data-stu-id="bee4b-134">Asynchronous container create with polling</span></span>

<span data-ttu-id="bee4b-135">Este exemplo cria um grupo de contêineres com um único contêiner usando o método para criar assíncrono.</span><span class="sxs-lookup"><span data-stu-id="bee4b-135">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="bee4b-136">Então, ele pesquisa o Azure para obter o grupo de contêineres e gera o status do grupo de contêineres até que seu estado seja "Em execução".</span><span class="sxs-lookup"><span data-stu-id="bee4b-136">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<span data-ttu-id="bee4b-137"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-137"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span></span>

## <a name="create-task-based-container-group"></a><span data-ttu-id="bee4b-138">Criar grupo de contêineres baseado em tarefas</span><span class="sxs-lookup"><span data-stu-id="bee4b-138">Create task-based container group</span></span>

<span data-ttu-id="bee4b-139">Este exemplo cria um grupo de contêineres com um único contêiner baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="bee4b-139">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="bee4b-140">O contêiner é configurado com uma [política de reiniciar](/azure/container-instances/container-instances-restart-policy) "Nunca" e uma [linha de comando personalizada](/azure/container-instances/container-instances-restart-policy#command-line-override).</span><span class="sxs-lookup"><span data-stu-id="bee4b-140">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="bee4b-141">Se você quiser executar um único comando com vários argumentos da linha de comando, por exemplo `echo FOO BAR`, deve fornecê-los como uma matriz de caracteres para o método `WithStartingCommandLines`.</span><span class="sxs-lookup"><span data-stu-id="bee4b-141">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="bee4b-142">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="bee4b-142">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="bee4b-143">Se, no entanto, quiser executar vários comandos (potencialmente) vários argumentos, deve executar um shell e passar os comandos em cadeia como um argumento.</span><span class="sxs-lookup"><span data-stu-id="bee4b-143">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="bee4b-144">Por exemplo, isso executa os comandos `echo` e `tail`:</span><span class="sxs-lookup"><span data-stu-id="bee4b-144">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<span data-ttu-id="bee4b-145"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-145"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span></span>

## <a name="list-container-groups"></a><span data-ttu-id="bee4b-146">Listar grupos de contêineres</span><span class="sxs-lookup"><span data-stu-id="bee4b-146">List container groups</span></span>

<span data-ttu-id="bee4b-147">Este exemplo lista os grupos de contêineres em um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="bee4b-147">This example lists the container groups in a resource group.</span></span>

<span data-ttu-id="bee4b-148"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-148"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span></span>

## <a name="get-an-existing-container-group"></a><span data-ttu-id="bee4b-149">Obter um grupo de contêineres existente</span><span class="sxs-lookup"><span data-stu-id="bee4b-149">Get an existing container group</span></span>

<span data-ttu-id="bee4b-150">Este exemplo obtém um grupo de contêineres específico que reside em um grupo de recursos, em seguida, imprime algumas de suas propriedades e valores.</span><span class="sxs-lookup"><span data-stu-id="bee4b-150">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<span data-ttu-id="bee4b-151"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-151"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span></span>

## <a name="delete-a-container-group"></a><span data-ttu-id="bee4b-152">Excluir um grupo de contêineres</span><span class="sxs-lookup"><span data-stu-id="bee4b-152">Delete a container group</span></span>

<span data-ttu-id="bee4b-153">Este exemplo exclui um grupo de contêineres de um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="bee4b-153">This example deletes a container group from a resource group.</span></span>

<span data-ttu-id="bee4b-154"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span><span class="sxs-lookup"><span data-stu-id="bee4b-154"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span></span>

## <a name="api-reference"></a><span data-ttu-id="bee4b-155">Referência de API</span><span class="sxs-lookup"><span data-stu-id="bee4b-155">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bee4b-156">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bee4b-156">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="bee4b-157">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bee4b-157">Samples</span></span>

* <span data-ttu-id="bee4b-158">O código-fonte para os exemplos anteriores pode ser encontrado no GitHub:</span><span class="sxs-lookup"><span data-stu-id="bee4b-158">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="bee4b-159">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="bee4b-159">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="bee4b-160">Mais exemplos de código das Instâncias de Contêiner do Azure:</span><span class="sxs-lookup"><span data-stu-id="bee4b-160">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="bee4b-161">[Exemplos de Código do Azure][samples]</span><span class="sxs-lookup"><span data-stu-id="bee4b-161">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="bee4b-162">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bee4b-162">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

<!-- LINKS - External -->
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[sdk-auth]: https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md

<!-- LINKS - Internal -->
[DotNetCLI]: /dotnet/core/tools/dotnet-add-package
[PackageManager]: /nuget/tools/package-manager-console
[iazure]: /dotnet/api/microsoft.azure.management.fluent.azure
[iazure-authenticate]: /dotnet/api/microsoft.azure.management.fluent.azure.authenticate
