---
title: Moduli di Azure Key Vault per Node.js
description: Informazioni di riferimento sui moduli di Azure Key Vault per Node.js
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51388545"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="2fb47-103">Moduli di Azure Key Vault per Node.js</span><span class="sxs-lookup"><span data-stu-id="2fb47-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="2fb47-104">L'insieme di credenziali delle chiavi di Azure consente di proteggere le chiavi e i segreti di crittografia usati da servizi e applicazioni cloud.</span><span class="sxs-lookup"><span data-stu-id="2fb47-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="2fb47-105">Con l'insieme di credenziali delle chiavi è possibile crittografare chiavi e segreti (ad esempio, chiavi di autenticazione, chiavi dell'account di archiviazione, chiavi di crittografia dati, file PFX e password) usando chiavi protette da moduli di protezione hardware (HSM).</span><span class="sxs-lookup"><span data-stu-id="2fb47-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="2fb47-106">Per una maggiore sicurezza, è possibile importare o generare le chiavi in moduli di protezione hardware.</span><span class="sxs-lookup"><span data-stu-id="2fb47-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="2fb47-107">Se si sceglie di eseguire questa operazione, Microsoft elabora le chiavi in moduli di protezione hardware FIPS 140-2 livello 2 convalidati (hardware e firmware).</span><span class="sxs-lookup"><span data-stu-id="2fb47-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="2fb47-108">L'insieme di credenziali chiave semplifica il processo di gestione delle chiavi e consente di mantenere il controllo delle chiavi che accedono ai dati e li crittografano.</span><span class="sxs-lookup"><span data-stu-id="2fb47-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="2fb47-109">Gli sviluppatori possono creare chiavi per lo sviluppo e il test in pochi minuti e quindi eseguirne facilmente la migrazione alle chiavi di produzione.</span><span class="sxs-lookup"><span data-stu-id="2fb47-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="2fb47-110">Gli amministratori della sicurezza possono concedere (e revocare) le autorizzazioni per chiavi, in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="2fb47-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="2fb47-111">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="2fb47-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2fb47-112">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="2fb47-112">Install the npm module</span></span> 

<span data-ttu-id="2fb47-113">Installare il modulo npm di Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="2fb47-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="2fb47-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="2fb47-114">Example</span></span>

<span data-ttu-id="2fb47-115">Questo esempio crea un nuovo servizio Key Vault in Azure.</span><span class="sxs-lookup"><span data-stu-id="2fb47-115">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2fb47-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="2fb47-116">Samples</span></span>

- [<span data-ttu-id="2fb47-117">Introduzione a Key Vault in Node.js</span><span class="sxs-lookup"><span data-stu-id="2fb47-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="2fb47-118">Gestire risorse e gruppi di risorse di Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="2fb47-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- <span data-ttu-id="2fb47-119">[Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) (Integrazione di Azure AD in un'applicazione Web NodeJS)</span><span class="sxs-lookup"><span data-stu-id="2fb47-119">[Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/)</span></span> 

<span data-ttu-id="2fb47-120">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="2fb47-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
