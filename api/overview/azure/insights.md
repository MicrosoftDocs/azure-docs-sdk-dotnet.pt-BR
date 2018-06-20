---
title: Bibliotecas do Azure Application Insights para .NET
description: Referência para bibliotecas do Azure Application Insights para .NET
keywords: Azure, .NET, SDK, API, AppInsights de aplicativo
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: application-insights
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 081143eafaeea2954703c337609a67fd5a7941c6
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2017
ms.locfileid: "23487209"
---
# <a name="azure-application-insights-libraries-for-net"></a><span data-ttu-id="f272e-104">Bibliotecas do Azure Application Insights para .NET</span><span class="sxs-lookup"><span data-stu-id="f272e-104">Azure Application Insights libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f272e-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f272e-105">Overview</span></span>

<span data-ttu-id="f272e-106">O Application Insights é um serviço de monitoramento e diagnóstico extensível para desenvolvedores Web com recursos de análise avançada ad hoc.</span><span class="sxs-lookup"><span data-stu-id="f272e-106">Application Insights is an extensible monitoring & diagnostics service for web developers with powerful ad-hoc analytics capabilities.</span></span> <span data-ttu-id="f272e-107">Você pode usar as classes no namespace do ApplicationInsights para configurar a coleta de telemetria e enviar telemetria personalizada de qualquer aplicativo seu que deseja monitorar.</span><span class="sxs-lookup"><span data-stu-id="f272e-107">You can use the classes in the ApplicationInsights namespace to configure telemetry collection and send any custom telemetry from your applications that you want to monitor.</span></span>

## <a name="client-library"></a><span data-ttu-id="f272e-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="f272e-108">Client library</span></span>

<span data-ttu-id="f272e-109">O SDK cliente do Application Insights para .NET permite que você registre eventos, dados agregados, exceções, dependências e métricas em log para o Azure para análise futura.</span><span class="sxs-lookup"><span data-stu-id="f272e-109">The Application Insights client SDK for .NET allows you to log event, aggregated data, exceptions, dependency, and metrics to Azure for future analysis.</span></span>

<span data-ttu-id="f272e-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f272e-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f272e-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f272e-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a><span data-ttu-id="f272e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f272e-112">Example</span></span>

<span data-ttu-id="f272e-113">Este exemplo rastreia um evento personalizado até o Application Insights.</span><span class="sxs-lookup"><span data-stu-id="f272e-113">This example tracks a custom event to Application Insights.</span></span>

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f272e-114">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="f272e-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a><span data-ttu-id="f272e-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f272e-115">Samples</span></span>

- [<span data-ttu-id="f272e-116">Análise do Application Insights com OpenSchema</span><span class="sxs-lookup"><span data-stu-id="f272e-116">Application Insights Analytics with OpenSchema</span></span>](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)

<span data-ttu-id="f272e-117">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) de exemplos do Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="f272e-117">View the [complete list](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) of Azure Application Insights samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
