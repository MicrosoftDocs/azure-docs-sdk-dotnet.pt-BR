---
title: "Bibliotecas do Barramento de Serviço para .NET"
description: "Referência para bibliotecas do Barramento de Serviço do Azure para .NET"
keywords: "Azure, .NET, SDK, API, Barramento de Serviço"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 08/01/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: d4d3ac982794fc7533b97fe8c053730b4b39ff58
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-service-bus-libraries-for-net"></a>Bibliotecas do Barramento de Serviço para .NET

## <a name="overview"></a>Visão geral

O [Barramento de Serviço do Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) é uma infraestrutura de mensagens situada entre os aplicativos, permitindo que eles troquem mensagens para melhor dimensionamento e resiliência.

## <a name="client-library"></a>Biblioteca do cliente

Instale o [pacote NuGet](https://www.nuget.org/packages/WindowsAzure.ServiceBus) diretamente do [console do Gerenciador de Pacotes][PackageManager].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package WindowsAzure.ServiceBus
```

### <a name="code-example"></a>Exemplo de código

Este exemplo envia uma mensagem para uma fila do Barramento de Serviço.

```csharp
// using Microsoft.ServiceBus.Messaging;

QueueClient client = QueueClient.CreateFromConnectionString(connectionString, queueName);
BrokeredMessage message = new BrokeredMessage("This is a test message!");
client.Send(message);
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a>Biblioteca de gerenciamento

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a>Exemplo de código

Este exemplo cria uma fila do Barramento de Serviço com um tamanho máximo de 1024 MB.

```csharp
// using Microsoft.Azure.Management.ServiceBus.Fluent;
// using Microsoft.Azure.Management.ServiceBus.Fluent.Models;

using (ServiceBusManagementClient client = new ServiceBusManagementClient(credentials))
{
    client.SubscriptionId = subscriptionId;
    QueueInner parameters = new QueueInner
    {
        MaxSizeInMegabytes = 1024
    };
    await client.Queues.CreateOrUpdateAsync(resourceGroupName, namespaceName, queueName, parameters);
}
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a>Exemplos

- [Fundamentos da Fila do Barramento de Serviço - .NET](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/)
- [Funcionalidades avançadas da Fila do Barramento de Serviço - .NET](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/)
- [Fundamentos de Publicação/Assinatura do Barramento de Serviço - .NET](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/)
- [Recursos avançados de Publicação/Assinatura do Barramento de Serviço - .NET](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/)
- [Barramento de Serviço com autorização baseada em declarações - .NET](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?term=service+bus) de exemplos do Barramento de Serviço.


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
