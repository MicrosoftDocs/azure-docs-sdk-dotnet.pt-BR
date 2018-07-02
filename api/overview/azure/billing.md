---
title: Bibliotecas da Cobrança do Azure para .NET
description: Referência para bibliotecas da Cobrança do Azure para .NET
keywords: Azure, .NET, SDK, API, Cobrança
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 97a4c642e8be03db7e31e8c9bc71dcf9c3fc1447
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065506"
---
# <a name="azure-billing-libraries-for-net"></a><span data-ttu-id="383a4-104">Bibliotecas da Cobrança do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="383a4-104">Azure Billing libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="383a4-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="383a4-105">Overview</span></span>

<span data-ttu-id="383a4-106">A API de cobrança do Azure (versão prévia) fornece acesso programático a suas faturas e informações de cobrança do Azure.</span><span class="sxs-lookup"><span data-stu-id="383a4-106">Azure Billing API (preview) provides programmatic access to your Azure billing information and invoices.</span></span>

## <a name="management-library"></a><span data-ttu-id="383a4-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="383a4-107">Management library</span></span>

<span data-ttu-id="383a4-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="383a4-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="383a4-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="383a4-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a><span data-ttu-id="383a4-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="383a4-110">Code Example</span></span>

<span data-ttu-id="383a4-111">Conecte-se ao Azure e obtenha uma lista de faturas.</span><span class="sxs-lookup"><span data-stu-id="383a4-111">Connect to Azure and get a list of invoices.</span></span>

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
> [<span data-ttu-id="383a4-112">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="383a4-112">Explore the management APIs</span></span>](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a><span data-ttu-id="383a4-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="383a4-113">Samples</span></span>

* [<span data-ttu-id="383a4-114">API de uso</span><span class="sxs-lookup"><span data-stu-id="383a4-114">Usage API</span></span>](https://github.com/Azure-Samples/billing-dotnet-usage-api)
* [<span data-ttu-id="383a4-115">API RateCard</span><span class="sxs-lookup"><span data-stu-id="383a4-115">RateCard API</span></span>](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)
* [<span data-ttu-id="383a4-116">Aplicativo Web multilocatário</span><span class="sxs-lookup"><span data-stu-id="383a4-116">Multi-Tenant Web Application</span></span>](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
