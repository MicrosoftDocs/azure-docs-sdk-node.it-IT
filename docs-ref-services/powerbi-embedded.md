---
title: Moduli di Azure Power BI Embedded per Node.js
description: Informazioni di riferimento sui moduli di Azure Power BI Embedded per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 5dbe134acb38787916f48277b2114e199601e128
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="674d8-103">Moduli di Azure Power BI Embedded per Node.js</span><span class="sxs-lookup"><span data-stu-id="674d8-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="674d8-104">Con il servizio Azure Power BI Embedded, è possibile integrare i report di Power BI direttamente nell'applicazione Node per creare o modificare grafici e report.</span><span class="sxs-lookup"><span data-stu-id="674d8-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="674d8-105">Altre informazioni su [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="674d8-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="674d8-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="674d8-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="674d8-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="674d8-107">Install the npm module</span></span>

<span data-ttu-id="674d8-108">Installare il modulo npm di Azure Power BI</span><span class="sxs-lookup"><span data-stu-id="674d8-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="674d8-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="674d8-109">Example</span></span>

<span data-ttu-id="674d8-110">Questo esempio crea una raccolta di aree di lavoro in un gruppo di risorse esistente.</span><span class="sxs-lookup"><span data-stu-id="674d8-110">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="674d8-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="674d8-111">Samples</span></span>

<span data-ttu-id="674d8-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="674d8-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
