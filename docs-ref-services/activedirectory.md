---
title: Moduli di Azure Active Directory per Node.js
description: Informazioni di riferimento sui moduli di Azure Active Directory per Node.js
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: c356801500aa3ef9038fc27634c8a95debf152b3
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259920"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Moduli di Azure Active Directory per Node.js

## <a name="overview"></a>Panoramica

> [!IMPORTANT]
> Per accedere alle risorse di Azure Active Directoryi è consigliabile usare [Microsoft Graph](https://graph.microsoft.io/) anziché l'API Graph di Azure AD. Le attività di sviluppo sono ora concentrate su Microsoft Graph e non sono previsti altri miglioramenti all'API Graph di Azure AD. Il numero di scenari in cui potrebbe essere ancora appropriato usare l'API Graph di Azure AD è piuttosto limitato. Per altre informazioni, vedere il post [Microsoft Graph o Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) nel blog di Office Developer Center.

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
