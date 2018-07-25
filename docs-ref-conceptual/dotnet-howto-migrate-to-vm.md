---
title: Migrar um aplicativo Web ASP.NET para uma Máquina Virtual do Azure
description: Saiba como migrar um aplicativo Web ASP.NET do local para uma Máquina Virtual do Azure.
keywords: .NET do Azure, ASP.NET, VM, máquina virtual, migrar, migração
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: virtual-machines
ms.custom: devcenter
ms.openlocfilehash: 53e899ba3cd2ff265a2068e1b7eee5baa4520879
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065336"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Migrar um aplicativo Web ASP.NET para uma Máquina Virtual do Azure

Este documento fornece uma visão geral de como migrar um aplicativo Web ASP.NET do local para uma Máquina Virtual do Azure.

## <a name="quickstart"></a>Início rápido

Saiba como criar uma máquina virtual e publicar o aplicativo nela: [Publicar em uma VM do Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>Introdução

Esses tutoriais demonstram as etapas para criar (ou migrar) uma máquina virtual, publicar seu aplicativo Web para ela e outras tarefas que podem ser necessárias para dar suporte ao seu aplicativo no Azure.

- Crie uma máquina virtual para seu aplicativo ASP.NET no Azure usando uma das duas opções a seguir:
    - [Criar uma nova máquina virtual para Aplicativos ASP.NET](https://go.microsoft.com/fwlink/?linkid=863237)
    - [Migrar uma máquina virtual local existente](https://docs.microsoft.com/azure/site-recovery/tutorial-migrate-on-premises-to-azure)
- [Publicar seu aplicativo usando o Visual Studio](https://go.microsoft.com/fwlink/?linkid=863240)
- [Criar uma rede virtual segura para suas VMs](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [Criar um pipeline CI/CD para seu aplicativo](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [Mover para um conjunto de dimensionamento da VM para ter alta disponibilidade e escalabilidade](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>Considerações

### <a name="benefits"></a>Benefícios

As máquinas virtuais oferecem o caminho mais fácil para migrar um aplicativo do local para a nuvem.  Elas permitem replicar o mesmo ambiente que seu aplicativo usa no local e eliminam a necessidade de manter seus próprios data centers.  Os Conjuntos de Dimensionamento da Máquina Virtual fornecem alta disponibilidade e escalabilidade para os aplicativos executados em Máquinas Virtuais.

### <a name="virtual-machine-size"></a>Tamanho da Máquina Virtual

Escolha o tamanho da máquina virtual e o tipo mais otimizados para sua carga de trabalho.  Confira os [tamanhos das máquinas virtuais do Windows no Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).

### <a name="maintenance"></a>Manutenção 

Assim como uma máquina local, você é responsável por manter e atualizar a máquina virtual<sup>& #42;</sup>.  Se seu aplicativo puder ser executado em um ambiente PaaS (Plataforma como Serviço), como o [Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service/), ou em um [contêiner](https://docs.microsoft.com/azure/app-service/containers/), isso eliminará a necessidade.

*<sup>&#42;</sup>[As atualizações automáticas do SO para os conjuntos de dimensionamento da máquina virtual](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) estão disponíveis atualmente como um serviço de Visualização.*

### <a name="virtual-networks"></a>Redes Virtuais

As Redes Virtuais do Azure permitem:
- compilar uma infraestrutura híbrida que você controla
- trazer seus próprios endereços IP e servidores DNS
- criar um ambiente isolado e altamente seguro para seus aplicativos
- conectar a VM à sua rede local usando uma das várias [opções de conectividade](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)
- integrar sua máquina virtual na rede local usando o [ExpressRoute](https://azure.microsoft.com/services/expressroute/)

Para começar, confira a [documentação da Rede Virtual](https://docs.microsoft.com/azure/virtual-network/)

### <a name="active-directory"></a>Active Directory
Muitos aplicativos usam o Active Directory para a autenticação e o gerenciamento das identidades.  
- O Azure AD Connect permite integrar seus diretórios locais no Azure Active Directory.  Para começar, confira [Integrar seus diretórios locais no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).  
- Como alternativa, o [ExpressRoute](https://azure.microsoft.com/services/expressroute/) permite que seu aplicativo acesse o Active Directory local.

### <a name="sql-databases"></a>BANCOS DE DADOS SQL

Se seu aplicativo estiver usando um banco de dados local, o aplicativo não conseguirá comunicar-se com ele por padrão. Você pode:
- Configure uma rede híbrida que permita ao seu aplicativo acessar o banco de dados em execução no local.  
- Migre seu banco de dados para o Azure.  Confira [Migrar seu banco de dados SQL Server para o Azure](dotnet-howto-migrate-sql.md) para obter mais informações.

### <a name="high-availability-and-scalability"></a>Alta disponibilidade e escalabilidade

#### <a name="virtual-machine-scale-sets"></a>Conjuntos de Dimensionamento de Máquinas Virtuais
Se você quiser verificar se seu aplicativo tem alta disponibilidade e pode ser dimensionado, migre sua imagem da VM para um conjunto de dimensionamento da máquina virtual para melhorar a disponibilidade e a escalabilidade do aplicativo.  Os Conjuntos de Dimensionamento de VM fornecem a capacidade de usar uma VM existente que você já configurou ou definem um pipeline de compilação para criar uma imagem com seu aplicativo.  

Para começar, confira [Implantar seu aplicativo nos conjuntos de dimensionamento da máquina virtual](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).

#### <a name="centralized-logging"></a>Log Centralizado
Ao executar seu aplicativo em várias instâncias, considere armazenar os logs em um local centralizado, como o [Armazenamento do Azure](https://docs.microsoft.com/azure/storage/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Migrar um banco de dados SQL Server para o Azure](dotnet-howto-migrate-sql.md)