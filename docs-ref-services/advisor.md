---
title: Moduli di Azure Advisor per Node.js
description: Informazioni di riferimento sui moduli di Azure Advisor per Node.js
keywords: Azure, SDK, API, Advisor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a>Moduli di Azure Advisor per Node.js

## <a name="overview"></a>Panoramica

Azure Advisor è un consulente cloud personalizzato che illustra come seguire le procedure consigliate per ottimizzare le distribuzioni di Azure. Advisor analizza i dati di telemetria dell'uso e della configurazione delle risorse e consiglia soluzioni che consentono di migliorare l'efficienza dei costi, le prestazioni, la disponibilità elevata e la sicurezza delle risorse di Azure.

Con Advisor, è possibile:
- Ottenere consigli personalizzati, attuabili e proattivi sulle procedure consigliate.
- Migliorare le prestazioni, la sicurezza e la disponibilità elevata delle risorse, cercando le opportunità per ridurre la spesa complessiva di Azure.
- Ricevere consigli con azioni proposte incorporate.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Azure Advisor

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>Esempio

Questo esempio visualizza l'elenco di raccomandazioni di Azure Advisor.

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
