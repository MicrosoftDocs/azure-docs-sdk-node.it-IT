---
title: Moduli di Azure Service Fabric per Node.js
description: Informazioni di riferimento sui moduli di Azure Service Fabric per Node.js
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51438405"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="713a4-103">Moduli di Azure Service Fabric per Node.js</span><span class="sxs-lookup"><span data-stu-id="713a4-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="713a4-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="713a4-104">Overview</span></span>

<span data-ttu-id="713a4-105">Azure Service Fabric è una piattaforma di sistemi distribuiti che semplifica la disposizione in pacchetti, la distribuzione e la gestione di microservizi e contenitori scalabili e affidabili.</span><span class="sxs-lookup"><span data-stu-id="713a4-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="713a4-106">Altre informazioni su [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="713a4-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="713a4-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="713a4-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="713a4-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="713a4-108">Install the npm module</span></span>

<span data-ttu-id="713a4-109">Installare il modulo npm di Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="713a4-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="713a4-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="713a4-110">Example</span></span>

<span data-ttu-id="713a4-111">Questo esempio illustra come è possibile elencare i cluster per una sottoscrizione di Azure.</span><span class="sxs-lookup"><span data-stu-id="713a4-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="713a4-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="713a4-112">Samples</span></span>

<span data-ttu-id="713a4-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="713a4-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
