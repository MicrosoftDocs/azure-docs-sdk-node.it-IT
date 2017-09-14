---
title: Moduli di Hub eventi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Hub eventi di Azure per Node.js
keywords: Azure, SDK, API, Hub eventi, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a>Moduli di Hub eventi di Azure per Node.js

## <a name="overview"></a>Panoramica
Hub eventi di Azure è una piattaforma di streaming di dati estremamente scalabile e un servizio di inserimento degli eventi che consente di ricevere ed elaborare milioni di eventi al secondo. Hub eventi consente di elaborare e archiviare eventi, dati o dati di telemetria generati dal software distribuito e dai dispositivi. I dati inviati a un hub eventi possono essere trasformati e archiviati usando qualsiasi provider di analisi in tempo reale o adattatori di invio in batch/archiviazione. Con la possibilità di fornire funzionalità di pubblicazione-sottoscrizione con una latenza bassa e su larga scala, Hub eventi funge da "rampa di ingresso" per Big Data.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm 

Usare npm per installare i moduli di Hub eventi di Azure per Node.js

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a>Esempio

Questo esempio recupera informazioni su un hub eventi esistente.

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
