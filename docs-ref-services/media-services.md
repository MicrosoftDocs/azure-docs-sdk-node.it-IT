---
title: Moduli di Servizi multimediali di Azure per Node.js
description: Informazioni di riferimento sui moduli di Servizi multimediali di Azure per Node.js
keywords: Azure, SDK, API, Servizi multimediali, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="9057d-104">Moduli di Servizi multimediali di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="9057d-104">Azure Media Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9057d-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="9057d-105">Overview</span></span>

<span data-ttu-id="9057d-106">Servizi multimediali di Azure costituisce una piattaforma estensibile basata sul cloud che consente agli sviluppatori di creare applicazioni di distribuzione e gestione di contenuti multimediali altamente scalabili.</span><span class="sxs-lookup"><span data-stu-id="9057d-106">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="9057d-107">Servizi multimediali si basa su API REST che consentono di caricare, archiviare e codificare contenuti video o audio in modo sicuro, nonché creare pacchetti di tali contenuti per la distribuzione in streaming live e on demand a vari client (ad esempio, TV, PC e dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="9057d-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="9057d-108">Con Servizi multimediali di Azure è possibile:</span><span class="sxs-lookup"><span data-stu-id="9057d-108">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="9057d-109">Creare flussi di lavoro end-to-end usando unicamente Servizi multimediali.</span><span class="sxs-lookup"><span data-stu-id="9057d-109">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="9057d-110">Usare componenti di terze parti per alcune parti del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="9057d-110">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="9057d-111">ad esempio, la codifica con un codificatore di terze parti.</span><span class="sxs-lookup"><span data-stu-id="9057d-111">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="9057d-112">Inoltre, sono possibili operazioni di caricamento, protezione, creazione di pacchetti e invio tramite Servizi multimediali.</span><span class="sxs-lookup"><span data-stu-id="9057d-112">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="9057d-113">Eseguire lo streaming dei contenuti live o on demand.</span><span class="sxs-lookup"><span data-stu-id="9057d-113">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="9057d-114">L'argomento contiene inoltre collegamenti ad altri argomenti rilevanti.</span><span class="sxs-lookup"><span data-stu-id="9057d-114">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="9057d-115">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="9057d-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9057d-116">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="9057d-116">Install the npm module</span></span>

<span data-ttu-id="9057d-117">Installare il modulo npm di Servizi multimediali di Azure</span><span class="sxs-lookup"><span data-stu-id="9057d-117">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="9057d-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="9057d-118">Example</span></span>

<span data-ttu-id="9057d-119">Questo esempio elenca tutti i servizi multimediali per un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="9057d-119">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="9057d-120">Esempi</span><span class="sxs-lookup"><span data-stu-id="9057d-120">Samples</span></span>

<span data-ttu-id="9057d-121">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="9057d-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
