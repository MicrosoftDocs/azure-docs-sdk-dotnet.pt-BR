---
title: APIs do .NET do Azure
description: Visão geral das APIs do Azure para .NET
ms.date: 10/19/2017
ms.openlocfilehash: 04997caa99ed60db6ad98cabbc72b36bfbf99f4d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190129"
---
# <a name="azure-net-apis"></a><span data-ttu-id="efb6f-103">APIs do .NET do Azure</span><span class="sxs-lookup"><span data-stu-id="efb6f-103">Azure .NET APIs</span></span>

<span data-ttu-id="efb6f-104">As APIs do .NET do Azure permitem que você use serviços Azure e gerencie recursos do Azure no código do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efb6f-104">The Azure .NET APIs let you use Azure services and manage Azure resources from your application code.</span></span> <span data-ttu-id="efb6f-105">As APIs estão disponíveis como [pacotes NuGet](/dotnet/api/overview/azure/) para uso em seus projetos .NET.</span><span class="sxs-lookup"><span data-stu-id="efb6f-105">The APIs are available as [NuGet packages](/dotnet/api/overview/azure/) for use in your .NET projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="efb6f-106">Gerenciar recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="efb6f-106">Manage Azure resources</span></span>

<span data-ttu-id="efb6f-107">As bibliotecas do Azure para .NET permitem criar e gerenciar recursos do Azure em aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="efb6f-107">The Azure libraries for .NET let you create and manage Azure resources from your .NET applications.</span></span>

<span data-ttu-id="efb6f-108">Muitos dos pacotes de gerenciamento de recursos do Azure têm uma interface [fluente](dotnet-sdk-azure-concepts.md) para configurar recursos exatamente de acordo com suas especificações.</span><span class="sxs-lookup"><span data-stu-id="efb6f-108">Many of the packages for managing Azure resources have a [fluent](dotnet-sdk-azure-concepts.md) interface to configure resources exactly to your specifications.</span></span> <span data-ttu-id="efb6f-109">Por exemplo, para criar uma VM Windows, você deve escrever o código abaixo:</span><span class="sxs-lookup"><span data-stu-id="efb6f-109">For example, to create a Windows VM you would write the following code:</span></span>

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

<span data-ttu-id="efb6f-110">Examine a [lista de serviços .NET](/dotnet/api/overview/azure/) para começar a usar as bibliotecas em seus projetos imediatamente.</span><span class="sxs-lookup"><span data-stu-id="efb6f-110">Review the [.NET service list](/dotnet/api/overview/azure/) to start using the libraries immediately with your projects.</span></span> <span data-ttu-id="efb6f-111">Em seguida, leia o [artigo de introdução](dotnet-sdk-azure-get-started.md) para configurar a autenticação e executar o código de exemplo em sua própria assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="efb6f-111">Then read the [get started article](dotnet-sdk-azure-get-started.md) to set up authentication and run sample code against your own Azure subscription.</span></span>  <span data-ttu-id="efb6f-112">O [artigo de conceitos](dotnet-sdk-azure-concepts.md) mostra as convenções que o SDK usa e como aproveitá-las para simplificar o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efb6f-112">The [concepts article](dotnet-sdk-azure-concepts.md) goes into the conventions the SDK uses and how to leverage them to simplify your application code.</span></span> <span data-ttu-id="efb6f-113">Novos recursos, alterações significativas e instruções de migração estão disponíveis nas [notas de versão](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="efb6f-113">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

## <a name="consume-azure-services"></a><span data-ttu-id="efb6f-114">Consumir serviços do Azure</span><span class="sxs-lookup"><span data-stu-id="efb6f-114">Consume Azure services</span></span>

<span data-ttu-id="efb6f-115">Além de usar as APIs do .NET para criar e gerenciar programaticamente os recursos no Azure, você pode também usar APIs do .NET para conectar seus aplicativos a esses recursos e usá-los no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="efb6f-115">In addition to using .NET APIs to create and programmatically manage resources within Azure, you can also then use .NET APIs to connect your applications to these resources and use them at runtime.</span></span>  <span data-ttu-id="efb6f-116">Por exemplo, você pode se conectar a um Banco de Dados SQL ou armazenar dados no Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="efb6f-116">For example, you might connect to a SQL Database or store data within Azure Storage.</span></span>  <span data-ttu-id="efb6f-117">Você pode identificar qual pacote de NuGet será usado para um determinado serviço do Azure navegando nossa [lista completa de APIs de serviço](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="efb6f-117">You can identify which NuGet package to use for a particular Azure service by browsing our [full list of service APIs](/dotnet/api/overview/azure/).</span></span>  

## <a name="samples"></a><span data-ttu-id="efb6f-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="efb6f-118">Samples</span></span>

<span data-ttu-id="efb6f-119">Os exemplos a seguir abordam tarefas comuns de automação com as bibliotecas do Azure para .NET:</span><span class="sxs-lookup"><span data-stu-id="efb6f-119">The following samples cover common automation tasks with the Azure libraries for .NET:</span></span>

- [<span data-ttu-id="efb6f-120">Máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="efb6f-120">Virtual machines</span></span>](dotnet-sdk-azure-virtual-machine-samples.md)
- [<span data-ttu-id="efb6f-121">Aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="efb6f-121">Web apps</span></span>](dotnet-sdk-azure-web-apps-samples.md)
- [<span data-ttu-id="efb6f-122">Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="efb6f-122">SQL Database</span></span>](dotnet-sdk-azure-sql-database-samples.md)

<span data-ttu-id="efb6f-123">Uma [referência](/dotnet/api/overview/azure/?view=azure-dotnet) unificada está disponível para todos os pacotes nas bibliotecas de serviço e de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="efb6f-123">A unified [reference](/dotnet/api/overview/azure/?view=azure-dotnet) is available for all packages in both the service and management libraries.</span></span> <span data-ttu-id="efb6f-124">Novos recursos, alterações significativas e instruções de migração estão disponíveis nas [notas de versão](dotnet-sdk-azure-release-notes.md).</span><span class="sxs-lookup"><span data-stu-id="efb6f-124">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

[!include[Contribute and community](includes/contribute.md)]