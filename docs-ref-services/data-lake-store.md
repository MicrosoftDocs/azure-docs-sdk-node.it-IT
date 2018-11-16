---
title: Moduli di Azure Data Lake Store per Node.js
description: Informazioni di riferimento sui moduli di Azure Data Lake Store per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51453385"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="eadce-103">Moduli di Azure Data Lake Store per Node.js</span><span class="sxs-lookup"><span data-stu-id="eadce-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="eadce-104">Azure Data Lake Store è un repository su vasta scala a livello aziendale per carichi di lavoro di analisi di Big Data.</span><span class="sxs-lookup"><span data-stu-id="eadce-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="eadce-105">Azure Data Lake consente di acquisire dati di qualsiasi dimensione, tipo e velocità di inserimento in un'unica posizione per le analisi esplorative e operative.</span><span class="sxs-lookup"><span data-stu-id="eadce-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="eadce-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="eadce-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="eadce-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="eadce-107">Install the npm module</span></span>

<span data-ttu-id="eadce-108">Usare npm per installare i moduli di Azure Data Lake Store per Node.js</span><span class="sxs-lookup"><span data-stu-id="eadce-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="eadce-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="eadce-109">Example</span></span>

<span data-ttu-id="eadce-110">Questo esempio elenca tutti gli account Data Lake Store in una determinata sottoscrizione di Azure</span><span class="sxs-lookup"><span data-stu-id="eadce-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="eadce-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="eadce-111">Samples</span></span>

<span data-ttu-id="eadce-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="eadce-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
