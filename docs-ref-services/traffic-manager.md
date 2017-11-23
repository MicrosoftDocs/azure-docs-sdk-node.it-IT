---
title: Moduli di Gestione traffico di Azure per Node.js
description: Informazioni di riferimento sui moduli di Gestione traffico di Azure per Node.js
keywords: Azure, SDK, API, Gestione traffico, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="3f768-104">Moduli di Gestione traffico di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="3f768-104">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3f768-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="3f768-105">Overview</span></span>

<span data-ttu-id="3f768-106">Gestione traffico di Microsoft Azure consente di controllare la distribuzione del traffico utente per gli endpoint di servizio in diversi data center.</span><span class="sxs-lookup"><span data-stu-id="3f768-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="3f768-107">Gli endpoint di servizio supportati da Gestione traffico includono servizi cloud, app Web e macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="3f768-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="3f768-108">È anche possibile usare Gestione traffico con endpoint esterni, non di Azure.</span><span class="sxs-lookup"><span data-stu-id="3f768-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="3f768-109">Altre informazioni su [Gestione traffico di Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="3f768-109">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="3f768-110">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="3f768-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3f768-111">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="3f768-111">Install the npm module</span></span>

<span data-ttu-id="3f768-112">Installare il modulo npm di Gestione Traffico di Azure</span><span class="sxs-lookup"><span data-stu-id="3f768-112">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="3f768-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="3f768-113">Example</span></span>

<span data-ttu-id="3f768-114">Questo esempio elenca tutte le istanze di Gestione traffico per un determinato gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="3f768-114">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="3f768-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="3f768-115">Samples</span></span>

<span data-ttu-id="3f768-116">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="3f768-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
