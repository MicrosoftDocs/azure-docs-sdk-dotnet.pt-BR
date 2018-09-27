---
title: Bibliotecas do Barramento de Serviço para .NET
description: Referência para bibliotecas do Barramento de Serviço do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: service-bus
ms.openlocfilehash: 506be9a669a2418f2437271d128a963e351442e7
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190869"
---
# <a name="azure-service-bus-libraries-for-net"></a><span data-ttu-id="5f3ba-103">Bibliotecas do Barramento de Serviço para .NET</span><span class="sxs-lookup"><span data-stu-id="5f3ba-103">Azure Service Bus libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="5f3ba-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5f3ba-104">Overview</span></span>

<span data-ttu-id="5f3ba-105">O [Barramento de Serviço do Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) é uma infraestrutura de mensagens situada entre os aplicativos, permitindo que eles troquem mensagens para melhor dimensionamento e resiliência.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-105">[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) is a messaging infrastructure that sits between applications allowing them to exchange messages for improved scale and resiliency.</span></span>

## <a name="client-library"></a><span data-ttu-id="5f3ba-106">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="5f3ba-106">Client library</span></span>

<span data-ttu-id="5f3ba-107">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.ServiceBus) diretamente do [console do Gerenciador de Pacotes][PackageManager].</span><span class="sxs-lookup"><span data-stu-id="5f3ba-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.ServiceBus) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5f3ba-108">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5f3ba-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.ServiceBus
```

### <a name="code-example"></a><span data-ttu-id="5f3ba-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5f3ba-109">Code Example</span></span>

<span data-ttu-id="5f3ba-110">Este exemplo envia uma mensagem para uma fila do Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-110">This example sends a message to a Service Bus queue.</span></span>

```csharp
// using Microsoft.Azure.ServiceBus;
// Microsoft.Azure.ServiceBus 2.0.0 (stable)

byte[] messageBody = System.Text.Encoding.Unicode.GetBytes("Hello, world!");
ServiceBusConnectionStringBuilder builder = new ServiceBusConnectionStringBuilder(connectionString);
QueueClient client = new QueueClient(builder, ReceiveMode.PeekLock);
client.SendAsync(new Message(messageBody));
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="5f3ba-111">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="5f3ba-111">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a><span data-ttu-id="5f3ba-112">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5f3ba-112">Management library</span></span>

<span data-ttu-id="5f3ba-113">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="5f3ba-113">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5f3ba-114">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5f3ba-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="5f3ba-115">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f3ba-115">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a><span data-ttu-id="5f3ba-116">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5f3ba-116">Code Example</span></span>

<span data-ttu-id="5f3ba-117">Este exemplo cria uma fila do Barramento de Serviço com um tamanho máximo de 1024 MB.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-117">This example creates a Service Bus queue with a maximum size of 1024 MB.</span></span>

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
> [<span data-ttu-id="5f3ba-118">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5f3ba-118">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a><span data-ttu-id="5f3ba-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5f3ba-119">Samples</span></span>

- [<span data-ttu-id="5f3ba-120">Fundamentos da Fila do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5f3ba-120">Service Bus Queue Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/)
- [<span data-ttu-id="5f3ba-121">Funcionalidades avançadas da Fila do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5f3ba-121">Service Bus Queue Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/)
- [<span data-ttu-id="5f3ba-122">Fundamentos de Publicação/Assinatura do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5f3ba-122">Service Bus Publish/Subscribe Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/)
- [<span data-ttu-id="5f3ba-123">Recursos avançados de Publicação/Assinatura do Barramento de Serviço - .NET</span><span class="sxs-lookup"><span data-stu-id="5f3ba-123">Service Bus Publish/Subscribe Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/)
- [<span data-ttu-id="5f3ba-124">Barramento de Serviço com autorização baseada em declarações - .NET</span><span class="sxs-lookup"><span data-stu-id="5f3ba-124">Service Bus with Claims-Based Authorization - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/)

<span data-ttu-id="5f3ba-125">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?term=service+bus) de exemplos do Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-125">View the [complete list](https://azure.microsoft.com/resources/samples/?term=service+bus) of Azure Service Bus samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
