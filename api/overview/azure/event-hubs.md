---
title: Bibliotecas de Hubs de Eventos do Azure para .NET
description: "Referência para bibliotecas de Hubs de Eventos do Azure para .NET"
keywords: Azure, .NET, SDK, API, Hubs de Eventos
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: event-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 2ec234959ffc46d2399d1c763e05f173a311b0d2
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2017
---
# <a name="azure-event-hubs-libraries-for-net"></a>Bibliotecas de Hubs de Eventos do Azure para .NET

## <a name="overview"></a>Visão geral

Hubs de Eventos do Azure é uma plataforma de streaming de dados e um serviço de recebimento de eventos altamente escalonável.

Para saber mais sobre os Hubs de Eventos do Azure, leia o artigo [O que são Hubs de Eventos?](/azure/event-hubs/event-hubs-what-is-event-hubs).  Como introdução, confira o [guia de programação de Hubs de Eventos](/azure/event-hubs/event-hubs-programming-guide).

## <a name="client-library"></a>Biblioteca do cliente

Use o cliente Hubs de Eventos para enviar mensagens e recebê-las de Hubs de Eventos.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a>Exemplo de código

O código a seguir cria um cliente Hubs de Eventos e envia uma mensagem para o hub.

```csharp
EventHubsConnectionStringBuilder connectionStringBuilder = new EventHubsConnectionStringBuilder(eventHubConnectionString)
{
    EntityPath = eventHubEntityPath
};

EventHubClient eventHubClient = EventHubClient.CreateFromConnectionString(connectionStringBuilder.ToString());
string message = $"Message {i}";
Console.WriteLine($"Sending message: {message}");
await eventHubClient.SendAsync(new EventData(Encoding.UTF8.GetBytes(message)));
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento de Hubs de Eventos para criar, atualizar e remover hubs e grupos de consumidores.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a>Exemplo de código

O código a seguir cria um novo hub de eventos.

```csharp
TokenCredentials creds = new TokenCredentials(token);
EventHubManagementClient ehClient = new EventHubManagementClient(creds)
{
    SubscriptionId = subscriptionId
};

EventHubCreateOrUpdateParameters ehParams = new EventHubCreateOrUpdateParameters()
{
    Location = location
};

Console.WriteLine("Creating Event Hub...");
await ehClient.EventHubs.CreateOrUpdateAsync(resourceGroupName, namespaceName, EventHubName, ehParams);
Console.WriteLine("Created Event Hub successfully.");
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a>Tutoriais

* [Enviar eventos para Hubs de Eventos do Azure usando o .NET Framework](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [Receber eventos de Hubs de Eventos do Azure usando o .NET Framework](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a>Exemplos

* [Exemplos de Hubs de Eventos do Azure](https://github.com/Azure/azure-event-hubs/tree/master/samples)

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
