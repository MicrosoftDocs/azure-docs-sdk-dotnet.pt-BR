---
title: "Introdução às APIs .NET do Azure"
description: "Introdução ao uso básico das bibliotecas do Azure para .NET com sua própria assinatura do Azure."
keywords: "Azure, .NET, SDK, API, autenticar, introdução"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: a3733898f948dbb2ec07da20aa61724e07f23e73
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-the-azure-net-apis"></a><span data-ttu-id="fa62c-104">Introdução às APIs do .NET do Azure</span><span class="sxs-lookup"><span data-stu-id="fa62c-104">Get started with the Azure .NET APIs</span></span>

<span data-ttu-id="fa62c-105">Este tutorial demonstra o uso de várias [APIs do Azure para .NET](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="fa62c-105">This tutorial demonstrates the usage of several [Azure APIs for .NET](/dotnet/api/overview/azure/).</span></span>  <span data-ttu-id="fa62c-106">Você vai configurar a autenticação, criar e usar uma conta de armazenamento do Azure, criar e usar um Banco de Dados SQL do Azure, implantar algumas máquinas virtuais e implantar um aplicativo Web do Serviço de Aplicativo do Azure no GitHub.</span><span class="sxs-lookup"><span data-stu-id="fa62c-106">You will set up authentication, create and use an Azure Storage account, create and use an Azure SQL Database, deploy some virtual machines, and deploy an Azure App Service Web App from GitHub.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa62c-107">pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fa62c-107">Prerequisites</span></span>

- <span data-ttu-id="fa62c-108">Uma conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa62c-108">An Azure account.</span></span> <span data-ttu-id="fa62c-109">Se você não tiver uma, [obtenha uma avaliação gratuita](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="fa62c-109">If you don't have one, [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="fa62c-110">PowerShell do Azure</span><span class="sxs-lookup"><span data-stu-id="fa62c-110">Azure PowerShell</span></span>](/powershell/azure/install-azurerm-ps)

## <a name="set-up-authentication"></a><span data-ttu-id="fa62c-111">Configurar a autenticação</span><span class="sxs-lookup"><span data-stu-id="fa62c-111">Set up authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="create-a-new-project"></a><span data-ttu-id="fa62c-112">Criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="fa62c-112">Create a new project</span></span> 

<span data-ttu-id="fa62c-113">Crie um novo projeto de aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="fa62c-113">Create a new console application project.</span></span>  <span data-ttu-id="fa62c-114">No Visual Studio, faça isso clicando em **Arquivo**, **Novo**e clicando em **Projeto...**.  Nos modelos do Visual C#, selecione **Aplicativo de Console (.NET Core)**, nomeie o projeto e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fa62c-114">In Visual Studio, do this by clicking **File**, **New**, and then clicking **Project...**.  Under the Visual C# templates, select **Console App (.NET Core)**, name your project, and then click **OK**.</span></span>

![Diálogo Novo projeto](media/dotnet-sdk-azure-get-started/new-project.png)

<span data-ttu-id="fa62c-116">Quando o novo aplicativo de console for criado, abra o Console do Gerenciador de Pacotes clicando em **Ferramentas**, **Gerenciador de Pacotes NuGet**e clicando em **Console do Gerenciador de Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="fa62c-116">When the new console app is created, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>  <span data-ttu-id="fa62c-117">No console, obtenha os pacotes necessários executando os três seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="fa62c-117">In the console, get the packages you'll need by executing the following three commands:</span></span>

```powershell
# Azure Management Libraries for .NET (Fluent)
Install-Package Microsoft.Azure.Management.Fluent

# Azure Store client libraries
Install-Package WindowsAzure.Storage

# SQL Database client libraries
Install-Package System.Data.SqlClient
```

## <a name="directives"></a><span data-ttu-id="fa62c-118">Diretivas</span><span class="sxs-lookup"><span data-stu-id="fa62c-118">Directives</span></span>

<span data-ttu-id="fa62c-119">Edite o arquivo `Program.cs` do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa62c-119">Edit your application's `Program.cs` file.</span></span>  <span data-ttu-id="fa62c-120">Substitua as diretivas `using` na parte superior pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="fa62c-120">Replace the `using` directives at the top with the following:</span></span>

```csharp
using System;
using System.Linq;
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Blob;
using System.Data.SqlClient;
```

## <a name="create-a-virtual-machine"></a><span data-ttu-id="fa62c-121">Criar uma máquina virtual</span><span class="sxs-lookup"><span data-stu-id="fa62c-121">Create a virtual machine</span></span>

<span data-ttu-id="fa62c-122">Este exemplo implanta uma máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="fa62c-122">This example deploys a virtual machine.</span></span> 

<span data-ttu-id="fa62c-123">Substitua o método `Main` pelo que se segue.</span><span class="sxs-lookup"><span data-stu-id="fa62c-123">Replace the `Main` method with the following.</span></span>  <span data-ttu-id="fa62c-124">Forneça um `username` e uma `password` reais para a máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="fa62c-124">Be sure to provide an actual `username` and `password` for the virtual machine.</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string username = "MY_USERNAME";
    string password = "MY_PASSWORD";
    string rgName = "sampleResourceGroup";
    string windowsVmName = "sampleWindowsVM";
    string publicIpDnsLabel = "samplePublicIP";

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .WithLogLevel(HttpLoggingDelegatingHandler.Level.Basic)
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the VM
    Console.WriteLine("Creating VM...");
    var windowsVM = azure.VirtualMachines.Define(windowsVmName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithNewPrimaryNetwork("10.0.0.0/28")
        .WithPrimaryPrivateIPAddressDynamic()
        .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
        .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
        .WithAdminUsername(username)
        .WithAdminPassword(password)
        .WithSize(VirtualMachineSizeTypes.StandardD2V2)
        .Create();

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

<span data-ttu-id="fa62c-125">Pressione **F5** para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="fa62c-125">Press **F5** to run the sample.</span></span>

<span data-ttu-id="fa62c-126">Depois de alguns minutos, o programa será concluído e solicitará que você pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="fa62c-126">After several minutes, the program will finish, prompting you to press enter.</span></span> <span data-ttu-id="fa62c-127">Após pressionar Enter, verifique a máquina virtual em sua assinatura com o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fa62c-127">After pressing enter, verify the virtual machine in your subscription with PowerShell:</span></span>

```powershell
Get-AzureRmVm -ResourceGroupName sampleResourceGroup
```

## <a name="deploy-a-web-app-from-a-github-repo"></a><span data-ttu-id="fa62c-128">Implantar um aplicativo Web de um repositório GitHub</span><span class="sxs-lookup"><span data-stu-id="fa62c-128">Deploy a web app from a GitHub repo</span></span>

<span data-ttu-id="fa62c-129">Agora, você modificará o código para criar e implantar um novo aplicativo Web de um repositório GitHub existente.</span><span class="sxs-lookup"><span data-stu-id="fa62c-129">Now you'll modify your code to create a deploy a new web app from an existing GitHub repository.</span></span> <span data-ttu-id="fa62c-130">Substitua o método `Main` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="fa62c-130">Replace the `Main` method with the following code:</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string appName = SdkContext.RandomResourceName("WebApp", 20);

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the web app
    Console.WriteLine("Creating Web App...");
    var app = azure.WebApps.Define(appName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithNewFreeAppServicePlan()
        .DefineSourceControl()
        .WithPublicGitRepository("https://github.com/Azure-Samples/app-service-web-dotnet-get-started")
        .WithBranch("master")
        .Attach()
        .Create();
    Console.WriteLine("Your web app is live at: https://{0}", app.HostNames.First());

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

<span data-ttu-id="fa62c-131">Execute o código, como feito anteriormente, pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="fa62c-131">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="fa62c-132">Verifique a implantação abrindo um navegador e acessando a URL exibida no console.</span><span class="sxs-lookup"><span data-stu-id="fa62c-132">Verify the deployment by opening a browser and navigating to URL displayed in the console.</span></span>

## <a name="connect-to-a-sql-database"></a><span data-ttu-id="fa62c-133">Conectar-se a um Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="fa62c-133">Connect to a SQL database</span></span>

<span data-ttu-id="fa62c-134">Este exemplo cria um novo Banco de Dados SQL do Azure e executa algumas operações de SQL.</span><span class="sxs-lookup"><span data-stu-id="fa62c-134">This example creates a new Azure SQL Database and performs a few SQL operations.</span></span>

<span data-ttu-id="fa62c-135">Substitua o método `Main` pelo seguinte (atribuindo uma senha forte para `dbPassword`):</span><span class="sxs-lookup"><span data-stu-id="fa62c-135">Replace the `Main` method with the following, making sure to assign a strong password for `dbPassword`:</span></span>

```csharp
 static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string adminUser = SdkContext.RandomResourceName("db", 8);
    string sqlServerName = SdkContext.RandomResourceName("sql", 10);
    string sqlDbName = SdkContext.RandomResourceName("dbname", 8);
    string dbPassword = "YOUR_PASSWORD_HERE";

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the SQL server and database
    Console.WriteLine("Creating server...");
    var sqlServer = azure.SqlServers.Define(sqlServerName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithAdministratorLogin(adminUser)
        .WithAdministratorPassword(dbPassword)
        .WithNewFirewallRule("0.0.0.0", "255.255.255.255")
        .Create();

    Console.WriteLine("Creating database...");
    var sqlDb = sqlServer.Databases.Define(sqlDbName).Create();
    
    // Display information for connecting later...
    Console.WriteLine("Created database {0} in server {1}.", sqlDbName, sqlServer.FullyQualifiedDomainName);
    Console.WriteLine("Your user name is {0}.", adminUser + "@" + sqlServer.Name);
    
    // Build the connection string
    var builder = new SqlConnectionStringBuilder();
    builder.DataSource = sqlServer.FullyQualifiedDomainName;
    builder.InitialCatalog = sqlDbName;
    builder.UserID = adminUser + "@" + sqlServer.Name; // Format user ID as "user@server"
    builder.Password = dbPassword;
    builder.Encrypt = true;
    builder.TrustServerCertificate = true;

    // connect to the database, create a table and insert an entry into it
    using (var conn = new SqlConnection(builder.ConnectionString))
    {
        conn.Open();

        Console.WriteLine("Populating database...");
        var createCommand = new SqlCommand("CREATE TABLE CLOUD (name varchar(255), code int);", conn);
        createCommand.ExecuteNonQuery();

        var insertCommand = new SqlCommand("INSERT INTO CLOUD (name, code ) VALUES ('Azure', 1);", conn);
        insertCommand.ExecuteNonQuery();

        Console.WriteLine("Reading from database...");
        var selectCommand = new SqlCommand("SELECT * FROM CLOUD", conn);
        var results = selectCommand.ExecuteReader();
        while(results.Read())
        {
            Console.WriteLine("Name: {0} Code: {1}", results[0], results[1]);
        }
    }

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```
<span data-ttu-id="fa62c-136">Execute o código, como feito anteriormente, pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="fa62c-136">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="fa62c-137">A saída do console deve validar que o servidor foi criado e funciona como esperado, mas você pode se conectar a ele diretamente com uma ferramenta como o SQL Server Management Studio, se desejar.</span><span class="sxs-lookup"><span data-stu-id="fa62c-137">The console output should validate that the server was created and works as expected, but you can connect to it directly with a tool like SQL Server Management Studio if you like.</span></span>

## <a name="write-a-blob-into-a-new-storage-account"></a><span data-ttu-id="fa62c-138">Gravar um blob em uma nova conta de armazenamento</span><span class="sxs-lookup"><span data-stu-id="fa62c-138">Write a blob into a new storage account</span></span>

<span data-ttu-id="fa62c-139">Este exemplo criará uma conta de armazenamento e carregará um blob.</span><span class="sxs-lookup"><span data-stu-id="fa62c-139">This example will create a storage account and upload a blob.</span></span>  

<span data-ttu-id="fa62c-140">Substitua o método `Main` pelo que se segue.</span><span class="sxs-lookup"><span data-stu-id="fa62c-140">Replace the `Main` method with the following.</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string storageAccountName = SdkContext.RandomResourceName("st", 10);

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the storage account
    Console.WriteLine("Creating storage account...");
    var storage = azure.StorageAccounts.Define(storageAccountName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .Create();

    var storageKeys = storage.GetKeys();
    string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

    var account = CloudStorageAccount.Parse(storageConnectionString);
    var serviceClient = account.CreateCloudBlobClient();
    
    // Create container. Name must be lower case.
    Console.WriteLine("Creating container...");
    var container = serviceClient.GetContainerReference("helloazure");
    container.CreateIfNotExistsAsync().Wait();

    // Make the container public
    var containerPermissions = new BlobContainerPermissions()
        { PublicAccess = BlobContainerPublicAccessType.Container };
    container.SetPermissionsAsync(containerPermissions).Wait();
    
    // write a blob to the container
    Console.WriteLine("Uploading blob...");
    var blob = container.GetBlockBlobReference("helloazure.txt");
    blob.UploadTextAsync("Hello, Azure!").Wait();
    Console.WriteLine("Your blob is located at {0}", blob.StorageUri.PrimaryUri);

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();        
}
```

<span data-ttu-id="fa62c-141">Pressione **F5** para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="fa62c-141">Press **F5** to run the sample.</span></span>

<span data-ttu-id="fa62c-142">Após alguns minutos, o programa será concluído.</span><span class="sxs-lookup"><span data-stu-id="fa62c-142">After several minutes, the program will finish.</span></span> <span data-ttu-id="fa62c-143">Verifique se o blob foi carregado navegando até a URL exibida no console.</span><span class="sxs-lookup"><span data-stu-id="fa62c-143">Verify the blob was uploaded by browsing to the URL displayed in the console.</span></span>  <span data-ttu-id="fa62c-144">Você verá o texto "Olá, Azure!"</span><span class="sxs-lookup"><span data-stu-id="fa62c-144">You should see the text "Hello, Azure!"</span></span> <span data-ttu-id="fa62c-145">em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="fa62c-145">in your browser.</span></span>

## <a name="clean-up"></a><span data-ttu-id="fa62c-146">Limpar</span><span class="sxs-lookup"><span data-stu-id="fa62c-146">Clean up</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa62c-147">Se não limpar os recursos deste tutorial, você continuará a ser cobrado por eles.</span><span class="sxs-lookup"><span data-stu-id="fa62c-147">If you don't clean up your resources from this tutorial, you will continue to be charged for them.</span></span>  <span data-ttu-id="fa62c-148">Não deixe de executar essa etapa.</span><span class="sxs-lookup"><span data-stu-id="fa62c-148">Be sure to do this step.</span></span>

<span data-ttu-id="fa62c-149">Exclua todos os recursos criados digitando o seguinte no PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fa62c-149">Delete all the resources you created by entering the following in PowerShell:</span></span>

```powershell
Remove-AzureRmResourceGroup -ResourceGroupName sampleResourceGroup
```
## <a name="explore-more-samples"></a><span data-ttu-id="fa62c-150">Explorar mais exemplos</span><span class="sxs-lookup"><span data-stu-id="fa62c-150">Explore more samples</span></span>

<span data-ttu-id="fa62c-151">Para saber mais sobre como usar as bibliotecas do Azure para .NET a fim de gerenciar recursos e automatizar tarefas, confira o nosso exemplo de código para [máquinas virtuais](dotnet-sdk-azure-virtual-machine-samples.md), [aplicativos Web](dotnet-sdk-azure-web-apps-samples.md) e [banco de dados SQL](dotnet-sdk-azure-sql-database-samples.md) .</span><span class="sxs-lookup"><span data-stu-id="fa62c-151">To learn more about how to use the Azure libraries for .NET to manage resources and automate tasks, see our sample code for [virtual machines](dotnet-sdk-azure-virtual-machine-samples.md), [web apps](dotnet-sdk-azure-web-apps-samples.md) and [SQL database](dotnet-sdk-azure-sql-database-samples.md).</span></span>

## <a name="reference"></a><span data-ttu-id="fa62c-152">Referência</span><span class="sxs-lookup"><span data-stu-id="fa62c-152">Reference</span></span>

<span data-ttu-id="fa62c-153">Uma [referência](http://docs.microsoft.com/dotnet/api) está disponível para todos os pacotes.</span><span class="sxs-lookup"><span data-stu-id="fa62c-153">A [reference](http://docs.microsoft.com/dotnet/api) is available for all packages.</span></span>

[!include[Contribute and community](includes/contribute.md)]
