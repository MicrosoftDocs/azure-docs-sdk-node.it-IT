---
title: Esempi di codice per IoT e messaggistica di Azure con Node.js
description: Codice di esempio che illustra come usare IoT e messaggistica di Azure con Node.js
author: rloutlaw
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: routlaw
ms.openlocfilehash: 3169c3ef0d204e902db47d81ba02b638a5eb02f5
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220683"
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="44aa5-103">Codice di esempio per l'uso della messaggistica di Azure e di IoT con Node.js</span><span class="sxs-lookup"><span data-stu-id="44aa5-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="44aa5-104">Il codice di esempio seguente illustra l'uso della messaggistica di Azure e di IoT con Node.js</span><span class="sxs-lookup"><span data-stu-id="44aa5-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="44aa5-105">Per ottenere il codice per altre attività, esplorare l'elenco completo di [esempi di Azure per Node.js](https://azure.microsoft.com/resources/samples/?term=nodejs).</span><span class="sxs-lookup"><span data-stu-id="44aa5-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="44aa5-106">**Hub IoT Azure**</span><span class="sxs-lookup"><span data-stu-id="44aa5-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="44aa5-107">Ping dell'hub IoT di Azure</span><span class="sxs-lookup"><span data-stu-id="44aa5-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="44aa5-108">Soluzione ping semplice che consente di convalidare la connettività di un dispositivo all'hub IoT di Azure.</span><span class="sxs-lookup"><span data-stu-id="44aa5-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| <span data-ttu-id="44aa5-109">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalie nella vibrazione dei tweet rilevate dai servizi IoT di Azure nei dati di Intel Edison che esegue Node.js)</span><span class="sxs-lookup"><span data-stu-id="44aa5-109">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span> | <span data-ttu-id="44aa5-110">Progetto IoT che usa l'hub IoT di Azure e illustra un dispositivo che esegue un nodo per inviare dati di telemetria e che viene analizzato dai servizi IoT di Azure.</span><span class="sxs-lookup"><span data-stu-id="44aa5-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="44aa5-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="44aa5-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="44aa5-112">Introduzione allo starter kit di Azure IoT per Intel Edison</span><span class="sxs-lookup"><span data-stu-id="44aa5-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="44aa5-113">Illustra Azure IoT usando lo starter kit di Azure IoT - Intel Edison.</span><span class="sxs-lookup"><span data-stu-id="44aa5-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="44aa5-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="44aa5-114">**MQTT**</span></span> ||
| [<span data-ttu-id="44aa5-115">Moduli gateway MQTT e HTTP di esempio</span><span class="sxs-lookup"><span data-stu-id="44aa5-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="44aa5-116">Fornisce due moduli del gateway che espongono gli endpoint MQTT e HTTPS di tipo hub IoT per il caricamento dei dati di telemetria e, nel caso dei moduli MQTT, anche la messaggistica da cloud a dispositivo.</span><span class="sxs-lookup"><span data-stu-id="44aa5-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="44aa5-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="44aa5-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="44aa5-118">Introduzione allo starter kit di Microsoft Azure IoT per Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="44aa5-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="44aa5-119">Illustra l'uso dello starter kit di Azure IoT per Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="44aa5-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="44aa5-120">Connettere lo starter kit di Microsoft Azure IoT per Raspberry Pi 3 alla soluzione di monitoraggio remoto</span><span class="sxs-lookup"><span data-stu-id="44aa5-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="44aa5-121">Informazioni su come connettere un dispositivo Raspberry Pi 3 alla soluzione di monitoraggio remoto Azure IoT Suite.</span><span class="sxs-lookup"><span data-stu-id="44aa5-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
