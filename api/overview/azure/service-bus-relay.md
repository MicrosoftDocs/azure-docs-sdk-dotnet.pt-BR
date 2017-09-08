---
title: "Bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET"
description: "Referência para bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET"
keywords: "Azure, .NET, SDK, API, Retransmissão do Barramento de Serviço"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/14/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 13a875b837648a05401453e975c9cd70d5e203a1
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-service-bus-relay-libraries-for-net"></a><span data-ttu-id="9f385-104">Bibliotecas da Retransmissão do Barramento de Serviço do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="9f385-104">Azure Service Bus Relay libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9f385-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9f385-105">Overview</span></span>

<span data-ttu-id="9f385-106">O serviço de Retransmissão do Azure cria os aplicativos híbridos habilitando a exposição segura de serviços que residem em uma rede empresarial corporativa para a nuvem pública sem precisar abrir uma conexão de firewall nem exigir mudanças intrusivas em uma infraestrutura de rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="9f385-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="9f385-107">A retransmissão dá suporte a vários protocolos de transporte e padrões de serviços Web diferentes.</span><span class="sxs-lookup"><span data-stu-id="9f385-107">Relay supports a variety of different transport protocols and web services standards.</span></span>
          
<span data-ttu-id="9f385-108">Saiba mais sobre [Retransmissão do Azure](https://docs.microsoft.com/en-us/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="9f385-108">Learn more about [Azure Relay](https://docs.microsoft.com/en-us/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="client-library"></a><span data-ttu-id="9f385-109">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="9f385-109">Client library</span></span>

<span data-ttu-id="9f385-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Relay) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9f385-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Relay) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9f385-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9f385-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f385-112">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="9f385-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a><span data-ttu-id="9f385-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9f385-113">Samples</span></span>

<span data-ttu-id="9f385-114">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9f385-114">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package