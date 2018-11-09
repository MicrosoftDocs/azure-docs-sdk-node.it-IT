---
title: Moduli di Azure DevTest Labs per Node.js
description: Informazioni di riferimento sui moduli di Azure DevTest Labs per Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 4528bf6a09bc86d23bfec982988added1aa3e257
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2018
ms.locfileid: "51192374"
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Moduli di Azure DevTest Labs per Node.js

Lab di sviluppo e test di Azure è un servizio che consente agli sviluppatori e ai tester di creare rapidamente ambienti in Azure riducendo al minimo gli sprechi e i costi di controllo. È possibile provare la versione più recente dell'applicazione eseguendo rapidamente il provisioning di ambienti Windows e Linux tramite modelli ed elementi riutilizzabili. Consente di integrare facilmente la pipeline di distribuzione in lab di sviluppo e test per effettuare il provisioning di ambienti su richiesta. Aumentare i propri test di carico tramite il provisioning di più agenti di test e creare ambienti di pre-provisioning per training e demo.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Azure DevTest Labs

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>Esempio

Questo esempio ottiene e visualizza i dettagli di un lab.

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
