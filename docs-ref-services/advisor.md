---
title: Moduli di Azure Advisor per Node.js
description: Informazioni di riferimento sui moduli di Azure Advisor per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: aad3b292c6304159f68a81270e671cd335c972ec
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="17f5b-103">Moduli di Azure Advisor per Node.js</span><span class="sxs-lookup"><span data-stu-id="17f5b-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="17f5b-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="17f5b-104">Overview</span></span>

<span data-ttu-id="17f5b-105">Azure Advisor è un consulente cloud personalizzato che illustra come seguire le procedure consigliate per ottimizzare le distribuzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="17f5b-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="17f5b-106">Advisor analizza i dati di telemetria dell'uso e della configurazione delle risorse e consiglia soluzioni che consentono di migliorare l'efficienza dei costi, le prestazioni, la disponibilità elevata e la sicurezza delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="17f5b-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="17f5b-107">Con Advisor, è possibile:</span><span class="sxs-lookup"><span data-stu-id="17f5b-107">With Advisor, you can:</span></span>
- <span data-ttu-id="17f5b-108">Ottenere consigli personalizzati, attuabili e proattivi sulle procedure consigliate.</span><span class="sxs-lookup"><span data-stu-id="17f5b-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="17f5b-109">Migliorare le prestazioni, la sicurezza e la disponibilità elevata delle risorse, cercando le opportunità per ridurre la spesa complessiva di Azure.</span><span class="sxs-lookup"><span data-stu-id="17f5b-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="17f5b-110">Ricevere consigli con azioni proposte incorporate.</span><span class="sxs-lookup"><span data-stu-id="17f5b-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="17f5b-111">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="17f5b-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="17f5b-112">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="17f5b-112">Install the npm module</span></span>

<span data-ttu-id="17f5b-113">Installare il modulo npm di Azure Advisor</span><span class="sxs-lookup"><span data-stu-id="17f5b-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="17f5b-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="17f5b-114">Example</span></span>

<span data-ttu-id="17f5b-115">Questo esempio visualizza l'elenco di raccomandazioni di Azure Advisor.</span><span class="sxs-lookup"><span data-stu-id="17f5b-115">This example displays the list of recommendations from Azure Advisor.</span></span>

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

## <a name="samples"></a><span data-ttu-id="17f5b-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="17f5b-116">Samples</span></span>

<span data-ttu-id="17f5b-117">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="17f5b-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
