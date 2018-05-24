---
title: Moduli di Azure DNS per Node.js
description: Informazioni di riferimento sui moduli di Azure DNS per Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="0a4d4-103">Moduli di Azure DNS per Node.js</span><span class="sxs-lookup"><span data-stu-id="0a4d4-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="0a4d4-104">Usare Azure DNS per ospitare i domini DNS (Domain Name System) in Azure.</span><span class="sxs-lookup"><span data-stu-id="0a4d4-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="0a4d4-105">Gestire i record DNS con le stesse credenziali, le stesse modalità di fatturazione e lo stesso contratto di supporto tecnico degli altri servizi di Azure.</span><span class="sxs-lookup"><span data-stu-id="0a4d4-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="0a4d4-106">Integrare agevolmente i servizi basati su Azure con gli aggiornamenti DNS corrispondenti, semplificando il processo di distribuzione end-to-end.</span><span class="sxs-lookup"><span data-stu-id="0a4d4-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="0a4d4-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="0a4d4-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0a4d4-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="0a4d4-108">Install the npm module</span></span>

<span data-ttu-id="0a4d4-109">Installare il modulo npm di Azure DNS</span><span class="sxs-lookup"><span data-stu-id="0a4d4-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="0a4d4-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a4d4-110">Example</span></span>

<span data-ttu-id="0a4d4-111">Questo esempio elenca le zone di gestione DNS.</span><span class="sxs-lookup"><span data-stu-id="0a4d4-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0a4d4-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="0a4d4-112">Samples</span></span>

<span data-ttu-id="0a4d4-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="0a4d4-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
