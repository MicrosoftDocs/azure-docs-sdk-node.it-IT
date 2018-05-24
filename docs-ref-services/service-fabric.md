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
ms.openlocfilehash: 12fcc4af4a78cc01370355cba0b4c642f202a30c
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="82254-103">Moduli di Azure Service Fabric per Node.js</span><span class="sxs-lookup"><span data-stu-id="82254-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="82254-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="82254-104">Overview</span></span>

<span data-ttu-id="82254-105">Azure Service Fabric è una piattaforma di sistemi distribuiti che semplifica la disposizione in pacchetti, la distribuzione e la gestione di microservizi e contenitori scalabili e affidabili.</span><span class="sxs-lookup"><span data-stu-id="82254-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="82254-106">Altre informazioni su [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="82254-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="82254-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="82254-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="82254-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="82254-108">Install the npm module</span></span>

<span data-ttu-id="82254-109">Installare il modulo npm di Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="82254-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="82254-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="82254-110">Example</span></span>

<span data-ttu-id="82254-111">Questo esempio illustra come è possibile elencare i cluster per una sottoscrizione di Azure.</span><span class="sxs-lookup"><span data-stu-id="82254-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="82254-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="82254-112">Samples</span></span>

<span data-ttu-id="82254-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="82254-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
