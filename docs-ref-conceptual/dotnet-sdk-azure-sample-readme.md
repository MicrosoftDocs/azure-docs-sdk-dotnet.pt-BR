---
title: Instruções de exemplo das bibliotecas de gerenciamento do Azure para .NET
description: Obtenha o exemplo de código para criar e atualizar recursos usando as bibliotecas de gerenciamento do Azure para .NET.
keywords: Azure, .NET, SDK, API, amostra, exemplo
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: a931e623768e1fddad263c7da8eb864c37613379
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
ms.locfileid: "29752468"
---
# <a name="azure-management-libraries-for-net-sample-instructions"></a>Instruções de exemplo das bibliotecas de gerenciamento do Azure para .NET

Este artigo descreve os pré-requisitos e a autenticação necessários para executar os exemplos das bibliotecas de gerenciamento do Azure para .NET.

## <a name="prerequisties"></a>Pré-requisitos 

* [Visual Studio 2017](https://www.visualstudio.com/vs/) ou [SDK do .NET Core](https://www.microsoft.com/net/download/core)
* Uma [assinatura do Microsoft Azure](https://azure.microsoft.com/free/)
* [Cliente de linha de comando Git](https://git-scm.com/)
* [PowerShell do Azure](/powershell/azure/install-azurerm-ps)

## <a name="authentication-for-all-samples"></a>Autenticação de todos os exemplo

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="running-the-samples"></a>Executando os exemplos

Depois de usar o Git para clonar o exemplo, você poderá abrir o exemplo no Visual Studio e executá-lo usando o IDE.  Como alternativa, use o SDK do .NET Core para compilar e executar o exemplo na linha de comando da seguinte maneira:

```cmd
git clone https://github.com/Azure-Samples/app-service-dotnet-configure-deployment-sources-for-web-apps.git
cd app-service-dotnet-configure-deployment-sources-for-web-apps
dotnet restore
dotnet run
```