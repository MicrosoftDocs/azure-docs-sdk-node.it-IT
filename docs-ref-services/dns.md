---
title: Moduli di Azure DNS per Node.js
description: Informazioni di riferimento sui moduli di Azure DNS per Node.js
keywords: Azure, SDK, API, DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a>Moduli di Azure DNS per Node.js

## <a name="overview"></a>Panoramica

Usare Azure DNS per ospitare i domini DNS (Domain Name System) in Azure. Gestire i record DNS con le stesse credenziali, le stesse modalità di fatturazione e lo stesso contratto di supporto tecnico degli altri servizi di Azure. Integrare agevolmente i servizi basati su Azure con gli aggiornamenti DNS corrispondenti, semplificando il processo di distribuzione end-to-end.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Azure DNS

```bash
npm install azure-arm-dns
```

### <a name="example"></a>Esempio

Questo esempio elenca le zone di gestione DNS.

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
