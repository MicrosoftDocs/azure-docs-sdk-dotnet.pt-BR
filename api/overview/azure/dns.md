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
# <a name="azure-dns-libraries-for-net"></a>Bibliotecas do DNS do Azure para .NET

Use as bibliotecas do DNS do Microsoft Azure para .NET a fim de criar e modificar zonas DNS e registros hospedados no Azure. As zonas e os registros são gerenciados como recursos do Azure. Saiba mais lendo a [Visão geral do DNS do Azure](/azure/dns/dns-overview).

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para criar e modificar zonas DNS e registros que estão hospedados no Azure.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a>Exemplo

O exemplo a seguir cria uma nova zona DNS.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a>Exemplos

* [Projeto de exemplo do SDK do .NET para DNS do Azure](https://www.microsoft.com/download/details.aspx?id=47268)

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
