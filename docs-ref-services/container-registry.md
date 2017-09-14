---
title: Moduli di Registro contenitori di Azure per Node.js
description: Informazioni di riferimento sui moduli di Registro contenitori di Azure per Node.js
keywords: Azure, SDK, API, registro contenitori, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="476e6-104">Moduli di Registro contenitori di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="476e6-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="476e6-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="476e6-105">Overview</span></span>

<span data-ttu-id="476e6-106">Registro contenitori di Azure è un servizio gestito di registri Docker basato sull'applicazione open source Docker Registry 2.0.</span><span class="sxs-lookup"><span data-stu-id="476e6-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="476e6-107">Creare e gestire registri contenitori di Azure per archiviare e gestire immagini contenitore Docker private.</span><span class="sxs-lookup"><span data-stu-id="476e6-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="476e6-108">È possibile usare i registri contenitori in Azure con la pipeline di sviluppo e distribuzione di contenitori esistente e attingere alle competenze della community Docker.</span><span class="sxs-lookup"><span data-stu-id="476e6-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="476e6-109">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="476e6-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="476e6-110">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="476e6-110">Install the npm module</span></span>

<span data-ttu-id="476e6-111">Installare il modulo npm di Registro contenitori di Azure</span><span class="sxs-lookup"><span data-stu-id="476e6-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="476e6-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="476e6-112">Example</span></span>

<span data-ttu-id="476e6-113">Questo esempio ottiene un elenco dei contenitori disponibili.</span><span class="sxs-lookup"><span data-stu-id="476e6-113">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="476e6-114">Esempi</span><span class="sxs-lookup"><span data-stu-id="476e6-114">Samples</span></span>

<span data-ttu-id="476e6-115">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="476e6-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
