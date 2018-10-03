---
title: Bibliotecas de Grade de Eventos do Azure para .NET
description: Referência para Bibliotecas de Grade de Eventos do Azure para .NET
ms.date: 04/16/2018
ms.topic: reference
ms.service: event-grid
ms.openlocfilehash: 5b19f8aa8b28b3e4aef528da051b6e7d177f1a2f
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190389"
---
# <a name="azure-event-grid-libraries-for-net"></a><span data-ttu-id="9f112-103">Bibliotecas de Grade de Eventos do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="9f112-103">Azure Event Grid libraries for .NET</span></span>

<span data-ttu-id="9f112-104">Crie aplicativos orientados para eventos que escutam e reagem a eventos de serviços do Azure e fontes personalizadas usando a manipulação de eventos simples com base em HTTP com a Grade de Eventos do Azure.</span><span class="sxs-lookup"><span data-stu-id="9f112-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="9f112-105">[Saiba mais](/azure/event-grid/overview) sobre a Grade de Eventos do Azure e começar a usar o [tutorial de eventos do armazenamento de Blobs do Azure](/azure/storage/blobs/storage-blob-event-quickstart-powershell).</span><span class="sxs-lookup"><span data-stu-id="9f112-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart-powershell).</span></span> 

## <a name="client-sdk"></a><span data-ttu-id="9f112-106">SDK do cliente</span><span class="sxs-lookup"><span data-stu-id="9f112-106">Client SDK</span></span>

<span data-ttu-id="9f112-107">Crie eventos, autentique e publique tópicos usando o SDK do cliente da Grade de Eventos do Azure.</span><span class="sxs-lookup"><span data-stu-id="9f112-107">Create events, authenticate, and post to topics using the Azure Event Grid Client SDK.</span></span>

<span data-ttu-id="9f112-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9f112-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9f112-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9f112-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="9f112-110">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f112-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.EventGrid 
```

### <a name="publish-events"></a><span data-ttu-id="9f112-111">Publicar eventos</span><span class="sxs-lookup"><span data-stu-id="9f112-111">Publish events</span></span>

<span data-ttu-id="9f112-112">O código a seguir autentica com o Azure e publica uma `List` de eventos `EventGridEvent` de um tipo personalizado (neste exemplo, `Contoso.Items.ItemsReceivedEvent`) para um tópico.</span><span class="sxs-lookup"><span data-stu-id="9f112-112">The following code authenticates with Azure and publishes a `List` of  `EventGridEvent` events of a custom type (in this example, `Contoso.Items.ItemsReceivedEvent` ) to a topic.</span></span> <span data-ttu-id="9f112-113">O tópico-chave e o endereço de ponto de extremidade usado no exemplo pode ser recuperado do Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9f112-113">The topic key and endpoint address used in the sample can be retrieved from Azure PowerShell:</span></span>

```powershell
$endpoint = (Get-AzureRmEventGridTopic -ResourceGroupName gridResourceGroup -Name <topic-name>).Endpoint
$keys = Get-AzureRmEventGridTopicKey -ResourceGroupName gridResourceGroup -Name <topic-name>
```

```csharp
string topicEndpoint = "https://<topic-name>.<region>-1.eventgrid.azure.net/api/events";
string topicKey = "<topic-key>";
string topicHostname = new Uri(topicEndpoint).Host;

TopicCredentials topicCredentials = new TopicCredentials(topicKey);
EventGridClient client = new EventGridClient(topicCredentials);

client.PublishEventsAsync(topicHostname, GetEventsList()).GetAwaiter().GetResult();
Console.Write("Published events to Event Grid.");

static IList<EventGridEvent> GetEventsList()
{
    List<EventGridEvent> eventsList = new List<EventGridEvent>();
    for (int i = 0; i < 1; i++)
    {
        eventsList.Add(new EventGridEvent()
        {
            Id = Guid.NewGuid().ToString(),
            EventType = "Contoso.Items.ItemReceivedEvent",
            Data = new ContosoItemReceivedEventData()
            {
                ItemUri = "ContosoSuperItemUri"
            },

            EventTime = DateTime.Now,
            Subject = "Door1",
            DataVersion = "2.0"
        });
    }
    return eventsList;
}
```

### <a name="consume-events"></a><span data-ttu-id="9f112-114">Consumir eventos</span><span class="sxs-lookup"><span data-stu-id="9f112-114">Consume events</span></span>

<span data-ttu-id="9f112-115">Esse snippet consome eventos, incluindo um evento personalizado `Contoso.Items.ItemsReceived` assim como eventos disparados de outros serviços do Azure, tais como o Armazenamento de Blobs.</span><span class="sxs-lookup"><span data-stu-id="9f112-115">This snippet consumes events, including a custom event `Contoso.Items.ItemsReceived` as well as events triggered from other Azure services, such as Blob Storage.</span></span>

```csharp
string response = string.Empty;
string requestContent = await req.Content.ReadAsStringAsync();

EventGridSubscriber eventGridSubscriber = new EventGridSubscriber();

// Optionally add one or more custom event type mappings
eventGridSubscriber.AddOrUpdateCustomEventMapping("Contoso.Items.ItemReceived", typeof(ContosoItemReceivedEventData));

var events = eventGridSubscriber.DeserializeEventGridEvents(requestContent);            
 
foreach (EventGridEvent receivedEvent in events)
{
    if (receivedEvent.Data is SubscriptionValidationEventData)
    {
        SubscriptionValidationEventData eventData = (SubscriptionValidationEventData)receivedEvent.Data;
        log.Info($"Got SubscriptionValidation event data, validationCode: {eventData.ValidationCode},  validationUrl: {eventData.ValidationUrl}, topic: {eventGridEvent.Topic}");
        // Handle subscription validation
    }
    else if (receivedEvent.Data is StorageBlobCreatedEventData)
    {
        StorageBlobCreatedEventData eventData = (StorageBlobCreatedEventData)receivedEvent.Data;
        log.Info($"Got BlobCreated event data, blob URI {eventData.Url}");
        // Handle StorageBlobCreatedEventData
    }
    else if (receivedEvent.Data is ContosoItemReceivedEventData)
    {
        ContosoItemReceivedEventData eventData = (ContosoItemReceivedEventData)receivedEvent.Data;
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f112-116">Explorar as APIs de publicação</span><span class="sxs-lookup"><span data-stu-id="9f112-116">Explore the publishing APIs</span></span>](/dotnet/api/overview/azure/eventgrid/publish)

## <a name="management-sdk"></a><span data-ttu-id="9f112-117">SDK de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9f112-117">Management SDK</span></span>

<span data-ttu-id="9f112-118">Crie, atualize ou exclua instâncias da Grade de Eventos, tópicos e assinaturas com o SDK de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="9f112-118">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

<span data-ttu-id="9f112-119">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="9f112-119">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9f112-120">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9f112-120">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="9f112-121">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f112-121">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.EventGrid
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f112-122">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9f112-122">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="9f112-123">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="9f112-123">Learn more</span></span>

- [<span data-ttu-id="9f112-124">Receber eventos usando o SDK de Grade de Eventos</span><span class="sxs-lookup"><span data-stu-id="9f112-124">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
