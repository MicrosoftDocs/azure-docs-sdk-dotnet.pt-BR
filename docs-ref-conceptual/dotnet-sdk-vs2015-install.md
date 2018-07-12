---
title: Ferramentas do Azure para Visual Studio 2015
description: Obtenha as ferramentas para começar a usar as bibliotecas .NET do Azure no Visual Studio 2015.
keywords: .NET do Azure, SDK, VS2015, Visual Studio 2015
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 5046781a16b5b330b95c4ad36e8a8187126fef4e
ms.sourcegitcommit: 1c2e1fd031ad012d6888fcde3cd325f7e8e49e0f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2018
ms.locfileid: "29752808"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Ferramentas do Azure para Visual Studio 2015

A maneira mais rápida e fácil de instalar o **SDK do Azure para Visual Studio 2015** e o **SDK do Service Fabric e Ferramentas para Visual Studio 2015** é usando o [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).  O Microsoft Web Platform Installer é uma ferramenta gratuita que simplifica o download, a instalação e a atualização de alguns dos componentes do Microsoft Web Platform, incluindo as ferramentas do Azure para Visual Studio 2015.  Esses SDKs também podem ser baixados e instalados como componentes individuais na [página Downloads do Azure](https://azure.microsoft.com/downloads/). 

## <a name="using-the-web-platform-installer"></a>Usando o Web Platform Installer

1. Baixe e execute este [bootstrapper do Web Platform Installer](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).  

2. O bootstrapper instalará o Web Platform Installer (se necessário) e colocará automaticamente as últimas versões dos itens do **SDK do Azure para Visual Studio 2015** e do **SDK do Service Fabric e Ferramentas para Visual Studio 2015** na sua lista *Itens a serem instalados*.  Clique em **Instalar**.

    ![Web Platform Installer](media/dotnet-sdk-vs2015-install/webpi.png)

3. Na próxima tela, clique em **Aceito**.  O Web PI começará a baixar e instalar os componentes selecionados.

4. Depois que a instalação for concluída, ela exibirá uma tela de confirmação.  Clique em **Concluir**.  Agora você pode fechar o Web Platform Installer.

## <a name="verifying-the-installation"></a>Verificando a instalação

1. No Visual Studio 2015, clique no menu **Ferramentas** e clique em **Extensões e Atualizações...**.

2. A lista exibida conterá várias ferramentas do Azure, como **Ferramentas do Serviço de Aplicativo do Microsoft Azure**, **Serviço Conectado do Armazenamento do Microsoft Azure** e **Ferramentas do Service Fabric**.

    ![Extensões e atualizações](media\dotnet-sdk-vs2015-install\ext-tools.png)

## <a name="next-steps"></a>Próximas etapas

[Introdução às bibliotecas do Azure para .NET](dotnet-sdk-azure-get-started.md).
