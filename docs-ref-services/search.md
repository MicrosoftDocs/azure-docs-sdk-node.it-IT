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
ms.openlocfilehash: a9c34a57d7964de1713ebf4d6c0f9c000df33042
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51366545"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="6e911-103">Moduli di Ricerca di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="6e911-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="6e911-104">Ricerca di Azure è una soluzione di ricerca distribuita come servizio cloud che delega la gestione di server e infrastruttura a Microsoft, offrendo un servizio pronto per l'uso che consente di inserire dati e di aggiungere ricerche alle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="6e911-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="6e911-105">Altre informazioni su [Ricerca di Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="6e911-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="6e911-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="6e911-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6e911-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="6e911-107">Install the npm module</span></span>

<span data-ttu-id="6e911-108">Installare il modulo npm di Ricerca di Azure</span><span class="sxs-lookup"><span data-stu-id="6e911-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="6e911-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="6e911-109">Example</span></span>

<span data-ttu-id="6e911-110">Questo esempio crea un nuovo servizio di ricerca in Azure ed elenca le risorse nel gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="6e911-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="6e911-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="6e911-111">Samples</span></span>

<span data-ttu-id="6e911-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="6e911-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
