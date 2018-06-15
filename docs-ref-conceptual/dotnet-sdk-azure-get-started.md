---
title: Introdução às APIs .NET do Azure
description: Introdução ao uso básico das bibliotecas do Azure para .NET com sua própria assinatura do Azure.
keywords: Azure, .NET, SDK, API, autenticar, introdução
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
ms.locfileid: "29752868"
---
# <a name="get-started-with-the-azure-net-apis"></a>Introdução às APIs do .NET do Azure

Este tutorial demonstra o uso de várias [APIs do Azure para .NET](/dotnet/api/overview/azure/).  Você vai configurar a autenticação, criar e usar uma conta de armazenamento do Azure, criar e usar um Banco de Dados SQL do Azure, implantar algumas máquinas virtuais e implantar um aplicativo Web do Serviço de Aplicativo do Azure no GitHub.

## <a name="prerequisites"></a>pré-requisitos

- Uma conta do Azure. Se você não tiver uma, [obtenha uma avaliação gratuita](https://azure.microsoft.com/free/)
- [PowerShell do Azure](/powershell/azure/install-azurerm-ps)

## <a name="set-up-authentication"></a>Configurar a autenticação

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="create-a-new-project"></a>Criar um novo projeto 

Crie um novo projeto de aplicativo de console.  No Visual Studio, faça isso clicando em **Arquivo**, **Novo**e clicando em **Projeto...**.  Nos modelos do Visual C#, selecione **Aplicativo de Console (.NET Core)**, nomeie o projeto e clique em **OK**.

![Diálogo Novo projeto](media/dotnet-sdk-azure-get-started/new-project.png)

Quando o novo aplicativo de console for criado, abra o Console do Gerenciador de Pacotes clicando em **Ferramentas**, **Gerenciador de Pacotes NuGet**e clicando em **Console do Gerenciador de Pacotes**.  No console, obtenha os pacotes necessários executando os três seguintes comandos:

```powershell
# Azure Management Libraries for .NET (Fluent)
Install-Package Microsoft.Azure.Management.Fluent

# Azure Store client libraries
Install-Package WindowsAzure.Storage

# SQL Database client libraries
Install-Package System.Data.SqlClient
```

## <a name="directives"></a>Diretivas

Edite o arquivo `Program.cs` do seu aplicativo.  Substitua as diretivas `using` na parte superior pelo seguinte:

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

## <a name="create-a-virtual-machine"></a>Criar uma máquina virtual

Este exemplo implanta uma máquina virtual. 

Substitua o método `Main` pelo que se segue.  Forneça um `username` e uma `password` reais para a máquina virtual.

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

Pressione **F5** para executar o exemplo.

Depois de alguns minutos, o programa será concluído e solicitará que você pressione Enter. Após pressionar Enter, verifique a máquina virtual em sua assinatura com o PowerShell:

```powershell
Get-AzureRmVm -ResourceGroupName sampleResourceGroup
```

## <a name="deploy-a-web-app-from-a-github-repo"></a>Implantar um aplicativo Web de um repositório GitHub

Agora, você modificará o código para criar e implantar um novo aplicativo Web de um repositório GitHub existente. Substitua o método `Main` pelo seguinte código:

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

Execute o código, como feito anteriormente, pressionando **F5**.  Verifique a implantação abrindo um navegador e acessando a URL exibida no console.

## <a name="connect-to-a-sql-database"></a>Conectar-se a um Banco de Dados SQL

Este exemplo cria um novo Banco de Dados SQL do Azure e executa algumas operações de SQL.

Substitua o método `Main` pelo seguinte (atribuindo uma senha forte para `dbPassword`):

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
Execute o código, como feito anteriormente, pressionando **F5**.  A saída do console deve validar que o servidor foi criado e funciona como esperado, mas você pode se conectar a ele diretamente com uma ferramenta como o SQL Server Management Studio, se desejar.

## <a name="write-a-blob-into-a-new-storage-account"></a>Gravar um blob em uma nova conta de armazenamento

Este exemplo criará uma conta de armazenamento e carregará um blob.  

Substitua o método `Main` pelo que se segue.

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

Pressione **F5** para executar o exemplo.

Após alguns minutos, o programa será concluído. Verifique se o blob foi carregado navegando até a URL exibida no console.  Você verá o texto "Olá, Azure!" em seu navegador.

## <a name="clean-up"></a>Limpar

> [!IMPORTANT]
> Se não limpar os recursos deste tutorial, você continuará a ser cobrado por eles.  Não deixe de executar essa etapa.

Exclua todos os recursos criados digitando o seguinte no PowerShell:

```powershell
Remove-AzureRmResourceGroup -ResourceGroupName sampleResourceGroup
```
## <a name="explore-more-samples"></a>Explorar mais exemplos

Para saber mais sobre como usar as bibliotecas do Azure para .NET a fim de gerenciar recursos e automatizar tarefas, confira o nosso exemplo de código para [máquinas virtuais](dotnet-sdk-azure-virtual-machine-samples.md), [aplicativos Web](dotnet-sdk-azure-web-apps-samples.md) e [banco de dados SQL](dotnet-sdk-azure-sql-database-samples.md) .

## <a name="reference"></a>Referência

Uma [referência](http://docs.microsoft.com/dotnet/api) está disponível para todos os pacotes.

[!include[Contribute and community](includes/contribute.md)]
