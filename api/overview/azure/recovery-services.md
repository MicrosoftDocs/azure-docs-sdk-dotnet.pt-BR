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
# <a name="azure-recovery-services-and-backup-libraries-for-net"></a>Bibliotecas de Serviços de Recuperação e Backup do Azure para .NET

## <a name="overview"></a>Visão geral

Os Serviços de Recuperação do Azure são um conjunto de serviços para a recuperação de dados, incluindo o [Backup do Azure](/azure/backup/) e o [Azure Site Recovery](/azure/site-recovery/).

## <a name="management-library"></a>Biblioteca de gerenciamento

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

#### <a name="net-core-cli"></a>CLI do .NET Core

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/recoveryservices/management)


## <a name="code-example"></a>Exemplo de código

O exemplo de código a seguir usa a biblioteca de gerenciamento para acionar um backup.

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
