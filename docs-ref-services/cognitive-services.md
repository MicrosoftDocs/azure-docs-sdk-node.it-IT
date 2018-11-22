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
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2018
ms.locfileid: "52144900"
---
# <a name="javascript-azure-cognitive-services-modules"></a>Moduli di Servizi cognitivi di Azure per JavaScript

## <a name="vision-modules"></a>Moduli di Visione

### <a name="computer-vision"></a>Visione artificiale 

Restituisce informazioni sul contenuto visivo presente in un'immagine:

- Usare l'aggiunta di tag, le descrizioni e i modelli specifici di un dominio per identificare i contenuti ed etichettarli in tutta sicurezza.
- Applicare le impostazioni relative ai contenuti per adulti per limitare automaticamente i contenuti di questo tipo.
- Identificare i tipi di immagine e le combinazioni colori nelle immagini.

[Provare Visione artificiale](https://azure.microsoft.com/services/cognitive-services/computer-vision/) gratuitamente nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-computervision
```

Vedere [altre informazioni](/azure/cognitive-services/computer-vision/home) sull'API Visione artificiale e la [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript) (Guida introduttiva all'API Visione artificiale per JavaScript).

### <a name="content-moderator"></a>Content Moderator

Moderazione di testo, video e immagini con supporto di computer, ottimizzata da strumenti di revisione umana.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-contentmoderator
```

[Altre informazioni](/azure/cognitive-services/content-moderator/overview) sul servizio Content Moderator.

### <a name="face-api"></a>API Viso

Rilevare, identificare, analizzare, organizzare e contrassegnare con tag i visi nelle foto. 

[Provare l'API Viso](https://azure.microsoft.com/services/cognitive-services/face/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-face
```

Vedere [altre informazioni](/azure/cognitive-services/face/overview) sull'API Viso e la [Guida introduttiva all'API Viso per JavaScript](/azure/cognitive-services/Face/quickstarts/javascript).

## <a name="search-modules"></a>Moduli di ricerca

### <a name="web-search"></a>Ricerca Web

Recuperare documenti Web indicizzati dall'API Ricerca Web Bing e limitare i risultati filtrandoli in base a tipo, aggiornamento e altro. 

[Provare l'API Ricerca Web](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-websearch
```

Vedere [altre informazioni](/azure/cognitive-services/bing-web-search/overview) sull'API Ricerca Web Bing e la [Guida introduttiva all'API Ricerca Web per Node.js](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).

### <a name="image-search"></a>Ricerca di immagini

Cercare immagini e ottenere anteprime, URL di immagini completi, metadati delle immagini e molto altro.

[Provare l'API Ricerca immagini](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-imagesearch
```

Vedere [altre informazioni](/azure/cognitive-services/bing-image-search/overview) sull'API Ricerca immagini Bing e la [Guida introduttiva all'API Ricerca immagini per Node.js](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).


### <a name="entity-search"></a>Ricerca entità

Cercare l'entità più pertinente (luogo, persona o oggetto) per un determinato termine di ricerca o luogo.

[Provare l'API Ricerca entità](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-entitysearch
```

Vedere [altre informazioni](/azure/cognitive-services/bing-entities-search/search-the-web) sull'API Ricerca entità Bing e la [Guida introduttiva all'API Ricerca entità per Node.js](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).

### <a name="custom-search"></a>Ricerca personalizzata

Compilare una ricerca Web personalizzata in funzione del dominio di ricerca specifico.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-customsearch
```

Vedere [altre informazioni](/azure/cognitive-services/bing-custom-search/) sul servizio Ricerca personalizzata Bing e la [Guida introduttiva all'API Ricerca personalizzata per Node.js](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs) per iniziare a eseguire query di ricerca personalizzata dalle app.

### <a name="video-search"></a>Ricerca video

Trovare video nel Web e ottenere risultati con metadati relativi ad autore, codifica, durata e conteggio delle visualizzazioni.

[Provare l'API Ricerca video](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-videosearch
```

Vedere [altre informazioni](/azure/cognitive-services/bing-video-search/search-the-web) sull'API Ricerca video Bing e la [Guida introduttiva all'API Ricerca video per Node.js](/azure/cognitive-services/bing-video-search/nodejs).


### <a name="news-search"></a>Ricerca notizie

Cercare articoli di notizie sul Web e usare i metadati relativi ad articoli, notizie correlate, immagini e informazioni del provider.

[Provare l'API Ricerca notizie](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-newssearch
```

Vedere [altre informazioni](/azure/cognitive-services/bing-news-search/search-the-web) sull'API Ricerca notizie Bing e la [Guida introduttiva all'API Ricerca notizie per JavaScript](/azure/cognitive-services/bing-news-search/nodejs).


## <a name="language-modules"></a>Moduli per la lingua

### <a name="text-analytics"></a>Text Analytics 

L'API Analisi del testo è un servizio basato su cloud che fornisce l'elaborazione in linguaggio naturale su testo non elaborato. L'API include tre funzioni principali:

- Analisi del sentiment
- Estrazione di frasi chiave
- Rilevamento della lingua

[Provare l'API Analisi del testo](https://azure.microsoft.com/services/cognitive-services/text-analytics/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-textanalytics
```

Vedere [altre informazioni](/azure/cognitive-services/text-analytics/overview) sull'API Analisi del testo e la [Guida introduttiva all'API Analisi del testo per Node.js](/azure/cognitive-services/text-analytics/quickstarts/nodejs).


### <a name="spell-check"></a>Controllo ortografico

Eseguire il controllo grammaticale e ortografico contestuale con l'API Controllo ortografico Bing.

[Provare l'API Controllo ortografico](https://azure.microsoft.com/services/cognitive-services/spell-check/) nel browser.

Ottenere il modulo JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-spellcheck
```

Vedere [altre informazioni](/azure/cognitive-services/bing-spell-check/proof-text) sull'API Controllo ortografico e la [Guida introduttiva all'API Controllo ortografico per Node.js](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).

## <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
