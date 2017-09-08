---
title: "Bibliotecas de Serviço de Aplicativo do Azure para .NET"
description: "Referência para bibliotecas do Serviço de Aplicativo do Azure para .NET"
keywords: "Azure, .NET, SDK, API, aplicativos web, serviço de aplicativo, mobile, asp.net"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: e81a296ea5f5dadf7086439c88a347c20ec2abee
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-app-service-libraries-for-net"></a><span data-ttu-id="c02a9-104">Bibliotecas de Serviço de Aplicativo do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="c02a9-104">Azure App Service libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="c02a9-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="c02a9-105">Overview</span></span>

<span data-ttu-id="c02a9-106">O [Serviço de Aplicativo do Azure](/azure/app-service/app-service-value-prop-what-is) permite implantar e dimensionar sites, aplicativos Web, serviços e APIs REST.</span><span class="sxs-lookup"><span data-stu-id="c02a9-106">[Azure App Service](/azure/app-service/app-service-value-prop-what-is) allows you to deploy and scale websites, web applications, services, and REST APIs.</span></span>

## <a name="management-api"></a><span data-ttu-id="c02a9-107">API de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c02a9-107">Management API</span></span>

<span data-ttu-id="c02a9-108">Implante, gerencie e dimensione elementos hospedados no Serviço de Aplicativo do Azure com a API de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="c02a9-108">Deploy, manage, and scale elements hosted in Azure App Service with the management API.</span></span>

<span data-ttu-id="c02a9-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="c02a9-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="c02a9-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c02a9-110">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="c02a9-111">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="c02a9-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a><span data-ttu-id="c02a9-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="c02a9-112">Code Example</span></span>

<span data-ttu-id="c02a9-113">Crie um novo aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="c02a9-113">Create a new web app.</span></span>

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
> [<span data-ttu-id="c02a9-114">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c02a9-114">Explore the Management APIs</span></span>](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a><span data-ttu-id="c02a9-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c02a9-115">Samples</span></span>

* [<span data-ttu-id="c02a9-116">Gerencie seus aplicativos Web com o SDK do .NET para Azure</span><span class="sxs-lookup"><span data-stu-id="c02a9-116">Manage your web apps with the .NET SDK for Azure</span></span>](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-manage/)
* [<span data-ttu-id="c02a9-117">Exemplo do ASP.NET para o Serviço de Aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="c02a9-117">ASP.NET sample for Azure App Service</span></span>](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-get-started/)

<span data-ttu-id="c02a9-118">Veja a [lista completa](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=app%20service) de exemplos do Serviço de Aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="c02a9-118">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=app%20service) of Azure App Service samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package