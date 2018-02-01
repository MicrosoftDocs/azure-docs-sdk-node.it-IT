---
title: Moduli di Azure Operational Insights per Node.js
description: Informazioni di riferimento sui moduli di Azure Operational Insights per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 7baa7f2f976cec9d9592231f193eede87a122532
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="7b428-103">Moduli di Azure Operational Insights per Node.js</span><span class="sxs-lookup"><span data-stu-id="7b428-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="7b428-104">Usare npm per installare il modulo di Azure Operational Insights per Node.js</span><span class="sxs-lookup"><span data-stu-id="7b428-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="7b428-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="7b428-105">Example</span></span> 

<span data-ttu-id="7b428-106">Questo esempio crea un client, si connette a Operational Insights e recupera un elenco di aree di lavoro in base a gruppo di risorse specificato.</span><span class="sxs-lookup"><span data-stu-id="7b428-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="7b428-107">Esempi</span><span class="sxs-lookup"><span data-stu-id="7b428-107">Samples</span></span>

<span data-ttu-id="7b428-108">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="7b428-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
