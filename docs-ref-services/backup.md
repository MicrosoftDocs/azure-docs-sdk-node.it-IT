---
title: Moduli di Backup di Azure per Node.js
description: Informazioni di riferimento sui moduli di Backup di Azure per Node.js
keywords: Azure, SDK, API, Backup, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 3ff9bff16a520bca461198531fd4c02139d2b293
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-backup-modules-for-nodejs"></a>Moduli di Backup di Azure per Node.js

## <a name="overview"></a>Panoramica

Backup di Azure è il servizio basato su Azure che consente di eseguire il backup, la protezione e il ripristino dei dati in Microsoft Cloud. Backup di Azure sostituisce la soluzione di backup locale o esterna esistente con una soluzione basata sul cloud affidabile, sicura e conveniente. Backup di Azure offre più componenti che vengono scaricati e distribuiti nel computer o server appropriato o nel cloud. Il componente o l'agente distribuito dipende da ciò che si intende proteggere. Tutti i componenti di Backup di Azure consentono di eseguire il backup dei dati in un insieme di credenziali di Servizi di ripristino, a prescindere che i dati da proteggere si trovino in locale o nel cloud. 

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-modules-with-npm"></a>Installare i moduli con npm

Usare npm per installare i moduli di Backup di Azure per Node.js

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>Esempio

Questo esempio elenca i processi di ripristino per un determinato insieme di credenziali e gruppo di risorse.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
