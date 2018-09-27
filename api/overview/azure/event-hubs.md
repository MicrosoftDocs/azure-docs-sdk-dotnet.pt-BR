---
title: Bibliotecas de Hubs de Eventos do Azure para .NET
description: Referência para bibliotecas de Hubs de Eventos do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: event-hubs
ms.openlocfilehash: 74c533bef598b90369009d68a759d35d122a368d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190269"
---
# <a name="azure-event-hubs-libraries-for-net"></a><span data-ttu-id="8f0ea-103">Bibliotecas de Hubs de Eventos do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="8f0ea-103">Azure Event Hubs libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="8f0ea-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="8f0ea-104">Overview</span></span>

<span data-ttu-id="8f0ea-105">Hubs de Eventos do Azure é uma plataforma de streaming de dados e um serviço de recebimento de eventos altamente escalonável.</span><span class="sxs-lookup"><span data-stu-id="8f0ea-105">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service.</span></span>

<span data-ttu-id="8f0ea-106">Para saber mais sobre os Hubs de Eventos do Azure, leia o artigo [O que são Hubs de Eventos?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span><span class="sxs-lookup"><span data-stu-id="8f0ea-106">To learn more about Azure Event Hubs, read the article [What is Event Hubs?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span></span>  <span data-ttu-id="8f0ea-107">Como introdução, confira o [guia de programação de Hubs de Eventos](/azure/event-hubs/event-hubs-programming-guide).</span><span class="sxs-lookup"><span data-stu-id="8f0ea-107">To get started, check out the [Event Hubs Programming Guide](/azure/event-hubs/event-hubs-programming-guide).</span></span>

## <a name="client-library"></a><span data-ttu-id="8f0ea-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="8f0ea-108">Client library</span></span>

<span data-ttu-id="8f0ea-109">Use o cliente Hubs de Eventos para enviar mensagens e recebê-las de Hubs de Eventos.</span><span class="sxs-lookup"><span data-stu-id="8f0ea-109">Use the Event Hubs client to send and receive messages to and from Event Hubs.</span></span>

<span data-ttu-id="8f0ea-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8f0ea-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8f0ea-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f0ea-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a><span data-ttu-id="8f0ea-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="8f0ea-112">Code Example</span></span>

<span data-ttu-id="8f0ea-113">O código a seguir cria um cliente Hubs de Eventos e envia uma mensagem para o hub.</span><span class="sxs-lookup"><span data-stu-id="8f0ea-113">The following code creates an Event Hubs client and sends a message to the hub.</span></span>

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
> [<span data-ttu-id="8f0ea-114">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="8f0ea-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a><span data-ttu-id="8f0ea-115">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="8f0ea-115">Management library</span></span>

<span data-ttu-id="8f0ea-116">Use a biblioteca de gerenciamento de Hubs de Eventos para criar, atualizar e remover hubs e grupos de consumidores.</span><span class="sxs-lookup"><span data-stu-id="8f0ea-116">Use the Event Hubs management library to create, update, and remove hubs and consumer groups.</span></span>

<span data-ttu-id="8f0ea-117">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="8f0ea-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="8f0ea-118">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f0ea-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a><span data-ttu-id="8f0ea-119">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="8f0ea-119">Code Example</span></span>

<span data-ttu-id="8f0ea-120">O código a seguir cria um novo hub de eventos.</span><span class="sxs-lookup"><span data-stu-id="8f0ea-120">The following code creates a new event hub.</span></span>

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
> [<span data-ttu-id="8f0ea-121">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="8f0ea-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a><span data-ttu-id="8f0ea-122">Tutoriais</span><span class="sxs-lookup"><span data-stu-id="8f0ea-122">Tutorials</span></span>

* [<span data-ttu-id="8f0ea-123">Enviar eventos para Hubs de Eventos do Azure usando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f0ea-123">Send events to Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [<span data-ttu-id="8f0ea-124">Receber eventos de Hubs de Eventos do Azure usando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f0ea-124">Receive events from Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a><span data-ttu-id="8f0ea-125">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8f0ea-125">Samples</span></span>

* [<span data-ttu-id="8f0ea-126">Exemplos de Hubs de Eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="8f0ea-126">Azure Event Hubs Samples</span></span>](https://github.com/Azure/azure-event-hubs/tree/master/samples)

<span data-ttu-id="8f0ea-127">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8f0ea-127">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
