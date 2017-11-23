---
title: Moduli di Rete virtuale di Azure per Node.js
description: Informazioni di riferimento sui moduli di Rete virtuale di Azure per Node.js
keywords: Azure, SDK, API, rete virtuale, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="9daca-104">Moduli di Rete virtuale di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="9daca-104">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9daca-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="9daca-105">Overview</span></span>

<span data-ttu-id="9daca-106">Il servizio Rete virtuale di Azure consente di connettere tra loro le risorse di Azure in modo sicuro con reti virtuali.</span><span class="sxs-lookup"><span data-stu-id="9daca-106">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="9daca-107">Una rete virtuale è una rappresentazione della propria rete nel cloud.</span><span class="sxs-lookup"><span data-stu-id="9daca-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="9daca-108">È un isolamento logico del cloud di Azure dedicato alla sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="9daca-108">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="9daca-109">È anche possibile connettere le reti virtuali alla rete locale.</span><span class="sxs-lookup"><span data-stu-id="9daca-109">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="9daca-110">Altre informazioni su [Rete virtuale di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="9daca-110">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="9daca-111">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="9daca-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9daca-112">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="9daca-112">Install the npm module</span></span>

<span data-ttu-id="9daca-113">Installare il modulo npm di Rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="9daca-113">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="9daca-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="9daca-114">Example</span></span>

<span data-ttu-id="9daca-115">Questo esempio ottiene e visualizza l'elenco di reti virtuali</span><span class="sxs-lookup"><span data-stu-id="9daca-115">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="9daca-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="9daca-116">Samples</span></span>

<span data-ttu-id="9daca-117">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="9daca-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
