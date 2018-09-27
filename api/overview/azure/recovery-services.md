---
title: Bibliotecas de Serviços de Recuperação e Backup do Azure para .NET
description: Referência para as bibliotecas de Serviços de Recuperação e Backup do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: recovery-services
ms.openlocfilehash: c0381ce9a566b5371faca24307edc7b26174e785
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190780"
---
# <a name="azure-recovery-services-and-backup-libraries-for-net"></a><span data-ttu-id="bc426-103">Bibliotecas de Serviços de Recuperação e Backup do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="bc426-103">Azure Recovery Services and Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="bc426-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="bc426-104">Overview</span></span>

<span data-ttu-id="bc426-105">Os Serviços de Recuperação do Azure são um conjunto de serviços para a recuperação de dados, incluindo o [Backup do Azure](/azure/backup/) e o [Azure Site Recovery](/azure/site-recovery/).</span><span class="sxs-lookup"><span data-stu-id="bc426-105">Azure Recovery Services is a suite of services for data recovery, including [Azure Backup](/azure/backup/) and [Azure Site Recovery](/azure/site-recovery/).</span></span>

## <a name="management-library"></a><span data-ttu-id="bc426-106">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bc426-106">Management library</span></span>

<span data-ttu-id="bc426-107">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="bc426-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="bc426-108">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc426-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

#### <a name="net-core-cli"></a><span data-ttu-id="bc426-109">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bc426-109">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="bc426-110">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bc426-110">Explore the management APIs</span></span>](/dotnet/api/overview/azure/recoveryservices/management)


## <a name="code-example"></a><span data-ttu-id="bc426-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="bc426-111">Code Example</span></span>

<span data-ttu-id="bc426-112">O exemplo de código a seguir usa a biblioteca de gerenciamento para acionar um backup.</span><span class="sxs-lookup"><span data-stu-id="bc426-112">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
