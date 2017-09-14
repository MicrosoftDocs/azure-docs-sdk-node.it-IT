---
title: Moduli di Azure Key Vault per Node.js
description: Informazioni di riferimento sui moduli di Azure Key Vault per Node.js
keywords: Azure, SDK, API, Key Vault, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: e497e1e0e369dfd975fe5a2d7759ec893fbf6aff
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-key-vault-modules-for-nodejs"></a>Moduli di Azure Key Vault per Node.js

## <a name="overview"></a>Panoramica

L'insieme di credenziali chiave di Azure consente di proteggere le chiavi e i segreti di crittografia usati da servizi e applicazioni cloud. Con l'insieme di credenziali delle chiavi è possibile crittografare chiavi e segreti (ad esempio, chiavi di autenticazione, chiavi dell'account di archiviazione, chiavi di crittografia dati, file PFX e password) usando chiavi protette da moduli di protezione hardware (HSM). Per una maggiore sicurezza, è possibile importare o generare le chiavi in moduli di protezione hardware. Se si sceglie di eseguire questa operazione, Microsoft elabora le chiavi in moduli di protezione hardware FIPS 140-2 livello 2 convalidati (hardware e firmware).

L'insieme di credenziali chiave semplifica il processo di gestione delle chiavi e consente di mantenere il controllo delle chiavi che accedono ai dati e li crittografano. Gli sviluppatori possono creare chiavi per lo sviluppo e il test in pochi minuti e quindi eseguirne facilmente la migrazione alle chiavi di produzione. Gli amministratori della sicurezza possono concedere (e revocare) le autorizzazioni per chiavi, in base alle esigenze.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm 

Installare il modulo npm di Azure Key Vault

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>Esempio

Questo esempio crea un nuovo servizio Key Vault in Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>Esempi

- [Introduzione a Key Vault in Node.js](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Manage Azure resources and resource groups with Node.js (Gestire risorse e gruppi di risorse di Azure con Node.js)](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) (Integrazione di Azure AD in un'applicazione Web NodeJS) 

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
