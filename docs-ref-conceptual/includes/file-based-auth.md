---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: 7f7c24957d2bc0574fc0b1bf2a8ae8fe8b4dfc64
ms.sourcegitcommit: e25b6ac74033f3b0a7610bf66feb654acb43054c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53430505"
---
<span data-ttu-id="69862-101">Crie um arquivo de texto chamado `azureauth.json`.</span><span class="sxs-lookup"><span data-stu-id="69862-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="69862-102">Cole o saída do JSON exibida quando criou a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="69862-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="69862-103">Salve esse arquivo em um local seguro no sistema onde o seu código possa lê-lo.</span><span class="sxs-lookup"><span data-stu-id="69862-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="69862-104">Use o PowerShell para definir uma variável de ambiente denominada `AZURE_AUTH_LOCATION` com o caminho completo para o arquivo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="69862-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
