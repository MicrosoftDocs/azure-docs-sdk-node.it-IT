---
title: Moduli SQL di Azure per Node.js
description: Informazioni di riferimento sui moduli SQL di Azure per Node.js
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 095a54a0919b237891ea89f4c826be0fc3060bbe
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259446"
---
# <a name="azure-sql-modules-for-nodejs"></a>Moduli SQL di Azure per Node.js

Usare i dati archiviati nel [database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) da Node.js.
La libreria di gestione fornisce un'interfaccia che facilita la gestione dei database SQL di Microsoft Azure.

## <a name="client-package"></a>Pacchetto client

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm client di SQL Server

```bash
npm install tedious
```

### <a name="example"></a>Esempio

Questo esempio si connette a un database SQL Server ed esegue una query semplice.

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-npm-modules"></a>Installare i moduli npm

Installare il modulo npm di gestione del server di Azure SQL

```
npm install azure-arm-sql
```   

### <a name="example"></a>Esempio

Eseguire l'autenticazione, creare un client ed elencare tutti i server.

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Esempi

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
