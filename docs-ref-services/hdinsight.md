---
title: Moduli di Azure HDInsight per Node.js
description: Informazioni di riferimento sui moduli di Azure HDInsight per Node.js
keywords: Azure, SDK, API, HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Moduli di Azure HDInsight per Node.js

## <a name="overview"></a>Panoramica

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
