---
title: Moduli di fatturazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di fatturazione di Azure per Node.js
keywords: Azure, SDK, API, fatturazione, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="d9433-104">Moduli di fatturazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="d9433-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d9433-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d9433-105">Overview</span></span>
<span data-ttu-id="d9433-106">Le API di fatturazione di Azure forniscono l'accesso alle informazioni di fatturazione e alle fatture di Azure.</span><span class="sxs-lookup"><span data-stu-id="d9433-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="d9433-107">Per usare questa API, l'amministratore account deve acconsentire esplicitamente tramite il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="d9433-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="d9433-108">Vedere [Gestire l'accesso alla fatturazione di Azure tramite i ruoli](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="d9433-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d9433-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="d9433-109">Install the npm module</span></span> 

<span data-ttu-id="d9433-110">Installare il modulo di npm di fatturazione di Azure</span><span class="sxs-lookup"><span data-stu-id="d9433-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="d9433-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="d9433-111">Example</span></span> 
 
<span data-ttu-id="d9433-112">Questo esempio visualizza un elenco di tutte le fatture precedenti.</span><span class="sxs-lookup"><span data-stu-id="d9433-112">This example prints a list of all of your past invoices.</span></span>
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a><span data-ttu-id="d9433-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="d9433-113">Samples</span></span>

<span data-ttu-id="d9433-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="d9433-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
