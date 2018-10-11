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
ms.openlocfilehash: 9a40830e7c5330d4e258840b1b1b2210acf891c5
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "48956275"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="4051c-103">Moduli di Azure HDInsight per Node.js</span><span class="sxs-lookup"><span data-stu-id="4051c-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="4051c-104">Azure HDInsight è una distribuzione cloud dei componenti Hadoop di Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="4051c-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="4051c-105">Apache Hadoop era il framework open source originale per l'elaborazione distribuita e l'analisi di set di Big Data in cluster di computer.</span><span class="sxs-lookup"><span data-stu-id="4051c-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="4051c-106">HDInsight rende le tecnologie Hadoop più semplici di usare offrendo i vantaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4051c-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="4051c-107">Meno attività di installazione e configurazione.</span><span class="sxs-lookup"><span data-stu-id="4051c-107">Less setup and configuration.</span></span> <span data-ttu-id="4051c-108">Vedere Effettuare il provisioning di cluster Hadoop in HDInsight.</span><span class="sxs-lookup"><span data-stu-id="4051c-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="4051c-109">Disponibilità e affidabilità elevate.</span><span class="sxs-lookup"><span data-stu-id="4051c-109">High availability and reliability.</span></span> <span data-ttu-id="4051c-110">Vedere Disponibilità e affidabilità di HDInsight.</span><span class="sxs-lookup"><span data-stu-id="4051c-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="4051c-111">Sicurezza e la governance grazie all'integrazione con Active Directory.</span><span class="sxs-lookup"><span data-stu-id="4051c-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="4051c-112">Vedere Cluster aggiunti al dominio.</span><span class="sxs-lookup"><span data-stu-id="4051c-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="4051c-113">Scalabilità dinamica senza interruzione dei processi</span><span class="sxs-lookup"><span data-stu-id="4051c-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="4051c-114">Componenti e versioni aggiornati.</span><span class="sxs-lookup"><span data-stu-id="4051c-114">Component updates and current versions.</span></span> <span data-ttu-id="4051c-115">Vedere Versioni di HDInsight e componenti di Hadoop.</span><span class="sxs-lookup"><span data-stu-id="4051c-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="4051c-116">Integrazione con altri servizi di Azure, inclusi App Web e Database SQL</span><span class="sxs-lookup"><span data-stu-id="4051c-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="4051c-117">Lo stack di tecnologie Hadoop include software e utilità correlate, tra cui Apache Hive, HBase, Spark, Kafka e molti altri.</span><span class="sxs-lookup"><span data-stu-id="4051c-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="4051c-118">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="4051c-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="4051c-119">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="4051c-119">Install the npm modules</span></span>

<span data-ttu-id="4051c-120">Usare npm per installare i moduli di Azure HDInsight per Node.js</span><span class="sxs-lookup"><span data-stu-id="4051c-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="4051c-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="4051c-121">Example</span></span> 

<span data-ttu-id="4051c-122">Questo esempio crea un client HDInsight e quindi elenca tutti i cluster disponibili.</span><span class="sxs-lookup"><span data-stu-id="4051c-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="4051c-123">Esempi</span><span class="sxs-lookup"><span data-stu-id="4051c-123">Samples</span></span>

<span data-ttu-id="4051c-124">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="4051c-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
