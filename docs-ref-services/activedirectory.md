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
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="49e55-103">Moduli di Azure Active Directory per Node.js</span><span class="sxs-lookup"><span data-stu-id="49e55-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="49e55-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="49e55-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49e55-105">Per accedere alle risorse di Azure Active Directoryi è consigliabile usare [Microsoft Graph](https://graph.microsoft.io/) anziché l'API Graph di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49e55-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="49e55-106">Le attività di sviluppo sono ora concentrate su Microsoft Graph e non sono previsti altri miglioramenti all'API Graph di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49e55-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="49e55-107">Il numero di scenari in cui potrebbe essere ancora appropriato usare l'API Graph di Azure AD è piuttosto limitato. Per altre informazioni, vedere il post [Microsoft Graph o Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) nel blog di Office Developer Center.</span><span class="sxs-lookup"><span data-stu-id="49e55-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="49e55-108">[Azure Active Directory Authentication Library (ADAL) per Node.js](https://www.npmjs.com/package/adal-node) consente alle applicazioni Node.js di eseguire l'autenticazione in AAD per accedere alle risorse Web protette da AAD.</span><span class="sxs-lookup"><span data-stu-id="49e55-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="49e55-109">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="49e55-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="49e55-110">Installare i moduli npm</span><span class="sxs-lookup"><span data-stu-id="49e55-110">Install the npm modules</span></span>

<span data-ttu-id="49e55-111">Usare npm per installare il client di archiviazione di Azure o i moduli di gestione.</span><span class="sxs-lookup"><span data-stu-id="49e55-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="49e55-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="49e55-112">Example</span></span>

<span data-ttu-id="49e55-113">Questo [esempio relativo alle credenziali client](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustra l'autenticazione da server a server tramite le credenziali client.</span><span class="sxs-lookup"><span data-stu-id="49e55-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="49e55-114">Esempi</span><span class="sxs-lookup"><span data-stu-id="49e55-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="49e55-115">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="49e55-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
