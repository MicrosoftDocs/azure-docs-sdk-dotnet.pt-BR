---
title: "Bibliotecas de Hubs de Notificação do Azure para .NET"
description: "Referência para bibliotecas de Hubs de Notificação do Azure para .NET"
keywords: "Azure, .NET, SDK, API, Hubs de Notificação"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: notification-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 9fd49ccc8d02eff09a8a53e6f1b9baa6a7a59082
ms.sourcegitcommit: 33732307162ddf6f272b0e9cc7f74eb8e6fdda1b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="azure-notification-hubs-libraries-for-net"></a>Bibliotecas de Hubs de Notificação do Azure para .NET

Os Hubs de Notificação do Azure fornecem um mecanismo de envio por push fácil de usar, multiplataforma e dimensionável. Com uma chamada à API única entre plataformas, você pode enviar notificações por push direcionadas e personalizadas para qualquer plataforma móvel de qualquer back-end local ou em nuvem.

## <a name="client-library"></a>Biblioteca do cliente

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

> [!NOTE]
> Uma [nova versão de visualização do pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) agora oferece suporte ao .NET Standard, que permite aplicar o .NET Core ao uso dos Hubs de Notificação no back-end

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a>Exemplo de código

Este exemplo se conecta a um banco de dados e lê as linhas de uma tabela.

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a>Biblioteca de gerenciamento

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a>Exemplos

- [Introdução ao Windows Universal](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
