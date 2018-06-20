---
title: Sviluppo di Node.js con Visual Studio Code e Azure
description: Completare l'esercitazione end-to-end che illustra come creare un'app Node.js, creare un contenitore Docker dall'app e distribuire l'app in Azure
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2017
ms.locfileid: "20908141"
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a>Sviluppo di Node.js con Visual Studio Code e Azure

Questa esercitazione illustra la creazione di un contenitore Docker da un'app Node.js esistente e la distribuzione dell'app in Azure con Visual Studio Code.

L'esercitazione usa una semplice app Todo creata e pubblicata da [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular). Si tratta di un'app MEAN a singola pagina e quindi usa MongoDB come database, Node/Express per il server Web/API REST e Angular.js 1. x per l'interfaccia front-end. 

## <a name="prerequisites"></a>Prerequisiti

Per seguire la demo è necessario avere installato il software seguente:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker)
- [Account DockerHub](https://hub.docker.com/)
- [Interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [Account di Azure](https://azure.microsoft.com/free/)
- [Yarn](https://yarnpkg.com/en/docs/install)
- [Chrome](https://www.google.com/chrome/browser/desktop/): usato per il debug del front-end dell'app demo.
- MongoDB: poiché l'app demo usa MongoDB, è necessaria un'istanza di MongoDB locale in ascolto sulla porta `27017` standard. Il modo più semplice per ottenere questo risultato è eseguire questi due comandi dopo l'installazione di Docker: `docker pull mongo` seguito da `docker run -it -p 27017:27017 mongo`.

## <a name="project-setup"></a>Configurazione del progetto

Per iniziare, scaricare il progetto di esempio usando la procedura seguente:

1. Aprire Visual Studio Code.

1. Premere **&lt;F1>** per visualizzare il riquadro comandi.

1. Al prompt del riquadro comandi immettere `gitcl`, selezionare il comando **Git: Clone** e premere **&lt;Invio>**.

    ![Comando gitcl nel prompt del riquadro comandi di Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. Quando viene richiesto l'**URL del repository**, immettere `https://github.com/scotch-io/node-todo`, quindi premere **&lt;Invio>**.

1. Selezionare o creare la directory locale in cui si vuole clonare il progetto.

    ![Esplora risorse di Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a>Terminale integrato

Trattandosi di un progetto Node.js, è prima di tutto necessario verificare che tutte le dipendenze del progetto siano installate da npm.  

1. Premere  **&lt;Ctrl>'** per visualizzare il terminale integrato di Visual Studio Code. 

1. Digitare `yarn` e premere **&lt;Invio>**.  

    ![Esecuzione del comando yarn in Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a>Controllo della versione integrato Git

Dopo l'installazione delle dipendenze dell'app tramite Yarn, viene creato un file `yarn.lock` che consente di riacquisire in modo prevedibile le stesse identiche dipendenze in futuro, senza eventi imprevisti nelle compilazioni CI (integrazione continua), nelle distribuzioni di produzione o in altri computer di sviluppo.

La procedura seguente illustra come verificare il file `yarn.lock` nel controllo del codice sorgente:

1. In Visual Studio Code passare alla scheda integrata Git, ovvero la scheda con il logo Git.

1. Nella casella **Messaggio**, immettere un messaggio di commit e premere **&lt;Ctrl>&lt;Invio>**. 

    ![Aggiunta del file yarn.lock a Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a>Esplorazione del progetto e del codice

Per orientarsi nella base di codici, si esamineranno alcuni esempi di funzionalità di esplorazione messe a disposizione da Visual Studio Code.

1. Premere **&lt;Ctrl>P**.

1. Immettere `.js` per visualizzare tutti i file JSON/JavaScript presenti nel progetto e la directory padre di ogni file 

    ![Visualizzare tutti i file con estensione js](./media/node-howto-e2e/git-output.png)

1. Selezionare `server.js`, ovvero lo script di avvio dell'app. 

1. Posizionare il mouse sulla variabile **database** importata alla riga 6 per visualizzarne il tipo. La possibilità di analizzare rapidamente variabili, moduli e tipi in un file è molto utile durante lo sviluppo dei progetti. 

    ![Individuare il tipo](./media/node-howto-e2e/hover-help.png)

1. Facendo clic all'interno di una variabile, ad esempio **database**, è possibile vedere tutti i riferimenti a tale variabile presenti nello stesso file. Per visualizzare tutti i riferimenti a una variabile nel progetto, fare clic con il pulsante destro del mouse sulla variabile e dal menu di scelta rapida scegliere **Trova tutti i riferimenti**.

    ![Trovare i riferimenti a una variabile](./media/node-howto-e2e/word-hilight.png)

1. Oltre a passare il mouse su una variabile per individuarne il tipo, è possibile esaminare la definizione di una variabile, anche se si trova in un altro file. Per visualizzare questa azione, fare clic con il pulsante destro del mouse su **database.localUrl** (riga 12) e quindi scegliere **Visualizza definizione** dal menu di scelta rapida. 

    ![Visualizzare la definizione di una variabile](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a>Modifica del codice e uso del completamento automatico

La stringa di connessione di MongoDB è hardcoded nella dichiarazione di **database.localUrl**. In questa sezione verrà modificato il codice per recuperare la stringa di connessione da una variabile di ambiente e verranno illustrate informazioni sulla funzionalità di completamento automatico di Visual Studio Code.  

1. Aprire il file `server.js`

1. Sostituire il codice seguente: 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    con questo codice:

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

Si noti che se si immette il codice manualmente (invece di copiarlo e incollarlo), quando si digita il punto dopo `process`, Visual Studio Code visualizza i membri disponibili dell'API globale **process** di Node.js.

![Il completamento automatico visualizza automaticamente i membri di un'API](./media/node-howto-e2e/process-env.png)

Il completamento automatico funziona perché Visual Studio Code usa TypeScript in background, anche per JavaScript, per fornire informazioni sui tipi che possono quindi essere usate per l'elenco di completamento durante la digitazione. Visual Studio Code può rilevare che si tratta di un progetto di Node.js e quindi scarica automaticamente il file delle definizioni di tipi TypeScript per [Node.js da NPM](https://www.npmjs.com/package/@types/node). Il file delle definizioni di tipi consente di ottenere il completamento automatico per altre variabili globali Node.js, ad esempio **Buffer** e **setTimeout**, oltre a tutti i moduli predefiniti, ad esempio **fs** e **http**.

Oltre alle API di Node.js predefinite, questa acquisizione automatica di definizioni di tipi funziona anche per oltre 2.000 moduli di terze parti, ad esempio React, Underscore ed Express. Ad esempio, per impedire a Mongoose di arrestare l'app di esempio in modo anomalo se non riesce a connettersi all'istanza di database MongoDB configurata, inserire la riga di codice seguente alla riga 13:

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

Come con il codice precedente, si noterà che il completamento automatico funziona senza operazioni aggiuntive da parte dell'utente.

![Il completamento automatico visualizza automaticamente i membri di un'API](./media/node-howto-e2e/mongoose.png)

È possibile vedere quali moduli supportano questa funzionalità di completamento automatico esplorando il progetto [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), che rappresenta la fonte gestita dalla community di tutte le definizioni di tipi TypeScript.

## <a name="running-the-app"></a>Esecuzione dell'app

Dopo aver esaminato il codice, eseguire l'app. Per eseguire l'app da Visual Studio Code premere **&lt;F5>**. Quando si esegue il codice tramite  **&lt;F5>** (modalità di debug), Visual Studio Code avvia l'app e visualizza la finestra **Console di debug** con il canale stdout per l'app.

![Monitoraggio di stdout di un'app tramite la console di debug](./media/node-howto-e2e/console.png)

La **console di debug** è collegata all'app appena avviata, quindi è possibile digitare espressioni JavaScript che verranno valutate nell'app. È anche disponibile il completamento automatico. Per un esempio pratico, digitare `process.env` nella console:

![Immissione del codice nella console di debug](./media/node-howto-e2e/console-code.png)

È stato possibile premere **&lt;F5>** per eseguire l'app perché il file attualmente aperto è un file JavaScript (`server.js`). Di conseguenza, Visual Studio Code presuppone che il progetto sia un'app Node.js. Se si chiudono tutti i file JavaScript in Visual Studio Code e quindi si preme **&lt;F5>**, Visual Studio Code chiederà di specificare l'ambiente:

![Indicazione dell'ambiente di runtime](./media/node-howto-e2e/select-env.png)

Aprire un browser e passare a `http://localhost:8080` per vedere l'app in esecuzione. Digitare un messaggio nella casella di testo e aggiungere/rimuovere alcuni elementi Todo per avere un'idea del funzionamento dell'app.

![App Todo in esecuzione](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a>Debug

Oltre a poter eseguire l'app e interagire con essa tramite la console integrata, Visual Studio Code consente di impostare punti di interruzione direttamente all'interno del codice. Premere ad esempio **&lt;Ctrl>P** per visualizzare la selezione file. Dopo aver visualizzato la selezione file, digitare `route` e selezionare il file `route.js`.

Impostare un punto di interruzione alla riga 28, che rappresenta la route Express che viene chiamata quando l'applicazione prova ad aggiungere una voce Todo. Per impostare un punto di interruzione è sufficiente fare clic sull'area a sinistra del numero di riga nell'editor come illustrato nell'immagine seguente.

![Impostazione di un punto di interruzione in Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> Oltre ai punti di interruzione standard, Visual Studio Code supporta punti di interruzione condizionali che consentono di definire quando l'app deve sospendere l'esecuzione. Per impostare un punto di interruzione condizionale, fare clic con il pulsante destro del mouse a sinistra della riga in cui si vuole sospendere l'esecuzione, selezionare **Aggiungi punto di interruzione condizionale** e specificare un'espressione JavaScript (ad esempio `foo = "bar"`) o il conteggio esecuzioni che definisce la condizione che determina la sospensione dell'esecuzione.
> 
> 

Dopo aver impostato il punto di interruzione, tornare all'app in esecuzione e aggiungere una voce Todo. Con l'aggiunta di una voce Todo, l'app sospende immediatamente l'esecuzione alla riga 28 in cui è stato impostato il punto di interruzione:

![Visual Studio Code sospende l'esecuzione nel punto di interruzione](./media/node-howto-e2e/debugger.png)

Quando l'applicazione è stata sospesa, è possibile passare il puntatore del mouse sulle espressioni del codice per visualizzare il relativo valore corrente, controllare le variabili locali o le espressioni di controllo e lo stack di chiamate e usare la barra degli strumenti di debug per scorrere l'esecuzione del codice. Premere  **&lt;F5>** per riprendere l'esecuzione dell'app.

## <a name="full-stack-debugging"></a>Debug dello stack completo

Come accennato in precedenza in questo argomento, l'app TODO è un'app MEAN, ovvero sia il front-end che il back-end sono scritti in JavaScript. Anche se quindi si esegue attualmente il debug del codice di back-end (Node/Express), a un certo punto potrebbe essere necessario eseguire il debug del codice di front-end (Angular). A tale scopo, Visual Studio Code mette a disposizione un vastissimo ecosistema di estensioni, incluso il debug di Chrome integrato.

Passare alla scheda **Estensioni** e digitare `chrome` nella casella di ricerca:

![Estensione di debug di Chrome per Visual Studio Code](./media/node-howto-e2e/chrome.png)

Selezionare l'estensione denominata **Debugger for Chrome** e selezionare **Installa**. Dopo aver installato l'estensione di debug di Chrome, selezionare **Ricarica** per chiudere e riaprire Visual Studio Code e attivare così l'estensione. 

![Ricaricamento di Visual Studio Code dopo l'installazione dell'estensione di debug di Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

Anche se è stato possibile eseguire il codice Node.js ed effettuarne il debug senza una configurazione specifica di Visual Studio Code, per eseguire il debug di un'app Web front-end è necessario generare un file `launch.json` che indica a Visual Studio Code come eseguire l'app. 

Per generare il file `launch.json`, passare alla scheda **Debug**, fare clic sull'icona dell'ingranaggio (con un puntino rosso in cima) e selezionare l'ambiente **node.js**.

![Opzione di Visual Studio Code per configurare il file launch.json](./media/node-howto-e2e/debug-gear.png)

Dopo la creazione, il file `launch.json` sarà simile al seguente e indicherà a Visual Studio Code come avviare e/o collegarsi all'app per eseguirne il debug. 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

Si noti che Visual Studio Code è riuscito a rilevare che lo script di avvio dell'app è `server.js`. 

Con il file `launch.json` aperto, selezionare **Aggiungi configurazione** in basso a destra e selezionare **Chrome: Launch with userDataDir**.

![Aggiunta di una configurazione di Chrome a Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

L'aggiunta di una nuova configurazione di esecuzione per Chrome consente di eseguire il debug del codice JavaScript di front-end. 

È possibile passare il puntatore del mouse su una qualsiasi delle impostazioni specificate per visualizzare l'indicazione della funzione dell'impostazione. Si noti anche che Visual Studio Code rileva automaticamente l'URL dell'app. Modificare la proprietà **webRoot** in `${workspaceRoot}/public` in modo che il debugger di Chrome possa trovare gli asset front-end dell'app:

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

Per avviare/eseguire il debug del front-end e del back-end contemporaneamente, è necessario creare una configurazione di esecuzione *composta* che indichi a Visual Studio Code quale set di configurazioni eseguire in parallelo. 

Aggiungere il frammento seguente come proprietà di primo livello nel file `launch.json`, ovvero come elemento di pari livello della proprietà **configurations** esistente.

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

I valori di stringa specificati nella matrice **compounds.configurations** si riferiscono al **nome** delle singole voci nell'elenco **configurations**. Se questi nomi sono stati modificati, è necessario apportare le modifiche appropriate nella matrice. Per vedere un esempio pratico, passare alla scheda Debug e impostare la configurazione su **Full-Stack** (il nome della configurazione composta), quindi premere **&lt;F5>** per eseguirla.

![Esecuzione di una configurazione in Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

Con l'esecuzione della configurazione vengono avviati l'app Node.js (come si può vedere nell'output della console di debug) e Chrome, che è configurato per passare all'app Node.js all'indirizzo `http://localhost:8080`.

Premere **&lt;Ctrl>P**, quindi immettere o selezionare `todos.js`, ovvero il controller Angular principale per il front-end dell'app. 

Impostare un punto di interruzione alla riga 11, ovvero nel punto di ingresso di una nuova voce Todo.

Tornare all'app in esecuzione e aggiungere una nuova voce Todo. Si noti che Visual Studio Code ha ora sospeso l'esecuzione nel codice Angular.

![Debug del codice di front-end in Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

Come per il debug di Node.js, è possibile posizionare il mouse su espressioni, visualizzare variabili locali/espressioni di controllo, valutare le espressioni nella console e così via. 

Esistono due aspetti importanti da notare:

1. Il riquadro **Stack di chiamate** visualizza due stack differenti, **Node** e **Chrome**, e indica quello attualmente sospeso.

1. È possibile passare dal codice di front-end al codice di back-end e viceversa. Per provare questa operazione, premere **&lt;F5>** per raggiungere il punto di interruzione impostato precedentemente nella route Express.

Con questa configurazione è possibile eseguire in modo efficiente il debug del codice JavaScript di front-end, back-end o dello stack completo direttamente da Visual Studio Code. 

Il concetto di debugger composto non è limitato a due processi di destinazione e non è limitato solo a JavaScript. Se quindi si usa un'app di microservizi, che è potenzialmente Polyglot, è possibile usare lo stesso flusso di lavoro dopo aver installato le estensioni appropriate per il linguaggio/framework.

## <a name="dockerizing-the-app"></a>Creazione di un contenitore Docker dell'app

Questa sezione è incentrata sull'esperienza offerta da Visual Studio Code per lo sviluppo con [Docker](https://www.docker.com/). Gli sviluppatori di Node.js usano Docker per fornire distribuzioni di app portabili per lo sviluppo, l'integrazione continua (CI) e gli ambienti di produzione. Dato che Docker presenta una curva di apprendimento ripida per alcuni, Visual Studio Code fornisce un'estensione per semplificare l'uso di Docker nelle app.

Tornare alla scheda **Estensioni**, cercare `docker` e selezionare l'estensione **Docker**. 

Installare l'estensione Docker e quindi ricaricare Visual Studio Code.

![Installazione dell'estensione Docker per Visual Studio Code](./media/node-howto-e2e/docker-search.png)

L'estensione Docker per Visual Studio Code include un comando per la generazione di un *Dockerfile* e del file `docker-compose.yml` per un progetto esistente. 

Per vedere i comandi Docker disponibili, visualizzare il riquadro comandi premendo **&lt;F1>** e quindi digitare `docker`.

![Comandi supportati dall'estensione Docker per Visual Studio ](./media/node-howto-e2e/docker-commands.png)

Selezionare **Docker: Add docker files to workspace** (Docker: Aggiungi file docker all'area di lavoro), selezionare **Node.js** come piattaforma dell'app e specificare che l'app espone la porta `8080`. 

Il comando Docker genera un `Dockerfile` completo e file Docker-compose che possono essere usati immediatamente.

![Dockerfile generato](./media/node-howto-e2e/docker-file.png)

Anche l'estensione Docker mette a disposizione il completamento automatico per `Dockerfiles` e i file `docker-compose.yml`. 

Per vedere un esempio pratico, aprire il `Dockerfile` e modificare la riga 2 da:

```docker
FROM node:latest
```

A:

```docker
FROM mhart
```

Con il cursore posizionato dopo la `t` di `mhart`, premere **&lt;Ctrl>&lt;spazio>** per visualizzare tutti i repository di immagini che `mhart` ha pubblicato su DockerHub.

![Completamento automatico dell'estensione Docker](./media/node-howto-e2e/docker-completion.png)

Selezionare `mhart/alpine-node`, che offre tutti gli elementi di cui l'app necessita. 

È di norma consigliabile usare immagini di piccole dimensioni perché si vuole che la compilazione e la distribuzione delle app siano il più possibile rapide, rendendo così distribuzione e ridimensionamento più veloci.

Ora che è stato generato il `Dockerfile` è necessario creare l'immagine effettiva di Docker. Anche in questo caso è possibile usare un comando installato dall'estensione Docker in Visual Studio Code. Premere **&lt;F1>**, immettere `dockerb` nel riquadro comandi e selezionare il comando **Docker: Build Image**. Scegliere il `/Dockerfile` appena generato e modificato. Specificare un tag che includa il nome utente DockerHub, ad esempio `lostintangent/node`. Premere **&lt;INVIO>** per avviare la finestra del terminale integrata che visualizza l'output dell'immagine Docker in fase di creazione.

![Stato di creazione dell'immagine Docker](./media/node-howto-e2e/docker-build.png)

Si noti che il comando ha automatizzato il processo di esecuzione di `docker build`. Si tratta di un altro esempio di strumento di incremento della produttività facoltativo. In alternativa è possibile usare direttamente l'interfaccia della riga di comando di Docker. 

Per rendere questa immagine facilmente acquisibile per le distribuzioni, a questo punto è necessario solo effettuare il push dell'immagine in DockerHub. A tale scopo, assicurarsi di avere già effettuato l'autenticazione con DockerHub eseguendo `docker login` dall'interfaccia della riga di comando e immettendo le credenziali dell'account. In Visual Studio Code è quindi possibile visualizzare il riquadro comandi, immettere `dockerpush` e selezionare il comando `Docker: Push`. Selezionare il tag di immagine appena creato, ad esempio `lostintangent/node`, e premere **&lt;Invio>**. Il comando automatizza la chiamata di `docker push` e visualizza l'output nel terminale integrato.

## <a name="deploying-the-app"></a>Distribuzione dell'app

Ora che l'immagine Docker è stata creata e inserita in DockerHub, è necessario distribuire l'app nel cloud per renderla visibile. A tale scopo è possibile usare il servizio app di Azure, ovvero l'offerta PaaS di Azure. Il servizio app presenta due funzionalità interessanti per gli sviluppatori di Node.js:

- Supporto per le macchine virtuali Linux, che consente di ridurre i problemi di compatibilità per le app che vengono compilate usando moduli Node nativi o altri strumenti che potrebbero non supportare Windows e/o possono comportarsi in modo diverso.
- Supporto per le distribuzioni basate su Docker, che consente di specificare il nome dell'immagine Docker e al servizio app di eseguire il pull, distribuire e ridimensionare automaticamente l'immagine.

Per iniziare, aprire il terminale di Visual Studio. Si userà la nuova interfaccia della riga di comando di Azure 2.0 per gestire l'account Azure ed effettuare il provisioning dell'infrastruttura necessaria per eseguire l'app Todo. Dopo aver effettuato l'accesso all'account dall'interfaccia della riga di comando con il comando `az login`, come indicato nei prerequisiti, eseguire questa procedura per eseguire il provisioning dell'istanza del servizio app e distribuire il contenitore dell'app Todo:

1. Creare un gruppo di risorse, che può essere considerato uno *spazio dei nomi* o una *directory* per organizzare le risorse di Azure. L'opzione `-n` viene usata per specificare il nome del gruppo e può essere un valore qualsiasi.

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > L'opzione `-l` indica la posizione del gruppo di risorse. Nell'anteprima, il supporto del servizio app in Linux è disponibile solo in alcune aree. Se quindi non ci si trova negli Stati Uniti occidentali e si vuole verificare quali altre aree sono disponibili, eseguire `az appservice list-locations --linux-workers-enabled` dall'interfaccia della riga di comando per visualizzare le opzioni per i data center.

2. Impostare il gruppo di risorse appena creato come gruppo di risorse predefinito, per poter continuare a usare l'interfaccia della riga di comando senza dover specificare esplicitamente il gruppo di risorse a ogni chiamata dell'interfaccia stessa:

   ```shell
   az configure -d group=nina-demo
   ```
   
3. Creare il *piano* del servizio app, che gestisce la creazione e il ridimensionamento delle macchine virtuali sottostanti nelle quali viene distribuita l'app. Anche in questo caso, specificare un valore qualsiasi per l'opzione `n`.

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > L'opzione --is-linux indica che le macchine virtuali dovranno essere basate su Linux. Senza questa opzione, l'impostazione predefinita dell'interfaccia della riga di comando sarà il provisioning di macchine virtuali Windows.

4. Creare l'app Web del servizio app, che rappresenta l'app Todo effettiva che verrà eseguita nel piano e nel gruppo di risorse appena creati. Un'app Web può essere considerata un sinonimo di processo o contenitore, mentre il piano può essere considerato l'host della macchina virtuale/contenitore su cui questi elementi vengono eseguiti. Nell'ambito della creazione dell'app Web sarà anche necessario configurare l'app per l'uso dell'immagine Docker pubblicata in DockerHub:

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > Se invece di un contenitore personalizzato si preferisce usare una distribuzione Git, vedere l'articolo [Creare un'app Web Node.js in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).

5. Impostare l'app Web come istanza Web predefinita:

    ```shell
    az configure -d web=nina-demo-app
    ```

6. Avviare l'app per visualizzare il contenitore distribuito, che sarà disponibile a un URL `*.azurewebsites.net`:

    ```shell
    az webapp browse
    ```

    ![App Todo in esecuzione nel browser](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > Potrebbero essere necessari alcuni minuti per caricare l'app la prima volta, perché il servizio app deve effettuare il pull dell'immagine Docker da DockerHub e quindi avviarla.

A questo punto, l'app Todo è stata appena distribuita ed eseguita. 

L'app Todo è ora distribuita. L'icona della rotellina indica tuttavia che l'app non può connettersi al database. Ciò è dovuto al fatto che durante lo sviluppo è stata usata un'istanza locale di MongoDB, che ovviamente non è raggiungibile dai data center di Azure. Dato che l'app è stata modificata per accettare la stringa di connessione tramite una variabile di ambiente, è sufficiente avviare un server di MongoDB e riconfigurare l'istanza del servizio app perché faccia riferimento alla variabile di ambiente. Questa procedura è illustrata nella sezione seguente.

## <a name="provisioning-a-mongodb-server"></a>Provisioning di un server di MongoDB

Anche se è possibile configurare un server di MongoDB o un set di repliche e gestire l'infrastruttura autonomamente, Azure mette a disposizione una soluzione denominata [Cosmos DB](https://azure.microsoft.com/services/documentdb/). Cosmos DB è un database NoSQL completamente gestito, con replica geografica e prestazioni elevate, che fornisce un livello di compatibilità per MongoDB. È quindi possibile puntarvi un'app MEAN esistente, oppure qualsiasi client/strumento MongoDB come [Studio 3T](https://studio3t.com/), senza dover modificare altri elementi oltre alla stringa di connessione. I passaggi seguenti illustrano la procedura:

1. Dal terminale di Visual Studio Code eseguire questo comando per creare un'istanza del servizio Cosmos DB compatibile con MongoDB. Sostituire il segnaposto **<NAME>** con un valore univoco globale. Cosmos DB usa questo nome per generare l'URL del server di database:

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. Recuperare la stringa di connessione MongoDB per questa istanza:

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. Aggiornare la variabile di ambiente **MONGODB_URL** dell'app Web in modo che si connetta all'istanza di Cosmos DB della quale è stato appena effettuato il provisioning, invece di provare a connettersi a un server di MongoDB eseguito in locale, che in realtà è inesistente:

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. Tornare al browser e aggiornarlo. Provare ad aggiungere e rimuovere un elemento Todo. L'app ora funziona senza dover modificare nulla. Impostare la variabile di ambiente sull'istanza di Cosmos DB creata, che emula completamente un database di MongoDB.

    ![App demo dopo la connessione a un database](./media/node-howto-e2e/finished-demo.png)

Quando necessario, è possibile tornare all'istanza di Cosmos DB e aumentare o ridurre la velocità effettiva riservata richiesta dall'istanza di MongoDB e sfruttare il traffico aggiunto senza dover gestire manualmente l'infrastruttura.

Cosmos DB indicizza anche automaticamente ogni documento e proprietà. Non è quindi necessario definire query lente o ottimizzare manualmente gli indici. È sufficiente eseguire il provisioning e il ridimensionamento secondo le esigenze e lasciare che Cosmos DB gestisca il resto.

## <a name="hosting-a-private-docker-registry"></a>Hosting di un registro Docker privato

DockerHub offre un'esperienza eccellente per la distribuzione delle immagini del contenitore, ma possono esistere scenari in cui si vuole ospitare un registro Docker privato, per obiettivi di sicurezza/governance o prestazioni. A tale scopo, Azure mette a disposizione [Registro contenitori di Azure](https://azure.microsoft.com/services/container-registry/), che consente di creare rapidamente un proprio registro Docker il cui archivio di backup si trova nello stesso data center dell'app Web, rendendo il pull più veloce. Registro contenitori di Azure fornisce anche il controllo completo del contenuto e dei controlli di accesso, consentendo ad esempio di definire chi può eseguire il push o pull delle immagini. 

Il provisioning di un registro personalizzato può essere eseguito con il comando seguente. Sostituire il segnaposto **<NAME>** con un valore univoco globale, perché Registro contenitori di Azure usa il valore specificato per generare l'URL del server di accesso al registro.

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> Anche se l'esempio di questo argomento usa l'**account amministratore** per obiettivi di semplificazione, l'uso di questo account non è consigliabile per i registri di produzione. 

Il comando `az acr create` visualizza l'URL del server di accesso (tramite la colonna `LOGIN SERVER`) usato per accedere con l'interfaccia della riga di comando di Docker, ad esempio `ninademo.azurecr.io`. Il comando genera anche le credenziali di amministratore usate per l'autenticazione. Per recuperare tali credenziali, eseguire questo comando e annotare il nome utente e la password visualizzati:

```shell
az acr credential show -n $ACR_NAME
```

Usando le credenziali del passaggio precedente e il proprio server di accesso è possibile accedere al registro tramite il flusso di lavoro standard dell'interfaccia della riga di comando di Docker.

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

È ora possibile contrassegnare il contenitore Docker per indicare che è associato al registro privato usando il comando seguente, in cui è necessario sostituire `lostintangent/node` con il nome assegnato all'immagine del contenitore.

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

Eseguire infine il push dell'immagine contrassegnata nel registro Docker privato.

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

Il contenitore è ora archiviato nel proprio registro privato e l'interfaccia della riga di comando di Docker consente di continuare a lavorare esattamente come quando si usa DockerHub. Per indicare all'app Web del servizio app di effettuare il pull dal registro privato, è sufficiente eseguire questo comando:

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> Aggiungere il prefisso `https://` all'inizio dell'opzione `-r`. Non aggiungere tuttavia il prefisso al nome dell'immagine del contenitore.

Aggiornando l'app nel browser, l'aspetto e il funzionamento rimarranno invariati. L'app viene ora tuttavia eseguita tramite il registro Docker privato. Dopo aver aggiornato l'app, contrassegnare ed eseguire il push delle modifiche come in precedenza e aggiornare il tag nella configurazione del contenitore del servizio app.

## <a name="configuring-a-custom-domain-name"></a>Configurazione di un nome di dominio personalizzato

Anche se l'URL `*.azurewebsites.net` è un'ottima opzione per i test, può essere successivamente opportuno aggiungere un nome di dominio personalizzato all'app Web. Dopo aver ottenuto un nome di dominio da un registrar, è sufficiente aggiungere al nome un record `A` che punti all'indirizzo IP esterno dell'app Web, che è in realtà un bilanciamento del carico. Questo indirizzo IP può essere recuperato con il comando seguente:

```shell
az webapp config hostname get-external-ip
```

Oltre ad aggiungere un record `A` è necessario aggiungere al dominio un record `TXT` che punti al dominio `*.azurewebsites.net` usato finora. La combinazione dei record `A` e `TXT` consente ad Azure di verificare che si è proprietari del dominio.

Dopo aver creato i record e aver propagato le modifiche DNS, registrare il dominio personalizzato con Azure per indicare l'origine corretta del traffico in ingresso. 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> Il comando non funziona fino a quando le modifiche DNS non vengono propagate.

Aprire un browser e passare al dominio personalizzato per verificare che ora si risolva nell'app distribuita in Azure.

## <a name="scaling-up-and-out"></a>Aumentare le prestazioni e il numero di istanze

A un certo punto, l'app Web può diventare talmente diffusa che le risorse allocate (CPU e RAM) non sono più sufficienti a gestire l'aumento del traffico e delle esigenze operative. Il piano del servizio app creato in precedenza (**B1**) prevede 1 core CPU e 1,75 GB di RAM, che si esauriscono abbastanza rapidamente. Il piano **B2** offre il doppio di RAM e CPU, quindi se si nota che l'app inizia a esaurire queste risorse è possibile aumentare le prestazioni della macchina virtuale sottostante eseguendo questo comando:

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> Per i dettagli e le specifiche dei prezzi dei piani app di Azure, vedere l'articolo [Prezzi di Servizio app](https://azure.microsoft.com/pricing/details/app-service/)

Dopo pochi istanti verrà eseguita la migrazione dell'app Web all'hardware richiesto e sarà possibile iniziare a sfruttare le risorse associate. Le prestazioni possono anche essere ridotte eseguendo lo stesso comando indicato in precedenza, specificando un'opzione `--sku` che offre meno risorse a un prezzo inferiore. 

Oltre ad aumentare le prestazioni per le macchine virtuali, finché l'app Web è senza stato, è anche possibile *aumentare il numero di istanze* aggiungendo più istanze di macchina virtuale sottostanti. Il piano del servizio app creato in precedenza include una sola macchina virtuale (un *ruolo di lavoro*) e quindi tutto il traffico in ingresso è vincolato ai limiti delle risorse disponibili per quella sola istanza. Se si vuole aggiungere una seconda istanza di macchina virtuale, è possibile eseguire lo stesso comando eseguito in precedenza, ma invece di aumentare lo SKU si aumenta il numero di macchine virtuali di lavoro.

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

Quando si aumenta il numero di istanze di un'app Web come questa, il carico del traffico in ingresso viene bilanciato in modo trasparente tra tutte le istanze, aumentando così immediatamente la capacità senza modifiche al codice e senza preoccuparsi dell'infrastruttura necessaria. 

Le app Web senza stato sono considerate procedure consigliate perché rendono la scalabilità (aumento o riduzione delle prestazioni e aumento del numero di istanze) interamente deterministica, poiché nessuna macchina virtuale o istanza dell'app include uno stato necessario per il funzionamento. 

> [!NOTE]
> Anche se l'esercitazione di questo argomento illustra l'esecuzione di una singola app Web nell'ambito di un piano di servizio app, è possibile creare e distribuire più app Web nello stesso piano, consentendo di effettuare il provisioning e sostenere i costi di un singolo piano. 

## <a name="clean-up"></a>Eliminazione

Per evitare che vengano addebitate risorse di Azure non usate, eseguire questo comando dal terminale di Visual Studio Code per eliminare tutte le risorse delle quali è stato effettuato il provisioning durante questa esercitazione.

```shell
az group delete
```

> [!NOTE]
> Il processo di eliminazione può richiedere alcuni minuti. 

Al termine, il comando `az group delete` lascia l'account di Azure nello stato in cui si trovava prima di iniziare l'esercitazione. La possibilità di organizzare, distribuire ed eliminare le risorse di Azure come singola unità è uno dei vantaggi principali dei gruppi di risorse. Si consiglia quindi di raggruppare le risorse che si prevede abbiano la stessa durata.