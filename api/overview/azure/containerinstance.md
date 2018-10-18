---
title: Bibliotecas de Instâncias de Contêiner do Azure para .NET
description: Referência para bibliotecas de Instâncias de Contêiner do Azure para .NET
ms.date: 06/11/2018
ms.topic: reference
ms.service: container-instances
ms.openlocfilehash: 8642fc654546edde81aeaa520f52b2aff9720e55
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348098"
---
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="3079c-103">Bibliotecas de Instâncias de Contêiner do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="3079c-103">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="3079c-104">Use as bibliotecas de Instâncias de Contêiner do Microsoft Azure para .NET para criar e gerenciar as instâncias de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="3079c-104">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="3079c-105">Saiba mais lendo a [Visão geral das Instâncias de Contêiner do Azure](/azure/container-instances/container-instances-overview).</span><span class="sxs-lookup"><span data-stu-id="3079c-105">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="3079c-106">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="3079c-106">Management library</span></span>

<span data-ttu-id="3079c-107">Use a biblioteca de gerenciamento para criar e gerenciar instâncias de contêiner do Azure no Azure.</span><span class="sxs-lookup"><span data-stu-id="3079c-107">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="3079c-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="3079c-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="3079c-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3079c-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="example-source"></a><span data-ttu-id="3079c-110">Fonte de exemplo</span><span class="sxs-lookup"><span data-stu-id="3079c-110">Example source</span></span>

<span data-ttu-id="3079c-111">Se quiser ver os seguintes exemplos de código em contexto, você pode encontrá-los no repositório do GitHub a seguir:</span><span class="sxs-lookup"><span data-stu-id="3079c-111">If you'd like to see the following code examples in context, you can find them in the following GitHub repository:</span></span>

[<span data-ttu-id="3079c-112">Azure-Samples/aci-docs-sample-dotnet</span><span class="sxs-lookup"><span data-stu-id="3079c-112">Azure-Samples/aci-docs-sample-dotnet</span></span>](https://github.com/Azure-Samples/aci-docs-sample-dotnet)

## <a name="authentication"></a><span data-ttu-id="3079c-113">Autenticação</span><span class="sxs-lookup"><span data-stu-id="3079c-113">Authentication</span></span>

<span data-ttu-id="3079c-114">Uma das maneiras mais fáceis de autenticar clientes de SDK é com a [autenticação baseada em arquivo][sdk-auth].</span><span class="sxs-lookup"><span data-stu-id="3079c-114">One of the easiest ways to authenticate SDK clients is with [file-based authentication][sdk-auth].</span></span> <span data-ttu-id="3079c-115">A autenticação baseada em arquivo analisa um arquivo de credenciais ao criar uma instância do objeto de cliente [IAzure][iazure], que, depois, usa essas credenciais ao autenticar com o Azure.</span><span class="sxs-lookup"><span data-stu-id="3079c-115">File-based authentication parses a credentials file when instantiating the [IAzure][iazure] client object, which then uses those credentials when authenticating with Azure.</span></span> <span data-ttu-id="3079c-116">Para usar a autenticação baseada em arquivo:</span><span class="sxs-lookup"><span data-stu-id="3079c-116">To use file-based authentication:</span></span>

1. <span data-ttu-id="3079c-117">Criar um arquivo de credenciais com a [CLI do Azure](/cli/azure) ou o [Cloud Shell](https://shell.azure.com/):</span><span class="sxs-lookup"><span data-stu-id="3079c-117">Create a credentials file with the [Azure CLI](/cli/azure) or [Cloud Shell](https://shell.azure.com/):</span></span>

   `az ad sp create-for-rbac --sdk-auth > my.azureauth`

   <span data-ttu-id="3079c-118">Se você usar o [Cloud Shell](https://shell.azure.com/) para gerar o arquivo de credenciais, copie o conteúdo em um arquivo local onde seu aplicativo .NET possa acessar.</span><span class="sxs-lookup"><span data-stu-id="3079c-118">If you use the [Cloud Shell](https://shell.azure.com/) to generate the credentials file, copy its contents into a local file that your .NET application can access.</span></span>

2. <span data-ttu-id="3079c-119">Defina a variável de ambiente `AZURE_AUTH_LOCATION` para o caminho completo do arquivo de credenciais gerado.</span><span class="sxs-lookup"><span data-stu-id="3079c-119">Set the `AZURE_AUTH_LOCATION` environment variable to the full path of the generated credentials file.</span></span> <span data-ttu-id="3079c-120">Por exemplo (no shell Bash):</span><span class="sxs-lookup"><span data-stu-id="3079c-120">For example (in the Bash shell):</span></span>

   ```bash
   export AZURE_AUTH_LOCATION=/home/yourusername/my.azureauth
   ```

<span data-ttu-id="3079c-121">Depois de criar o arquivo de credenciais e preencher a variável de ambiente `AZURE_AUTH_LOCATION`, use o método [Azure.Authenticate][iazure-authenticate] para inicializar o objeto de cliente [IAzure][iazure].</span><span class="sxs-lookup"><span data-stu-id="3079c-121">Once you've created the credentials file and populated the `AZURE_AUTH_LOCATION` environment variable, use the [Azure.Authenticate][iazure-authenticate] method to initialize the [IAzure][iazure] client object.</span></span> <span data-ttu-id="3079c-122">O projeto de exemplo obtém primeiro o valor de `AZURE_AUTH_LOCATION` e, em seguida, chama um método que retorna um objeto de cliente `IAzure` inicializado:</span><span class="sxs-lookup"><span data-stu-id="3079c-122">The example project first obtains the `AZURE_AUTH_LOCATION` value, then calls a method that returns an initialized `IAzure` client object:</span></span>

<span data-ttu-id="3079c-123"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span><span class="sxs-lookup"><span data-stu-id="3079c-123"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span></span>

<span data-ttu-id="3079c-124">Esse método do aplicativo de exemplo retorna a instância [IAzure][iazure] inicializada, que é passada como o primeiro parâmetro para todos os outros métodos no exemplo:</span><span class="sxs-lookup"><span data-stu-id="3079c-124">This method from the sample application returns the initialized [IAzure][iazure] instance, which is then passed as the first parameter to all other methods in the sample:</span></span>

<span data-ttu-id="3079c-125"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span><span class="sxs-lookup"><span data-stu-id="3079c-125"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span></span>

<span data-ttu-id="3079c-126">Para obter mais detalhes sobre os métodos de autenticação disponíveis nas bibliotecas de gerenciamento do .NET para Azure, confira [Autenticar em Bibliotecas de Gerenciamento do Azure para .NET][sdk-auth].</span><span class="sxs-lookup"><span data-stu-id="3079c-126">For more details about the available authentication methods in the .NET management libraries for Azure, see [Authentication in Azure Management Libraries for .NET][sdk-auth].</span></span>

## <a name="create-container-group---single-container"></a><span data-ttu-id="3079c-127">Criar grupo de contêineres - contêiner único</span><span class="sxs-lookup"><span data-stu-id="3079c-127">Create container group - single container</span></span>

<span data-ttu-id="3079c-128">Este exemplo cria um grupo de contêineres com um único contêiner.</span><span class="sxs-lookup"><span data-stu-id="3079c-128">This example creates a container group with a single container.</span></span>

<span data-ttu-id="3079c-129"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span><span class="sxs-lookup"><span data-stu-id="3079c-129"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span></span>

## <a name="create-container-group---multiple-containers"></a><span data-ttu-id="3079c-130">Criar grupo de contêineres - vários contêineres</span><span class="sxs-lookup"><span data-stu-id="3079c-130">Create container group - multiple containers</span></span>

<span data-ttu-id="3079c-131">Este exemplo cria um grupo de contêineres com dois contêineres: um contêiner do aplicativo e um secundário.</span><span class="sxs-lookup"><span data-stu-id="3079c-131">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<span data-ttu-id="3079c-132"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span><span class="sxs-lookup"><span data-stu-id="3079c-132"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span></span>

## <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="3079c-133">Criar contêiner assíncrono com a sondagem</span><span class="sxs-lookup"><span data-stu-id="3079c-133">Asynchronous container create with polling</span></span>

<span data-ttu-id="3079c-134">Este exemplo cria um grupo de contêineres com um único contêiner usando o método para criar assíncrono.</span><span class="sxs-lookup"><span data-stu-id="3079c-134">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="3079c-135">Então, ele pesquisa o Azure para obter o grupo de contêineres e gera o status do grupo de contêineres até que seu estado seja "Em execução".</span><span class="sxs-lookup"><span data-stu-id="3079c-135">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<span data-ttu-id="3079c-136"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span><span class="sxs-lookup"><span data-stu-id="3079c-136"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span></span>

## <a name="create-task-based-container-group"></a><span data-ttu-id="3079c-137">Criar grupo de contêineres baseado em tarefas</span><span class="sxs-lookup"><span data-stu-id="3079c-137">Create task-based container group</span></span>

<span data-ttu-id="3079c-138">Este exemplo cria um grupo de contêineres com um único contêiner baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="3079c-138">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="3079c-139">O contêiner é configurado com uma [política de reiniciar](/azure/container-instances/container-instances-restart-policy) "Nunca" e uma [linha de comando personalizada](/azure/container-instances/container-instances-restart-policy#command-line-override).</span><span class="sxs-lookup"><span data-stu-id="3079c-139">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="3079c-140">Se você quiser executar um único comando com vários argumentos da linha de comando, por exemplo `echo FOO BAR`, deve fornecê-los como uma matriz de caracteres para o método `WithStartingCommandLines`.</span><span class="sxs-lookup"><span data-stu-id="3079c-140">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="3079c-141">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="3079c-141">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="3079c-142">Se, no entanto, quiser executar vários comandos (potencialmente) vários argumentos, deve executar um shell e passar os comandos em cadeia como um argumento.</span><span class="sxs-lookup"><span data-stu-id="3079c-142">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="3079c-143">Por exemplo, isso executa os comandos `echo` e `tail`:</span><span class="sxs-lookup"><span data-stu-id="3079c-143">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<span data-ttu-id="3079c-144"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span><span class="sxs-lookup"><span data-stu-id="3079c-144"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span></span>

## <a name="list-container-groups"></a><span data-ttu-id="3079c-145">Listar grupos de contêineres</span><span class="sxs-lookup"><span data-stu-id="3079c-145">List container groups</span></span>

<span data-ttu-id="3079c-146">Este exemplo lista os grupos de contêineres em um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="3079c-146">This example lists the container groups in a resource group.</span></span>

<span data-ttu-id="3079c-147"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span><span class="sxs-lookup"><span data-stu-id="3079c-147"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span></span>

## <a name="get-an-existing-container-group"></a><span data-ttu-id="3079c-148">Obter um grupo de contêineres existente</span><span class="sxs-lookup"><span data-stu-id="3079c-148">Get an existing container group</span></span>

<span data-ttu-id="3079c-149">Este exemplo obtém um grupo de contêineres específico que reside em um grupo de recursos, em seguida, imprime algumas de suas propriedades e valores.</span><span class="sxs-lookup"><span data-stu-id="3079c-149">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<span data-ttu-id="3079c-150"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span><span class="sxs-lookup"><span data-stu-id="3079c-150"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span></span>

## <a name="delete-a-container-group"></a><span data-ttu-id="3079c-151">Excluir um grupo de contêineres</span><span class="sxs-lookup"><span data-stu-id="3079c-151">Delete a container group</span></span>

<span data-ttu-id="3079c-152">Este exemplo exclui um grupo de contêineres de um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="3079c-152">This example deletes a container group from a resource group.</span></span>

<span data-ttu-id="3079c-153"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span><span class="sxs-lookup"><span data-stu-id="3079c-153"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span></span>

## <a name="api-reference"></a><span data-ttu-id="3079c-154">Referência de API</span><span class="sxs-lookup"><span data-stu-id="3079c-154">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3079c-155">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="3079c-155">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="3079c-156">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3079c-156">Samples</span></span>

* <span data-ttu-id="3079c-157">O código-fonte para os exemplos anteriores pode ser encontrado no GitHub:</span><span class="sxs-lookup"><span data-stu-id="3079c-157">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="3079c-158">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="3079c-158">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="3079c-159">Mais exemplos de código das Instâncias de Contêiner do Azure:</span><span class="sxs-lookup"><span data-stu-id="3079c-159">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="3079c-160">[Exemplos de Código do Azure][samples]</span><span class="sxs-lookup"><span data-stu-id="3079c-160">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="3079c-161">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3079c-161">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

<!-- LINKS - External -->
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[sdk-auth]: https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md

<!-- LINKS - Internal -->
[DotNetCLI]: /dotnet/core/tools/dotnet-add-package
[PackageManager]: /nuget/tools/package-manager-console
[iazure]: /dotnet/api/microsoft.azure.management.fluent.azure
[iazure-authenticate]: /dotnet/api/microsoft.azure.management.fluent.azure.authenticate
