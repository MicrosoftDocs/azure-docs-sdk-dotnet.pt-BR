---
title: Bibliotecas do Azure Data Lake Analytics para .NET
description: "Referência para bibliotecas do Azure Data Lake Analytics para .NET"
keywords: Azure, .NET, SDK, API, Data Lake Analytics
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/18/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 935afa104b1a47f537ea3bcc981670abd6c56413
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a><span data-ttu-id="cb222-104">Bibliotecas do Azure Data Lake Analytics para .NET</span><span class="sxs-lookup"><span data-stu-id="cb222-104">Azure Data Lake Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="cb222-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="cb222-105">Overview</span></span>

<span data-ttu-id="cb222-106">O Azure Data Lake Analytics é um serviço de análise sob demanda que simplifica a análise de big data.</span><span class="sxs-lookup"><span data-stu-id="cb222-106">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span>

<span data-ttu-id="cb222-107">Para saber mais, confira [Visão geral da do Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).</span><span class="sxs-lookup"><span data-stu-id="cb222-107">To learn more, see [Overview of Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="cb222-108">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="cb222-108">Management library</span></span>

<span data-ttu-id="cb222-109">Use a biblioteca de gerenciamento para se conectar ao serviço e gerenciar trabalhos de análise.</span><span class="sxs-lookup"><span data-stu-id="cb222-109">Use the management library to connect to the service and manage analytics jobs.</span></span>

<span data-ttu-id="cb222-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="cb222-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="cb222-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb222-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a><span data-ttu-id="cb222-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="cb222-112">Code Example</span></span>

<span data-ttu-id="cb222-113">Este exemplo cria os clientes para conexão e gerenciamento da conta da análise.</span><span class="sxs-lookup"><span data-stu-id="cb222-113">This example creates the clients to connect with and manage the analytics account.</span></span>

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
> [<span data-ttu-id="cb222-114">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="cb222-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a><span data-ttu-id="cb222-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cb222-115">Samples</span></span>
* [<span data-ttu-id="cb222-116">Exemplo de cliente .NET do Azure Data Lake</span><span class="sxs-lookup"><span data-stu-id="cb222-116">Azure Data Lake .NET Client Example</span></span>](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)

<span data-ttu-id="cb222-117">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="cb222-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
