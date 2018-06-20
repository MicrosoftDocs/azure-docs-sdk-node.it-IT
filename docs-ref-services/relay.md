---
title: Moduli di inoltro di Azure per Node.js
description: Informazioni di riferimento sui moduli di inoltro di Azure per Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 1f9b4263b8ffae78fcf9f35b8ef0160095059693
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260784"
---
# <a name="azure-relay-modules-for-nodejs"></a>Moduli di inoltro di Azure per Node.js

Il servizio di inoltro di Azure crea applicazioni ibride consentendo di esporre in modo sicuro nel cloud pubblico i servizi che risiedono in una rete aziendale, senza dover aprire una connessione firewall o richiedere modifiche di notevole impatto a un'infrastruttura di rete aziendale. Il servizio di inoltro supporta un'ampia gamma di protocolli di trasporto e standard dei servizi Web.

Altre informazioni sul [servizio di inoltro di Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di inoltro di Azure

```bash
npm install azure-arm-relay
```

### <a name="example"></a>Esempio

Questo esempio elenca gli spazi dei nomi per un client di inoltro.

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
