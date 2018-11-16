---
title: Speech SDK di Servizi cognitivi per JavaScript
description: Informazioni di riferimento su Speech SDK di Servizi cognitivi per JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51487906"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Speech SDK di Servizi cognitivi per JavaScript

## <a name="overview"></a>Panoramica

Per semplificare lo sviluppo di applicazioni con funzioni vocali, Microsoft offre Speech SDK, da usare con il [servizio di riconoscimento vocale](https://aka.ms/csspeech).
Speech SDK offre API di riconoscimento vocale e di traduzione vocale native e coerenti.

> [!NOTE]
> Speech SDK di Servizi cognitivi è attualmente disponibile solo per browser.
> Verrà presto offerto un pacchetto NPM.

### <a name="install-the-speech-sdk"></a>Installare Speech SDK

Scaricare Speech SDK come [pacchetto con estensione zip](https://aka.ms/csspeech/jsbrowserpackage) e decomprimerlo.
Verranno così decompressi diversi file, tra cui uno denominato `microsoft.cognitiveservices.speech.sdk.bundle.js`.
Caricare questo file come risorsa script nella pagina Web per iniziare a usare Speech SDK:

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>Esempio 

Il frammento di codice seguente illustra come eseguire semplice riconoscimento vocale dal browser:

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

Vedere la [guida introduttiva dettagliata](/azure/cognitive-services/speech-service/quickstart-js-browser).

## <a name="samples"></a>Esempi

Per altri esempi, esplorare il [repository di esempi di Speech SDK](https://aka.ms/csspeech/samples).
