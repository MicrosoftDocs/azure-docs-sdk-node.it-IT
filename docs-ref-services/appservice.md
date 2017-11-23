---
title: Moduli del servizio app di Azure per Node.js
description: Informazioni di riferimento sui moduli del servizio app di Azure per Node.js
keywords: Azure, Node, SDK, API, app Web, dispositivi mobili, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: c695ae6d523ea731b18382ba0906f78b40ce301f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="5eefe-104">Moduli del servizio app di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="5eefe-104">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5eefe-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="5eefe-105">Overview</span></span>

<span data-ttu-id="5eefe-106">Il servizio app di Azure è un'offerta di piattaforma distribuita come servizio (PaaS) di Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="5eefe-106">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="5eefe-107">Consente di creare app Web e per dispositivi mobili per qualsiasi piattaforma o dispositivo,</span><span class="sxs-lookup"><span data-stu-id="5eefe-107">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="5eefe-108">integrare le app con soluzioni SaaS, connettersi con applicazioni locali e automatizzare i processi aziendali.</span><span class="sxs-lookup"><span data-stu-id="5eefe-108">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="5eefe-109">Azure esegue le app in macchine virtuali (VM) completamente gestite, con le risorse di VM condivise o le VM dedicate desiderate.</span><span class="sxs-lookup"><span data-stu-id="5eefe-109">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="5eefe-110">Il servizio app include le funzionalità Web e per dispositivi mobili prima fornite separatamente come Siti Web di Azure e Servizi mobili di Azure.</span><span class="sxs-lookup"><span data-stu-id="5eefe-110">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="5eefe-111">Include anche nuove funzionalità per l'automazione dei processi aziendali e l'hosting di API cloud.</span><span class="sxs-lookup"><span data-stu-id="5eefe-111">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="5eefe-112">Come singolo servizio integrato, il servizio app consente di combinare vari componenti (siti Web, back-end di app per dispositivi mobili, API RESTful e processi aziendali) in un'unica soluzione.</span><span class="sxs-lookup"><span data-stu-id="5eefe-112">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="5eefe-113">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="5eefe-113">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="5eefe-114">Installare il pacchetto npm</span><span class="sxs-lookup"><span data-stu-id="5eefe-114">Install the npm package</span></span>

<span data-ttu-id="5eefe-115">Installare i moduli del servizio app di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="5eefe-115">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="5eefe-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="5eefe-116">Example</span></span>

<span data-ttu-id="5eefe-117">Questo esempio crea un sito Web in Azure usando Node.js.</span><span class="sxs-lookup"><span data-stu-id="5eefe-117">This example creates a website on Azure using Node.js.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a><span data-ttu-id="5eefe-118">Esempi</span><span class="sxs-lookup"><span data-stu-id="5eefe-118">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="5eefe-119">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="5eefe-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
