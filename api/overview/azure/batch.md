---
title: Bibliotecas do Lote do Azure para .NET
description: "Referência para bibliotecas do Lote do Azure para .NET"
keywords: Azure, .NET, SDK, API, Lote
author: camsoper
ms.author: casoper
manager: douge
ms.date: 08/01/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 753721d430de0577c0bc1dd3774d728783a3bfee
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-batch-libraries-for-net"></a>Bibliotecas do Lote do Azure para .NET

O Lote do Azure é um serviço de plataforma para execução de aplicativos paralelos em grande escala e aplicativos HPC (computação de alto desempenho) com eficiência na nuvem. O Lote do Azure agenda o trabalho de computação intensiva para executar em uma coleção gerenciada de máquinas virtuais e que pode dimensionar automaticamente os recursos de computação para atender às necessidades dos trabalhos.

Com o Lote do Azure, você pode definir facilmente os recursos de computação do Azure para executar os aplicativos em paralelo e em escala. Não é necessário criar, configurar e gerenciar manualmente um cluster HPC, máquinas virtuais, redes virtuais ou um trabalho e infraestrutura de agendamento de tarefas complexos. O Lote do Azure automatiza ou simplifica essas tarefas para você.

Leia mais sobre como [executar cargas de trabalho intrinsecamente paralelas com o Lote](/azure/batch/batch-technical-overview). Você também pode aprender a [criar soluções com a biblioteca de cliente do Lote para .NET](/azure/batch/batch-dotnet-get-started). Saiba como [gerenciar contas e cotas do Lote com a biblioteca de gerenciamento do Lote para .NET](/azure/batch/batch-management-dotnet).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de cliente para executar cargas de trabalho paralelas com o Lote.

Instale o [pacote NuGet](https://www.nuget.org/packages/Azure.Batch) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Azure.Batch
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Azure.Batch
```

### <a name="example"></a>Exemplo

O exemplo a seguir usa o SDK do cliente a fim de criar um trabalho para execução no Lote do Azure.

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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/batch/client)

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para gerenciar programaticamente contas, cotas e pacotes de aplicativos do Lote.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Batch
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.Management.Batch
```

### <a name="example"></a>Exemplo

O exemplo a seguir recupera a cota para a assinatura, cria uma conta e regenera a chave de conta principal.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/batch/management)

## <a name="samples"></a>Exemplos

* [Cliente do Lote do Azure e SDK de gerenciamento para exemplos do .NET](https://github.com/Azure/azure-batch-samples/tree/master/CSharp)

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
