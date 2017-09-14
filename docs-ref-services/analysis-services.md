---
title: Moduli di Azure Analysis Services per Node.js
description: Informazioni di riferimento sui moduli di Azure Analysis Services per Node.js
keywords: Azure, SDK, API, Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="cd431-104">Moduli di Azure Analysis Services per Node.js</span><span class="sxs-lookup"><span data-stu-id="cd431-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="cd431-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="cd431-105">Overview</span></span>
<span data-ttu-id="cd431-106">Questo pacchetto fornisce un modulo per Node.js che semplifica la gestione di Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="cd431-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="cd431-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="cd431-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cd431-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="cd431-108">Install the npm module</span></span>

<span data-ttu-id="cd431-109">Installare il modulo npm di Azure Analysis Services</span><span class="sxs-lookup"><span data-stu-id="cd431-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="cd431-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="cd431-110">Example</span></span>

<span data-ttu-id="cd431-111">Questo esempio elenca tutti i server di Analysis Services disponibili.</span><span class="sxs-lookup"><span data-stu-id="cd431-111">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="cd431-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="cd431-112">Samples</span></span>

<span data-ttu-id="cd431-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="cd431-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
