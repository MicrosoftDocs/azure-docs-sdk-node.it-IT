---
title: Moduli del servizio contenitore di Azure per Node.js
description: Informazioni di riferimento sui moduli del servizio contenitore di Azure per Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689827"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>Microsoft Azure SDK per Node.js: ContainerServiceClient
Questo progetto fornisce un pacchetto Node.js per l'accesso ad Azure. Attualmente supporta:
- **Node.js versione 6.x.x o successiva**

## <a name="features"></a>Funzionalità


## <a name="how-to-install"></a>Come eseguire l'installazione

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>Utilizzo

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>Esempio di autenticazione, creazione di client e visualizzazione di un elenco dei servizi contenitore

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a>Progetti correlati

- [Microsoft Azure SDK per Node.js](https://github.com/Azure/azure-sdk-for-node)