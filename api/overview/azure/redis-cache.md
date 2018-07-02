---
title: Bibliotecas do Cache Redis do Azure para .NET
description: Referência para bibliotecas do Cache Redis do Azure para .NET
keywords: Azure, .NET, SDK, API, Cache Redis
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: redis-cache
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 879f42aa254103239fb0dceeb25cb99a7d5e9814
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065916"
---
# <a name="azure-redis-cache-libraries-for-net"></a>Bibliotecas do Cache Redis do Azure para .NET

## <a name="overview"></a>Visão geral

O Cache Redis do Azure é um cache de dados seguro e agente de mensagens que fornece alta taxa de transferência e acesso de baixa latência a dados para aplicativos.  Para saber mais, confira [Como usar o Cache Redis do Azure](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).

## <a name="client-library"></a>Biblioteca do cliente

O Cache Redis do Azure é compatível com qualquer API de cliente Redis, incluindo `StackExchange.Redis`.

Instale o [pacote NuGet](https://www.nuget.org/packages/StackExchange.Redis) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package StackExchange.Redis
```

```bash
dotnet add package StackExchange.Redis
```

### <a name="example"></a>Exemplo

Este exemplo conecta-se a uma instância de banco de dados do Cache Redis, adiciona algumas cadeias de caracteres ao cache por nome e as recupera novamente.

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

## <a name="management-library"></a>Biblioteca de gerenciamento

A biblioteca de gerenciamento do Cache Redis permite que você gerencie recursos do Cache Redis e chaves de acesso.

Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Management.Redis.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Redis.Fluent
```

### <a name="example"></a>Exemplo

Este exemplo cria um novo Cache Redis.

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
> [Explorar as APIs de gerenciamento](/dotnet/api/overview/azure/rediscache/management)


## <a name="samples"></a>Exemplos

* [Introdução ao Redis - Gerenciar o Redis - no .NET](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
