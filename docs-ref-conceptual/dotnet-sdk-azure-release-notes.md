---
title: Notas de versão de bibliotecas de gerenciamento do Azure para .NET | Microsoft Docs
description: Veja o que há de novo e fique de olho em alterações significativas nas bibliotecas de gerenciamento do Azure para .NET.
keywords: Azure, .NET, API, referência, anotações, atualizações, substituir, obsoleto
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 48ff29507268f6b38acb24217801cf7b0227e444
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2018
ms.locfileid: "31005903"
---
# <a name="release-notes"></a><span data-ttu-id="20ad1-104">Notas de versão</span><span class="sxs-lookup"><span data-stu-id="20ad1-104">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="20ad1-105">Disponibilidade de recursos e roteiro a partir da versão 1.0.0</span><span class="sxs-lookup"><span data-stu-id="20ad1-105">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="20ad1-106">26 de abril de 2017</span><span class="sxs-lookup"><span data-stu-id="20ad1-106">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="20ad1-107">Serviço | recurso</span><span class="sxs-lookup"><span data-stu-id="20ad1-107">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="20ad1-108">Disponível como GA (disponibilidade geral)</span><span class="sxs-lookup"><span data-stu-id="20ad1-108">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="20ad1-109">Disponível como versão prévia</span><span class="sxs-lookup"><span data-stu-id="20ad1-109">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="20ad1-110">Em breve</span><span class="sxs-lookup"><span data-stu-id="20ad1-110">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="20ad1-111">Computação</span><span class="sxs-lookup"><span data-stu-id="20ad1-111">Compute</span></span></td>
    <td><span data-ttu-id="20ad1-112">Máquinas virtuais e extensões de VM</span><span class="sxs-lookup"><span data-stu-id="20ad1-112">Virtual machines and VM extensions</span></span><br><span data-ttu-id="20ad1-113">conjuntos de escala de máquina virtual</span><span class="sxs-lookup"><span data-stu-id="20ad1-113">Virtual machine scale sets</span></span><br><span data-ttu-id="20ad1-114">Discos gerenciados</span><span class="sxs-lookup"><span data-stu-id="20ad1-114">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="20ad1-115">Serviços de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="20ad1-115">Azure container services</span></span><br><span data-ttu-id="20ad1-116">Registro de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="20ad1-116">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="20ad1-117">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="20ad1-117">Storage</span></span></td>
    <td><span data-ttu-id="20ad1-118">Contas de armazenamento</span><span class="sxs-lookup"><span data-stu-id="20ad1-118">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="20ad1-119">Criptografia</span><span class="sxs-lookup"><span data-stu-id="20ad1-119">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="20ad1-120">Banco de dados SQL</span><span class="sxs-lookup"><span data-stu-id="20ad1-120">SQL Database</span></span></td>
    <td><span data-ttu-id="20ad1-121">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="20ad1-121">Databases</span></span><br><span data-ttu-id="20ad1-122">Firewalls</span><span class="sxs-lookup"><span data-stu-id="20ad1-122">Firewalls</span></span><br><span data-ttu-id="20ad1-123">Pools elásticos</span><span class="sxs-lookup"><span data-stu-id="20ad1-123">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="20ad1-124">Rede</span><span class="sxs-lookup"><span data-stu-id="20ad1-124">Networking</span></span></td>
    <td><span data-ttu-id="20ad1-125">Redes virtuais</span><span class="sxs-lookup"><span data-stu-id="20ad1-125">Virtual networks</span></span><br><span data-ttu-id="20ad1-126">Interfaces de rede</span><span class="sxs-lookup"><span data-stu-id="20ad1-126">Network interfaces</span></span><br><span data-ttu-id="20ad1-127">Endereços IP</span><span class="sxs-lookup"><span data-stu-id="20ad1-127">IP addresses</span></span><br><span data-ttu-id="20ad1-128">Tabela de roteamento</span><span class="sxs-lookup"><span data-stu-id="20ad1-128">Routing table</span></span><br><span data-ttu-id="20ad1-129">Grupos de segurança de rede</span><span class="sxs-lookup"><span data-stu-id="20ad1-129">Network security groups</span></span><br><span data-ttu-id="20ad1-130">DNS</span><span class="sxs-lookup"><span data-stu-id="20ad1-130">DNS</span></span><br><span data-ttu-id="20ad1-131">Gerenciadores de tráfego</span><span class="sxs-lookup"><span data-stu-id="20ad1-131">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="20ad1-132">Balanceadores de carga</span><span class="sxs-lookup"><span data-stu-id="20ad1-132">Load balancers</span></span><br><span data-ttu-id="20ad1-133">Application gateways</span><span class="sxs-lookup"><span data-stu-id="20ad1-133">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="20ad1-134">Mais serviços</span><span class="sxs-lookup"><span data-stu-id="20ad1-134">More services</span></span></td>
    <td><span data-ttu-id="20ad1-135">Gerenciador de Recursos</span><span class="sxs-lookup"><span data-stu-id="20ad1-135">Resource Manager</span></span><br><span data-ttu-id="20ad1-136">Cofre da Chave</span><span class="sxs-lookup"><span data-stu-id="20ad1-136">Key Vault</span></span><br><span data-ttu-id="20ad1-137">Redis</span><span class="sxs-lookup"><span data-stu-id="20ad1-137">Redis</span></span><br><span data-ttu-id="20ad1-138">CDN</span><span class="sxs-lookup"><span data-stu-id="20ad1-138">CDN</span></span><br><span data-ttu-id="20ad1-139">Batch</span><span class="sxs-lookup"><span data-stu-id="20ad1-139">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="20ad1-140">Serviço de Aplicativo - Aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="20ad1-140">App service - Web apps</span></span><br><span data-ttu-id="20ad1-141">Funções</span><span class="sxs-lookup"><span data-stu-id="20ad1-141">Functions</span></span><br><span data-ttu-id="20ad1-142">Barramento de Serviço</span><span class="sxs-lookup"><span data-stu-id="20ad1-142">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="20ad1-143">Monitoramento</span><span class="sxs-lookup"><span data-stu-id="20ad1-143">Monitor</span></span><br><span data-ttu-id="20ad1-144">RBAC do Graph</span><span class="sxs-lookup"><span data-stu-id="20ad1-144">Graph RBAC</span></span><br><span data-ttu-id="20ad1-145">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="20ad1-145">Azure Cosmos DB</span></span><br><span data-ttu-id="20ad1-146">Agendador</span><span class="sxs-lookup"><span data-stu-id="20ad1-146">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="20ad1-147">Conceitos básicos</span><span class="sxs-lookup"><span data-stu-id="20ad1-147">Fundamentals</span></span></td>
    <td><span data-ttu-id="20ad1-148">Autenticação - básico</span><span class="sxs-lookup"><span data-stu-id="20ad1-148">Authentication - core</span></span></td>
    <td><span data-ttu-id="20ad1-149">Métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="20ad1-149">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="20ad1-150">A *versão prévia* dos recursos está sinalizada nos comentários da documentação nas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="20ad1-150">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="20ad1-151">Esses recursos estão sujeitos a alterações.</span><span class="sxs-lookup"><span data-stu-id="20ad1-151">These features are subject to change.</span></span> <span data-ttu-id="20ad1-152">Eles podem ser modificados de alguma forma (ou até mesmo removidos) no futuro.</span><span class="sxs-lookup"><span data-stu-id="20ad1-152">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
