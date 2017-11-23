---
title: Moduli di Azure Operational Insights per Node.js
description: Informazioni di riferimento sui moduli di Azure Operational Insights per Node.js
keywords: Azure, SDK, API, Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="b642b-104">Moduli di Azure Operational Insights per Node.js</span><span class="sxs-lookup"><span data-stu-id="b642b-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b642b-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="b642b-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="b642b-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="b642b-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b642b-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="b642b-107">Install the npm module</span></span>

<span data-ttu-id="b642b-108">Usare npm per installare il modulo di Azure Operational Insights per Node.js</span><span class="sxs-lookup"><span data-stu-id="b642b-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="b642b-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="b642b-109">Example</span></span> 

<span data-ttu-id="b642b-110">Questo esempio crea un client, si connette a Operational Insights e recupera un elenco di aree di lavoro in base a gruppo di risorse specificato.</span><span class="sxs-lookup"><span data-stu-id="b642b-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b642b-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="b642b-111">Samples</span></span>

<span data-ttu-id="b642b-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="b642b-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
