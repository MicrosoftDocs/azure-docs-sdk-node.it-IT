---
title: Moduli di autorizzazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di autorizzazione di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 6fbaaeba28cac81d360e93c5066791adfa51bcd5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="453f2-103">Moduli di autorizzazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="453f2-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="453f2-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="453f2-104">Overview</span></span>

<span data-ttu-id="453f2-105">La funzionalità di autenticazione/autorizzazione del servizio app di Azure consente all'applicazione di eseguire la procedura di accesso degli utenti in modo che non sia necessario modificare il codice nel back-end dell'app.</span><span class="sxs-lookup"><span data-stu-id="453f2-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="453f2-106">L'autorizzazione fornisce un modo semplice per proteggere l'applicazione e lavorare con i dati per utente.</span><span class="sxs-lookup"><span data-stu-id="453f2-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="453f2-107">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="453f2-107">Management package</span></span>

<span data-ttu-id="453f2-108">Usare npm per installare i moduli di autorizzazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="453f2-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="453f2-109">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="453f2-109">Install the npm module</span></span>

<span data-ttu-id="453f2-110">Installare il modulo npm di autorizzazione di Azure</span><span class="sxs-lookup"><span data-stu-id="453f2-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="453f2-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="453f2-111">Example</span></span>

<span data-ttu-id="453f2-112">Questo esempio elenca tutte le assegnazioni di ruolo per il gruppo di risorse richiesto.</span><span class="sxs-lookup"><span data-stu-id="453f2-112">This example lists all role assignments for the requested resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a><span data-ttu-id="453f2-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="453f2-113">Samples</span></span>

<span data-ttu-id="453f2-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="453f2-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
