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
ms.openlocfilehash: 2e2813bb3b213de4066b2a3bc971586667a83f68
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51439435"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Moduli di Azure Cosmos DB per Node.js

Azure Cosmos DB è il database multimodello distribuito a livello globale di Microsoft. Azure Cosmos DB garantisce la scalabilità elastica e indipendente della velocità effettiva e dello spazio di archiviazione tra un numero qualsiasi di aree geografiche di Azure. Assicura anche velocità effettiva, latenza, disponibilità e coerenza grazie a contratti di servizio completi, una garanzia che nessun altro servizio di database riesce a offrire.

Azure Cosmos DB include un motore di database indipendente dallo schema, ottimizzato per la scrittura e gestito da risorse, che supporta in modo nativo più modelli di dati: chiave-valore, documenti, grafici e a colonne. Supporta anche molte API per l'accesso ai dati, tra cui MongoDB, SQL, Gremlin/Graph, tabelle di Azure e Cassandra (anteprima), in modo estendibile.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm 

Installare il modulo npm di Azure Cosmos DB.

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>Esempio

Questo esempio elenca tutti gli account Azure Cosmos DB.

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

## <a name="samples"></a>Esempi

* [Developing a Node.js app using Azure Cosmos DB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) (Sviluppo di un'app Node.js con Azure Cosmos DB)
* [Developing a Node.js app using Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) (Sviluppo di un'app Node.js con Azure Cosmos DB - Gremlin)

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
