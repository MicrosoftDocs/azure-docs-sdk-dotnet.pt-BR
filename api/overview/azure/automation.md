---
title: "Bibliotecas da Automação do Azure para .NET"
description: "Referência para bibliotecas da Automação do Azure para .NET"
keywords: "Azure, .NET, SDK, API, Automação"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 1e1b5a662947503ff71f3e4a9b67f20a1e2d5f87
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-automation-libraries-for-net"></a>Bibliotecas da Automação do Azure para .NET

## <a name="overview"></a>Visão geral

A Automação do Microsoft Azure fornece uma maneira para os usuários automatizarem as tarefas que são normalmente executadas em ambientes de nuvem e corporativo. 

Saiba mais lendo a [Visão geral da Automação do Azure](/azure/automation/automation-intro).

## <a name="management-library"></a>Biblioteca de gerenciamento

Usando a biblioteca de gerenciamento para gerenciar trabalhos e runbooks e gerenciar definições de Configuração de Estado Desejado.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Automation
```

```bash
dotnet add package Microsoft.Azure.Management.Automation
```

### <a name="code-example"></a>Exemplo de código

O exemplo a seguir ilustra como iniciar um novo trabalho com base em um runbook existente.

```csharp
/*
  using Microsoft.Azure.Management.Automation;
*/
AutomationManagementClient client =
    new AutomationManagementClient(new CertificateCloudCredentials(subscriptionId, cert));

// Create job create parameters
JobCreateParameters jcParam = new JobCreateParameters
{
    Properties = new JobCreateProperties
    {
        Runbook = new RunbookAssociationProperty
        {
            Name = runbookName
        },
        Parameters = null // optional parameters here
    }
};

// create runbook job. This gives back the Job
Job job = automationManagementClient.Jobs.Create(automationAccountName, jcParam).Job;
```

> [!div class="nextstepaction"]
> [Explorar as APIs de Gerenciamento](/dotnet/api/overview/azure/automation/management)

## <a name="samples"></a>Exemplos

* O [AzureBot](https://github.com/Microsoft/AzureBot) usa a biblioteca de automação com o [Bot Framework](https://docs.microsoft.com/bot-framework/) e os [Serviços Cognitivos](/cognitive-services) para melhorar a produtividade do desenvolvedor no Azure

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
