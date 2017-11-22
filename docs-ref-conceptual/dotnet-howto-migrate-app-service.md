---
title: "Migrar um aplicativo Web ASP.NET para o Serviço de Aplicativo do Azure"
description: "Saiba como migrar um aplicativo Web ASP.NET do local para o Serviço de Aplicativo do Azure."
keywords: ".NET do Azure, ASP.NET, Serviço de Aplicativo, Aplicativo Web, migrar, migração"
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter
ms.openlocfilehash: 1e2274c428fedc8c65627a99ae7be8a15c85e610
ms.sourcegitcommit: c360a22d5bff6eedd714b28b847d2f26b06665f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="migrate-an-aspnet-web-application-to-azure-app-service"></a>Migrar um aplicativo Web ASP.NET para o Serviço de Aplicativo do Azure

O [Serviço de Aplicativo](https://docs.microsoft.com/azure/app-service/app-service-web-overview#why-use-web-apps) é um serviço de plataforma de computação totalmente gerenciado que é otimizado para hospedar sites escalonáveis e aplicativos Web. Este documento fornece informações sobre como fazer um lift-and-shift em um aplicativo existente para o Serviço de Aplicativo do Azure, fornece as modificações a considerar e recursos adicionais para mover para a nuvem.

Pronto para começar? [Publique seu aplicativo ASP.NET + SQL para o Serviço de Aplicativo do Azure](https://go.microsoft.com/fwlink/?linkid=863214).

# <a name="preparation"></a>Preparação   
* [Como determinar se seu aplicativo se qualifica para o Serviço de Aplicativo](https://azure.microsoft.com/downloads/migration-assistant/)
* [Movendo o banco de dados para a nuvem](https://go.microsoft.com/fwlink/?linkid=863217)

# <a name="considerations"></a>Considerações
Há vários fatores que você deve considerar antes de migrar seu aplicativo. Abaixo, está uma lista de possíveis modificações que talvez você precise fazer em seu aplicativo e como fazê-las.

## <a name="sql-database-configuration"></a>Configuração do Banco de Dados SQL
Se seu aplicativo está usando um banco de dados local, você tem várias opções para o aplicativo Web. [Leia mais sobre como migrar os bancos de dados SQL para o Azure](https://go.microsoft.com/fwlink/?linkid=863217).

## <a name="iis"></a>IIS
Tudo configurado tradicionalmente via applicationHost.config em seu aplicativo, agora pode ser configurado com o portal do Azure. Isso se aplica ao número de bits do AppPool, habilitar/desabilitar websockets, versão do pipeline gerenciada, versão do .NET Framework (2.0/4.0) etc. Para modificar as [configurações do aplicativo](https://docs.microsoft.com/en-us/azure/app-service/web-sites-configure), navegue até o [portal do Azure](https://portal.azure.com), abra a folha de seu aplicativo Web, em seguida, selecione a guia **Configurações do Aplicativo**.

## <a name="authentication"></a>Autenticação
Se o aplicativo autentica os usuários a qualquer momento, você precisará modificar essa funcionalidade para ser executada assim que o aplicativo for implantado nos Aplicativos Web do Azure. Uma possibilidade é usar o Azure AD Connect para integrar seus diretórios locais no Azure Active Directory. [Saiba mais sobre como integrar seus diretórios locais no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

## <a name="virtual-network-modification"></a>Modificação da Rede Virtual
Se você usar mais de um serviço do Azure, poderá considerar o uso de uma rede virtual para se comunicar com segurança entre os serviços. Você pode configurar uma conexão da rede local com uma [Rede Virtual do Azure](https://docs.microsoft.com/en-us/azure/app-service/web-sites-integrate-with-vnet) usando a VPN ou o ExpressRoute.

## <a name="monitoring-and-diagnostics"></a>Monitoramento e diagnóstico
As atuais soluções locais para o monitoramento e diagnóstico provavelmente não funcionarão na nuvem. No entanto, o Azure fornece ferramentas para o registro em log, monitoramento e diagnóstico, para que você possa identificar e depurar os problemas nos aplicativos Web. Você pode habilitar facilmente o diagnóstico para seu aplicativo Web na configuração e pode exibir os logs registrados no Azure Application Insights. [Saiba mais sobre como habilitar o log de diagnóstico para os aplicativos Web](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

## <a name="connection-strings-and-application-settings"></a>Configurações do aplicativo e Cadeias de Conexão
Uma opção para manter as informações seguras é usar o [KeyVault do Azure](https://docs.microsoft.com/azure/key-vault/), um serviço que armazena com segurança as informações confidenciais usadas em seu aplicativo. Como alternativa, você pode armazenar esses dados como uma configuração do Serviço de Aplicativo.

## <a name="dns"></a>DNS
Talvez seja necessário atualizar as configurações de DNS com base nos requisitos de seu aplicativo. Essas configurações de DNS podem ser definidas nas [configurações de domínio personalizadas](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain) do Serviço de Aplicativo. Outro fator a considerar é como [associar um certificado SSL personalizado existente](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-tutorial-custom-ssl).

## <a name="file-system-and-storage"></a>Sistema de arquivos e Armazenamento
Se seu aplicativo persistir os dados, você precisará atualizá-lo para usar o Armazenamento do Azure. O Armazenamento do Azure é um serviço que fornece compartilhamentos de arquivos para compartilhar via protocolo SMB, armazenamento de blobs, filas simples e tabelas não relacionais. [Saiba mais sobre os compartilhamentos de arquivos do Armazenamento do Azure](https://docs.microsoft.com/azure/storage/files/storage-files-introduction).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Migrar um aplicativo Web ASP.NET para uma Máquina Virtual do Azure](dotnet-howto-migrate-to-vm.md)