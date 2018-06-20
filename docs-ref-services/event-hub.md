---
title: Moduli di Hub eventi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Hub eventi di Azure per Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: ff167e911b68b82b880e792e7ff2649cbe5af342
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260384"
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="dcb82-103">Moduli di Hub eventi di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="dcb82-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="dcb82-104">Hub eventi di Azure è una piattaforma di streaming di dati estremamente scalabile e un servizio di inserimento degli eventi che consente di ricevere ed elaborare milioni di eventi al secondo.</span><span class="sxs-lookup"><span data-stu-id="dcb82-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="dcb82-105">Hub eventi consente di elaborare e archiviare eventi, dati o dati di telemetria generati dal software distribuito e dai dispositivi.</span><span class="sxs-lookup"><span data-stu-id="dcb82-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="dcb82-106">I dati inviati a un hub eventi possono essere trasformati e archiviati usando qualsiasi provider di analisi in tempo reale o adattatori di invio in batch/archiviazione.</span><span class="sxs-lookup"><span data-stu-id="dcb82-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="dcb82-107">Con la possibilità di fornire funzionalità di pubblicazione-sottoscrizione con una latenza bassa e su larga scala, Hub eventi funge da "rampa di ingresso" per Big Data.</span><span class="sxs-lookup"><span data-stu-id="dcb82-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="dcb82-108">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="dcb82-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="dcb82-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="dcb82-109">Install the npm module</span></span> 

<span data-ttu-id="dcb82-110">Usare npm per installare i moduli di Hub eventi di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="dcb82-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="dcb82-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="dcb82-111">Example</span></span>

<span data-ttu-id="dcb82-112">Questo esempio recupera informazioni su un hub eventi esistente.</span><span class="sxs-lookup"><span data-stu-id="dcb82-112">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="dcb82-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="dcb82-113">Samples</span></span>

<span data-ttu-id="dcb82-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="dcb82-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
