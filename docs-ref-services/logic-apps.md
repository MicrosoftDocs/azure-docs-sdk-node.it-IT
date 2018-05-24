---
title: Moduli di App per la logica di Azure per Node.js
description: Informazioni di riferimento sui moduli di App per la logica di Azure per Node.js
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 2de867fdd0aa31b63b9680cc3f0c2e7f6301e632
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="e2c13-103">Moduli di App per la logica di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="e2c13-103">Azure Logic Apps modules for Node.js</span></span>

<span data-ttu-id="e2c13-104">Le app per la logica consentono di semplificare e implementare flussi di lavoro e integrazioni scalabili nel cloud.</span><span class="sxs-lookup"><span data-stu-id="e2c13-104">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="e2c13-105">Offrono una finestra di progettazione visiva per modellare e automatizzare il processo come una serie di passaggi definita flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="e2c13-105">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="e2c13-106">Nel cloud e in locale sono disponibili numerosi connettori per una rapida integrazione in servizi e protocolli.</span><span class="sxs-lookup"><span data-stu-id="e2c13-106">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="e2c13-107">Un'app per la logica viene avviata con un trigger (corrispondente ad esempio all'aggiunta di un account a Dynamics CRM) e dopo l'attivazione può avviare molte combinazioni di azioni, conversioni e logica condizionale.</span><span class="sxs-lookup"><span data-stu-id="e2c13-107">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="e2c13-108">Ecco alcuni vantaggi dell'uso delle app per la logica:</span><span class="sxs-lookup"><span data-stu-id="e2c13-108">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="e2c13-109">Risparmio di tempo nella progettazione di processi complessi tramite strumenti di progettazione di facile comprensione</span><span class="sxs-lookup"><span data-stu-id="e2c13-109">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="e2c13-110">Facile implementazione di modelli e flussi di lavoro altrimenti difficili da implementare nel codice</span><span class="sxs-lookup"><span data-stu-id="e2c13-110">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="e2c13-111">Possibilità di iniziare subito la progettazione dai modelli</span><span class="sxs-lookup"><span data-stu-id="e2c13-111">Getting started quickly from templates</span></span>
- <span data-ttu-id="e2c13-112">Personalizzazione dell'app per la logica con API, azioni e codice personalizzati</span><span class="sxs-lookup"><span data-stu-id="e2c13-112">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="e2c13-113">Connessione e sincronizzazione di sistemi diversi in locale e nel cloud</span><span class="sxs-lookup"><span data-stu-id="e2c13-113">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="e2c13-114">Possibilità di sfruttare BizTalk Server, Gestione API, Funzioni di Azure e il bus di servizio di Azure con supporto ottimale dell'integrazione</span><span class="sxs-lookup"><span data-stu-id="e2c13-114">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="e2c13-115">Le app per la logica sono un servizio iPaaS (integration Platform as a Service) completamente gestito che consente agli sviluppatori di evitare di occuparsi di hosting, scalabilità, disponibilità e gestione.</span><span class="sxs-lookup"><span data-stu-id="e2c13-115">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="e2c13-116">Le prestazioni delle app per la logica aumenteranno automaticamente per soddisfare le richieste.</span><span class="sxs-lookup"><span data-stu-id="e2c13-116">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="e2c13-117">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="e2c13-117">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e2c13-118">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="e2c13-118">Install the npm module</span></span>

<span data-ttu-id="e2c13-119">Installare il modulo per la logica di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="e2c13-119">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="e2c13-120">Esempio</span><span class="sxs-lookup"><span data-stu-id="e2c13-120">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="e2c13-121">Esempi</span><span class="sxs-lookup"><span data-stu-id="e2c13-121">Samples</span></span>

<span data-ttu-id="e2c13-122">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="e2c13-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
