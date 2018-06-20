---
title: Bibliotecas dos Serviços de Mídia do Azure para .NET
description: Referência para bibliotecas dos Serviços de Mídia do Azure para .NET
keywords: Azure, .NET, SDK, API, Serviços de Mídia
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: media-services
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 872ed60363c0c886e9844d0cb0bef07cf41a0242
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2017
ms.locfileid: "23487439"
---
# <a name="azure-media-services-libraries-for-net"></a><span data-ttu-id="92e07-104">Bibliotecas dos Serviços de Mídia do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="92e07-104">Azure Media Services libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="92e07-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="92e07-105">Overview</span></span>

<span data-ttu-id="92e07-106">Os Serviços de Mídia do Microsoft Azure tratam-se de uma plataforma extensível baseada em nuvem que permite aos desenvolvedores compilar aplicativos de gerenciamento e entrega de mídia escalonável.</span><span class="sxs-lookup"><span data-stu-id="92e07-106">Microsoft Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="92e07-107">Os serviços de mídia se baseiam em APIs REST que permitem que você carregue com segurança, armazene, codifique e empacote o conteúdo de áudio ou vídeo para entrega de streaming sob demanda e ao vivo para vários clientes (por exemplo, TV, PCs e dispositivos móveis).</span><span class="sxs-lookup"><span data-stu-id="92e07-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span> 

<span data-ttu-id="92e07-108">Para saber mais, confira [Visão Geral](/azure/media-services/media-services-overview) e [Introdução ao .NET](/azure/media-services/media-services-dotnet-how-to-use).</span><span class="sxs-lookup"><span data-stu-id="92e07-108">To learn more, see [Overview](/azure/media-services/media-services-overview) and [Getting started with .NET](/azure/media-services/media-services-dotnet-how-to-use).</span></span> 

## <a name="client-library"></a><span data-ttu-id="92e07-109">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="92e07-109">Client library</span></span>

<span data-ttu-id="92e07-110">A biblioteca do SDK do .NET dos Serviços de Mídia do Azure permite que você programe em relação aos serviços de mídia usando o .NET.</span><span class="sxs-lookup"><span data-stu-id="92e07-110">The Azure Media Services .NET SDK library enables you to program against Media Services using .NET.</span></span> <span data-ttu-id="92e07-111">Use a biblioteca de cliente dos Serviços de Mídia do Azure para se conectar, autenticar e desenvolver com APIs dos Serviços de Mídia.</span><span class="sxs-lookup"><span data-stu-id="92e07-111">Use the Azure Media Services client library to connect, authenticate, and develop against Media Services APIs.</span></span>  

<span data-ttu-id="92e07-112">Para saber mais, confira [Introdução ao fornecimento de conteúdo sob demanda usando o SDK do .NET](/azure/media-services/media-services-dotnet-get-started).</span><span class="sxs-lookup"><span data-stu-id="92e07-112">For more information, see [Get started with delivering content on demand using .NET SDK](/azure/media-services/media-services-dotnet-get-started).</span></span>

<span data-ttu-id="92e07-113">Instale o [pacote NuGet](https://www.nuget.org/packages/windowsazure.mediaservices) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="92e07-113">Install the [NuGet package](https://www.nuget.org/packages/windowsazure.mediaservices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="92e07-114">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="92e07-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package windowsazure.mediaservices
```

### <a name="code-example"></a><span data-ttu-id="92e07-115">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="92e07-115">Code Example</span></span>

<span data-ttu-id="92e07-116">O exemplo de código a seguir usa o SDK .NET dos Serviços de Mídia para executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="92e07-116">The following code example uses Media Services .NET SDK to perform the following tasks:</span></span>

- <span data-ttu-id="92e07-117">Crie um trabalho de codificação.</span><span class="sxs-lookup"><span data-stu-id="92e07-117">Create an encoding job.</span></span>
- <span data-ttu-id="92e07-118">Obtenha uma referência para o Codificador de Mídia Padrão.</span><span class="sxs-lookup"><span data-stu-id="92e07-118">Get a reference to the Media Encoder Standard encoder.</span></span>
- <span data-ttu-id="92e07-119">Especifique para usar a predefinição Transmissão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="92e07-119">Specify to use the Adaptive Streaming preset.</span></span>
- <span data-ttu-id="92e07-120">Adicione uma única tarefa de codificação para o trabalho.</span><span class="sxs-lookup"><span data-stu-id="92e07-120">Add a single encoding task to the job.</span></span>
- <span data-ttu-id="92e07-121">Especifique o ativo de entrada a ser codificado.</span><span class="sxs-lookup"><span data-stu-id="92e07-121">Specify the input asset to be encoded.</span></span>
- <span data-ttu-id="92e07-122">Crie um ativo de saída para receber o ativo codificado.</span><span class="sxs-lookup"><span data-stu-id="92e07-122">Create an output asset to receive the encoded asset.</span></span>
- <span data-ttu-id="92e07-123">Enviar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="92e07-123">Submit the job.</span></span>


```csharp
/* Include this 'using' directive:
using Microsoft.WindowsAzure.MediaServices.Client;
*/

CloudMediaContext context = new CloudMediaContext(new Uri(mediaServiceRESTAPIEndpoint), tokenProvider);

// Get an uploaded asset.
IAsset asset = context.Assets.FirstOrDefault();

// Encode and generate the output using the "Adaptive Streaming" preset.
// Declare a new job.
IJob job = context.Jobs.Create("Media Encoder Standard Job");
// Get a media processor reference, and pass to it the name of the 
// processor to use for the specific task.
IMediaProcessor processor = context.MediaProcessors.Where(p => p.Name == mediaProcessorName)
    .ToList().OrderBy(p => new Version(p.Version)).LastOrDefault();
if (processor == null) 
{
    throw new ArgumentException(string.Format("Unknown media processor", mediaProcessorName));
}

// Create a task with the encoding details, using a string preset.
// In this case "Adaptive Streaming" preset is used.
ITask task = job.Tasks.AddNew("My encoding task", processor, "Adaptive Streaming", TaskOptions.None);

// Specify the input asset to be encoded.
task.InputAssets.Add(asset);
// Add an output asset to contain the results of the job. 
// This output is specified as AssetCreationOptions.None, which 
// means the output asset is not encrypted. 
task.OutputAssets.AddNew("Output asset", AssetCreationOptions.None);

job.Submit();
job.GetExecutionProgressTask(CancellationToken.None).Wait();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="92e07-124">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="92e07-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/mediaservices/client)

## <a name="samples"></a><span data-ttu-id="92e07-125">Exemplos</span><span class="sxs-lookup"><span data-stu-id="92e07-125">Samples</span></span>

- [<span data-ttu-id="92e07-126">Transmita seu conteúdo HLS protegido com o Apple FairPlay</span><span class="sxs-lookup"><span data-stu-id="92e07-126">Stream your HLS content Protected with Apple FairPlay</span></span>](https://azure.microsoft.com/resources/samples/media-services-dotnet-dynamic-encryption-with-fairplay/)
- [<span data-ttu-id="92e07-127">Copiar blob em um ativo dos Serviços de Mídia do Azure usando as extensões do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="92e07-127">Copy blob into an Azure Media Services asset using .NET SDK Extensions</span></span>](https://azure.microsoft.com/resources/samples/media-services-dotnet-copy-blob-into-asset/)
- [<span data-ttu-id="92e07-128">Codificar e entregar um Live Stream com os Serviços de Mídia do Azure usando o SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="92e07-128">Encode and Deliver a Live Stream with Azure Media Services using .NET SDK</span></span>](https://azure.microsoft.com/resources/samples/media-services-dotnet-encode-live-stream-with-ams-clear/)

<span data-ttu-id="92e07-129">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services) de exemplos dos Serviços de Mídia do Azure.</span><span class="sxs-lookup"><span data-stu-id="92e07-129">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services) of Azure Media Services samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
