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
# <a name="azure-traffic-manager-libraries-for-net"></a>Bibliotecas do Gerenciador de Tráfego do Azure para .NET

## <a name="overview"></a>Visão geral

O Gerenciador de Tráfego do Microsoft Azure permite controlar a distribuição do tráfego do usuário para pontos de extremidade do serviço em diferentes datacenters. Os pontos de extremidade de serviço com suporte no Gerenciador de Tráfego incluem VMs do Azure, Aplicativos Web e serviços de nuvem. Você também pode usar o Gerenciador de Tráfego com pontos de extremidade externos e não do Azure.

Saiba mais sobre o [Gerenciador de Tráfego do Azure](/azure/traffic-manager/traffic-manager-overview).  

## <a name="management-library"></a>Biblioteca de gerenciamento

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a>Exemplos

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package