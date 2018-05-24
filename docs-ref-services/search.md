---
title: Moduli di Ricerca di Azure per Node.js
description: Informazioni di riferimento sui moduli di Ricerca di Azure per Node.js
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: 895281acd2359240f3d483e4205c628e1f85f724
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="00294-103">Moduli di Ricerca di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="00294-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="00294-104">Ricerca di Azure è una soluzione di ricerca distribuita come servizio cloud che delega la gestione di server e infrastruttura a Microsoft, offrendo un servizio pronto per l'uso che consente di inserire dati e di aggiungere ricerche alle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="00294-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="00294-105">Altre informazioni su [Ricerca di Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="00294-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="00294-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="00294-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="00294-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="00294-107">Install the npm module</span></span>

<span data-ttu-id="00294-108">Installare il modulo npm di Ricerca di Azure</span><span class="sxs-lookup"><span data-stu-id="00294-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="00294-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="00294-109">Example</span></span>

<span data-ttu-id="00294-110">Questo esempio crea un nuovo servizio di ricerca in Azure ed elenca le risorse nel gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="00294-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="00294-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="00294-111">Samples</span></span>

<span data-ttu-id="00294-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="00294-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
