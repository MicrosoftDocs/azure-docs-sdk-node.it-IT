---
title: Moduli di Servizi cognitivi di Azure per Node.js
description: Informazioni di riferimento sui moduli di Servizi cognitivi di Azure per Node.js
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2018
ms.locfileid: "51071865"
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="c2d4b-103">Moduli di Servizi cognitivi di Azure per JavaScript</span><span class="sxs-lookup"><span data-stu-id="c2d4b-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="c2d4b-104">Moduli di Visione</span><span class="sxs-lookup"><span data-stu-id="c2d4b-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="c2d4b-105">Visione artificiale</span><span class="sxs-lookup"><span data-stu-id="c2d4b-105">Computer Vision</span></span> 

<span data-ttu-id="c2d4b-106">Restituisce informazioni sul contenuto visivo presente in un'immagine:</span><span class="sxs-lookup"><span data-stu-id="c2d4b-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="c2d4b-107">Usare l'aggiunta di tag, le descrizioni e i modelli specifici di un dominio per identificare i contenuti ed etichettarli in tutta sicurezza.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="c2d4b-108">Applicare le impostazioni relative ai contenuti per adulti per limitare automaticamente i contenuti di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="c2d4b-109">Identificare i tipi di immagine e le combinazioni colori nelle immagini.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="c2d4b-110">[Provare Visione artificiale](https://azure.microsoft.com/services/cognitive-services/computer-vision/) gratuitamente nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-110">[Try Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="c2d4b-111">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="c2d4b-112">Vedere [altre informazioni](/azure/cognitive-services/computer-vision/home) sull'API Visione artificiale e la [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript) (Guida introduttiva all'API Visione artificiale per JavaScript).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="c2d4b-113">Content Moderator</span><span class="sxs-lookup"><span data-stu-id="c2d4b-113">Content Moderator</span></span>

<span data-ttu-id="c2d4b-114">Moderazione di testo, video e immagini con supporto di computer, ottimizzata da strumenti di revisione umana.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="c2d4b-115">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="c2d4b-116">[Altre informazioni](/azure/cognitive-services/content-moderator/overview) sul servizio Content Moderator.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="c2d4b-117">API Viso</span><span class="sxs-lookup"><span data-stu-id="c2d4b-117">Face API</span></span>

<span data-ttu-id="c2d4b-118">Rilevare, identificare, analizzare, organizzare e contrassegnare con tag i visi nelle foto.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="c2d4b-119">[Provare l'API Viso](https://azure.microsoft.com/services/cognitive-services/face/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-119">[Try the Face API](https://azure.microsoft.com/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="c2d4b-120">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="c2d4b-121">Vedere [altre informazioni](/azure/cognitive-services/face/overview) sull'API Viso e la [Guida introduttiva all'API Viso per JavaScript](/azure/cognitive-services/Face/quickstarts/javascript).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="c2d4b-122">Moduli di ricerca</span><span class="sxs-lookup"><span data-stu-id="c2d4b-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="c2d4b-123">Ricerca Web</span><span class="sxs-lookup"><span data-stu-id="c2d4b-123">Web search</span></span>

<span data-ttu-id="c2d4b-124">Recuperare documenti Web indicizzati dall'API Ricerca Web Bing e limitare i risultati filtrandoli in base a tipo, aggiornamento e altro.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="c2d4b-125">[Provare l'API Ricerca Web](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-125">[Try the Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="c2d4b-126">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="c2d4b-127">Vedere [altre informazioni](/azure/cognitive-services/bing-web-search/overview) sull'API Ricerca Web Bing e la [Guida introduttiva all'API Ricerca Web per Node.js](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="c2d4b-128">Ricerca di immagini</span><span class="sxs-lookup"><span data-stu-id="c2d4b-128">Image search</span></span>

<span data-ttu-id="c2d4b-129">Cercare immagini e ottenere anteprime, URL di immagini completi, metadati delle immagini e molto altro.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="c2d4b-130">[Provare l'API Ricerca immagini](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-130">[Try the Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="c2d4b-131">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="c2d4b-132">Vedere [altre informazioni](/azure/cognitive-services/bing-image-search/overview) sull'API Ricerca immagini Bing e la [Guida introduttiva all'API Ricerca immagini per Node.js](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="c2d4b-133">Ricerca entità</span><span class="sxs-lookup"><span data-stu-id="c2d4b-133">Entity search</span></span>

<span data-ttu-id="c2d4b-134">Cercare l'entità più pertinente (luogo, persona o oggetto) per un determinato termine di ricerca o luogo.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="c2d4b-135">[Provare l'API Ricerca entità](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="c2d4b-136">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="c2d4b-137">Vedere [altre informazioni](/azure/cognitive-services/bing-entities-search/search-the-web) sull'API Ricerca entità Bing e la [Guida introduttiva all'API Ricerca entità per Node.js](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="c2d4b-138">Ricerca personalizzata</span><span class="sxs-lookup"><span data-stu-id="c2d4b-138">Custom search</span></span>

<span data-ttu-id="c2d4b-139">Compilare una ricerca Web personalizzata in funzione del dominio di ricerca specifico.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="c2d4b-140">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="c2d4b-141">Vedere [altre informazioni](/azure/cognitive-services/bing-custom-search/) sul servizio Ricerca personalizzata Bing e la [Guida introduttiva all'API Ricerca personalizzata per Node.js](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs) per iniziare a eseguire query di ricerca personalizzata dalle app.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="c2d4b-142">Ricerca video</span><span class="sxs-lookup"><span data-stu-id="c2d4b-142">Video search</span></span>

<span data-ttu-id="c2d4b-143">Trovare video nel Web e ottenere risultati con metadati relativi ad autore, codifica, durata e conteggio delle visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="c2d4b-144">[Provare l'API Ricerca video](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="c2d4b-145">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="c2d4b-146">Vedere [altre informazioni](/azure/cognitive-services/bing-video-search/search-the-web) sull'API Ricerca video Bing e la [Guida introduttiva all'API Ricerca video per Node.js](/azure/cognitive-services/bing-video-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="c2d4b-147">Ricerca notizie</span><span class="sxs-lookup"><span data-stu-id="c2d4b-147">News search</span></span>

<span data-ttu-id="c2d4b-148">Cercare articoli di notizie sul Web e usare i metadati relativi ad articoli, notizie correlate, immagini e informazioni del provider.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="c2d4b-149">[Provare l'API Ricerca notizie](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="c2d4b-150">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="c2d4b-151">Vedere [altre informazioni](/azure/cognitive-services/bing-news-search/search-the-web) sull'API Ricerca notizie Bing e la [Guida introduttiva all'API Ricerca notizie per JavaScript](/azure/cognitive-services/bing-news-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="c2d4b-152">Moduli per la lingua</span><span class="sxs-lookup"><span data-stu-id="c2d4b-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="c2d4b-153">Text Analytics</span><span class="sxs-lookup"><span data-stu-id="c2d4b-153">Text Analytics</span></span> 

<span data-ttu-id="c2d4b-154">L'API Analisi del testo è un servizio basato su cloud che fornisce l'elaborazione in linguaggio naturale su testo non elaborato.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="c2d4b-155">L'API include tre funzioni principali:</span><span class="sxs-lookup"><span data-stu-id="c2d4b-155">The API includes three main functions:</span></span>

- <span data-ttu-id="c2d4b-156">Analisi del sentiment</span><span class="sxs-lookup"><span data-stu-id="c2d4b-156">Sentiment analysis</span></span>
- <span data-ttu-id="c2d4b-157">Estrazione di frasi chiave</span><span class="sxs-lookup"><span data-stu-id="c2d4b-157">Key phrase extraction</span></span>
- <span data-ttu-id="c2d4b-158">Rilevamento della lingua</span><span class="sxs-lookup"><span data-stu-id="c2d4b-158">Language detection</span></span>

<span data-ttu-id="c2d4b-159">[Provare l'API Analisi del testo](https://azure.microsoft.com/services/cognitive-services/text-analytics/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-159">[Try the Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="c2d4b-160">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="c2d4b-161">Vedere [altre informazioni](/azure/cognitive-services/text-analytics/overview) sull'API Analisi del testo e la [Guida introduttiva all'API Analisi del testo per Node.js](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="c2d4b-162">Controllo ortografico</span><span class="sxs-lookup"><span data-stu-id="c2d4b-162">Spell Check</span></span>

<span data-ttu-id="c2d4b-163">Eseguire il controllo grammaticale e ortografico contestuale con l'API Controllo ortografico Bing.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="c2d4b-164">[Provare l'API Controllo ortografico](https://azure.microsoft.com/services/cognitive-services/spell-check/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-164">[Try the Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="c2d4b-165">Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="c2d4b-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="c2d4b-166">Vedere [altre informazioni](/azure/cognitive-services/bing-spell-check/proof-text) sull'API Controllo ortografico e la [Guida introduttiva all'API Controllo ortografico per Node.js](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="c2d4b-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="c2d4b-167">Esempi</span><span class="sxs-lookup"><span data-stu-id="c2d4b-167">Samples</span></span>

<span data-ttu-id="c2d4b-168">Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.</span><span class="sxs-lookup"><span data-stu-id="c2d4b-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
