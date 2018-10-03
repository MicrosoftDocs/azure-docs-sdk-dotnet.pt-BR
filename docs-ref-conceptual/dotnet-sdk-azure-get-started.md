---
title: Introdução ao Azure e ao .NET
description: Conheça o básico que você precisa saber sobre o Azure e o .NET.
ms.date: 09/19/2018
ms.openlocfilehash: 89fdae6afa5c040127975de43c79d837550a9fbc
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190589"
---
# <a name="get-started-with-azure-and-net"></a>Introdução ao Azure e ao .NET

Este documento fornece uma visão geral dos principais conceitos e serviços do .NET que os desenvolvedores devem conhecer para que possam começar a desenvolver aplicativos usando os serviços do Azure.

## <a name="key-concepts"></a>Principais Conceitos

**Conta do Azure**: sua conta do Azure é a credencial que você usa para entrar nos serviços do Azure, como o [Portal do Azure](https://portal.azure.com) ou o [Cloud Shell](https://shell.azure.com). Se você ainda não tiver uma conta do Azure, poderá [criar uma conta gratuitamente](https://azure.microsoft.com/free/dotnet/).

**Assinatura do Azure**: uma assinatura é o plano de cobrança no qual os recursos do Azure são criados. As assinaturas podem ser individuais ou corporativas, gerenciadas por sua empresa. Sua conta do Azure pode estar associada a várias assinaturas. Nesse caso, verifique se escolheu a assinatura correta ao criar os recursos. Para obter mais informações, confira [Noções básicas sobre contas, assinaturas e cobrança](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

> [!TIP]
> Se você tem uma assinatura do Visual Studio, [tem créditos mensais do Azure aguardando serem ativados](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

**Grupo de recursos**: os grupos de recursos são uma maneira de organizar seus recursos do Azure em grupos para o gerenciamento. Os recursos criados no Azure serão armazenados em um grupo de recursos de forma semelhante a salvar um arquivo em uma pasta no computador.

**Hospedagem**: para executar o código no Azure, ele precisa estar hospedado em um serviço que dê suporte à execução do código fornecido pelo usuário.

**Serviços gerenciados**: o Azure fornece alguns serviços em que você fornece dados ou informações ao Azure e a implementação do Azure executa a ação apropriada. Um exemplo é o Armazenamento de Blobs do Azure, em que você fornece arquivos e o Azure lida com a leitura, a gravação e a persistência.

## <a name="choosing-a-hosting-option"></a>Escolhendo uma opção de hospedagem

A hospedagem no Azure pode ser dividida em três categorias.

* **IaaS (Infraestrutura como Serviço)**: com a IaaS, você provisiona as máquinas virtuais necessárias juntamente com os componentes de rede e armazenamento associados. Em seguida, implanta o software e os aplicativos que deseja nas VMs. Esse modelo é o mais próximo de um ambiente local tradicional, com a exceção de que a Microsoft gerencia a infraestrutura. Você ainda pode gerenciar as VMs individualmente, incluindo o sistema operacional, o software personalizado e as atualizações de segurança.

* **PaaS (Plataforma como Serviço)**: a PaaS fornece um ambiente de hospedagem gerenciado, no qual você implanta o aplicativo sem precisar gerenciar as VMs ou os recursos de rede. Por exemplo, em vez de criar VMs individuais, você especifica uma contagem de instâncias, e o serviço vai provisionar, configurar e gerenciar os recursos necessários. O Serviço de Aplicativo do Azure é um exemplo de um serviço de PaaS.
  
* **FaaS (Funções como Serviço)**: comumente conhecida como computação sem servidor, a FaaS vai ainda além da PaaS em termos de abstrair as questões do ambiente de hospedagem. Em vez de criar instâncias de computação e implantar o código para essas instâncias, você implanta o código e o serviço o executará automaticamente. Não é necessário administrar os recursos de computação. A plataforma dimensiona seu código perfeitamente para qualquer nível necessário a fim de lidar com o tráfego e você paga apenas quando seu código está em execução. O Azure Functions é um serviço FaaS.

Em geral, quanto mais seu aplicativo favorecer os modelos FaaS e PaaS, mais benefícios você terá com a execução na nuvem. Abaixo está um resumo das três opções comuns de hospedagem no Azure e quando escolhê-las.

* [Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is): se você estiver procurando hospedar um aplicativo ou serviço Web, examine o Serviço de Aplicativo primeiro. Para se familiarizar com o Serviço de Aplicativo e os aplicativos ASP.NET, WCF e ASP.NET Core, consulte [Criar um aplicativo Web ASP.NET Core no Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet).

* [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview): o Azure Functions é ótimo para fluxos de trabalho voltados para eventos. Os exemplos incluem respostas a webhooks, processamento de itens em filas ou armazenamento de blobs e temporizadores. Para se familiarizar com o Azure Functions, consulte [Criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

* [Máquinas Virtuais do Azure](https://docs.microsoft.com/azure/virtual-machines/): se o Serviço de Aplicativo não atender às suas necessidades para hospedar um aplicativo existente devido a dependências específicas, as Máquinas Virtuais serão o melhor lugar para começar. Para se familiarizar com as Máquinas Virtuais e o ASP.NET ou o WCF, consulte [Implantar um aplicativo ASP.NET em uma máquina virtual do Azure](https://tutorials.visualstudio.com/aspnet-vm/intro).

> [!TIP]
> Para obter uma lista mais completa de serviços do Azure, consulte [Visão geral das opções de computação do Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-overview#azure-compute-options). Para obter mais informações sobre como escolher um serviço, consulte [Árvore de decisão para os serviços de computação do Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree).

## <a name="choosing-a-data-storage-service"></a>Escolhendo um serviço de armazenamento de dados

O Azure oferece vários serviços para armazenar os dados, dependendo de suas necessidades. Os serviços de dados mais comuns para os desenvolvedores do .NET são:

* [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/): se você está querendo migrar para a nuvem um aplicativo que já usa o SQL Server, o Banco de Dados SQL é, naturalmente, o lugar para começar. Para começar, consulte o [Tutorial: Compilar um aplicativo ASP.NET no Azure com o Banco de Dados SQL](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase).

* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/): o Azure Cosmos DB é um banco de dados moderno projetado para a nuvem. Ao iniciar um novo aplicativo que ainda não tem uma dependência de banco de dados específica, avalie o Azure Cosmos DB. O Cosmos DB é uma ótima escolha para os novos aplicativos Web, móveis, de jogos e IoT, em que o dimensionamento automático, desempenho previsível, tempos de resposta rápidos e capacidade de consultar dados sem esquemas são importantes. Para começar, consulte o [Início Rápido: Compilar um aplicativo Web do .NET com o Azure Cosmos DB usando a API SQL e o portal do Azure](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).

* [Armazenamento de Blobs do Azure](https://docs.microsoft.com/azure/storage/): o Armazenamento de Blobs do Azure é otimizado para armazenar e recuperar grandes objetos binários, como imagens, arquivos e fluxos. Os repositórios de objetos permitem o gerenciamento de quantidades extremamente grandes de dados não estruturados. Para começar, consulte o [Início Rápido: Usar .NET para criar um blob no armazenamento de objetos](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet).

> [!TIP]
> Para obter mais informações, consulte [Escolher o armazenamento de dados correto](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview).

## <a name="diagnosing-problems-in-the-cloud"></a>Diagnosticando problemas na nuvem

Depois de implantar seu aplicativo no Azure, poderá haver situações em que ele funciona no desenvolvimento, mas não no Azure. Abaixo estão duas opções para começar a diagnosticar problemas:

* **Depuração remota no Visual Studio**: a maioria dos serviços de computação do Azure (incluindo os serviços abordados neste documento) dá suporte à depuração remota com o Visual Studio e à aquisição de logs. Para explorar os recursos do Visual Studio com seu aplicativo, abra a janela da ferramenta Cloud Explorer digitando “Cloud Explorer” na barra de ferramentas de início rápido do Visual Studio (no canto superior direito) e localize seu aplicativo na árvore. Para obter detalhes, consulte [Solucionar problemas de um aplicativo Web no Serviço de Aplicativo do Azure usando o Visual Studio](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).

* **Application Insights**: o [Application Insights](https://docs.microsoft.com/azure/application-insights/) é uma solução APM (monitoramento de desempenho do aplicativo) completa que captura automaticamente dados de diagnóstico, telemetria e dados de desempenho nos aplicativos. Para começar a coletar dados de diagnóstico para seu aplicativo, consulte [Iniciar monitoramento de seu Aplicativo Web ASP.NET](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal).

## <a name="next-steps"></a>Próximas etapas

* [Implantar seu primeiro aplicativo Web ASP.NET Core no Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)
* [Saiba mais sobre autenticação nas APIs do Azure para .NET](dotnet-sdk-azure-authenticate.md)
* [Diagnosticar erros nos aplicativos de nuvem](https://blogs.msdn.microsoft.com/webdev/2018/02/07/diagnosing-errors-on-your-cloud-apps)
* Baixe o livro eletrônico gratuito [Guia de Início Rápido do Azure para Desenvolvedores do .NET](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook)
