---
title: Moduli di Azure Service Fabric per Node.js
description: Informazioni di riferimento sui moduli di Azure Service Fabric per Node.js
keywords: Azure, SDK, API, Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="ff93e-104">Moduli di Azure Service Fabric per Node.js</span><span class="sxs-lookup"><span data-stu-id="ff93e-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ff93e-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="ff93e-105">Overview</span></span>

<span data-ttu-id="ff93e-106">Azure Service Fabric è una piattaforma di sistemi distribuiti che semplifica la disposizione in pacchetti, la distribuzione e la gestione di microservizi e contenitori scalabili e affidabili.</span><span class="sxs-lookup"><span data-stu-id="ff93e-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="ff93e-107">Altre informazioni su [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="ff93e-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="ff93e-108">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="ff93e-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ff93e-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="ff93e-109">Install the npm module</span></span>

<span data-ttu-id="ff93e-110">Installare il modulo npm di Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="ff93e-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="ff93e-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="ff93e-111">Example</span></span>

<span data-ttu-id="ff93e-112">Questo esempio illustra come è possibile elencare i cluster per una sottoscrizione di Azure.</span><span class="sxs-lookup"><span data-stu-id="ff93e-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="ff93e-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="ff93e-113">Samples</span></span>

<span data-ttu-id="ff93e-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="ff93e-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
