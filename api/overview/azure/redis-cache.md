---
title: Bibliotecas do Cache Redis do Azure para .NET
description: "Referência para bibliotecas do Cache Redis do Azure para .NET"
keywords: Azure, .NET, SDK, API, Cache Redis
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/31/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: redis-cache
ms.openlocfilehash: 2316a179712b143b7e099f4592035c489d270bc3
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-redis-cache-libraries-for-net"></a><span data-ttu-id="70421-104">Bibliotecas do Cache Redis do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="70421-104">Azure Redis Cache libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="70421-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="70421-105">Overview</span></span>

<span data-ttu-id="70421-106">O Cache Redis do Azure é um cache de dados seguro e agente de mensagens que fornece alta taxa de transferência e acesso de baixa latência a dados para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="70421-106">Azure Redis Cache is a secure data cache and messaging broker that provides high throughput and low-latency access to data for applications.</span></span>  <span data-ttu-id="70421-107">Para saber mais, confira [Como usar o Cache Redis do Azure](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).</span><span class="sxs-lookup"><span data-stu-id="70421-107">For more information, see [How to Use Redis Cache](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).</span></span>

## <a name="client-library"></a><span data-ttu-id="70421-108">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="70421-108">Client library</span></span>

<span data-ttu-id="70421-109">O Cache Redis do Azure é compatível com qualquer API de cliente Redis, incluindo `StackExchange.Redis`.</span><span class="sxs-lookup"><span data-stu-id="70421-109">Azure Redis Cache is compatible with any Redis client API, including `StackExchange.Redis`.</span></span>

<span data-ttu-id="70421-110">Instale o [pacote NuGet](https://www.nuget.org/packages/StackExchange.Redis) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="70421-110">Install the [NuGet package](https://www.nuget.org/packages/StackExchange.Redis) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="70421-111">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="70421-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package StackExchange.Redis
```

```bash
dotnet add package StackExchange.Redis
```

### <a name="example"></a><span data-ttu-id="70421-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70421-112">Example</span></span>

<span data-ttu-id="70421-113">Este exemplo conecta-se a uma instância de banco de dados do Cache Redis, adiciona algumas cadeias de caracteres ao cache por nome e as recupera novamente.</span><span class="sxs-lookup"><span data-stu-id="70421-113">This example connects to a Redis Cache database instance, adds some strings to the cache by name, and then retrieves them again.</span></span>

```csharp
/* Include this "using" directive.
using StackExchange.Redis;
*/

ConnectionMultiplexer connection = 
    ConnectionMultiplexer.Connect("contoso.redis.cache.windows.net,abortConnect=false,ssl=true,password=...");
    IDatabase cache = connection.GetDatabase();

// Perform cache operations using the cache object...
// Simple put of integral data types into the cache
cache.StringSet("key1", "value");
cache.StringSet("key2", 25);

// Simple get of data types from the cache
string key1 = cache.StringGet("key1");
int key2 = (int)cache.StringGet("key2");
```

## <a name="management-library"></a><span data-ttu-id="70421-114">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="70421-114">Management library</span></span>

<span data-ttu-id="70421-115">A biblioteca de gerenciamento do Cache Redis permite que você gerencie recursos do Cache Redis e chaves de acesso.</span><span class="sxs-lookup"><span data-stu-id="70421-115">The Redis Cache management library allows you to manage Redis Cache resources and access keys.</span></span>

<span data-ttu-id="70421-116">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="70421-116">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="70421-117">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="70421-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Redis.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Redis.Fluent
```

### <a name="example"></a><span data-ttu-id="70421-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70421-118">Example</span></span>

<span data-ttu-id="70421-119">Este exemplo cria um novo Cache Redis.</span><span class="sxs-lookup"><span data-stu-id="70421-119">This example creates a new Redis Cache.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.Redis.Fluent;
*/

IRedisCache redisCache1 = azure.RedisCaches.Define("RedisCacheName")
    .WithRegion(Region.USCentral)
    .WithNewResourceGroup("ResourceGroupName")
    .WithBasicSku()
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="70421-120">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="70421-120">Explore the management APIs</span></span>](/dotnet/api/overview/azure/rediscache/management)


## <a name="samples"></a><span data-ttu-id="70421-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="70421-121">Samples</span></span>

* [<span data-ttu-id="70421-122">Introdução ao Redis - Gerenciar o Redis - no .NET</span><span class="sxs-lookup"><span data-stu-id="70421-122">Getting Started with Redis - Manage Redis - in .NET</span></span>](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
