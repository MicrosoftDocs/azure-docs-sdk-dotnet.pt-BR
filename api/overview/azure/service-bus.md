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
# <a name="azure-service-bus-libraries-for-net"></a><span data-ttu-id="5208b-104">Bibliotecas do Barramento de Serviço para .NET</span><span class="sxs-lookup"><span data-stu-id="5208b-104">Azure Service Bus libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="5208b-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5208b-105">Overview</span></span>

<span data-ttu-id="5208b-106">O [Barramento de Serviço do Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) é uma infraestrutura de mensagens situada entre os aplicativos, permitindo que eles troquem mensagens para melhor dimensionamento e resiliência.</span><span class="sxs-lookup"><span data-stu-id="5208b-106">[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) is a messaging infrastructure that sits between applications allowing them to exchange messages for improved scale and resiliency.</span></span>

## <a name="client-library"></a><span data-ttu-id="5208b-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="5208b-107">Client library</span></span>

<span data-ttu-id="5208b-108">Instale o [pacote NuGet](https://www.nuget.org/packages/WindowsAzure.ServiceBus) diretamente do [console do Gerenciador de Pacotes][PackageManager].</span><span class="sxs-lookup"><span data-stu-id="5208b-108">Install the [NuGet package](https://www.nuget.org/packages/WindowsAzure.ServiceBus) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5208b-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5208b-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package WindowsAzure.ServiceBus
```

### <a name="code-example"></a><span data-ttu-id="5208b-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5208b-110">Code Example</span></span>

<span data-ttu-id="5208b-111">Este exemplo envia uma mensagem para uma fila do Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="5208b-111">This example sends a message to a Service Bus queue.</span></span>

```csharp
// using Microsoft.ServiceBus.Messaging;

QueueClient client = QueueClient.CreateFromConnectionString(connectionString, queueName);
BrokeredMessage message = new BrokeredMessage("This is a test message!");
client.Send(message);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5208b-112">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="5208b-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a><span data-ttu-id="5208b-113">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5208b-113">Management library</span></span>

<span data-ttu-id="5208b-114">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5208b-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5208b-115">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5208b-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="5208b-116">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5208b-116">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a><span data-ttu-id="5208b-117">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5208b-117">Code Example</span></span>

<span data-ttu-id="5208b-118">Este exemplo cria uma fila do Barramento de Serviço com um tamanho máximo de 1024 MB.</span><span class="sxs-lookup"><span data-stu-id="5208b-118">This example creates a Service Bus queue with a maximum size of 1024 MB.</span></span>

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
> [<span data-ttu-id="5208b-119">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5208b-119">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a><span data-ttu-id="5208b-120">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5208b-120">Samples</span></span>

- [<span data-ttu-id="5208b-121">Fundamentos da Fila do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5208b-121">Service Bus Queue Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/)
- [<span data-ttu-id="5208b-122">Funcionalidades avançadas da Fila do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5208b-122">Service Bus Queue Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/)
- [<span data-ttu-id="5208b-123">Fundamentos de Publicação/Assinatura do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5208b-123">Service Bus Publish/Subscribe Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/)
- [<span data-ttu-id="5208b-124">Recursos avançados de Publicação/Assinatura do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5208b-124">Service Bus Publish/Subscribe Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/)
- [<span data-ttu-id="5208b-125">Barramento de Serviço com autorização baseada em declarações - .NET</span><span class="sxs-lookup"><span data-stu-id="5208b-125">Service Bus with Claims-Based Authorization - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/)

<span data-ttu-id="5208b-126">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?term=service+bus) de exemplos do Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="5208b-126">View the [complete list](https://azure.microsoft.com/resources/samples/?term=service+bus) of Azure Service Bus samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
