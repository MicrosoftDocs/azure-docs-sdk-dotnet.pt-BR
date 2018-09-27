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
# <a name="power-bi-embedded-libraries-for-net"></a><span data-ttu-id="4865e-103">Bibliotecas do Power BI Embedded para .NET</span><span class="sxs-lookup"><span data-stu-id="4865e-103">Power BI Embedded libraries for .NET</span></span>

<span data-ttu-id="4865e-104">O [Power BI](https://powerbi.microsoft.com/) é um serviço de análise de negócios baseado em nuvem que fornece uma exibição total de seus dados de negócios mais importantes em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="4865e-104">[Power BI](https://powerbi.microsoft.com/) is a cloud-based business analytics service that gives you a single view of your most critical business data.</span></span>

<span data-ttu-id="4865e-105">Para saber mais sobre como usar o Power BI com o .NET, confira [Incorporando com o Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="4865e-105">To learn more about using Power BI with .NET, see [Embedding with Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).</span></span>

## <a name="client-library"></a><span data-ttu-id="4865e-106">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="4865e-106">Client library</span></span>

<span data-ttu-id="4865e-107">Use a biblioteca de cliente para se conectar com APIs do Power BI a fim de acessar e interagir com relatórios e conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="4865e-107">Use the client library to connect with Power BI APIs to access and interact with data sets and reports.</span></span>

<span data-ttu-id="4865e-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.PowerBI.Api) diretamente do [console do Gerenciador de Pacotes][PackageManager].</span><span class="sxs-lookup"><span data-stu-id="4865e-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.PowerBI.Api) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="4865e-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4865e-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.PowerBI.Api
```

### <a name="example"></a><span data-ttu-id="4865e-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4865e-110">Example</span></span>

<span data-ttu-id="4865e-111">O exemplo a seguir recupera e exibe uma lista de conjuntos de dados e relatórios.</span><span class="sxs-lookup"><span data-stu-id="4865e-111">The following example retrieves and displays a list of datasets and reports.</span></span>

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
> [<span data-ttu-id="4865e-112">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="4865e-112">Explore the client APIs</span></span>](https://powerbi.microsoft.com/documentation/powerbi-developer-rest-api-reference/)

## <a name="samples"></a><span data-ttu-id="4865e-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4865e-113">Samples</span></span>

* [<span data-ttu-id="4865e-114">Exemplos de desenvolvedor do Power BI</span><span class="sxs-lookup"><span data-stu-id="4865e-114">Power BI Developer Samples</span></span>](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [<span data-ttu-id="4865e-115">Repositório do Power BI .NET no GitHub</span><span class="sxs-lookup"><span data-stu-id="4865e-115">Power BI .NET GitHub repo</span></span>](https://github.com/Microsoft/PowerBI-CSharp)

<span data-ttu-id="4865e-116">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4865e-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
