---
title: Moduli SQL di Azure per Node.js
description: Informazioni di riferimento sui moduli SQL di Azure per Node.js
keywords: Azure, Node, SDK, API, nodejs, javascript, sql
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="cb162-104">Moduli SQL di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="cb162-104">Azure SQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="cb162-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="cb162-105">Overview</span></span>

<span data-ttu-id="cb162-106">Usare i dati archiviati nel [database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) da Node.js.</span><span class="sxs-lookup"><span data-stu-id="cb162-106">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="cb162-107">La libreria di gestione fornisce un'interfaccia che facilita la gestione dei database SQL di Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="cb162-107">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="cb162-108">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="cb162-108">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cb162-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="cb162-109">Install the npm module</span></span>

<span data-ttu-id="cb162-110">Installare il modulo npm client di SQL Server</span><span class="sxs-lookup"><span data-stu-id="cb162-110">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="cb162-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="cb162-111">Example</span></span>

<span data-ttu-id="cb162-112">Questo esempio si connette a un database SQL Server ed esegue una query semplice.</span><span class="sxs-lookup"><span data-stu-id="cb162-112">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="cb162-113">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="cb162-113">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="cb162-114">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="cb162-114">Install npm modules</span></span>

<span data-ttu-id="cb162-115">Installare il modulo npm di gestione del server di Azure SQL</span><span class="sxs-lookup"><span data-stu-id="cb162-115">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="cb162-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="cb162-116">Example</span></span>

<span data-ttu-id="cb162-117">Eseguire l'autenticazione, creare un client ed elencare tutti i server.</span><span class="sxs-lookup"><span data-stu-id="cb162-117">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="cb162-118">Esempi</span><span class="sxs-lookup"><span data-stu-id="cb162-118">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="cb162-119">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="cb162-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
