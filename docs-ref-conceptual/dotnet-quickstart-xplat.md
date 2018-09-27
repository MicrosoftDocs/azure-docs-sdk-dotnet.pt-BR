---
title: Implantar no Azure a partir da linha de comando com o .NET Core
description: Este artigo descreve como implantar um aplicativo ASP.NET Core a um Serviço de Aplicativo do Azure usando as ferramentas de linha de comando.
ms.date: 06/20/2017
ms.openlocfilehash: a29f5474dcfedc6f8d044f09ad4d54c5be6a371f
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190489"
---
# <a name="deploy-to-azure-from-the-command-line-with-net-core"></a><span data-ttu-id="c73e4-103">Implantar no Azure a partir da linha de comando com o .NET Core</span><span class="sxs-lookup"><span data-stu-id="c73e4-103">Deploy to Azure from the command line with .NET Core</span></span>

<span data-ttu-id="c73e4-104">Este tutorial orientará você durante a criação e implantação de um aplicativo do Microsoft Azure usando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c73e4-104">This tutorial will walk you through building and deploying a Microsoft Azure application using .NET Core.</span></span>  <span data-ttu-id="c73e4-105">Quando terminar, você terá um aplicativo de tarefas pendentes baseado na Web criado em ASP.NET MVC Core, hospedado como aplicativo Web do Azure e que usa o Azure Cosmos DB para armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="c73e4-105">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure Cosmos DB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c73e4-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c73e4-106">Prerequisites</span></span>

* <span data-ttu-id="c73e4-107">Uma [assinatura do Microsoft Azure](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="c73e4-107">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>
* <span data-ttu-id="c73e4-108">[.NET Core](https://www.microsoft.com/net/download/core) (opcional)</span><span class="sxs-lookup"><span data-stu-id="c73e4-108">[.NET Core](https://www.microsoft.com/net/download/core) (optional)</span></span>
* <span data-ttu-id="c73e4-109">[CLI do Azure 2.0 do Azure](/cli/azure/install-az-cli2) (opcional)</span><span class="sxs-lookup"><span data-stu-id="c73e4-109">[Azure CLI 2.0](/cli/azure/install-az-cli2) (optional)</span></span>
* <span data-ttu-id="c73e4-110">Cliente de linha de comando [Git](https://www.git-scm.com/) (opcional)</span><span class="sxs-lookup"><span data-stu-id="c73e4-110">[Git](https://www.git-scm.com/) command line client (optional)</span></span>

<span data-ttu-id="c73e4-111">O [Azure Cloud Shell](/azure/cloud-shell/) tem todos os pré-requisitos opcionais para este tutorial pré-instalados.</span><span class="sxs-lookup"><span data-stu-id="c73e4-111">The [Azure Cloud Shell](/azure/cloud-shell/) has all of the optional prerequisites for this tutorial preinstalled.</span></span>  <span data-ttu-id="c73e4-112">Você só precisa instalar os componentes opcionais acima se deseja executar o tutorial localmente.</span><span class="sxs-lookup"><span data-stu-id="c73e4-112">You only need to install the optional components above if you wish to run the tutorial locally.</span></span>  <span data-ttu-id="c73e4-113">Para iniciar rapidamente o Cloud Shell, clique no botão **Experimente** no canto superior direito de um dos blocos de código abaixo.</span><span class="sxs-lookup"><span data-stu-id="c73e4-113">To quickly launch the Cloud Shell, just click the **Try it** button in the top-right of any of the below code blocks.</span></span>

## <a name="create-an-azure-cosmos-db-account"></a><span data-ttu-id="c73e4-114">Criar uma conta do Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="c73e4-114">Create an Azure Cosmos DB account</span></span>

<span data-ttu-id="c73e4-115">O Azure Cosmos DB é usado para o armazenamento de dados neste tutorial, portanto, você precisará criar uma conta.</span><span class="sxs-lookup"><span data-stu-id="c73e4-115">Azure Cosmos DB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="c73e4-116">Execute esse script localmente ou no Cloud Shell para criar uma conta da API do SQL do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="c73e4-116">Run this script locally or in the Cloud Shell to create an Azure Cosmos DB SQL API account.</span></span>

```azurecli-interactive
# Create the DotNetAzureTutorial resource group
az group create --name DotNetAzureTutorial --location EastUS

# Generate a unique name for the account
let randomNum=$RANDOM*$RANDOM
cosmosdbname=dotnettutorial$randomNum

# Create the Azure Cosmos DB account
az cosmosdb create --name $cosmosdbname --resource-group DotNetAzureTutorial

# Retrieve the endpoint and key (you'll need these later)
cosmosEndpoint=$(az cosmosdb show -n $cosmosdbname -g DotNetAzureTutorial --query [documentEndpoint] -o tsv)
cosmosAuthKey=$(az cosmosdb list-keys -n $cosmosdbname -g DotNetAzureTutorial --query [primaryMasterKey] -o tsv)

```

## <a name="download-and-configure-the-application"></a><span data-ttu-id="c73e4-117">Baixar e configurar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c73e4-117">Download and configure the application</span></span>

<span data-ttu-id="c73e4-118">O aplicativo que você pretende implantar é um [aplicativo de tarefas pendentes simples](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) codificado usando ASP.NET MVC Core e as bibliotecas de cliente do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="c73e4-118">The application you're going to deploy is a [simple to-do app](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) written using ASP.NET MVC Core using the Azure Cosmos DB client libraries.</span></span>  <span data-ttu-id="c73e4-119">Agora você vai obter o código para este tutorial e vai configurá-lo com suas informações do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="c73e4-119">Now you'll get the code for this tutorial and configure it with your Azure Cosmos DB information.</span></span>

```azurecli-interactive
# Get the code from GitHub
git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart

# Change the working directory
cd dotnet-cosmosdb-quickstart

# Replace authKey and endpoint values in appsettings.json
sed -i "s|AUTHKEYVALUE|$cosmosAuthKey|g" appsettings.json
sed -i "s|ENDPOINTVALUE|$cosmosEndpoint|g" appsettings.json

# Now commit your changes to the local Git repository.
git commit -a -m "Modified settings"

```

> [!NOTE]
> <span data-ttu-id="c73e4-120">Se você nunca executou `git commit` nesse ambiente antes, a definição da sua identidade poderá ser solicitada.</span><span class="sxs-lookup"><span data-stu-id="c73e4-120">If you've never run `git commit` in this environment before, you may be prompted to set your identity.</span></span> <span data-ttu-id="c73e4-121">Siga as instruções na tela e execute novamente o comando `git commit`.</span><span class="sxs-lookup"><span data-stu-id="c73e4-121">Follow the on-screen instructions and then re-run the `git commit` command.</span></span>

<span data-ttu-id="c73e4-122">Restaure os pacotes NuGet e compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c73e4-122">Restore the NuGet packages and build the application.</span></span>

```azurecli-interactive
dotnet restore
dotnet build
```

> [!TIP]
> <span data-ttu-id="c73e4-123">Se você estiver usando as ferramentas em seu próprio computador, poderá testar o aplicativo executando `dotnet run` e navegando até o endereço `localhost` exibido.</span><span class="sxs-lookup"><span data-stu-id="c73e4-123">If you are using the tools on your own machine, you can test the application by running `dotnet run` and browsing to the displayed `localhost` address.</span></span>  <span data-ttu-id="c73e4-124">No entanto, não é possível navegar até esse endereço no Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="c73e4-124">You are not able to browse to this address in the Cloud Shell, however.</span></span>  

## <a name="configure-azure-app-service-and-deploy-the-web-app"></a><span data-ttu-id="c73e4-125">Configurar o Serviço de Aplicativo do Azure e implantar o aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="c73e4-125">Configure Azure App Service and deploy the web app</span></span>

<span data-ttu-id="c73e4-126">Você baixou e compilou o aplicativo Web com êxito e está pronto para implantá-lo como um aplicativo Web do Azure.</span><span class="sxs-lookup"><span data-stu-id="c73e4-126">You've successfully downloaded and built the web application, and you're ready to deploy it as an Azure Web App.</span></span>  <span data-ttu-id="c73e4-127">Comece criando o recurso aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="c73e4-127">You'll start by creating the Web App resource.</span></span>

```azurecli-interactive
# Generate a unique Web App name
let randomNum=$RANDOM*$RANDOM
webappname=todoApp$randomNum

# Create an App Service plan.
az appservice plan create --name $webappname --resource-group DotNetAzureTutorial --sku FREE

# Create the Web App
az webapp create --name $webappname --resource-group DotNetAzureTutorial --plan $webappname

```

<span data-ttu-id="c73e4-128">Antes de implantá-lo, você precisa definir as credenciais de implantação no nível da conta.</span><span class="sxs-lookup"><span data-stu-id="c73e4-128">Before you deploy, you need to set the account-level deployment credentials.</span></span>  <span data-ttu-id="c73e4-129">Use o script abaixo incluindo seus próprios valores como nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="c73e4-129">Use the script below, making sure to include your own values for the user name and password.</span></span>

```azurecli-interactive
az webapp deployment user set --user-name <desired user name> --password <desired password>
```

<span data-ttu-id="c73e4-130">Por fim, implante o aplicativo no Azure.</span><span class="sxs-lookup"><span data-stu-id="c73e4-130">Finally, deploy the application to Azure.</span></span>  <span data-ttu-id="c73e4-131">Será solicitada a senha que você criou acima.</span><span class="sxs-lookup"><span data-stu-id="c73e4-131">You will be prompted for the password you created above.</span></span>

```azurecli-interactive
# Get the Git deployment URL
giturl=$(az webapp deployment source config-local-git -n $webappname -g DotNetAzureTutorial --query [url] -o tsv)

# Add the URL as a Git remote repository
git remote add azure $giturl

# Push the local repository to the remote
git push azure master
```

<span data-ttu-id="c73e4-132">O aplicativo será criado remotamente e implantado.</span><span class="sxs-lookup"><span data-stu-id="c73e4-132">The application will be built remotely and deployed.</span></span>  <span data-ttu-id="c73e4-133">Teste o aplicativo navegando até `https://<web app name>.azurewebsites.net`.</span><span class="sxs-lookup"><span data-stu-id="c73e4-133">Test the application by browsing to `https://<web app name>.azurewebsites.net`.</span></span>  <span data-ttu-id="c73e4-134">Para exibir o endereço no console, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c73e4-134">To display the address in the console, use the following:</span></span>

```azurecli-interactive
az webapp show -n $webappname -g DotNetAzureTutorial --query defaultHostName -o tsv
```

<span data-ttu-id="c73e4-135">Você pode adicionar novos itens à lista de tarefas pendentes clicando em **Criar Novo**.</span><span class="sxs-lookup"><span data-stu-id="c73e4-135">You can add new items to the to-do list by clicking **Create New**.</span></span>

![O aplicativo concluído](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="c73e4-137">Limpar</span><span class="sxs-lookup"><span data-stu-id="c73e4-137">Clean up</span></span>

<span data-ttu-id="c73e4-138">Ao terminar de testar o aplicativo e inspecionar o código e os recursos, é possível excluir o aplicativo Web e a conta do Azure Cosmos DB por meio da exclusão do grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="c73e4-138">When you're done testing the app and inspecting the code and resources, you can delete the Web App and Azure Cosmos DB account by deleting the resource group.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="c73e4-139">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c73e4-139">Next steps</span></span>

* [<span data-ttu-id="c73e4-140">Usar o Azure Active Directory para autenticação em um aplicativo Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c73e4-140">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="c73e4-141">Criar um aplicativo Web do Azure usando o Banco de Dados SQL do Azure</span><span class="sxs-lookup"><span data-stu-id="c73e4-141">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="c73e4-142">Experimentar um aplicativo .NET de exemplo com o Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="c73e4-142">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


