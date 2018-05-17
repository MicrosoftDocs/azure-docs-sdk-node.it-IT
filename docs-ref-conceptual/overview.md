---
title: Moduli di Azure per Node.js
description: Panoramica dei moduli di gestione e di servizi di Azure per Node.js
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 165e1580e408b71b6147e51c41e22bc8fe7277a1
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-modules-for-nodejs"></a>Moduli di Azure per Node.js

Gestire le risorse di Azure e connettersi ai servizi dalle applicazioni Node.js con i moduli di Azure per Node.js. Il codice è disponibile come [moduli npm](node-sdk-azure-install.md) da usare nei progetti. 

## <a name="manage-azure-resources"></a>Gestire le risorse di Azure

Usare i moduli di gestione per creare ed eseguire query sulle risorse dalle app o per creare i propri strumenti di automazione di Azure. 

Ad esempio, per creare una VM Linux usando un'interfaccia di rete esistente, scrivere il codice seguente:

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
                    primary: true
                }
            ]
        },
        storageProfile: {
            imageReference: {
                publisher: 'Canonical',
                offer: 'UbuntuServer',
                sku: '16.04-LTS',
                version: 'latest'
            },
        }
    };
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

Vedere le [istruzioni di installazione](node-sdk-azure-install.md) per ottenere un elenco completo dei moduli e l'[articolo introduttivo](node-sdk-azure-get-started.md) per configurare l'autenticazione ed eseguire il codice di esempio per creare e aggiornare le risorse nella propria sottoscrizione di Azure. 

## <a name="connect-to-azure-services"></a>Connettersi ai servizi di Azure

Oltre a usare i moduli di Azure per creare e gestire risorse in Azure, è possibile usare pacchetti per connettersi ai servizi cloud di Azure e usarli nelle app. È ad esempio possibile aggiornare una tabella di un database SQL o caricare file in Archiviazione di Azure. Selezionare il pacchetto necessario per un servizio specifico dall'[elenco completo](node-sdk-azure-install.md) e passare al [centro per sviluppatori Node.js](https://azure.microsoft.com/develop/nodejs/) per ottenere esercitazioni e codice di esempio per scoprire come usare i moduli nelle app.

Per stampare, ad esempio, i contenuti di ogni BLOB in un contenitore di archiviazione di Azure:

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>Codice di esempio e informazioni di riferimento

Gli esempi seguenti sono relativi ad attività comuni con i moduli di gestione di Azure e includono codice pronto per l'uso nelle app:

- [Macchine virtuali](node-samples-services-compute.md)
- [App Web](node-samples-services-web-and-mobile.md)
- [Database SQL](node-samples-services-database.md)
   
Le [informazioni di riferimento](https://docs.microsoft.com/javascript/api) sono disponibili per tutti i moduli nei moduli di gestione e di servizi. Le nuove funzionalità, le modifiche di rilievo e le istruzioni per la migrazione dalle versioni precedenti sono disponibili nelle [note sulla versione](https://github.com/Azure/azure-sdk-for-node/releases).