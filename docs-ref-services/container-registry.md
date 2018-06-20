---
title: Moduli di Registro contenitori di Azure per Node.js
description: Informazioni di riferimento sui moduli di Registro contenitori di Azure per Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: ca83b97e94312498f4f93c587cf0c90485136841
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259940"
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="4307c-103">Moduli di Registro contenitori di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="4307c-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="4307c-104">Registro contenitori di Azure è un servizio gestito di registri Docker basato sull'applicazione open source Docker Registry 2.0.</span><span class="sxs-lookup"><span data-stu-id="4307c-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="4307c-105">Creare e gestire registri contenitori di Azure per archiviare e gestire immagini contenitore Docker private.</span><span class="sxs-lookup"><span data-stu-id="4307c-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="4307c-106">È possibile usare i registri contenitori in Azure con la pipeline di sviluppo e distribuzione di contenitori esistente e attingere alle competenze della community Docker.</span><span class="sxs-lookup"><span data-stu-id="4307c-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="4307c-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="4307c-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4307c-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="4307c-108">Install the npm module</span></span>

<span data-ttu-id="4307c-109">Installare il modulo npm di Registro contenitori di Azure</span><span class="sxs-lookup"><span data-stu-id="4307c-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="4307c-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="4307c-110">Example</span></span>

<span data-ttu-id="4307c-111">Questo esempio ottiene un elenco dei contenitori disponibili.</span><span class="sxs-lookup"><span data-stu-id="4307c-111">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4307c-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="4307c-112">Samples</span></span>

<span data-ttu-id="4307c-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="4307c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
