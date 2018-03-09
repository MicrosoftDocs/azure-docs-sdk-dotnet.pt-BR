---
title: Implantar no Azure por meio do Visual Studio
description: "Este tutorial orientará você durante a criação e implantação de um aplicativo do Microsoft Azure usando o Visual Studio e o .NET."
keywords: ".NET do Azure, SDK, Referência da API .NET do Azure, Biblioteca de classes .NET do Azure"
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.openlocfilehash: d5c34dfc7e649e00e8ef458537f3f76410db61d4
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="deploy-to-azure-from-visual-studio"></a><span data-ttu-id="adde4-104">Implantar no Azure por meio do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="adde4-104">Deploy to Azure from Visual Studio</span></span>

<span data-ttu-id="adde4-105">Este tutorial orientará você durante a criação e implantação de um aplicativo do Microsoft Azure usando o Visual Studio e o .NET.</span><span class="sxs-lookup"><span data-stu-id="adde4-105">This tutorial will walk you through building and deploying a Microsoft Azure application using Visual Studio and .NET.</span></span>  <span data-ttu-id="adde4-106">Quando terminar, você terá um aplicativo baseado na Web de tarefas pendentes criado em ASP.NET MVC Core, hospedado como aplicativo Web do Azure e que usa o Azure CosmosDB para armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="adde4-106">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure CosmosDB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="adde4-107">pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="adde4-107">Prerequisites</span></span>

* [<span data-ttu-id="adde4-108">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="adde4-108">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* <span data-ttu-id="adde4-109">Uma [assinatura do Microsoft Azure](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="adde4-109">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>

## <a name="create-a-cosmosdb-account"></a><span data-ttu-id="adde4-110">Criar uma conta do CosmosDB</span><span class="sxs-lookup"><span data-stu-id="adde4-110">Create a CosmosDB account</span></span>

<span data-ttu-id="adde4-111">O CosmosDB é usado para armazenamento de dados neste tutorial e, portanto, você precisará criar uma conta.</span><span class="sxs-lookup"><span data-stu-id="adde4-111">CosmosDB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="adde4-112">Execute esse script localmente ou no Cloud Shell para criar uma conta da API DocumentDB do Azure CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="adde4-112">Run this script locally or in the Cloud Shell to create an Azure CosmosDB DocumentDB API account.</span></span>  <span data-ttu-id="adde4-113">Clique no botão **Experimente** no bloco de código abaixo para iniciar o [Azure Cloud Shell](/azure/cloud-shell/) e copiar/colar o bloco de script no shell.</span><span class="sxs-lookup"><span data-stu-id="adde4-113">Click the **Try it** button on the code block below to launch the [Azure Cloud Shell](/azure/cloud-shell/) and copy/paste the script block into the shell.</span></span>

```azurecli-interactive
# Create the DotNetAzureTutorial resource group
az group create --name DotNetAzureTutorial --location EastUS

# Generate a unique name for the account
let randomNum=$RANDOM*$RANDOM
cosmosdbname=dotnettutorial$randomNum

# Create the CosmosDB account
az cosmosdb create --name $cosmosdbname --resource-group DotNetAzureTutorial

# Retrieve the endpoint and key (you'll need these later)
cosmosEndpoint=$(az cosmosdb show -n $cosmosdbname -g DotNetAzureTutorial --query [documentEndpoint] -o tsv)
cosmosAuthKey=$(az cosmosdb list-keys -n $cosmosdbname -g DotNetAzureTutorial --query [primaryMasterKey] -o tsv)
printf "\n\nauthKey: $cosmosAuthKey\nendpoint: $cosmosEndpoint\n\n"

# Done!

```

<span data-ttu-id="adde4-114">Anote o **authKey** e o **ponto de extremidade** exibidos</span><span class="sxs-lookup"><span data-stu-id="adde4-114">Make a note of the displayed **authKey** and **endpoint**</span></span> 

## <a name="downloading-and-running-the-application"></a><span data-ttu-id="adde4-115">Baixando e executando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="adde4-115">Downloading and running the application</span></span>

<span data-ttu-id="adde4-116">Vamos obter o código de exemplo para este passo a passo e associá-lo à conta do CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="adde4-116">Let's get the sample code for this walkthrough and hook it up to your CosmosDB account.</span></span>

1. <span data-ttu-id="adde4-117">Baixe o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="adde4-117">Download the sample code.</span></span>  <span data-ttu-id="adde4-118">Você pode [obtê-lo no GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) ou, se tiver o [cliente de linha de comando git](https://git-scm.com/), cloná-lo em seu computador local com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="adde4-118">You can [get it from GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), or if you have the [git command line client](https://git-scm.com/), clone it to your local machine with the following command:</span></span>

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. <span data-ttu-id="adde4-119">Abra **todo.csproj** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="adde4-119">Open **todo.csproj** in Visual Studio.</span></span>

3. <span data-ttu-id="adde4-120">Abra **appSettings.json** no projeto Web.</span><span class="sxs-lookup"><span data-stu-id="adde4-120">Open **appsettings.json** in the web project.</span></span>  <span data-ttu-id="adde4-121">Procure as seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="adde4-121">Look for the following lines:</span></span>

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    <span data-ttu-id="adde4-122">Substitua **AUTHKEYVALUE** e **ENDPOINTVALUE** pelos valores anotados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="adde4-122">Replace **AUTHKEYVALUE** and **ENDPOINTVALUE** with the values you noted earlier.</span></span>

4. <span data-ttu-id="adde4-123">Pressione **F5** para restaurar os pacotes NuGet do projeto, compilá-lo e executá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="adde4-123">Press **F5** to restore the project's NuGet packages, build the project, and run it locally.</span></span>

<span data-ttu-id="adde4-124">O aplicativo Web deve ser executado localmente em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="adde4-124">The web application should run locally in your browser.</span></span>  <span data-ttu-id="adde4-125">Você pode adicionar novos itens à lista de tarefas pendentes clicando em **Criar Novo**.</span><span class="sxs-lookup"><span data-stu-id="adde4-125">You can add new items to the to-do list by clicking **Create New**.</span></span>  <span data-ttu-id="adde4-126">Observe que os dados que você insere no aplicativo estão sendo armazenados em sua conta do CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="adde4-126">Note the data you enter in the application is being stored in your CosmosDB account.</span></span>  <span data-ttu-id="adde4-127">Você pode [exibir seus dados no portal do Azure](/azure/documentdb/documentdb-view-json-document-explorer).</span><span class="sxs-lookup"><span data-stu-id="adde4-127">You can [view your data in the Azure portal](/azure/documentdb/documentdb-view-json-document-explorer).</span></span>

## <a name="deploying-the-application-as-an-azure-web-app"></a><span data-ttu-id="adde4-128">Implantar o aplicativo como um aplicativo Web do Azure</span><span class="sxs-lookup"><span data-stu-id="adde4-128">Deploying the application as an Azure Web App</span></span>

<span data-ttu-id="adde4-129">Você construiu um aplicativo que usa serviços do Azure, como o DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="adde4-129">You've successfully built an application that uses Azure services like DocumentDB.</span></span>  <span data-ttu-id="adde4-130">Em seguida, vamos implantar nosso aplicativo Web na nuvem.</span><span class="sxs-lookup"><span data-stu-id="adde4-130">Next, we'll deploy our web application to the cloud.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="adde4-131">Verifique se você está conectado ao Visual Studio com a mesma conta associada à assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="adde4-131">Be sure you're signed into Visual Studio with the same account your Azure subscription is associated with.</span></span>

1. <span data-ttu-id="adde4-132">No Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no nome do projeto e selecione **Publicar...**</span><span class="sxs-lookup"><span data-stu-id="adde4-132">In Visual Studio Solution Explorer, right-click on the project name and select **Publish...**</span></span>

2. <span data-ttu-id="adde4-133">Na caixa de diálogo Publicar, selecione **Serviço de Aplicativo do Microsoft Azure**, selecione **Criar Novo** e clique em **Publicar**</span><span class="sxs-lookup"><span data-stu-id="adde4-133">Using the Publish dialog, select **Microsoft Azure App Service**, select **Create New**, and then click **Publish**</span></span>

3. <span data-ttu-id="adde4-134">Preencha o diálogo Criar Serviço de Aplicativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="adde4-134">Complete the Create App Service dialog as follows:</span></span>

    * <span data-ttu-id="adde4-135">Insira um **nome de aplicativo Web** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="adde4-135">Enter a unique **Web App Name**.</span></span>  <span data-ttu-id="adde4-136">Ele fará parte da URL para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="adde4-136">This will be part of the URL for your app.</span></span>
    * <span data-ttu-id="adde4-137">Selecione a **assinatura** do Azure em que você está implantando.</span><span class="sxs-lookup"><span data-stu-id="adde4-137">Select the Azure **Subscription** you're deploying to.</span></span>  <span data-ttu-id="adde4-138">Use a mesma assinatura com a qual você se conectou ao Cloud Shell anteriormente.</span><span class="sxs-lookup"><span data-stu-id="adde4-138">Use same subscription with which you were logged into Cloud Shell earlier.</span></span>
    * <span data-ttu-id="adde4-139">Selecione *DotNetAzureTutorial* em **grupo de recursos** para seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="adde4-139">Select *DotNetAzureTutorial* for the **Resource Group** for your web application.</span></span>
    * <span data-ttu-id="adde4-140">Selecione ou crie um **Plano do Serviço de Aplicativo** para determinar o preço do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="adde4-140">Select or create an **App Service Plan** to determine the pricing your your application.</span></span>  <span data-ttu-id="adde4-141">Veja aqui [mais informações sobre Planos de Serviço de Aplicativo](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="adde4-141">Here's [more information about App Service Plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

4. <span data-ttu-id="adde4-142">Clique em **Criar** para implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="adde4-142">Click **Create** to deploy the application.</span></span>  <span data-ttu-id="adde4-143">Quando a implantação for concluída, um navegador será aberto com o aplicativo implantado.</span><span class="sxs-lookup"><span data-stu-id="adde4-143">When deployment is complete, a browser will open with your deployed application.</span></span>

![O aplicativo concluído](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="adde4-145">Limpar</span><span class="sxs-lookup"><span data-stu-id="adde4-145">Clean up</span></span>

<span data-ttu-id="adde4-146">Ao terminar de testar o aplicativo e inspecionar o código e os recursos, você poderá excluir o aplicativo Web e a conta do CosmosDB excluindo o grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="adde4-146">When you're done testing the app and inspecting the code and resources, you can delete the Web App and CosmosDB account by deleting the resource group.</span></span> <span data-ttu-id="adde4-147">no Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="adde4-147">in the Cloud Shell.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="adde4-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="adde4-148">Next steps</span></span>

* [<span data-ttu-id="adde4-149">Usar o Azure Active Directory para autenticação em um aplicativo Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="adde4-149">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="adde4-150">Criar um aplicativo Web do Azure usando o Banco de Dados SQL do Azure</span><span class="sxs-lookup"><span data-stu-id="adde4-150">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="adde4-151">Experimentar um aplicativo .NET de exemplo com o Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="adde4-151">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


