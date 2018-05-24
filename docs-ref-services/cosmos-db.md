---
title: Moduli di Azure Cosmos DB per Node.js
description: Informazioni di riferimento sui moduli di Azure Cosmos DB per Node.js
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 4064f9f6c0e1369c8d6261a70709102e7492b340
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="9bf69-103">Moduli di Azure Cosmos DB per Node.js</span><span class="sxs-lookup"><span data-stu-id="9bf69-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="9bf69-104">Azure Cosmos DB è il database multimodello distribuito a livello globale di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9bf69-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="9bf69-105">Azure Cosmos DB garantisce la scalabilità elastica e indipendente della velocità effettiva e dello spazio di archiviazione tra un numero qualsiasi di aree geografiche di Azure.</span><span class="sxs-lookup"><span data-stu-id="9bf69-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="9bf69-106">Assicura anche velocità effettiva, latenza, disponibilità e coerenza grazie a contratti di servizio completi, una garanzia che nessun altro servizio di database riesce a offrire.</span><span class="sxs-lookup"><span data-stu-id="9bf69-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="9bf69-107">Azure Cosmos DB include un motore di database indipendente dallo schema, ottimizzato per la scrittura e gestito da risorse, che supporta in modo nativo più modelli di dati: chiave-valore, documenti, grafici e a colonne.</span><span class="sxs-lookup"><span data-stu-id="9bf69-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="9bf69-108">Supporta anche molte API per l'accesso ai dati, tra cui MongoDB, SQL, Gremlin/Graph, tabelle di Azure e Cassandra (anteprima), in modo estendibile.</span><span class="sxs-lookup"><span data-stu-id="9bf69-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="9bf69-109">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="9bf69-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9bf69-110">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="9bf69-110">Install the npm module</span></span> 

<span data-ttu-id="9bf69-111">Installare il modulo npm di Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="9bf69-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="9bf69-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="9bf69-112">Example</span></span>

<span data-ttu-id="9bf69-113">Questo esempio elenca tutti gli account Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="9bf69-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9bf69-114">Esempi</span><span class="sxs-lookup"><span data-stu-id="9bf69-114">Samples</span></span>

* <span data-ttu-id="9bf69-115">[Developing a Node.js app using Azure Cosmos DB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) (Sviluppo di un'app Node.js con Azure Cosmos DB)</span><span class="sxs-lookup"><span data-stu-id="9bf69-115">[Developing a Node.js app using Azure Cosmos DB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)</span></span>
* <span data-ttu-id="9bf69-116">[Developing a Node.js app using Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) (Sviluppo di un'app Node.js con Azure Cosmos DB - Gremlin)</span><span class="sxs-lookup"><span data-stu-id="9bf69-116">[Developing a Node.js app using Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)</span></span>

<span data-ttu-id="9bf69-117">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="9bf69-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
