---
title: Moduli di Archiviazione di Azure per Node.js
description: Informazioni di riferimento sui moduli di Archiviazione di Azure per Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="def58-103">Moduli di Archiviazione di Azure per Node.js</span><span class="sxs-lookup"><span data-stu-id="def58-103">Azure Storage modules for Node.js</span></span>

<span data-ttu-id="def58-104">Usare il modulo client di Archiviazione di Azure per:</span><span class="sxs-lookup"><span data-stu-id="def58-104">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="def58-105">Leggere e scrivere oggetti e file dall'[archivio BLOB di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span><span class="sxs-lookup"><span data-stu-id="def58-105">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="def58-106">Inviare e ricevere messaggi tra applicazioni connesse al cloud con l'[archiviazione code di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span><span class="sxs-lookup"><span data-stu-id="def58-106">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="def58-107">Leggere e scrivere dati strutturati di grandi dimensioni con l'[archiviazione tabelle di Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span><span class="sxs-lookup"><span data-stu-id="def58-107">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="def58-108">Creare, aggiornare e gestire gli account di archiviazione di Azure, eseguire query e rigenerare chiavi di accesso dalle app Node.js con i moduli di gestione.</span><span class="sxs-lookup"><span data-stu-id="def58-108">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="def58-109">Pacchetto client</span><span class="sxs-lookup"><span data-stu-id="def58-109">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="def58-110">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="def58-110">Install the npm module</span></span>

<span data-ttu-id="def58-111">Installare il modulo npm client di Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="def58-111">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="def58-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="def58-112">Example</span></span>

<span data-ttu-id="def58-113">Questo esempio crea un contenitore di archiviazione e vi carica un file locale `data.txt`.</span><span class="sxs-lookup"><span data-stu-id="def58-113">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="def58-114">Pacchetto di gestione</span><span class="sxs-lookup"><span data-stu-id="def58-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="def58-115">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="def58-115">Install the npm module</span></span> 

<span data-ttu-id="def58-116">Installare il modulo npm di gestione di Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="def58-116">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="def58-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="def58-117">Example</span></span>

<span data-ttu-id="def58-118">Questo esempio elenca gli account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="def58-118">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="def58-119">Esempi</span><span class="sxs-lookup"><span data-stu-id="def58-119">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="def58-120">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="def58-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
