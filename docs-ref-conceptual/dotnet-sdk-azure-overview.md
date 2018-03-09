---
title: APIs do .NET do Azure
description: "Visão geral das APIs do Azure para .NET"
keywords: Azure, .NET, SDK, API, o NuGet, bibliotecas, pacotes
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 26360a516220ca9d3e8901e60cb23ecbd02863cd
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="azure-net-apis"></a>APIs do .NET do Azure

As APIs do .NET do Azure permitem que você use serviços Azure e gerencie recursos do Azure no código do seu aplicativo. As APIs estão disponíveis como [pacotes NuGet](/dotnet/api/overview/azure/) para uso em seus projetos .NET. 

## <a name="manage-azure-resources"></a>Gerenciar recursos do Azure

As bibliotecas do Azure para .NET permitem criar e gerenciar recursos do Azure em aplicativos .NET.

Muitos dos pacotes de gerenciamento de recursos do Azure têm uma interface [fluente](dotnet-sdk-azure-concepts.md) para configurar recursos exatamente de acordo com suas especificações. Por exemplo, para criar uma VM Windows, você deve escrever o código abaixo:

```csharp
var windowsVM = azure.VirtualMachines.Define(windowsVmName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername(username)
    .WithAdminPassword(password)
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
 ```

Examine a [lista de serviços .NET](/dotnet/api/overview/azure/) para começar a usar as bibliotecas em seus projetos imediatamente. Em seguida, leia o [artigo de introdução](dotnet-sdk-azure-get-started.md) para configurar a autenticação e executar o código de exemplo em sua própria assinatura do Azure.  O [artigo de conceitos](dotnet-sdk-azure-concepts.md) mostra as convenções que o SDK usa e como aproveitá-las para simplificar o código do aplicativo. Novos recursos, alterações significativas e instruções de migração estão disponíveis nas [notas de versão](dotnet-sdk-azure-release-notes.md).

## <a name="consume-azure-services"></a>Consumir serviços do Azure

Além de usar as APIs do .NET para criar e gerenciar programaticamente os recursos no Azure, você pode também usar APIs do .NET para conectar seus aplicativos a esses recursos e usá-los no tempo de execução.  Por exemplo, você pode se conectar a um Banco de Dados SQL ou armazenar dados no Armazenamento do Azure.  Você pode identificar qual pacote de NuGet será usado para um determinado serviço do Azure navegando nossa [lista completa de APIs de serviço](/dotnet/api/overview/azure/).  

## <a name="samples"></a>Exemplos

Os exemplos a seguir abordam tarefas comuns de automação com as bibliotecas do Azure para .NET:

- [Máquinas virtuais](dotnet-sdk-azure-virtual-machine-samples.md)
- [Aplicativos Web](dotnet-sdk-azure-web-apps-samples.md)
- [Banco de Dados SQL](dotnet-sdk-azure-sql-database-samples.md)

Uma [referência](/dotnet/api/overview/azure/?view=azure-dotnet) unificada está disponível para todos os pacotes nas bibliotecas de serviço e de gerenciamento. Novos recursos, alterações significativas e instruções de migração estão disponíveis nas [notas de versão](dotnet-sdk-azure-release-notes.md).

[!include[Contribute and community](includes/contribute.md)]