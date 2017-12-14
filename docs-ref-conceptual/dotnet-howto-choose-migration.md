---
title: "Escolher a opção de hospedagem certa do Azure"
description: "Saiba qual caminho de migração do Azure é correto para seu aplicativo Web ASP.NET."
keywords: ".NET do Azure, ASP.NET, Serviço de Aplicativo, VM, máquina virtual, Aplicativo Web, migrar, migração"
author: CESARDELATORRE
manager: wpickett
ms.author: cesardl
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, casoper
ms.openlocfilehash: dbf54bb1a6e3d612ef8363a6b30e06b388b4490f
ms.sourcegitcommit: 3e904e6e4f04f1c92d729459434c85faff32e386
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="choose-the-right-azure-hosting-option"></a>Escolher a opção de hospedagem certa do Azure

Este documento fornece várias considerações e comparações entre as várias opções disponíveis no Azure ao migrar seus aplicativos .NET Framework existentes do local para o Azure.

As áreas fundamentais a considerar ao migrar os aplicativos .NET existentes para o Azure são:

1.  Opções de computação
2.  Opções de banco de dados
3.  Considerações de rede e segurança
4.  Considerações de autenticação e autorização

## <a name="compute-choices"></a>Opções de computação

Ao migrar os aplicativos .NET Framework existentes para o Azure, você tem várias opções.  No entanto, como o .NET Framework depende do Windows, as seguintes opções são limitadas aos serviços de computação baseados no Windows.

A tabela a seguir mostra várias comparações e recomendações para ajudá-lo a escolher o caminho de migração da computação correto para seu aplicativo .NET existente.

|                 | VMs do Azure | Serviço de aplicativo do Azure | Contêineres do Windows |
|-----------------|-----------|-------------------|--------------------|
|Quando usar      |<ul><li>O aplicativo depende muito do servidor e das instalações .msi locais.</li><li>Você deseja o caminho de migração do aplicativo mais fácil</li></ul>|O aplicativo não tem nenhuma dependência do servidor, ele é apenas um aplicativo Web ASP.NET limpo (MVC, WebForm) ou um aplicativo de N Camadas (API da Web, WCf) acessando um servidor do banco de dados. |<ul><li>O aplicativo tem dependências no servidor original, mas essas dependências podem ser incluídas na imagem do Docker Windows.</li><li>Deseja modernizar o aplicativo para que seja [Cloud DevOps-Ready](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-devops/reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications)</li></ul>|
|Vantagens e benefícios  |<ul><li>Caminho de migração mais fácil</li><li>Ambiente familiar. O ambiente de implantação é uma VM muito semelhante aos servidores locais.</li></ul> |Manutenção PaaS contínua, um modo mais simples de gerenciar e dimensionar os aplicativos no Azure. |<ul><li>Preparado para o futuro, Cloud DevOps-Ready com dependências incluídas nos contêineres do aplicativo.</li><li>Quase não há necessidade de reestruturar o código do .NET/C#.</li></ul> |
|Contras             |É IaaS. A manutenção é cara. Você precisa gerenciar a infraestrutura de VMs quanto à rede, balanceador de carga, expansão, gerenciamento do IIS etc. |<ul><li>Nem todos os aplicativos têm [suporte](http://www.migratetoazure.net/ReadinessAssessment)</li><li>Alguns aplicativos talvez precisem ser reestruturados e até um pouco recriados para que suportem o Serviço de Aplicativo do Azure.</li></ul> |<ul><li>Aprendizado das habilidades do Docker</li><li>Algumas alterações nas definições de configuração do aplicativo e do código</li></ul>|
|Requisitos |VM do Windows Server com os mesmos requisitos do aplicativo local | Requisitos do Serviço de Aplicativo do Azure especificados na [Análise de compatibilidade do Serviço de Aplicativo do Azure](https://www.migratetoazure.net/Resources). |<ul><li>[Windows Server 2016 com Contêineres - VM do Azure](https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.WindowsServer?tab=Overview)<br />ou o</li><li>[Serviço de Contêiner do Azure (AKS)](https://azure.microsoft.com/services/container-service/) (que é o orquestrador Kubernetes)<br />ou o<li>Orquestrador [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)</li></ul> |
|Como migrar |Confira [Migrar para Máquinas Virtuais do Azure](https://go.microsoft.com/fwlink/?linkid=862531) | Confira [Migrar o Serviço de Aplicativo do Azure](https://go.microsoft.com/fwlink/?linkid=862532) | Siga as considerações, cenários e o passo a passo explicado no [eBook Modernizando os aplicativos .NET existentes com Contêineres do Azure e Windows](https://aka.ms/liftandshiftwithcontainersebook) |

 O fluxograma a seguir mostra uma árvore de decisão ao planejar uma migração para o Azure para seus aplicativos .NET Framework existentes, sendo a opção A a primeira a testar e executar se for viável, mas a opção B é o caminho mais fácil de executar.

![Fluxograma mostrando a árvore de decisão de hospedagem](media/dotnet-howto-choose-migration/decision-tree.png)

## <a name="database-choices"></a>Opções de banco de dados

Ao migrar os bancos de dados relacionais para o Azure, você tem várias opções. Confira [Migrar seu banco de dados SQL Server para o Azure](https://go.microsoft.com/fwlink/?linkid=862533) para ajudá-lo a escolher o caminho de migração do banco de dados correto para seu aplicativo .NET existente.

## <a name="networking-and-security-considerations"></a>Considerações de rede e segurança

Ao implantar aplicativos em uma nuvem pública, como o Microsoft Azure, convém isolar e proteger certas redes [criando redes de perímetro de rede](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/), como um [rede de perímetro entre o Azure e o local](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) ou um [rede de perímetro entre o Azure e a Internet](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz). As redes de perímetro podem ser implementados com a [Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).
As redes virtuais do Azure permitem:

- compilar uma infraestrutura híbrida que você controla
- trazer seus próprios endereços IP e servidores DNS
- proteger suas conexões com uma VPN IPsec ou ExpressRoute
- ter um controle granular do tráfego entre as sub-redes
- criar topologias de rede sofisticadas usando soluções de virtualização
- ter um ambiente isolado e altamente seguro para seus aplicativos
 
Para começar a criar sua própria rede virtual, confira a [Documentação da Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Considerações de autenticação e autorização ao migrar para o Azure

Uma preocupação principal de qualquer organização ao mover para a nuvem é a segurança. A maioria das empresas investiu uma quantidade significativa de tempo, dinheiro e engenharia ao projetar e desenvolver um modelo de segurança, e é importante que elas possam aproveitar os investimentos existentes, como armazenamentos de identidade e soluções de logon único.

Muitos aplicativos .NET B2E existentes de empresas em execução no local usam o Active Directory para a autenticação e o gerenciamento de identidades.  O Azure AD Connect permite integrar seus diretórios locais no Azure Active Directory.  Para começar, confira [Integrar seus diretórios locais no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

Confira [Requisitos de identidade para sua solução de identidade híbrida](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs) para ter um planejamento adicional relacionado ao Azure Active Directory.

As outras opções de protocolo de autenticação são [OAuth](https://en.wikipedia.org/wiki/OAuth) e [OpenID](https://en.wikipedia.org/wiki/OpenID), comuns nos aplicativos voltados para o consumidor.  Ao usar bancos de dados de identidade autônomos, como um banco de dados SQL de Identidade do ASP.NET encapsulado pelo IdentityServer4 que usa o OAuth, geralmente não é necessária nenhuma conectividade com diretórios ou bancos de dados locais.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Migrar um aplicativo Web ASP.NET para o Serviço de Aplicativo do Azure](dotnet-howto-migrate-app-service.md)