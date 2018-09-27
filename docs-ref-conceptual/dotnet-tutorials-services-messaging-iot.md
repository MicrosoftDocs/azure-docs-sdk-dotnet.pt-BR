---
title: Tutoriais para sistemas de mensagens e IoT com .NET no Azure | Microsoft Docs
description: Envie mensagens entre aplicativos de nuvem e entre dispositivos e a nuvem usando o .NET e serviços do Azure.
ms.date: 10/19/2017
ms.openlocfilehash: 92cb78b34706a453630dbf36913d53400962ff25
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190769"
---
# <a name="net-tutorials-for-enterprise-messaging-and-internet-of-things-iot"></a><span data-ttu-id="f0dc5-103">Tutoriais do .NET para sistema de mensagens corporativas e IoT (Internet das Coisas)</span><span class="sxs-lookup"><span data-stu-id="f0dc5-103">.NET tutorials for enterprise messaging and Internet of Things (IoT)</span></span>

<span data-ttu-id="f0dc5-104">A tabela a seguir contém links para tutoriais detalhados sobre envio e leitura de mensagens entre aplicativos e dispositivos no seu código .NET usando os serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-104">The following table links to in-depth tutorials for sending and reading messages between applications and devices in from your .NET code using Azure services.</span></span>

<span data-ttu-id="f0dc5-105">Para exemplos de código-fonte, confira a lista de [exemplos do serviço do Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span><span class="sxs-lookup"><span data-stu-id="f0dc5-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>


| | |
|---|---|
| <span data-ttu-id="f0dc5-106">**Barramento de Serviço**</span><span class="sxs-lookup"><span data-stu-id="f0dc5-106">**Service Bus**</span></span> | |
| <span data-ttu-id="f0dc5-107">[Como usar filas do Barramento de Serviço][1]</span><span class="sxs-lookup"><span data-stu-id="f0dc5-107">[How to use Service Bus queues][1]</span></span> | <span data-ttu-id="f0dc5-108">Criar filas, enviar e receber mensagens e excluir filas.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-108">Create queues, send and receive messages, and delete queues.</span></span> | 
| <span data-ttu-id="f0dc5-109">[Como usar tópicos e assinaturas do Barramento de Serviço][2]</span><span class="sxs-lookup"><span data-stu-id="f0dc5-109">[How to use Service Bus topics and subscriptions][2]</span></span> | <span data-ttu-id="f0dc5-110">Saiba como usar o modelo de comunicação publicação/assinatura com o Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-110">Learn how to use publish/subscribe communication model with Service Bus.</span></span>
| <span data-ttu-id="f0dc5-111">[Usando o Barramento de Serviço do .NET com AMQP 1.0][3]</span><span class="sxs-lookup"><span data-stu-id="f0dc5-111">[Using Service Bus from .NET with AMQP 1.0][3]</span></span> | <span data-ttu-id="f0dc5-112">Saiba como usar o AMQP em aplicativos do Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-112">Learn how to use AMQP in you Service Bus applications.</span></span>
|<span data-ttu-id="f0dc5-113">**Hub IoT**</span><span class="sxs-lookup"><span data-stu-id="f0dc5-113">**IoT Hub**</span></span>|
| <span data-ttu-id="f0dc5-114">[Conectar um dispositivo simulado ao Hub IoT][4]</span><span class="sxs-lookup"><span data-stu-id="f0dc5-114">[Connect a simulated device to your IoT Hub][4]</span></span> | <span data-ttu-id="f0dc5-115">Criar uma identidade de dispositivo, enviar mensagens e processar a telemetria do seu Hub IoT.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-115">Create a device identity, send messages, and process telemetry from your IoT Hub.</span></span> |   
| <span data-ttu-id="f0dc5-116">[Processar mensagens de dispositivo para nuvem][5]</span><span class="sxs-lookup"><span data-stu-id="f0dc5-116">[Process device-to-cloud messages][5]</span></span> | <span data-ttu-id="f0dc5-117">Enviar mensagens de um dispositivo simulado e processá-las na nuvem.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-117">Send messages from a simulated device and process them in the cloud.</span></span> |
|<span data-ttu-id="f0dc5-118">**Hub de Evento**</span><span class="sxs-lookup"><span data-stu-id="f0dc5-118">**Event Hub**</span></span>|
| <span data-ttu-id="f0dc5-119">[Enviar eventos para um Hub de Eventos][6]</span><span class="sxs-lookup"><span data-stu-id="f0dc5-119">[Send events to an Event Hub][6]</span></span> | <span data-ttu-id="f0dc5-120">Enviar eventos ao Hub de Eventos de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-120">Send events to Event hub from a console application.</span></span>
| <span data-ttu-id="f0dc5-121">[Receber eventos de Hubs de Eventos][7]</span><span class="sxs-lookup"><span data-stu-id="f0dc5-121">[Receive events from Event Hubs][7]</span></span> | <span data-ttu-id="f0dc5-122">Receba mensagens e processe-as em paralelo.</span><span class="sxs-lookup"><span data-stu-id="f0dc5-122">Receive messages and process them in parallel.</span></span>


[1]: /azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues
[2]: /azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions
[3]: /azure/service-bus-messaging/service-bus-amqp-dotnet
[4]: /azure/iot-hub/iot-hub-csharp-csharp-getstarted
[5]: /azure/iot-hub/iot-hub-csharp-csharp-process-d2c
[6]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-send
[7]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph


