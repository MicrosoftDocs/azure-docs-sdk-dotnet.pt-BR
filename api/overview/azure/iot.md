---
title: Bibliotecas do IoT do Azure para .NET
description: "Referência para bibliotecas do IoT do Azure para .NET"
keywords: Azure, .NET, SDK, API, IoT
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: bdbcc37affb55336d1a3fafe24b8e7ffd78ec180
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-iot-libraries-for-net"></a><span data-ttu-id="64d08-104">Bibliotecas do IoT do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="64d08-104">Azure IoT libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="64d08-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="64d08-105">Overview</span></span>

<span data-ttu-id="64d08-106">O [Hub IoT do Azure](https://azure.microsoft.com/services/iot-hub/) é um serviço totalmente gerenciado que permite comunicações bidirecionais confiáveis e seguras entre milhões de dispositivos e um back-end da solução.</span><span class="sxs-lookup"><span data-stu-id="64d08-106">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is a fully managed service that enables reliable and secure bi-directional communications between millions of devices and a solution back end.</span></span>

<span data-ttu-id="64d08-107">Dispositivos e fontes de dados em uma solução do IoT podem variar de um simples sensor conectado à rede a um dispositivo de computação eficiente e autônomo.</span><span class="sxs-lookup"><span data-stu-id="64d08-107">Devices and data sources in an IoT solution can range from a simple network-connected sensor to a powerful, standalone computing device.</span></span> <span data-ttu-id="64d08-108">Os dispositivos podem ter capacidade de processamento, memória, largura de banda de comunicação e suporte ao protocolo de comunicação limitados.</span><span class="sxs-lookup"><span data-stu-id="64d08-108">Devices may have limited processing capability, memory, communication bandwidth, and communication protocol support.</span></span> <span data-ttu-id="64d08-109">Os [SDKs de dispositivo](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) do IoT permitem implementar aplicativos clientes em uma ampla variedade de dispositivos e aplicativos de back-end.</span><span class="sxs-lookup"><span data-stu-id="64d08-109">The IoT [device SDKs](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) enable you to implement client applications for a wide variety of devices and back-end applications.</span></span>

<span data-ttu-id="64d08-110">O SDK de dispositivos para .NET facilita a criação de dispositivos que executam o .NET e se conectam ao Hub IoT do Azure.</span><span class="sxs-lookup"><span data-stu-id="64d08-110">The device SDK for .NET facilitates building devices running .NET that connect to Azure IoT Hub.</span></span>

<span data-ttu-id="64d08-111">O SDK de serviço para .NET facilita a criação de aplicativos de back-end com o .NET que gerenciam e permitem controlar dispositivos na nuvem.</span><span class="sxs-lookup"><span data-stu-id="64d08-111">The service SDK for .NET facilitates building back-end applications using .NET that manage and allow controlling devices from the Cloud.</span></span>

<span data-ttu-id="64d08-112">[Saiba mais sobre o IoT do Azure](https://docs.microsoft.com/azure/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="64d08-112">[Learn more about Azure IoT](https://docs.microsoft.com/azure/iot-hub/).</span></span>


## <a name="client-library"></a><span data-ttu-id="64d08-113">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="64d08-113">Client library</span></span>

<span data-ttu-id="64d08-114">Use o cliente de dispositivos IoT .NET para se conectar e enviar mensagens para o Hub IoT.</span><span class="sxs-lookup"><span data-stu-id="64d08-114">Use the .NET IoT devices client to connect and send messages to your IoT Hub.</span></span>

<span data-ttu-id="64d08-115">Instale o [pacote NuGet]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) diretamente do [console do Gerenciador de Pacotes] [ PackageManager] do Visual Studio ou com a [CLI do .NET Core] [DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="64d08-115">Install the [NuGet package]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="64d08-116">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64d08-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Devices.Client
```

```bash
dotnet add package Microsoft.Azure.Devices.Client
```
### <a name="code-examples"></a><span data-ttu-id="64d08-117">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="64d08-117">Code Examples</span></span> 

<span data-ttu-id="64d08-118">Este exemplo conecta-se ao Hub IoT e envia uma mensagem por segundo.</span><span class="sxs-lookup"><span data-stu-id="64d08-118">This example connects to the IoT Hub and sends one message per second.</span></span>

```csharp
string deviceKey = "<deviceKey>";
string deviceId = "<deviceId>";
string iotHubHostName = "<IoTHubHostname>";
DeviceAuthenticationWithRegistrySymmetricKeyvar deviceAuthentication = new DeviceAuthenticationWithRegistrySymmetricKey(deviceId, deviceKey);

DeviceClient deviceClient = DeviceClient.Create(iotHubHostName, deviceAuthentication, TransportType.Mqtt);

while (true)
{
    double currentTemperature = 20 + Rand.NextDouble() * 15;
    double currentHumidity = 60 + Rand.NextDouble() * 20;

    var telemetryDataPoint = new
    {
        messageId = _messageId++,
        deviceId = deviceId,
        temperature = currentTemperature,
        humidity = currentHumidity
    };
    string messageString = JsonConvert.SerializeObject(telemetryDataPoint);
    Message message = new Message(Encoding.ASCII.GetBytes(messageString));
    message.Properties.Add("temperatureAlert", (currentTemperature > 30) ? "true" : "false");

    await deviceClient.SendEventAsync(message);
    Console.WriteLine("{0} > Sending message: {1}", DateTime.Now, messageString);

    await Task.Delay(1000);
}
```


> [!div class="nextstepaction"]
> [<span data-ttu-id="64d08-119">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="64d08-119">Explore the client APIs</span></span>](/dotnet/api/overview/azure/iot/client)

## <a name="samples"></a><span data-ttu-id="64d08-120">Exemplos</span><span class="sxs-lookup"><span data-stu-id="64d08-120">Samples</span></span>

- [<span data-ttu-id="64d08-121">Serviço Web genérico para o cenário do Hub de Eventos</span><span class="sxs-lookup"><span data-stu-id="64d08-121">Generic Web Service to Event Hub scenario</span></span>](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/)

<span data-ttu-id="64d08-122">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) de exemplos do IoT do Azure.</span><span class="sxs-lookup"><span data-stu-id="64d08-122">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) of Azure IoT Upsamples.</span></span>

<span data-ttu-id="64d08-123">Consulte o [guia do desenvolvedor do Hub IoT do Azure](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide) para obter instruções.</span><span class="sxs-lookup"><span data-stu-id="64d08-123">View the [Azure IoT Hub developer guide](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide) for more guidance.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
