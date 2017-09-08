---
title: "Notas de versão de bibliotecas de gerenciamento do Azure para .NET | Microsoft Docs"
description: "Veja o que há de novo e fique de olho em alterações significativas nas bibliotecas de gerenciamento do Azure para .NET."
keywords: "Azure, .NET, API, referência, anotações, atualizações, substituir, obsoleto"
author: camsoper
ms.author: casoper
manager: douge
ms.assetid: 
ms.service: Azure
ms.devlang: dotnet
ms.topic: reference
ms.technology: Azure
ms.date: 06/20/2017
ms.openlocfilehash: b4a66eb2860673f63a0d11c3cf31486337f36131
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="release-notes"></a><span data-ttu-id="ef858-104">Notas de versão</span><span class="sxs-lookup"><span data-stu-id="ef858-104">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="ef858-105">Disponibilidade de recursos e roteiro a partir da versão 1.0.0</span><span class="sxs-lookup"><span data-stu-id="ef858-105">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="ef858-106">26 de abril de 2017</span><span class="sxs-lookup"><span data-stu-id="ef858-106">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="ef858-107">Serviço | recurso</span><span class="sxs-lookup"><span data-stu-id="ef858-107">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="ef858-108">Disponível como GA (disponibilidade geral)</span><span class="sxs-lookup"><span data-stu-id="ef858-108">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="ef858-109">Disponível como versão prévia</span><span class="sxs-lookup"><span data-stu-id="ef858-109">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="ef858-110">Em breve</span><span class="sxs-lookup"><span data-stu-id="ef858-110">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="ef858-111">Computação</span><span class="sxs-lookup"><span data-stu-id="ef858-111">Compute</span></span></td>
    <td><span data-ttu-id="ef858-112">Máquinas virtuais e extensões de VM</span><span class="sxs-lookup"><span data-stu-id="ef858-112">Virtual machines and VM extensions</span></span><br><span data-ttu-id="ef858-113">conjuntos de escala de máquina virtual</span><span class="sxs-lookup"><span data-stu-id="ef858-113">Virtual machine scale sets</span></span><br><span data-ttu-id="ef858-114">Discos gerenciados</span><span class="sxs-lookup"><span data-stu-id="ef858-114">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="ef858-115">Serviços de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="ef858-115">Azure container services</span></span><br><span data-ttu-id="ef858-116">Registro de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="ef858-116">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="ef858-117">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="ef858-117">Storage</span></span></td>
    <td><span data-ttu-id="ef858-118">Contas de armazenamento</span><span class="sxs-lookup"><span data-stu-id="ef858-118">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="ef858-119">Criptografia</span><span class="sxs-lookup"><span data-stu-id="ef858-119">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="ef858-120">Banco de dados SQL</span><span class="sxs-lookup"><span data-stu-id="ef858-120">SQL Database</span></span></td>
    <td><span data-ttu-id="ef858-121">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="ef858-121">Databases</span></span><br><span data-ttu-id="ef858-122">Firewalls</span><span class="sxs-lookup"><span data-stu-id="ef858-122">Firewalls</span></span><br><span data-ttu-id="ef858-123">Pools elásticos</span><span class="sxs-lookup"><span data-stu-id="ef858-123">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="ef858-124">Rede</span><span class="sxs-lookup"><span data-stu-id="ef858-124">Networking</span></span></td>
    <td><span data-ttu-id="ef858-125">Redes virtuais</span><span class="sxs-lookup"><span data-stu-id="ef858-125">Virtual networks</span></span><br><span data-ttu-id="ef858-126">Interfaces de rede</span><span class="sxs-lookup"><span data-stu-id="ef858-126">Network interfaces</span></span><br><span data-ttu-id="ef858-127">Endereços IP</span><span class="sxs-lookup"><span data-stu-id="ef858-127">IP addresses</span></span><br><span data-ttu-id="ef858-128">Tabela de roteamento</span><span class="sxs-lookup"><span data-stu-id="ef858-128">Routing table</span></span><br><span data-ttu-id="ef858-129">Grupos de segurança de rede</span><span class="sxs-lookup"><span data-stu-id="ef858-129">Network security groups</span></span><br><span data-ttu-id="ef858-130">DNS</span><span class="sxs-lookup"><span data-stu-id="ef858-130">DNS</span></span><br><span data-ttu-id="ef858-131">Gerenciadores de tráfego</span><span class="sxs-lookup"><span data-stu-id="ef858-131">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="ef858-132">Balanceadores de carga</span><span class="sxs-lookup"><span data-stu-id="ef858-132">Load balancers</span></span><br><span data-ttu-id="ef858-133">Application gateways</span><span class="sxs-lookup"><span data-stu-id="ef858-133">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="ef858-134">Mais serviços</span><span class="sxs-lookup"><span data-stu-id="ef858-134">More services</span></span></td>
    <td><span data-ttu-id="ef858-135">Gerenciador de Recursos</span><span class="sxs-lookup"><span data-stu-id="ef858-135">Resource Manager</span></span><br><span data-ttu-id="ef858-136">Cofre de Chaves</span><span class="sxs-lookup"><span data-stu-id="ef858-136">Key Vault</span></span><br><span data-ttu-id="ef858-137">Redis</span><span class="sxs-lookup"><span data-stu-id="ef858-137">Redis</span></span><br><span data-ttu-id="ef858-138">CDN</span><span class="sxs-lookup"><span data-stu-id="ef858-138">CDN</span></span><br><span data-ttu-id="ef858-139">Batch</span><span class="sxs-lookup"><span data-stu-id="ef858-139">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="ef858-140">Serviço de Aplicativo - Aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="ef858-140">App service - Web apps</span></span><br><span data-ttu-id="ef858-141">Funções</span><span class="sxs-lookup"><span data-stu-id="ef858-141">Functions</span></span><br><span data-ttu-id="ef858-142">Barramento de Serviço</span><span class="sxs-lookup"><span data-stu-id="ef858-142">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="ef858-143">Monitoramento</span><span class="sxs-lookup"><span data-stu-id="ef858-143">Monitor</span></span><br><span data-ttu-id="ef858-144">RBAC do Graph</span><span class="sxs-lookup"><span data-stu-id="ef858-144">Graph RBAC</span></span><br><span data-ttu-id="ef858-145">DocumentDB</span><span class="sxs-lookup"><span data-stu-id="ef858-145">DocumentDB</span></span><br><span data-ttu-id="ef858-146">Agendador</span><span class="sxs-lookup"><span data-stu-id="ef858-146">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="ef858-147">Conceitos básicos</span><span class="sxs-lookup"><span data-stu-id="ef858-147">Fundamentals</span></span></td>
    <td><span data-ttu-id="ef858-148">Autenticação - básico</span><span class="sxs-lookup"><span data-stu-id="ef858-148">Authentication - core</span></span></td>
    <td><span data-ttu-id="ef858-149">Métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="ef858-149">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="ef858-150">A *versão prévia* dos recursos está sinalizada nos comentários da documentação nas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="ef858-150">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="ef858-151">Esses recursos estão sujeitos a alterações.</span><span class="sxs-lookup"><span data-stu-id="ef858-151">These features are subject to change.</span></span> <span data-ttu-id="ef858-152">Eles podem ser modificados de alguma forma (ou até mesmo removidos) no futuro.</span><span class="sxs-lookup"><span data-stu-id="ef858-152">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
