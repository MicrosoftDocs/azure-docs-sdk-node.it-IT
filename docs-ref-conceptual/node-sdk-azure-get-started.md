---
title: Introduzione ai moduli di Azure per Node.js
description: Introduzione all'uso di base dei moduli di Azure per Node.js con la propria sottoscrizione di Azure.
keywords: Azure, Node, SDK, API, introduzione, node.js
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: ec83d58585014cca05885af4de55473637c410e8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a>Introduzione ai moduli di Azure per Node.js

Questa guida illustra l'installazione dei moduli di Azure per Node.js, l'autenticazione in Azure con un'entità servizio e l'esecuzione del codice di esempio che crea le risorse nella sottoscrizione di Azure e si connette ai servizi cloud di Azure.

## <a name="prerequisites"></a>Prerequisiti

- Un account Azure. Se non è disponibile, [ottenere una versione di valutazione gratuita](https://azure.microsoft.com/free/)
- [Node.js](https://nodejs.org)
- [Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) o [interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a>Preparare l'ambiente

Creare un nuovo progetto in una directory vuota e installare i moduli npm seguenti:

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a>Configurare l'autenticazione

Le applicazioni Node.js devono leggere e creare le autorizzazioni nella sottoscrizione di Azure per eseguire il codice di esempio in questa guida. Creare un'entità servizio e configurare l'applicazione per l'esecuzione con le rispettive credenziali. Le entità servizio sono un account non interattivo associato all'identità a cui vengono concessi solo i privilegi necessari per l'esecuzione dell'app.

[Crea un'entità servizio usando l'interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) e acquisire l'output. Sarà necessario fornire una [password di protezione](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) nell'argomento password invece di `MY_SECURE_PASSWORD`.

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

Esportare i valori per *appId*, *password* e *tenant* come variabili di ambiente:

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

Ottenere l'ID per la propria sottoscrizione con [az account show](https://docs.microsoft.com/cli/azure/account#show)

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

Esportare l'ID sottoscrizione come variabile di ambiente

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a>Creare una macchina virtuale Linux

Creare un nuovo file *createVM.js* nella directory corrente con il codice seguente. Aggiornare il valore di `adminPass` con una password valida.

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
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

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

Eseguire il codice dalla riga di comando:

```bash
node createVM.js
```

Dopo il completamento del codice, ottenere l'IP della nuova macchina virtuale ed eseguire l'accesso con SSH usando il valore di `adminPass` ricavato dal codice.

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a>Scrivere un BLOB in Archiviazione di Azure

Creare un nuovo file *uploadFile.js* nella directory corrente con il codice seguente.

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

Eseguire il comando e quindi copiare e incollare l'URL dall'output nel Web browser per visualizzare il file in Archiviazione di Azure:

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a>Pulire le risorse

Eliminare il gruppo di risorse per rimuovere le risorse create in questa guida.

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a>Passaggi successivi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.

## <a name="reference"></a>riferimento 

Le [informazioni di riferimento](/nodejs/api/overview/azure/?view=azure-node-2.0.0) sono disponibili per tutti i pacchetti.

## <a name="get-help-and-give-feedback"></a>Ottenere supporto e inviare commenti

Pubblicare le domande per la community in [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js). Segnalare bug e problemi in sospeso relativi ai moduli di Azure per Node.js nel [progetto GitHub](https://github.com/Azure/azure-sdk-for-node).

