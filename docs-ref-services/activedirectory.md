---
title: Moduli di Azure Active Directory per Node.js
description: Informazioni di riferimento sui moduli di Azure Active Directory per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="d35ec-103">Moduli di Azure Active Directory per Node.js</span><span class="sxs-lookup"><span data-stu-id="d35ec-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d35ec-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d35ec-104">Overview</span></span>

<span data-ttu-id="d35ec-105">[Azure Active Directory Authentication Library (ADAL) per Node.js](https://www.npmjs.com/package/adal-node) consente alle applicazioni Node.js di eseguire l'autenticazione in AAD per accedere alle risorse Web protette da AAD.</span><span class="sxs-lookup"><span data-stu-id="d35ec-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="d35ec-106">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="d35ec-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="d35ec-107">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="d35ec-107">Install the npm modules</span></span>

<span data-ttu-id="d35ec-108">Usare npm per installare il client di archiviazione di Azure o i moduli di gestione.</span><span class="sxs-lookup"><span data-stu-id="d35ec-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="d35ec-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="d35ec-109">Example</span></span>

<span data-ttu-id="d35ec-110">Questo [esempio relativo alle credenziali client](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustra l'autenticazione da server a server tramite le credenziali client.</span><span class="sxs-lookup"><span data-stu-id="d35ec-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d35ec-111">Esempi</span><span class="sxs-lookup"><span data-stu-id="d35ec-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="d35ec-112">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="d35ec-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
