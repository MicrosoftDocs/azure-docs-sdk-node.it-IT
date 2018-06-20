---
title: Moduli di macchine virtuali di Azure per Node.js - Azure
description: Guida di riferimento sui moduli di macchine virtuali di Azure per Node.js
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259843"
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Moduli di macchine virtuali di Azure per Node.js

## <a name="overview"></a>Panoramica

Definire, configurare e distribuire nuovi set di scalabilità di macchine virtuali e macchine virtuali Windows e Linux dal codice con i moduli di gestione di Azure per Node.js. I moduli consentono di avviare e arrestare le macchine virtuali esistenti e di collegare o scollegare i dischi nelle VM arrestate nella sottoscrizione di Azure.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di calcolo di Azure

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>Esempio

L'esempio seguente illustra come accedere ad Azure, creare un client di gestione ed elencare tutte le immagini di VM per la località, l'entità di pubblicazione, l'offerta e lo SKU specificati.

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Esempi

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
