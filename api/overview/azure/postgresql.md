---
title: Bibliotecas do Banco de Dados do Azure para PostgreSQL para .NET
description: "Documentação de referência para as bibliotecas de cliente .NET para o Banco de Dados do Azure para PostgreSQL"
keywords: Azure, .NET ODBC, SDK, API, SQL, ADO.NET, banco de dados, PostGres, PostgreSQL
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: postgresql
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e3153a35845a2d7660aded64e5dbc3787c62afb6
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-database-for-postgresql-libraries-for-net"></a><span data-ttu-id="1dc2d-104">Bibliotecas do Banco de Dados do Azure para PostgreSQL para .NET</span><span class="sxs-lookup"><span data-stu-id="1dc2d-104">Azure Database for PostgreSQL libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="1dc2d-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="1dc2d-105">Overview</span></span>

<span data-ttu-id="1dc2d-106">Trabalhar com dados e recursos armazenados no [Banco de Dados do Azure para PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span><span class="sxs-lookup"><span data-stu-id="1dc2d-106">Work with data and resources stored in [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span></span>

## <a name="client-api"></a><span data-ttu-id="1dc2d-107">API do cliente</span><span class="sxs-lookup"><span data-stu-id="1dc2d-107">Client API</span></span>

<span data-ttu-id="1dc2d-108">A biblioteca de cliente recomendada para acessar o Banco de Dados do Azure para PostgreSQL é o [provedor de dados ADO.NET Npgsql](http://www.npgsql.org/) de software livre.</span><span class="sxs-lookup"><span data-stu-id="1dc2d-108">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Npgsql ADO.NET data provider](http://www.npgsql.org/).</span></span> <span data-ttu-id="1dc2d-109">Use o provedor ADO.NET para se conectar ao banco de dados e executar instruções SQL diretamente ou por meio do Entity Framework com os provedores Npgsql [Entity Framework 6](http://www.npgsql.org/ef6/index.html) ou [Entity Framework Core](http://www.npgsql.org/efcore/index.html).</span><span class="sxs-lookup"><span data-stu-id="1dc2d-109">Use the ADO.NET provider to connect to the database and execute SQL statements directly or through Entity Framework with the Npgsql's [Entity Framework 6](http://www.npgsql.org/ef6/index.html) or [Entity Framework Core](http://www.npgsql.org/efcore/index.html) providers.</span></span>

<span data-ttu-id="1dc2d-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Npgsql) diretamente do Visual Studio[console do Gerenciador de Pacotes][PackageManager] ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="1dc2d-110">Install the [NuGet package](https://www.nuget.org/packages/Npgsql) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1dc2d-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1dc2d-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Npgsql
```

#### <a name="net-core-cli"></a><span data-ttu-id="1dc2d-112">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1dc2d-112">.NET Core CLI</span></span>

```bash
dotnet add package Npgsql
```

### <a name="code-example"></a><span data-ttu-id="1dc2d-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="1dc2d-113">Code Example</span></span>

```csharp
/* Include this 'using' directive...
using Npgsql;
*/

// Always store connection strings securely. 
string connectionString = "Server=[servername].postgres.database.azure.com; " +
    "Port=5432; Database=myDataBase; User Id=[userid]@[servername]; Password=password;";

// Best practice is to scope the NpgsqlConnection to a "using" block
using (NpgsqlConnection conn = new NpgsqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    NpgsqlCommand selectCommand = new NpgsqlCommand("SELECT * FROM MyTable", conn);
    NpgsqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

### <a name="samples"></a><span data-ttu-id="1dc2d-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1dc2d-114">Samples</span></span>

- [<span data-ttu-id="1dc2d-115">Exemplos de código ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1dc2d-115">ADO.NET code examples</span></span>](/dotnet/framework/data/adonet/ado-net-code-examples)
- <span data-ttu-id="1dc2d-116">[Crie um banco de dados PostgreSQL usando a CLI do Azure](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli) [GerenciadorPacotes]: https://docs.microsoft.com/nuget/tools/package-manager-console [DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package</span><span class="sxs-lookup"><span data-stu-id="1dc2d-116">[Design a PostgreSQL database using the Azure CLI](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli) [PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console [DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package</span></span>