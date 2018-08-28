---
title: Introdução às APIs .NET e .NET Core do Azure
description: Introdução ao uso básico das bibliotecas do Azure para .NET e .NET Core com sua própria assinatura do Azure.
keywords: Azure, .NET, .NET Core, ASP.NET, ASP.NET Core SDK, API, autenticar, introdução
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 08/22/2018
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: ad894e47704fcccc83f7d02acb8e418b167993f9
ms.sourcegitcommit: b2a53a3aea9de6720bd975fb7fe4e722e9d182a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42703049"
---
# <a name="get-started-with-the-azure-net-and-net-core-apis"></a><span data-ttu-id="5bf3d-104">Introdução às APIs .NET e .NET Core do Azure</span><span class="sxs-lookup"><span data-stu-id="5bf3d-104">Get started with the Azure .NET and .NET Core APIs</span></span>

<span data-ttu-id="5bf3d-105">Este tutorial demonstra o uso de várias [APIs do Azure para .NET](/dotnet/api/overview/azure/).</span><span class="sxs-lookup"><span data-stu-id="5bf3d-105">This tutorial demonstrates the usage of several [Azure APIs for .NET](/dotnet/api/overview/azure/).</span></span>  <span data-ttu-id="5bf3d-106">Você vai configurar a autenticação, criar e usar uma conta de armazenamento do Azure, criar e usar um Banco de Dados SQL do Azure, implantar algumas máquinas virtuais e implantar um aplicativo Web do Serviço de Aplicativo do Azure no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-106">You will set up authentication, create and use an Azure Storage account, create and use an Azure SQL Database, deploy some virtual machines, and deploy an Azure App Service Web App from GitHub.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5bf3d-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5bf3d-107">Prerequisites</span></span>

- <span data-ttu-id="5bf3d-108">Uma conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-108">An Azure account.</span></span> <span data-ttu-id="5bf3d-109">Se você não tiver uma, [obtenha uma avaliação gratuita](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="5bf3d-109">If you don't have one, [get a free trial](https://azure.microsoft.com/free/)</span></span>

## <a name="set-up-authentication"></a><span data-ttu-id="5bf3d-110">Configurar a autenticação</span><span class="sxs-lookup"><span data-stu-id="5bf3d-110">Set up authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="create-a-new-project"></a><span data-ttu-id="5bf3d-111">Criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="5bf3d-111">Create a new project</span></span> 

<span data-ttu-id="5bf3d-112">Crie um novo projeto de aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-112">Create a new console application project.</span></span>  <span data-ttu-id="5bf3d-113">No Visual Studio, faça isso clicando em **Arquivo**, **Novo**e clicando em **Projeto...**.  Nos modelos do Visual C#, selecione **Aplicativo de Console (.NET Core)**, nomeie o projeto e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-113">In Visual Studio, do this by clicking **File**, **New**, and then clicking **Project...**.  Under the Visual C# templates, select **Console App (.NET Core)**, name your project, and then click **OK**.</span></span>

![Diálogo Novo projeto](media/dotnet-sdk-azure-get-started/new-project.png)

<span data-ttu-id="5bf3d-115">Quando o novo aplicativo de console for criado, abra o Console do Gerenciador de Pacotes clicando em **Ferramentas**, **Gerenciador de Pacotes NuGet**e clicando em **Console do Gerenciador de Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-115">When the new console app is created, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>  <span data-ttu-id="5bf3d-116">No console, obtenha os pacotes necessários executando os três seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="5bf3d-116">In the console, get the packages you'll need by executing the following three commands:</span></span>

```powershell
# Azure Management Libraries for .NET (Fluent)
Install-Package Microsoft.Azure.Management.Fluent

# Azure Store client libraries
Install-Package WindowsAzure.Storage

# SQL Database client libraries
Install-Package System.Data.SqlClient
```

## <a name="directives"></a><span data-ttu-id="5bf3d-117">Diretivas</span><span class="sxs-lookup"><span data-stu-id="5bf3d-117">Directives</span></span>

<span data-ttu-id="5bf3d-118">Edite o arquivo `Program.cs` do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-118">Edit your application's `Program.cs` file.</span></span>  <span data-ttu-id="5bf3d-119">Substitua as diretivas `using` na parte superior pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="5bf3d-119">Replace the `using` directives at the top with the following:</span></span>

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

## <a name="create-a-virtual-machine"></a><span data-ttu-id="5bf3d-120">Criar uma máquina virtual</span><span class="sxs-lookup"><span data-stu-id="5bf3d-120">Create a virtual machine</span></span>

<span data-ttu-id="5bf3d-121">Este exemplo implanta uma máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-121">This example deploys a virtual machine.</span></span> 

<span data-ttu-id="5bf3d-122">Substitua o método `Main` pelo que se segue.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-122">Replace the `Main` method with the following.</span></span>  <span data-ttu-id="5bf3d-123">Forneça um `username` e uma `password` reais para a máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-123">Be sure to provide an actual `username` and `password` for the virtual machine.</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string username = "MY_USERNAME";
    string password = "MY_PASSWORD";
    string rgName = "sampleResourceGroup";
    string windowsVmName = "sampleWindowsVM";
    string publicIpDnsLabel = "samplePublicIP" + (new Random().Next(0,100000)).ToString();

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

<span data-ttu-id="5bf3d-124">Pressione **F5** para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-124">Press **F5** to run the sample.</span></span>

<span data-ttu-id="5bf3d-125">Depois de alguns minutos, o programa será concluído e solicitará que você pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-125">After several minutes, the program will finish, prompting you to press enter.</span></span> <span data-ttu-id="5bf3d-126">Após pressionar Enter, verifique a máquina virtual em sua assinatura com o Cloud Shell:</span><span class="sxs-lookup"><span data-stu-id="5bf3d-126">After pressing enter, verify the virtual machine in your subscription with the Cloud Shell:</span></span>

```azurecli-interactive
az vm list
```

## <a name="deploy-a-web-app-from-a-github-repo"></a><span data-ttu-id="5bf3d-127">Implantar um aplicativo Web a partir de um repositório GitHub</span><span class="sxs-lookup"><span data-stu-id="5bf3d-127">Deploy a web app from a GitHub repo</span></span>

<span data-ttu-id="5bf3d-128">Agora, você modificará o código para criar e implantar um novo aplicativo Web de um repositório GitHub existente.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-128">Now you'll modify your code to create a deploy a new web app from an existing GitHub repository.</span></span> <span data-ttu-id="5bf3d-129">Substitua o método `Main` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="5bf3d-129">Replace the `Main` method with the following code:</span></span>

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

<span data-ttu-id="5bf3d-130">Execute o código, como feito anteriormente, pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-130">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="5bf3d-131">Verifique a implantação abrindo um navegador e acessando a URL exibida no console.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-131">Verify the deployment by opening a browser and navigating to URL displayed in the console.</span></span>

## <a name="connect-to-a-sql-database"></a><span data-ttu-id="5bf3d-132">Conectar-se a um Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="5bf3d-132">Connect to a SQL database</span></span>

<span data-ttu-id="5bf3d-133">Este exemplo cria um novo Banco de Dados SQL do Azure e executa algumas operações de SQL.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-133">This example creates a new Azure SQL Database and performs a few SQL operations.</span></span>

<span data-ttu-id="5bf3d-134">Substitua o método `Main` pelo seguinte (atribuindo uma senha forte para `dbPassword`):</span><span class="sxs-lookup"><span data-stu-id="5bf3d-134">Replace the `Main` method with the following, making sure to assign a strong password for `dbPassword`:</span></span>

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

<span data-ttu-id="5bf3d-135">Execute o código, como feito anteriormente, pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-135">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="5bf3d-136">A saída do console deve validar que o servidor foi criado e funciona como esperado, mas você pode se conectar a ele diretamente com uma ferramenta como o SQL Server Management Studio, se desejar.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-136">The console output should validate that the server was created and works as expected, but you can connect to it directly with a tool like SQL Server Management Studio if you like.</span></span>

## <a name="write-a-blob-into-a-new-storage-account"></a><span data-ttu-id="5bf3d-137">Gravar um blob em uma nova conta de armazenamento</span><span class="sxs-lookup"><span data-stu-id="5bf3d-137">Write a blob into a new storage account</span></span>

<span data-ttu-id="5bf3d-138">Este exemplo cria uma conta de armazenamento e carrega um blob.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-138">This example creates a storage account and upload a blob.</span></span>  

<span data-ttu-id="5bf3d-139">Substitua o método `Main` pelo que se segue.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-139">Replace the `Main` method with the following.</span></span>

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

<span data-ttu-id="5bf3d-140">Pressione **F5** para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-140">Press **F5** to run the sample.</span></span>

<span data-ttu-id="5bf3d-141">Após alguns minutos, o programa será concluído.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-141">After several minutes, the program finishes.</span></span> <span data-ttu-id="5bf3d-142">Verifique se o blob foi carregado navegando até a URL exibida no console.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-142">Verify the blob was uploaded by browsing to the URL displayed in the console.</span></span>  <span data-ttu-id="5bf3d-143">Você verá o texto "Olá, Azure!"</span><span class="sxs-lookup"><span data-stu-id="5bf3d-143">You should see the text "Hello, Azure!"</span></span> <span data-ttu-id="5bf3d-144">em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-144">in your browser.</span></span>

## <a name="clean-up"></a><span data-ttu-id="5bf3d-145">Limpar</span><span class="sxs-lookup"><span data-stu-id="5bf3d-145">Clean up</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5bf3d-146">Se não limpar os recursos deste tutorial, você continuará a ser cobrado por eles.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-146">If you don't clean up your resources from this tutorial, you will continue to be charged for them.</span></span>  <span data-ttu-id="5bf3d-147">Não deixe de executar essa etapa.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-147">Be sure to do this step.</span></span>

<span data-ttu-id="5bf3d-148">Exclua todos os recursos criados digitando o seguinte no Cloud Shell:</span><span class="sxs-lookup"><span data-stu-id="5bf3d-148">Delete all the resources you created by entering the following in the Cloud Shell:</span></span>

```azurecli-interactive
az group delete --name sampleResourceGroup
```

## <a name="explore-more-samples"></a><span data-ttu-id="5bf3d-149">Explorar mais exemplos</span><span class="sxs-lookup"><span data-stu-id="5bf3d-149">Explore more samples</span></span>

<span data-ttu-id="5bf3d-150">Para saber mais sobre como usar as bibliotecas do Azure para .NET a fim de gerenciar recursos e automatizar tarefas, confira o nosso exemplo de código para [máquinas virtuais](dotnet-sdk-azure-virtual-machine-samples.md), [aplicativos Web](dotnet-sdk-azure-web-apps-samples.md) e [banco de dados SQL](dotnet-sdk-azure-sql-database-samples.md) .</span><span class="sxs-lookup"><span data-stu-id="5bf3d-150">To learn more about how to use the Azure libraries for .NET to manage resources and automate tasks, see our sample code for [virtual machines](dotnet-sdk-azure-virtual-machine-samples.md), [web apps](dotnet-sdk-azure-web-apps-samples.md) and [SQL database](dotnet-sdk-azure-sql-database-samples.md).</span></span>

## <a name="reference"></a><span data-ttu-id="5bf3d-151">Referência</span><span class="sxs-lookup"><span data-stu-id="5bf3d-151">Reference</span></span>

<span data-ttu-id="5bf3d-152">Uma [referência](http://docs.microsoft.com/dotnet/api) está disponível para todos os pacotes.</span><span class="sxs-lookup"><span data-stu-id="5bf3d-152">A [reference](http://docs.microsoft.com/dotnet/api) is available for all packages.</span></span>

[!include[Contribute and community](includes/contribute.md)]
