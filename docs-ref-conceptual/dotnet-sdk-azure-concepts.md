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
ms.sourcegitcommit: 1c2e1fd031ad012d6888fcde3cd325f7e8e49e0f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2018
ms.locfileid: "29752858"
---
# <a name="azure-management-library-for-net-fluent-concepts"></a><span data-ttu-id="2250c-103">Conceitos fluentes da biblioteca de gerenciamento do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="2250c-103">Azure management library for .NET fluent concepts</span></span>

<span data-ttu-id="2250c-104">Este artigo o ajudará a entender como usar com eficiência a interface fluente nas bibliotecas de gerenciamento do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="2250c-104">This article will help you understand how to effectively use the fluent interface in the Azure management libraries for .NET.</span></span>

## <a name="building-resources-using-a-fluent-interface"></a><span data-ttu-id="2250c-105">Criando recursos usando uma interface fluente</span><span class="sxs-lookup"><span data-stu-id="2250c-105">Building resources using a fluent interface</span></span>

<span data-ttu-id="2250c-106">Uma interface fluente é um formulário específico do padrão de construtor que cria objetos usando uma cadeia de métodos que impõe a configuração correta de um recurso.</span><span class="sxs-lookup"><span data-stu-id="2250c-106">A fluent interface is a specific form of the builder pattern that creates objects through a method chain that enforces correct configuration of a resource.</span></span> <span data-ttu-id="2250c-107">Por exemplo, o ponto de entrada do objeto do Azure é criado usando uma interface fluente:</span><span class="sxs-lookup"><span data-stu-id="2250c-107">For example, the entry-point Azure object is created using a fluent interface:</span></span>

```csharp
var azure = Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

## <a name="resource-collections"></a><span data-ttu-id="2250c-108">Coleções de recursos</span><span class="sxs-lookup"><span data-stu-id="2250c-108">Resource collections</span></span>

<span data-ttu-id="2250c-109">O objeto `Microsoft.Azure.Management.Fluent.Azure` mostrado acima é o ponto de entrada para toda a criação de recursos nas bibliotecas de gerenciamento fluentes.</span><span class="sxs-lookup"><span data-stu-id="2250c-109">The `Microsoft.Azure.Management.Fluent.Azure` object shown above is the entry point for all resource creation in the fluent management libraries.</span></span> <span data-ttu-id="2250c-110">Selecione o tipo de recurso para trabalhar usando as coleções de recursos no objeto `Azure`.</span><span class="sxs-lookup"><span data-stu-id="2250c-110">Select which type of resources to work with using the resource collections in the `Azure` object.</span></span> <span data-ttu-id="2250c-111">Por exemplo, para o Banco de Dados SQL:</span><span class="sxs-lookup"><span data-stu-id="2250c-111">For example, for SQL Database:</span></span>

```csharp
var sql = azure.SqlServers.Define(sqlServerName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithAdministratorLogin(administratorLogin)
    .WithAdministratorPassword(administratorPassword)
    .Create();
```

<span data-ttu-id="2250c-112">Como mostrado acima, a maioria das "conversas" mais fluentes que você tem com a API envolvem a escolha da coleção de recursos adequada aos recursos do Azure com os quais precisa trabalhar.</span><span class="sxs-lookup"><span data-stu-id="2250c-112">As seen above, most fluent "conversations" you have with the API start with selecting the appropriate resource collection for the Azure resources you need to work with.</span></span>  <span data-ttu-id="2250c-113">O IntelliSense, no Visual Studio, o orienta durante a conversa.</span><span class="sxs-lookup"><span data-stu-id="2250c-113">Intellisense in Visual Studio then guides you through the conversation.</span></span> 

![GIF do Intellisense no Visual Studio, gerando uma conversa fluente](media/dotnet-sdk-azure-concepts/vs-fluent.gif)   

## <a name="lists-and-iterations"></a><span data-ttu-id="2250c-115">Listas e iterações</span><span class="sxs-lookup"><span data-stu-id="2250c-115">Lists and iterations</span></span>

<span data-ttu-id="2250c-116">Cada coleta de recurso possui um método `List()` para retornar todas as instâncias desse recurso em sua assinatura atual.</span><span class="sxs-lookup"><span data-stu-id="2250c-116">Every resource collection has a `List()` method to return every instance of that resource in your current subscription.</span></span> <span data-ttu-id="2250c-117">Por exemplo, `Azure.SqlServers.List()` retorna todos os servidores SQL na assinatura.</span><span class="sxs-lookup"><span data-stu-id="2250c-117">For example, `Azure.SqlServers.List()` returns all SQL servers in the subscription.</span></span>

<span data-ttu-id="2250c-118">Use o método `ListByResourceGroup()` para definir o escopo da lista retornada para um determinado [grupo de recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups).</span><span class="sxs-lookup"><span data-stu-id="2250c-118">Use the `ListByResourceGroup()` method to scope the returned List to a specific [Azure resource group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups).</span></span>  

<span data-ttu-id="2250c-119">Pesquise e itere na coleção retornada exatamente como faria com um `List<T>` normal:</span><span class="sxs-lookup"><span data-stu-id="2250c-119">Iterate over the returned collection just as you would a normal `List<T>`:</span></span>

```csharp
var vmList = azure.VirtualMachines.List();
foreach(var vm in vmList)
{
    Console.WriteLine("VM Name: {0}", vm.Name);
}
```   

## <a name="actionable-verbs"></a><span data-ttu-id="2250c-120">Verbos acionáveis</span><span class="sxs-lookup"><span data-stu-id="2250c-120">Actionable verbs</span></span>

<span data-ttu-id="2250c-121">Os métodos de coleção de recursos com verbos em seus nomes executam uma ação imediatamente no Azure.</span><span class="sxs-lookup"><span data-stu-id="2250c-121">Resource collection methods with verbs in their names take immediate action in Azure.</span></span> <span data-ttu-id="2250c-122">Esses métodos funcionam de forma síncrona e bloqueiam a execução do thread atual até que sejam concluídos.</span><span class="sxs-lookup"><span data-stu-id="2250c-122">These methods work synchronously and block execution in the current thread until they complete.</span></span> 

| <span data-ttu-id="2250c-123">Verbo</span><span class="sxs-lookup"><span data-stu-id="2250c-123">Verb</span></span>   |  <span data-ttu-id="2250c-124">Amostra de uso</span><span class="sxs-lookup"><span data-stu-id="2250c-124">Sample usage</span></span> |
|--------|---------------|
| <span data-ttu-id="2250c-125">Criar</span><span class="sxs-lookup"><span data-stu-id="2250c-125">Create</span></span> | `azure.VirtualMachines.Create(listOfVMCreatables)` |
| <span data-ttu-id="2250c-126">Aplicar</span><span class="sxs-lookup"><span data-stu-id="2250c-126">Apply</span></span>  | `virtualMachineScaleSet.Update().WithCapacity(6).Apply()` |
| <span data-ttu-id="2250c-127">Excluir</span><span class="sxs-lookup"><span data-stu-id="2250c-127">Delete</span></span> | `azure.Disks.DeleteById(id)` | 
| <span data-ttu-id="2250c-128">Listar</span><span class="sxs-lookup"><span data-stu-id="2250c-128">List</span></span>   | `azure.SqlServers.List()` | 
| <span data-ttu-id="2250c-129">Obter</span><span class="sxs-lookup"><span data-stu-id="2250c-129">Get</span></span>    | `var vm  = azure.VirtualMachines.GetByResourceGroup(group, vmName)` |

>[!NOTE]
> <span data-ttu-id="2250c-130">`Define()` e `Update()` são verbos, mas não bloquearão a menos que seguidos por um `Create()` ou `Apply()`.</span><span class="sxs-lookup"><span data-stu-id="2250c-130">`Define()` and `Update()` are verbs but do not block unless followed by a `Create()` or `Apply()`.</span></span>
 
<span data-ttu-id="2250c-131">Os objetos de recurso específico têm verbos que alteram o estado do recurso no Azure.</span><span class="sxs-lookup"><span data-stu-id="2250c-131">Specific resource objects have verbs that change the state of the resource in Azure.</span></span> <span data-ttu-id="2250c-132">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="2250c-132">For example:</span></span>

```csharp
var vmToRestart = azure.VirtualMachines.GetById(id);
vmToRestart.Restart();
```

<span data-ttu-id="2250c-133">A maioria dos métodos descritos nesta seção também têm uma versão assíncrona, indicada pelo sufixo `Async`.</span><span class="sxs-lookup"><span data-stu-id="2250c-133">Most of the methods described in this section have an asynchronous version as well, denoted by the suffix `Async`.</span></span>

```csharp
Task restartTask = azure.VirtualMachines.GetById(id).RestartAsync();
```

## <a name="lazy-resource-creation"></a><span data-ttu-id="2250c-134">Criação de recursos lenta</span><span class="sxs-lookup"><span data-stu-id="2250c-134">Lazy resource creation</span></span>

<span data-ttu-id="2250c-135">Um desafio ao criar recursos do Azure ocorre quando um novo recurso depende de outro recurso que ainda não existe.</span><span class="sxs-lookup"><span data-stu-id="2250c-135">A challenge when creating Azure resources arises when a new resource depends on another resource that doesn't yet exist.</span></span> <span data-ttu-id="2250c-136">Um exemplo é a reserva de um endereço IP público e a configuração de um disco na criação de uma nova máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="2250c-136">An example is reserving a public IP address and setting up a disk when creating a new virtual machine.</span></span> <span data-ttu-id="2250c-137">Você não deseja ter de verificar a reserva do endereço ou a criação de disco; quer apenas configurar a máquina virtual com esses recursos.</span><span class="sxs-lookup"><span data-stu-id="2250c-137">You don't want to verify reserving the address or the creating the disk, you just want to configure the virtual machine with those resources.</span></span>

<span data-ttu-id="2250c-138">Use objetos instanciáveis a fim de definir recursos do Azure para usar em seu código, mas criá-los somente quando necessário no Azure.</span><span class="sxs-lookup"><span data-stu-id="2250c-138">Use creatable objects to define Azure resources for use in your code but only create them when needed in Azure.</span></span> <span data-ttu-id="2250c-139">O código criado com objetos instanciáveis repassa a criação de recursos no ambiente do Azure para a API de gerenciamento, aumentando o desempenho.</span><span class="sxs-lookup"><span data-stu-id="2250c-139">Code written with creatable objects offloads resource creation in the Azure environment to the management API, boosting performance.</span></span> 

<span data-ttu-id="2250c-140">Gere objetos instanciáveis com o verbo `Define()` da coleção de recursos sem um verbo `Create()`:</span><span class="sxs-lookup"><span data-stu-id="2250c-140">Generate creatable objects through the resource collections' `Define()` verb without a `Create()` verb:</span></span>

```csharp
// Init a creatable Public IP Address
var publicIpAddressCreatable = azure.PublicIPAddresses.Define("publicIPAddressName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName);
```

<span data-ttu-id="2250c-141">O recurso do Azure definido pelo objeto instanciável ainda não existe na sua assinatura.</span><span class="sxs-lookup"><span data-stu-id="2250c-141">The Azure resource defined by the creatable object does not yet exist in your subscription.</span></span> <span data-ttu-id="2250c-142">Um objeto instanciável é uma representação local de um recurso que a API de gerenciamento criará quando for necessário (quando `.Create()` é chamado).</span><span class="sxs-lookup"><span data-stu-id="2250c-142">A creatable object is a local representation of a resource that the management API will create when it's needed (when `.Create()` is called).</span></span> <span data-ttu-id="2250c-143">Use esse objeto instanciável na definição de outros recursos do Azure que precisem dele.</span><span class="sxs-lookup"><span data-stu-id="2250c-143">Use this creatable object in the definition of other Azure resources that need this resource.</span></span> 

```csharp
// Init a creatable VM using the creatable Public IP Address
var vmCreatable = azure.VirtualMachines.Define("creatableVM")
    // ...
    .withNewPrimaryPublicIPAddress(publicIPAddressCreatable)
    // ...
```

<span data-ttu-id="2250c-144">Crie os recursos em sua assinatura do Azure usando o método `Create()` para a coleção de recursos.</span><span class="sxs-lookup"><span data-stu-id="2250c-144">Create the resources in your Azure subscription using the `Create()` method for the resource collection.</span></span> 

```csharp
// Create the VM and its Public IP Address
var virtualMachine = azure.VirtualMachines.Create(vmCreatable);
```

<span data-ttu-id="2250c-145">Passar objetos instanciáveis para `Create()` retorna um objeto `ICreatedResources` em vez de um objeto de recurso único.</span><span class="sxs-lookup"><span data-stu-id="2250c-145">Passing creatable objects to `Create()` returns a `ICreatedResources` object instead of a single resource object.</span></span>  <span data-ttu-id="2250c-146">O objeto `CreatedRelatedResource` permite acessar todos os recursos criados pela chamada `Create()`, não apenas o tipo da coleção de recursos.</span><span class="sxs-lookup"><span data-stu-id="2250c-146">The `CreatedRelatedResource` object lets you access all resources created by the `Create()` call, not just the type from the resource collection.</span></span> <span data-ttu-id="2250c-147">Para acessar o endereço IP público criado no Azure para a máquina virtual criada no exemplo acima:</span><span class="sxs-lookup"><span data-stu-id="2250c-147">To access the public IP address created in Azure for the virtual machine created in the above example:</span></span>

```csharp
var pip = virtualMachine.CreatedRelatedResource(publicIPAddressCreatable.Key()) as PublicIPAddress;;
```    

## <a name="exception-handling"></a><span data-ttu-id="2250c-148">Manipulação de exceção</span><span class="sxs-lookup"><span data-stu-id="2250c-148">Exception handling</span></span>

<span data-ttu-id="2250c-149">A API de gerenciamento define classes de exceção que estendem `Microsoft.Rest.RestException`.</span><span class="sxs-lookup"><span data-stu-id="2250c-149">The management API defines exception classes that extend `Microsoft.Rest.RestException`.</span></span> <span data-ttu-id="2250c-150">Capture exceções geradas pela API de gerenciamento com um bloco `catch (RestException exception)` após a instrução `try` relevante.</span><span class="sxs-lookup"><span data-stu-id="2250c-150">Catch exceptions generated by management API, with a `catch (RestException exception)` block after the relevant `try` statement.</span></span>

## <a name="logs-and-tracing"></a><span data-ttu-id="2250c-151">Logs e rastreamento</span><span class="sxs-lookup"><span data-stu-id="2250c-151">Logs and tracing</span></span>

<span data-ttu-id="2250c-152">O registro em log nas bibliotecas de gerenciamento fluentes do Azure para .NET aproveita o rastreamento de cliente subjacente do serviço [AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="2250c-152">Logging in the fluent Azure management libraries for .NET leverages the underlying [AutoRest](https://github.com/Azure/AutoRest) service client tracing.</span></span>

<span data-ttu-id="2250c-153">Crie uma classe que implementa `Microsoft.Rest.IServiceClientTracingInterceptor`.</span><span class="sxs-lookup"><span data-stu-id="2250c-153">Create a class that implements `Microsoft.Rest.IServiceClientTracingInterceptor`.</span></span>  <span data-ttu-id="2250c-154">Essa classe será responsável por interceptar mensagens de log e transmiti-las para qualquer mecanismo de registro em log que você esteja usando.</span><span class="sxs-lookup"><span data-stu-id="2250c-154">This class will be responsible for intercepting log messages and passing them to whatever logging mechanism you're using.</span></span>  <span data-ttu-id="2250c-155">Neste exemplo, estamos apenas escrevendo mensagens para o console, mas você também pode transmiti-las ao Log4Net, `Microsoft.Extensions.Logging`, ou a outra estrutura de registro em log.</span><span class="sxs-lookup"><span data-stu-id="2250c-155">In this example, we're just writing messages to the console, but you could also pass them to Log4Net, `Microsoft.Extensions.Logging`, or any other logging framework.</span></span>

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

<span data-ttu-id="2250c-156">Antes de criar o objeto `Microsoft.Azure.Management.Fluent.Azure`, inicialize o `IServiceClientTracingInterceptor` criado acima chamando `ServiceClientTracing.AddTracingInterceptor()` e defina `ServiceClientTracing.IsEnabled` como *true*.</span><span class="sxs-lookup"><span data-stu-id="2250c-156">Before creating the `Microsoft.Azure.Management.Fluent.Azure` object, initialize the `IServiceClientTracingInterceptor` you created above by calling `ServiceClientTracing.AddTracingInterceptor()` and set `ServiceClientTracing.IsEnabled` to *true*.</span></span>  <span data-ttu-id="2250c-157">Ao criar o objeto `Azure`, inclua os métodos `.WithDelegatingHandler()` e `.WithLogLevel()` para conectar o cliente ao rastreamento de clientes do serviço AutoRest.</span><span class="sxs-lookup"><span data-stu-id="2250c-157">When you create the `Azure` object, include the `.WithDelegatingHandler()` and `.WithLogLevel()` methods to wire up the client to AutoRest's service client tracing.</span></span>

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

<span data-ttu-id="2250c-158">Os níveis de log de `HttpLoggingDelegatingHandler` são definidos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2250c-158">The `HttpLoggingDelegatingHandler` log levels are defined as follows:</span></span>

| <span data-ttu-id="2250c-159">Nível de rastreamento</span><span class="sxs-lookup"><span data-stu-id="2250c-159">Trace level</span></span> | <span data-ttu-id="2250c-160">Registro em log ativado</span><span class="sxs-lookup"><span data-stu-id="2250c-160">Logging enabled</span></span> 
| ------------ | ---------------
| <span data-ttu-id="2250c-161">HttpLoggingDelegatingHandler.Level.None</span><span class="sxs-lookup"><span data-stu-id="2250c-161">HttpLoggingDelegatingHandler.Level.None</span></span> | <span data-ttu-id="2250c-162">Sem saída</span><span class="sxs-lookup"><span data-stu-id="2250c-162">No output</span></span>
| <span data-ttu-id="2250c-163">HttpLoggingDelegatingHandler.Level.Basic</span><span class="sxs-lookup"><span data-stu-id="2250c-163">HttpLoggingDelegatingHandler.Level.Basic</span></span> | <span data-ttu-id="2250c-164">Registra em log as URLs para chamadas REST, códigos de resposta e tempos subjacentes</span><span class="sxs-lookup"><span data-stu-id="2250c-164">Logs the URLs to underlying REST calls, response codes and times</span></span>
| <span data-ttu-id="2250c-165">HttpLoggingDelegatingHandler.Level.Body</span><span class="sxs-lookup"><span data-stu-id="2250c-165">HttpLoggingDelegatingHandler.Level.Body</span></span> | <span data-ttu-id="2250c-166">Tudo em Basic mais os corpos de resposta e solicitação para as chamadas REST</span><span class="sxs-lookup"><span data-stu-id="2250c-166">Everything in Basic plus request and response bodies for the REST calls</span></span>
| <span data-ttu-id="2250c-167">HttpLoggingDelegatingHandler.Level.Headers</span><span class="sxs-lookup"><span data-stu-id="2250c-167">HttpLoggingDelegatingHandler.Level.Headers</span></span> | <span data-ttu-id="2250c-168">Tudo em Basic mais os cabeçalhos de resposta e solicitação para as chamadas REST</span><span class="sxs-lookup"><span data-stu-id="2250c-168">Everything in Basic plus the request and response headers REST calls</span></span>
| <span data-ttu-id="2250c-169">HttpLoggingDelegatingHandler.Level.BodyAndHeaders</span><span class="sxs-lookup"><span data-stu-id="2250c-169">HttpLoggingDelegatingHandler.Level.BodyAndHeaders</span></span> | <span data-ttu-id="2250c-170">Tudo no nível de log de Corpo e Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="2250c-170">Everything in both Body and Headers log level</span></span>
