---
title: Moduli di inoltro di Azure per Node.js
description: Informazioni di riferimento sui moduli di inoltro di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 632e17f9169353ad9348b3b098b4a3e8d873238a
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="8f52b-103">Moduli di inoltro di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="8f52b-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="8f52b-104">Il servizio di inoltro di Azure crea applicazioni ibride consentendo di esporre in modo sicuro nel cloud pubblico i servizi che risiedono in una rete aziendale, senza dover aprire una connessione firewall o richiedere modifiche di notevole impatto a un'infrastruttura di rete aziendale.</span><span class="sxs-lookup"><span data-stu-id="8f52b-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="8f52b-105">Il servizio di inoltro supporta un'ampia gamma di protocolli di trasporto e standard dei servizi Web.</span><span class="sxs-lookup"><span data-stu-id="8f52b-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="8f52b-106">Altre informazioni sul [servizio di inoltro di Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="8f52b-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="8f52b-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="8f52b-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8f52b-108">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="8f52b-108">Install the npm module</span></span>

<span data-ttu-id="8f52b-109">Installare il modulo npm di inoltro di Azure</span><span class="sxs-lookup"><span data-stu-id="8f52b-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="8f52b-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="8f52b-110">Example</span></span>

<span data-ttu-id="8f52b-111">Questo esempio elenca gli spazi dei nomi per un client di inoltro.</span><span class="sxs-lookup"><span data-stu-id="8f52b-111">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="8f52b-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="8f52b-112">Samples</span></span>

<span data-ttu-id="8f52b-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="8f52b-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
