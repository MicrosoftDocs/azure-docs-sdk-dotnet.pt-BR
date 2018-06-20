---
title: Bibliotecas do Azure HDInsight para .NET
description: Referência para bibliotecas do Azure HDInsight para .NET
keywords: Azure, .NET, SDK, API, HDInsight
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: hd-insight
ms.custom: devcenter, svc-overview
ms.openlocfilehash: da9023ab4e6106754d48acb31cda58cdb358f5cb
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2017
ms.locfileid: "23486949"
---
# <a name="azure-hdinsight-libraries-for-net"></a>Bibliotecas do Azure HDInsight para .NET

## <a name="overview"></a>Visão geral

O SDK do .NET para o serviço HDInsight fornece classes relacionadas a criação, configuração, envio e monitoramento de trabalhos de Hadoop gerenciados por um serviço Azure HDInsight. Além disso, ele fornece classes para gerenciar assinaturas do Azure usando serviço HDInsight e configurar clusters, contas de armazenamento e outros ativos associados aos clusters HDInsight que são gerenciados por uma assinatura do Azure.

## <a name="management-libraries"></a>Bibliotecas de gerenciamento

### <a name="jobs"></a>Trabalhos

Use o SDK de cliente do Azure HDInsight para criar, gerenciar e monitorar trabalhos em um cluster Hadoop. 

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a>Exemplo de código

Este exemplo executa um trabalho de Hive em um cluster Hadoop.

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

### <a name="hdinsight"></a>HDInsight

Use o gerenciamento de HDInsight do Azure SDK para criar, gerenciar, iniciar, parar e dimensionar clusters Hadoop.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a>Exemplo de código

Este exemplo cria um cluster HDInsight Linux Hadoop de dois nós com um armazenamento de Blobs do Azure existente.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a>Exemplos

- [Criação do cluster](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [Gerenciamento de clusters](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [Executar trabalhos de Hive](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [Executar trabalhos de Pig](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [Mais trabalhos](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) de exemplos do Banco de Dados SQL.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
