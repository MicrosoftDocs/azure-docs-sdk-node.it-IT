---
title: Moduli di Azure Analysis Services per Node.js
description: Informazioni di riferimento sui moduli di Azure Analysis Services per Node.js
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 166d0450ac9b2d005f3ce4ecba5ce36e1786ae09
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="78816-103">Moduli di Azure Analysis Services per Node.js</span><span class="sxs-lookup"><span data-stu-id="78816-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="78816-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="78816-104">Overview</span></span>
<span data-ttu-id="78816-105">Questo pacchetto fornisce un modulo per Node.js che semplifica la gestione di Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="78816-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="78816-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="78816-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="78816-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="78816-107">Install the npm module</span></span>

<span data-ttu-id="78816-108">Installare il modulo npm di Azure Analysis Services</span><span class="sxs-lookup"><span data-stu-id="78816-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="78816-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="78816-109">Example</span></span>

<span data-ttu-id="78816-110">Questo esempio elenca tutti i server di Analysis Services disponibili.</span><span class="sxs-lookup"><span data-stu-id="78816-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="78816-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="78816-111">Samples</span></span>

<span data-ttu-id="78816-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="78816-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
