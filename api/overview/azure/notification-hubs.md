---
title: Bibliotecas de Hubs de Notificação do Azure para .NET
description: Referência para bibliotecas de Hubs de Notificação do Azure para .NET
keywords: Azure, .NET, SDK, API, Hubs de Notificação
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: notification-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 0cbbfbafd2d1900c00f08fd1ab2e0f1af80ae8ff
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065496"
---
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="f136a-104">Bibliotecas de Hubs de Notificação do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="f136a-104">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="f136a-105">Os Hubs de Notificação do Azure fornecem um mecanismo de envio por push fácil de usar, multiplataforma e dimensionável.</span><span class="sxs-lookup"><span data-stu-id="f136a-105">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="f136a-106">Com uma chamada à API única entre plataformas, você pode enviar notificações por push direcionadas e personalizadas para qualquer plataforma móvel de qualquer back-end local ou em nuvem.</span><span class="sxs-lookup"><span data-stu-id="f136a-106">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="f136a-107">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="f136a-107">Client library</span></span>

<span data-ttu-id="f136a-108">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f136a-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

> [!NOTE]
> <span data-ttu-id="f136a-109">Uma [nova versão de visualização do pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) agora oferece suporte ao .NET Standard, que permite aplicar o .NET Core ao uso dos Hubs de Notificação no back-end</span><span class="sxs-lookup"><span data-stu-id="f136a-109">A [new preview version of the NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) now supports .NET Standard, which allows using .NET core for backend use of Notifications Hubs</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f136a-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f136a-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="f136a-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f136a-111">Code Example</span></span>

<span data-ttu-id="f136a-112">Este exemplo se conecta a um Hub de Notificação e envia uma mensagem do Serviço de Notificações por Push do Windows (WNS).</span><span class="sxs-lookup"><span data-stu-id="f136a-112">This example connects to a Notification Hub and sends a Windows Push Notification Service (WNS) message.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f136a-113">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="f136a-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a><span data-ttu-id="f136a-114">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f136a-114">Management library</span></span>

<span data-ttu-id="f136a-115">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="f136a-115">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f136a-116">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f136a-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f136a-117">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f136a-117">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="f136a-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f136a-118">Samples</span></span>

- [<span data-ttu-id="f136a-119">Introdução ao Windows Universal</span><span class="sxs-lookup"><span data-stu-id="f136a-119">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
