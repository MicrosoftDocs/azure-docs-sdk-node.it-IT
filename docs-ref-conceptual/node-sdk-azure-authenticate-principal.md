---
title: Creare un'entità servizio di Azure con Node.js
description: Informazioni su come Usare l'autenticazione basata su entità servizio tramite Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 98d52e21332138512d40ff2de9f5d3388fa596e4
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52140826"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="4a95a-103">Creare un'entità servizio di Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="4a95a-103">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="4a95a-104">Quando un'app deve accedere alle risorse, è possibile configurare un'identità per l'app ed eseguirne l'autenticazione con credenziali specifiche.</span><span class="sxs-lookup"><span data-stu-id="4a95a-104">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="4a95a-105">Questa identità è nota come *entità servizio*.</span><span class="sxs-lookup"><span data-stu-id="4a95a-105">This identity is known as a *service principal*.</span></span> <span data-ttu-id="4a95a-106">Essenzialmente, si creano le chiavi per l'account Azure Active Directory da fornire all'SDK per l'autenticazione invece di richiedere l'intervento dell'utente o il nome utente e la password.</span><span class="sxs-lookup"><span data-stu-id="4a95a-106">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="4a95a-107">L'approccio basato sull'entità servizio consente di:</span><span class="sxs-lookup"><span data-stu-id="4a95a-107">The service principal approach enables you to:</span></span>
- <span data-ttu-id="4a95a-108">Assegnare all'identità dell'app autorizzazioni diverse rispetto a quelle dell'utente.</span><span class="sxs-lookup"><span data-stu-id="4a95a-108">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="4a95a-109">Tali autorizzazioni sono in genere limitate alle specifiche operazioni che devono essere eseguite dall'app.</span><span class="sxs-lookup"><span data-stu-id="4a95a-109">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="4a95a-110">Usare un certificato per l'autenticazione in caso di esecuzione di uno script automatico.</span><span class="sxs-lookup"><span data-stu-id="4a95a-110">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="4a95a-111">Questo argomento illustra tre tecniche per creare un'entità servizio.</span><span class="sxs-lookup"><span data-stu-id="4a95a-111">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="4a95a-112">Portale di Azure</span><span class="sxs-lookup"><span data-stu-id="4a95a-112">Azure portal</span></span>
- <span data-ttu-id="4a95a-113">Interfaccia della riga di comando di Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="4a95a-113">Azure CLI 2.0</span></span>
- <span data-ttu-id="4a95a-114">Azure SDK per Node.js</span><span class="sxs-lookup"><span data-stu-id="4a95a-114">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="4a95a-115">Creare un'entità servizio usando il portale di Azure</span><span class="sxs-lookup"><span data-stu-id="4a95a-115">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="4a95a-116">Seguire i passaggi illustrati nell'argomento [Usare il portale per creare un'applicazione Azure Active Directory e un'entità servizio che possano accedere alle risorse](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) per generare l'entità servizio.</span><span class="sxs-lookup"><span data-stu-id="4a95a-116">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="4a95a-117">Creare un'entità servizio usando l'interfaccia della riga di comando di Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="4a95a-117">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="4a95a-118">Per creare un'entità servizio usando l'[interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2), seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="4a95a-118">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="4a95a-119">Scaricare l'[interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="4a95a-119">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="4a95a-120">Aprire una finestra del terminale.</span><span class="sxs-lookup"><span data-stu-id="4a95a-120">Open a terminal window.</span></span>

3. <span data-ttu-id="4a95a-121">Digitare il comando seguente per avviare il processo di accesso:</span><span class="sxs-lookup"><span data-stu-id="4a95a-121">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="4a95a-122">La chiamata a `az login` restituisce un URL e un codice.</span><span class="sxs-lookup"><span data-stu-id="4a95a-122">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="4a95a-123">Passare all'URL specificato, immettere il codice e accedere con l'identità di Azure. Questa operazione potrebbe venire eseguita automaticamente se l'accesso è già stato eseguito.</span><span class="sxs-lookup"><span data-stu-id="4a95a-123">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="4a95a-124">Sarà quindi possibile accedere all'account tramite l'interfaccia della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="4a95a-124">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="4a95a-125">Ottenere l'ID sottoscrizione e tenant:</span><span class="sxs-lookup"><span data-stu-id="4a95a-125">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="4a95a-126">Il testo seguente è un esempio di output:</span><span class="sxs-lookup"><span data-stu-id="4a95a-126">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="4a95a-127">**Prendere nota dell'ID sottoscrizione, che verrà usato nel passaggio 7.**</span><span class="sxs-lookup"><span data-stu-id="4a95a-127">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="4a95a-128">Creare un'entità servizio per ottenere un oggetto JSON contenente le altre informazioni necessarie per l'autenticazione con Azure.</span><span class="sxs-lookup"><span data-stu-id="4a95a-128">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="4a95a-129">Il testo seguente è un esempio di output:</span><span class="sxs-lookup"><span data-stu-id="4a95a-129">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="4a95a-130">**Prendere nota dei valori di tenant, nome e password, che verranno usati nel passaggio 7.**</span><span class="sxs-lookup"><span data-stu-id="4a95a-130">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="4a95a-131">Configurare le variabili di ambiente sostituendo i segnaposto &lt;subscriptionId>, &lt;tenant>, &lt;name> e &lt;password> con i valori ottenuti nei passaggi 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="4a95a-131">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="4a95a-132">**Tramite Bash**</span><span class="sxs-lookup"><span data-stu-id="4a95a-132">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="4a95a-133">**Tramite PowerShell**</span><span class="sxs-lookup"><span data-stu-id="4a95a-133">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="4a95a-134">Creare un'entità servizio usando Azure SDK per Node.js</span><span class="sxs-lookup"><span data-stu-id="4a95a-134">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="4a95a-135">Per creare un'entità servizio a livello di codice con JavaScript, usare lo [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="4a95a-135">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="4a95a-136">Uso dell'entità servizio</span><span class="sxs-lookup"><span data-stu-id="4a95a-136">Using the service principal</span></span>

<span data-ttu-id="4a95a-137">Dopo avere creato un'entità servizio, il frammento di codice JavaScript seguente illustra come usare le chiavi dell'entità servizio per l'autenticazione con Azure SDK per Node.js.</span><span class="sxs-lookup"><span data-stu-id="4a95a-137">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="4a95a-138">Modificare i segnaposto seguenti: &lt;clientId or appId>, &lt;secret or password> e &lt;domain or tenant>.</span><span class="sxs-lookup"><span data-stu-id="4a95a-138">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
