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
ms.openlocfilehash: 6fe4e3f25aa420322478dc7c10aecd055a70f5c8
ms.sourcegitcommit: 4114b8821f20e02f4185fcea7549d716f29b9c90
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2017
---
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="df05d-104">Bibliotecas de Hubs de Notificação do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="df05d-104">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="df05d-105">Os Hubs de Notificação do Azure fornecem um mecanismo de envio por push fácil de usar, multiplataforma e dimensionável.</span><span class="sxs-lookup"><span data-stu-id="df05d-105">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="df05d-106">Com uma chamada à API única entre plataformas, você pode enviar notificações por push direcionadas e personalizadas para qualquer plataforma móvel de qualquer back-end local ou em nuvem.</span><span class="sxs-lookup"><span data-stu-id="df05d-106">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="df05d-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="df05d-107">Client library</span></span>

<span data-ttu-id="df05d-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="df05d-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="df05d-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df05d-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="df05d-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="df05d-110">Code Example</span></span>

<span data-ttu-id="df05d-111">Este exemplo se conecta a um banco de dados e lê as linhas de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="df05d-111">This example connects to a database and reads rows from a table.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="df05d-112">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="df05d-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a><span data-ttu-id="df05d-113">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="df05d-113">Management library</span></span>

<span data-ttu-id="df05d-114">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="df05d-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="df05d-115">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df05d-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="df05d-116">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="df05d-116">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="df05d-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="df05d-117">Samples</span></span>

- [<span data-ttu-id="df05d-118">Introdução ao Windows Universal</span><span class="sxs-lookup"><span data-stu-id="df05d-118">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
