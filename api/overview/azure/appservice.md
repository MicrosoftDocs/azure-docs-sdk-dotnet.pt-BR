---
title: Bibliotecas de Serviço de Aplicativo do Azure para .NET
description: Referência para bibliotecas do Serviço de Aplicativo do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: app-service
ms.openlocfilehash: 82f8eccfafd2f7b1cf1df1ce0f40212509ccddd3
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189989"
---
# <a name="azure-app-service-libraries-for-net"></a><span data-ttu-id="b741b-103">Bibliotecas de Serviço de Aplicativo do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="b741b-103">Azure App Service libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b741b-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b741b-104">Overview</span></span>

<span data-ttu-id="b741b-105">O [Serviço de Aplicativo do Azure](/azure/app-service/app-service-value-prop-what-is) permite implantar e dimensionar sites, aplicativos Web, serviços e APIs REST.</span><span class="sxs-lookup"><span data-stu-id="b741b-105">[Azure App Service](/azure/app-service/app-service-value-prop-what-is) allows you to deploy and scale websites, web applications, services, and REST APIs.</span></span>

## <a name="management-api"></a><span data-ttu-id="b741b-106">API de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="b741b-106">Management API</span></span>

<span data-ttu-id="b741b-107">Implante, gerencie e dimensione elementos hospedados no Serviço de Aplicativo do Azure com a API de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="b741b-107">Deploy, manage, and scale elements hosted in Azure App Service with the management API.</span></span>

<span data-ttu-id="b741b-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="b741b-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b741b-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b741b-109">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="b741b-110">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="b741b-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a><span data-ttu-id="b741b-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="b741b-111">Code Example</span></span>

<span data-ttu-id="b741b-112">Crie um novo aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="b741b-112">Create a new web app.</span></span>

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
> [<span data-ttu-id="b741b-113">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="b741b-113">Explore the Management APIs</span></span>](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a><span data-ttu-id="b741b-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b741b-114">Samples</span></span>

* [<span data-ttu-id="b741b-115">Gerencie seus aplicativos Web com o SDK do .NET para Azure</span><span class="sxs-lookup"><span data-stu-id="b741b-115">Manage your web apps with the .NET SDK for Azure</span></span>](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-manage/)
* [<span data-ttu-id="b741b-116">Exemplo do ASP.NET para o Serviço de Aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="b741b-116">ASP.NET sample for Azure App Service</span></span>](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-get-started/)

<span data-ttu-id="b741b-117">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) de exemplos do Serviço de Aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="b741b-117">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) of Azure App Service samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package