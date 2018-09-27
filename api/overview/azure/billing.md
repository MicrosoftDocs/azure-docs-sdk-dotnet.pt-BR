---
title: Bibliotecas da Cobrança do Azure para .NET
description: Referência para bibliotecas da Cobrança do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: 88b90c71d29eacf61e4da2099f8a054d74df4a83
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190249"
---
# <a name="azure-billing-libraries-for-net"></a><span data-ttu-id="1b12b-103">Bibliotecas da Cobrança do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="1b12b-103">Azure Billing libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="1b12b-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="1b12b-104">Overview</span></span>

<span data-ttu-id="1b12b-105">A API de cobrança do Azure (versão prévia) fornece acesso programático a suas faturas e informações de cobrança do Azure.</span><span class="sxs-lookup"><span data-stu-id="1b12b-105">Azure Billing API (preview) provides programmatic access to your Azure billing information and invoices.</span></span>

## <a name="management-library"></a><span data-ttu-id="1b12b-106">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1b12b-106">Management library</span></span>

<span data-ttu-id="1b12b-107">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="1b12b-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1b12b-108">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b12b-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a><span data-ttu-id="1b12b-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="1b12b-109">Code Example</span></span>

<span data-ttu-id="1b12b-110">Conecte-se ao Azure e obtenha uma lista de faturas.</span><span class="sxs-lookup"><span data-stu-id="1b12b-110">Connect to Azure and get a list of invoices.</span></span>

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
> [<span data-ttu-id="1b12b-111">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1b12b-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a><span data-ttu-id="1b12b-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1b12b-112">Samples</span></span>

* [<span data-ttu-id="1b12b-113">API de uso</span><span class="sxs-lookup"><span data-stu-id="1b12b-113">Usage API</span></span>](https://github.com/Azure-Samples/billing-dotnet-usage-api)
* [<span data-ttu-id="1b12b-114">API RateCard</span><span class="sxs-lookup"><span data-stu-id="1b12b-114">RateCard API</span></span>](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)
* [<span data-ttu-id="1b12b-115">Aplicativo Web multilocatário</span><span class="sxs-lookup"><span data-stu-id="1b12b-115">Multi-Tenant Web Application</span></span>](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
