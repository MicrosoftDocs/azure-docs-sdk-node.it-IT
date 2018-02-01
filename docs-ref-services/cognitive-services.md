---
title: Moduli di Servizi cognitivi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Servizi cognitivi di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="9df6c-103">Moduli di Servizi cognitivi di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="9df6c-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="9df6c-104">Servizi cognitivi di Azure sono costituiti da un set di API, SDK e servizi che aiutano gli sviluppatori a rendere le applicazioni più intelligenti, coinvolgenti e individuabili.</span><span class="sxs-lookup"><span data-stu-id="9df6c-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="9df6c-105">Servizi cognitivi Microsoft si basa sul portafoglio in evoluzione di Microsoft di API di Machine Learning e consente agli sviluppatori di aggiungere facilmente funzionalità intelligenti, ad esempio il rilevamento di emozioni e video, il riconoscimento facciale, vocale e visivo, nelle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="9df6c-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="9df6c-106">Gli obiettivi sono un'esperienza di elaborazione più personale e una maggiore produttività supportate da sistemi che sempre più riescono a vedere, sentire, parlare, comprendere e persino iniziare a ragionare.</span><span class="sxs-lookup"><span data-stu-id="9df6c-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="9df6c-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="9df6c-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9df6c-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="9df6c-108">Install the npm module</span></span>

<span data-ttu-id="9df6c-109">Installare il modulo npm di Servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="9df6c-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="9df6c-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="9df6c-110">Example</span></span>

<span data-ttu-id="9df6c-111">Questo esempio elenca tutti gli account di Servizi cognitivi.</span><span class="sxs-lookup"><span data-stu-id="9df6c-111">This example lists all cognitive service accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a><span data-ttu-id="9df6c-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="9df6c-112">Samples</span></span>

<span data-ttu-id="9df6c-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="9df6c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
