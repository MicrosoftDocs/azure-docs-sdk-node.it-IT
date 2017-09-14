---
title: Moduli di Servizi cognitivi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Servizi cognitivi di Azure per Node.js
keywords: Azure, SDK, API, Servizi cognitivi, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Moduli di Servizi cognitivi di Azure per Node.js

## <a name="overview"></a>Panoramica

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
