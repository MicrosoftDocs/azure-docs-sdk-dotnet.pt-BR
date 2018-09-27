---
title: Bibliotecas do Azure Data Lake Analytics para .NET
description: Referência para bibliotecas do Azure Data Lake Analytics para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-lake-analytics
ms.openlocfilehash: 829f9245ae06c64c4ad9a175fd25c742533a284e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189789"
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a><span data-ttu-id="715a6-103">Bibliotecas do Azure Data Lake Analytics para .NET</span><span class="sxs-lookup"><span data-stu-id="715a6-103">Azure Data Lake Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="715a6-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="715a6-104">Overview</span></span>

<span data-ttu-id="715a6-105">O Azure Data Lake Analytics é um serviço de análise sob demanda que simplifica a análise de big data.</span><span class="sxs-lookup"><span data-stu-id="715a6-105">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span>

<span data-ttu-id="715a6-106">Para saber mais, confira [Visão geral da do Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).</span><span class="sxs-lookup"><span data-stu-id="715a6-106">To learn more, see [Overview of Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="715a6-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="715a6-107">Management library</span></span>

<span data-ttu-id="715a6-108">Use a biblioteca de gerenciamento para se conectar ao serviço e gerenciar trabalhos de análise.</span><span class="sxs-lookup"><span data-stu-id="715a6-108">Use the management library to connect to the service and manage analytics jobs.</span></span>

<span data-ttu-id="715a6-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="715a6-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="715a6-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="715a6-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a><span data-ttu-id="715a6-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="715a6-111">Code Example</span></span>

<span data-ttu-id="715a6-112">Este exemplo cria os clientes para conexão e gerenciamento da conta da análise.</span><span class="sxs-lookup"><span data-stu-id="715a6-112">This example creates the clients to connect with and manage the analytics account.</span></span>

```csharp
/*
using AdlClient 
*/

// Setup authentication for this demo
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
AnalyticsAccountRef adla_account = new AnalyticsAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
AnalyticsClient adla = new AnalyticsClient(auth, adla_account);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="715a6-113">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="715a6-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a><span data-ttu-id="715a6-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="715a6-114">Samples</span></span>
* [<span data-ttu-id="715a6-115">Exemplo de cliente .NET do Azure Data Lake</span><span class="sxs-lookup"><span data-stu-id="715a6-115">Azure Data Lake .NET Client Example</span></span>](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)

<span data-ttu-id="715a6-116">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="715a6-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
