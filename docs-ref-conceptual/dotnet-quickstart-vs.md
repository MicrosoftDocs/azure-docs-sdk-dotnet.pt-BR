---
title: .NET para desenvolvedores do Azure
description: .NET para desenvolvedores do Azure
keywords: ".NET do Azure, SDK, Referência da API .NET do Azure, Biblioteca de classes .NET do Azure"
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.assetid: 
ms.openlocfilehash: 1defed888972ae2f9d60d57bc34c518df9b5867c
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="get-started-with-net-for-azure-developers"></a>Introdução ao .NET para desenvolvedores do Azure

Este tutorial orientará você durante a criação e implantação de um aplicativo do Microsoft Azure usando o Visual Studio e o .NET.  Quando terminar, você terá um aplicativo baseado na Web de tarefas pendentes criado em ASP.NET MVC Core, hospedado como aplicativo Web do Azure e que usa o Azure CosmosDB para armazenamento de dados.

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017](https://www.visualstudio.com/downloads/)
* Uma [assinatura do Microsoft Azure](https://azure.microsoft.com/free/)

## <a name="create-a-cosmosdb-account"></a>Criar uma conta do CosmosDB

O CosmosDB é usado para armazenamento de dados neste tutorial e, portanto, você precisará criar uma conta.  Execute esse script localmente ou no Cloud Shell para criar uma conta da API DocumentDB do Azure CosmosDB.  Clique no botão **Experimente** no bloco de código abaixo para iniciar o [Azure Cloud Shell](/azure/cloud-shell/) e copiar/colar o bloco de script no shell.

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

Anote o **authKey** e o **ponto de extremidade** exibidos 

## <a name="downloading-and-running-the-application"></a>Baixando e executando o aplicativo

Vamos obter o código de exemplo para este passo a passo e associá-lo à conta do CosmosDB.

1. Baixe o código de exemplo.  Você pode [obtê-lo no GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) ou, se tiver o [cliente de linha de comando git](https://git-scm.com/), cloná-lo em seu computador local com o seguinte comando:

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. Abra **todo.csproj** no Visual Studio.

3. Abra **appSettings.json** no projeto Web.  Procure as seguintes linhas:

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    Substitua **AUTHKEYVALUE** e **ENDPOINTVALUE** pelos valores anotados anteriormente.

4. Pressione **F5** para restaurar os pacotes NuGet do projeto, compilá-lo e executá-lo localmente.

O aplicativo Web deve ser executado localmente em seu navegador.  Você pode adicionar novos itens à lista de tarefas pendentes clicando em **Criar Novo**.  Observe que os dados que você insere no aplicativo estão sendo armazenados em sua conta do CosmosDB.  Você pode [exibir seus dados no portal do Azure](https://docs.microsoft.com/en-us/azure/documentdb/documentdb-view-json-document-explorer).

## <a name="deploying-the-application-as-an-azure-web-app"></a>Implantar o aplicativo como um aplicativo Web do Azure

Você construiu um aplicativo que usa serviços do Azure, como o DocumentDB.  Em seguida, vamos implantar nosso aplicativo Web na nuvem.

> [!IMPORTANT]
> Verifique se você está conectado ao Visual Studio com a mesma conta associada à assinatura do Azure.

1. No Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no nome do projeto e selecione **Publicar...**

2. Na caixa de diálogo Publicar, selecione **Serviço de Aplicativo do Microsoft Azure**, selecione **Criar Novo** e clique em **Publicar**

3. Preencha o diálogo Criar Serviço de Aplicativo da seguinte maneira:

    * Insira um **nome de aplicativo Web** exclusivo.  Ele fará parte da URL para seu aplicativo.
    * Selecione a **assinatura** do Azure em que você está implantando.  Use a mesma assinatura com a qual você se conectou ao Cloud Shell anteriormente.
    * Selecione *DotNetAzureTutorial* em **grupo de recursos** para seu aplicativo Web.
    * Selecione ou crie um **Plano do Serviço de Aplicativo** para determinar o preço do seu aplicativo.  Veja aqui [mais informações sobre Planos de Serviço de Aplicativo](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

4. Clique em **Criar** para implantar o aplicativo.  Quando a implantação for concluída, um navegador será aberto com o aplicativo implantado.

![O aplicativo concluído](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a>Limpar

Ao terminar de testar o aplicativo e inspecionar o código e os recursos, você poderá excluir o aplicativo Web e a conta do CosmosDB excluindo o grupo de recursos. no Cloud Shell.

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a>Próximas etapas

* [Usar o Azure Active Directory para autenticação em um aplicativo Web ASP.NET](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [Criar um aplicativo Web do Azure usando o Banco de Dados SQL do Azure](/azure/app-service-web/web-sites-dotnet-get-started)
* [Experimentar um aplicativo .NET de exemplo com o Armazenamento do Azure](/azure/storage/storage-samples-dotnet)


