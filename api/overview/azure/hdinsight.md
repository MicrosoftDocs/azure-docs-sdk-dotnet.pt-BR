---
title: SDK .NET do Azure HDInsight
description: Referência para SDK .NET do Azure HDInsight
ms.date: 9/19/2018
ms.topic: reference
ms.service: hdinsight
ms.openlocfilehash: 35e2c8c07fb2b86b2d0ae9be4f855e369c1aa86d
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348198"
---
# <a name="azure-hdinsight-net-sdk"></a><span data-ttu-id="5fe96-103">SDK .NET do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="5fe96-103">Azure HDInsight .NET SDK</span></span>

## <a name="azure-hdinsight-libraries-for-net-2x"></a><span data-ttu-id="5fe96-104">Bibliotecas do Azure HDInsight para .NET 2.X</span><span class="sxs-lookup"><span data-stu-id="5fe96-104">Azure HDInsight libraries for .NET 2.X</span></span>

## <a name="overview"></a><span data-ttu-id="5fe96-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5fe96-105">Overview</span></span>

<span data-ttu-id="5fe96-106">O SDK do .NET para o serviço HDInsight fornece classes relacionadas a criação, configuração, envio e monitoramento de trabalhos de Hadoop gerenciados por um serviço Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="5fe96-106">The HDInsight Service .NET SDK provides classes that relate to the creation, configuration, submission, and monitoring of Hadoop jobs managed by an Azure HDInsight Service.</span></span> <span data-ttu-id="5fe96-107">Além disso, ele fornece classes para gerenciar assinaturas do Azure usando serviço HDInsight e configurar clusters, contas de armazenamento e outros ativos associados aos clusters HDInsight que são gerenciados por uma assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="5fe96-107">In addition, it provides classes to manage Azure subscriptions using the HDInsight Service and to configure the clusters, storage accounts, and other assets associated with the HDInsight clusters that are managed by an Azure subscription.</span></span>

## <a name="management-libraries"></a><span data-ttu-id="5fe96-108">Bibliotecas de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5fe96-108">Management libraries</span></span>

### <a name="jobs"></a><span data-ttu-id="5fe96-109">Trabalhos</span><span class="sxs-lookup"><span data-stu-id="5fe96-109">Jobs</span></span>

<span data-ttu-id="5fe96-110">Use o SDK de cliente do Azure HDInsight para criar, gerenciar e monitorar trabalhos em um cluster Hadoop.</span><span class="sxs-lookup"><span data-stu-id="5fe96-110">Use the Azure HDInsight client SDK to create, manage, and monitor jobs on a Hadoop cluster.</span></span> 

<span data-ttu-id="5fe96-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5fe96-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5fe96-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fe96-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a><span data-ttu-id="5fe96-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5fe96-113">Code Example</span></span>

<span data-ttu-id="5fe96-114">Este exemplo executa um trabalho de Hive em um cluster Hadoop.</span><span class="sxs-lookup"><span data-stu-id="5fe96-114">This example runs a Hive job in a Hadoop cluster.</span></span>

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

### <a name="hdinsight"></a><span data-ttu-id="5fe96-115">HDInsight</span><span class="sxs-lookup"><span data-stu-id="5fe96-115">HDInsight</span></span>

<span data-ttu-id="5fe96-116">Use o gerenciamento de HDInsight do Azure SDK para criar, gerenciar, iniciar, parar e dimensionar clusters Hadoop.</span><span class="sxs-lookup"><span data-stu-id="5fe96-116">Use the Azure HDInsight management SDK to create, manage, start, stop, and scale Hadoop clusters.</span></span>

<span data-ttu-id="5fe96-117">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5fe96-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5fe96-118">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fe96-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a><span data-ttu-id="5fe96-119">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5fe96-119">Code Example</span></span>

<span data-ttu-id="5fe96-120">Este exemplo cria um cluster HDInsight Linux Hadoop de dois nós com um armazenamento de Blobs do Azure existente.</span><span class="sxs-lookup"><span data-stu-id="5fe96-120">This example creates an HDInsight two node Linux Hadoop cluster with an existing Azure Blob Storage.</span></span>

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
> [<span data-ttu-id="5fe96-121">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5fe96-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a><span data-ttu-id="5fe96-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5fe96-122">Samples</span></span>

- [<span data-ttu-id="5fe96-123">Criação do cluster</span><span class="sxs-lookup"><span data-stu-id="5fe96-123">Cluster creation</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [<span data-ttu-id="5fe96-124">Gerenciamento de clusters</span><span class="sxs-lookup"><span data-stu-id="5fe96-124">Cluster management</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [<span data-ttu-id="5fe96-125">Executar trabalhos de Hive</span><span class="sxs-lookup"><span data-stu-id="5fe96-125">Run Hive jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [<span data-ttu-id="5fe96-126">Executar trabalhos de Pig</span><span class="sxs-lookup"><span data-stu-id="5fe96-126">Run Pig jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [<span data-ttu-id="5fe96-127">Mais trabalhos</span><span class="sxs-lookup"><span data-stu-id="5fe96-127">More jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

<span data-ttu-id="5fe96-128">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) de exemplos do Banco de Dados SQL.</span><span class="sxs-lookup"><span data-stu-id="5fe96-128">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) of Azure SQL Database samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package

## <a name="hdinsight-net-management-sdk-3x-preview"></a><span data-ttu-id="5fe96-129">Versão prévia do SDK 3.X de gerenciamento .NET do HDInsight</span><span class="sxs-lookup"><span data-stu-id="5fe96-129">HDInsight .NET Management SDK 3.X Preview</span></span>

## <a name="overview"></a><span data-ttu-id="5fe96-130">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5fe96-130">Overview</span></span>

<span data-ttu-id="5fe96-131">O SDK .NET do HDInsight oferece classes e métodos que permitem gerenciar os seus clusters do HDInsight.</span><span class="sxs-lookup"><span data-stu-id="5fe96-131">The HDInsight .NET SDK provides classes and methods that allow you to manage your HDInsight clusters.</span></span> <span data-ttu-id="5fe96-132">Inclui operações para criar, excluir, atualizar, listar, redimensionar, executar ações de script, monitorar, obter propriedades dos clusters HDInsight e muito mais.</span><span class="sxs-lookup"><span data-stu-id="5fe96-132">It includes operations to create, delete, update, list, resize, execute script actions, monitor, get properties of HDInsight clusters, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fe96-133">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5fe96-133">Prerequisites</span></span>

* <span data-ttu-id="5fe96-134">Uma conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="5fe96-134">An Azure account.</span></span> <span data-ttu-id="5fe96-135">Se você não tiver uma, [obtenha uma avaliação gratuita](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="5fe96-135">If you don't have one, [get a free trial](https://azure.microsoft.com/free/).</span></span>
* [<span data-ttu-id="5fe96-136">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fe96-136">Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/)

## <a name="sdk-installation"></a><span data-ttu-id="5fe96-137">Instalação do SDK</span><span class="sxs-lookup"><span data-stu-id="5fe96-137">SDK Installation</span></span>

<span data-ttu-id="5fe96-138">No projeto do Visual Studio, abra o Console do Gerenciador de Pacotes clicando em **Ferramentas**, **Gerenciador de Pacotes NuGet** e, em seguida, clique em **Console do Gerenciador de Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="5fe96-138">From your Visual Studio project, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>

<span data-ttu-id="5fe96-139">No Console do Gerenciador de Pacotes, execute os comandos a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fe96-139">In the Package Manager Console, execute the following commands:</span></span>

```
  Install-Package Microsoft.Azure.Management.HDInsight -Version 3.1.0-preview
  Install-Package Microsoft.Azure.Management.Fluent
  Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

## <a name="authentication"></a><span data-ttu-id="5fe96-140">Autenticação</span><span class="sxs-lookup"><span data-stu-id="5fe96-140">Authentication</span></span>

<span data-ttu-id="5fe96-141">O SDK precisa primeiro ser autenticado com a assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="5fe96-141">The SDK first needs to be authenticated with your Azure subscription.</span></span>  <span data-ttu-id="5fe96-142">Siga o exemplo abaixo para criar uma entidade de serviço e use-a para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5fe96-142">Follow the example below to create a service principal and use it to authenticate.</span></span> <span data-ttu-id="5fe96-143">Após isso ser feito, você terá uma instância de um `HDInsightManagementClient`, que contém muitos métodos (destacados nas seções abaixo) que podem ser usados para realizar operações de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="5fe96-143">After this is done, you will have an instance of an `HDInsightManagementClient`, which contains many methods (outlined in below sections) that can be used to perform management operations.</span></span>

> [!NOTE]
> <span data-ttu-id="5fe96-144">Existem outras formas de autenticar além do exemplo abaixo que talvez sejam mais adequadas às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="5fe96-144">There are other ways to authenticate besides the below example that could potentially be better suited for your needs.</span></span> <span data-ttu-id="5fe96-145">Todos os métodos são descritos aqui: [Autenticar com as Bibliotecas do Azure para .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span><span class="sxs-lookup"><span data-stu-id="5fe96-145">All methods are outlined here: [Authenticate with the Azure Libraries for .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span></span>

### <a name="authentication-example-using-a-service-principal"></a><span data-ttu-id="5fe96-146">Exemplo de autenticação usando uma entidade de serviço</span><span class="sxs-lookup"><span data-stu-id="5fe96-146">Authentication Example Using a Service Principal</span></span>

<span data-ttu-id="5fe96-147">Primeiro, faça logon no [Azure Cloud Shell](https://shell.azure.com/bash).</span><span class="sxs-lookup"><span data-stu-id="5fe96-147">First, login to [Azure Cloud Shell](https://shell.azure.com/bash).</span></span> <span data-ttu-id="5fe96-148">Verifique se você está usando atualmente a assinatura na qual deseja a entidade de serviço criada.</span><span class="sxs-lookup"><span data-stu-id="5fe96-148">Verify you are currently using the subscription in which you want the service principal created.</span></span> 

```azurecli-interactive
az account show
```

<span data-ttu-id="5fe96-149">As informações da assinatura são exibidas como JSON.</span><span class="sxs-lookup"><span data-stu-id="5fe96-149">Your subscription information is displayed as JSON.</span></span>

```json
{
  "environmentName": "AzureCloud",
  "id": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "isDefault": true,
  "name": "XXXXXXX",
  "state": "Enabled",
  "tenantId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "user": {
    "cloudShellID": true,
    "name": "XXX@XXX.XXX",
    "type": "user"
  }
}
```

<span data-ttu-id="5fe96-150">Se você não estiver conectado à assinatura correta, selecione a correta executando:</span><span class="sxs-lookup"><span data-stu-id="5fe96-150">If you're not logged into the correct subscription, select the correct one by running:</span></span> 
```azurecli-interactive
az account set -s <name or ID of subscription>
```

> [!IMPORTANT]
> <span data-ttu-id="5fe96-151">Se você já não tiver registrado o Provedor de Recursos do HDInsight através de outro método (tais como criar um cluster do HDInsight através do portal do Azure), você precisa fazer isso uma vez antes de poder autenticar.</span><span class="sxs-lookup"><span data-stu-id="5fe96-151">If you have not already registered the HDInsight Resource Provider by another method (such as by creating an HDInsight Cluster through the Azure Portal), you need to do this once before you can authenticate.</span></span> <span data-ttu-id="5fe96-152">Isso também pode ser feito no [Azure Cloud Shell](https://shell.azure.com/bash) executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5fe96-152">This can be done from the [Azure Cloud Shell](https://shell.azure.com/bash) by running the following command:</span></span>
>```azurecli-interactive
>az provider register --namespace Microsoft.HDInsight
>```

<span data-ttu-id="5fe96-153">Em seguida, escolha um nome para a sua entidade de serviço e crie-a com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5fe96-153">Next, choose a name for your service principal and create it with the following command:</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name <Service Principal Name> --sdk-auth
```

<span data-ttu-id="5fe96-154">As informações da entidade de serviço são exibidas como JSON.</span><span class="sxs-lookup"><span data-stu-id="5fe96-154">The service principal information is displayed as JSON.</span></span>

```json
{
  "clientId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "clientSecret": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "subscriptionId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "tenantId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```
<span data-ttu-id="5fe96-155">Copie o trecho abaixo e preencha `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET` e `SUBSCRIPTION_ID` com as cadeias de caracteres do JSON que foi retornado após a execução do comando para criar a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="5fe96-155">Copy the below snippet and fill in `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET`, and `SUBSCRIPTION_ID` with the strings from the JSON that was returned after running the command to create the service principal.</span></span>

```csharp
using Microsoft.Azure.Management.HDInsight;
using Microsoft.Azure.Management.HDInsight.Models;
using Microsoft.Azure.Management.ResourceManager.Fluent;

namespace HDI_SDK_Test
{
    class Program
    {
        static void Main(string[] args)
        {
            // Tenant ID for your Azure Subscription
            var TENANT_ID = "";
            // Your Service Principal App Client ID
            var CLIENT_ID = "";
            // Your Service Principal Client Secret
            var CLIENT_SECRET = "";
            // Azure Subscription ID
            var SUBSCRIPTION_ID = "";

            var credentials = SdkContext.AzureCredentialsFactory
                .FromServicePrincipal(
                CLIENT_ID,
                CLIENT_SECRET,
                TENANT_ID,
                AzureEnvironment.AzureGlobalCloud);

            var client = new HDInsightManagementClient(credentials);
            client.SubscriptionId = SUBSCRIPTION_ID;
        }
    }
}
```


## <a name="cluster-management"></a><span data-ttu-id="5fe96-156">Gerenciamento de clusters</span><span class="sxs-lookup"><span data-stu-id="5fe96-156">Cluster Management</span></span>

> [!NOTE]
> <span data-ttu-id="5fe96-157">Essa seção pressupõe que você já autenticou e criou uma `HDInsightManagementClient` instância e a armazenou em uma variável chamada `client`.</span><span class="sxs-lookup"><span data-stu-id="5fe96-157">This section assumes you have already authenticated and constructed an `HDInsightManagementClient` instance and store it in a variable called `client`.</span></span> <span data-ttu-id="5fe96-158">As instruções para autenticar e obter um `HDInsightManagementClient` podem ser encontradas na seção Autenticação acima.</span><span class="sxs-lookup"><span data-stu-id="5fe96-158">Instructions for authenticating and obtaining an `HDInsightManagementClient` can be found in the Authentication section above.</span></span>

### <a name="create-a-cluster"></a><span data-ttu-id="5fe96-159">Criar um cluster</span><span class="sxs-lookup"><span data-stu-id="5fe96-159">Create a Cluster</span></span>

<span data-ttu-id="5fe96-160">Um novo cluster pode ser criado chamando `client.Clusters.Create()`.</span><span class="sxs-lookup"><span data-stu-id="5fe96-160">A new cluster can be created by calling `client.Clusters.Create()`.</span></span> 

#### <a name="example"></a><span data-ttu-id="5fe96-161">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe96-161">Example</span></span>

<span data-ttu-id="5fe96-162">Este exemplo demonstra como criar um cluster Spark com 2 nós principais e 1 nó de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5fe96-162">This example demonstrates how to create a Spark cluster with 2 head nodes and 1 worker node.</span></span>

> [!NOTE]
> <span data-ttu-id="5fe96-163">Primeiro você precisa criar um grupo de recursos e uma conta de armazenamento, conforme explicado abaixo.</span><span class="sxs-lookup"><span data-stu-id="5fe96-163">You first need to create a Resource Group and Storage Account, as explained below.</span></span> <span data-ttu-id="5fe96-164">Se você já os tiver criado, ignore as próximas etapas.</span><span class="sxs-lookup"><span data-stu-id="5fe96-164">If you have already created these, you can skip these steps.</span></span>

##### <a name="creating-a-resource-group"></a><span data-ttu-id="5fe96-165">Criar um grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="5fe96-165">Creating a Resource Group</span></span>

<span data-ttu-id="5fe96-166">É possível criar um grupo de recursos usando o [Azure Cloud Shell](https://shell.azure.com/bash) executando:</span><span class="sxs-lookup"><span data-stu-id="5fe96-166">You can create a resource group using the [Azure Cloud Shell](https://shell.azure.com/bash) by running</span></span>
```azurecli-interactive
az group create -l <Region Name (i.e. eastus)> --n <Resource Group Name>
```
##### <a name="creating-a-storage-account"></a><span data-ttu-id="5fe96-167">Criar uma conta de armazenamento</span><span class="sxs-lookup"><span data-stu-id="5fe96-167">Creating a Storage Account</span></span>

<span data-ttu-id="5fe96-168">É possível criar uma conta de armazenamento usando o [Azure Cloud Shell](https://shell.azure.com/bash) executando:</span><span class="sxs-lookup"><span data-stu-id="5fe96-168">You can create a storage account using the [Azure Cloud Shell](https://shell.azure.com/bash) by running:</span></span>
```azurecli-interactive
az storage account create -n <Storage Account Name> -g <Existing Resource Group Name> -l <Region Name (i.e. eastus)> --sku <SKU i.e. Standard_LRS>
```
<span data-ttu-id="5fe96-169">Agora execute o comando a seguir para obter a chave para a sua conta de armazenamento (você precisará dela para criar um cluster):</span><span class="sxs-lookup"><span data-stu-id="5fe96-169">Now run the following command to get the key for your storage account (you will need this to create a cluster):</span></span>
```azurecli-interactive
az storage account keys list -n <Storage Account Name>
```
---
<span data-ttu-id="5fe96-170">O trecho do .NET abaixo cria um cluster Spark com 2 nós principais e 1 nó de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5fe96-170">The below .NET snippet creates a Spark cluster with 2 head nodes and 1 worker node.</span></span> <span data-ttu-id="5fe96-171">Preencha as variáveis em branco conforme explicado nos comentários e fique à vontade para alterar outros parâmetros conforme as suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="5fe96-171">Fill in the blank variables as explained in the comments and feel free to change other parameters to suit your specific needs.</span></span>

```csharp
// The name for the cluster you are creating
var clusterName = "";
// The name of your existing Resource Group
var resourceGroupName = "";
// Choose a username
var username = "";
// Choose a password
var password = "";
// Replace <> with the name of your storage account
var storageAccount = "<>.blob.core.windows.net";
// Storage account key you obtained above
var storageAccountKey = "";
// Choose a region
var location = "";
var container = "default";

var parameters = new ClusterCreateParametersExtended
{
    Location = location,
    Tags = new Dictionary<string, string>(),
    Properties = new ClusterCreateProperties
    {
        ClusterVersion = "3.6",
        OsType = OSType.Linux,
        ClusterDefinition = new ClusterDefinition
        {
            Kind = "Hadoop",            
            Configurations = new Dictionary<string, Dictionary<string, string>>()
            {                
                { "gateway", new Dictionary<string, string>
                    {
                        { "restAuthCredential.isEnabled", "true" },
                        { "restAuthCredential.username", username},
                        { "restAuthCredential.password", password}
                    }
                }
            }
        },
        Tier = Tier.Standard,
        ComputeProfile = new ComputeProfile
        {
            Roles = new List<Role>{
                new Role
                {
                    Name = "headnode",
                    TargetInstanceCount = 2,
                    HardwareProfile = new HardwareProfile
                    {
                        VmSize = "Large"
                    },
                    OsProfile = new OsProfile
                    {
                        LinuxOperatingSystemProfile = new LinuxOperatingSystemProfile
                        {
                            Username = username,
                            Password = password
                        }
                    }
                },
                new Role
                {
                    Name = "workernode",
                    TargetInstanceCount = 1,
                    HardwareProfile = new HardwareProfile
                    {
                        VmSize = "Large"
                    },
                    OsProfile = new OsProfile
                    {
                        LinuxOperatingSystemProfile = new LinuxOperatingSystemProfile
                        {
                            Username = username,
                            Password = password
                        }
                    }
                },
            }
        },
        StorageProfile = new StorageProfile
        {
            Storageaccounts = new[]
            {
                new StorageAccount
                {
                    Name = storageAccount,
                    Key = storageAccountKey,
                    Container = container,
                    IsDefault = true
                }
            }
        }
    }
};
client.Clusters.Create(
    resourceGroupName,
    clusterName,
    parameters
);
```

### <a name="get-cluster-details"></a><span data-ttu-id="5fe96-172">Obter detalhes do cluster</span><span class="sxs-lookup"><span data-stu-id="5fe96-172">Get Cluster Details</span></span>

<span data-ttu-id="5fe96-173">Para obter propriedades para um determinado cluster:</span><span class="sxs-lookup"><span data-stu-id="5fe96-173">To get properties for a given cluster:</span></span>

```csharp
client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="5fe96-174">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe96-174">Example</span></span>

<span data-ttu-id="5fe96-175">Você pode usar `get` para confirmar que criou com êxito o seu cluster.</span><span class="sxs-lookup"><span data-stu-id="5fe96-175">You can use `get` to confirm that you have successfully created your cluster.</span></span>

```csharp
var myCluster = client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
Debug.WriteLine(myCluster.Name); //Prints the name of the cluster
Debug.WriteLine(myCluster.Id) //Prints the resource Id of the cluster
```

<span data-ttu-id="5fe96-176">A saída deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="5fe96-176">The output should look like:</span></span>

```
<Cluster Name>
/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/<Resource Group Name>/providers/Microsoft.HDInsight/clusters/<Cluster Name>
```
> [!NOTE]
> <span data-ttu-id="5fe96-177">O valor de retorno de `get`, armazenado na variável `myCluster`, é do tipo `Microsoft.Azure.Management.HDInsight.ModelsCluster`.</span><span class="sxs-lookup"><span data-stu-id="5fe96-177">The return value of `get`, stored in variable `myCluster`, is of type `Microsoft.Azure.Management.HDInsight.ModelsCluster`.</span></span> <span data-ttu-id="5fe96-178">Uma lista completa das propriedades desse objeto pode ser encontrada [aqui](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).</span><span class="sxs-lookup"><span data-stu-id="5fe96-178">A full list of this object's properties can be found [here](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).</span></span>


### <a name="list-clusters"></a><span data-ttu-id="5fe96-179">Listar clusters</span><span class="sxs-lookup"><span data-stu-id="5fe96-179">List Clusters</span></span>

#### <a name="list-clusters-under-the-subscription"></a><span data-ttu-id="5fe96-180">Listar os clusters em uma assinatura</span><span class="sxs-lookup"><span data-stu-id="5fe96-180">List Clusters Under The Subscription</span></span>

```csharp
client.Clusters.List();
```
#### <a name="list-clusters-by-resource-group"></a><span data-ttu-id="5fe96-181">Listar os clusters por grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="5fe96-181">List Clusters By Resource Group</span></span>

```csharp
client.Clusters.ListByResourceGroup("<Resource Group Name>");
```
> [!NOTE]
> <span data-ttu-id="5fe96-182">Ambos `List()` e `ListByResourceGroup()` retornam um objeto `IPage<Cluster>`.</span><span class="sxs-lookup"><span data-stu-id="5fe96-182">Both `List()` and `ListByResourceGroup()` return an `IPage<Cluster>` object.</span></span> <span data-ttu-id="5fe96-183">Para obter a página seguinte, você pode chamar `client.Clusters.ListNext("Next Page Link")`.</span><span class="sxs-lookup"><span data-stu-id="5fe96-183">To get the next page, you can call `client.Clusters.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="5fe96-184">Isso pode ser repetido até que `NextPageLink` seja `null`, conforme mostrado no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="5fe96-184">This can be repeated until `NextPageLink` is `null`, as shown in the example below.</span></span>

#### <a name="example"></a><span data-ttu-id="5fe96-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe96-185">Example</span></span>
<span data-ttu-id="5fe96-186">O exemplo a seguir imprime as propriedades de todos os clusters da assinatura atual:</span><span class="sxs-lookup"><span data-stu-id="5fe96-186">The following example prints the properties of all clusters for the current subscription:</span></span>

```csharp
var clustersPaged = client.Clusters.List();
while (true)
{
  foreach (var cluster in clustersPaged)
  {
    Debug.WriteLine(cluster.Name);
  
}  if (clustersPaged.NextPageLink == null)
  {
    break;
  }
  clustersPaged = client.Clusters.ListNext(clustersPaged.NextPageLink);
}
```

### <a name="delete-a-cluster"></a><span data-ttu-id="5fe96-187">Excluir um cluster</span><span class="sxs-lookup"><span data-stu-id="5fe96-187">Delete a Cluster</span></span>

<span data-ttu-id="5fe96-188">Para excluir um cluster:</span><span class="sxs-lookup"><span data-stu-id="5fe96-188">To delete a cluster:</span></span>

```csharp
client.Clusters.Delete("<Resource Group Name>", "<Cluster Name>");
```

### <a name="update-cluster-tags"></a><span data-ttu-id="5fe96-189">Atualizar marcas de cluster</span><span class="sxs-lookup"><span data-stu-id="5fe96-189">Update Cluster Tags</span></span>

<span data-ttu-id="5fe96-190">É possível atualizar as marcas de um determinado cluster da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5fe96-190">You can update the tags of a given cluster like so:</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(<Dictionary of Tags>));
```
#### <a name="example"></a><span data-ttu-id="5fe96-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe96-191">Example</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(new Dictionary<string, string> { { "tag1Name", "tag1Value" }, { "tag2Name", "tag2Value" } }));
```

### <a name="resize-cluster"></a><span data-ttu-id="5fe96-192">Redimensionar Cluster</span><span class="sxs-lookup"><span data-stu-id="5fe96-192">Resize Cluster</span></span>

<span data-ttu-id="5fe96-193">É possível redimensionar o número de nós de trabalho de determinado cluster especificando um novo tamanho, assim:</span><span class="sxs-lookup"><span data-stu-id="5fe96-193">You can resize a given cluster's number of worker nodes by specifying a new size like so:</span></span>

```csharp
client.Clusters.Resize("<Resource Group Name>", "<Cluster Name>", <Num of Worker Nodes (int)>)
```

## <a name="cluster-monitoring"></a><span data-ttu-id="5fe96-194">Monitoramento do cluster</span><span class="sxs-lookup"><span data-stu-id="5fe96-194">Cluster Monitoring</span></span>

<span data-ttu-id="5fe96-195">O SDK de gerenciamento do HDInsight também pode ser usado para gerenciar o monitoramento dos seus clusters através do Operations Management Suite (OMS).</span><span class="sxs-lookup"><span data-stu-id="5fe96-195">The HDInsight Management SDK can also be used to manage monitoring on your clusters via the Operations Management Suite (OMS).</span></span>

### <a name="enable-oms-monitoring"></a><span data-ttu-id="5fe96-196">Habilitar Monitoramento de OMS</span><span class="sxs-lookup"><span data-stu-id="5fe96-196">Enable OMS Monitoring</span></span>

> [!NOTE]
> <span data-ttu-id="5fe96-197">Para habilitar o Monitoramento de OMS, você deve ter um espaço de trabalho existente do Log Analytics.</span><span class="sxs-lookup"><span data-stu-id="5fe96-197">To enable OMS Monitoring, you must have an existing Log Analytics workspace.</span></span> <span data-ttu-id="5fe96-198">Se você já não tiver criado um, você pode aprender como fazer isso aqui: [Criar um espaço de trabalho do Log Analytics no portal do Azure](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).</span><span class="sxs-lookup"><span data-stu-id="5fe96-198">If you have not already created one, you can learn how to do that here: [Create a Log Analytics workspace in the Azure portal](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).</span></span>

<span data-ttu-id="5fe96-199">Para habilitar o Monitoramento de OMS no seu cluster:</span><span class="sxs-lookup"><span data-stu-id="5fe96-199">To enable OMS Monitoring on your cluster:</span></span>

```csharp
client.Extension.EnableMonitoring("<Resource Group Name", "Cluster Name", new ClusterMonitoringRequest(workspaceId: "<Workspace Id>"));
```

### <a name="view-status-of-oms-monitoring"></a><span data-ttu-id="5fe96-200">Exibir o status do Monitoramento de OMS</span><span class="sxs-lookup"><span data-stu-id="5fe96-200">View Status Of OMS Monitoring</span></span>

<span data-ttu-id="5fe96-201">Para obter o status do OMS no seu cluster:</span><span class="sxs-lookup"><span data-stu-id="5fe96-201">To get the status of OMS on your cluster:</span></span>

```csharp
client.Extension.GetMonitoringStatus("<Resource Group Name", "Cluster Name");
```

### <a name="disable-oms-monitoring"></a><span data-ttu-id="5fe96-202">Desabilitar Monitoramento de OMS</span><span class="sxs-lookup"><span data-stu-id="5fe96-202">Disable OMS Monitoring</span></span>

<span data-ttu-id="5fe96-203">Para desabilitar o OMS no seu cluster:</span><span class="sxs-lookup"><span data-stu-id="5fe96-203">To disable OMS on your cluster:</span></span>

```csharp
client.Extension.DisableMonitoring("<Resource Group Name>", "<Cluster Name>");
```

## <a name="script-actions"></a><span data-ttu-id="5fe96-204">Ações de script</span><span class="sxs-lookup"><span data-stu-id="5fe96-204">Script Actions</span></span>

<span data-ttu-id="5fe96-205">O HDInsight fornece um método de configuração chamado ações de script que chama os scripts personalizados para personalizar o cluster.</span><span class="sxs-lookup"><span data-stu-id="5fe96-205">HDInsight provides a configuration method called script actions that invokes custom scripts to customize the cluster.</span></span>
> [!NOTE]
> <span data-ttu-id="5fe96-206">Mais informações sobre como usar as ações de script podem ser encontradas aqui: [Personalizar clusters HDInsight com base em Linux usando ações de script](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)</span><span class="sxs-lookup"><span data-stu-id="5fe96-206">More information on how to use script actions can be found here: [Customize Linux-based HDInsight clusters using script actions](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)</span></span>

### <a name="execute-script-actions"></a><span data-ttu-id="5fe96-207">Executar ações de script</span><span class="sxs-lookup"><span data-stu-id="5fe96-207">Execute Script Actions</span></span>

<span data-ttu-id="5fe96-208">É possível executar ações de script em um determinado cluster da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5fe96-208">You can execute script actions on a given cluster like so:</span></span>

```csharp
var scriptAction1 = new RuntimeScriptAction("<Script Name>", "<URL To Script>", <List<string> of roles>); //valid roles are "headnode", "workernode", "zookeepernode", and "edgenode"

client.Clusters.ExecuteScriptActions("<Resource Group Name>", "<Cluster Name>", new List<RuntimeScriptAction> { scriptAction1 }, <persistOnSuccess (bool)>); //add more RuntimeScriptActions to the list to execute multiple scripts
```

### <a name="delete-script-action"></a><span data-ttu-id="5fe96-209">Excluir ação de script</span><span class="sxs-lookup"><span data-stu-id="5fe96-209">Delete Script Action</span></span>

<span data-ttu-id="5fe96-210">Para excluir uma ação de script persistente específica em um determinado cluster:</span><span class="sxs-lookup"><span data-stu-id="5fe96-210">To delete a specified persisted script action on a given cluster:</span></span>

```csharp
client.ScriptActions.Delete("<Resource Group Name>", "<Cluster Name>", "<Script Name>");
```

### <a name="list-persisted-script-actions"></a><span data-ttu-id="5fe96-211">Listar ações de script persistentes</span><span class="sxs-lookup"><span data-stu-id="5fe96-211">List Persisted Script Actions</span></span>

> [!NOTE]
> <span data-ttu-id="5fe96-212">`ListPersistedScripts()` e `List()` retornam um objeto `IPage<RuntimeScriptActionDetail>`.</span><span class="sxs-lookup"><span data-stu-id="5fe96-212">`ListPersistedScripts()` and `List()` return an `IPage<RuntimeScriptActionDetail>` object.</span></span> <span data-ttu-id="5fe96-213">Para obter a página seguinte, você pode chamar `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` ou `client.ScriptExecutionHistory.ListNext("Next Page Link")`.</span><span class="sxs-lookup"><span data-stu-id="5fe96-213">To get the next page, you can call `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` or `client.ScriptExecutionHistory.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="5fe96-214">Isso pode ser repetido até que `NextPageLink` seja `null`, conforme mostrado nos exemplos abaixo.</span><span class="sxs-lookup"><span data-stu-id="5fe96-214">This can be repeated until `NextPageLink` is `null`, as shown in the examples below.</span></span>

<span data-ttu-id="5fe96-215">Para listar todas as ações de script persistentes para o cluster especificado:</span><span class="sxs-lookup"><span data-stu-id="5fe96-215">To list all persisted script actions for the specified cluster:</span></span>
```csharp
client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="5fe96-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe96-216">Example</span></span>

```csharp
var scriptsPaged = client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
while (true)
{
    foreach (var script in scriptsPaged)
    {
        Debug.WriteLine(script.Name); //There are other properties of RuntimeScriptActionDetail besides Name, such as Status, Operation, StartTime, EndTime, etc. See reference documentation.
    }
    if (scriptsPaged.NextPageLink == null)
    {
        break;
    }
    scriptsPaged = client.ScriptActions.ListPersistedScriptsNext(scriptsPaged.NextPageLink);
}
```

### <a name="list-all-scripts-execution-history"></a><span data-ttu-id="5fe96-217">Listar o histórico de execução de todos os scripts</span><span class="sxs-lookup"><span data-stu-id="5fe96-217">List All Scripts' Execution History</span></span>

<span data-ttu-id="5fe96-218">Para listar o histórico de execução de todos os scripts para o cluster especificado:</span><span class="sxs-lookup"><span data-stu-id="5fe96-218">To list all scripts' execution history for the specified cluster:</span></span>

```csharp
client.script_execution_history.list("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="5fe96-219">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe96-219">Example</span></span>

<span data-ttu-id="5fe96-220">Este exemplo imprime todos os detalhes para todas as execuções de script anteriores.</span><span class="sxs-lookup"><span data-stu-id="5fe96-220">This example prints all the details for all past script executions.</span></span>

```csharp
var scriptExecutionsPaged = client.ScriptExecutionHistory.List("<Resource Group Name>", "<Cluster Name>");
while (true)
{
    foreach (var script in scriptExecutionsPaged)
    {
        Debug.WriteLine(script.Name); //There are other properties of RuntimeScriptActionDetail besides Name, such as Status, Operation, StartTime, EndTime, etc. See reference documentation.

    }
    if (scriptExecutionsPaged.NextPageLink == null)
    {
        break;
    }
    scriptExecutionsPaged = client.ScriptExecutionHistory.ListNext(scriptExecutionsPaged.NextPageLink);
}
```
