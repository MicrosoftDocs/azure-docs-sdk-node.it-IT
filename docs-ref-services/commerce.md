---
title: Moduli di Azure Commerce per Node.js
description: Informazioni di riferimento sui moduli di Azure Commerce per Node.js
keywords: Azure, SDK, API, Commerce, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a>Moduli di Azure Commerce per Node.js

## <a name="overview"></a>Panoramica

Usare le API di Azure Commerce per raccogliere e immettere i dati di uso e delle risorse negli strumenti di analisi dei dati scelti. Le API di utilizzo delle risorse di Azure e RateCard possono aiutare a prevedere e gestire i costi con precisione. Le API vengono implementate come provider di risorse, nell’ambito della famiglia di API esposte da Azure Resource Manager.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Azure Commerce

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>Esempio

Questo esempio recupera i dati sul consumo di Azure stimato per l'ultimo mese.

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
