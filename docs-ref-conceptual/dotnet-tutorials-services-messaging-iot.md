---
title: Tutoriais para sistemas de mensagens e IoT com .NET no Azure | Microsoft Docs
description: "Envie mensagens entre aplicativos de nuvem e entre dispositivos e a nuvem usando o .NET e serviços do Azure."
author: camsoper
manager: douge
ms.assetid: 2ce6ea06-7b0b-45e6-8ca0-44e4e4030b82
ms.devlang: dotnet
ms.topic: article
ms.service: Azure
ms.technology: Azure
ms.date: 4/10/2017
ms.author: casoper
ms.openlocfilehash: 0c3e81231ac88b2418778b83ecabcbb553608e24
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2017
---
# <a name="net-tutorials-for-enterprise-messaging-and-internet-of-things-iot"></a><span data-ttu-id="16ceb-103">Tutoriais do .NET para sistema de mensagens corporativas e IoT (Internet das Coisas)</span><span class="sxs-lookup"><span data-stu-id="16ceb-103">.NET tutorials for enterprise messaging and Internet of Things (IoT)</span></span>

<span data-ttu-id="16ceb-104">A tabela a seguir contém links para tutoriais detalhados sobre envio e leitura de mensagens entre aplicativos e dispositivos no seu código .NET usando os serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="16ceb-104">The following table links to in-depth tutorials for sending and reading messages between applications and devices in from your .NET code using Azure services.</span></span>

<span data-ttu-id="16ceb-105">Para exemplos de código-fonte, confira a lista de [exemplos do serviço do Azure](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span><span class="sxs-lookup"><span data-stu-id="16ceb-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>


| | |
|---|---|
| <span data-ttu-id="16ceb-106">**Barramento de Serviço**</span><span class="sxs-lookup"><span data-stu-id="16ceb-106">**Service Bus**</span></span> | |
| <span data-ttu-id="16ceb-107">[Como usar filas do Barramento de Serviço][1]</span><span class="sxs-lookup"><span data-stu-id="16ceb-107">[How to use Service Bus queues][1]</span></span> | <span data-ttu-id="16ceb-108">Criar filas, enviar e receber mensagens e excluir filas.</span><span class="sxs-lookup"><span data-stu-id="16ceb-108">Create queues, send and receive messages, and delete queues.</span></span> | 
| <span data-ttu-id="16ceb-109">[Como usar tópicos e assinaturas do Barramento de Serviço][2]</span><span class="sxs-lookup"><span data-stu-id="16ceb-109">[How to use Service Bus topics and subscriptions][2]</span></span> | <span data-ttu-id="16ceb-110">Saiba como usar o modelo de comunicação publicação/assinatura com o Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="16ceb-110">Learn how to use publish/subscribe communication model with Service Bus.</span></span>
| <span data-ttu-id="16ceb-111">[Usando o Barramento de Serviço do .NET com AMQP 1.0][3]</span><span class="sxs-lookup"><span data-stu-id="16ceb-111">[Using Service Bus from .NET with AMQP 1.0][3]</span></span> | <span data-ttu-id="16ceb-112">Saiba como usar o AMQP em aplicativos do Barramento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="16ceb-112">Learn how to use AMQP in you Service Bus applications.</span></span>
|<span data-ttu-id="16ceb-113">**Hub IoT**</span><span class="sxs-lookup"><span data-stu-id="16ceb-113">**IoT Hub**</span></span>|
| <span data-ttu-id="16ceb-114">[Conectar um dispositivo simulado ao Hub IoT][4]</span><span class="sxs-lookup"><span data-stu-id="16ceb-114">[Connect a simulated device to your IoT Hub][4]</span></span> | <span data-ttu-id="16ceb-115">Criar uma identidade de dispositivo, enviar mensagens e processar a telemetria do seu Hub IoT.</span><span class="sxs-lookup"><span data-stu-id="16ceb-115">Create a device identity, send messages, and process telemetry from your IoT Hub.</span></span> |   
| <span data-ttu-id="16ceb-116">[Processar mensagens de dispositivo para nuvem][5]</span><span class="sxs-lookup"><span data-stu-id="16ceb-116">[Process device-to-cloud messages][5]</span></span> | <span data-ttu-id="16ceb-117">Enviar mensagens de um dispositivo simulado e processá-las na nuvem.</span><span class="sxs-lookup"><span data-stu-id="16ceb-117">Send messages from a simulated device and process them in the cloud.</span></span> |
|<span data-ttu-id="16ceb-118">**Hub de Evento**</span><span class="sxs-lookup"><span data-stu-id="16ceb-118">**Event Hub**</span></span>|
| <span data-ttu-id="16ceb-119">[Enviar eventos para um Hub de Eventos][6]</span><span class="sxs-lookup"><span data-stu-id="16ceb-119">[Send events to an Event Hub][6]</span></span> | <span data-ttu-id="16ceb-120">Enviar eventos ao Hub de Eventos de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="16ceb-120">Send events to Event hub from a console application.</span></span>
| <span data-ttu-id="16ceb-121">[Receber eventos de Hubs de Eventos][7]</span><span class="sxs-lookup"><span data-stu-id="16ceb-121">[Receive events from Event Hubs][7]</span></span> | <span data-ttu-id="16ceb-122">Receba mensagens e processe-as em paralelo.</span><span class="sxs-lookup"><span data-stu-id="16ceb-122">Receive messages and process them in parallel.</span></span>


[1]: /azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues
[2]: /azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions
[3]: /azure/service-bus-messaging/service-bus-amqp-dotnet
[4]: /azure/iot-hub/iot-hub-csharp-csharp-getstarted
[5]: /azure/iot-hub/iot-hub-csharp-csharp-process-d2c
[6]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-send
[7]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph


