---
title: Moduli di autorizzazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di autorizzazione di Azure per Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52048376"
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
