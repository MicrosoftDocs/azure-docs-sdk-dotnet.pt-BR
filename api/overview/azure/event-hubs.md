---
title: Bibliotecas de Hubs de Eventos do Azure para .NET
description: "Referência para bibliotecas de Hubs de Eventos do Azure para .NET"
keywords: Azure, .NET, SDK, API, Hubs de Eventos
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 1dca44ed716e387d531661093d4c7cfc7780964b
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-event-hubs-libraries-for-net"></a><span data-ttu-id="7e89d-104">Bibliotecas de Hubs de Eventos do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="7e89d-104">Azure Event Hubs libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="7e89d-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="7e89d-105">Overview</span></span>

<span data-ttu-id="7e89d-106">Hubs de Eventos do Azure é uma plataforma de streaming de dados e um serviço de recebimento de eventos altamente escalonável.</span><span class="sxs-lookup"><span data-stu-id="7e89d-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service.</span></span>

<span data-ttu-id="7e89d-107">Para saber mais sobre os Hubs de Eventos do Azure, leia o artigo [O que são Hubs de Eventos?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span><span class="sxs-lookup"><span data-stu-id="7e89d-107">To learn more about Azure Event Hubs, read the article [What is Event Hubs?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span></span>  <span data-ttu-id="7e89d-108">Como introdução, confira o [guia de programação de Hubs de Eventos](/azure/event-hubs/event-hubs-programming-guide).</span><span class="sxs-lookup"><span data-stu-id="7e89d-108">To get started, check out the [Event Hubs Programming Guide](/azure/event-hubs/event-hubs-programming-guide).</span></span>

## <a name="client-library"></a><span data-ttu-id="7e89d-109">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="7e89d-109">Client library</span></span>

<span data-ttu-id="7e89d-110">Use o cliente Hubs de Eventos para enviar mensagens e recebê-las de Hubs de Eventos.</span><span class="sxs-lookup"><span data-stu-id="7e89d-110">Use the Event Hubs client to send and receive messages to and from Event Hubs.</span></span>

<span data-ttu-id="7e89d-111">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="7e89d-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="7e89d-112">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e89d-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a><span data-ttu-id="7e89d-113">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="7e89d-113">Code Example</span></span>

<span data-ttu-id="7e89d-114">O código a seguir cria um cliente Hubs de Eventos e envia uma mensagem para o hub.</span><span class="sxs-lookup"><span data-stu-id="7e89d-114">The following code creates an Event Hubs client and sends a message to the hub.</span></span>

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
> [<span data-ttu-id="7e89d-115">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="7e89d-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a><span data-ttu-id="7e89d-116">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="7e89d-116">Management library</span></span>

<span data-ttu-id="7e89d-117">Use a biblioteca de gerenciamento de Hubs de Eventos para criar, atualizar e remover hubs e grupos de consumidores.</span><span class="sxs-lookup"><span data-stu-id="7e89d-117">Use the Event Hubs management library to create, update, and remove hubs and consumer groups.</span></span>

<span data-ttu-id="7e89d-118">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="7e89d-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="7e89d-119">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e89d-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a><span data-ttu-id="7e89d-120">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="7e89d-120">Code Example</span></span>

<span data-ttu-id="7e89d-121">O código a seguir cria um novo hub de eventos.</span><span class="sxs-lookup"><span data-stu-id="7e89d-121">The following code creates a new event hub.</span></span>

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
> [<span data-ttu-id="7e89d-122">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="7e89d-122">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a><span data-ttu-id="7e89d-123">Tutoriais</span><span class="sxs-lookup"><span data-stu-id="7e89d-123">Tutorials</span></span>

* [<span data-ttu-id="7e89d-124">Enviar eventos para Hubs de Eventos do Azure usando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7e89d-124">Send events to Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [<span data-ttu-id="7e89d-125">Receber eventos de Hubs de Eventos do Azure usando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7e89d-125">Receive events from Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a><span data-ttu-id="7e89d-126">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7e89d-126">Samples</span></span>

* [<span data-ttu-id="7e89d-127">Exemplos de Hubs de Eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="7e89d-127">Azure Event Hubs Samples</span></span>](https://github.com/Azure/azure-event-hubs/tree/master/samples)

<span data-ttu-id="7e89d-128">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7e89d-128">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
