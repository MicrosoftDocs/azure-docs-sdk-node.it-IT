---
title: Moduli di Automazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di Automazione di Azure per Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: f364bb09c97c1262f640a4b48514c6abaee5f14a
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52154896"
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="4811a-103">Moduli di Automazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="4811a-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4811a-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="4811a-104">Overview</span></span>

<span data-ttu-id="4811a-105">Automazione di Azure offre agli utenti la possibilità di automatizzare le attività manuali, a esecuzione prolungata, soggette a errori e ripetute di frequente comunemente eseguite negli ambienti cloud e aziendali.</span><span class="sxs-lookup"><span data-stu-id="4811a-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="4811a-106">Automazione consente di risparmiare tempo e aumenta l'affidabilità delle normali attività amministrative e le pianifica anche per essere eseguite automaticamente a intervalli regolari.</span><span class="sxs-lookup"><span data-stu-id="4811a-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="4811a-107">È possibile automatizzare i processi utilizzando runbook o automatizzare la gestione della configurazione tramite Configurazione dello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="4811a-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="4811a-108">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="4811a-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="4811a-109">Installare i moduli con npm</span><span class="sxs-lookup"><span data-stu-id="4811a-109">Install the modules with npm</span></span>

<span data-ttu-id="4811a-110">Usare npm per installare i moduli di Automazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="4811a-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="4811a-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="4811a-111">Example</span></span>

<span data-ttu-id="4811a-112">Questo esempio elenca gli account di Automazione.</span><span class="sxs-lookup"><span data-stu-id="4811a-112">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="4811a-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="4811a-113">Samples</span></span>

<span data-ttu-id="4811a-114">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="4811a-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
