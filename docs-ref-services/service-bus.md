---
title: Moduli del bus di servizio di Azure per Node.js
description: Informazioni di riferimento sui moduli del bus di servizio di Azure per Node.js
keywords: Azure, SDK, API, bus di servizio, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="338d3-104">Moduli del bus di servizio di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="338d3-104">Azure Service Bus Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="338d3-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="338d3-105">Overview</span></span>

<span data-ttu-id="338d3-106">Il bus di servizio di Azure è una piattaforma cloud di messaggistica asincrona che consente di scambiare dati tra sistemi disaccoppiati.</span><span class="sxs-lookup"><span data-stu-id="338d3-106">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="338d3-107">Altre informazioni sul [bus di servizio di Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="338d3-107">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="338d3-108">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="338d3-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="338d3-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="338d3-109">Install the npm module</span></span>

<span data-ttu-id="338d3-110">Usare npm per installare il modulo del bus di servizio di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="338d3-110">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="338d3-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="338d3-111">Example</span></span>

<span data-ttu-id="338d3-112">Questo esempio crea un client e quindi elenca tutti gli spazi dei nomi del bus di servizio associati a una determinata sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="338d3-112">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a><span data-ttu-id="338d3-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="338d3-113">Samples</span></span>

<span data-ttu-id="338d3-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="338d3-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
