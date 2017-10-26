---
title: "Bibliotecas da Cobrança do Azure para .NET"
description: "Referência para bibliotecas da Cobrança do Azure para .NET"
keywords: "Azure, .NET, SDK, API, Cobrança"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 8df15d55a80991f29b694f4af06a20514bf20b32
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-billing-libraries-for-net"></a><span data-ttu-id="43ad9-104">Bibliotecas da Cobrança do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="43ad9-104">Azure Billing libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="43ad9-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="43ad9-105">Overview</span></span>

<span data-ttu-id="43ad9-106">A API de cobrança do Azure (versão prévia) fornece acesso programático a suas faturas e informações de cobrança do Azure.</span><span class="sxs-lookup"><span data-stu-id="43ad9-106">Azure Billing API (preview) provides programmatic access to your Azure billing information and invoices.</span></span>

## <a name="management-library"></a><span data-ttu-id="43ad9-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="43ad9-107">Management library</span></span>

<span data-ttu-id="43ad9-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="43ad9-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="43ad9-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43ad9-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a><span data-ttu-id="43ad9-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="43ad9-110">Code Example</span></span>

<span data-ttu-id="43ad9-111">Conecte-se ao Azure e obtenha uma lista de faturas.</span><span class="sxs-lookup"><span data-stu-id="43ad9-111">Connect to Azure and get a list of invoices.</span></span>

```csharp
/* Include these directives
using Microsoft.Rest.Azure.Authentication;
using Microsoft.Azure.Management.Billing;
using Microsoft.Azure.Management.Billing.Models;
*/

// Log into Azure
var serviceCreds = ApplicationTokenProvider.LoginSilentAsync(tenantId, clientId, secret);
var billingClient = new BillingClient(serviceCreds);
billingClient.SubscriptionId = subscriptionId;

// Get list of invoices
billingClient.Invoices.List();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="43ad9-112">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="43ad9-112">Explore the management APIs</span></span>](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a><span data-ttu-id="43ad9-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="43ad9-113">Samples</span></span>

* [<span data-ttu-id="43ad9-114">API de uso</span><span class="sxs-lookup"><span data-stu-id="43ad9-114">Usage API</span></span>](https://github.com/Azure-Samples/billing-dotnet-usage-api)
* [<span data-ttu-id="43ad9-115">API RateCard</span><span class="sxs-lookup"><span data-stu-id="43ad9-115">RateCard API</span></span>](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)
* [<span data-ttu-id="43ad9-116">Aplicativo Web multilocatário</span><span class="sxs-lookup"><span data-stu-id="43ad9-116">Multi-Tenant Web Application</span></span>](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
