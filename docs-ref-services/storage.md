---
title: Moduli di Archiviazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di Archiviazione di Azure per Node.js
keywords: Azure, Node, SDK, API, archiviazione, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a>Moduli di Archiviazione di Azure per Node.js

## <a name="overview"></a>Panoramica

Usare il modulo client di Archiviazione di Azure per:

- Leggere e scrivere oggetti e file dall'[archivio BLOB di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)
- Inviare e ricevere messaggi tra applicazioni connesse al cloud con l'[archiviazione code di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)
- Leggere e scrivere dati strutturati di grandi dimensioni con l'[archiviazione tabelle di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)

Creare, aggiornare e gestire gli account di archiviazione di Azure, eseguire query e rigenerare chiavi di accesso dalle app Node.js con i moduli di gestione.

## <a name="client-package"></a>Pacchetto client

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm client di Archiviazione di Azure

```bash
npm install azure-storage
```

### <a name="example"></a>Esempio

Questo esempio crea un contenitore di archiviazione e vi carica un file locale `data.txt`.

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm 

Installare il modulo npm di gestione di Archiviazione di Azure

```bash
npm install azure-arm-storage
```

### <a name="example"></a>Esempio

Questo esempio elenca gli account di archiviazione.

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Esempi

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
