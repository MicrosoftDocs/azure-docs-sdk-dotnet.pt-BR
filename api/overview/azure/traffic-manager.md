---
title: Bibliotecas do Gerenciador de Tráfego do Azure para .NET
description: Referência para bibliotecas do Gerenciador de Tráfego do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: traffic-manager
ms.openlocfilehash: a75b5c566496f73475d24d62288a00c7d5775168
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190779"
---
# <a name="azure-traffic-manager-libraries-for-net"></a><span data-ttu-id="fb166-103">Bibliotecas do Gerenciador de Tráfego do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="fb166-103">Azure Traffic Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="fb166-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="fb166-104">Overview</span></span>

<span data-ttu-id="fb166-105">O Gerenciador de Tráfego do Microsoft Azure permite controlar a distribuição do tráfego do usuário para pontos de extremidade do serviço em diferentes datacenters.</span><span class="sxs-lookup"><span data-stu-id="fb166-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="fb166-106">Os pontos de extremidade de serviço com suporte no Gerenciador de Tráfego incluem VMs do Azure, Aplicativos Web e serviços de nuvem.</span><span class="sxs-lookup"><span data-stu-id="fb166-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="fb166-107">Você também pode usar o Gerenciador de Tráfego com pontos de extremidade externos e não do Azure.</span><span class="sxs-lookup"><span data-stu-id="fb166-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="fb166-108">Saiba mais sobre o [Gerenciador de Tráfego do Azure](/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="fb166-108">Learn more about [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview).</span></span>  

## <a name="management-library"></a><span data-ttu-id="fb166-109">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="fb166-109">Management library</span></span>

<span data-ttu-id="fb166-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="fb166-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="fb166-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fb166-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb166-112">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="fb166-112">Explore the management APIs</span></span>](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a><span data-ttu-id="fb166-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fb166-113">Samples</span></span>

<span data-ttu-id="fb166-114">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fb166-114">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package