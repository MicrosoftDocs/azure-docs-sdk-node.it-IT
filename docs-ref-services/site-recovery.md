---
title: Moduli di Azure Site Recovery per Node.js
description: Informazioni di riferimento sui moduli di Azure Site Recovery per Node.js
keywords: Azure, SDK, API, Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="c015a-104">Moduli di Azure Site Recovery per Node.js</span><span class="sxs-lookup"><span data-stu-id="c015a-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c015a-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="c015a-105">Overview</span></span>

<span data-ttu-id="c015a-106">Site Recovery consente di automatizzare la replica delle VM di Azure tra aree, macchine virtuali locali e server fisici in Azure e tra computer locali in un data center secondario.</span><span class="sxs-lookup"><span data-stu-id="c015a-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="c015a-107">Altre informazioni su [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="c015a-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="c015a-108">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="c015a-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c015a-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="c015a-109">Install the npm module</span></span>

<span data-ttu-id="c015a-110">Installare il modulo npm del servizio Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="c015a-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="c015a-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="c015a-111">Example</span></span>

<span data-ttu-id="c015a-112">Questo esempio elenca il servizio Site Recovery per un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="c015a-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="c015a-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="c015a-113">Samples</span></span>

<span data-ttu-id="c015a-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="c015a-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
