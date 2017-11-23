---
title: Moduli di Archiviazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di Archiviazione di Azure per Node.js
keywords: Azure, Node, SDK, API, archiviazione, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="374a0-104">Moduli di Archiviazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="374a0-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="374a0-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="374a0-105">Overview</span></span>

<span data-ttu-id="374a0-106">Usare il modulo client di Archiviazione di Azure per:</span><span class="sxs-lookup"><span data-stu-id="374a0-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="374a0-107">Leggere e scrivere oggetti e file dall'[archivio BLOB di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span><span class="sxs-lookup"><span data-stu-id="374a0-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="374a0-108">Inviare e ricevere messaggi tra applicazioni connesse al cloud con l'[archiviazione code di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span><span class="sxs-lookup"><span data-stu-id="374a0-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="374a0-109">Leggere e scrivere dati strutturati di grandi dimensioni con l'[archiviazione tabelle di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span><span class="sxs-lookup"><span data-stu-id="374a0-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="374a0-110">Creare, aggiornare e gestire gli account di archiviazione di Azure, eseguire query e rigenerare chiavi di accesso dalle app Node.js con i moduli di gestione.</span><span class="sxs-lookup"><span data-stu-id="374a0-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="374a0-111">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="374a0-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="374a0-112">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="374a0-112">Install the npm module</span></span>

<span data-ttu-id="374a0-113">Installare il modulo npm client di Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="374a0-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="374a0-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="374a0-114">Example</span></span>

<span data-ttu-id="374a0-115">Questo esempio crea un contenitore di archiviazione e vi carica un file locale `data.txt`.</span><span class="sxs-lookup"><span data-stu-id="374a0-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a><span data-ttu-id="374a0-116">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="374a0-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="374a0-117">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="374a0-117">Install the npm module</span></span> 

<span data-ttu-id="374a0-118">Installare il modulo npm di gestione di Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="374a0-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="374a0-119">Esempio</span><span class="sxs-lookup"><span data-stu-id="374a0-119">Example</span></span>

<span data-ttu-id="374a0-120">Questo esempio elenca gli account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="374a0-120">This example list the storage accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="374a0-121">Esempi</span><span class="sxs-lookup"><span data-stu-id="374a0-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="374a0-122">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="374a0-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
