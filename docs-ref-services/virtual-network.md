---
title: Moduli di Rete virtuale di Azure per Node.js
description: Informazioni di riferimento sui moduli di Rete virtuale di Azure per Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 11341fdff5df3b7521319d841707493db1d07732
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52031585"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="84e2e-103">Moduli di Rete virtuale di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="84e2e-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="84e2e-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="84e2e-104">Overview</span></span>

<span data-ttu-id="84e2e-105">Il servizio Rete virtuale di Azure consente di connettere tra loro le risorse di Azure in modo sicuro con reti virtuali.</span><span class="sxs-lookup"><span data-stu-id="84e2e-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="84e2e-106">Una rete virtuale è una rappresentazione della propria rete nel cloud.</span><span class="sxs-lookup"><span data-stu-id="84e2e-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="84e2e-107">È un isolamento logico del cloud di Azure dedicato alla sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="84e2e-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="84e2e-108">È anche possibile connettere le reti virtuali alla rete locale.</span><span class="sxs-lookup"><span data-stu-id="84e2e-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="84e2e-109">Altre informazioni su [Rete virtuale di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="84e2e-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="84e2e-110">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="84e2e-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="84e2e-111">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="84e2e-111">Install the npm module</span></span>

<span data-ttu-id="84e2e-112">Installare il modulo npm di Rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="84e2e-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="84e2e-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="84e2e-113">Example</span></span>

<span data-ttu-id="84e2e-114">Questo esempio ottiene e visualizza l'elenco di reti virtuali</span><span class="sxs-lookup"><span data-stu-id="84e2e-114">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="84e2e-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="84e2e-115">Samples</span></span>

<span data-ttu-id="84e2e-116">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="84e2e-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
