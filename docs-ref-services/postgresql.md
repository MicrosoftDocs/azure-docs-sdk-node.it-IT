---
title: Moduli PostgreSQL di Azure per Node.js
description: Informazioni di riferimento sui moduli PostgreSQL di Azure per Node.js
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: 706f636a89e5e89c1dbf760e01c684bcc9588f1f
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262055"
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Moduli PostgreSQL di Azure per Node.js

La libreria client consigliata per l'accesso a Database di Azure per PostgreSQL è la [raccolta di connessioni di Node.js per Database di Azure per PostgreSQL](https://www.npmjs.com/package/pg) open source. Questa libreria è un client PostgreSQL che non causa blocchi per Node.js, che supporta associazioni libpq native facoltative e JavaScript puro.

Altre informazioni su [Database di Azure per PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>Pacchetto client

### <a name="install-the-npm-module"></a>Installare il modulo npm

Usare npm per installare il modulo client PostgreSQL.

```bash
npm install pg
```   

### <a name="example"></a>Esempio

Questo esempio apre una connessione client ed esegue una query semplice.

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

## <a name="samples"></a>Esempi

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
