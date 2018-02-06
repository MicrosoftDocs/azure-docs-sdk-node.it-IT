---
title: Strumenti per gli sviluppatori Node.js in Azure | Microsoft Docs
description: Installare i singoli strumenti per lo sviluppo con Node.js in Azure
services: multiple
author: craigshoemaker
manager: routlaw
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 11/07/2017
ms.author: cshoe
ms.openlocfilehash: e9fe95ce6c02d50a70ea51284174c938796148fe
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="azure-tools-for-nodejs-developers"></a><span data-ttu-id="aa0e0-103">Strumenti di Azure per sviluppatori Node.js</span><span class="sxs-lookup"><span data-stu-id="aa0e0-103">Azure tools for Node.js developers</span></span>
<span data-ttu-id="aa0e0-104">Di seguito sono riportati gli strumenti consigliati per lo sviluppo con Azure in Node.js.</span><span class="sxs-lookup"><span data-stu-id="aa0e0-104">The following tools are recommended for developing with Azure on Node.js.</span></span>

## <a name="azure-cli"></a><span data-ttu-id="aa0e0-105">Interfaccia della riga di comando di Azure</span><span class="sxs-lookup"><span data-stu-id="aa0e0-105">Azure CLI</span></span>
<span data-ttu-id="aa0e0-106">L'interfaccia della riga di comando di Azure è ottimizzata per la gestione delle risorse di Azure dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="aa0e0-106">Azure CLI is optimized for managing Azure resources from the command line.</span></span>

![CLI](media/node-azure-tools/cli.png)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="aa0e0-108">Installare l'interfaccia della riga di comando di Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="aa0e0-108">Install the Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)

## <a name="visual-studio-code"></a><span data-ttu-id="aa0e0-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="aa0e0-109">Visual Studio Code</span></span>
<span data-ttu-id="aa0e0-110">È possibile modificare ed eseguire il debug delle app Node.js in qualsiasi sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="aa0e0-110">Edit and debug Node.js apps on any OS.</span></span>

![Visual Studio Code](media/node-azure-tools/vs-code.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="aa0e0-112">Download di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="aa0e0-112">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="azure-extensions"></a><span data-ttu-id="aa0e0-113">Estensioni di Azure</span><span class="sxs-lookup"><span data-stu-id="aa0e0-113">Azure Extensions</span></span>
<span data-ttu-id="aa0e0-114">Per interagire con i servizi di Azure direttamente in Visual Studio Code, usare le estensioni gratuite seguenti.</span><span class="sxs-lookup"><span data-stu-id="aa0e0-114">Use the following free extensions to interface with Azure services directly in Visual Studio Code.</span></span>

| <span data-ttu-id="aa0e0-115">Strumento</span><span class="sxs-lookup"><span data-stu-id="aa0e0-115">Tool</span></span> | <span data-ttu-id="aa0e0-116">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="aa0e0-116">Description</span></span>  |
|:---------:|---------|
| [<span data-ttu-id="aa0e0-117">Funzioni di Azure</span><span class="sxs-lookup"><span data-stu-id="aa0e0-117">Azure Functions</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions) <br> <span data-ttu-id="aa0e0-118">[![Strumenti: Funzioni di Azure](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span><span class="sxs-lookup"><span data-stu-id="aa0e0-118">[![Azure Functions Tools](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span></span> | <span data-ttu-id="aa0e0-119">Creare, gestire, visualizzare e distribuire funzioni ed eseguirne il debug</span><span class="sxs-lookup"><span data-stu-id="aa0e0-119">Create, manage, view, debug, and deploy functions</span></span>|
| [<span data-ttu-id="aa0e0-120">Servizio app di Azure</span><span class="sxs-lookup"><span data-stu-id="aa0e0-120">Azure App Service</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice) <br> <span data-ttu-id="aa0e0-121">[![Strumenti: Servizio app](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span><span class="sxs-lookup"><span data-stu-id="aa0e0-121">[![App Service Tools](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span></span> | <span data-ttu-id="aa0e0-122">Esplorare siti e il portale di Azure, creare nuovi siti (solo Linux in Node.js) ed eseguire la distribuzione in slot</span><span class="sxs-lookup"><span data-stu-id="aa0e0-122">Browse sites and the Azure portal, create new sites (Linux on Node.js only) and deploy to slots</span></span> |
| [<span data-ttu-id="aa0e0-123">Cosmos DB </span><span class="sxs-lookup"><span data-stu-id="aa0e0-123">Cosmos DB </span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)  <br> <span data-ttu-id="aa0e0-124">[![Strumenti: Cosmos DB](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span><span class="sxs-lookup"><span data-stu-id="aa0e0-124">[![Cosmos DB Tools](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span></span>| <span data-ttu-id="aa0e0-125">Creare, esplorare e aggiornare database multimodello distribuiti a livello globale in Azure</span><span class="sxs-lookup"><span data-stu-id="aa0e0-125">Create, browse, and update globally distributed, multi-model databases in Azure</span></span> |
| [<span data-ttu-id="aa0e0-126">Docker</span><span class="sxs-lookup"><span data-stu-id="aa0e0-126">Docker</span></span>](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)   <br> <span data-ttu-id="aa0e0-127">[![Strumenti: Cosmos DB](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span><span class="sxs-lookup"><span data-stu-id="aa0e0-127">[![Cosmos DB Tools](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span></span>| <span data-ttu-id="aa0e0-128">Gestire immagini e contenitori Docker, l'hub Docker e Registro contenitori di Azure</span><span class="sxs-lookup"><span data-stu-id="aa0e0-128">Manage Docker containers and images, Docker Hub, and Azure container registry</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="aa0e0-129">Altre estensioni di Azure nel marketplace per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="aa0e0-129">Get more Azure extensions in the Visual Studio Code marketplace</span></span>](https://marketplace.visualstudio.com/search?term=azure&target=VSCode&category=All%20categories&sortBy=Relevance)