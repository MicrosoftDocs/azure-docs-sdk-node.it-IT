---
title: Eseguire l'autenticazione con i moduli di gestione di Azure per Node.js
description: Eseguire l'autenticazione con un'entità servizio nei moduli di gestione di Azure per Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: b665c537bf17d08c44357009552054d6b2e609d2
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220513"
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="10d88-103">Eseguire l'autenticazione con i moduli di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="10d88-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="10d88-104">Tutte le API di un servizio richiedono l'autenticazione tramite un oggetto `credentials` quando ne viene creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="10d88-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="10d88-105">Esistono tre modi per autenticare e creare le credenziali necessarie tramite Azure SDK per Node.js:</span><span class="sxs-lookup"><span data-stu-id="10d88-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="10d88-106">Autenticazione di base</span><span class="sxs-lookup"><span data-stu-id="10d88-106">Basic authentication</span></span>
- <span data-ttu-id="10d88-107">Accesso interattivo</span><span class="sxs-lookup"><span data-stu-id="10d88-107">Interactive login</span></span>
- <span data-ttu-id="10d88-108">Autenticazione di un'entità servizio</span><span class="sxs-lookup"><span data-stu-id="10d88-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="10d88-109">Autenticazione di base</span><span class="sxs-lookup"><span data-stu-id="10d88-109">Basic authentication</span></span>

<span data-ttu-id="10d88-110">Per eseguire l'autenticazione a livello di codice usando le credenziali dell'account Azure, usare la funzione `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="10d88-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="10d88-111">Il frammento di codice JavaScript seguente illustra come usare l'autenticazione di base usando le credenziali archiviate come variabili di ambiente.</span><span class="sxs-lookup"><span data-stu-id="10d88-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="10d88-112">Accesso interattivo</span><span class="sxs-lookup"><span data-stu-id="10d88-112">Interactive login</span></span>

<span data-ttu-id="10d88-113">L'accesso interattivo fornisce un collegamento e un codice che consente all'utente di eseguire l'autenticazione da un browser.</span><span class="sxs-lookup"><span data-stu-id="10d88-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="10d88-114">Usare questo metodo quando più account sono usati dallo stesso script o quando è preferibile l'intervento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="10d88-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="10d88-115">Autenticazione di un'entità servizio</span><span class="sxs-lookup"><span data-stu-id="10d88-115">Service principal authentication</span></span>

<span data-ttu-id="10d88-116">L'[accesso interattivo](#interactive-login) è il modo più semplice per eseguire l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="10d88-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="10d88-117">Quando tuttavia si usa Node.js SDK, è consigliabile usare l'autenticazione basata su entità servizio invece di specificare le credenziali dell'account.</span><span class="sxs-lookup"><span data-stu-id="10d88-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="10d88-118">L'argomento [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md) (Creare un'entità servizio di Azure con Node.js) illustra diverse tecniche per creare (e usare) un'entità servizio.</span><span class="sxs-lookup"><span data-stu-id="10d88-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 