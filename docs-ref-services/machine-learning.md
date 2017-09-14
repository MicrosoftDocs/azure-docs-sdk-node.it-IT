---
title: Moduli di Azure Machine Learning per Node.js
description: Informazioni di riferimento sui moduli di Azure Machine Learning per Node.js
keywords: Azure, SDK, API, Machine Learning, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 465b569d0eef53208211be2c2ff36d28bb28d107
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>Moduli di Azure Machine Learning per Node.js

## <a name="overview"></a>Panoramica

L'apprendimento automatico è una tecnica di analisi scientifica dei dati che consente ai computer di apprendere dai dati esistenti per prevedere comportamenti, risultati e tendenze futuri. Queste previsioni o stime dell'apprendimento automatico possono rendere più intelligenti le app e i dispositivi. Quando si effettuano acquisti online, l'apprendimento automatico consente di consigliare altri prodotti che potrebbero interessare in base a ciò che si è acquistato. Quando si usa la carta di credito, l'apprendimento automatico confronta la transazione con un database di transazioni e consente di rilevare eventuali frodi. Quando il robot aspirapolvere aspira la polvere in una stanza, l'apprendimento automatico gli consente di decidere se il lavoro è stato completato.

## <a name="management-package"></a>Pacchetto di gestione


### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Azure Machine Learning

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti i piani di impegno di Machine Learning.

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
