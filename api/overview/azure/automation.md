---
title: Bibliotecas da Automação do Azure para .NET
description: Referência para bibliotecas da Automação do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: automation
ms.openlocfilehash: 4890faab86d1319fe802a30e3735419ac65e8d64
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190279"
---
# <a name="azure-automation-libraries-for-net"></a>Bibliotecas da Automação do Azure para .NET

## <a name="overview"></a>Visão geral

A Automação do Microsoft Azure fornece uma maneira para os usuários automatizarem as tarefas que são normalmente executadas em ambientes de nuvem e corporativo. 

Saiba mais lendo a [Visão geral da Automação do Azure](/azure/automation/automation-intro).

## <a name="management-library"></a>Biblioteca de gerenciamento

Usando a biblioteca de gerenciamento para gerenciar trabalhos e runbooks e gerenciar definições de Configuração de Estado Desejado.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/automation/management)

## <a name="samples"></a>Exemplos

* O [AzureBot](https://github.com/Microsoft/AzureBot) usa a biblioteca de automação com o [Bot Framework](https://docs.microsoft.com/bot-framework/) e os [Serviços Cognitivos](/cognitive-services) para melhorar a produtividade do desenvolvedor no Azure

Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
