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
ms.component: speech-service
ms.openlocfilehash: 43a6921d4ec782287cc041ecaabab4567b0fe677
ms.sourcegitcommit: 74417c10aee8987c3e0343728efac75823c902d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185988"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Speech SDK di Servizi cognitivi per JavaScript

## <a name="overview"></a>Panoramica

Per semplificare lo sviluppo di applicazioni con funzioni vocali, Microsoft offre Speech SDK, da usare con il [servizio di riconoscimento vocale](https://aka.ms/csspeech).
Speech SDK offre API di riconoscimento vocale e di traduzione vocale native e coerenti.

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo npm di Speech SDK di Servizi cognitivi

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a>Esempio 

I frammenti di codice seguente illustrano come eseguire un semplice riconoscimento vocale da un file:

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

Vedere la [guida introduttiva dettagliata](/azure/cognitive-services/speech-service/quickstart-js-node).

## <a name="samples"></a>Esempi

* [Guida introduttiva dettagliata per Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).
* [Guida introduttiva dettagliata per il browser](/azure/cognitive-services/speech-service/quickstart-js-browser).
* Altri esempi sono disponibili nel [repository di esempi di Speech SDK](https://aka.ms/csspeech/samples).
