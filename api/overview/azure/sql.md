---
title: APIs do Banco de Dados SQL do Azure para .NET
description: "Referência para bibliotecas de Banco de Dados SQL do Azure para .NET"
keywords: Azure, .NET, SDK, API, SQL, banco de dados
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/31/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: sql
ms.openlocfilehash: 110b7e554666a4fa6386d6715919684e121441a3
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-sql-database-apis-for-net"></a>APIs do Banco de Dados SQL do Azure para .NET

## <a name="overview"></a>Visão geral

O [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) é um serviço de banco de dados que usa o mecanismo do Microsoft SQL Server com suporte para dados relacionais, JSON, espaciais e XML. 

Para saber mais sobre como usar o Banco de Dados SQL com .NET, confira [Usar .NET com Visual Studio para se conectar e consultar um Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de cliente SQL do .NET para se conectar, fazer a autenticação com seu banco de dados e executar instruções T-SQL ad hoc e procedimentos armazenados.

Instale o [pacote NuGet]( https://www.nuget.org/packages/System.Data.SqlClient) diretamente do console do [Gerenciador de Pacotes](https://docs.microsoft.com/nuget/tools/package-manager-console) do Visual Studio ou com a [CLI do .NET Core](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package).

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package System.Data.SqlClient
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package System.Data.SqlClient
```

### <a name="code-example"></a>Exemplo de código

Este exemplo se conecta a um banco de dados e lê as linhas de uma tabela.

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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/sql/client)

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento do Banco de Dados SQL para criar, gerenciar e dimensionar as instâncias de servidor do Banco de Dados SQL.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/) diretamente do console do [Gerenciador de Pacotes](https://docs.microsoft.com/nuget/tools/package-manager-console) do Visual Studio ou com a [CLI do .NET Core](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Sql.Fluent
``` 

#### <a name="net-core-command-line"></a>Linha de comando do .NET Core

```bash
dotnet add package Microsoft.Azure.Management.Sql.Fluent
```

### <a name="code-example"></a>Exemplo de código

Este exemplo cria uma nova instância de servidor do Banco de Dados SQL e cria um novo banco de dados nessa instância.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/sql/management)

## <a name="samples"></a>Exemplos

- [Exemplos de código ADO.NET](/dotnet/framework/data/adonet/ado-net-code-examples)
- [Bibliotecas de gerenciamento do Azure para exemplos de .NET para Banco de Dados SQL](/dotnet/azure/dotnet-sdk-azure-sql-database-samples)

Veja a [lista completa](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=sql+database) de exemplos do Banco de Dados SQL.
