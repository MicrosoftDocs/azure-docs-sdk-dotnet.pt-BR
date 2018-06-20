---
title: Migrar um banco de dados do SQL Server para o Azure
description: Saiba como migrar um banco de dados do SQL Server local para o Azure.
keywords: .NET do Azure, ASP.NET, SQL, SQL Server, Banco de Dados SQL, migrar, migração
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: sql-database
ms.custom: devcenter
ms.openlocfilehash: d118d39e2168686c851f0daa6cb611f0a0c9d2fc
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
ms.locfileid: "29728487"
---
## <a name="migrate-a-sql-server-database-to-azure"></a>Migrar um banco de dados do SQL Server para o Azure

Este artigo curto fornece uma breve descrição de duas opções para migrar um banco de dados do SQL Server para o Azure.

O Azure tem duas opções principais para migrar um banco de dados do SQL Server de produção:

1. [SQL Server em VMs do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): uma instância do SQL Server instalada e hospedada em uma Máquina Virtual do Windows executada no Azure, também conhecida como IaaS (Infraestrutura como Serviço).
2. [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): um serviço Azure do banco de dados SQL totalmente gerenciado, também conhecido como PaaS (Plataforma como Serviço).

Ambos são fornecidos com vantagens e desvantagens que você precisará avaliar antes de migrar.

## <a name="get-started"></a>Introdução

Os guias de migração a seguir serão úteis, dependendo de qual serviço você usar:

* [Migrar um banco de dados do SQL Server para o SQL Server em uma VM do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [Migrar seu banco de dados do SQL Server para o banco de dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Além disso, os links a seguir para conteúdos conceituais vão ajudá-lo a entender melhor as VMs:

* [Alta disponibilidade e recuperação de desastres para SQL Server em Máquinas Virtuais do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Práticas recomendadas para o SQL Server em Máquinas Virtuais do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Estratégias de Desenvolvimento e Padrões de Aplicativo para o SQL Server em Máquinas Virtuais do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

E os links a seguir o ajudarão a compreender melhor o Banco de Dados SQL do Azure:

* [Criar e gerenciar servidores do Banco de Dados SQL e bancos de dados](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [DTUs (Unidades de Transação do Banco de Dados) e eDTUs (Unidades de Transação do Banco de Dados Elásticas)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Limites de recursos do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>Escolhendo IaaS ou PaaS

Ao avaliar onde migrar seu banco de dados, você deve determinar se IaaS ou PaaS é mais adequada para você.

**Você deve escolher o SQL Server nas VMs do Azure se:**

* está procurando "aumentar e mover" seu banco de dados e aplicativos com uma alteração mínima ou nenhuma.
* prefere ter controle total sobre o servidor do banco de dados e a VM na qual ele é executado.
* já tem licenças do SQL Server e Windows Server que pretende usar.

**Você deve escolher o Banco de Dados SQL do Azure se:**

* está procurando para modernizar seus aplicativos e está migrando para usar outros serviços de PaaS no Azure.
* não deseja gerenciar seu servidor do banco de dados e a VM na qual ele é executado.
* não tem licenças do SQL Server ou Windows Server, nem pretende permitir que as licenças expirem.

A tabela a seguir descreve as diferenças entre cada serviço com base em vários cenários.

| Cenário | SQL Server nas VMs do Azure | Banco de Dados SQL do Azure |
|----------|-------------------------|--------------------|
| Migração | Requer alterações mínimas no banco de dados. | Poderá exigir alterações em seu banco de dados se você usar recursos indisponíveis no SQL do Azure, conforme determinado pelo [Assistente de Migração de Dados](https://www.microsoft.com/download/details.aspx?id=53595) ou se tiver outras dependências, como executáveis instalados localmente.|
| Gerenciando a disponibilidade, recuperação e atualizações | A disponibilidade e a recuperação são configuradas manualmente. As atualizações podem ser automatizadas com os [Conjuntos de Dimensionamento de VMs](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade). | Gerenciadas automaticamente para você. |
| Configuração do SO subjacente | Configuração manual. | Gerenciadas automaticamente para você. |
| Gerenciando o tamanho do banco de dados | Suporta até 64 TB de armazenamento por instância do SQL Server. | Suporta 4 TB de armazenamento antes de precisar de uma partição horizontal. |
| Gerenciando os custos | Você deve gerenciar os custos de licença do SQL Server, custos de licença do Windows Server e custos da VM (com base nos núcleos, RAM e armazenamento). | Deve gerenciar os custos do serviço (com base nas [eDTUs ou DTUs](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), armazenamento e número de bancos de dados se usar um pool elástico).  Também deve gerenciar o custo de qualquer SLA. |

Para saber mais sobre as diferenças entre os dois, leia Escolher uma opção do SQL Server na nuvem: [banco de dados SQL do Azure ou SQL Server nas VMs do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).

## <a name="faq"></a>Perguntas frequentes

* **Ainda posso usar ferramentas, como o SQL Server Management Studio e SQL Server Reporting Services (SSRS), com o SQL Server nas VMs do Azure ou no Banco de Dados SQL do Azure?**

    Sim! Todas as ferramentas do Microsoft SQL funcionam com ambos os serviços. No entanto, o SSRS não faz parte do Banco de Dados SQL do Azure e é recomendado que você execute-o em uma VM do Azure, em seguida, aponte-o para sua instância do banco de dados.
    
* **Desejo ir para o PaaS, mas não sei se meu banco de dados é compatível. Há ferramentas para ajudar?**

    Sim. O [Assistente de Migração de Dados](https://www.microsoft.com/download/details.aspx?id=53595) é uma ferramenta usada como parte da migração para o Banco de Dados SQL do Azure.  O [Serviço de Migração de Banco de Dados do Azure](https://azure.microsoft.com/campaigns/database-migration/) é um serviço de visualização que você pode usar para o IaaS ou PaaS.

* **Posso estimar os custos?**

    Sim.  A [Calculadora de Preços do Azure](https://azure.microsoft.com/pricing/calculator/) pode ser usada para estimar os custos para todos os serviços do Azure, incluindo as VMs e os serviços de banco de dados.
    
## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Escolher a opção de hospedagem correta do Azure](dotnet-howto-choose-migration.md)
