---
title: "Moduli di Utilità di pianificazione di Azure per Node.js"
description: "Informazioni di riferimento sui moduli di Utilità di pianificazione di Azure per Node.js"
keywords: "Azure, SDK, API, utilità di pianificazione, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a>Moduli di Utilità di pianificazione di Azure per Node.js

## <a name="overview"></a>Panoramica

Utilità di pianificazione di Azure crea, gestisce e richiama il lavoro pianificato tramite HTTP, HTTPS, una coda di archiviazione o il [bus di servizio di Azure](/azure/service-bus-messaging/service-bus-messaging-overview).

Altre informazioni su [Utilità di pianificazione di Azure](/azure/scheduler/scheduler-intro).

## <a name="management-package"></a>Pacchetto di gestione

Creare, gestire e richiamare il lavoro pianificato in diversi canali di comunicazione con l'API di gestione.

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Utilità di pianificazione di Azure

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>Esempio

Questo esempio elenca le utilità di pianificazione correnti.

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
