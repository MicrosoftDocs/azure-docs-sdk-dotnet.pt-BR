---
title: "Instruções de exemplo das bibliotecas de gerenciamento do Azure para .NET"
description: "Obtenha o exemplo de código para criar e atualizar recursos usando as bibliotecas de gerenciamento do Azure para .NET."
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
---
# <a name="azure-management-libraries-for-net-sample-instructions"></a><span data-ttu-id="84018-104">Instruções de exemplo das bibliotecas de gerenciamento do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="84018-104">Azure management libraries for .NET sample instructions</span></span>

<span data-ttu-id="84018-105">Este artigo descreve os pré-requisitos e a autenticação necessários para executar os exemplos das bibliotecas de gerenciamento do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="84018-105">This article describes the prerequisites and authentication required for running the samples for the Azure management libraries for .NET.</span></span>

## <a name="prerequisties"></a><span data-ttu-id="84018-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="84018-106">Prerequisties</span></span> 

* <span data-ttu-id="84018-107">[Visual Studio 2017](https://www.visualstudio.com/vs/) ou [SDK do .NET Core](https://www.microsoft.com/net/download/core)</span><span class="sxs-lookup"><span data-stu-id="84018-107">[Visual Studio 2017](https://www.visualstudio.com/vs/) or [.NET Core SDK](https://www.microsoft.com/net/download/core)</span></span>
* <span data-ttu-id="84018-108">Uma [assinatura do Microsoft Azure](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="84018-108">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>
* [<span data-ttu-id="84018-109">Cliente de linha de comando Git</span><span class="sxs-lookup"><span data-stu-id="84018-109">Git command line client</span></span>](https://git-scm.com/)
* [<span data-ttu-id="84018-110">PowerShell do Azure</span><span class="sxs-lookup"><span data-stu-id="84018-110">Azure PowerShell</span></span>](/powershell/azure/install-azurerm-ps)

## <a name="authentication-for-all-samples"></a><span data-ttu-id="84018-111">Autenticação de todos os exemplo</span><span class="sxs-lookup"><span data-stu-id="84018-111">Authentication for all samples</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="running-the-samples"></a><span data-ttu-id="84018-112">Executando os exemplos</span><span class="sxs-lookup"><span data-stu-id="84018-112">Running the samples</span></span>

<span data-ttu-id="84018-113">Depois de usar o Git para clonar o exemplo, você poderá abrir o exemplo no Visual Studio e executá-lo usando o IDE.</span><span class="sxs-lookup"><span data-stu-id="84018-113">Once you have used Git to clone the sample, you can open the sample in Visual Studio and run the sample using the IDE.</span></span>  <span data-ttu-id="84018-114">Como alternativa, use o SDK do .NET Core para compilar e executar o exemplo na linha de comando da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="84018-114">Alternatively, use the .NET Core SDK to build and run the sample from the command line, like this:</span></span>

```cmd
git clone https://github.com/Azure-Samples/app-service-dotnet-configure-deployment-sources-for-web-apps.git
cd app-service-dotnet-configure-deployment-sources-for-web-apps
dotnet restore
dotnet run
```