---
title: Bibliotecas do Azure Application Insights para .NET
description: Referência para bibliotecas do Azure Application Insights para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: application-insights
ms.openlocfilehash: 10b65f536c6461959b0be9b8f9bd3ec56a307bea
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190829"
---
# <a name="azure-application-insights-libraries-for-net"></a><span data-ttu-id="1a02e-103">Bibliotecas do Azure Application Insights para .NET</span><span class="sxs-lookup"><span data-stu-id="1a02e-103">Azure Application Insights libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="1a02e-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="1a02e-104">Overview</span></span>

<span data-ttu-id="1a02e-105">O Application Insights é um serviço de monitoramento e diagnóstico extensível para desenvolvedores Web com recursos de análise avançada ad hoc.</span><span class="sxs-lookup"><span data-stu-id="1a02e-105">Application Insights is an extensible monitoring & diagnostics service for web developers with powerful ad-hoc analytics capabilities.</span></span> <span data-ttu-id="1a02e-106">Você pode usar as classes no namespace do ApplicationInsights para configurar a coleta de telemetria e enviar telemetria personalizada de qualquer aplicativo seu que deseja monitorar.</span><span class="sxs-lookup"><span data-stu-id="1a02e-106">You can use the classes in the ApplicationInsights namespace to configure telemetry collection and send any custom telemetry from your applications that you want to monitor.</span></span>

## <a name="client-library"></a><span data-ttu-id="1a02e-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="1a02e-107">Client library</span></span>

<span data-ttu-id="1a02e-108">O SDK cliente do Application Insights para .NET permite que você registre eventos, dados agregados, exceções, dependências e métricas em log para o Azure para análise futura.</span><span class="sxs-lookup"><span data-stu-id="1a02e-108">The Application Insights client SDK for .NET allows you to log event, aggregated data, exceptions, dependency, and metrics to Azure for future analysis.</span></span>

<span data-ttu-id="1a02e-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="1a02e-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1a02e-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1a02e-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a><span data-ttu-id="1a02e-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a02e-111">Example</span></span>

<span data-ttu-id="1a02e-112">Este exemplo rastreia um evento personalizado até o Application Insights.</span><span class="sxs-lookup"><span data-stu-id="1a02e-112">This example tracks a custom event to Application Insights.</span></span>

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="1a02e-113">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="1a02e-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a><span data-ttu-id="1a02e-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1a02e-114">Samples</span></span>

- [<span data-ttu-id="1a02e-115">Análise do Application Insights com OpenSchema</span><span class="sxs-lookup"><span data-stu-id="1a02e-115">Application Insights Analytics with OpenSchema</span></span>](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)

<span data-ttu-id="1a02e-116">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) de exemplos do Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="1a02e-116">View the [complete list](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) of Azure Application Insights samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
