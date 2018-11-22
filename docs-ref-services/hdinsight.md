---
title: Moduli di Azure HDInsight per Node.js
description: Informazioni di riferimento sui moduli di Azure HDInsight per Node.js
ms.service: hdinsight
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.topic: article
ms.devlang: nodejs
ms.date: 07/18/2017
ms.openlocfilehash: e35e0d487efce2a591130403f8b72a43c638fdec
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52101726"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Moduli di Azure HDInsight per Node.js

Azure HDInsight è una distribuzione cloud dei componenti Hadoop di Hortonworks Data Platform (HDP). Apache Hadoop era il framework open source originale per l'elaborazione distribuita e l'analisi di set di Big Data in cluster di computer.

HDInsight rende le tecnologie Hadoop più semplici di usare offrendo i vantaggi seguenti:
- Meno attività di installazione e configurazione. Vedere Effettuare il provisioning di cluster Hadoop in HDInsight.
- Disponibilità e affidabilità elevate. Vedere Disponibilità e affidabilità di HDInsight.
- Sicurezza e la governance grazie all'integrazione con Active Directory. Vedere Cluster aggiunti al dominio.
- Scalabilità dinamica senza interruzione dei processi
- Componenti e versioni aggiornati. Vedere Versioni di HDInsight e componenti di Hadoop.
- Integrazione con altri servizi di Azure, inclusi App Web e Database SQL

Lo stack di tecnologie Hadoop include software e utilità correlate, tra cui Apache Hive, HBase, Spark, Kafka e molti altri. 

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-modules"></a>Installare i moduli npm

Usare npm per installare i moduli di Azure HDInsight per Node.js

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>Esempio 

Questo esempio crea un client HDInsight e quindi elenca tutti i cluster disponibili. 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
