---
title: Moduli di Servizi multimediali di Azure per Node.js
description: Informazioni di riferimento sui moduli di Servizi multimediali di Azure per Node.js
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: bfd4402c215a81c9ed8753cfe9ad9dbfaa52bd6f
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51374985"
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="b43a1-103">Moduli di Servizi multimediali di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="b43a1-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="b43a1-104">Servizi multimediali di Azure costituisce una piattaforma estensibile basata sul cloud che consente agli sviluppatori di creare applicazioni di distribuzione e gestione di contenuti multimediali altamente scalabili.</span><span class="sxs-lookup"><span data-stu-id="b43a1-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="b43a1-105">Servizi multimediali si basa su API REST che consentono di caricare, archiviare e codificare contenuti video o audio in modo sicuro, nonché creare pacchetti di tali contenuti per la distribuzione in streaming live e on demand a vari client (ad esempio, TV, PC e dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="b43a1-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="b43a1-106">Con Servizi multimediali di Azure è possibile:</span><span class="sxs-lookup"><span data-stu-id="b43a1-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="b43a1-107">Creare flussi di lavoro end-to-end usando unicamente Servizi multimediali.</span><span class="sxs-lookup"><span data-stu-id="b43a1-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="b43a1-108">Usare componenti di terze parti per alcune parti del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="b43a1-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="b43a1-109">ad esempio, la codifica con un codificatore di terze parti.</span><span class="sxs-lookup"><span data-stu-id="b43a1-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="b43a1-110">Inoltre, sono possibili operazioni di caricamento, protezione, creazione di pacchetti e invio tramite Servizi multimediali.</span><span class="sxs-lookup"><span data-stu-id="b43a1-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="b43a1-111">Eseguire lo streaming dei contenuti live o on demand.</span><span class="sxs-lookup"><span data-stu-id="b43a1-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="b43a1-112">L'argomento contiene inoltre collegamenti ad altri argomenti rilevanti.</span><span class="sxs-lookup"><span data-stu-id="b43a1-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="b43a1-113">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="b43a1-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b43a1-114">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="b43a1-114">Install the npm module</span></span>

<span data-ttu-id="b43a1-115">Installare il modulo npm di Servizi multimediali di Azure</span><span class="sxs-lookup"><span data-stu-id="b43a1-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="b43a1-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="b43a1-116">Example</span></span>

<span data-ttu-id="b43a1-117">Questo esempio elenca tutti i servizi multimediali per un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="b43a1-117">This example lists all media services for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b43a1-118">Esempi</span><span class="sxs-lookup"><span data-stu-id="b43a1-118">Samples</span></span>

<span data-ttu-id="b43a1-119">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="b43a1-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
