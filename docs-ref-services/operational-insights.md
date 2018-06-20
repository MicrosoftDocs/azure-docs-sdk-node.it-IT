---
title: Moduli di Azure Operational Insights per Node.js
description: Informazioni di riferimento sui moduli di Azure Operational Insights per Node.js
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 2cd948a57925954ecddc077ead727b1a7689ce0e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261970"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="b54fb-103">Moduli di Azure Operational Insights per Node.js</span><span class="sxs-lookup"><span data-stu-id="b54fb-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="b54fb-104">Usare npm per installare il modulo di Azure Operational Insights per Node.js</span><span class="sxs-lookup"><span data-stu-id="b54fb-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="b54fb-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="b54fb-105">Example</span></span> 

<span data-ttu-id="b54fb-106">Questo esempio crea un client, si connette a Operational Insights e recupera un elenco di aree di lavoro in base a gruppo di risorse specificato.</span><span class="sxs-lookup"><span data-stu-id="b54fb-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b54fb-107">Esempi</span><span class="sxs-lookup"><span data-stu-id="b54fb-107">Samples</span></span>

<span data-ttu-id="b54fb-108">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="b54fb-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
