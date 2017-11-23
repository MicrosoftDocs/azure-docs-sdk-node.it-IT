---
title: Moduli di Azure Advisor per Node.js
description: Informazioni di riferimento sui moduli di Azure Advisor per Node.js
keywords: Azure, SDK, API, Advisor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="4078b-104">Moduli di Azure Advisor per Node.js</span><span class="sxs-lookup"><span data-stu-id="4078b-104">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4078b-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="4078b-105">Overview</span></span>

<span data-ttu-id="4078b-106">Azure Advisor è un consulente cloud personalizzato che illustra come seguire le procedure consigliate per ottimizzare le distribuzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="4078b-106">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="4078b-107">Advisor analizza i dati di telemetria dell'uso e della configurazione delle risorse e consiglia soluzioni che consentono di migliorare l'efficienza dei costi, le prestazioni, la disponibilità elevata e la sicurezza delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="4078b-107">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="4078b-108">Con Advisor, è possibile:</span><span class="sxs-lookup"><span data-stu-id="4078b-108">With Advisor, you can:</span></span>
- <span data-ttu-id="4078b-109">Ottenere consigli personalizzati, attuabili e proattivi sulle procedure consigliate.</span><span class="sxs-lookup"><span data-stu-id="4078b-109">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="4078b-110">Migliorare le prestazioni, la sicurezza e la disponibilità elevata delle risorse, cercando le opportunità per ridurre la spesa complessiva di Azure.</span><span class="sxs-lookup"><span data-stu-id="4078b-110">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="4078b-111">Ricevere consigli con azioni proposte incorporate.</span><span class="sxs-lookup"><span data-stu-id="4078b-111">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="4078b-112">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="4078b-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4078b-113">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="4078b-113">Install the npm module</span></span>

<span data-ttu-id="4078b-114">Installare il modulo npm di Azure Advisor</span><span class="sxs-lookup"><span data-stu-id="4078b-114">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="4078b-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="4078b-115">Example</span></span>

<span data-ttu-id="4078b-116">Questo esempio visualizza l'elenco di raccomandazioni di Azure Advisor.</span><span class="sxs-lookup"><span data-stu-id="4078b-116">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="4078b-117">Esempi</span><span class="sxs-lookup"><span data-stu-id="4078b-117">Samples</span></span>

<span data-ttu-id="4078b-118">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="4078b-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
