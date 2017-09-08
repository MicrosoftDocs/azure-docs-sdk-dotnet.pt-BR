---
title: Bibliotecas do Banco de Dados do Azure para PostgreSQL para .NET
description: "Documentação de referência para as bibliotecas de cliente .NET para o Banco de Dados do Azure para PostgreSQL"
keywords: Azure, .NET ODBC, SDK, API, SQL, ADO.NET, banco de dados, PostGres, PostgreSQL
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: postgresql
ms.openlocfilehash: 899002b12dd36e6b23a05c8516670ff841abed79
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-database-for-postgresql-libraries-for-net"></a>Bibliotecas do Banco de Dados do Azure para PostgreSQL para .NET

## <a name="overview"></a>Visão geral

Trabalhar com dados e recursos armazenados no [Banco de Dados do Azure para PostgreSQL](https://docs.microsoft.com/azure/postgresql/).

## <a name="client-api"></a>API do cliente

A biblioteca de cliente recomendada para acessar o Banco de Dados do Azure para PostgreSQL é o [provedor de dados ADO.NET Npgsql](http://www.npgsql.org/) de software livre. Use o provedor ADO.NET para se conectar ao banco de dados e executar instruções SQL diretamente ou por meio do Entity Framework com os provedores Npgsql [Entity Framework 6](http://www.npgsql.org/ef6/index.html) ou [Entity Framework Core](http://www.npgsql.org/efcore/index.html).

Instale o [pacote NuGet](https://www.nuget.org/packages/Npgsql) diretamente do Visual Studio[console do Gerenciador de Pacotes][PackageManager] ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Npgsql
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Npgsql
```

### <a name="code-example"></a>Exemplo de código

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

### <a name="samples"></a>Exemplos

- [Exemplos de código ADO.NET](/dotnet/framework/data/adonet/ado-net-code-examples)
- [Crie um banco de dados PostgreSQL usando a CLI do Azure](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli) [PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console [DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package