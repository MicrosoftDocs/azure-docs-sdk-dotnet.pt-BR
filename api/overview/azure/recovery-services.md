---
title: Bibliotecas de Serviços de Recuperação e Backup do Azure para .NET
description: Referência para as bibliotecas de Serviços de Recuperação e Backup do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: backup
ms.openlocfilehash: c2faef5c83f28cb35158609b92f0334671161d1d
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348168"
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
