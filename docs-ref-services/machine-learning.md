---
title: Moduli di Azure Machine Learning per Node.js
description: Informazioni di riferimento sui moduli di Azure Machine Learning per Node.js
keywords: Azure, SDK, API, Machine Learning, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 465b569d0eef53208211be2c2ff36d28bb28d107
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="39b21-104">Moduli di Azure Machine Learning per Node.js</span><span class="sxs-lookup"><span data-stu-id="39b21-104">Azure Machine Learning modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="39b21-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="39b21-105">Overview</span></span>

<span data-ttu-id="39b21-106">L'apprendimento automatico è una tecnica di analisi scientifica dei dati che consente ai computer di apprendere dai dati esistenti per prevedere comportamenti, risultati e tendenze futuri.</span><span class="sxs-lookup"><span data-stu-id="39b21-106">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="39b21-107">Queste previsioni o stime dell'apprendimento automatico possono rendere più intelligenti le app e i dispositivi.</span><span class="sxs-lookup"><span data-stu-id="39b21-107">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="39b21-108">Quando si effettuano acquisti online, l'apprendimento automatico consente di consigliare altri prodotti che potrebbero interessare in base a ciò che si è acquistato.</span><span class="sxs-lookup"><span data-stu-id="39b21-108">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="39b21-109">Quando si usa la carta di credito, l'apprendimento automatico confronta la transazione con un database di transazioni e consente di rilevare eventuali frodi.</span><span class="sxs-lookup"><span data-stu-id="39b21-109">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="39b21-110">Quando il robot aspirapolvere aspira la polvere in una stanza, l'apprendimento automatico gli consente di decidere se il lavoro è stato completato.</span><span class="sxs-lookup"><span data-stu-id="39b21-110">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="39b21-111">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="39b21-111">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="39b21-112">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="39b21-112">Install the npm module</span></span>

<span data-ttu-id="39b21-113">Installare il modulo npm di Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="39b21-113">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="39b21-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="39b21-114">Example</span></span>

<span data-ttu-id="39b21-115">Questo esempio elenca tutti i piani di impegno di Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="39b21-115">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="39b21-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="39b21-116">Samples</span></span>

<span data-ttu-id="39b21-117">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="39b21-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
