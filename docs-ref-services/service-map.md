---
title: Moduli di Mapping dei servizi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Mapping dei servizi di Azure per Node.js
keywords: Azure, SDK, API, Mapping dei servizi, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="1a389-104">Moduli di Mapping dei servizi di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="1a389-104">Azure Service Map modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1a389-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="1a389-105">Overview</span></span>

<span data-ttu-id="1a389-106">Mapping dei servizi individua automaticamente i componenti delle applicazioni nei sistemi Windows e Linux ed esegue la mappatura della comunicazione fra i servizi.</span><span class="sxs-lookup"><span data-stu-id="1a389-106">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="1a389-107">Il Mapping dei servizi mostra le connessioni fra i server, i processi e le porte di tutte le architetture connesse via TCP senza il bisogno di alcuna configurazione a parte l'installazione di un agente.</span><span class="sxs-lookup"><span data-stu-id="1a389-107">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="1a389-108">Altre informazioni su [Mapping dei servizi di Azure](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="1a389-108">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="1a389-109">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="1a389-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1a389-110">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="1a389-110">Install the npm module</span></span>

<span data-ttu-id="1a389-111">Installare il modulo npm di Mapping dei servizi di Azure</span><span class="sxs-lookup"><span data-stu-id="1a389-111">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="1a389-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="1a389-112">Example</span></span>

<span data-ttu-id="1a389-113">Questo esempio elenca tutti i mapping dei servizi per il gruppo di risorse e l'area di lavoro specificati.</span><span class="sxs-lookup"><span data-stu-id="1a389-113">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="1a389-114">Esempi</span><span class="sxs-lookup"><span data-stu-id="1a389-114">Samples</span></span>

<span data-ttu-id="1a389-115">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="1a389-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
