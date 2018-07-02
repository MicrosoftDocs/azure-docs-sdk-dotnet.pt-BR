---
title: Bibliotecas de Serviços de Recuperação e Backup do Azure para .NET
description: Referência para as bibliotecas de Serviços de Recuperação e Backup do Azure para .NET
keywords: Azure, .NET, SDK, API, Serviços de Recuperação, Backup
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: recovery-services
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 6186411b668d0950328b49bb826e5b05c5ee0304
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065426"
---
# <a name="azure-recovery-services-and-backup-libraries-for-net"></a><span data-ttu-id="073b5-104">Bibliotecas de Serviços de Recuperação e Backup do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="073b5-104">Azure Recovery Services and Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="073b5-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="073b5-105">Overview</span></span>

<span data-ttu-id="073b5-106">Os Serviços de Recuperação do Azure são um conjunto de serviços para a recuperação de dados, incluindo o [Backup do Azure](/azure/backup/) e o [Azure Site Recovery](/azure/site-recovery/).</span><span class="sxs-lookup"><span data-stu-id="073b5-106">Azure Recovery Services is a suite of services for data recovery, including [Azure Backup](/azure/backup/) and [Azure Site Recovery](/azure/site-recovery/).</span></span>

## <a name="management-library"></a><span data-ttu-id="073b5-107">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="073b5-107">Management library</span></span>

<span data-ttu-id="073b5-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="073b5-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="073b5-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="073b5-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

#### <a name="net-core-cli"></a><span data-ttu-id="073b5-110">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="073b5-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="073b5-111">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="073b5-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/recoveryservices/management)


## <a name="code-example"></a><span data-ttu-id="073b5-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="073b5-112">Code Example</span></span>

<span data-ttu-id="073b5-113">O exemplo de código a seguir usa a biblioteca de gerenciamento para acionar um backup.</span><span class="sxs-lookup"><span data-stu-id="073b5-113">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
