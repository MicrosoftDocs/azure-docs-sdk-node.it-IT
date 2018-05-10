---
title: Moduli di macchine virtuali di Azure per Node.js - Azure
description: Guida di riferimento sui moduli di macchine virtuali di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 5ba40cb4c068b1af62aa8c654cbf2c3f66f83ff1
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="a6db2-103">Moduli di macchine virtuali di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="a6db2-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a6db2-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="a6db2-104">Overview</span></span>

<span data-ttu-id="a6db2-105">Definire, configurare e distribuire nuovi set di scalabilità di macchine virtuali e macchine virtuali Windows e Linux dal codice con i moduli di gestione di Azure per Node.js.</span><span class="sxs-lookup"><span data-stu-id="a6db2-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="a6db2-106">I moduli consentono di avviare e arrestare le macchine virtuali esistenti e di collegare o scollegare i dischi nelle VM arrestate nella sottoscrizione di Azure.</span><span class="sxs-lookup"><span data-stu-id="a6db2-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="a6db2-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="a6db2-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a6db2-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="a6db2-108">Install the npm module</span></span>

<span data-ttu-id="a6db2-109">Installare il modulo npm di calcolo di Azure</span><span class="sxs-lookup"><span data-stu-id="a6db2-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="a6db2-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="a6db2-110">Example</span></span>

<span data-ttu-id="a6db2-111">L'esempio seguente illustra come accedere ad Azure, creare un client di gestione ed elencare tutte le immagini di VM per la località, l'entità di pubblicazione, l'offerta e lo SKU specificati.</span><span class="sxs-lookup"><span data-stu-id="a6db2-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="a6db2-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="a6db2-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="a6db2-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="a6db2-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
