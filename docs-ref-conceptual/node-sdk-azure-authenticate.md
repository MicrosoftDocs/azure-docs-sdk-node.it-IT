---
title: Eseguire l'autenticazione con i moduli di gestione di Azure per Node.js
description: "Eseguire l'autenticazione con un'entità servizio nei moduli di gestione di Azure per Node.js"
keywords: "Azure, Node, SDK, API, autenticazione, active directory, entità servizio"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="e044f-104">Eseguire l'autenticazione con i moduli di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="e044f-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="e044f-105">Tutte le API di un servizio richiedono l'autenticazione tramite un oggetto `credentials` quando ne viene creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="e044f-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="e044f-106">Esistono tre modi per autenticare e creare le credenziali necessarie tramite Azure SDK per Node.js:</span><span class="sxs-lookup"><span data-stu-id="e044f-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="e044f-107">Autenticazione di base</span><span class="sxs-lookup"><span data-stu-id="e044f-107">Basic authentication</span></span>
- <span data-ttu-id="e044f-108">Accesso interattivo</span><span class="sxs-lookup"><span data-stu-id="e044f-108">Interactive login</span></span>
- <span data-ttu-id="e044f-109">Autenticazione di un'entità servizio</span><span class="sxs-lookup"><span data-stu-id="e044f-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="e044f-110">Autenticazione di base</span><span class="sxs-lookup"><span data-stu-id="e044f-110">Basic authentication</span></span>

<span data-ttu-id="e044f-111">Per eseguire l'autenticazione a livello di codice usando le credenziali dell'account Azure, usare la funzione `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="e044f-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="e044f-112">Il frammento di codice JavaScript seguente illustra come usare l'autenticazione di base usando le credenziali archiviate come variabili di ambiente.</span><span class="sxs-lookup"><span data-stu-id="e044f-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="e044f-113">Accesso interattivo</span><span class="sxs-lookup"><span data-stu-id="e044f-113">Interactive login</span></span>

<span data-ttu-id="e044f-114">L'accesso interattivo fornisce un collegamento e un codice che consente all'utente di eseguire l'autenticazione da un browser.</span><span class="sxs-lookup"><span data-stu-id="e044f-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="e044f-115">Usare questo metodo quando più account sono usati dallo stesso script o quando è preferibile l'intervento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="e044f-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="e044f-116">Autenticazione di un'entità servizio</span><span class="sxs-lookup"><span data-stu-id="e044f-116">Service principal authentication</span></span>

<span data-ttu-id="e044f-117">L'[accesso interattivo](#interactive-login) è il modo più semplice per eseguire l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="e044f-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="e044f-118">Quando tuttavia si usa Node.js SDK, è consigliabile usare l'autenticazione basata su entità servizio invece di specificare le credenziali dell'account.</span><span class="sxs-lookup"><span data-stu-id="e044f-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="e044f-119">L'argomento [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md) (Creare un'entità servizio di Azure con Node.js) illustra diverse tecniche per creare (e usare) un'entità servizio.</span><span class="sxs-lookup"><span data-stu-id="e044f-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 