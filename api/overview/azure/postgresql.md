---
title: Bibliotecas do Banco de Dados do Azure para PostgreSQL para .NET
description: Documentação de referência para as bibliotecas de cliente .NET para o Banco de Dados do Azure para PostgreSQL
ms.date: 10/19/2017
ms.topic: reference
ms.service: postgresql
ms.openlocfilehash: 4137e024eadba93c9cb3e94c1e7478d0816f8370
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190739"
---
# <a name="azure-database-for-postgresql-libraries-for-net"></a><span data-ttu-id="7b488-103">Bibliotecas do Banco de Dados do Azure para PostgreSQL para .NET</span><span class="sxs-lookup"><span data-stu-id="7b488-103">Azure Database for PostgreSQL libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="7b488-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="7b488-104">Overview</span></span>

<span data-ttu-id="7b488-105">Trabalhar com dados e recursos armazenados no [Banco de Dados do Azure para PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span><span class="sxs-lookup"><span data-stu-id="7b488-105">Work with data and resources stored in [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span></span>

## <a name="client-api"></a><span data-ttu-id="7b488-106">API do cliente</span><span class="sxs-lookup"><span data-stu-id="7b488-106">Client API</span></span>

<span data-ttu-id="7b488-107">A biblioteca de cliente recomendada para acessar o Banco de Dados do Azure para PostgreSQL é o [provedor de dados ADO.NET Npgsql](http://www.npgsql.org/) de software livre.</span><span class="sxs-lookup"><span data-stu-id="7b488-107">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Npgsql ADO.NET data provider](http://www.npgsql.org/).</span></span> <span data-ttu-id="7b488-108">Use o provedor ADO.NET para se conectar ao banco de dados e executar instruções SQL diretamente ou por meio do Entity Framework com os provedores Npgsql [Entity Framework 6](http://www.npgsql.org/ef6/index.html) ou [Entity Framework Core](http://www.npgsql.org/efcore/index.html).</span><span class="sxs-lookup"><span data-stu-id="7b488-108">Use the ADO.NET provider to connect to the database and execute SQL statements directly or through Entity Framework with the Npgsql's [Entity Framework 6](http://www.npgsql.org/ef6/index.html) or [Entity Framework Core](http://www.npgsql.org/efcore/index.html) providers.</span></span>

<span data-ttu-id="7b488-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Npgsql) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="7b488-109">Install the [NuGet package](https://www.nuget.org/packages/Npgsql) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="7b488-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7b488-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Npgsql
```

#### <a name="net-core-cli"></a><span data-ttu-id="7b488-111">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b488-111">.NET Core CLI</span></span>

```bash
dotnet add package Npgsql
```

### <a name="code-example"></a><span data-ttu-id="7b488-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="7b488-112">Code Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="7b488-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7b488-113">Samples</span></span>

- [<span data-ttu-id="7b488-114">Exemplos de código ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b488-114">ADO.NET code examples</span></span>](/dotnet/framework/data/adonet/ado-net-code-examples)
- [<span data-ttu-id="7b488-115">Criar um banco de dados PostgreSQL usando a CLI do Azure</span><span class="sxs-lookup"><span data-stu-id="7b488-115">Design a PostgreSQL database using the Azure CLI</span></span>](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
