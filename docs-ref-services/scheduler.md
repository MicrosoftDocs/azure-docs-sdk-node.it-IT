---
title: "Moduli di Utilità di pianificazione di Azure per Node.js"
description: "Informazioni di riferimento sui moduli di Utilità di pianificazione di Azure per Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 539337abd2fff3830cb022a49aff374e877a08ee
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="90e57-103">Moduli di Utilità di pianificazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="90e57-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="90e57-104">Utilità di pianificazione di Azure crea, gestisce e richiama il lavoro pianificato tramite HTTP, HTTPS, una coda di archiviazione o il [bus di servizio di Azure](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="90e57-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="90e57-105">Altre informazioni su [Utilità di pianificazione di Azure](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="90e57-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="90e57-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="90e57-106">Management package</span></span>

<span data-ttu-id="90e57-107">Creare, gestire e richiamare il lavoro pianificato in diversi canali di comunicazione con l'API di gestione.</span><span class="sxs-lookup"><span data-stu-id="90e57-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="90e57-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="90e57-108">Install the npm module</span></span>

<span data-ttu-id="90e57-109">Installare il modulo npm di Utilità di pianificazione di Azure</span><span class="sxs-lookup"><span data-stu-id="90e57-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="90e57-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="90e57-110">Example</span></span>

<span data-ttu-id="90e57-111">Questo esempio elenca le utilità di pianificazione correnti.</span><span class="sxs-lookup"><span data-stu-id="90e57-111">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="90e57-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="90e57-112">Samples</span></span>

<span data-ttu-id="90e57-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="90e57-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
