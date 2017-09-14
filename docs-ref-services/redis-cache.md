---
title: Moduli di Cache Redis di Azure per Node.js
description: Informazioni di riferimento sui moduli di Cache Redis di Azure per Node.js
keywords: Azure, SDK, API, Redis Cache, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>Moduli di Cache Redis di Azure per Node.js

## <a name="overview"></a>Panoramica

La cache Redis di Azure si basa sul noto progetto Redis open source. Consente di accedere a un'istanza sicura e dedicata della cache Redis, gestita da Microsoft e accessibile dalle app di Azure.

Redis è un archivio chiave-valore avanzato, in cui le chiavi possono contenere strutture di dati come stringhe, hash, elenchi, set e set ordinati. Redis supporta una serie di operazioni atomiche su questi tipi di dati.

Altre informazioni sulla [Cache Redis di Azure](https://docs.microsoft.com/azure/redis-cache/).

## <a name="client-package"></a>Pacchetto client

### <a name="install-the-npm-module"></a>Installare il modulo npm

Usare npm per installare il modulo Redis per Node.js

```bash
npm install redis
```

### <a name="example"></a>Esempio

Questo esempio connette a un'istanza di Cache Redis di Azure, archivia una coppia chiave/valore e quindi legge il valore archiviato in base alla chiave.

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Usare npm per installare i moduli di Cache Redis di Azure per Node.js

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>Esempio

Questo esempio esegue l'autenticazione in Azure ed elenca tutte le istanze di Cache Redis in un gruppo di risorse specificato.

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a>Esempi

* [Come usare Cache Redis di Azure con Node.js](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
