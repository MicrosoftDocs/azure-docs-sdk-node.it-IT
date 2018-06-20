---
title: Moduli di Hub di notifica di Azure per Node.js
description: Informazioni di riferimento sui moduli di Hub di notifica di Azure per Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 30b8caa07111f9ceb5fa58f92649e4670aa6bee6
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261720"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="56935-103">Moduli di Hub di notifica di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="56935-103">Azure Notification Hubs modules for Node.js</span></span>

<span data-ttu-id="56935-104">Hub di notifica di Azure offre un motore di push di facile uso, multipiattaforma e con scalabilità orizzontale.</span><span class="sxs-lookup"><span data-stu-id="56935-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="56935-105">Con una sola chiamata all'API multipiattaforma, è possibile inviare facilmente notifiche push mirate e personalizzate a qualsiasi piattaforma mobile da qualsiasi cloud o back-end locale.</span><span class="sxs-lookup"><span data-stu-id="56935-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="56935-106">Hub di notifica funziona perfettamente per scenari aziendali e di consumo.</span><span class="sxs-lookup"><span data-stu-id="56935-106">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="56935-107">Di seguito sono riportati alcuni esempi degli usi di Hub di notifica fatti dai clienti:</span><span class="sxs-lookup"><span data-stu-id="56935-107">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="56935-108">Invio di notifiche sulle ultime notizie a milioni di utenti con bassa latenza.</span><span class="sxs-lookup"><span data-stu-id="56935-108">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="56935-109">Invio di coupon in base alla posizione a segmenti di utenti interessati.</span><span class="sxs-lookup"><span data-stu-id="56935-109">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="56935-110">Invio di notifiche sugli eventi a utenti o gruppi per applicazioni di media, sport, finanza e gioco.</span><span class="sxs-lookup"><span data-stu-id="56935-110">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="56935-111">Contenuti push promozionali per le app per coinvolgere e offrire prodotti ai clienti.</span><span class="sxs-lookup"><span data-stu-id="56935-111">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="56935-112">Notifiche agli utenti su eventi aziendali, come nuovi messaggi ed elementi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="56935-112">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="56935-113">Invio di codici per l'autenticazione a più fattori.</span><span class="sxs-lookup"><span data-stu-id="56935-113">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="56935-114">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="56935-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="56935-115">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="56935-115">Install the npm module</span></span>

<span data-ttu-id="56935-116">Installare il modulo Hub di notifica di Azure</span><span class="sxs-lookup"><span data-stu-id="56935-116">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="56935-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="56935-117">Example</span></span>

<span data-ttu-id="56935-118">Questo esempio elenca tutti gli hub di notifica.</span><span class="sxs-lookup"><span data-stu-id="56935-118">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="56935-119">Esempi</span><span class="sxs-lookup"><span data-stu-id="56935-119">Samples</span></span>

* <span data-ttu-id="56935-120">[App Service Mobile completed quickstart for Node.js backend](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/) (Guida introduttiva per dispositivi mobili del servizio app per back-end Node.js completata)</span><span class="sxs-lookup"><span data-stu-id="56935-120">[App Service Mobile completed quickstart for Node.js backend](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)</span></span>
* <span data-ttu-id="56935-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalie nella vibrazione dei tweet rilevate dai servizi IoT di Azure nei dati di Intel Edison che esegue Node.js)</span><span class="sxs-lookup"><span data-stu-id="56935-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span>

<span data-ttu-id="56935-122">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="56935-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
