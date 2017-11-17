---
title: "Bibliotecas da Automação do Azure para .NET"
description: "Referência para bibliotecas da Automação do Azure para .NET"
keywords: "Azure, .NET, SDK, API, Automação"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: automation
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 2055a5e24d445468763c049c34a5055cea108688
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2017
---
# <a name="azure-automation-libraries-for-net"></a><span data-ttu-id="ab9e2-104">Bibliotecas da Automação do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="ab9e2-104">Azure Automation libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="ab9e2-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ab9e2-105">Overview</span></span>

<span data-ttu-id="ab9e2-106">A Automação do Microsoft Azure fornece uma maneira para os usuários automatizarem as tarefas que são normalmente executadas em ambientes de nuvem e corporativo.</span><span class="sxs-lookup"><span data-stu-id="ab9e2-106">Microsoft Azure Automation provides a way for users to automate the tasks that are commonly performed in a cloud and enterprise environment.</span></span> 

<span data-ttu-id="ab9e2-107">Saiba mais lendo a [Visão geral da Automação do Azure](/azure/automation/automation-intro).</span><span class="sxs-lookup"><span data-stu-id="ab9e2-107">Learn more by reading the [Azure Automation Overview](/azure/automation/automation-intro).</span></span>

## <a name="management-library"></a><span data-ttu-id="ab9e2-108">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="ab9e2-108">Management library</span></span>

<span data-ttu-id="ab9e2-109">Usando a biblioteca de gerenciamento para gerenciar trabalhos e runbooks e gerenciar definições de Configuração de Estado Desejado.</span><span class="sxs-lookup"><span data-stu-id="ab9e2-109">Using the management library to manage runbooks and jobs and manage Desired State Configuration settings.</span></span>

<span data-ttu-id="ab9e2-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="ab9e2-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="ab9e2-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ab9e2-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Automation
```

```bash
dotnet add package Microsoft.Azure.Management.Automation
```

### <a name="code-example"></a><span data-ttu-id="ab9e2-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="ab9e2-112">Code Example</span></span>

<span data-ttu-id="ab9e2-113">O exemplo a seguir ilustra como iniciar um novo trabalho com base em um runbook existente.</span><span class="sxs-lookup"><span data-stu-id="ab9e2-113">The following example illustrates how to start a new job based on an existing runbook.</span></span>

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
> [<span data-ttu-id="ab9e2-114">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="ab9e2-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/automation/management)

## <a name="samples"></a><span data-ttu-id="ab9e2-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ab9e2-115">Samples</span></span>

* <span data-ttu-id="ab9e2-116">O [AzureBot](https://github.com/Microsoft/AzureBot) usa a biblioteca de automação com o [Bot Framework](https://docs.microsoft.com/bot-framework/) e os [Serviços Cognitivos](/cognitive-services) para melhorar a produtividade do desenvolvedor no Azure</span><span class="sxs-lookup"><span data-stu-id="ab9e2-116">[AzureBot](https://github.com/Microsoft/AzureBot) uses the automation library with the [Bot Framework](https://docs.microsoft.com/bot-framework/) and [Cognitive Services](/cognitive-services) to improve developer productivity on Azure</span></span>

<span data-ttu-id="ab9e2-117">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ab9e2-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
