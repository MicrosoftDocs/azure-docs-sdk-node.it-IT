---
title: "Creare un'entità servizio di Azure con Node.js"
description: "Informazioni su come Usare l'autenticazione basata su entità servizio tramite Node.js"
keywords: "Azure, Node, SDK, API, autenticazione, active directory, entità servizio"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: faa97e7a9ab6a8b6e04eeee590c7b642d26ba620
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="f50ed-104">Creare un'entità servizio di Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="f50ed-104">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="f50ed-105">Quando un'app deve accedere alle risorse, è possibile configurare un'identità per l'app ed eseguirne l'autenticazione con credenziali specifiche.</span><span class="sxs-lookup"><span data-stu-id="f50ed-105">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="f50ed-106">Questa identità è nota come *entità servizio*.</span><span class="sxs-lookup"><span data-stu-id="f50ed-106">This identity is known as a *service principal*.</span></span> <span data-ttu-id="f50ed-107">Essenzialmente, si creano le chiavi per l'account Azure Active Directory da fornire all'SDK per l'autenticazione invece di richiedere l'intervento dell'utente o il nome utente e la password.</span><span class="sxs-lookup"><span data-stu-id="f50ed-107">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="f50ed-108">L'approccio basato sull'entità servizio consente di:</span><span class="sxs-lookup"><span data-stu-id="f50ed-108">The service principal approach enables you to:</span></span>
- <span data-ttu-id="f50ed-109">Assegnare all'identità dell'app autorizzazioni diverse rispetto a quelle dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f50ed-109">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="f50ed-110">Tali autorizzazioni sono in genere limitate alle specifiche operazioni che devono essere eseguite dall'app.</span><span class="sxs-lookup"><span data-stu-id="f50ed-110">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="f50ed-111">Usare un certificato per l'autenticazione in caso di esecuzione di uno script automatico.</span><span class="sxs-lookup"><span data-stu-id="f50ed-111">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="f50ed-112">Questo argomento illustra tre tecniche per creare un'entità servizio.</span><span class="sxs-lookup"><span data-stu-id="f50ed-112">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="f50ed-113">Portale di Azure</span><span class="sxs-lookup"><span data-stu-id="f50ed-113">Azure portal</span></span>
- <span data-ttu-id="f50ed-114">Interfaccia della riga di comando di Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="f50ed-114">Azure CLI 2.0</span></span>
- <span data-ttu-id="f50ed-115">Azure SDK per Node.js</span><span class="sxs-lookup"><span data-stu-id="f50ed-115">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="f50ed-116">Creare un'entità servizio usando il portale di Azure</span><span class="sxs-lookup"><span data-stu-id="f50ed-116">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="f50ed-117">Seguire i passaggi illustrati nell'argomento [Usare il portale per creare un'applicazione Azure Active Directory e un'entità servizio che possano accedere alle risorse](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) per generare l'entità servizio.</span><span class="sxs-lookup"><span data-stu-id="f50ed-117">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="f50ed-118">Creare un'entità servizio usando l'interfaccia della riga di comando di Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="f50ed-118">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="f50ed-119">Per creare un'entità servizio usando l'[interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2), seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="f50ed-119">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="f50ed-120">Scaricare l'[interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="f50ed-120">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="f50ed-121">Aprire una finestra del terminale.</span><span class="sxs-lookup"><span data-stu-id="f50ed-121">Open a terminal window.</span></span>

3. <span data-ttu-id="f50ed-122">Digitare il comando seguente per avviare il processo di accesso:</span><span class="sxs-lookup"><span data-stu-id="f50ed-122">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="f50ed-123">La chiamata a `az login` restituisce un URL e un codice.</span><span class="sxs-lookup"><span data-stu-id="f50ed-123">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="f50ed-124">Passare all'URL specificato, immettere il codice e accedere con l'identità di Azure. Questa operazione potrebbe venire eseguita automaticamente se l'accesso è già stato eseguito.</span><span class="sxs-lookup"><span data-stu-id="f50ed-124">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="f50ed-125">Sarà quindi possibile accedere all'account tramite l'interfaccia della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="f50ed-125">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="f50ed-126">Ottenere l'ID sottoscrizione e tenant:</span><span class="sxs-lookup"><span data-stu-id="f50ed-126">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="f50ed-127">Il testo seguente è un esempio di output:</span><span class="sxs-lookup"><span data-stu-id="f50ed-127">The following shows an example of the output:</span></span>

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

    <span data-ttu-id="f50ed-128">**Prendere nota dell'ID sottoscrizione, che verrà usato nel passaggio 7.**</span><span class="sxs-lookup"><span data-stu-id="f50ed-128">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="f50ed-129">Creare un'entità servizio per ottenere un oggetto JSON contenente le altre informazioni necessarie per l'autenticazione con Azure.</span><span class="sxs-lookup"><span data-stu-id="f50ed-129">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="f50ed-130">Il testo seguente è un esempio di output:</span><span class="sxs-lookup"><span data-stu-id="f50ed-130">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="f50ed-131">**Prendere nota dei valori di tenant, nome e password, che verranno usati nel passaggio 7.**</span><span class="sxs-lookup"><span data-stu-id="f50ed-131">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="f50ed-132">Configurare le variabili di ambiente sostituendo i segnaposto &lt;subscriptionId>, &lt;tenant>, &lt;name> e &lt;password> con i valori ottenuti nei passaggi 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="f50ed-132">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="f50ed-133">**Tramite Bash**</span><span class="sxs-lookup"><span data-stu-id="f50ed-133">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="f50ed-134">**Uso di PowerShell**</span><span class="sxs-lookup"><span data-stu-id="f50ed-134">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="f50ed-135">Creare un'entità servizio usando Azure SDK per Node.js</span><span class="sxs-lookup"><span data-stu-id="f50ed-135">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="f50ed-136">Per creare un'entità servizio a livello di codice con JavaScript, usare lo [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="f50ed-136">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="f50ed-137">Uso dell'entità servizio</span><span class="sxs-lookup"><span data-stu-id="f50ed-137">Using the service principal</span></span>

<span data-ttu-id="f50ed-138">Dopo avere creato un'entità servizio, il frammento di codice JavaScript seguente illustra come usare le chiavi dell'entità servizio per l'autenticazione con Azure SDK per Node.js.</span><span class="sxs-lookup"><span data-stu-id="f50ed-138">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="f50ed-139">Modificare i segnaposto seguenti: &lt;clientId or appId>, &lt;secret or password> e &lt;domain or tenant>.</span><span class="sxs-lookup"><span data-stu-id="f50ed-139">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

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
