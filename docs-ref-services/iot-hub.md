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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2018
ms.locfileid: "50326618"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>Moduli di Hub IoT di Azure per Node.js

L'hub IoT di Azure è un servizio completamente gestito che consente comunicazioni bidirezionali affidabili e sicure tra milioni di dispositivi IoT e un back-end della soluzione. L'hub IoT di Azure:
- Offre più opzioni di comunicazione dispositivo a cloud e cloud a dispositivo, inclusi la messaggistica unidirezionale, il trasferimento di file e i metodi di risposta alle richieste.
- Fornisce routing incorporato dichiarativo dei messaggi ad altri servizi di Azure.
- Offre un archivio in cui eseguire query sui metadati e informazioni di stato sincronizzate.
- Abilita comunicazioni sicure e controllo di accesso tramite chiavi di sicurezza o certificati X.509 per dispositivo.
- Fornisce un monitoraggio esteso per gli eventi relativi alla connettività dei dispositivi e alla gestione delle identità dei dispositivi.
- Comprende librerie di dispositivi per i linguaggi e le piattaforme più diffusi.

Usare npm per installare i moduli di Hub IoT di Azure per Node.js

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Hub IoT di Azure

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>Esempio

Questo esempio crea e assegna un nome a un hub IoT.

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

Questo esempio ottiene l'hub IoT esistente, in base al nome.

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

## <a name="samples"></a>Esempi

- [Introduzione allo starter kit di Azure IoT per Raspberry Pi](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalie nella vibrazione dei tweet rilevate dai servizi IoT di Azure nei dati di Intel Edison che esegue Node.js)

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
