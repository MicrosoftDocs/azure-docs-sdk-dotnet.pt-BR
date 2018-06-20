---
title: Bibliotecas do Azure StorSimple para .NET
description: Referência para as bibliotecas do Azure StorSimple para .NET
keywords: Azure, .NET, SDK, API, StorSimple
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/27/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: storsimple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: dcb6732bf1eded6852a3185546a09c96cfe84eca
ms.sourcegitcommit: 64c9e16e42894e8db8ed088487e55c5e0edd6861
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
ms.locfileid: "23639644"
---
# <a name="azure-storsimple-libraries-for-net"></a><span data-ttu-id="d2c72-104">Bibliotecas do Azure StorSimple para .NET</span><span class="sxs-lookup"><span data-stu-id="d2c72-104">Azure StorSimple libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="d2c72-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d2c72-105">Overview</span></span>

<span data-ttu-id="d2c72-106">O Microsoft Azure StorSimple é uma solução de armazenamento corporativo que fornece as interfaces iSCSI ou SMB físicas para o armazenamento em nuvem.</span><span class="sxs-lookup"><span data-stu-id="d2c72-106">Microsoft Azure StorSimple is an enterprise storage solution that provides physical iSCSI or SMB interfaces to cloud-based storage.</span></span> 

<span data-ttu-id="d2c72-107">Saiba mais sobre o [Azure StorSimple](/azure/storsimple/).</span><span class="sxs-lookup"><span data-stu-id="d2c72-107">Learn more about [Azure StorSimple](/azure/storsimple/).</span></span>    

## <a name="management-library"></a><span data-ttu-id="d2c72-108">Biblioteca de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d2c72-108">Management library</span></span>

<span data-ttu-id="d2c72-109">Instale o [pacote NuGet](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="d2c72-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="d2c72-110">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2c72-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StorSimple.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.StorSimple.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="d2c72-111">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d2c72-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="d2c72-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d2c72-112">Samples</span></span>

<span data-ttu-id="d2c72-113">Explore mais [códigos .NET de exemplo](https://azure.microsoft.com/resources/samples/?platform=dotnet) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d2c72-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package