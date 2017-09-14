---
title: Moduli di Rete virtuale di Azure per Node.js
description: Informazioni di riferimento sui moduli di Rete virtuale di Azure per Node.js
keywords: Azure, SDK, API, rete virtuale, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Moduli di Rete virtuale di Azure per Node.js

## <a name="overview"></a>Panoramica

Il servizio Rete virtuale di Azure consente di connettere tra loro le risorse di Azure in modo sicuro con reti virtuali. Una rete virtuale è una rappresentazione della propria rete nel cloud. È un isolamento logico del cloud di Azure dedicato alla sottoscrizione. È anche possibile connettere le reti virtuali alla rete locale.

Altre informazioni su [Rete virtuale di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Rete virtuale di Azure

```bash
npm install azure-arm-network
```

### <a name="example"></a>Esempio

Questo esempio ottiene e visualizza l'elenco di reti virtuali

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
