---
title: Moduli di Hub di notifica di Azure per Node.js
description: Informazioni di riferimento sui moduli di Hub di notifica di Azure per Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "49720686"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Moduli di Hub di notifica di Azure per Node.js

Hub di notifica di Azure offre un motore di push di facile uso, multipiattaforma e con scalabilità orizzontale. Con una sola chiamata all'API multipiattaforma, è possibile inviare facilmente notifiche push mirate e personalizzate a qualsiasi piattaforma mobile da qualsiasi cloud o back-end locale.

Hub di notifica funziona perfettamente per scenari aziendali e di consumo. Di seguito sono riportati alcuni esempi degli usi di Hub di notifica fatti dai clienti:
- Invio di notifiche sulle ultime notizie a milioni di utenti con bassa latenza.
- Invio di coupon in base alla posizione a segmenti di utenti interessati.
- Invio di notifiche sugli eventi a utenti o gruppi per applicazioni di media, sport, finanza e gioco.
- Contenuti push promozionali per le app per coinvolgere e offrire prodotti ai clienti.
- Notifiche agli utenti su eventi aziendali, come nuovi messaggi ed elementi di lavoro.
- Invio di codici per l'autenticazione a più fattori.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo Hub di notifica di Azure 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti gli hub di notifica.

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a>Esempi

* [App Service Mobile completed quickstart for Node.js backend](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/) (Guida introduttiva per dispositivi mobili del servizio app per back-end Node.js completata)
* [Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalie nella vibrazione dei tweet rilevate dai servizi IoT di Azure nei dati di Intel Edison che esegue Node.js)

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
