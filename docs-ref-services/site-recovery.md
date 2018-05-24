---
title: Moduli di Azure Site Recovery per Node.js
description: Informazioni di riferimento sui moduli di Azure Site Recovery per Node.js
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 470124eb69a48486fa54be6628c028399f0c038e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="c8012-103">Moduli di Azure Site Recovery per Node.js</span><span class="sxs-lookup"><span data-stu-id="c8012-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="c8012-104">Site Recovery consente di automatizzare la replica delle VM di Azure tra aree, macchine virtuali locali e server fisici in Azure e tra computer locali in un data center secondario.</span><span class="sxs-lookup"><span data-stu-id="c8012-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="c8012-105">Altre informazioni su [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="c8012-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="c8012-106">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="c8012-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c8012-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="c8012-107">Install the npm module</span></span>

<span data-ttu-id="c8012-108">Installare il modulo npm del servizio Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="c8012-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="c8012-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="c8012-109">Example</span></span>

<span data-ttu-id="c8012-110">Questo esempio elenca il servizio Site Recovery per un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="c8012-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="c8012-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="c8012-111">Samples</span></span>

<span data-ttu-id="c8012-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="c8012-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
