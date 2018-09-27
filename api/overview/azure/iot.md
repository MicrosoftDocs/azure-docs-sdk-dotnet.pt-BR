---
title: Bibliotecas do IoT do Azure para .NET
description: Referência para bibliotecas do IoT do Azure para .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: iot-hub
ms.openlocfilehash: 54182d8fabec0d3aee3ca3b58c7315bdf43cc24e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190179"
---
# <a name="azure-iot-libraries-for-net"></a>Bibliotecas do IoT do Azure para .NET

## <a name="overview"></a>Visão geral

O [Hub IoT do Azure](https://azure.microsoft.com/services/iot-hub/) é um serviço totalmente gerenciado que permite comunicações bidirecionais confiáveis e seguras entre milhões de dispositivos e um back-end da solução.

Dispositivos e fontes de dados em uma solução do IoT podem variar de um simples sensor conectado à rede a um dispositivo de computação eficiente e autônomo. Os dispositivos podem ter capacidade de processamento, memória, largura de banda de comunicação e suporte ao protocolo de comunicação limitados. Os [SDKs de dispositivo](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) do IoT permitem implementar aplicativos clientes em uma ampla variedade de dispositivos e aplicativos de back-end.

O SDK de dispositivos para .NET facilita a criação de dispositivos que executam o .NET e se conectam ao Hub IoT do Azure.

O SDK de serviço para .NET facilita a criação de aplicativos de back-end com o .NET que gerenciam e permitem controlar dispositivos na nuvem.

[Saiba mais sobre o IoT do Azure](https://docs.microsoft.com/azure/iot-hub/).


## <a name="client-library"></a>Biblioteca do cliente

Use o cliente de dispositivos IoT .NET para se conectar e enviar mensagens para o Hub IoT.

Instale o [pacote NuGet]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) diretamente do [console do Gerenciador de Pacotes][PackageManager] do Visual Studio ou com a [CLI do .NET Core][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Gerenciador de Pacotes do Visual Studio

```powershell
Install-Package Microsoft.Azure.Devices.Client
```

```bash
dotnet add package Microsoft.Azure.Devices.Client
```
### <a name="code-examples"></a>Exemplos de código 

Este exemplo conecta-se ao Hub IoT e envia uma mensagem por segundo.

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
> [Explorar as APIs de cliente](/dotnet/api/overview/azure/iot/client)

## <a name="samples"></a>Exemplos

- [Serviço Web genérico para o cenário do Hub de Eventos](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/)

Veja a [lista completa](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) de exemplos do IoT do Azure.

Consulte o [guia do desenvolvedor do Hub IoT do Azure](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide) para obter instruções.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
