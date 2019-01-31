---
title: Moduli SQL di Azure per Node.js
description: Informazioni di riferimento sui moduli SQL di Azure per Node.js
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: sql-database
ms.subservice: development
ms.openlocfilehash: 00ba5984b5f8aef85570c54f23efefd1d741ca57
ms.sourcegitcommit: 0e294f7c4dcdfae9df18ff3e82b6563680ef2519
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55046431"
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="ca1d1-103">Moduli SQL di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="ca1d1-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="ca1d1-104">Usare i dati archiviati nel [database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) da Node.js.</span><span class="sxs-lookup"><span data-stu-id="ca1d1-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="ca1d1-105">La libreria di gestione fornisce un'interfaccia che facilita la gestione dei database SQL di Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ca1d1-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="ca1d1-106">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="ca1d1-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ca1d1-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="ca1d1-107">Install the npm module</span></span>

<span data-ttu-id="ca1d1-108">Installare il modulo npm client di SQL Server</span><span class="sxs-lookup"><span data-stu-id="ca1d1-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="ca1d1-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="ca1d1-109">Example</span></span>

<span data-ttu-id="ca1d1-110">Questo esempio si connette a un database SQL Server ed esegue una query semplice.</span><span class="sxs-lookup"><span data-stu-id="ca1d1-110">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="ca1d1-111">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="ca1d1-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="ca1d1-112">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="ca1d1-112">Install npm modules</span></span>

<span data-ttu-id="ca1d1-113">Installare il modulo npm di gestione del server di Azure SQL</span><span class="sxs-lookup"><span data-stu-id="ca1d1-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="ca1d1-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="ca1d1-114">Example</span></span>

<span data-ttu-id="ca1d1-115">Eseguire l'autenticazione, creare un client ed elencare tutti i server.</span><span class="sxs-lookup"><span data-stu-id="ca1d1-115">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ca1d1-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="ca1d1-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="ca1d1-117">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="ca1d1-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
