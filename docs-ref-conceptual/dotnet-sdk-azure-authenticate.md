---
title: Autenticar com as bibliotecas do Azure para .NET
description: Fazer autenticação nas bibliotecas do Azure para .NET
ms.date: 08/22/2018
ms.openlocfilehash: d0d8db89816a887fa23490a213917a3c554ecdb4
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190850"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a><span data-ttu-id="ffafe-103">Autenticar com as Bibliotecas do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="ffafe-103">Authenticate with the Azure Libraries for .NET</span></span>

## <a name="connect-to-services-with-connection-strings"></a><span data-ttu-id="ffafe-104">Conectar-se aos serviços com cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="ffafe-104">Connect to services with connection strings</span></span>

<span data-ttu-id="ffafe-105">A maioria das bibliotecas de serviço do Azure exige uma cadeia de conexão ou chaves para autenticação.</span><span class="sxs-lookup"><span data-stu-id="ffafe-105">Most Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="ffafe-106">Por exemplo, o Banco de Dados SQL usa uma cadeia de conexão SQL padrão:</span><span class="sxs-lookup"><span data-stu-id="ffafe-106">For example, SQL Database uses a standard SQL connection string:</span></span>

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;
                
using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

<span data-ttu-id="ffafe-107">O Armazenamento do Azure usa uma chave de armazenamento:</span><span class="sxs-lookup"><span data-stu-id="ffafe-107">Azure Storage uses a storage key:</span></span>

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

<span data-ttu-id="ffafe-108">As cadeias de conexão de serviço são usadas em outros serviços do Azure, como [CosmosDB](/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [Cache Redis](/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache) e [Barramento de Serviço](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues), e você pode obter essas cadeias de caracteres usando o portal do Azure, a CLI ou o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffafe-108">Service connection strings are used in other Azure services like [CosmosDB](/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [Redis Cache](/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues) and you can get those strings using the Azure portal, CLI, or PowerShell.</span></span>  <span data-ttu-id="ffafe-109">Você também pode usar as bibliotecas de gerenciamento do Azure para .NET a fim de consultar recursos para criar cadeias de conexão no seu código.</span><span class="sxs-lookup"><span data-stu-id="ffafe-109">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span> 

<span data-ttu-id="ffafe-110">Esse snippet de código usa as bibliotecas de gerenciamento para criar uma cadeia de conexão da conta de armazenamento:</span><span class="sxs-lookup"><span data-stu-id="ffafe-110">This snippet uses the management libraries to create a storage account connection string:</span></span>

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

<span data-ttu-id="ffafe-111">Outras bibliotecas exigem que o aplicativo seja executado com um [entidade de serviço](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) que autoriza o aplicativo a ser executado com as credenciais concedidas.</span><span class="sxs-lookup"><span data-stu-id="ffafe-111">Other libraries require your application to run with a [service principal](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) authorizing the application to run with granted credentials.</span></span> <span data-ttu-id="ffafe-112">Essa configuração é semelhante às etapas de autenticação baseada em objeto para a biblioteca de gerenciamento listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="ffafe-112">This configuration is similar to the object-based authentication steps for the management library listed below.</span></span>

## <a name="mgmt-auth"></a><span data-ttu-id="ffafe-113">Bibliotecas de gerenciamento do Azure para autenticação do .NET</span><span class="sxs-lookup"><span data-stu-id="ffafe-113">Azure management libraries for .NET authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="ffafe-114">Agora que a entidade de serviço foi criada, duas opções estão disponíveis para fazer a autenticação na entidade de serviço a fim de criar e gerenciar recursos.</span><span class="sxs-lookup"><span data-stu-id="ffafe-114">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="ffafe-115">Nas duas opções, você precisará adicionar os pacotes NuGet a seguir ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ffafe-115">For both options you will need to add the following nuget packages to your project.</span></span>

```
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="ffafe-116">Fazer autenticação com credenciais do token</span><span class="sxs-lookup"><span data-stu-id="ffafe-116">Authenticate with token credentials</span></span>

<span data-ttu-id="ffafe-117">O primeiro método é compilar o objeto de credencial de token no código.</span><span class="sxs-lookup"><span data-stu-id="ffafe-117">The first method is to build the token credential object in code.</span></span>  <span data-ttu-id="ffafe-118">Você deve armazenar as credenciais com segurança em um arquivo de configuração, no registro ou no Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="ffafe-118">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId, 
    AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="ffafe-119">Use os valores *clientId*, *clientSecret* e *tenantId* da saída do JSON quando criou a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="ffafe-119">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="ffafe-120">Em seguida, crie o objeto `Azure` do ponto de entrada para começar a trabalhar com a API:</span><span class="sxs-lookup"><span data-stu-id="ffafe-120">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="mgmt-file"></a><span data-ttu-id="ffafe-121">Autenticação baseada em arquivo</span><span class="sxs-lookup"><span data-stu-id="ffafe-121">File-based authentication</span></span>

<span data-ttu-id="ffafe-122">A autenticação baseada em arquivo permite que você coloque as credenciais da entidade de serviço em um arquivo de texto sem formatação e proteja-o no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ffafe-122">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="ffafe-123">Leia o conteúdo do arquivo e crie o objeto `Azure` de ponto de entrada para começar a trabalhar com a API:</span><span class="sxs-lookup"><span data-stu-id="ffafe-123">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment 
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
