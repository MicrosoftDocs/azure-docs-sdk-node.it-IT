---
title: Moduli di Mapping dei servizi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Mapping dei servizi di Azure per Node.js
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: db064603e32446ba2f094da2a1601520b99a7304
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="aaf2d-103">Moduli di Mapping dei servizi di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="aaf2d-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="aaf2d-104">Mapping dei servizi individua automaticamente i componenti delle applicazioni nei sistemi Windows e Linux ed esegue la mappatura della comunicazione fra i servizi.</span><span class="sxs-lookup"><span data-stu-id="aaf2d-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="aaf2d-105">Il Mapping dei servizi mostra le connessioni fra i server, i processi e le porte di tutte le architetture connesse via TCP senza il bisogno di alcuna configurazione a parte l'installazione di un agente.</span><span class="sxs-lookup"><span data-stu-id="aaf2d-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="aaf2d-106">Altre informazioni su [Mapping dei servizi di Azure](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="aaf2d-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="aaf2d-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="aaf2d-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aaf2d-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="aaf2d-108">Install the npm module</span></span>

<span data-ttu-id="aaf2d-109">Installare il modulo npm di Mapping dei servizi di Azure</span><span class="sxs-lookup"><span data-stu-id="aaf2d-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="aaf2d-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="aaf2d-110">Example</span></span>

<span data-ttu-id="aaf2d-111">Questo esempio elenca tutti i mapping dei servizi per il gruppo di risorse e l'area di lavoro specificati.</span><span class="sxs-lookup"><span data-stu-id="aaf2d-111">This example lists all service maps for the specified resource group and workspace.</span></span>

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

## <a name="samples"></a><span data-ttu-id="aaf2d-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="aaf2d-112">Samples</span></span>

<span data-ttu-id="aaf2d-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="aaf2d-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
