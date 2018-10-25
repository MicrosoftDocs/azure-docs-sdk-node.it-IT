---
title: Moduli di Azure Commerce per Node.js
description: Informazioni di riferimento sui moduli di Azure Commerce per Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 87a0e8d689d8d782a705a4525fdbe9b681403c07
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "49757396"
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="d1213-103">Moduli di Azure Commerce per Node.js</span><span class="sxs-lookup"><span data-stu-id="d1213-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d1213-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d1213-104">Overview</span></span>

<span data-ttu-id="d1213-105">Usare le API di Azure Commerce per raccogliere e immettere i dati di uso e delle risorse negli strumenti di analisi dei dati scelti.</span><span class="sxs-lookup"><span data-stu-id="d1213-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="d1213-106">Le API di utilizzo delle risorse di Azure e RateCard possono aiutare a prevedere e gestire i costi con precisione.</span><span class="sxs-lookup"><span data-stu-id="d1213-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="d1213-107">Le API vengono implementate come provider di risorse, nell’ambito della famiglia di API esposte da Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="d1213-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="d1213-108">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="d1213-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d1213-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="d1213-109">Install the npm module</span></span>

<span data-ttu-id="d1213-110">Installare il modulo npm di Azure Commerce</span><span class="sxs-lookup"><span data-stu-id="d1213-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="d1213-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="d1213-111">Example</span></span>

<span data-ttu-id="d1213-112">Questo esempio recupera i dati sul consumo di Azure stimato per l'ultimo mese.</span><span class="sxs-lookup"><span data-stu-id="d1213-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="d1213-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="d1213-113">Samples</span></span>

<span data-ttu-id="d1213-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="d1213-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
