---
title: Bibliotecas da Cobrança do Azure para .NET
description: Referência para bibliotecas da Cobrança do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: billing
ms.openlocfilehash: 196b9b4ed5f1f5f6794d86a43d26827355800d7b
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348078"
---
# <a name="azure-billing-libraries-for-net"></a>Bibliotecas da Cobrança do Azure para .NET

## <a name="overview"></a>Visão geral

A API de cobrança do Azure (versão prévia) fornece acesso programático a suas faturas e informações de cobrança do Azure.

## <a name="management-library"></a>Biblioteca de gerenciamento

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a>Exemplo de código

Conecte-se ao Azure e obtenha uma lista de faturas.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a>Exemplos

* [API de uso](https://github.com/Azure-Samples/billing-dotnet-usage-api)
* [API RateCard](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)
* [Aplicativo Web multilocatário](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
