---
title: Moduli MySQL di Azure per Node.js
description: Informazioni di riferimento sui moduli MySQL di Azure per Node.js
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2018
ms.locfileid: "51134170"
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="150f6-103">Moduli MySQL di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="150f6-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="150f6-104">La libreria client consigliata per l'accesso a Database di Azure per MySQL è la [raccolta di connessioni di Node.js per Database di Azure per MySQL](https://github.com/sidorares/node-mysql2) open source.</span><span class="sxs-lookup"><span data-stu-id="150f6-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="150f6-105">Altre informazioni su [Database di Azure per MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="150f6-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="150f6-106">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="150f6-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="150f6-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="150f6-107">Install the npm module</span></span>

<span data-ttu-id="150f6-108">Usare npm per installare il modulo client MySQL.</span><span class="sxs-lookup"><span data-stu-id="150f6-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="150f6-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="150f6-109">Example</span></span>

<span data-ttu-id="150f6-110">Questo esempio connette a un database MySQL ed esegue una semplice query per recuperare tutti i clienti.</span><span class="sxs-lookup"><span data-stu-id="150f6-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a><span data-ttu-id="150f6-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="150f6-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="150f6-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="150f6-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
