---
title: Bibliotecas do Backup do Azure para .NET
description: "Referência para bibliotecas do Backup do Azure para .NET"
keywords: Azure, .NET, SDK, API, Backup
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/24/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 93eeaeda1860e3b7190dfb0ae917b4b85b5a3609
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-backup-libraries-for-net"></a><span data-ttu-id="666b8-104">Bibliotecas do Backup do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="666b8-104">Azure Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="666b8-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="666b8-105">Overview</span></span>

<span data-ttu-id="666b8-106">O Backup do Azure é o serviço de nuvem que você pode usar para fazer backup, proteger e restaurar os dados.</span><span class="sxs-lookup"><span data-stu-id="666b8-106">Azure Backup is the cloud service you can use to back up, protect, and restore your data.</span></span>

<span data-ttu-id="666b8-107">Saiba mais sobre o Backup do Azure lendo [O que é o Backup do Azure?](/azure/backup/backup-introduction-to-azure-backup).</span><span class="sxs-lookup"><span data-stu-id="666b8-107">Learn more about Azure Backup by reading [What is Azure Backup?](/azure/backup/backup-introduction-to-azure-backup).</span></span>

## <a name="management-library"></a><span data-ttu-id="666b8-108">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="666b8-108">Management library</span></span>

<span data-ttu-id="666b8-109">Use a biblioteca de gerenciamento de backups para gerenciar backups e configurar cofres dos Serviços de Recuperação.</span><span class="sxs-lookup"><span data-stu-id="666b8-109">Use the backup management library to manage backups and set up Recovery Services vaults.</span></span>

<span data-ttu-id="666b8-110">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="666b8-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="666b8-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="666b8-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

<span data-ttu-id="666b8-112">O exemplo de código a seguir usa a biblioteca de gerenciamento para acionar um backup.</span><span class="sxs-lookup"><span data-stu-id="666b8-112">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="666b8-113">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="666b8-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/backup/management)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
