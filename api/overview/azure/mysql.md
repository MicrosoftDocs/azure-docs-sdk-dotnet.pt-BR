---
title: Bibliotecas do Banco de Dados do Azure para MySQL para .NET
description: Documentação de referência para as bibliotecas de cliente .NET para o Banco de Dados do Azure para MySQL
keywords: Azure, .NET, SDK, API, SQL, banco de dados, MySQL
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: mysql
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 27c1a2c7d36966d14daff5397b248a24197bec3b
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566047"
---
# <a name="azure-database-for-mysql-libraries-for-net"></a><span data-ttu-id="718a6-104">Bibliotecas do Banco de Dados do Azure para MySQL para .NET</span><span class="sxs-lookup"><span data-stu-id="718a6-104">Azure Database for MySQL libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="718a6-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="718a6-105">Overview</span></span>

<span data-ttu-id="718a6-106">Trabalhar com dados e recursos armazenados no [Banco de Dados do Azure para MySQL](/azure/mysql/overview).</span><span class="sxs-lookup"><span data-stu-id="718a6-106">Work with data and resources stored in [Azure Database for MySQL](/azure/mysql/overview).</span></span>

## <a name="client-apis"></a><span data-ttu-id="718a6-107">APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="718a6-107">Client APIs</span></span>

<span data-ttu-id="718a6-108">A biblioteca de cliente recomendada para acessar o Banco de Dados do Azure para MySQL é o [Connector/Net](https://dev.mysql.com/doc/connector-net/en) do MySQL.</span><span class="sxs-lookup"><span data-stu-id="718a6-108">The recommended client library for accessing Azure Database for MySQL is MySQL's [Connector/Net](https://dev.mysql.com/doc/connector-net/en).</span></span> <span data-ttu-id="718a6-109">Use o pacote para se conectar ao banco de dados e executar instruções SQL diretamente.</span><span class="sxs-lookup"><span data-stu-id="718a6-109">Use the package to connect to the database and execute SQL statements directly.</span></span> 

<span data-ttu-id="718a6-110">Instale o [pacote NuGet](https://www.nuget.org/packages/MySql.Data) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="718a6-110">Install the [NuGet package](https://www.nuget.org/packages/MySql.Data) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="718a6-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="718a6-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package MySql.Data
```

#### <a name="net-core-cli"></a><span data-ttu-id="718a6-112">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="718a6-112">.NET Core CLI</span></span>

```bash
dotnet add package MySql.Data
```

### <a name="code-example"></a><span data-ttu-id="718a6-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="718a6-113">Code Example</span></span>

<span data-ttu-id="718a6-114">Conecte-se ao banco de dados MySQL e execute uma consulta:</span><span class="sxs-lookup"><span data-stu-id="718a6-114">Connect to a MySQL database and execute a query:</span></span>

```csharp
/* Include this "using" directive...
using MySql.Data.MySqlClient;
*/

string connectionString = "Server=[servername].mysql.database.azure.com; " +
    "Database=myDataBase; Uid=[userid]@[servername]; Pwd=myPassword;";

// Best practice is to scope the MySqlConnection to a "using" block
using (MySqlConnection conn = new MySqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    MySqlCommand selectCommand = new MySqlCommand("SELECT * FROM MyTable", conn);
    MySqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

## <a name="samples"></a><span data-ttu-id="718a6-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="718a6-115">Samples</span></span>

- [<span data-ttu-id="718a6-116">Exemplos de código ADO.NET</span><span class="sxs-lookup"><span data-stu-id="718a6-116">ADO.NET code examples</span></span>](/dotnet/framework/data/adonet/ado-net-code-examples)
- [<span data-ttu-id="718a6-117">Criar um banco de dados MySQL usando a CLI do Azure</span><span class="sxs-lookup"><span data-stu-id="718a6-117">Design a MySQL database using the Azure CLI</span></span>](https://docs.microsoft.com/azure/mysql/tutorial-design-database-using-cli) 

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
