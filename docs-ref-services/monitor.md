---
title: Moduli di Monitoraggio di Azure per Node.js
description: Informazioni di riferimento sui moduli di Monitoraggio di Azure per Node.js
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: fb2cc5ba927fe03fb5fe3114919ed1b0b6e969ae
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2018
ms.locfileid: "50346349"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="1e90d-103">Moduli di Monitoraggio di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="1e90d-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="1e90d-104">Le applicazioni cloud sono complesse e hanno molte parti mobili.</span><span class="sxs-lookup"><span data-stu-id="1e90d-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="1e90d-105">Il monitoraggio offre la possibilità di garantire il funzionamento e l'integrità dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1e90d-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="1e90d-106">Consente anche di prevenire i problemi potenziali o di risolvere quelli precedenti.</span><span class="sxs-lookup"><span data-stu-id="1e90d-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="1e90d-107">Inoltre, è possibile usare i dati di monitoraggio per ottenere informazioni approfondite sull'applicazione,</span><span class="sxs-lookup"><span data-stu-id="1e90d-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="1e90d-108">utili per migliorarne le prestazioni o la manutenibilità oppure per automatizzare azioni che altrimenti richiederebbero un intervento manuale.</span><span class="sxs-lookup"><span data-stu-id="1e90d-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="1e90d-109">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="1e90d-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="1e90d-110">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="1e90d-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="1e90d-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="1e90d-111">Example</span></span>

<span data-ttu-id="1e90d-112">Questo esempio di codice visualizza tutte le regole di avviso associate a un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="1e90d-112">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });
```

### <a name="samples"></a><span data-ttu-id="1e90d-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="1e90d-113">Samples</span></span>

<span data-ttu-id="1e90d-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="1e90d-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
