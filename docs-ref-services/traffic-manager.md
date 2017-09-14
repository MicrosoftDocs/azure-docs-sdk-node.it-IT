---
title: Moduli di Gestione traffico di Azure per Node.js
description: Informazioni di riferimento sui moduli di Gestione traffico di Azure per Node.js
keywords: Azure, SDK, API, Gestione traffico, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>Moduli di Gestione traffico di Azure per Node.js

## <a name="overview"></a>Panoramica

Gestione traffico di Microsoft Azure consente di controllare la distribuzione del traffico utente per gli endpoint di servizio in diversi data center. Gli endpoint di servizio supportati da Gestione traffico includono servizi cloud, app Web e macchine virtuali di Azure. È anche possibile usare Gestione traffico con endpoint esterni, non di Azure.

Altre informazioni su [Gestione traffico di Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Gestione Traffico di Azure

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>Esempio

Questo esempio elenca tutte le istanze di Gestione traffico per un determinato gruppo di risorse.

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
