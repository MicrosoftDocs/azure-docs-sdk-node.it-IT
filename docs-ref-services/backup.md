---
title: Moduli di Backup di Azure per Node.js
description: Informazioni di riferimento sui moduli di Backup di Azure per Node.js
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 6daeb443c2f1d8560a6a455cb6d174462b483f79
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264644"
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="6a873-103">Moduli di Backup di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="6a873-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6a873-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="6a873-104">Overview</span></span>

<span data-ttu-id="6a873-105">Backup di Azure è il servizio basato su Azure che consente di eseguire il backup, la protezione e il ripristino dei dati in Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="6a873-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="6a873-106">Backup di Azure sostituisce la soluzione di backup locale o esterna esistente con una soluzione basata sul cloud affidabile, sicura e conveniente.</span><span class="sxs-lookup"><span data-stu-id="6a873-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="6a873-107">Backup di Azure offre più componenti che vengono scaricati e distribuiti nel computer o server appropriato o nel cloud.</span><span class="sxs-lookup"><span data-stu-id="6a873-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="6a873-108">Il componente o l'agente distribuito dipende da ciò che si intende proteggere.</span><span class="sxs-lookup"><span data-stu-id="6a873-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="6a873-109">Tutti i componenti di Backup di Azure consentono di eseguire il backup dei dati in un insieme di credenziali di Servizi di ripristino, a prescindere che i dati da proteggere si trovino in locale o nel cloud.</span><span class="sxs-lookup"><span data-stu-id="6a873-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="6a873-110">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="6a873-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="6a873-111">Installare i moduli con npm</span><span class="sxs-lookup"><span data-stu-id="6a873-111">Install the modules with npm</span></span>

<span data-ttu-id="6a873-112">Usare npm per installare i moduli di Backup di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="6a873-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="6a873-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="6a873-113">Example</span></span>

<span data-ttu-id="6a873-114">Questo esempio elenca i processi di ripristino per un determinato insieme di credenziali e gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="6a873-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="6a873-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="6a873-115">Samples</span></span>

<span data-ttu-id="6a873-116">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="6a873-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
