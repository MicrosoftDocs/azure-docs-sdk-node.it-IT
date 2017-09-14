---
title: Moduli di Azure Active Directory per Node.js
description: Informazioni di riferimento sui moduli di Azure Active Directory per Node.js
keywords: Azure, Node, SDK, API, archiviazione, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: d0084faa78986bd5518526c6eb84b9c13fdb10bf
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Moduli di Azure Active Directory per Node.js

## <a name="overview"></a>Panoramica

[Azure Active Directory Authentication Library (ADAL) per Node.js](https://www.npmjs.com/package/adal-node) consente alle applicazioni Node.js di eseguire l'autenticazione in AAD per accedere alle risorse Web protette da AAD.

## <a name="client-package"></a>Pacchetto client

### <a name="install-the-npm-modules"></a>Installare i moduli npm

Usare npm per installare il client di archiviazione di Azure o i moduli di gestione.

```bash
npm install adal-node
```   

### <a name="example"></a>Esempio

Questo [esempio relativo alle credenziali client](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustra l'autenticazione da server a server tramite le credenziali client.

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a>Esempi

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
