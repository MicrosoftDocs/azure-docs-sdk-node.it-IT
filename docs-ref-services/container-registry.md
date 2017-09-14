---
title: Moduli di Registro contenitori di Azure per Node.js
description: Informazioni di riferimento sui moduli di Registro contenitori di Azure per Node.js
keywords: Azure, SDK, API, registro contenitori, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Moduli di Registro contenitori di Azure per Node.js

## <a name="overview"></a>Panoramica

Registro contenitori di Azure è un servizio gestito di registri Docker basato sull'applicazione open source Docker Registry 2.0. Creare e gestire registri contenitori di Azure per archiviare e gestire immagini contenitore Docker private. È possibile usare i registri contenitori in Azure con la pipeline di sviluppo e distribuzione di contenitori esistente e attingere alle competenze della community Docker.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Registro contenitori di Azure

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>Esempio

Questo esempio ottiene un elenco dei contenitori disponibili.

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
