---
title: Moduli di Azure DevTest Labs per Node.js
description: Informazioni di riferimento sui moduli di Azure DevTest Labs per Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 4528bf6a09bc86d23bfec982988added1aa3e257
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51494735"
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="ccb9b-103">Moduli di Azure DevTest Labs per Node.js</span><span class="sxs-lookup"><span data-stu-id="ccb9b-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="ccb9b-104">Lab di sviluppo e test di Azure è un servizio che consente agli sviluppatori e ai tester di creare rapidamente ambienti in Azure riducendo al minimo gli sprechi e i costi di controllo.</span><span class="sxs-lookup"><span data-stu-id="ccb9b-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="ccb9b-105">È possibile provare la versione più recente dell'applicazione eseguendo rapidamente il provisioning di ambienti Windows e Linux tramite modelli ed elementi riutilizzabili.</span><span class="sxs-lookup"><span data-stu-id="ccb9b-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="ccb9b-106">Consente di integrare facilmente la pipeline di distribuzione in lab di sviluppo e test per effettuare il provisioning di ambienti su richiesta.</span><span class="sxs-lookup"><span data-stu-id="ccb9b-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="ccb9b-107">Aumentare i propri test di carico tramite il provisioning di più agenti di test e creare ambienti di pre-provisioning per training e demo.</span><span class="sxs-lookup"><span data-stu-id="ccb9b-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="ccb9b-108">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="ccb9b-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ccb9b-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="ccb9b-109">Install the npm module</span></span>

<span data-ttu-id="ccb9b-110">Installare il modulo npm di Azure DevTest Labs</span><span class="sxs-lookup"><span data-stu-id="ccb9b-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="ccb9b-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="ccb9b-111">Example</span></span>

<span data-ttu-id="ccb9b-112">Questo esempio ottiene e visualizza i dettagli di un lab.</span><span class="sxs-lookup"><span data-stu-id="ccb9b-112">This example gets and prints the details of a lab.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ccb9b-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="ccb9b-113">Samples</span></span>

<span data-ttu-id="ccb9b-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="ccb9b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
