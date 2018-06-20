---
title: Moduli di Cache Redis di Azure per Node.js
description: Informazioni di riferimento sui moduli di Cache Redis di Azure per Node.js
author: wesmc7777
ms.author: wesmc
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: afeee19cb79b54561b6cbef4a79de8b1606adb4d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265062"
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="a46ef-103">Moduli di Cache Redis di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="a46ef-103">Azure Redis Cache modules for Node.js</span></span>

<span data-ttu-id="a46ef-104">La cache Redis di Azure si basa sul noto progetto Redis open source.</span><span class="sxs-lookup"><span data-stu-id="a46ef-104">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="a46ef-105">Consente di accedere a un'istanza sicura e dedicata della cache Redis, gestita da Microsoft e accessibile dalle app di Azure.</span><span class="sxs-lookup"><span data-stu-id="a46ef-105">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="a46ef-106">Redis è un archivio chiave-valore avanzato, in cui le chiavi possono contenere strutture di dati come stringhe, hash, elenchi, set e set ordinati.</span><span class="sxs-lookup"><span data-stu-id="a46ef-106">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="a46ef-107">Redis supporta una serie di operazioni atomiche su questi tipi di dati.</span><span class="sxs-lookup"><span data-stu-id="a46ef-107">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="a46ef-108">Altre informazioni sulla [Cache Redis di Azure](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="a46ef-108">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="a46ef-109">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="a46ef-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a46ef-110">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="a46ef-110">Install the npm module</span></span>

<span data-ttu-id="a46ef-111">Usare npm per installare il modulo Redis per Node.js</span><span class="sxs-lookup"><span data-stu-id="a46ef-111">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="a46ef-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="a46ef-112">Example</span></span>

<span data-ttu-id="a46ef-113">Questo esempio connette a un'istanza di Cache Redis di Azure, archivia una coppia chiave/valore e quindi legge il valore archiviato in base alla chiave.</span><span class="sxs-lookup"><span data-stu-id="a46ef-113">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="a46ef-114">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="a46ef-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a46ef-115">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="a46ef-115">Install the npm module</span></span>

<span data-ttu-id="a46ef-116">Usare npm per installare i moduli di Cache Redis di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="a46ef-116">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="a46ef-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="a46ef-117">Example</span></span>

<span data-ttu-id="a46ef-118">Questo esempio esegue l'autenticazione in Azure ed elenca tutte le istanze di Cache Redis in un gruppo di risorse specificato.</span><span class="sxs-lookup"><span data-stu-id="a46ef-118">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

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


## <a name="samples"></a><span data-ttu-id="a46ef-119">Esempi</span><span class="sxs-lookup"><span data-stu-id="a46ef-119">Samples</span></span>

* [<span data-ttu-id="a46ef-120">Come usare Cache Redis di Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="a46ef-120">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="a46ef-121">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="a46ef-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
