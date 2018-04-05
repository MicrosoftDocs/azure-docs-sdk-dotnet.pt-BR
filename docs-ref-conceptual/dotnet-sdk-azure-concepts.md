---
title: Padrões e conceitos de uso das bibliotecas de gerenciamento do Azure para .NET
description: ''
keywords: Azure, .NET, SDK, API, padrões, conceitos, fluente, registrar em log
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: b817216e114e5ab3ff22c1c5adb0f892c7874147
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="azure-management-library-for-net-fluent-concepts"></a>Conceitos fluentes da biblioteca de gerenciamento do Azure para .NET

Este artigo o ajudará a entender como usar com eficiência a interface fluente nas bibliotecas de gerenciamento do Azure para .NET.

## <a name="building-resources-using-a-fluent-interface"></a>Criando recursos usando uma interface fluente

Uma interface fluente é um formulário específico do padrão de construtor que cria objetos usando uma cadeia de métodos que impõe a configuração correta de um recurso. Por exemplo, o ponto de entrada do objeto do Azure é criado usando uma interface fluente:

```csharp
var azure = Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

## <a name="resource-collections"></a>Coleções de recursos

O objeto `Microsoft.Azure.Management.Fluent.Azure` mostrado acima é o ponto de entrada para toda a criação de recursos nas bibliotecas de gerenciamento fluentes. Selecione o tipo de recurso para trabalhar usando as coleções de recursos no objeto `Azure`. Por exemplo, para o Banco de Dados SQL:

```csharp
var sql = azure.SqlServers.Define(sqlServerName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithAdministratorLogin(administratorLogin)
    .WithAdministratorPassword(administratorPassword)
    .Create();
```

Como mostrado acima, a maioria das "conversas" mais fluentes que você tem com a API envolvem a escolha da coleção de recursos adequada aos recursos do Azure com os quais precisa trabalhar.  O IntelliSense, no Visual Studio, o orienta durante a conversa. 

![GIF do Intellisense no Visual Studio, gerando uma conversa fluente](media/dotnet-sdk-azure-concepts/vs-fluent.gif)   

## <a name="lists-and-iterations"></a>Listas e iterações

Cada coleta de recurso possui um método `List()` para retornar todas as instâncias desse recurso em sua assinatura atual. Por exemplo, `Azure.SqlServers.List()` retorna todos os servidores SQL na assinatura.

Use o método `ListByResourceGroup()` para definir o escopo da lista retornada para um determinado [grupo de recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups).  

Pesquise e itere na coleção retornada exatamente como faria com um `List<T>` normal:

```csharp
var vmList = azure.VirtualMachines.List();
foreach(var vm in vmList)
{
    Console.WriteLine("VM Name: {0}", vm.Name);
}
```   

## <a name="actionable-verbs"></a>Verbos acionáveis

Os métodos de coleção de recursos com verbos em seus nomes executam uma ação imediatamente no Azure. Esses métodos funcionam de forma síncrona e bloqueiam a execução do thread atual até que sejam concluídos. 

| Verbo   |  Amostra de uso |
|--------|---------------|
| Criar | `azure.VirtualMachines.Create(listOfVMCreatables)` |
| Aplicar  | `virtualMachineScaleSet.Update().WithCapacity(6).Apply()` |
| Excluir | `azure.Disks.DeleteById(id)` | 
| Listar   | `azure.SqlServers.List()` | 
| Obter    | `var vm  = azure.VirtualMachines.GetByResourceGroup(group, vmName)` |

>[!NOTE]
> `Define()` e `Update()` são verbos, mas não bloquearão a menos que seguidos por um `Create()` ou `Apply()`.
 
Os objetos de recurso específico têm verbos que alteram o estado do recurso no Azure. Por exemplo: 

```csharp
var vmToRestart = azure.VirtualMachines.GetById(id);
vmToRestart.Restart();
```

A maioria dos métodos descritos nesta seção também têm uma versão assíncrona, indicada pelo sufixo `Async`.

```csharp
Task restartTask = azure.VirtualMachines.GetById(id).RestartAsync();
```

## <a name="lazy-resource-creation"></a>Criação de recursos lenta

Um desafio ao criar recursos do Azure ocorre quando um novo recurso depende de outro recurso que ainda não existe. Um exemplo é a reserva de um endereço IP público e a configuração de um disco na criação de uma nova máquina virtual. Você não deseja ter de verificar a reserva do endereço ou a criação de disco; quer apenas configurar a máquina virtual com esses recursos.

Use objetos instanciáveis a fim de definir recursos do Azure para usar em seu código, mas criá-los somente quando necessário no Azure. O código criado com objetos instanciáveis repassa a criação de recursos no ambiente do Azure para a API de gerenciamento, aumentando o desempenho. 

Gere objetos instanciáveis com o verbo `Define()` da coleção de recursos sem um verbo `Create()`:

```csharp
// Init a creatable Public IP Address
var publicIpAddressCreatable = azure.PublicIPAddresses.Define("publicIPAddressName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName);
```

O recurso do Azure definido pelo objeto instanciável ainda não existe na sua assinatura. Um objeto instanciável é uma representação local de um recurso que a API de gerenciamento criará quando for necessário (quando `.Create()` é chamado). Use esse objeto instanciável na definição de outros recursos do Azure que precisem dele. 

```csharp
// Init a creatable VM using the creatable Public IP Address
var vmCreatable = azure.VirtualMachines.Define("creatableVM")
    // ...
    .withNewPrimaryPublicIPAddress(publicIPAddressCreatable)
    // ...
```

Crie os recursos em sua assinatura do Azure usando o método `Create()` para a coleção de recursos. 

```csharp
// Create the VM and its Public IP Address
var virtualMachine = azure.VirtualMachines.Create(vmCreatable);
```

Passar objetos instanciáveis para `Create()` retorna um objeto `ICreatedResources` em vez de um objeto de recurso único.  O objeto `CreatedRelatedResource` permite acessar todos os recursos criados pela chamada `Create()`, não apenas o tipo da coleção de recursos. Para acessar o endereço IP público criado no Azure para a máquina virtual criada no exemplo acima:

```csharp
var pip = virtualMachine.CreatedRelatedResource(publicIPAddressCreatable.Key()) as PublicIPAddress;;
```    

## <a name="exception-handling"></a>Manipulação de exceção

A API de gerenciamento define classes de exceção que estendem `Microsoft.Rest.RestException`. Capture exceções geradas pela API de gerenciamento com um bloco `catch (RestException exception)` após a instrução `try` relevante.

## <a name="logs-and-tracing"></a>Logs e rastreamento

O registro em log nas bibliotecas de gerenciamento fluentes do Azure para .NET aproveita o rastreamento de cliente subjacente do serviço [AutoRest](https://github.com/Azure/AutoRest).

Crie uma classe que implementa `Microsoft.Rest.IServiceClientTracingInterceptor`.  Essa classe será responsável por interceptar mensagens de log e transmiti-las para qualquer mecanismo de registro em log que você esteja usando.  Neste exemplo, estamos apenas escrevendo mensagens para o console, mas você também pode transmiti-las ao Log4Net, `Microsoft.Extensions.Logging`, ou a outra estrutura de registro em log.

```csharp
class ConsoleTracer : IServiceClientTracingInterceptor
{
    public void Information(string message)
    {
        Console.WriteLine(message);
    }

    public void TraceError(string invocationId, Exception exception)
    {
        Console.WriteLine("Exception in {0}: {1}", invocationId, exception);
    }

    public void ReceiveResponse(string invocationId, HttpResponseMessage response) { }

    public void SendRequest(string invocationId, HttpRequestMessage request) { }

    public void Configuration(string source, string name, string value) { }

    public void EnterMethod(string invocationId, object instance, string method, IDictionary<string, object> parameters) { }

    public void ExitMethod(string invocationId, object returnValue) { }
}
```

Antes de criar o objeto `Microsoft.Azure.Management.Fluent.Azure`, inicialize o `IServiceClientTracingInterceptor` criado acima chamando `ServiceClientTracing.AddTracingInterceptor()` e defina `ServiceClientTracing.IsEnabled` como *true*.  Ao criar o objeto `Azure`, inclua os métodos `.WithDelegatingHandler()` e `.WithLogLevel()` para conectar o cliente ao rastreamento de clientes do serviço AutoRest.

```csharp
ServiceClientTracing.AddTracingInterceptor(new ConsoleTracer());
ServiceClientTracing.IsEnabled = true;

var azure = Azure
    .Configure()
    .WithDelegatingHandler(new HttpLoggingDelegatingHandler())
    .WithLogLevel(HttpLoggingDelegatingHandler.Level.Basic)
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

Os níveis de log de `HttpLoggingDelegatingHandler` são definidos da seguinte maneira:

| Nível de rastreamento | Registro em log ativado 
| ------------ | ---------------
| HttpLoggingDelegatingHandler.Level.None | Sem saída
| HttpLoggingDelegatingHandler.Level.Basic | Registra em log as URLs para chamadas REST, códigos de resposta e tempos subjacentes
| HttpLoggingDelegatingHandler.Level.Body | Tudo em Basic mais os corpos de resposta e solicitação para as chamadas REST
| HttpLoggingDelegatingHandler.Level.Headers | Tudo em Basic mais os cabeçalhos de resposta e solicitação para as chamadas REST
| HttpLoggingDelegatingHandler.Level.BodyAndHeaders | Tudo no nível de log de Corpo e Cabeçalhos
