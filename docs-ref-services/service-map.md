---
title: Moduli di Mapping dei servizi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Mapping dei servizi di Azure per Node.js
keywords: Azure, SDK, API, Mapping dei servizi, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a>Moduli di Mapping dei servizi di Azure per Node.js

## <a name="overview"></a>Panoramica

Mapping dei servizi individua automaticamente i componenti delle applicazioni nei sistemi Windows e Linux ed esegue la mappatura della comunicazione fra i servizi. Il Mapping dei servizi mostra le connessioni fra i server, i processi e le porte di tutte le architetture connesse via TCP senza il bisogno di alcuna configurazione a parte l'installazione di un agente.

Altre informazioni su [Mapping dei servizi di Azure](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Mapping dei servizi di Azure

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti i mapping dei servizi per il gruppo di risorse e l'area di lavoro specificati.

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
