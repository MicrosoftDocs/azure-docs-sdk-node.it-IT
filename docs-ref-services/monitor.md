---
title: Moduli di Monitoraggio di Azure per Node.js
description: Informazioni di riferimento sui moduli di Monitoraggio di Azure per Node.js
keywords: Azure, SDK, API, Monitoraggio, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="e9322-104">Moduli di Monitoraggio di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="e9322-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e9322-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="e9322-105">Overview</span></span>
<span data-ttu-id="e9322-106">Le applicazioni cloud sono complesse e hanno molte parti mobili.</span><span class="sxs-lookup"><span data-stu-id="e9322-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="e9322-107">Il monitoraggio offre la possibilità di garantire il funzionamento e l'integrità dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e9322-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="e9322-108">Consente anche di prevenire i problemi potenziali o di risolvere quelli precedenti.</span><span class="sxs-lookup"><span data-stu-id="e9322-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="e9322-109">Inoltre, è possibile usare i dati di monitoraggio per ottenere informazioni approfondite sull'applicazione,</span><span class="sxs-lookup"><span data-stu-id="e9322-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="e9322-110">utili per migliorarne le prestazioni o la manutenibilità oppure per automatizzare azioni che altrimenti richiederebbero un intervento manuale.</span><span class="sxs-lookup"><span data-stu-id="e9322-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="e9322-111">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="e9322-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="e9322-112">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="e9322-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="e9322-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="e9322-113">Example</span></span>

<span data-ttu-id="e9322-114">Questo esempio di codice visualizza tutte le regole di avviso associate a un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="e9322-114">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="e9322-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="e9322-115">Samples</span></span>

<span data-ttu-id="e9322-116">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="e9322-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
