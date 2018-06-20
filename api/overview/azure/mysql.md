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
# <a name="azure-database-for-mysql-libraries-for-net"></a>Bibliotecas do Banco de Dados do Azure para MySQL para .NET

## <a name="overview"></a>Visão geral

Trabalhar com dados e recursos armazenados no [Banco de Dados do Azure para MySQL](/azure/mysql/overview).

## <a name="client-apis"></a>APIs de cliente

A biblioteca de cliente recomendada para acessar o Banco de Dados do Azure para MySQL é o [Connector/Net](https://dev.mysql.com/doc/connector-net/en) do MySQL. Use o pacote para se conectar ao banco de dados e executar instruções SQL diretamente. 

Instale o [pacote NuGet](https://www.nuget.org/packages/MySql.Data) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package MySql.Data
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package MySql.Data
```

### <a name="code-example"></a>Exemplo de código

Conecte-se ao banco de dados MySQL e execute uma consulta:

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

## <a name="samples"></a>Exemplos

- [Exemplos de código ADO.NET](/dotnet/framework/data/adonet/ado-net-code-examples)
- [Criar um banco de dados MySQL usando a CLI do Azure](https://docs.microsoft.com/azure/mysql/tutorial-design-database-using-cli) 

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
