---
title: Moduli di App per la logica di Azure per Node.js
description: Informazioni di riferimento sui moduli di App per la logica di Azure per Node.js
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 021f57c7f4f1b86a3c0e97f345d2f934351669b8
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2018
ms.locfileid: "51111170"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Moduli di App per la logica di Azure per Node.js

Le app per la logica consentono di semplificare e implementare flussi di lavoro e integrazioni scalabili nel cloud. Offrono una finestra di progettazione visiva per modellare e automatizzare il processo come una serie di passaggi definita flusso di lavoro. Nel cloud e in locale sono disponibili numerosi connettori per una rapida integrazione in servizi e protocolli. Un'app per la logica viene avviata con un trigger (corrispondente ad esempio all'aggiunta di un account a Dynamics CRM) e dopo l'attivazione può avviare molte combinazioni di azioni, conversioni e logica condizionale.

Ecco alcuni vantaggi dell'uso delle app per la logica:
- Risparmio di tempo nella progettazione di processi complessi tramite strumenti di progettazione di facile comprensione
- Facile implementazione di modelli e flussi di lavoro altrimenti difficili da implementare nel codice
- Possibilità di iniziare subito la progettazione dai modelli
- Personalizzazione dell'app per la logica con API, azioni e codice personalizzati
- Connessione e sincronizzazione di sistemi diversi in locale e nel cloud
- Possibilità di sfruttare BizTalk Server, Gestione API, Funzioni di Azure e il bus di servizio di Azure con supporto ottimale dell'integrazione

Le app per la logica sono un servizio iPaaS (integration Platform as a Service) completamente gestito che consente agli sviluppatori di evitare di occuparsi di hosting, scalabilità, disponibilità e gestione. Le prestazioni delle app per la logica aumenteranno automaticamente per soddisfare le richieste.

## <a name="management-package"></a>Pacchetto di gestione

### <a name="install-the-npm-module"></a>Installare il modulo npm

Installare il modulo per la logica di Azure per Node.js

```bash
npm install azure-arm-logic
```

### <a name="example"></a>Esempio

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>Esempi

Esplorare altro [codice Node.js di esempio](https://azure.microsoft.com/resources/samples/?platform=nodejs) da usare nelle app.
