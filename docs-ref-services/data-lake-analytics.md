---
title: Moduli di Azure Data Lake Analytics per Node.js
description: Informazioni di riferimento sui moduli di Azure Data Lake Analytics per Node.js
keywords: Azure, SDK, API, Data Lake Analytics, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 46f414ac6909de5bd956666baf51be1ca9d25ac7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Moduli di Azure Data Lake Analytics per Node.js

## <a name="overview"></a>Panoramica
Azure Data Lake Analytics è un servizio per processi di analisi su richiesta che semplifica l'analisi dei Big Data. Consente di concentrarsi su scrittura, esecuzione e gestione dei processi invece che sul funzionamento dell'infrastruttura distribuita. Anziché distribuire, configurare e ottimizzare l'hardware, è possibile scrivere query per trasformare i dati ed estrarre informazioni di interesse. Con il servizio di analisi è possibile gestire processi di qualsiasi dimensione immediatamente definendo il livello e l'ambito necessari. Verrà addebitato un costo per il processo solo durante la sua esecuzione, per la massima convenienza. Il servizio di analisi supporta l'integrazione di Azure Active Directory, che consente di gestire l'accesso e i ruoli, con il sistema di gestione delle identità locale in uso. È incluso anche U-SQL, un linguaggio che combina i vantaggi di SQL con la potenza espressiva del codice utente. Il runtime distribuito scalabile di U-SQL permette di analizzare in modo efficiente i dati nell'archivio e nel server SQL in Azure, nel database SQL di Azure e SQL Data Warehouse di Azure.

### <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Usare npm per installare i moduli di Azure Data Lake Analytics per Node.js

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti gli account di analisi per una determinata sottoscrizione.

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
