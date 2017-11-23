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
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="6294f-104">Moduli di Azure Active Directory per Node.js</span><span class="sxs-lookup"><span data-stu-id="6294f-104">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6294f-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="6294f-105">Overview</span></span>

<span data-ttu-id="6294f-106">[Azure Active Directory Authentication Library (ADAL) per Node.js](https://www.npmjs.com/package/adal-node) consente alle applicazioni Node.js di eseguire l'autenticazione in AAD per accedere alle risorse Web protette da AAD.</span><span class="sxs-lookup"><span data-stu-id="6294f-106">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="6294f-107">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="6294f-107">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="6294f-108">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="6294f-108">Install the npm modules</span></span>

<span data-ttu-id="6294f-109">Usare npm per installare il client di archiviazione di Azure o i moduli di gestione.</span><span class="sxs-lookup"><span data-stu-id="6294f-109">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="6294f-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="6294f-110">Example</span></span>

<span data-ttu-id="6294f-111">Questo [esempio relativo alle credenziali client](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustra l'autenticazione da server a server tramite le credenziali client.</span><span class="sxs-lookup"><span data-stu-id="6294f-111">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="6294f-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="6294f-112">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="6294f-113">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="6294f-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
