---
title: Bibliotecas do Azure Data Lake Analytics para .NET
description: Referência para bibliotecas do Azure Data Lake Analytics para .NET
keywords: Azure, .NET, SDK, API, Data Lake Analytics
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-lake-analytics
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 063513d8c523330276cdfc222d3ca00a9629f63a
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a>Bibliotecas do Azure Data Lake Analytics para .NET

## <a name="overview"></a>Visão geral

O Azure Data Lake Analytics é um serviço de análise sob demanda que simplifica a análise de big data.

Para saber mais, confira [Visão geral da do Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento para se conectar ao serviço e gerenciar trabalhos de análise.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a>Exemplo de código

Este exemplo cria os clientes para conexão e gerenciamento da conta da análise.

```csharp
/*
using AdlClient 
*/

// Setup authentication for this demo
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
AnalyticsAccountRef adla_account = new AnalyticsAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
AnalyticsClient adla = new AnalyticsClient(auth, adla_account);
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a>Exemplos
* [Exemplo de cliente .NET do Azure Data Lake](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
