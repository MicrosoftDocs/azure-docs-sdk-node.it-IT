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
# <a name="azure-app-service-modules-for-nodejs"></a>Moduli del servizio app di Azure per Node.js

## <a name="overview"></a>Panoramica

Il servizio app di Azure è un'offerta di piattaforma distribuita come servizio (PaaS) di Microsoft Azure. Consente di creare app Web e per dispositivi mobili per qualsiasi piattaforma o dispositivo, integrare le app con soluzioni SaaS, connettersi con applicazioni locali e automatizzare i processi aziendali. Azure esegue le app in macchine virtuali (VM) completamente gestite, con le risorse di VM condivise o le VM dedicate desiderate.

Il servizio app include le funzionalità Web e per dispositivi mobili prima fornite separatamente come Siti Web di Azure e Servizi mobili di Azure. Include anche nuove funzionalità per l'automazione dei processi aziendali e l'hosting di API cloud. Come singolo servizio integrato, il servizio app consente di combinare vari componenti (siti Web, back-end di app per dispositivi mobili, API RESTful e processi aziendali) in un'unica soluzione.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-package"></a>Installare il pacchetto npm

Installare i moduli del servizio app di Azure per Node.js

```bash
npm install azure-arm-website
```

### <a name="example"></a>Esempio

Questo esempio crea un sito Web in Azure usando Node.js.

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

## <a name="samples"></a>Esempi

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
