---
title: Bibliotecas do Azure Search para .NET
description: Referência para bibliotecas do Azure Search para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: search
ms.openlocfilehash: cf622ccb59f10a5270c02fa76d7396345fbb1a9b
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190239"
---
# <a name="azure-search-libraries-for-net"></a>Bibliotecas do Azure Search para .NET

## <a name="overview"></a>Visão geral

O [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) é um serviço de pesquisa na nuvem totalmente gerenciado que fornece uma experiência de pesquisa avançada em dados de aplicativos Web, móveis e empresariais.

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de cliente do Azure Search para acessar e executar operações de indexação e pesquisa em um serviço de pesquisa, índice, documentos ou outro objeto. Para obter uma introdução passo a passo, confira [Como usar o Azure Search em um aplicativo .NET](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Search) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Search
```

```bash
dotnet add package Microsoft.Azure.Search
```

### <a name="code-example"></a>Exemplo de código

```csharp
/* Include these 'using' directives:
   using Microsoft.Azure.Search;
   using Microsoft.Azure.Search.Models;
*/

// A service endpoint and an api-key are required on a connection.
// Set them in a config file (not shown) and then connect to the client.
IConfigurationBuilder builder = new ConfigurationBuilder().AddJsonFile("appsettings.json");
IConfigurationRoot configuration = builder.Build();

SearchServiceClient serviceClient = CreateSearchServiceClient(configuration);

// Create an index named hotels
ISearchIndexClient indexClient = serviceClient.Indexes.GetClient("hotels");

```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/search/client)


## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento do Azure Search para provisionar um serviço, gerenciar chaves de API e ajustar os recursos. O gerenciamento de serviço tem uma dependência no Azure Resource Manager para identificação de locatário e assinante. Normalmente, a autenticação e o registro de aplicativo com o Azure Active Directory também são necessários para dar suporte ao fluxo de trabalho. Para obter uma introdução sobre o provisionamento do serviço Azure Search, confira [Como usar a API REST de gerenciamento](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Search
```

```bash
dotnet add package Microsoft.Azure.Management.Search
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/search/management)

## <a name="samples"></a>Exemplos

 + [Exemplos do Azure/search-dotnet-getting-started](https://github.com/Azure-Samples/search-dotnet-getting-started)
 + [Exemplos do Azure/search-dotnet-management-api](https://github.com/Azure-Samples/search-dotnet-management-api)

Encontre mais amostras de pesquisa no [repositório de exemplos do Azure](https://github.com/Azure-Samples/) no Github.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
