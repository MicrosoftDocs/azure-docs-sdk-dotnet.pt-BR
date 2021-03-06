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
# <a name="azure-application-insights-libraries-for-net"></a>Bibliotecas do Azure Application Insights para .NET

## <a name="overview"></a>Visão geral

O Application Insights é um serviço de monitoramento e diagnóstico extensível para desenvolvedores Web com recursos de análise avançada ad hoc. Você pode usar as classes no namespace do ApplicationInsights para configurar a coleta de telemetria e enviar telemetria personalizada de qualquer aplicativo seu que deseja monitorar.

## <a name="client-library"></a>Biblioteca do cliente

O SDK cliente do Application Insights para .NET permite que você registre eventos, dados agregados, exceções, dependências e métricas em log para o Azure para análise futura.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

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
