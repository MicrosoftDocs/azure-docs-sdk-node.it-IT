---
title: Speech SDK di Servizi cognitivi per JavaScript
description: Informazioni di riferimento su Speech SDK di Servizi cognitivi per JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.subservice: speech-service
ms.openlocfilehash: b1375b6beb478cab2475539c03b6bac9f0ea99e0
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052575"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="170d6-103">Speech SDK di Servizi cognitivi per JavaScript</span><span class="sxs-lookup"><span data-stu-id="170d6-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="170d6-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="170d6-104">Overview</span></span>

<span data-ttu-id="170d6-105">Per semplificare lo sviluppo di applicazioni con funzioni vocali, Microsoft offre Speech SDK, da usare con il [servizio di riconoscimento vocale](https://aka.ms/csspeech).</span><span class="sxs-lookup"><span data-stu-id="170d6-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="170d6-106">Speech SDK offre API di riconoscimento vocale e di traduzione vocale native e coerenti.</span><span class="sxs-lookup"><span data-stu-id="170d6-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="170d6-107">Installare il modulo npm</span><span class="sxs-lookup"><span data-stu-id="170d6-107">Install the npm module</span></span>

<span data-ttu-id="170d6-108">Installare il modulo npm di Speech SDK di Servizi cognitivi</span><span class="sxs-lookup"><span data-stu-id="170d6-108">Install the Cognitive Services Speech SDK npm module</span></span>

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a><span data-ttu-id="170d6-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="170d6-109">Example</span></span> 

<span data-ttu-id="170d6-110">I frammenti di codice seguente illustrano come eseguire un semplice riconoscimento vocale da un file:</span><span class="sxs-lookup"><span data-stu-id="170d6-110">The following code snippets illustrates how to do simple speech recognition from a file:</span></span>

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

<span data-ttu-id="170d6-111">Vedere la [guida introduttiva dettagliata](/azure/cognitive-services/speech-service/quickstart-js-node).</span><span class="sxs-lookup"><span data-stu-id="170d6-111">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>

## <a name="samples"></a><span data-ttu-id="170d6-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="170d6-112">Samples</span></span>

* <span data-ttu-id="170d6-113">[Guida introduttiva dettagliata per Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span><span class="sxs-lookup"><span data-stu-id="170d6-113">[Step-by-step quickstart for Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>
* <span data-ttu-id="170d6-114">[Guida introduttiva dettagliata per il browser](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="170d6-114">[Step-by-step quickstart for the browser](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>
* <span data-ttu-id="170d6-115">Altri esempi sono disponibili nel [repository di esempi di Speech SDK](https://aka.ms/csspeech/samples).</span><span class="sxs-lookup"><span data-stu-id="170d6-115">More samples can be found in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
