---
title: APIs do Banco de Dados SQL do Azure para .NET
description: "Referência para bibliotecas de Banco de Dados SQL do Azure para .NET"
keywords: Azure, .NET, SDK, API, SQL, banco de dados
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: sql
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 61b98b3096123b509b5c9f08bfc654aa37cf2149
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-sql-database-apis-for-net"></a><span data-ttu-id="4b785-104">APIs do Banco de Dados SQL do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="4b785-104">Azure SQL Database APIs for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="4b785-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="4b785-105">Overview</span></span>

<span data-ttu-id="4b785-106">O [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) é um serviço de banco de dados que usa o mecanismo do Microsoft SQL Server com suporte para dados relacionais, JSON, espaciais e XML.</span><span class="sxs-lookup"><span data-stu-id="4b785-106">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) is a database service using the Microsoft SQL Server engine that supports relational, JSON, spatial, and XML data.</span></span> 

<span data-ttu-id="4b785-107">Para saber mais sobre como usar o Banco de Dados SQL com .NET, confira [Usar .NET com Visual Studio para se conectar e consultar um Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4b785-107">To learn more about the using SQL Database with .NET, see [Use .NET with Visual Studio to connect and query an Azure SQL database](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).</span></span>

## <a name="client-library"></a><span data-ttu-id="4b785-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="4b785-108">Client library</span></span>

<span data-ttu-id="4b785-109">Use a biblioteca de cliente SQL do .NET para se conectar, fazer a autenticação com seu banco de dados e executar instruções T-SQL ad hoc e procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="4b785-109">Use the .NET SQL client library to connect and authenticate with your database and execute ad-hoc T-SQL statements and stored procedures.</span></span>

<span data-ttu-id="4b785-110">Instale o [pacote NuGet]( https://www.nuget.org/packages/System.Data.SqlClient) diretamente do console do [Gerenciador de Pacotes](https://docs.microsoft.com/nuget/tools/package-manager-console) do Visual Studio ou com a [CLI do .NET Core](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span><span class="sxs-lookup"><span data-stu-id="4b785-110">Install the [NuGet package]( https://www.nuget.org/packages/System.Data.SqlClient) directly from the Visual Studio [Package Manager console](https://docs.microsoft.com/nuget/tools/package-manager-console) or with the [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4b785-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4b785-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package System.Data.SqlClient
```

#### <a name="net-core-cli"></a><span data-ttu-id="4b785-112">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b785-112">.NET Core CLI</span></span>

```bash
dotnet add package System.Data.SqlClient
```

### <a name="code-example"></a><span data-ttu-id="4b785-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4b785-113">Code Example</span></span>

<span data-ttu-id="4b785-114">Este exemplo se conecta a um banco de dados e lê as linhas de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="4b785-114">This example connects to a database and reads rows from a table.</span></span>

```csharp
/* Include this 'using' directive...
using System.Data.SqlClient;
*/

// Always store connection strings securely. 
string connectionString = "Server=tcp:[serverName].database.windows.net;" 
    + "Database=myDataBase;User ID=[loginname]@[serverName];Password=myPassword;"
    + "Trusted_Connection=False;Encrypt=True;";

// Best practice is to scope the SqlConnection to a "using" block
using (SqlConnection conn = new SqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    SqlCommand selectCommand = new SqlCommand("SELECT * FROM MyTable", conn);
    SqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b785-115">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="4b785-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/sql/client)

## <a name="management-library"></a><span data-ttu-id="4b785-116">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4b785-116">Management library</span></span>

<span data-ttu-id="4b785-117">Use a biblioteca de gerenciamento do Banco de Dados SQL para criar, gerenciar e dimensionar as instâncias de servidor do Banco de Dados SQL.</span><span class="sxs-lookup"><span data-stu-id="4b785-117">Use the Azure SQL Database management library to create, manage, and scale Azure SQL Database server instances.</span></span>

<span data-ttu-id="4b785-118">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/) diretamente do console do [Gerenciador de Pacotes](https://docs.microsoft.com/nuget/tools/package-manager-console) do Visual Studio ou com a [CLI do .NET Core](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span><span class="sxs-lookup"><span data-stu-id="4b785-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/) directly from the Visual Studio [Package Manager console](https://docs.microsoft.com/nuget/tools/package-manager-console) or with the [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4b785-119">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4b785-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Sql.Fluent
``` 

#### <a name="net-core-command-line"></a><span data-ttu-id="4b785-120">Linha de comando do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b785-120">.NET Core command line</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Sql.Fluent
```

### <a name="code-example"></a><span data-ttu-id="4b785-121">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4b785-121">Code Example</span></span>

<span data-ttu-id="4b785-122">Este exemplo cria uma nova instância de servidor do Banco de Dados SQL e cria um novo banco de dados nessa instância.</span><span class="sxs-lookup"><span data-stu-id="4b785-122">This example creates a new SQL Database server instance and then creates a new database on that instance.</span></span>

```csharp
/* Include these 'using' directives...
using Microsoft.Azure.Management.Sql.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

string startAddress = "0.0.0.0";
string endAddress = "255.255.255.255";

// Create the SQL server instance
ISqlServer sqlServer = azure.SqlServers.Define("UniqueServerName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup("ResourceGroupName")
    .WithAdministratorLogin("UserName")
    .WithAdministratorPassword("Password")
    .WithNewFirewallRule(startAddress, endAddress)
    .Create();

// Create the database
ISqlDatabase sqlDb = sqlServer.Databases.Define("DatabaseName").Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b785-123">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4b785-123">Explore the management APIs</span></span>](/dotnet/api/overview/azure/sql/management)

## <a name="samples"></a><span data-ttu-id="4b785-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4b785-124">Samples</span></span>

- [<span data-ttu-id="4b785-125">Exemplos de código ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4b785-125">ADO.NET code examples</span></span>](/dotnet/framework/data/adonet/ado-net-code-examples)
- [<span data-ttu-id="4b785-126">Bibliotecas de gerenciamento do Azure para exemplos de .NET para Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="4b785-126">Azure management libraries for .NET samples for SQL Database</span></span>](/dotnet/azure/dotnet-sdk-azure-sql-database-samples)

<span data-ttu-id="4b785-127">Veja a [lista completa](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=sql+database) de exemplos do Banco de Dados SQL.</span><span class="sxs-lookup"><span data-stu-id="4b785-127">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=sql+database) of Azure SQL Database samples.</span></span>

