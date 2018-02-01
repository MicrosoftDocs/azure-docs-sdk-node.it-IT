---
title: Moduli di Azure HDInsight per Node.js
description: Informazioni di riferimento sui moduli di Azure HDInsight per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 897ef2e3d2316a1f6f5637027ac2a2211c556f7a
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="ec19b-103">Moduli di Azure HDInsight per Node.js</span><span class="sxs-lookup"><span data-stu-id="ec19b-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="ec19b-104">Azure HDInsight è una distribuzione cloud dei componenti Hadoop di Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="ec19b-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="ec19b-105">Apache Hadoop era il framework open source originale per l'elaborazione distribuita e l'analisi di set di Big Data in cluster di computer.</span><span class="sxs-lookup"><span data-stu-id="ec19b-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="ec19b-106">HDInsight rende le tecnologie Hadoop più semplici di usare offrendo i vantaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ec19b-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="ec19b-107">Meno attività di installazione e configurazione.</span><span class="sxs-lookup"><span data-stu-id="ec19b-107">Less setup and configuration.</span></span> <span data-ttu-id="ec19b-108">Vedere Effettuare il provisioning di cluster Hadoop in HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ec19b-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="ec19b-109">Disponibilità e affidabilità elevate.</span><span class="sxs-lookup"><span data-stu-id="ec19b-109">High availability and reliability.</span></span> <span data-ttu-id="ec19b-110">Vedere Disponibilità e affidabilità di HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ec19b-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="ec19b-111">Sicurezza e la governance grazie all'integrazione con Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ec19b-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="ec19b-112">Vedere Cluster aggiunti al dominio.</span><span class="sxs-lookup"><span data-stu-id="ec19b-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="ec19b-113">Scalabilità dinamica senza interruzione dei processi</span><span class="sxs-lookup"><span data-stu-id="ec19b-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="ec19b-114">Componenti e versioni aggiornati.</span><span class="sxs-lookup"><span data-stu-id="ec19b-114">Component updates and current versions.</span></span> <span data-ttu-id="ec19b-115">Vedere Versioni di HDInsight e componenti di Hadoop.</span><span class="sxs-lookup"><span data-stu-id="ec19b-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="ec19b-116">Integrazione con altri servizi di Azure, inclusi App Web e Database SQL</span><span class="sxs-lookup"><span data-stu-id="ec19b-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="ec19b-117">Lo stack di tecnologie Hadoop include software e utilità correlate, tra cui Apache Hive, HBase, Spark, Kafka e molti altri.</span><span class="sxs-lookup"><span data-stu-id="ec19b-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="ec19b-118">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="ec19b-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="ec19b-119">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="ec19b-119">Install the npm modules</span></span>

<span data-ttu-id="ec19b-120">Usare npm per installare i moduli di Azure HDInsight per Node.js</span><span class="sxs-lookup"><span data-stu-id="ec19b-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="ec19b-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="ec19b-121">Example</span></span> 

<span data-ttu-id="ec19b-122">Questo esempio crea un client HDInsight e quindi elenca tutti i cluster disponibili.</span><span class="sxs-lookup"><span data-stu-id="ec19b-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="ec19b-123">Esempi</span><span class="sxs-lookup"><span data-stu-id="ec19b-123">Samples</span></span>

<span data-ttu-id="ec19b-124">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="ec19b-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
