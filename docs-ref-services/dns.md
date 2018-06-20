---
title: Moduli di Azure DNS per Node.js
description: Informazioni di riferimento sui moduli di Azure DNS per Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262218"
---
# <a name="azure-dns-modules-for-nodejs"></a>Moduli di Azure DNS per Node.js

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
