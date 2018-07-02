---
title: Bibliotecas do Azure Stream Analytics para .NET
description: Referência para bibliotecas do Azure Stream Analytics para .NET
keywords: Azure, .NET, SDK, API, Stream Analytics
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: stream-analytics
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 4fc8c5700122a82a5e31df870787a67dad277542
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065926"
---
# <a name="azure-stream-analytics-libraries-for-net"></a>Bibliotecas do Azure Stream Analytics para .NET

## <a name="overview"></a>Visão geral

O [Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction) é um mecanismo de processamento de eventos totalmente gerenciado que lhe permite configurar cálculos de análise em tempo real no fluxo de dados. Os dados podem vir de dispositivos, sensores, sites, feeds de mídia social, aplicativos, sistemas de infraestrutura e muito mais. 

Para saber mais sobre o Azure Stream Analytics, confira [Introdução à detecção de fraudes em tempo real do Azure Stream Analytics](/azure/stream-analytics/stream-analytics-real-time-fraud-detection).


## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento do Azure Stream Analytics para criar, iniciar e parar trabalhos do Azure Stream Analytics.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.StreamAnalytics
```

```bash
dotnet add package Microsoft.Azure.Management.StreamAnalytics
```

### <a name="code-example"></a>Exemplo de código

Este exemplo cria um cliente do Stream Analytics e um trabalho de streaming.

```csharp
/* Include these 'using' directives:
using Microsoft.Azure.Management.StreamAnalytics;
*/
SynchronizationContext.SetSynchronizationContext(new SynchronizationContext());

// Get credentials
ServiceClientCredentials credentials = GetCredentials().Result;

// Create Stream Analytics management client
StreamAnalyticsManagementClient streamAnalyticsManagementClient = new StreamAnalyticsManagementClient(credentials)
{
    SubscriptionId = subscriptionId
};

// Create a streaming job
StreamingJob streamingJob = new StreamingJob()
{
    Tags = new Dictionary<string, string>()
    {
        { "Origin", ".NET SDK" },
        { "ReasonCreated", "Getting started tutorial" }
    },
    Location = "West US",
    EventsOutOfOrderPolicy = EventsOutOfOrderPolicy.Drop,
    EventsOutOfOrderMaxDelayInSeconds = 5,
    EventsLateArrivalMaxDelayInSeconds = 16,
    OutputErrorPolicy = OutputErrorPolicy.Drop,
    DataLocale = "en-US",
    CompatibilityLevel = CompatibilityLevel.OneFullStopZero,
    Sku = new Sku()
    {
        Name = SkuName.Standard
    }
};
StreamingJob createStreamingJobResult = streamAnalyticsManagementClient.StreamingJobs.CreateOrReplace(streamingJob, resourceGroupName, streamingJobName);
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/streamanalytics/management)


## <a name="samples"></a>Exemplos

- [SDK .NET de gerenciamento: configurar e executar trabalhos de análise usando a API do Azure Stream Analytics para .NET](/azure/stream-analytics/stream-analytics-dotnet-management-sdk)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics) de exemplos do Azure Stream Analytics.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
