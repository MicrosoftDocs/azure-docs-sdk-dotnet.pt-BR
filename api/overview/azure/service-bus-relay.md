---
title: Bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET
description: Referência para bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET
keywords: Azure, .NET, SDK, API, Retransmissão do Barramento de Serviço
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: service-bus
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e0dd9c9b0a187fe6ca81d764e60afd00cbaab654
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065946"
---
# <a name="azure-service-bus-relay-libraries-for-net"></a>Bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET

## <a name="overview"></a>Visão geral

O serviço de Retransmissão do Azure cria os aplicativos híbridos habilitando a exposição segura de serviços que residem em uma rede empresarial corporativa para a nuvem pública sem precisar abrir uma conexão de firewall nem exigir mudanças intrusivas em uma infraestrutura de rede corporativa. A retransmissão dá suporte a vários protocolos de transporte e padrões de serviços Web diferentes.
          
Saiba mais sobre [Retransmissão do Azure](/azure/service-bus-relay/relay-what-is-it).

## <a name="client-library"></a>Biblioteca do cliente

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a>Exemplos

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package