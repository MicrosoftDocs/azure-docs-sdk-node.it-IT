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
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51494865"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="a3cb7-103">Moduli di Azure DNS per Node.js</span><span class="sxs-lookup"><span data-stu-id="a3cb7-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="a3cb7-104">Usare Azure DNS per ospitare i domini DNS (Domain Name System) in Azure.</span><span class="sxs-lookup"><span data-stu-id="a3cb7-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="a3cb7-105">Gestire i record DNS con le stesse credenziali, le stesse modalità di fatturazione e lo stesso contratto di supporto tecnico degli altri servizi di Azure.</span><span class="sxs-lookup"><span data-stu-id="a3cb7-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="a3cb7-106">Integrare agevolmente i servizi basati su Azure con gli aggiornamenti DNS corrispondenti, semplificando il processo di distribuzione end-to-end.</span><span class="sxs-lookup"><span data-stu-id="a3cb7-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="a3cb7-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="a3cb7-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a3cb7-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="a3cb7-108">Install the npm module</span></span>

<span data-ttu-id="a3cb7-109">Installare il modulo npm di Azure DNS</span><span class="sxs-lookup"><span data-stu-id="a3cb7-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="a3cb7-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="a3cb7-110">Example</span></span>

<span data-ttu-id="a3cb7-111">Questo esempio elenca le zone di gestione DNS.</span><span class="sxs-lookup"><span data-stu-id="a3cb7-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a3cb7-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="a3cb7-112">Samples</span></span>

<span data-ttu-id="a3cb7-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="a3cb7-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
