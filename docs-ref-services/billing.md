---
title: Moduli di fatturazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di fatturazione di Azure per Node.js
keywords: Azure, SDK, API, fatturazione, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a>Moduli di fatturazione di Azure per Node.js

## <a name="overview"></a>Panoramica
Le API di fatturazione di Azure forniscono l'accesso alle informazioni di fatturazione e alle fatture di Azure.

Per usare questa API, l'amministratore account deve acconsentire esplicitamente tramite il portale di Azure. Vedere [Gestire l'accesso alla fatturazione di Azure tramite i ruoli](https://docs.microsoft.com/azure/billing/billing-manage-access).

### <a name="install-the-npm-module"></a>Installare il modulo npm 

Installare il modulo di npm di fatturazione di Azure 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>Esempio 
 
Questo esempio visualizza un elenco di tutte le fatture precedenti.
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
