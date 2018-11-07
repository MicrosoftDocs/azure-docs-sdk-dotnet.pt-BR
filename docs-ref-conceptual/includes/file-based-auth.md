---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: 7f7c24957d2bc0574fc0b1bf2a8ae8fe8b4dfc64
ms.sourcegitcommit: 70982e900bd4adfbc121eba55d94544f17c6b495
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51196039"
---
<span data-ttu-id="0bdd8-101">Crie um arquivo de texto chamado `azureauth.json`.</span><span class="sxs-lookup"><span data-stu-id="0bdd8-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="0bdd8-102">Cole o saída do JSON exibida quando criou a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="0bdd8-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="0bdd8-103">Salve esse arquivo em um local seguro no sistema onde o seu código possa lê-lo.</span><span class="sxs-lookup"><span data-stu-id="0bdd8-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="0bdd8-104">Use o PowerShell para definir uma variável de ambiente denominada `AZURE_AUTH_LOCATION` com o caminho completo para o arquivo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0bdd8-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
