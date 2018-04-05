---
title: APIs do .NET do Azure
description: Visão geral das APIs do Azure para .NET
keywords: Azure, .NET, SDK, API, o NuGet, bibliotecas, pacotes
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 26360a516220ca9d3e8901e60cb23ecbd02863cd
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="azure-net-apis"></a><span data-ttu-id="4ba26-104">APIs do .NET do Azure</span><span class="sxs-lookup"><span data-stu-id="4ba26-104">Azure .NET APIs</span></span>

<span data-ttu-id="4ba26-105">As APIs do .NET do Azure permitem que você use serviços Azure e gerencie recursos do Azure no código do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ba26-105">The Azure .NET APIs let you use Azure services and manage Azure resources from your application code.</span></span> <span data-ttu-id="4ba26-106">As APIs estão disponíveis como [pacotes NuGet](/dotnet/api/overview/azure/) para uso em seus projetos .NET.</span><span class="sxs-lookup"><span data-stu-id="4ba26-106">The APIs are available as [NuGet packages](/dotnet/api/overview/azure/) for use in your .NET projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="4ba26-107">Gerenciar recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="4ba26-107">Manage Azure resources</span></span>

<span data-ttu-id="4ba26-108">As bibliotecas do Azure para .NET permitem criar e gerenciar recursos do Azure em aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="4ba26-108">The Azure libraries for .NET let you create and manage Azure resources from your .NET applications.</span></span>

<span data-ttu-id="4ba26-109">Muitos dos pacotes de gerenciamento de recursos do Azure têm uma interface [fluente](dotnet-sdk-azure-concepts.md) para configurar recursos exatamente de acordo com suas especificações.</span><span class="sxs-lookup"><span data-stu-id="4ba26-109">Many of the packages for managing Azure resources have a [fluent](dotnet-sdk-azure-concepts.md) interface to configure resources exactly to your specifications.</span></span> <span data-ttu-id="4ba26-110">Por exemplo, para criar uma VM Windows, você deve escrever o código abaixo:</span><span class="sxs-lookup"><span data-stu-id="4ba26-110">For example, to create a Windows VM you would write the following code:</span></span>

```csharp
var windowsVM = azure.VirtualMachines.Define(windowsVmName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername(username)
    .WithAdminPassword(password)
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
 ```

<span data-ttu-id="4ba26-111">Examine a [lista de serviços .NET](/dotnet/api/overview/azure/) para começar a usar as bibliotecas em seus projetos imediatamente.</span><span class="sxs-lookup"><span data-stu-id="4ba26-111">Review the [.NET service list](/dotnet/api/overview/azure/) to start using the libraries immediately with your projects.</span></span> <span data-ttu-id="4ba26-112">Em seguida, leia o [artigo de introdução](dotnet-sdk-azure-get-started.md) para configurar a autenticação e executar o código de exemplo em sua própria assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="4ba26-112">Then read the [get started article](dotnet-sdk-azure-get-started.md) to set up authentication and run sample code against your own Azure subscription.</span></span>  <span data-ttu-id="4ba26-113">O [artigo de conceitos](dotnet-sdk-azure-concepts.md) mostra as convenções que o SDK usa e como aproveitá-las para simplificar o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ba26-113">The [concepts article](dotnet-sdk-azure-concepts.md) goes into the conventions the SDK uses and how to leverage them to simplify your application code.</span></span> <span data-ttu-id="4ba26-114">Novos recursos, alterações significativas e instruções de migração estão disponíveis nas [notas de versão](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="4ba26-114">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

## <a name="consume-azure-services"></a><span data-ttu-id="4ba26-115">Consumir serviços do Azure</span><span class="sxs-lookup"><span data-stu-id="4ba26-115">Consume Azure services</span></span>

<span data-ttu-id="4ba26-116">Além de usar as APIs do .NET para criar e gerenciar programaticamente os recursos no Azure, você pode também usar APIs do .NET para conectar seus aplicativos a esses recursos e usá-los no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4ba26-116">In addition to using .NET APIs to create and programmatically manage resources within Azure, you can also then use .NET APIs to connect your applications to these resources and use them at runtime.</span></span>  <span data-ttu-id="4ba26-117">Por exemplo, você pode se conectar a um Banco de Dados SQL ou armazenar dados no Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="4ba26-117">For example, you might connect to a SQL Database or store data within Azure Storage.</span></span>  <span data-ttu-id="4ba26-118">Você pode identificar qual pacote de NuGet será usado para um determinado serviço do Azure navegando nossa [lista completa de APIs de serviço](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="4ba26-118">You can identify which NuGet package to use for a particular Azure service by browsing our [full list of service APIs](/dotnet/api/overview/azure/).</span></span>  

## <a name="samples"></a><span data-ttu-id="4ba26-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4ba26-119">Samples</span></span>

<span data-ttu-id="4ba26-120">Os exemplos a seguir abordam tarefas comuns de automação com as bibliotecas do Azure para .NET:</span><span class="sxs-lookup"><span data-stu-id="4ba26-120">The following samples cover common automation tasks with the Azure libraries for .NET:</span></span>

- [<span data-ttu-id="4ba26-121">Máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="4ba26-121">Virtual machines</span></span>](dotnet-sdk-azure-virtual-machine-samples.md)
- [<span data-ttu-id="4ba26-122">Aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="4ba26-122">Web apps</span></span>](dotnet-sdk-azure-web-apps-samples.md)
- [<span data-ttu-id="4ba26-123">Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="4ba26-123">SQL Database</span></span>](dotnet-sdk-azure-sql-database-samples.md)

<span data-ttu-id="4ba26-124">Uma [referência](/dotnet/api/overview/azure/?view=azure-dotnet) unificada está disponível para todos os pacotes nas bibliotecas de serviço e de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="4ba26-124">A unified [reference](/dotnet/api/overview/azure/?view=azure-dotnet) is available for all packages in both the service and management libraries.</span></span> <span data-ttu-id="4ba26-125">Novos recursos, alterações significativas e instruções de migração estão disponíveis nas [notas de versão](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="4ba26-125">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

[!include[Contribute and community](includes/contribute.md)]