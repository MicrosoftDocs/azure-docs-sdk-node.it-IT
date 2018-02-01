---
title: Moduli di Servizi cognitivi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Servizi cognitivi di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Moduli di Servizi cognitivi di Azure per Node.js

Servizi cognitivi di Azure sono costituiti da un set di API, SDK e servizi che aiutano gli sviluppatori a rendere le applicazioni più intelligenti, coinvolgenti e individuabili. Servizi cognitivi Microsoft si basa sul portafoglio in evoluzione di Microsoft di API di Machine Learning e consente agli sviluppatori di aggiungere facilmente funzionalità intelligenti, ad esempio il rilevamento di emozioni e video, il riconoscimento facciale, vocale e visivo, nelle applicazioni. Gli obiettivi sono un'esperienza di elaborazione più personale e una maggiore produttività supportate da sistemi che sempre più riescono a vedere, sentire, parlare, comprendere e persino iniziare a ragionare.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Servizi cognitivi di Azure

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti gli account di Servizi cognitivi.

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
