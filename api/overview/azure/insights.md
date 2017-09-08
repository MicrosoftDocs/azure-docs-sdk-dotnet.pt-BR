---
title: Bibliotecas do Azure Application Insights para .NET
description: "Referência para bibliotecas do Azure Application Insights para .NET"
keywords: Azure, .NET, SDK, API, AppInsights de aplicativo
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/24/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 2eef8d322d905679e8aceaed77ba44726c14dd94
ms.sourcegitcommit: fa02d34afbf981f809661ab842b3b93242a38f68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2017
---
# <a name="azure-application-insights-libraries-for-net"></a>Bibliotecas do Azure Application Insights para .NET

## <a name="overview"></a>Visão geral

O Application Insights é um serviço de monitoramento e diagnóstico extensível para desenvolvedores Web com recursos de análise avançada ad hoc. Você pode usar as classes no namespace do ApplicationInsights para configurar a coleta de telemetria e enviar telemetria personalizada de qualquer aplicativo seu que deseja monitorar.

## <a name="client-library"></a>Biblioteca do cliente

O SDK cliente do Application Insights para .NET permite que você registre eventos, dados agregados, exceções, dependências e métricas em log para o Azure para análise futura.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a>Exemplo

Este exemplo rastreia um evento personalizado até o Application Insights.

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a>Exemplos

- [Análise do Application Insights com OpenSchema](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) de exemplos do Azure Application Insights.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
