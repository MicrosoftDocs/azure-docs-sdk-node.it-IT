---
title: Moduli del bus di servizio di Azure per Node.js
description: Informazioni di riferimento sui moduli del bus di servizio di Azure per Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51380351"
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="b6833-103">Moduli del bus di servizio di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="b6833-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="b6833-104">Il bus di servizio di Azure è una piattaforma cloud di messaggistica asincrona che consente di scambiare dati tra sistemi disaccoppiati.</span><span class="sxs-lookup"><span data-stu-id="b6833-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="b6833-105">Altre informazioni sul [bus di servizio di Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="b6833-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="b6833-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="b6833-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b6833-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="b6833-107">Install the npm module</span></span>

<span data-ttu-id="b6833-108">Usare npm per installare il modulo del bus di servizio di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="b6833-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="b6833-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="b6833-109">Example</span></span>

<span data-ttu-id="b6833-110">Questo esempio crea un client e quindi elenca tutti gli spazi dei nomi del bus di servizio associati a una determinata sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="b6833-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b6833-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="b6833-111">Samples</span></span>

<span data-ttu-id="b6833-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="b6833-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
