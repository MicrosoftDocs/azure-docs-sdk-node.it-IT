---
title: Moduli di fatturazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di fatturazione di Azure per Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 7be64d01c1bf8d247694735b8581f72678f55983
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094471"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="b674c-103">Moduli di fatturazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="b674c-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b674c-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="b674c-104">Overview</span></span>
<span data-ttu-id="b674c-105">Le API di fatturazione di Azure forniscono l'accesso alle informazioni di fatturazione e alle fatture di Azure.</span><span class="sxs-lookup"><span data-stu-id="b674c-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="b674c-106">Per usare questa API, l'amministratore account deve acconsentire esplicitamente tramite il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="b674c-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="b674c-107">Vedere [Gestire l'accesso alla fatturazione di Azure tramite i ruoli](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="b674c-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b674c-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="b674c-108">Install the npm module</span></span> 

<span data-ttu-id="b674c-109">Installare il modulo di npm di fatturazione di Azure</span><span class="sxs-lookup"><span data-stu-id="b674c-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="b674c-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="b674c-110">Example</span></span> 
 
<span data-ttu-id="b674c-111">Questo esempio visualizza un elenco di tutte le fatture precedenti.</span><span class="sxs-lookup"><span data-stu-id="b674c-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="b674c-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="b674c-112">Samples</span></span>

<span data-ttu-id="b674c-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="b674c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
