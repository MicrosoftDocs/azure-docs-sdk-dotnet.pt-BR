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
# <a name="azure-media-services-libraries-for-net"></a>Bibliotecas dos Serviços de Mídia do Azure para .NET

## <a name="overview"></a>Visão geral

Os Serviços de Mídia do Microsoft Azure tratam-se de uma plataforma extensível baseada em nuvem que permite aos desenvolvedores compilar aplicativos de gerenciamento e entrega de mídia escalonável. Os serviços de mídia se baseiam em APIs REST que permitem que você carregue com segurança, armazene, codifique e empacote o conteúdo de áudio ou vídeo para entrega de streaming sob demanda e ao vivo para vários clientes (por exemplo, TV, PCs e dispositivos móveis). 

Para saber mais, confira [Visão Geral](/azure/media-services/media-services-overview) e [Introdução ao .NET](/azure/media-services/media-services-dotnet-how-to-use). 

## <a name="client-library"></a>Biblioteca do cliente

A biblioteca do SDK do .NET dos Serviços de Mídia do Azure permite que você programe em relação aos serviços de mídia usando o .NET. Use a biblioteca de cliente dos Serviços de Mídia do Azure para se conectar, autenticar e desenvolver com APIs dos Serviços de Mídia.  

Para saber mais, confira [Introdução ao fornecimento de conteúdo sob demanda usando o SDK do .NET](/azure/media-services/media-services-dotnet-get-started).

Instale o [pacote NuGet](https://www.nuget.org/packages/windowsazure.mediaservices) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package windowsazure.mediaservices
```

### <a name="code-example"></a>Exemplo de código

O exemplo de código a seguir usa o SDK .NET dos Serviços de Mídia para executar as seguintes tarefas:

- Crie um trabalho de codificação.
- Obtenha uma referência para o Codificador de Mídia Padrão.
- Especifique para usar a predefinição Transmissão Adaptável.
- Adicione uma única tarefa de codificação para o trabalho.
- Especifique o ativo de entrada a ser codificado.
- Crie um ativo de saída para receber o ativo codificado.
- Enviar o trabalho.


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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/mediaservices/client)

## <a name="samples"></a>Exemplos

- [Transmita seu conteúdo HLS protegido com o Apple FairPlay](https://azure.microsoft.com/resources/samples/media-services-dotnet-dynamic-encryption-with-fairplay/)
- [Copiar blob em um ativo dos Serviços de Mídia do Azure usando as extensões do SDK do .NET](https://azure.microsoft.com/resources/samples/media-services-dotnet-copy-blob-into-asset/)
- [Codificar e entregar um Live Stream com os Serviços de Mídia do Azure usando o SDK do .NET](https://azure.microsoft.com/resources/samples/media-services-dotnet-encode-live-stream-with-ams-clear/)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services) de exemplos dos Serviços de Mídia do Azure.


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
