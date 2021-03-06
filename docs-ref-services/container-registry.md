---
title: Moduli di Registro Azure Container per Node.js
description: Informazioni di riferimento sui moduli di Registro Azure Container per Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52155016"
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Moduli di Registro Azure Container per Node.js

Registro Azure Container è un servizio gestito di registri Docker basato sull'applicazione open source Docker Registry 2.0. Creare e gestire registri contenitori di Azure per archiviare e gestire immagini contenitore Docker private. È possibile usare i registri contenitori in Azure con la pipeline di sviluppo e distribuzione di contenitori esistente e attingere alle competenze della community Docker.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Registro Azure Container

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>Esempio

Questo esempio ottiene un elenco dei contenitori disponibili.

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
