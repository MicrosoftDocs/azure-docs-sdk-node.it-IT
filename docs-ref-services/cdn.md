---
title: Moduli della rete CDN di Azure per Node.js
description: Informazioni di riferimento sui moduli della rete CDN di Azure per Node.js
keywords: Azure, SDK, API, rete CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a>Moduli della rete CDN di Azure per Node.js

## <a name="overview"></a>Panoramica

La rete per la distribuzione di contenuti di Azure (rete CDN) offre agli sviluppatori una soluzione globale per distribuire contenuti a larghezza di banda elevata ospitati in Azure o in altre posizioni. Con la rete CDN è possibile memorizzare nella cache gli oggetti disponibili pubblicamente caricati dall'archivio BLOB di Azure un'applicazione Web, una macchina virtuale, una cartella dell'applicazione o altre posizioni HTTP/HTTPS. La cache della rete CDN può essere mantenuta in posizioni strategiche per fornire la larghezza di banda massima per la distribuzione di contenuto agli utenti. In genere, la rete CDN viene usata per recapitare contenuto statico come immagini, fogli di stile, documenti, file script sul lato client e pagine HTML.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm della rete CDN

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti i profili della rete CDN.

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
