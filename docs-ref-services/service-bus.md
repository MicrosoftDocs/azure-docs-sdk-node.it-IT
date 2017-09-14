---
title: Moduli del bus di servizio di Azure per Node.js
description: Informazioni di riferimento sui moduli del bus di servizio di Azure per Node.js
keywords: Azure, SDK, API, bus di servizio, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Moduli del bus di servizio di Azure per Node.js

## <a name="overview"></a>Panoramica

Il bus di servizio di Azure è una piattaforma cloud di messaggistica asincrona che consente di scambiare dati tra sistemi disaccoppiati.

Altre informazioni sul [bus di servizio di Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Usare npm per installare il modulo del bus di servizio di Azure per Node.js

```bash
npm install azure-arm-sb
```

### <a name="example"></a>Esempio

Questo esempio crea un client e quindi elenca tutti gli spazi dei nomi del bus di servizio associati a una determinata sottoscrizione.

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
