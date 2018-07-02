---
title: Bibliotecas de Serviço de Aplicativo do Azure para .NET
description: Referência para bibliotecas do Serviço de Aplicativo do Azure para .NET
keywords: Azure, .NET, SDK, API, aplicativos web, serviço de aplicativo, mobile, asp.net
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 0fee28930dff5075cdd84fe3cb88850e07bc6ccb
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065796"
---
# <a name="azure-app-service-libraries-for-net"></a>Bibliotecas de Serviço de Aplicativo do Azure para .NET

## <a name="overview"></a>Visão geral

O [Serviço de Aplicativo do Azure](/azure/app-service/app-service-value-prop-what-is) permite implantar e dimensionar sites, aplicativos Web, serviços e APIs REST.

## <a name="management-api"></a>API de gerenciamento

Implante, gerencie e dimensione elementos hospedados no Serviço de Aplicativo do Azure com a API de gerenciamento.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].


#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a>Exemplo de código

Crie um novo aplicativo Web.

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.AppService.Fluent;
*/

IWebApp app1 = azure.WebApps
    .Define("MyUniqueWebAddress")
    .WithRegion(Region.USWest)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewWindowsPlan(PricingTier.StandardS1)
    .Create();
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a>Exemplos

* [Gerencie seus aplicativos Web com o SDK do .NET para Azure](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-manage/)
* [Exemplo do ASP.NET para o Serviço de Aplicativo do Azure](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-get-started/)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) de exemplos do Serviço de Aplicativo do Azure.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package