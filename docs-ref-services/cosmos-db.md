---
title: Moduli di Azure Cosmos DB per Node.js
description: Informazioni di riferimento sui moduli di Azure Cosmos DB per Node.js
keywords: Azure, SDK, API, Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="d8559-104">Moduli di Azure Cosmos DB per Node.js</span><span class="sxs-lookup"><span data-stu-id="d8559-104">Azure Cosmos DB Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d8559-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d8559-105">Overview</span></span>

<span data-ttu-id="d8559-106">Azure Cosmos DB è il database multimodello distribuito a livello globale di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d8559-106">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="d8559-107">Azure Cosmos DB garantisce la scalabilità elastica e indipendente della velocità effettiva e dello spazio di archiviazione tra un numero qualsiasi di aree geografiche di Azure.</span><span class="sxs-lookup"><span data-stu-id="d8559-107">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="d8559-108">Assicura anche velocità effettiva, latenza, disponibilità e coerenza grazie a contratti di servizio completi, una garanzia che nessun altro servizio di database riesce a offrire.</span><span class="sxs-lookup"><span data-stu-id="d8559-108">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="d8559-109">Azure Cosmos DB include un motore di database indipendente dallo schema, ottimizzato per la scrittura e gestito da risorse, che supporta in modo nativo più modelli di dati: chiave-valore, documenti, grafici e a colonne.</span><span class="sxs-lookup"><span data-stu-id="d8559-109">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="d8559-110">Supporta anche molte API per l'accesso ai dati, tra cui MongoDB, SQL di DocumentDB, Gremlin (anteprima) e tabelle di Azure (anteprima), in modo estendibile.</span><span class="sxs-lookup"><span data-stu-id="d8559-110">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="d8559-111">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="d8559-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d8559-112">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="d8559-112">Install the npm module</span></span> 

<span data-ttu-id="d8559-113">Installare il modulo npm di Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="d8559-113">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="d8559-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="d8559-114">Example</span></span>

<span data-ttu-id="d8559-115">Questo esempio elenca tutti gli account di Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="d8559-115">This example lists all Cosmos DB accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a><span data-ttu-id="d8559-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="d8559-116">Samples</span></span>

* <span data-ttu-id="d8559-117">[Developing a Node.js app using Azure Cosmos DB - DocumentDB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) (Sviluppo di un'app Node.js con Azure Cosmos DB - DocumentDB)</span><span class="sxs-lookup"><span data-stu-id="d8559-117">[Developing a Node.js app using Azure Cosmos DB - DocumentDB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)</span></span>
* <span data-ttu-id="d8559-118">[Developing a Node.js app using Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) (Sviluppo di un'app Node.js con Azure Cosmos DB - Gremlin)</span><span class="sxs-lookup"><span data-stu-id="d8559-118">[Developing a Node.js app using Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)</span></span>

<span data-ttu-id="d8559-119">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="d8559-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
