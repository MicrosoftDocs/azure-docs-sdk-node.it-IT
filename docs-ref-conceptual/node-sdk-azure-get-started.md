---
title: Introduzione ai moduli di Azure per Node.js
description: Introduzione alla gestione dell'autenticazione e delle risorse con i moduli di Azure per Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 072574c70b658806cd998dc0af8a81be3ea56bb4
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="09175-103">Introduzione ai moduli di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="09175-103">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="09175-104">Questa guida illustra l'installazione dei moduli di Azure per Node.js, l'autenticazione in Azure con un'entità servizio e l'esecuzione del codice di esempio che crea le risorse nella sottoscrizione di Azure e si connette ai servizi cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="09175-104">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09175-105">prerequisiti</span><span class="sxs-lookup"><span data-stu-id="09175-105">Prerequisites</span></span>

- <span data-ttu-id="09175-106">Un account Azure.</span><span class="sxs-lookup"><span data-stu-id="09175-106">An Azure account.</span></span> <span data-ttu-id="09175-107">Se non è disponibile, [ottenere una versione di valutazione gratuita](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="09175-107">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="09175-108">Node.JS</span><span class="sxs-lookup"><span data-stu-id="09175-108">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="09175-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) o [interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="09175-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="09175-110">Preparare l'ambiente</span><span class="sxs-lookup"><span data-stu-id="09175-110">Prepare your environment</span></span>

<span data-ttu-id="09175-111">Creare un nuovo progetto in una directory vuota e installare i moduli npm seguenti:</span><span class="sxs-lookup"><span data-stu-id="09175-111">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="09175-112">Configurare l'autenticazione</span><span class="sxs-lookup"><span data-stu-id="09175-112">Set up authentication</span></span>

<span data-ttu-id="09175-113">Le applicazioni Node.js devono leggere e creare le autorizzazioni nella sottoscrizione di Azure per eseguire il codice di esempio in questa guida.</span><span class="sxs-lookup"><span data-stu-id="09175-113">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="09175-114">Creare un'entità servizio e configurare l'applicazione per l'esecuzione con le rispettive credenziali.</span><span class="sxs-lookup"><span data-stu-id="09175-114">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="09175-115">Le entità servizio sono un account non interattivo associato all'identità a cui vengono concessi solo i privilegi necessari per l'esecuzione dell'app.</span><span class="sxs-lookup"><span data-stu-id="09175-115">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="09175-116">[Crea un'entità servizio usando l'interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) e acquisire l'output.</span><span class="sxs-lookup"><span data-stu-id="09175-116">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="09175-117">Sarà necessario fornire una [password di protezione](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) nell'argomento password invece di `MY_SECURE_PASSWORD`.</span><span class="sxs-lookup"><span data-stu-id="09175-117">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

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

<span data-ttu-id="09175-118">Esportare i valori per *appId*, *password* e *tenant* come variabili di ambiente:</span><span class="sxs-lookup"><span data-stu-id="09175-118">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="09175-119">Ottenere l'ID per la propria sottoscrizione con [az account show](https://docs.microsoft.com/cli/azure/account#show)</span><span class="sxs-lookup"><span data-stu-id="09175-119">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

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

<span data-ttu-id="09175-120">Esportare l'ID sottoscrizione come variabile di ambiente</span><span class="sxs-lookup"><span data-stu-id="09175-120">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="09175-121">Creare una macchina virtuale Linux</span><span class="sxs-lookup"><span data-stu-id="09175-121">Create a Linux virtual machine</span></span>

<span data-ttu-id="09175-122">Creare un nuovo file *createVM.js* nella directory corrente con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="09175-122">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="09175-123">Aggiornare il valore di `adminPass` con una password valida.</span><span class="sxs-lookup"><span data-stu-id="09175-123">Update the value of `adminPass` with a good password.</span></span>

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

<span data-ttu-id="09175-124">Eseguire il codice dalla riga di comando:</span><span class="sxs-lookup"><span data-stu-id="09175-124">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="09175-125">Dopo il completamento del codice, ottenere l'IP della nuova macchina virtuale ed eseguire l'accesso con SSH usando il valore di `adminPass` ricavato dal codice.</span><span class="sxs-lookup"><span data-stu-id="09175-125">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="09175-126">Scrivere un BLOB in Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="09175-126">Write a blob to Azure Storage</span></span>

<span data-ttu-id="09175-127">Creare un nuovo file *uploadFile.js* nella directory corrente con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="09175-127">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

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

<span data-ttu-id="09175-128">Eseguire il comando e quindi copiare e incollare l'URL dall'output nel Web browser per visualizzare il file in Archiviazione di Azure:</span><span class="sxs-lookup"><span data-stu-id="09175-128">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="09175-129">Pulire le risorse</span><span class="sxs-lookup"><span data-stu-id="09175-129">Clean up resources</span></span>

<span data-ttu-id="09175-130">Eliminare il gruppo di risorse per rimuovere le risorse create in questa guida.</span><span class="sxs-lookup"><span data-stu-id="09175-130">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="09175-131">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="09175-131">Next steps</span></span>

<span data-ttu-id="09175-132">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="09175-132">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="09175-133">Riferimenti</span><span class="sxs-lookup"><span data-stu-id="09175-133">Reference</span></span> 

<span data-ttu-id="09175-134">Le [informazioni di riferimento](/javascript/api/overview/azure/) sono disponibili per tutti i pacchetti.</span><span class="sxs-lookup"><span data-stu-id="09175-134">A [reference](/javascript/api/overview/azure/) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="09175-135">Ottenere supporto e inviare commenti</span><span class="sxs-lookup"><span data-stu-id="09175-135">Get help and give feedback</span></span>

<span data-ttu-id="09175-136">Pubblicare le domande per la community in [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span><span class="sxs-lookup"><span data-stu-id="09175-136">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="09175-137">Segnalare bug e problemi in sospeso relativi ai moduli di Azure per Node.js nel [progetto GitHub](https://github.com/Azure/azure-sdk-for-node).</span><span class="sxs-lookup"><span data-stu-id="09175-137">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

