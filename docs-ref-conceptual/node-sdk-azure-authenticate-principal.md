---
title: Creare un'entità servizio di Azure con Node.js
description: Informazioni su come Usare l'autenticazione basata su entità servizio tramite Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 81958e3d928eb2fe7d391044e3242492e54a1011
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220543"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a>Creare un'entità servizio di Azure con Node.js 

Quando un'app deve accedere alle risorse, è possibile configurare un'identità per l'app ed eseguirne l'autenticazione con credenziali specifiche. Questa identità è nota come *entità servizio*. Essenzialmente, si creano le chiavi per l'account Azure Active Directory da fornire all'SDK per l'autenticazione invece di richiedere l'intervento dell'utente o il nome utente e la password.

L'approccio basato sull'entità servizio consente di:
- Assegnare all'identità dell'app autorizzazioni diverse rispetto a quelle dell'utente. Tali autorizzazioni sono in genere limitate alle specifiche operazioni che devono essere eseguite dall'app.
- Usare un certificato per l'autenticazione in caso di esecuzione di uno script automatico.

Questo argomento illustra tre tecniche per creare un'entità servizio.

- Portale di Azure
- Interfaccia della riga di comando di Azure 2.0
- Azure SDK per Node.js

## <a name="create-a-service-principal-using-the-azure-portal"></a>Creare un'entità servizio usando il portale di Azure

Seguire i passaggi illustrati nell'argomento [Usare il portale per creare un'applicazione Azure Active Directory e un'entità servizio che possano accedere alle risorse](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) per generare l'entità servizio.

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>Creare un'entità servizio usando l'interfaccia della riga di comando di Azure 2.0

Per creare un'entità servizio usando l'[interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2), seguire questa procedura:

1. Scaricare l'[interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).

2. Aprire una finestra del terminale.

3. Digitare il comando seguente per avviare il processo di accesso:

    ```shell
    $ az login
    ```

4. La chiamata a `az login` restituisce un URL e un codice. Passare all'URL specificato, immettere il codice e accedere con l'identità di Azure. Questa operazione potrebbe venire eseguita automaticamente se l'accesso è già stato eseguito. Sarà quindi possibile accedere all'account tramite l'interfaccia della riga di comando.

5. Ottenere l'ID sottoscrizione e tenant:

    ```shell
    $ az account list
    ```

    Il testo seguente è un esempio di output:

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    **Prendere nota dell'ID sottoscrizione, che verrà usato nel passaggio 7.**

6. Creare un'entità servizio per ottenere un oggetto JSON contenente le altre informazioni necessarie per l'autenticazione con Azure.

    ```shell
    $ az ad sp create-for-rbac
    ```

    Il testo seguente è un esempio di output:

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **Prendere nota dei valori di tenant, nome e password, che verranno usati nel passaggio 7.**

7. Configurare le variabili di ambiente sostituendo i segnaposto &lt;subscriptionId>, &lt;tenant>, &lt;name> e &lt;password> con i valori ottenuti nei passaggi 4 e 5. 

    **Tramite Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **Tramite PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>Creare un'entità servizio usando Azure SDK per Node.js

Per creare un'entità servizio a livello di codice con JavaScript, usare lo [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).   

## <a name="using-the-service-principal"></a>Uso dell'entità servizio

Dopo avere creato un'entità servizio, il frammento di codice JavaScript seguente illustra come usare le chiavi dell'entità servizio per l'autenticazione con Azure SDK per Node.js. Modificare i segnaposto seguenti: &lt;clientId or appId>, &lt;secret or password> e &lt;domain or tenant>.

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
