---
title: Moduli di Azure DNS per Node.js
description: Informazioni di riferimento sui moduli di Azure DNS per Node.js
keywords: Azure, SDK, API, DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="23d3b-104">Moduli di Azure DNS per Node.js</span><span class="sxs-lookup"><span data-stu-id="23d3b-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="23d3b-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="23d3b-105">Overview</span></span>

<span data-ttu-id="23d3b-106">Usare Azure DNS per ospitare i domini DNS (Domain Name System) in Azure.</span><span class="sxs-lookup"><span data-stu-id="23d3b-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="23d3b-107">Gestire i record DNS con le stesse credenziali, le stesse modalità di fatturazione e lo stesso contratto di supporto tecnico degli altri servizi di Azure.</span><span class="sxs-lookup"><span data-stu-id="23d3b-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="23d3b-108">Integrare agevolmente i servizi basati su Azure con gli aggiornamenti DNS corrispondenti, semplificando il processo di distribuzione end-to-end.</span><span class="sxs-lookup"><span data-stu-id="23d3b-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="23d3b-109">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="23d3b-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="23d3b-110">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="23d3b-110">Install the npm module</span></span>

<span data-ttu-id="23d3b-111">Installare il modulo npm di Azure DNS</span><span class="sxs-lookup"><span data-stu-id="23d3b-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="23d3b-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="23d3b-112">Example</span></span>

<span data-ttu-id="23d3b-113">Questo esempio elenca le zone di gestione DNS.</span><span class="sxs-lookup"><span data-stu-id="23d3b-113">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="23d3b-114">Esempi</span><span class="sxs-lookup"><span data-stu-id="23d3b-114">Samples</span></span>

<span data-ttu-id="23d3b-115">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="23d3b-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
