---
title: Moduli di Servizi multimediali di Azure per Node.js
description: Informazioni di riferimento sui moduli di Servizi multimediali di Azure per Node.js
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: e8b2b4b994c25fadda7a37d05a12778d8c9970d8
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261993"
---
# <a name="azure-media-services-modules-for-nodejs"></a>Moduli di Servizi multimediali di Azure per Node.js

Servizi multimediali di Azure costituisce una piattaforma estensibile basata sul cloud che consente agli sviluppatori di creare applicazioni di distribuzione e gestione di contenuti multimediali altamente scalabili. Servizi multimediali si basa su API REST che consentono di caricare, archiviare e codificare contenuti video o audio in modo sicuro, nonché creare pacchetti di tali contenuti per la distribuzione in streaming live e on demand a vari client (ad esempio, TV, PC e dispositivi mobili).

Con Servizi multimediali di Azure è possibile:
- Creare flussi di lavoro end-to-end usando unicamente Servizi multimediali. 
- Usare componenti di terze parti per alcune parti del flusso di lavoro. ad esempio, la codifica con un codificatore di terze parti. Inoltre, sono possibili operazioni di caricamento, protezione, creazione di pacchetti e invio tramite Servizi multimediali.
- Eseguire lo streaming dei contenuti live o on demand. L'argomento contiene inoltre collegamenti ad altri argomenti rilevanti.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Servizi multimediali di Azure

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti i servizi multimediali per un gruppo di risorse.

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
