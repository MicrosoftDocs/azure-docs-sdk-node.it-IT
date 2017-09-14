---
title: Moduli di Monitoraggio di Azure per Node.js
description: Informazioni di riferimento sui moduli di Monitoraggio di Azure per Node.js
keywords: Azure, SDK, API, Monitoraggio, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a>Moduli di Monitoraggio di Azure per Node.js

## <a name="overview"></a>Panoramica
Le applicazioni cloud sono complesse e hanno molte parti mobili. Il monitoraggio offre la possibilità di garantire il funzionamento e l'integrità dell'applicazione. Consente anche di prevenire i problemi potenziali o di risolvere quelli precedenti. Inoltre, è possibile usare i dati di monitoraggio per ottenere informazioni approfondite sull'applicazione, utili per migliorarne le prestazioni o la manutenibilità oppure per automatizzare azioni che altrimenti richiederebbero un intervento manuale.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-npm-module"></a>Installare il modulo npm

```bash
npm install azure-arm-monitor
```

### <a name="example"></a>Esempio

Questo esempio di codice visualizza tutte le regole di avviso associate a un gruppo di risorse.

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
