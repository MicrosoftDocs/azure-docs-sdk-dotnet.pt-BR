---
title: Bibliotecas do Lote do Azure para .NET
description: Referência para bibliotecas do Lote do Azure para .NET
keywords: Azure, .NET, SDK, API, Lote
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: batch
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 79ca70e5d0f3d5555c8a691da6dbcc1e6a55ab0b
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2017
ms.locfileid: "23487259"
---
# <a name="azure-batch-libraries-for-net"></a><span data-ttu-id="8887f-104">Bibliotecas do Lote do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="8887f-104">Azure Batch libraries for .NET</span></span>

<span data-ttu-id="8887f-105">O Lote do Azure é um serviço de plataforma para execução de aplicativos paralelos em grande escala e aplicativos HPC (computação de alto desempenho) com eficiência na nuvem.</span><span class="sxs-lookup"><span data-stu-id="8887f-105">Azure Batch is a platform service for running large-scale parallel and high-performance computing (HPC) applications efficiently in the cloud.</span></span> <span data-ttu-id="8887f-106">O Lote do Azure agenda o trabalho de computação intensiva para executar em uma coleção gerenciada de máquinas virtuais e que pode dimensionar automaticamente os recursos de computação para atender às necessidades dos trabalhos.</span><span class="sxs-lookup"><span data-stu-id="8887f-106">Azure Batch schedules compute-intensive work to run on a managed collection of virtual machines, and can automatically scale compute resources to meet the needs of your jobs.</span></span>

<span data-ttu-id="8887f-107">Com o Lote do Azure, você pode definir facilmente os recursos de computação do Azure para executar os aplicativos em paralelo e em escala.</span><span class="sxs-lookup"><span data-stu-id="8887f-107">With Azure Batch, you can easily define Azure compute resources to execute your applications in parallel, and at scale.</span></span> <span data-ttu-id="8887f-108">Não é necessário criar, configurar e gerenciar manualmente um cluster HPC, máquinas virtuais, redes virtuais ou um trabalho e infraestrutura de agendamento de tarefas complexos.</span><span class="sxs-lookup"><span data-stu-id="8887f-108">There's no need to manually create, configure, and manage an HPC cluster, individual virtual machines, virtual networks, or a complex job and task scheduling infrastructure.</span></span> <span data-ttu-id="8887f-109">O Lote do Azure automatiza ou simplifica essas tarefas para você.</span><span class="sxs-lookup"><span data-stu-id="8887f-109">Azure Batch automates or simplifies these tasks for you.</span></span>

<span data-ttu-id="8887f-110">Leia mais sobre como [executar cargas de trabalho intrinsecamente paralelas com o Lote](/azure/batch/batch-technical-overview).</span><span class="sxs-lookup"><span data-stu-id="8887f-110">Read more about how to [run intrinsically parallel workloads with Batch](/azure/batch/batch-technical-overview).</span></span> <span data-ttu-id="8887f-111">Você também pode aprender a [criar soluções com a biblioteca de cliente do Lote para .NET](/azure/batch/batch-dotnet-get-started).</span><span class="sxs-lookup"><span data-stu-id="8887f-111">You can also learn how to [get started building solutions with the Batch client library for .NET](/azure/batch/batch-dotnet-get-started).</span></span> <span data-ttu-id="8887f-112">Saiba como [gerenciar contas e cotas do Lote com a biblioteca de gerenciamento do Lote para .NET](/azure/batch/batch-management-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8887f-112">Discover how to [manage Batch accounts and quotas with the Batch Management library for .NET](/azure/batch/batch-management-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="8887f-113">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="8887f-113">Client library</span></span>

<span data-ttu-id="8887f-114">Use a biblioteca de cliente para executar cargas de trabalho paralelas com o Lote.</span><span class="sxs-lookup"><span data-stu-id="8887f-114">Use the client library to run parallel workloads with Batch.</span></span>

<span data-ttu-id="8887f-115">Instale o [pacote NuGet](https://www.nuget.org/packages/Azure.Batch) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8887f-115">Install the [NuGet package](https://www.nuget.org/packages/Azure.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8887f-116">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8887f-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Azure.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="8887f-117">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="8887f-117">.NET Core CLI</span></span>

```bash
dotnet add package Azure.Batch
```

### <a name="example"></a><span data-ttu-id="8887f-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8887f-118">Example</span></span>

<span data-ttu-id="8887f-119">O exemplo a seguir usa o SDK do cliente a fim de criar um trabalho para execução no Lote do Azure.</span><span class="sxs-lookup"><span data-stu-id="8887f-119">The following example uses the client SDK to create a job to run in Azure Batch.</span></span>

```csharp
/*
using Microsoft.Azure.Batch.Auth;
using Microsoft.Azure.Batch;
*/
BatchSharedKeyCredentials credentials = new BatchSharedKeyCredentials(batchUrl, accountName, accountKey);
using (BatchClient batchClient = await BatchClient.OpenAsync(credentials))
{
    //set up pool specification and information along with resource files here
    JobManagerTask jobManagerTask = new JobManagerTask()
    {
        ResourceFiles = jobManagerResourceFiles,
        CommandLine = Constants.JobManagerExecutable,

        //Determines if the job should terminate when the job manager process exits.
        KillJobOnCompletion = true,
        Id = jobManagerTaskId
    };

    string jobId = Environment.GetEnvironmentVariable("USERNAME") + DateTime.UtcNow.ToString("yyyyMMdd-HHmmss");

    CloudJob unboundJob = batchClient.JobOperations.CreateJob(jobId, poolInformation);
    unboundJob.JobManagerTask = jobManagerTask;

    // now interact with the job ...
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="8887f-120">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="8887f-120">Explore the client APIs</span></span>](/dotnet/api/overview/azure/batch/client)

## <a name="management-library"></a><span data-ttu-id="8887f-121">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="8887f-121">Management library</span></span>

<span data-ttu-id="8887f-122">Use a biblioteca de gerenciamento para gerenciar programaticamente contas, cotas e pacotes de aplicativos do Lote.</span><span class="sxs-lookup"><span data-stu-id="8887f-122">Use the management library to programmatically manage Batch accounts, quotas, and application packages.</span></span>

<span data-ttu-id="8887f-123">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8887f-123">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8887f-124">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8887f-124">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="8887f-125">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="8887f-125">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Batch
```

### <a name="example"></a><span data-ttu-id="8887f-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8887f-126">Example</span></span>

<span data-ttu-id="8887f-127">O exemplo a seguir recupera a cota para a assinatura, cria uma conta e regenera a chave de conta principal.</span><span class="sxs-lookup"><span data-stu-id="8887f-127">The following example retrieves the quota for the subscription, creates an account, and regenerates the primary account key.</span></span>

```csharp
/*
using Microsoft.Azure.Management.Batch;
using Microsoft.Azure.Management.Batch.Models;
using Microsoft.Rest;
*/
using (BatchManagementClient batchManagementClient = new BatchManagementClient(new TokenCredentials(accessToken)))
{
    batchManagementClient.SubscriptionId = subscriptionId;

    // Get the account quota for the subscription
    BatchLocationQuota quotaResponse = await batchManagementClient.Location.GetQuotasAsync(location);
    Console.WriteLine("Your subscription can create {0} account(s) in the {1} region.", quotaResponse.AccountQuota, location);

    // Create account
    await batchManagementClient.BatchAccount.CreateAsync(ResourceGroupName, accountName, 
        new BatchAccountCreateParameters() { Location = location });

    // Regenerate primary account key
    BatchAccountKeys newKeys = await batchManagementClient.BatchAccount.RegenerateKeyAsync(
        ResourceGroupName, account.Name, AccountKeyType.Primary);
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="8887f-128">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="8887f-128">Explore the management APIs</span></span>](/dotnet/api/overview/azure/batch/management)

## <a name="samples"></a><span data-ttu-id="8887f-129">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8887f-129">Samples</span></span>

* [<span data-ttu-id="8887f-130">Cliente do Lote do Azure e SDK de gerenciamento para exemplos do .NET</span><span class="sxs-lookup"><span data-stu-id="8887f-130">Azure Batch Client and Management SDK for .NET Samples</span></span>](https://github.com/Azure/azure-batch-samples/tree/master/CSharp)

<span data-ttu-id="8887f-131">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8887f-131">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
