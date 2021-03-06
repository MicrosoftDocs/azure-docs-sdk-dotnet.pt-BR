---
title: Bibliotecas do Power BI Embedded para .NET
description: Referência para bibliotecas do Power BI Embedded para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: acb327b56e89522142e51016a6a9b279f995a674
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190369"
---
# <a name="power-bi-embedded-libraries-for-net"></a>Bibliotecas do Power BI Embedded para .NET

O [Power BI](https://powerbi.microsoft.com/) é um serviço de análise de negócios baseado em nuvem que fornece uma exibição total de seus dados de negócios mais importantes em um só lugar.

Para saber mais sobre como usar o Power BI com o .NET, confira [Incorporando com o Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).

## <a name="client-library"></a>Biblioteca do cliente

Use a biblioteca de cliente para se conectar com APIs do Power BI a fim de acessar e interagir com relatórios e conjuntos de dados.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.PowerBI.Api) diretamente do [console do Gerenciador de Pacotes][PackageManager].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.PowerBI.Api
```

### <a name="example"></a>Exemplo

O exemplo a seguir recupera e exibe uma lista de conjuntos de dados e relatórios.

```csharp
/* Include these'using' directive:
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;
*/
using (PowerBIClient client = new PowerBIClient(new Uri(apiUrl), tokenCredentials))
{

    Console.WriteLine("\r*** DATASETS ***\r");

    // List of datasets in a group/app workspace
    ODataResponseListDataset datasetList = client.Datasets.GetDatasetsInGroup(groupId);

    foreach(Dataset ds in datasetList.Value)
    {
        Console.WriteLine(ds.Id + " | " + ds.Name);
    }

    Console.WriteLine("\r*** REPORTS ***\r");

    // List of reports in a group/app workspace
    ODataResponseListReport reportList = client.Reports.GetReportsInGroup(groupId);

    foreach (Report rpt in reportList.Value)
    {
        Console.WriteLine(rpt.Id + " | " + rpt.Name +  " | DatasetID = " + rpt.DatasetId);
    }
}
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](https://powerbi.microsoft.com/documentation/powerbi-developer-rest-api-reference/)

## <a name="samples"></a>Exemplos

* [Exemplos de desenvolvedor do Power BI](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [Repositório do Power BI .NET no GitHub](https://github.com/Microsoft/PowerBI-CSharp)

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
