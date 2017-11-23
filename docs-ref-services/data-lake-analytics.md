---
title: Moduli di Azure Data Lake Analytics per Node.js
description: Informazioni di riferimento sui moduli di Azure Data Lake Analytics per Node.js
keywords: Azure, SDK, API, Data Lake Analytics, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 46f414ac6909de5bd956666baf51be1ca9d25ac7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="7412b-104">Moduli di Azure Data Lake Analytics per Node.js</span><span class="sxs-lookup"><span data-stu-id="7412b-104">Azure Data Lake Analytics modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7412b-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="7412b-105">Overview</span></span>
<span data-ttu-id="7412b-106">Azure Data Lake Analytics è un servizio per processi di analisi su richiesta che semplifica l'analisi dei Big Data.</span><span class="sxs-lookup"><span data-stu-id="7412b-106">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="7412b-107">Consente di concentrarsi su scrittura, esecuzione e gestione dei processi invece che sul funzionamento dell'infrastruttura distribuita.</span><span class="sxs-lookup"><span data-stu-id="7412b-107">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="7412b-108">Anziché distribuire, configurare e ottimizzare l'hardware, è possibile scrivere query per trasformare i dati ed estrarre informazioni di interesse.</span><span class="sxs-lookup"><span data-stu-id="7412b-108">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="7412b-109">Con il servizio di analisi è possibile gestire processi di qualsiasi dimensione immediatamente definendo il livello e l'ambito necessari.</span><span class="sxs-lookup"><span data-stu-id="7412b-109">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="7412b-110">Verrà addebitato un costo per il processo solo durante la sua esecuzione, per la massima convenienza.</span><span class="sxs-lookup"><span data-stu-id="7412b-110">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="7412b-111">Il servizio di analisi supporta l'integrazione di Azure Active Directory, che consente di gestire l'accesso e i ruoli, con il sistema di gestione delle identità locale in uso.</span><span class="sxs-lookup"><span data-stu-id="7412b-111">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="7412b-112">È incluso anche U-SQL, un linguaggio che combina i vantaggi di SQL con la potenza espressiva del codice utente.</span><span class="sxs-lookup"><span data-stu-id="7412b-112">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="7412b-113">Il runtime distribuito scalabile di U-SQL permette di analizzare in modo efficiente i dati nell'archivio e nel server SQL in Azure, nel database SQL di Azure e SQL Data Warehouse di Azure.</span><span class="sxs-lookup"><span data-stu-id="7412b-113">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="7412b-114">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="7412b-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7412b-115">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="7412b-115">Install the npm module</span></span>

<span data-ttu-id="7412b-116">Usare npm per installare i moduli di Azure Data Lake Analytics per Node.js</span><span class="sxs-lookup"><span data-stu-id="7412b-116">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="7412b-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="7412b-117">Example</span></span>

<span data-ttu-id="7412b-118">Questo esempio elenca tutti gli account di analisi per una determinata sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="7412b-118">This example lists all of the analytics accounts for a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="7412b-119">Esempi</span><span class="sxs-lookup"><span data-stu-id="7412b-119">Samples</span></span>

<span data-ttu-id="7412b-120">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="7412b-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
