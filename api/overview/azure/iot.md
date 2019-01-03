---
title: Bibliotecas do IoT do Azure para .NET
description: Referência para bibliotecas do IoT do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: iot-hub
ms.openlocfilehash: 667663c5f5e3452fcc5ec0c4f3ded997370c5852
ms.sourcegitcommit: 7f1a1bf275d8489f8df266b746baa33d66fcb2c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737071"
---
# <a name="azure-iot-libraries-for-net"></a><span data-ttu-id="6995d-103">Bibliotecas do IoT do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="6995d-103">Azure IoT libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="6995d-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="6995d-104">Overview</span></span>

<span data-ttu-id="6995d-105">O [Hub IoT do Azure](https://azure.microsoft.com/services/iot-hub/) é um serviço totalmente gerenciado que permite comunicações bidirecionais confiáveis e seguras entre milhões de dispositivos e um back-end da solução.</span><span class="sxs-lookup"><span data-stu-id="6995d-105">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is a fully managed service that enables reliable and secure bi-directional communications between millions of devices and a solution back end.</span></span>

<span data-ttu-id="6995d-106">Dispositivos e fontes de dados em uma solução do IoT podem variar de um simples sensor conectado à rede a um dispositivo de computação eficiente e autônomo.</span><span class="sxs-lookup"><span data-stu-id="6995d-106">Devices and data sources in an IoT solution can range from a simple network-connected sensor to a powerful, standalone computing device.</span></span> <span data-ttu-id="6995d-107">Os dispositivos podem ter capacidade de processamento, memória, largura de banda de comunicação e suporte ao protocolo de comunicação limitados.</span><span class="sxs-lookup"><span data-stu-id="6995d-107">Devices may have limited processing capability, memory, communication bandwidth, and communication protocol support.</span></span> <span data-ttu-id="6995d-108">Os [SDKs de dispositivo](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) do IoT permitem implementar aplicativos clientes em uma ampla variedade de dispositivos e aplicativos de back-end.</span><span class="sxs-lookup"><span data-stu-id="6995d-108">The IoT [device SDKs](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) enable you to implement client applications for a wide variety of devices and back-end applications.</span></span>

<span data-ttu-id="6995d-109">O SDK de dispositivos para .NET facilita a criação de dispositivos que executam o .NET e se conectam ao Hub IoT do Azure.</span><span class="sxs-lookup"><span data-stu-id="6995d-109">The device SDK for .NET facilitates building devices running .NET that connect to Azure IoT Hub.</span></span>

<span data-ttu-id="6995d-110">O SDK de serviço para .NET facilita a criação de aplicativos de back-end com o .NET que gerenciam e permitem controlar dispositivos na nuvem.</span><span class="sxs-lookup"><span data-stu-id="6995d-110">The service SDK for .NET facilitates building back-end applications using .NET that manage and allow controlling devices from the Cloud.</span></span>

<span data-ttu-id="6995d-111">[Saiba mais sobre o IoT do Azure](https://docs.microsoft.com/azure/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="6995d-111">[Learn more about Azure IoT](https://docs.microsoft.com/azure/iot-hub/).</span></span>


## <a name="client-library"></a><span data-ttu-id="6995d-112">Biblioteca do cliente</span><span class="sxs-lookup"><span data-stu-id="6995d-112">Client library</span></span>

<span data-ttu-id="6995d-113">Use o cliente de dispositivos IoT .NET para se conectar e enviar mensagens para o Hub IoT.</span><span class="sxs-lookup"><span data-stu-id="6995d-113">Use the .NET IoT devices client to connect and send messages to your IoT Hub.</span></span>

<span data-ttu-id="6995d-114">Instale o [pacote NuGet]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="6995d-114">Install the [NuGet package]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="6995d-115">Gerenciador de Pacotes do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6995d-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Devices.Client
```

```bash
dotnet add package Microsoft.Azure.Devices.Client
```
### <a name="code-examples"></a><span data-ttu-id="6995d-116">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="6995d-116">Code Examples</span></span> 

<span data-ttu-id="6995d-117">Este exemplo conecta-se ao Hub IoT e envia uma mensagem por segundo.</span><span class="sxs-lookup"><span data-stu-id="6995d-117">This example connects to the IoT Hub and sends one message per second.</span></span>

```csharp
string deviceKey = "<deviceKey>";
string deviceId = "<deviceId>";
string iotHubHostName = "<IoTHubHostname>";
var deviceAuthentication = new DeviceAuthenticationWithRegistrySymmetricKey(deviceId, deviceKey);

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
> [<span data-ttu-id="6995d-118">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="6995d-118">Explore the client APIs</span></span>](/dotnet/api/overview/azure/iot/client)

## <a name="samples"></a><span data-ttu-id="6995d-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6995d-119">Samples</span></span>

- [<span data-ttu-id="6995d-120">Serviço Web genérico para o cenário do Hub de Eventos</span><span class="sxs-lookup"><span data-stu-id="6995d-120">Generic Web Service to Event Hub scenario</span></span>](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/)

<span data-ttu-id="6995d-121">Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) de exemplos do IoT do Azure.</span><span class="sxs-lookup"><span data-stu-id="6995d-121">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) of Azure IoT Upsamples.</span></span>

<span data-ttu-id="6995d-122">Consulte o [guia do desenvolvedor do Hub IoT do Azure](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide) para obter instruções.</span><span class="sxs-lookup"><span data-stu-id="6995d-122">View the [Azure IoT Hub developer guide](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide) for more guidance.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
