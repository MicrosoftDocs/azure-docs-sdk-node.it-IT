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
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49027435"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="b24cc-103">Speech SDK di Servizi cognitivi per JavaScript</span><span class="sxs-lookup"><span data-stu-id="b24cc-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="b24cc-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="b24cc-104">Overview</span></span>

<span data-ttu-id="b24cc-105">Per semplificare lo sviluppo di applicazioni con funzioni vocali, Microsoft offre Speech SDK, da usare con il [servizio di riconoscimento vocale](https://aka.ms/csspeech).</span><span class="sxs-lookup"><span data-stu-id="b24cc-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="b24cc-106">Speech SDK offre API di riconoscimento vocale e di traduzione vocale native e coerenti.</span><span class="sxs-lookup"><span data-stu-id="b24cc-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="b24cc-107">Speech SDK di Servizi cognitivi è attualmente disponibile solo per browser.</span><span class="sxs-lookup"><span data-stu-id="b24cc-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="b24cc-108">Verrà presto offerto un pacchetto NPM.</span><span class="sxs-lookup"><span data-stu-id="b24cc-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="b24cc-109">Installare Speech SDK</span><span class="sxs-lookup"><span data-stu-id="b24cc-109">Install the Speech SDK</span></span>

<span data-ttu-id="b24cc-110">Scaricare Speech SDK come [pacchetto con estensione zip](https://aka.ms/csspeech/jsbrowserpackage) e decomprimerlo.</span><span class="sxs-lookup"><span data-stu-id="b24cc-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="b24cc-111">Verranno così decompressi diversi file, tra cui uno denominato `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span><span class="sxs-lookup"><span data-stu-id="b24cc-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="b24cc-112">Caricare questo file come risorsa script nella pagina Web per iniziare a usare Speech SDK:</span><span class="sxs-lookup"><span data-stu-id="b24cc-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="b24cc-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="b24cc-113">Example</span></span> 

<span data-ttu-id="b24cc-114">Il frammento di codice seguente illustra come eseguire semplice riconoscimento vocale dal browser:</span><span class="sxs-lookup"><span data-stu-id="b24cc-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

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

<span data-ttu-id="b24cc-115">Vedere la [guida introduttiva dettagliata](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="b24cc-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="b24cc-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="b24cc-116">Samples</span></span>

<span data-ttu-id="b24cc-117">Per altri esempi, esplorare il [repository di esempi di Speech SDK](https://aka.ms/csspeech/samples).</span><span class="sxs-lookup"><span data-stu-id="b24cc-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
