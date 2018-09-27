---
title: Bibliotecas do DNS do Azure para .NET
description: Referência para bibliotecas do DNS do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: dns
ms.openlocfilehash: b9ab6359aaa1e4e9b6e99e7a7b007928d18f3453
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190189"
---
# <a name="azure-dns-libraries-for-net"></a><span data-ttu-id="e0341-103">Bibliotecas do DNS do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="e0341-103">Azure DNS libraries for .NET</span></span>

<span data-ttu-id="e0341-104">Use as bibliotecas do DNS do Microsoft Azure para .NET a fim de criar e modificar zonas DNS e registros hospedados no Azure.</span><span class="sxs-lookup"><span data-stu-id="e0341-104">Use the Microsoft Azure DNS libraries for .NET to create and modify DNS zones and records hosted within Azure.</span></span> <span data-ttu-id="e0341-105">As zonas e os registros são gerenciados como recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="e0341-105">Zones and records are managed as Azure Resources.</span></span> <span data-ttu-id="e0341-106">Saiba mais lendo a [Visão geral do DNS do Azure](/azure/dns/dns-overview).</span><span class="sxs-lookup"><span data-stu-id="e0341-106">Learn more by reading the [Azure DNS overview](/azure/dns/dns-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="e0341-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="e0341-107">Management library</span></span>

<span data-ttu-id="e0341-108">Use a biblioteca de gerenciamento para criar e modificar zonas DNS e registros que estão hospedados no Azure.</span><span class="sxs-lookup"><span data-stu-id="e0341-108">Use the management library to create and modify DNS zones and records that are hosted in Azure.</span></span>

<span data-ttu-id="e0341-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="e0341-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="e0341-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e0341-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a><span data-ttu-id="e0341-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e0341-111">Example</span></span>

<span data-ttu-id="e0341-112">O exemplo a seguir cria uma nova zona DNS.</span><span class="sxs-lookup"><span data-stu-id="e0341-112">The following example creates a new DNS zone.</span></span>

```csharp
/*
using Microsoft.Rest.Azure.Authentication;
using Microsoft.Azure.Management.Dns;
using Microsoft.Azure.Management.Dns.Models;
*/
Microsoft.Rest.ServiceClientCredentials serviceCreds = await ApplicationTokenProvider.LoginSilentAsync(tenantId, clientId, secret);
DnsManagementClient dnsClient = new DnsManagementClient(serviceCreds);            
Zone dnsZoneParams = new Zone("global");
dnsZoneParams.Tags = new Dictionary<string, string>();
dnsZoneParams.Tags.Add("dept", "finance");
Zone dnsZone =
    await dnsClient.Zones.CreateOrUpdateAsync(resourceGroupName, zoneName, dnsZoneParams, null, "*");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="e0341-113">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="e0341-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a><span data-ttu-id="e0341-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e0341-114">Samples</span></span>

* [<span data-ttu-id="e0341-115">Projeto de exemplo do SDK do .NET para DNS do Azure</span><span class="sxs-lookup"><span data-stu-id="e0341-115">Azure DNS .NET SDK Sample Project</span></span>](https://www.microsoft.com/download/details.aspx?id=47268)

<span data-ttu-id="e0341-116">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e0341-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
