---
title: Moduli di Rete virtuale di Azure per Node.js
description: Informazioni di riferimento sui moduli di Rete virtuale di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: f073c700c8df7f7aa05c93d725051d3a9976bebc
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="c6374-103">Moduli di Rete virtuale di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="c6374-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c6374-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="c6374-104">Overview</span></span>

<span data-ttu-id="c6374-105">Il servizio Rete virtuale di Azure consente di connettere tra loro le risorse di Azure in modo sicuro con reti virtuali.</span><span class="sxs-lookup"><span data-stu-id="c6374-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="c6374-106">Una rete virtuale è una rappresentazione della propria rete nel cloud.</span><span class="sxs-lookup"><span data-stu-id="c6374-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="c6374-107">È un isolamento logico del cloud di Azure dedicato alla sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="c6374-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="c6374-108">È anche possibile connettere le reti virtuali alla rete locale.</span><span class="sxs-lookup"><span data-stu-id="c6374-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="c6374-109">Altre informazioni su [Rete virtuale di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="c6374-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="c6374-110">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="c6374-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c6374-111">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="c6374-111">Install the npm module</span></span>

<span data-ttu-id="c6374-112">Installare il modulo npm di Rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="c6374-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="c6374-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="c6374-113">Example</span></span>

<span data-ttu-id="c6374-114">Questo esempio ottiene e visualizza l'elenco di reti virtuali</span><span class="sxs-lookup"><span data-stu-id="c6374-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="c6374-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="c6374-115">Samples</span></span>

<span data-ttu-id="c6374-116">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="c6374-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
