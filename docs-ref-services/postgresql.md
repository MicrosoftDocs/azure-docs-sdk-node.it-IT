---
title: Moduli PostgreSQL di Azure per Node.js
description: Informazioni di riferimento sui moduli PostgreSQL di Azure per Node.js
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "49772236"
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="6c176-103">Moduli PostgreSQL di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="6c176-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="6c176-104">La libreria client consigliata per l'accesso a Database di Azure per PostgreSQL è la [raccolta di connessioni di Node.js per Database di Azure per PostgreSQL](https://www.npmjs.com/package/pg) open source.</span><span class="sxs-lookup"><span data-stu-id="6c176-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="6c176-105">Questa libreria è un client PostgreSQL che non causa blocchi per Node.js, che supporta associazioni libpq native facoltative e JavaScript puro.</span><span class="sxs-lookup"><span data-stu-id="6c176-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="6c176-106">Altre informazioni su [Database di Azure per PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="6c176-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="6c176-107">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="6c176-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6c176-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="6c176-108">Install the npm module</span></span>

<span data-ttu-id="6c176-109">Usare npm per installare il modulo client PostgreSQL.</span><span class="sxs-lookup"><span data-stu-id="6c176-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="6c176-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="6c176-110">Example</span></span>

<span data-ttu-id="6c176-111">Questo esempio apre una connessione client ed esegue una query semplice.</span><span class="sxs-lookup"><span data-stu-id="6c176-111">This example opens a client connection and executes a simple query.</span></span>

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a><span data-ttu-id="6c176-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="6c176-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="6c176-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="6c176-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
