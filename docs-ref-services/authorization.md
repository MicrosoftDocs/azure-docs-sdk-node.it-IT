---
title: Moduli di autorizzazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di autorizzazione di Azure per Node.js
keywords: Azure, SDK, API, autorizzazione, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a>Moduli di autorizzazione di Azure per Node.js

## <a name="overview"></a>Panoramica

La funzionalità di autenticazione/autorizzazione del servizio app di Azure consente all'applicazione di eseguire la procedura di accesso degli utenti in modo che non sia necessario modificare il codice nel back-end dell'app. L'autorizzazione fornisce un modo semplice per proteggere l'applicazione e lavorare con i dati per utente.

## <a name="management-package"></a>Pacchetto di gestione

Usare npm per installare i moduli di autorizzazione di Azure per Node.js

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di autorizzazione di Azure

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>Esempio

Questo esempio elenca tutte le assegnazioni di ruolo per il gruppo di risorse richiesto.

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
