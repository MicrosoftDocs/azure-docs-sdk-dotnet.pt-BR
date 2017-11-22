---
title: "Migrar um aplicativo Web ASP.NET para uma Máquina Virtual do Azure"
description: "Saiba como migrar um aplicativo Web ASP.NET do local para uma Máquina Virtual do Azure."
keywords: ".NET do Azure, ASP.NET, VM, máquina virtual, migrar, migração"
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: virtual-machines
ms.custom: devcenter
ms.openlocfilehash: 718d91b98180a7584f78a2383d430c4700743306
ms.sourcegitcommit: c360a22d5bff6eedd714b28b847d2f26b06665f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="78160-104">Migrar um aplicativo Web ASP.NET para uma Máquina Virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="78160-104">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="78160-105">Este documento fornece uma visão geral de como migrar um aplicativo Web ASP.NET do local para uma Máquina Virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="78160-105">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="get-started"></a><span data-ttu-id="78160-106">Introdução</span><span class="sxs-lookup"><span data-stu-id="78160-106">Get Started</span></span>

<span data-ttu-id="78160-107">Esses tutoriais demonstram as etapas para criar (ou migrar) uma máquina virtual, publicar seu aplicativo Web para ela e outras tarefas que podem ser necessárias para dar suporte ao seu aplicativo no Azure.</span><span class="sxs-lookup"><span data-stu-id="78160-107">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="78160-108">Crie uma máquina virtual para seu aplicativo ASP.NET no Azure usando uma das duas opções a seguir:</span><span class="sxs-lookup"><span data-stu-id="78160-108">Create a virtual machine for your ASP.NET application in Azure using one of the following two options:</span></span>
    - [<span data-ttu-id="78160-109">Criar uma nova máquina virtual para Aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78160-109">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
    - [<span data-ttu-id="78160-110">Migrar uma máquina virtual local existente</span><span class="sxs-lookup"><span data-stu-id="78160-110">Migrate an existing on-premises virtual machine</span></span>](https://docs.microsoft.com/azure/site-recovery/tutorial-migrate-on-premises-to-azure)
- [<span data-ttu-id="78160-111">Publicar seu aplicativo usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="78160-111">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="78160-112">Criar uma rede virtual segura para suas VMs</span><span class="sxs-lookup"><span data-stu-id="78160-112">Create a secure virtual network for your VMs</span></span>](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="78160-113">Criar um pipeline CI/CD para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="78160-113">Create a CI/CD pipeline for your application</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="78160-114">Mover para um conjunto de dimensionamento da VM para ter alta disponibilidade e escalabilidade</span><span class="sxs-lookup"><span data-stu-id="78160-114">Move to a VM scale set for high availability and scalability</span></span>](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="78160-115">Considerações</span><span class="sxs-lookup"><span data-stu-id="78160-115">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="78160-116">Benefícios</span><span class="sxs-lookup"><span data-stu-id="78160-116">Benefits</span></span>

<span data-ttu-id="78160-117">As máquinas virtuais oferecem o caminho mais fácil para migrar um aplicativo do local para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="78160-117">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span>  <span data-ttu-id="78160-118">Elas permitem replicar o mesmo ambiente que seu aplicativo usa no local e eliminam a necessidade de manter seus próprios data centers.</span><span class="sxs-lookup"><span data-stu-id="78160-118">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span>  <span data-ttu-id="78160-119">Os Conjuntos de Dimensionamento da Máquina Virtual fornecem alta disponibilidade e escalabilidade para os aplicativos executados em Máquinas Virtuais.</span><span class="sxs-lookup"><span data-stu-id="78160-119">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="78160-120">Tamanho da Máquina Virtual</span><span class="sxs-lookup"><span data-stu-id="78160-120">Virtual Machine Size</span></span>

<span data-ttu-id="78160-121">Escolha o tamanho da máquina virtual e o tipo mais otimizados para sua carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="78160-121">Choose the virtual machine size and type that is best optimized for your workload.</span></span>  <span data-ttu-id="78160-122">Confira os [tamanhos das máquinas virtuais do Windows no Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).</span><span class="sxs-lookup"><span data-stu-id="78160-122">See [sizes for Windows virtual machines in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) for more information.</span></span>

### <a name="maintenance"></a><span data-ttu-id="78160-123">Manutenção </span><span class="sxs-lookup"><span data-stu-id="78160-123">Maintenance</span></span>

<span data-ttu-id="78160-124">Assim como uma máquina local, você é responsável por manter e atualizar a máquina virtual<sup>&#42;</sup>.</span><span class="sxs-lookup"><span data-stu-id="78160-124">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span>  <span data-ttu-id="78160-125">Se seu aplicativo puder ser executado em um ambiente PaaS (Plataforma como Serviço), como o [Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service/), ou em um [contêiner](https://docs.microsoft.com/azure/app-service/containers/), isso eliminará a necessidade.</span><span class="sxs-lookup"><span data-stu-id="78160-125">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](https://docs.microsoft.com/azure/app-service/) or in a [container](https://docs.microsoft.com/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="78160-126">*<sup>&#42; </sup>[As atualizações automáticas do SO para os conjuntos de dimensionamento da máquina virtual](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) estão disponíveis atualmente como um serviço de Visualização.*</span><span class="sxs-lookup"><span data-stu-id="78160-126">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="78160-127">Redes Virtuais</span><span class="sxs-lookup"><span data-stu-id="78160-127">Virtual Networks</span></span>

<span data-ttu-id="78160-128">As Redes Virtuais do Azure permitem:</span><span class="sxs-lookup"><span data-stu-id="78160-128">Azure Virtual Networks enable you to:</span></span>
- <span data-ttu-id="78160-129">compilar uma infraestrutura híbrida que você controla</span><span class="sxs-lookup"><span data-stu-id="78160-129">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="78160-130">trazer seus próprios endereços IP e servidores DNS</span><span class="sxs-lookup"><span data-stu-id="78160-130">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="78160-131">criar um ambiente isolado e altamente seguro para seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="78160-131">Create an isolated and highly-secure environment for your applications</span></span>
- <span data-ttu-id="78160-132">conectar a VM à sua rede local usando uma das várias [opções de conectividade](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span><span class="sxs-lookup"><span data-stu-id="78160-132">Connect your VM to your on-premises network using one of several [connectivity options](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="78160-133">integrar sua máquina virtual na rede local usando o [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span><span class="sxs-lookup"><span data-stu-id="78160-133">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="78160-134">Para começar, confira a [documentação da Rede Virtual](https://docs.microsoft.com/azure/virtual-network/)</span><span class="sxs-lookup"><span data-stu-id="78160-134">To get started, see the [Virtual Network documentation](https://docs.microsoft.com/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="78160-135">Active Directory</span><span class="sxs-lookup"><span data-stu-id="78160-135">Active Directory</span></span>
<span data-ttu-id="78160-136">Muitos aplicativos usam o Active Directory para a autenticação e o gerenciamento das identidades.</span><span class="sxs-lookup"><span data-stu-id="78160-136">Many applications use Active Directory for authentication and identity management.</span></span>  
- <span data-ttu-id="78160-137">O Azure AD Connect permite integrar seus diretórios locais no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="78160-137">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span>  <span data-ttu-id="78160-138">Para começar, confira [Integrar seus diretórios locais no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="78160-138">To get started, see [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span></span>  
- <span data-ttu-id="78160-139">Como alternativa, o [ExpressRoute](https://azure.microsoft.com/services/expressroute/) permite que seu aplicativo acesse o Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="78160-139">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="78160-140">BANCOS DE DADOS SQL</span><span class="sxs-lookup"><span data-stu-id="78160-140">SQL Databases</span></span>

<span data-ttu-id="78160-141">Se seu aplicativo estiver usando um banco de dados local, o aplicativo não conseguirá comunicar-se com ele por padrão.</span><span class="sxs-lookup"><span data-stu-id="78160-141">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="78160-142">Você pode:</span><span class="sxs-lookup"><span data-stu-id="78160-142">You can either:</span></span>
- <span data-ttu-id="78160-143">Configure uma rede híbrida que permita ao seu aplicativo acessar o banco de dados em execução no local.</span><span class="sxs-lookup"><span data-stu-id="78160-143">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>  
- <span data-ttu-id="78160-144">Migre seu banco de dados para o Azure.</span><span class="sxs-lookup"><span data-stu-id="78160-144">Migrate your database to the Azure.</span></span>  <span data-ttu-id="78160-145">Confira [Migrar seu banco de dados SQL Server para o Azure](dotnet-howto-migrate-sql.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="78160-145">See [Migrate your SQL Server database to Azure](dotnet-howto-migrate-sql.md) for more information.</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="78160-146">Alta disponibilidade e escalabilidade</span><span class="sxs-lookup"><span data-stu-id="78160-146">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="78160-147">Conjuntos de Escala de Máquina Virtual</span><span class="sxs-lookup"><span data-stu-id="78160-147">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="78160-148">Se você quiser verificar se seu aplicativo tem alta disponibilidade e pode ser dimensionado, migre sua imagem da VM para um conjunto de dimensionamento da máquina virtual para melhorar a disponibilidade e a escalabilidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78160-148">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span>  <span data-ttu-id="78160-149">Os Conjuntos de Dimensionamento de VM fornecem a capacidade de usar uma VM existente que você já configurou ou definem um pipeline de compilação para criar uma imagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78160-149">VM Scale Sets provide the ability to use an existing VM you’ve already configured or set up a build pipeline to build an image with your application.</span></span>  

<span data-ttu-id="78160-150">Para começar, confira [Implantar seu aplicativo nos conjuntos de dimensionamento da máquina virtual](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="78160-150">To get started, see [Deploy your application on virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="78160-151">Log Centralizado</span><span class="sxs-lookup"><span data-stu-id="78160-151">Centralized Logging</span></span>
<span data-ttu-id="78160-152">Ao executar seu aplicativo em várias instâncias, considere armazenar os logs em um local centralizado, como o [Armazenamento do Azure](https://docs.microsoft.com/azure/storage/).</span><span class="sxs-lookup"><span data-stu-id="78160-152">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](https://docs.microsoft.com/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="78160-153">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="78160-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="78160-154">Migrar um banco de dados SQL Server para o Azure</span><span class="sxs-lookup"><span data-stu-id="78160-154">Migrate a SQL Server database to Azure</span></span>](dotnet-howto-migrate-sql.md)