---
title: Bibliotecas de Hubs de Notificação do Azure para .NET
description: Referência para bibliotecas de Hubs de Notificação do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: notification-hubs
ms.openlocfilehash: 750a51e8dfa7323f6afb54735b4bfc517f9ec15f
ms.sourcegitcommit: 4b68c73652cb7e44cf4db36f70cb33a17dd863ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58085833"
---
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="218ce-103">Bibliotecas de Hubs de Notificação do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="218ce-103">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="218ce-104">Os Hubs de Notificação do Azure fornecem um mecanismo de envio por push fácil de usar, multiplataforma e dimensionável.</span><span class="sxs-lookup"><span data-stu-id="218ce-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="218ce-105">Com uma chamada à API única entre plataformas, você pode enviar notificações por push direcionadas e personalizadas para qualquer plataforma móvel de qualquer back-end local ou em nuvem.</span><span class="sxs-lookup"><span data-stu-id="218ce-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="218ce-106">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="218ce-106">Client library</span></span>

<span data-ttu-id="218ce-107">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="218ce-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

> [!NOTE]
> <span data-ttu-id="218ce-108">O [pacote NuGet dos Hubs de Notificação do Azure](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) agora dá suporte ao .NET Standard, que permite usar o .NET Core para a utilização em back-end dos Hubs de Notificação</span><span class="sxs-lookup"><span data-stu-id="218ce-108">The [Azure Notification Hubs NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) now supports .NET Standard, which allows using .NET core for backend use of Notifications Hubs</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="218ce-109">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="218ce-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="218ce-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="218ce-110">Code Example</span></span>

<span data-ttu-id="218ce-111">Este exemplo se conecta a um Hub de Notificação e envia uma mensagem do Serviço de Notificações por Push do Windows (WNS).</span><span class="sxs-lookup"><span data-stu-id="218ce-111">This example connects to a Notification Hub and sends a Windows Push Notification Service (WNS) message.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="218ce-112">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="218ce-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)

## <a name="management-library"></a><span data-ttu-id="218ce-113">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="218ce-113">Management library</span></span>

<span data-ttu-id="218ce-114">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="218ce-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="218ce-115">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="218ce-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="218ce-116">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="218ce-116">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="218ce-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="218ce-117">Samples</span></span>

- [<span data-ttu-id="218ce-118">Introdução ao Windows Universal</span><span class="sxs-lookup"><span data-stu-id="218ce-118">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
