---
title: "Bibliotecas do Gerenciador de Tráfego do Azure para .NET"
description: "Referência para bibliotecas do Gerenciador de Tráfego do Azure para .NET"
keywords: "Azure, .NET, SDK, API, Gerenciador de Tráfego"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: traffic-manager
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 491a8b12146882b32f7fc6d85ad58cca1d00fd04
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-traffic-manager-libraries-for-net"></a><span data-ttu-id="dc63c-104">Bibliotecas do Gerenciador de Tráfego do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="dc63c-104">Azure Traffic Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="dc63c-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="dc63c-105">Overview</span></span>

<span data-ttu-id="dc63c-106">O Gerenciador de Tráfego do Microsoft Azure permite controlar a distribuição do tráfego do usuário para pontos de extremidade do serviço em diferentes datacenters.</span><span class="sxs-lookup"><span data-stu-id="dc63c-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="dc63c-107">Os pontos de extremidade de serviço com suporte no Gerenciador de Tráfego incluem VMs do Azure, Aplicativos Web e serviços de nuvem.</span><span class="sxs-lookup"><span data-stu-id="dc63c-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="dc63c-108">Você também pode usar o Gerenciador de Tráfego com pontos de extremidade externos e não do Azure.</span><span class="sxs-lookup"><span data-stu-id="dc63c-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="dc63c-109">Saiba mais sobre o [Gerenciador de Tráfego do Azure](/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="dc63c-109">Learn more about [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview).</span></span>  

## <a name="management-library"></a><span data-ttu-id="dc63c-110">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="dc63c-110">Management library</span></span>

<span data-ttu-id="dc63c-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="dc63c-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="dc63c-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc63c-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc63c-113">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="dc63c-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a><span data-ttu-id="dc63c-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dc63c-114">Samples</span></span>

<span data-ttu-id="dc63c-115">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="dc63c-115">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package