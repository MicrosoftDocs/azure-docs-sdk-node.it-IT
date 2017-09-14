---
title: Moduli della rete CDN di Azure per Node.js
description: Informazioni di riferimento sui moduli della rete CDN di Azure per Node.js
keywords: Azure, SDK, API, rete CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="869b0-104">Moduli della rete CDN di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="869b0-104">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="869b0-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="869b0-105">Overview</span></span>

<span data-ttu-id="869b0-106">La rete per la distribuzione di contenuti di Azure (rete CDN) offre agli sviluppatori una soluzione globale per distribuire contenuti a larghezza di banda elevata ospitati in Azure o in altre posizioni.</span><span class="sxs-lookup"><span data-stu-id="869b0-106">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="869b0-107">Con la rete CDN è possibile memorizzare nella cache gli oggetti disponibili pubblicamente caricati dall'archivio BLOB di Azure un'applicazione Web, una macchina virtuale, una cartella dell'applicazione o altre posizioni HTTP/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="869b0-107">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="869b0-108">La cache della rete CDN può essere mantenuta in posizioni strategiche per fornire la larghezza di banda massima per la distribuzione di contenuto agli utenti.</span><span class="sxs-lookup"><span data-stu-id="869b0-108">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="869b0-109">In genere, la rete CDN viene usata per recapitare contenuto statico come immagini, fogli di stile, documenti, file script sul lato client e pagine HTML.</span><span class="sxs-lookup"><span data-stu-id="869b0-109">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="869b0-110">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="869b0-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="869b0-111">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="869b0-111">Install the npm module</span></span>

<span data-ttu-id="869b0-112">Installare il modulo npm della rete CDN</span><span class="sxs-lookup"><span data-stu-id="869b0-112">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="869b0-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="869b0-113">Example</span></span>

<span data-ttu-id="869b0-114">Questo esempio elenca tutti i profili della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="869b0-114">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="869b0-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="869b0-115">Samples</span></span>

<span data-ttu-id="869b0-116">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="869b0-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
