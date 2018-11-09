---
title: Moduli di Rete virtuale di Azure per Node.js
description: Informazioni di riferimento sui moduli di Rete virtuale di Azure per Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 11341fdff5df3b7521319d841707493db1d07732
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2018
ms.locfileid: "51062050"
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
