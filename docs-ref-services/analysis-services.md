---
title: Moduli di Azure Analysis Services per Node.js
description: Informazioni di riferimento sui moduli di Azure Analysis Services per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 7dd9ac4a2a4939b66f5a91d048e49fb59cd547c0
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="d6579-103">Moduli di Azure Analysis Services per Node.js</span><span class="sxs-lookup"><span data-stu-id="d6579-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d6579-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d6579-104">Overview</span></span>
<span data-ttu-id="d6579-105">Questo pacchetto fornisce un modulo per Node.js che semplifica la gestione di Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="d6579-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="d6579-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="d6579-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d6579-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="d6579-107">Install the npm module</span></span>

<span data-ttu-id="d6579-108">Installare il modulo npm di Azure Analysis Services</span><span class="sxs-lookup"><span data-stu-id="d6579-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="d6579-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="d6579-109">Example</span></span>

<span data-ttu-id="d6579-110">Questo esempio elenca tutti i server di Analysis Services disponibili.</span><span class="sxs-lookup"><span data-stu-id="d6579-110">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="d6579-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="d6579-111">Samples</span></span>

<span data-ttu-id="d6579-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="d6579-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
