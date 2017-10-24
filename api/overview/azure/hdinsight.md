---
title: Bibliotecas do Azure HDInsight para .NET
description: "Referência para bibliotecas do Azure HDInsight para .NET"
keywords: Azure, .NET, SDK, API, HDInsight
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 3f0b6f48d89d582180193f52ce85c328e6bdf8e0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-hdinsight-libraries-for-net"></a><span data-ttu-id="f3341-104">Bibliotecas do Azure HDInsight para .NET</span><span class="sxs-lookup"><span data-stu-id="f3341-104">Azure HDInsight libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f3341-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f3341-105">Overview</span></span>

<span data-ttu-id="f3341-106">O SDK do .NET para o serviço HDInsight fornece classes relacionadas a criação, configuração, envio e monitoramento de trabalhos de Hadoop gerenciados por um serviço Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="f3341-106">The HDInsight Service .NET SDK provides classes that relate to the creation, configuration, submission, and monitoring of Hadoop jobs managed by an Azure HDInsight Service.</span></span> <span data-ttu-id="f3341-107">Além disso, ele fornece classes para gerenciar assinaturas do Azure usando serviço HDInsight e configurar clusters, contas de armazenamento e outros ativos associados aos clusters HDInsight que são gerenciados por uma assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="f3341-107">In addition, it provides classes to manage Azure subscriptions using the HDInsight Service and to configure the clusters, storage accounts, and other assets associated with the HDInsight clusters that are managed by an Azure subscription.</span></span>

## <a name="management-libraries"></a><span data-ttu-id="f3341-108">Bibliotecas de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f3341-108">Management libraries</span></span>

### <a name="jobs"></a><span data-ttu-id="f3341-109">Trabalhos</span><span class="sxs-lookup"><span data-stu-id="f3341-109">Jobs</span></span>

<span data-ttu-id="f3341-110">Use o SDK de cliente do Azure HDInsight para criar, gerenciar e monitorar trabalhos em um cluster Hadoop.</span><span class="sxs-lookup"><span data-stu-id="f3341-110">Use the Azure HDInsight client SDK to create, manage, and monitor jobs on a Hadoop cluster.</span></span> 

<span data-ttu-id="f3341-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f3341-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f3341-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3341-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a><span data-ttu-id="f3341-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f3341-113">Code Example</span></span>

<span data-ttu-id="f3341-114">Este exemplo executa um trabalho de Hive em um cluster Hadoop.</span><span class="sxs-lookup"><span data-stu-id="f3341-114">This example runs a Hive job in a Hadoop cluster.</span></span>

```csharp
HDInsightJobManagementClient managementClient = new HDInsightJobManagementClient(clusterUri, credentials);

Dictionary<string, string> defines = new Dictionary<string, string> {
    { "hive.execution.engine", "tez" },
    { "hive.exec.reducers.max", "1" }
};
List<string> arguments = new List<string> { { "argA" }, { "argB" } };
HiveJobSubmissionParameters parameters = new HiveJobSubmissionParameters
{
    Query = "SHOW TABLES",
    Defines = defines,
    Arguments = arguments
};

JobSubmissionResponse jobResponse = managementClient.JobManagement.SubmitHiveJob(parameters);
```

### <a name="hdinsight"></a><span data-ttu-id="f3341-115">HDInsight</span><span class="sxs-lookup"><span data-stu-id="f3341-115">HDInsight</span></span>

<span data-ttu-id="f3341-116">Use o gerenciamento de HDInsight do Azure SDK para criar, gerenciar, iniciar, parar e dimensionar clusters Hadoop.</span><span class="sxs-lookup"><span data-stu-id="f3341-116">Use the Azure HDInsight management SDK to create, manage, start, stop, and scale Hadoop clusters.</span></span>

<span data-ttu-id="f3341-117">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f3341-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f3341-118">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3341-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a><span data-ttu-id="f3341-119">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f3341-119">Code Example</span></span>

<span data-ttu-id="f3341-120">Este exemplo cria um cluster HDInsight Linux Hadoop de dois nós com um armazenamento de Blobs do Azure existente.</span><span class="sxs-lookup"><span data-stu-id="f3341-120">This example creates an HDInsight two node Linux Hadoop cluster with an existing Azure Blob Storage.</span></span>

```csharp
HDInsightManagementClient managementClient = new HDInsightManagementClient(authToken);
// Set parameters for the new cluster
ClusterCreateParameters parameters = new ClusterCreateParameters
{
    ClusterSizeInNodes = 2,
    UserName = "admin",
    Password = "<Enter HTTP User Password>",
    ClusterType = "Hadoop",
    OSType = OSType.Linux,
    Version = "3.5",
    // Use an Azure storage account as the default storage
    DefaultStorageInfo = new AzureStorageInfo("<StorageAccount>", "<StorageKey>", "<BlobContainerName>"),
    Location = "EAST US 2",
    SshUserName = "sshuser",
    SshPassword = "<Enter SSH User Password>",
};

// Create the cluster
managementClient.Clusters.Create("<ExistingResourceGroupName>", "<NewClusterName>", parameters);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3341-121">Explorar as APIs de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f3341-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a><span data-ttu-id="f3341-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f3341-122">Samples</span></span>

- [<span data-ttu-id="f3341-123">Criação do cluster</span><span class="sxs-lookup"><span data-stu-id="f3341-123">Cluster creation</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [<span data-ttu-id="f3341-124">Gerenciamento de clusters</span><span class="sxs-lookup"><span data-stu-id="f3341-124">Cluster management</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [<span data-ttu-id="f3341-125">Executar trabalhos de Hive</span><span class="sxs-lookup"><span data-stu-id="f3341-125">Run Hive jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [<span data-ttu-id="f3341-126">Executar trabalhos de Pig</span><span class="sxs-lookup"><span data-stu-id="f3341-126">Run Pig jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [<span data-ttu-id="f3341-127">Mais trabalhos</span><span class="sxs-lookup"><span data-stu-id="f3341-127">More jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

<span data-ttu-id="f3341-128">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) de exemplos do Banco de Dados SQL.</span><span class="sxs-lookup"><span data-stu-id="f3341-128">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) of Azure SQL Database samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
