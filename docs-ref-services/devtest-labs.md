---
title: Moduli di Azure DevTest Labs per Node.js
description: Informazioni di riferimento sui moduli di Azure DevTest Labs per Node.js
keywords: Azure, SDK, API, DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="a9716-104">Moduli di Azure DevTest Labs per Node.js</span><span class="sxs-lookup"><span data-stu-id="a9716-104">Azure DevTest Labs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a9716-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="a9716-105">Overview</span></span>

<span data-ttu-id="a9716-106">Lab di sviluppo e test di Azure è un servizio che consente agli sviluppatori e ai tester di creare rapidamente ambienti in Azure riducendo al minimo gli sprechi e i costi di controllo.</span><span class="sxs-lookup"><span data-stu-id="a9716-106">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="a9716-107">È possibile provare la versione più recente dell'applicazione eseguendo rapidamente il provisioning di ambienti Windows e Linux tramite modelli ed elementi riutilizzabili.</span><span class="sxs-lookup"><span data-stu-id="a9716-107">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="a9716-108">Consente di integrare facilmente la pipeline di distribuzione in lab di sviluppo e test per effettuare il provisioning di ambienti su richiesta.</span><span class="sxs-lookup"><span data-stu-id="a9716-108">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="a9716-109">Aumentare i propri test di carico tramite il provisioning di più agenti di test e creare ambienti di pre-provisioning per training e demo.</span><span class="sxs-lookup"><span data-stu-id="a9716-109">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="a9716-110">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="a9716-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a9716-111">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="a9716-111">Install the npm module</span></span>

<span data-ttu-id="a9716-112">Installare il modulo npm di Azure DevTest Labs</span><span class="sxs-lookup"><span data-stu-id="a9716-112">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="a9716-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="a9716-113">Example</span></span>

<span data-ttu-id="a9716-114">Questo esempio ottiene e visualizza i dettagli di un lab.</span><span class="sxs-lookup"><span data-stu-id="a9716-114">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="a9716-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="a9716-115">Samples</span></span>

<span data-ttu-id="a9716-116">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="a9716-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
