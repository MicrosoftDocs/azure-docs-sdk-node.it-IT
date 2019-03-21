---
title: Moduli di Automazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di Automazione di Azure per Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 281b5081163fc3b0b74219c766ff9be5c421296b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052600"
---
# <a name="azure-automation-modules-for-nodejs"></a>Moduli di Automazione di Azure per Node.js

## <a name="overview"></a>Panoramica

Automazione di Azure offre agli utenti la possibilità di automatizzare le attività manuali, a esecuzione prolungata, soggette a errori e ripetute di frequente comunemente eseguite negli ambienti cloud e aziendali. Automazione consente di risparmiare tempo e aumenta l'affidabilità delle normali attività amministrative e le pianifica anche per essere eseguite automaticamente a intervalli regolari. È possibile automatizzare i processi utilizzando runbook o automatizzare la gestione della configurazione tramite Configurazione dello stato desiderato.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-modules-with-npm"></a>Installare i moduli con npm

Usare npm per installare i moduli di Automazione di Azure per Node.js

```bash
npm install azure-arm-automation
```

### <a name="example"></a>Esempio

Questo esempio elenca gli account di Automazione.

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
