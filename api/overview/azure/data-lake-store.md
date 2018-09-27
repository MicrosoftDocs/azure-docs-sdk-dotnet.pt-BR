---
title: Bibliotecas do Azure Data Lake Store para .NET
description: Referência para bibliotecas do Azure Data Lake Store para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-lake-store
ms.openlocfilehash: 8e55a21d84eae2ef4104c8253adec2cbc4b008e5
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190559"
---
# <a name="azure-data-lake-store-libraries-for-net"></a>Bibliotecas do Azure Data Lake Store para .NET

## <a name="overview"></a>Visão geral

O Repositório Azure Data Lake é um repositório em hiper-escala corporativo para cargas de trabalho de análise de big data. O Azure Data Lake permite que você capture dados de qualquer tamanho, tipo e velocidade de ingestão em um único lugar para análises operacionais e exploratórias.

Para saber mais, confira [Visão geral do Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de clientes para executar operações de sistema de arquivos no Data Lake Store, como a criação de pastas em uma conta do Data Lake Store, o carregamento e o download de arquivos.  Para obter um tutorial completo sobre como usar o Data Lake Store com o .NET, confira [Operações de sistema de arquivos no Azure Data Lake Store usando o SDK do .NET](/azure/data-lake-store/data-lake-store-data-operations-net-sdk).

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.DataLake.Store
```
### <a name="authentication"></a>Autenticação

* Para saber sobre autenticação do usuário final em seu aplicativo, consulte [Autenticação do usuário final com Data Lake Store usando SDK do .NET](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk).
* Para saber sobre autenticação do usuário final em seu aplicativo, consulte [Autenticação de serviço para serviço com Data Lake Store usando o SDK do .NET](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk).

### <a name="code-example"></a>Exemplo de código

O snippet de código a seguir cria o objeto de cliente de sistema de arquivos do Data Lake Store, que é usado para emitir solicitações para o serviço.

```csharp
// Create client objects
AdlsClient client = AdlsClient.CreateClient(_adlsAccountName, adlCreds);
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/datalakestore/client)


## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para se conectar e gerenciar seus grandes armazenamentos de dados.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/datalakestore/management)


## <a name="samples"></a>Exemplos

* [Exemplo de cliente .NET do Azure Data Lake](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
