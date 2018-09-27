---
title: Bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET
description: Referência para bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: service-bus
ms.openlocfilehash: 75c481ab23e461c5194a9eeb0ca668af98f4d2d7
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189979"
---
# <a name="azure-service-bus-relay-libraries-for-net"></a><span data-ttu-id="b110a-103">Bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="b110a-103">Azure Service Bus Relay libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b110a-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b110a-104">Overview</span></span>

<span data-ttu-id="b110a-105">O serviço de Retransmissão do Azure cria os aplicativos híbridos habilitando a exposição segura de serviços que residem em uma rede empresarial corporativa para a nuvem pública sem precisar abrir uma conexão de firewall nem exigir mudanças intrusivas em uma infraestrutura de rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="b110a-105">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="b110a-106">A retransmissão dá suporte a vários protocolos de transporte e padrões de serviços Web diferentes.</span><span class="sxs-lookup"><span data-stu-id="b110a-106">Relay supports a variety of different transport protocols and web services standards.</span></span>
          
<span data-ttu-id="b110a-107">Saiba mais sobre [Retransmissão do Azure](/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="b110a-107">Learn more about [Azure Relay](/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="client-library"></a><span data-ttu-id="b110a-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="b110a-108">Client library</span></span>

<span data-ttu-id="b110a-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="b110a-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Relay) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b110a-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b110a-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b110a-111">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="b110a-111">Explore the client APIs</span></span>](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a><span data-ttu-id="b110a-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b110a-112">Samples</span></span>

<span data-ttu-id="b110a-113">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b110a-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package