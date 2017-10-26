---
title: Autenticar com as bibliotecas do Azure para .NET
description: "Fazer autenticação nas bibliotecas do Azure para .NET"
keywords: "Azure, .NET, SDK, API, autenticação, active directory, entidade de serviço"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: c9755d7e9c20186c7677b4bfe69d4033f9852607
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a>Autenticar com as Bibliotecas do Azure para .NET

## <a name="connect-to-services-with-connection-strings"></a>Conectar-se aos serviços com cadeias de conexão

A maioria das bibliotecas de serviço do Azure exige uma cadeia de conexão ou chaves para autenticação. Por exemplo, o Banco de Dados SQL usa uma cadeia de conexão SQL padrão:

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

O Armazenamento do Azure usa uma chave de armazenamento:

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

As cadeias de conexão de serviço são usadas em outros serviços do Azure, como [CosmosDB](/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [Cache Redis](/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache) e [Barramento de Serviço](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues), e você pode obter essas cadeias de caracteres usando o portal do Azure, a CLI ou o PowerShell.  Você também pode usar as bibliotecas de gerenciamento do Azure para .NET a fim de consultar recursos para criar cadeias de conexão no seu código. 

Esse trecho de código usa as bibliotecas de gerenciamento para criar uma cadeia de conexão da conta de armazenamento:

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

Outras bibliotecas exigem que o aplicativo seja executado com um [entidade de serviço](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) que autoriza o aplicativo a ser executado com as credenciais concedidas. Essa configuração é semelhante às etapas de autenticação baseada em objeto para a biblioteca de gerenciamento listadas abaixo.

## <a name="mgmt-auth"></a>Bibliotecas de gerenciamento do Azure para autenticação do .NET

[!include[Create service principal](includes/create-sp.md)]

Agora que a entidade de serviço foi criada, duas opções estão disponíveis para fazer a autenticação na entidade de serviço a fim de criar e gerenciar recursos.

Nas duas opções, você precisará adicionar os pacotes NuGet a seguir ao seu projeto.

```
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>Fazer autenticação com credenciais do token

O primeiro método é compilar o objeto de credencial de token no código.  Você deve armazenar as credenciais com segurança em um arquivo de configuração, no registro ou no Azure Key Vault.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId, 
    AzureEnvironment.AzureGlobalCloud);
```

- clientId: use o valor *ApplicationId* da saída da entidade de serviço.
- clientSecret: use o parâmetro *-Password* atribuído quando você executou `New-AzureRmADServicePrincipal` (sem aspas).
- tenantId: use o valor *TenantId* de quando você executou `Login-AzureRmAccount`.

Em seguida, crie o objeto `Azure` do ponto de entrada para começar a trabalhar com a API:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="mgmt-file"></a>Autenticação baseada em arquivo

A autenticação baseada em arquivo permite que você coloque as credenciais da entidade de serviço em um arquivo de texto sem formatação e proteja-o no sistema de arquivos.

[!include[File-based authentication](includes/file-based-auth.md)]

Leia o conteúdo do arquivo e crie o objeto `Azure` de ponto de entrada para começar a trabalhar com a API:

```csharp
// pull in the location of the authentication properties file from the environment 
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
