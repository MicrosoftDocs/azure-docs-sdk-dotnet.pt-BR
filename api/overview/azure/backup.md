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
# <a name="azure-backup-libraries-for-net"></a>Bibliotecas do Backup do Azure para .NET

## <a name="overview"></a>Visão geral

O Backup do Azure é o serviço de nuvem que você pode usar para fazer backup, proteger e restaurar os dados.

Saiba mais sobre o Backup do Azure lendo [O que é o Backup do Azure?](/azure/backup/backup-introduction-to-azure-backup).

## <a name="management-library"></a>Biblioteca de gerenciamento

Use a biblioteca de gerenciamento de backups para gerenciar backups e configurar cofres dos Serviços de Recuperação.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

O exemplo de código a seguir usa a biblioteca de gerenciamento para acionar um backup.

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/backup/management)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
