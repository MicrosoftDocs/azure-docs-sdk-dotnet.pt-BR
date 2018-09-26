---
title: Tutoriais do .NET para proteger seus aplicativos Azure
description: Tutoriais de segurança do aplicativo e gerenciamento de identidades nos aplicativos .NET em execução no Azure.
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 88ecfc69fbd57becf1adf1163a063c0d2bb086a8
ms.sourcegitcommit: 61638b504b6c4d96b357894835c80c2680a99fe6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750584"
---
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a><span data-ttu-id="1dab7-103">Tutoriais para autenticar usuários em seus aplicativos .NET em execução no Azure</span><span class="sxs-lookup"><span data-stu-id="1dab7-103">Tutorials for authenticating users in your .NET apps running on Azure</span></span>

<span data-ttu-id="1dab7-104">A tabela a seguir contém links para tutoriais detalhados sobre a autenticação de usuários e a proteção de aplicativos .NET em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="1dab7-104">The following table links to in-depth tutorials for authenticating users and securing .NET applications running on Azure.</span></span>

<span data-ttu-id="1dab7-105">Para exemplos de código-fonte, confira a lista de [exemplos do serviço do Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span><span class="sxs-lookup"><span data-stu-id="1dab7-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>

| | |
|---|---|
|<span data-ttu-id="1dab7-106">**Active Directory**</span><span class="sxs-lookup"><span data-stu-id="1dab7-106">**Active Directory**</span></span>||
| <span data-ttu-id="1dab7-107">[Adicionar o Azure Active Directory ao seu aplicativo Web usando os Serviços Conectados do Visual Studio][5]</span><span class="sxs-lookup"><span data-stu-id="1dab7-107">[Add Azure Active Directory to your web application by using Visual Studio Connected Services][5]</span></span> | <span data-ttu-id="1dab7-108">Conectar um aplicativo Web ao Azure AD no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1dab7-108">Connect a web app to Azure AD in Visual Studio</span></span> |
| <span data-ttu-id="1dab7-109">[Entrada e saída do aplicativo Web com o Azure AD][1]</span><span class="sxs-lookup"><span data-stu-id="1dab7-109">[Web app sign-in and sign-out with Azure AD][1]</span></span> | <span data-ttu-id="1dab7-110">Conectar e desconectar usuários do ASP.NET com a biblioteca ADAL.</span><span class="sxs-lookup"><span data-stu-id="1dab7-110">Sign users in and out of your ASP.NET with the ADAL library.</span></span> |
| <span data-ttu-id="1dab7-111">[Autenticação do aplicativo de área de trabalho com o Azure AD][2]</span><span class="sxs-lookup"><span data-stu-id="1dab7-111">[Desktop application authentication with Azure AD][2]</span></span>| <span data-ttu-id="1dab7-112">Integrar o Azure AD com um aplicativo WPF de área de trabalho do Windows usando a ADAL.</span><span class="sxs-lookup"><span data-stu-id="1dab7-112">Integrate Azure AD into a Windows Desktop WPF app using ADAL.</span></span> | 
| <span data-ttu-id="1dab7-113">[Autenticação da API Web com o Azure AD][3]</span><span class="sxs-lookup"><span data-stu-id="1dab7-113">[Web API authentication with Azure AD][3]</span></span> | <span data-ttu-id="1dab7-114">Proteja uma API Web usando os tokens de portador do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1dab7-114">Protect a web API using bearer tokens from Azure AD.</span></span> |
|<span data-ttu-id="1dab7-115">**Key Vault**</span><span class="sxs-lookup"><span data-stu-id="1dab7-115">**Key Vault**</span></span>||
| <span data-ttu-id="1dab7-116">[Adicionar o Key Vault a seu aplicativo Web usando os Serviço Conectados do Visual Studio][6]</span><span class="sxs-lookup"><span data-stu-id="1dab7-116">[Add Key Vault to your web application by using Visual Studio Connected Services][6]</span></span> | <span data-ttu-id="1dab7-117">Conectar um aplicativo Web ao Azure Key Vault no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1dab7-117">Connect a web app to Azure Key Vault in Visual Studio</span></span> |
| <span data-ttu-id="1dab7-118">[Usar Azure Key Vault em um aplicativo Web][4]</span><span class="sxs-lookup"><span data-stu-id="1dab7-118">[Use Azure Key Vault from a Web Application][4]</span></span> | <span data-ttu-id="1dab7-119">Acesse um segredo de Azure Key Vault para que ele possa ser usado em seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="1dab7-119">Access a secret from an Azure Key Vault so that it can be used in your web application.</span></span> | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application
[5]: /azure/active-directory/develop/vs-active-directory-add-connected-service
[6]: /azure/key-vault/vs-key-vault-add-connected-service