---
title: Moduli MySQL di Azure per Node.js
description: Informazioni di riferimento sui moduli MySQL di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 21b98aeba1e21ec1d9f7da4a115110fffe05b2b8
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="azure-mysql-modules-for-nodejs"></a>Moduli MySQL di Azure per Node.js

La libreria client consigliata per l'accesso a Database di Azure per MySQL è la [raccolta di connessioni di Node.js per Database di Azure per MySQL](https://github.com/sidorares/node-mysql2) open source. 

Altre informazioni su [Database di Azure per MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>Pacchetto client

### <a name="install-the-npm-module"></a>Installare il modulo npm

Usare npm per installare il modulo client MySQL.

```bash
npm install mysql2
```   

### <a name="example"></a>Esempio

Questo esempio connette a un database MySQL ed esegue una semplice query per recuperare tutti i clienti.

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

## <a name="samples"></a>Esempi

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
