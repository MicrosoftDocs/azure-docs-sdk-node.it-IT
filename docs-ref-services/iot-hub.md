---
title: Moduli di Hub IoT di Azure per Node.js
description: Informazioni di riferimento sui moduli di Hub IoT di Azure per Node.js
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 1f83e016023722f149384ac015726e9257a9f3af
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "49702846"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="35e91-103">Moduli di Hub IoT di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="35e91-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="35e91-104">L'hub IoT di Azure è un servizio completamente gestito che consente comunicazioni bidirezionali affidabili e sicure tra milioni di dispositivi IoT e un back-end della soluzione.</span><span class="sxs-lookup"><span data-stu-id="35e91-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="35e91-105">L'hub IoT di Azure:</span><span class="sxs-lookup"><span data-stu-id="35e91-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="35e91-106">Offre più opzioni di comunicazione dispositivo a cloud e cloud a dispositivo, inclusi la messaggistica unidirezionale, il trasferimento di file e i metodi di risposta alle richieste.</span><span class="sxs-lookup"><span data-stu-id="35e91-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="35e91-107">Fornisce routing incorporato dichiarativo dei messaggi ad altri servizi di Azure.</span><span class="sxs-lookup"><span data-stu-id="35e91-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="35e91-108">Offre un archivio in cui eseguire query sui metadati e informazioni di stato sincronizzate.</span><span class="sxs-lookup"><span data-stu-id="35e91-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="35e91-109">Abilita comunicazioni sicure e controllo di accesso tramite chiavi di sicurezza o certificati X.509 per dispositivo.</span><span class="sxs-lookup"><span data-stu-id="35e91-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="35e91-110">Fornisce un monitoraggio esteso per gli eventi relativi alla connettività dei dispositivi e alla gestione delle identità dei dispositivi.</span><span class="sxs-lookup"><span data-stu-id="35e91-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="35e91-111">Comprende librerie di dispositivi per i linguaggi e le piattaforme più diffusi.</span><span class="sxs-lookup"><span data-stu-id="35e91-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="35e91-112">Usare npm per installare i moduli di Hub IoT di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="35e91-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="35e91-113">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="35e91-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="35e91-114">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="35e91-114">Install the npm module</span></span>

<span data-ttu-id="35e91-115">Installare il modulo npm di Hub IoT di Azure</span><span class="sxs-lookup"><span data-stu-id="35e91-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="35e91-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="35e91-116">Example</span></span>

<span data-ttu-id="35e91-117">Questo esempio crea e assegna un nome a un hub IoT.</span><span class="sxs-lookup"><span data-stu-id="35e91-117">This example creates and names an IoT hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

<span data-ttu-id="35e91-118">Questo esempio ottiene l'hub IoT esistente, in base al nome.</span><span class="sxs-lookup"><span data-stu-id="35e91-118">This example gets the existing IoT hub, by name.</span></span>

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a><span data-ttu-id="35e91-119">Esempi</span><span class="sxs-lookup"><span data-stu-id="35e91-119">Samples</span></span>

- [<span data-ttu-id="35e91-120">Introduzione allo starter kit di Azure IoT per Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="35e91-120">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- <span data-ttu-id="35e91-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalie nella vibrazione dei tweet rilevate dai servizi IoT di Azure nei dati di Intel Edison che esegue Node.js)</span><span class="sxs-lookup"><span data-stu-id="35e91-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span>

<span data-ttu-id="35e91-122">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="35e91-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
