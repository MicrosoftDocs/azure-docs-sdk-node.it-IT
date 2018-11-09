---
title: Librerie di Griglia di eventi di Azure per Node.js
description: Informazioni di riferimento sulle librerie di Griglia di eventi di Azure per Node.js
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2018
ms.locfileid: "51173124"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a>Librerie di Griglia di eventi di Azure per Node.js

È possibile creare applicazioni basate su eventi che rimangono in ascolto e reagiscono a eventi dai servizi di Azure e da origini personalizzate usando la gestione semplice di eventi basati su HTTP con Griglia di eventi di Azure.

[Altre informazioni](/azure/event-grid/overview) su Griglia di eventi di Azure e introduzione all'[esercitazione sugli eventi di archiviazione BLOB di Azure](/azure/storage/blobs/storage-blob-event-quickstart). 

## <a name="publish-sdk"></a>SDK di pubblicazione

Creare eventi, eseguire l'autenticazione e inserire commenti negli argomenti usando l'SDK di pubblicazione di Griglia di eventi di Azure.

### <a name="installation"></a>Installazione

Aggiungere il modulo al progetto con npm:

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a>Codice di esempio

Il segmento di codice seguente pubblica un evento fittizio in un argomento di Griglia di eventi. È possibile recuperare l'endpoint e le chiavi di accesso all'argomento dal portale di Azure o tramite l'interfaccia della riga di comando di Azure:

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

Questo esempio mostra come gestire un evento da Archiviazione di Azure:

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [Esplorare le API client](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a>SDK di gestione

Creare, aggiornare o eliminare istanze, argomenti e sottoscrizioni di Griglia di eventi con l'SDK di gestione.

### <a name="installation"></a>Installazione

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a>Codice di esempio

Il codice seguente crea un argomento `topic1` di Griglia di eventi e restituisce le chiavi di accesso associate all'argomento appena creato.

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [Esplorare le API di gestione](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a>Altre informazioni

- [Receive events using the Event Grid SDK](/azure/event-grid/receive-events) (Ricevere eventi tramite l'SDK di Griglia di eventi)
