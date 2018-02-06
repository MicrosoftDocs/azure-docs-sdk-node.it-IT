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
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="90d98-103">Moduli di macchine virtuali di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="90d98-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="90d98-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="90d98-104">Overview</span></span>

<span data-ttu-id="90d98-105">Definire, configurare e distribuire nuovi set di scalabilità di macchine virtuali e macchine virtuali Windows e Linux dal codice con i moduli di gestione di Azure per Node.js.</span><span class="sxs-lookup"><span data-stu-id="90d98-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="90d98-106">I moduli consentono di avviare e arrestare le macchine virtuali esistenti e di collegare o scollegare i dischi nelle VM arrestate nella sottoscrizione di Azure.</span><span class="sxs-lookup"><span data-stu-id="90d98-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="90d98-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="90d98-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="90d98-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="90d98-108">Install the npm module</span></span>

<span data-ttu-id="90d98-109">Installare il modulo npm di calcolo di Azure</span><span class="sxs-lookup"><span data-stu-id="90d98-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="90d98-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="90d98-110">Example</span></span>

<span data-ttu-id="90d98-111">L'esempio seguente illustra come accedere ad Azure, creare un client di gestione ed elencare tutte le immagini di VM per la località, l'entità di pubblicazione, l'offerta e lo SKU specificati.</span><span class="sxs-lookup"><span data-stu-id="90d98-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

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

## <a name="samples"></a><span data-ttu-id="90d98-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="90d98-112">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="90d98-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="90d98-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
