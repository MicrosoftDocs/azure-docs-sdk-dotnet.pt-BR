---
title: Implantar no Azure por meio do Visual Studio
description: Este tutorial orientará você durante a criação e implantação de um aplicativo do Microsoft Azure usando o Visual Studio e o .NET.
keywords: .NET do Azure, SDK, Referência da API .NET do Azure, Biblioteca de classes .NET do Azure
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.openlocfilehash: 87f65d8b8b1b1a5184b9d71770c08be472c7e498
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2018
---
# <a name="deploy-to-azure-from-visual-studio"></a><span data-ttu-id="3edcf-104">Implantar no Azure por meio do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3edcf-104">Deploy to Azure from Visual Studio</span></span>

<span data-ttu-id="3edcf-105">Este tutorial orientará você durante a criação e implantação de um aplicativo do Microsoft Azure usando o Visual Studio e o .NET.</span><span class="sxs-lookup"><span data-stu-id="3edcf-105">This tutorial will walk you through building and deploying a Microsoft Azure application using Visual Studio and .NET.</span></span>  <span data-ttu-id="3edcf-106">Quando terminar, você terá um aplicativo de tarefas pendentes baseado na Web criado em ASP.NET MVC Core, hospedado como aplicativo Web do Azure e que usa o Azure Cosmos DB para armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="3edcf-106">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure Cosmos DB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3edcf-107">pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3edcf-107">Prerequisites</span></span>

* [<span data-ttu-id="3edcf-108">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3edcf-108">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* <span data-ttu-id="3edcf-109">Uma [assinatura do Microsoft Azure](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="3edcf-109">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>

## <a name="create-an-azure-cosmos-db-account"></a><span data-ttu-id="3edcf-110">Criar uma conta do Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="3edcf-110">Create an Azure Cosmos DB account</span></span>

<span data-ttu-id="3edcf-111">O Azure Cosmos DB é usado para o armazenamento de dados neste tutorial, portanto, você precisará criar uma conta.</span><span class="sxs-lookup"><span data-stu-id="3edcf-111">Azure Cosmos DB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="3edcf-112">Execute esse script localmente ou no Cloud Shell para criar uma conta da API do SQL do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3edcf-112">Run this script locally or in the Cloud Shell to create an Azure Cosmos DB SQL API account.</span></span>  <span data-ttu-id="3edcf-113">Clique no botão **Experimente** no bloco de código abaixo para iniciar o [Azure Cloud Shell](/azure/cloud-shell/) e copiar/colar o bloco de script no shell.</span><span class="sxs-lookup"><span data-stu-id="3edcf-113">Click the **Try it** button on the code block below to launch the [Azure Cloud Shell](/azure/cloud-shell/) and copy/paste the script block into the shell.</span></span>

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
printf "\n\nauthKey: $cosmosAuthKey\nendpoint: $cosmosEndpoint\n\n"

# Done!

```

<span data-ttu-id="3edcf-114">Anote o **authKey** e o **ponto de extremidade** exibidos</span><span class="sxs-lookup"><span data-stu-id="3edcf-114">Make a note of the displayed **authKey** and **endpoint**</span></span> 

## <a name="downloading-and-running-the-application"></a><span data-ttu-id="3edcf-115">Baixando e executando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3edcf-115">Downloading and running the application</span></span>

<span data-ttu-id="3edcf-116">Vamos obter o código de exemplo para este passo a passo e associá-lo à conta do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3edcf-116">Let's get the sample code for this walkthrough and hook it up to your Azure Cosmos DB account.</span></span>

1. <span data-ttu-id="3edcf-117">Baixe o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-117">Download the sample code.</span></span>  <span data-ttu-id="3edcf-118">Você pode [obtê-lo no GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) ou, se tiver o [cliente de linha de comando git](https://git-scm.com/), cloná-lo em seu computador local com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3edcf-118">You can [get it from GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), or if you have the [git command line client](https://git-scm.com/), clone it to your local machine with the following command:</span></span>

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. <span data-ttu-id="3edcf-119">Abra **todo.csproj** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3edcf-119">Open **todo.csproj** in Visual Studio.</span></span>

3. <span data-ttu-id="3edcf-120">Abra **appSettings.json** no projeto Web.</span><span class="sxs-lookup"><span data-stu-id="3edcf-120">Open **appsettings.json** in the web project.</span></span>  <span data-ttu-id="3edcf-121">Procure as seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="3edcf-121">Look for the following lines:</span></span>

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    <span data-ttu-id="3edcf-122">Substitua **AUTHKEYVALUE** e **ENDPOINTVALUE** pelos valores anotados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3edcf-122">Replace **AUTHKEYVALUE** and **ENDPOINTVALUE** with the values you noted earlier.</span></span>

4. <span data-ttu-id="3edcf-123">Pressione **F5** para restaurar os pacotes NuGet do projeto, compilá-lo e executá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="3edcf-123">Press **F5** to restore the project's NuGet packages, build the project, and run it locally.</span></span>

<span data-ttu-id="3edcf-124">O aplicativo Web deve ser executado localmente em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="3edcf-124">The web application should run locally in your browser.</span></span>  <span data-ttu-id="3edcf-125">Você pode adicionar novos itens à lista de tarefas pendentes clicando em **Criar Novo**.</span><span class="sxs-lookup"><span data-stu-id="3edcf-125">You can add new items to the to-do list by clicking **Create New**.</span></span>  <span data-ttu-id="3edcf-126">Observe que os dados inseridos no aplicativo estão sendo armazenados em sua conta do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3edcf-126">Note the data you enter in the application is being stored in your Azure Cosmos DB account.</span></span>  <span data-ttu-id="3edcf-127">Você pode exibir os dados no [Portal do Azure](https://portal.azure.com) selecionando o Azure Cosmos DB no menu à esquerda, selecionando a sua conta e, depois, o **Data Explorer**.</span><span class="sxs-lookup"><span data-stu-id="3edcf-127">You can view your data in the [Azure portal](https://portal.azure.com) by selecting Azure Cosmos DB from the left menu, selecting your account, and then selecting **Data Explorer**.</span></span>

## <a name="deploying-the-application-as-an-azure-web-app"></a><span data-ttu-id="3edcf-128">Implantar o aplicativo como um aplicativo Web do Azure</span><span class="sxs-lookup"><span data-stu-id="3edcf-128">Deploying the application as an Azure Web App</span></span>

<span data-ttu-id="3edcf-129">Você construiu com êxito um aplicativo que usa serviços do Azure, como o Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3edcf-129">You've successfully built an application that uses Azure services like Azure Cosmos DB.</span></span>  <span data-ttu-id="3edcf-130">Em seguida, vamos implantar nosso aplicativo Web na nuvem.</span><span class="sxs-lookup"><span data-stu-id="3edcf-130">Next, we'll deploy our web application to the cloud.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3edcf-131">Verifique se você está conectado ao Visual Studio com a mesma conta associada à assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="3edcf-131">Be sure you're signed into Visual Studio with the same account your Azure subscription is associated with.</span></span>

1. <span data-ttu-id="3edcf-132">No Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no nome do projeto e selecione **Publicar...**</span><span class="sxs-lookup"><span data-stu-id="3edcf-132">In Visual Studio Solution Explorer, right-click on the project name and select **Publish...**</span></span>

2. <span data-ttu-id="3edcf-133">Na caixa de diálogo Publicar, selecione **Serviço de Aplicativo do Microsoft Azure**, selecione **Criar Novo** e clique em **Publicar**</span><span class="sxs-lookup"><span data-stu-id="3edcf-133">Using the Publish dialog, select **Microsoft Azure App Service**, select **Create New**, and then click **Publish**</span></span>

3. <span data-ttu-id="3edcf-134">Preencha o diálogo Criar Serviço de Aplicativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3edcf-134">Complete the Create App Service dialog as follows:</span></span>

    * <span data-ttu-id="3edcf-135">Insira um **nome de aplicativo Web** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-135">Enter a unique **Web App Name**.</span></span>  <span data-ttu-id="3edcf-136">Ele fará parte da URL para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-136">This will be part of the URL for your app.</span></span>
    * <span data-ttu-id="3edcf-137">Selecione a **assinatura** do Azure em que você está implantando.</span><span class="sxs-lookup"><span data-stu-id="3edcf-137">Select the Azure **Subscription** you're deploying to.</span></span>  <span data-ttu-id="3edcf-138">Use a mesma assinatura com a qual você se conectou ao Cloud Shell anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3edcf-138">Use same subscription with which you were logged into Cloud Shell earlier.</span></span>
    * <span data-ttu-id="3edcf-139">Selecione *DotNetAzureTutorial* em **grupo de recursos** para seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="3edcf-139">Select *DotNetAzureTutorial* for the **Resource Group** for your web application.</span></span>
    * <span data-ttu-id="3edcf-140">Selecione ou crie um **Plano do Serviço de Aplicativo** para determinar o preço do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-140">Select or create an **App Service Plan** to determine the pricing your your application.</span></span>  <span data-ttu-id="3edcf-141">Veja aqui [mais informações sobre Planos de Serviço de Aplicativo](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="3edcf-141">Here's [more information about App Service Plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

4. <span data-ttu-id="3edcf-142">Clique em **Criar** para implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-142">Click **Create** to deploy the application.</span></span>  <span data-ttu-id="3edcf-143">Quando a implantação for concluída, um navegador será aberto com o aplicativo implantado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-143">When deployment is complete, a browser will open with your deployed application.</span></span>

![O aplicativo concluído](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="3edcf-145">Limpar</span><span class="sxs-lookup"><span data-stu-id="3edcf-145">Clean up</span></span>

<span data-ttu-id="3edcf-146">Ao terminar de testar o aplicativo e inspecionar o código e os recursos, é possível excluir o aplicativo Web e a conta do Azure Cosmos DB excluindo o grupo de recursos no Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="3edcf-146">When you're done testing the app and inspecting the code and resources, you can delete the Web App and Azure Cosmos DB account by deleting the resource group in the Cloud Shell.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="3edcf-147">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3edcf-147">Next steps</span></span>

* [<span data-ttu-id="3edcf-148">Usar o Azure Active Directory para autenticação em um aplicativo Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3edcf-148">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="3edcf-149">Criar um aplicativo Web do Azure usando o Banco de Dados SQL do Azure</span><span class="sxs-lookup"><span data-stu-id="3edcf-149">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="3edcf-150">Experimentar um aplicativo .NET de exemplo com o Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="3edcf-150">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


