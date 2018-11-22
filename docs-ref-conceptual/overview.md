---
title: Moduli di Azure per JavaScript
description: Panoramica dei moduli di gestione e di servizi di Azure per JavaScript
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 1d97df65f12c465cf6c790d1e3c016a9ff4aa5ba
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52064562"
---
# <a name="azure-modules-for-javascript"></a><span data-ttu-id="1f148-103">Moduli di Azure per JavaScript</span><span class="sxs-lookup"><span data-stu-id="1f148-103">Azure modules for JavaScript</span></span>

<span data-ttu-id="1f148-104">Gestire le risorse di Azure e connettersi ai servizi dalle applicazioni JavaScript con i moduli di Azure per JavaScript.</span><span class="sxs-lookup"><span data-stu-id="1f148-104">Manage Azure resources and connect to services from your JavaScript applications with the Azure modules for JavaScript.</span></span> <span data-ttu-id="1f148-105">Il codice è disponibile come [moduli npm](node-sdk-azure-install.md) da usare nei progetti.</span><span class="sxs-lookup"><span data-stu-id="1f148-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="1f148-106">Gestire le risorse di Azure</span><span class="sxs-lookup"><span data-stu-id="1f148-106">Manage Azure resources</span></span>

<span data-ttu-id="1f148-107">Usare i moduli di gestione per creare ed eseguire query sulle risorse dalle app o per creare i propri strumenti di automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="1f148-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="1f148-108">Ad esempio, per creare una VM Linux usando un'interfaccia di rete esistente, scrivere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="1f148-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

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

<span data-ttu-id="1f148-109">Vedere le [istruzioni di installazione](node-sdk-azure-install.md) per ottenere un elenco completo dei moduli e l'[articolo introduttivo](node-sdk-azure-get-started.md) per configurare l'autenticazione ed eseguire il codice di esempio per creare e aggiornare le risorse nella propria sottoscrizione di Azure.</span><span class="sxs-lookup"><span data-stu-id="1f148-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="1f148-110">Connettersi ai servizi di Azure</span><span class="sxs-lookup"><span data-stu-id="1f148-110">Connect to Azure services</span></span>

<span data-ttu-id="1f148-111">Oltre a usare i moduli di Azure per creare e gestire risorse in Azure, è possibile usare pacchetti per connettersi ai servizi cloud di Azure e usarli nelle app.</span><span class="sxs-lookup"><span data-stu-id="1f148-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="1f148-112">È ad esempio possibile aggiornare una tabella di un database SQL o caricare file in Archiviazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="1f148-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="1f148-113">Selezionare il pacchetto necessario per un servizio specifico dall'[elenco completo](node-sdk-azure-install.md) e passare al [centro per sviluppatori JavaScript](https://azure.microsoft.com/develop/nodejs/) per ottenere esercitazioni e codice di esempio e apprendere l'uso dei moduli nelle app.</span><span class="sxs-lookup"><span data-stu-id="1f148-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [JavaScript developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="1f148-114">Per stampare, ad esempio, i contenuti di ogni BLOB in un contenitore di archiviazione di Azure:</span><span class="sxs-lookup"><span data-stu-id="1f148-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="1f148-115">Codice di esempio e informazioni di riferimento</span><span class="sxs-lookup"><span data-stu-id="1f148-115">Sample code and reference</span></span>

<span data-ttu-id="1f148-116">Gli esempi seguenti sono relativi ad attività comuni con i moduli di gestione di Azure e includono codice pronto per l'uso nelle app:</span><span class="sxs-lookup"><span data-stu-id="1f148-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="1f148-117">Macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="1f148-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="1f148-118">App Web</span><span class="sxs-lookup"><span data-stu-id="1f148-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="1f148-119">Database SQL</span><span class="sxs-lookup"><span data-stu-id="1f148-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="1f148-120">Le [informazioni di riferimento](https://docs.microsoft.com/javascript/api) sono disponibili per tutti i moduli nei moduli di gestione e di servizi.</span><span class="sxs-lookup"><span data-stu-id="1f148-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="1f148-121">Le nuove funzionalità, le modifiche di rilievo e le istruzioni per la migrazione dalle versioni precedenti sono disponibili nelle [note sulla versione](https://github.com/Azure/azure-sdk-for-node/releases).</span><span class="sxs-lookup"><span data-stu-id="1f148-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>