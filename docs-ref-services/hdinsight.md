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
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="c28ce-104">Moduli di Azure HDInsight per Node.js</span><span class="sxs-lookup"><span data-stu-id="c28ce-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c28ce-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="c28ce-105">Overview</span></span>

<span data-ttu-id="c28ce-106">Azure HDInsight è una distribuzione cloud dei componenti Hadoop di Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="c28ce-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="c28ce-107">Apache Hadoop era il framework open source originale per l'elaborazione distribuita e l'analisi di set di Big Data in cluster di computer.</span><span class="sxs-lookup"><span data-stu-id="c28ce-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="c28ce-108">HDInsight rende le tecnologie Hadoop più semplici di usare offrendo i vantaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="c28ce-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="c28ce-109">Meno attività di installazione e configurazione.</span><span class="sxs-lookup"><span data-stu-id="c28ce-109">Less setup and configuration.</span></span> <span data-ttu-id="c28ce-110">Vedere Effettuare il provisioning di cluster Hadoop in HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c28ce-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="c28ce-111">Disponibilità e affidabilità elevate.</span><span class="sxs-lookup"><span data-stu-id="c28ce-111">High availability and reliability.</span></span> <span data-ttu-id="c28ce-112">Vedere Disponibilità e affidabilità di HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c28ce-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="c28ce-113">Sicurezza e la governance grazie all'integrazione con Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c28ce-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="c28ce-114">Vedere Cluster aggiunti al dominio.</span><span class="sxs-lookup"><span data-stu-id="c28ce-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="c28ce-115">Scalabilità dinamica senza interruzione dei processi</span><span class="sxs-lookup"><span data-stu-id="c28ce-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="c28ce-116">Componenti e versioni aggiornati.</span><span class="sxs-lookup"><span data-stu-id="c28ce-116">Component updates and current versions.</span></span> <span data-ttu-id="c28ce-117">Vedere Versioni di HDInsight e componenti di Hadoop.</span><span class="sxs-lookup"><span data-stu-id="c28ce-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="c28ce-118">Integrazione con altri servizi di Azure, inclusi App Web e Database SQL</span><span class="sxs-lookup"><span data-stu-id="c28ce-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="c28ce-119">Lo stack di tecnologie Hadoop include software e utilità correlate, tra cui Apache Hive, HBase, Spark, Kafka e molti altri.</span><span class="sxs-lookup"><span data-stu-id="c28ce-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="c28ce-120">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="c28ce-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="c28ce-121">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="c28ce-121">Install the npm modules</span></span>

<span data-ttu-id="c28ce-122">Usare npm per installare i moduli di Azure HDInsight per Node.js</span><span class="sxs-lookup"><span data-stu-id="c28ce-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="c28ce-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="c28ce-123">Example</span></span> 

<span data-ttu-id="c28ce-124">Questo esempio crea un client HDInsight e quindi elenca tutti i cluster disponibili.</span><span class="sxs-lookup"><span data-stu-id="c28ce-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="c28ce-125">Esempi</span><span class="sxs-lookup"><span data-stu-id="c28ce-125">Samples</span></span>

<span data-ttu-id="c28ce-126">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="c28ce-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
