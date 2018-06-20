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
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="8179b-103">Sviluppo di Node.js con Visual Studio Code e Azure</span><span class="sxs-lookup"><span data-stu-id="8179b-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="8179b-104">Questa esercitazione illustra la creazione di un contenitore Docker da un'app Node.js esistente e la distribuzione dell'app in Azure con Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="8179b-105">L'esercitazione usa una semplice app Todo creata e pubblicata da [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span><span class="sxs-lookup"><span data-stu-id="8179b-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="8179b-106">Si tratta di un'app MEAN a singola pagina e quindi usa MongoDB come database, Node/Express per il server Web/API REST e Angular.js 1. x per l'interfaccia front-end.</span><span class="sxs-lookup"><span data-stu-id="8179b-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="8179b-107">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="8179b-107">Prerequisites</span></span>

<span data-ttu-id="8179b-108">Per seguire la demo è necessario avere installato il software seguente:</span><span class="sxs-lookup"><span data-stu-id="8179b-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="8179b-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8179b-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="8179b-110">Docker</span><span class="sxs-lookup"><span data-stu-id="8179b-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="8179b-111">Account DockerHub</span><span class="sxs-lookup"><span data-stu-id="8179b-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="8179b-112">Interfaccia della riga di comando di Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="8179b-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="8179b-113">Account di Azure</span><span class="sxs-lookup"><span data-stu-id="8179b-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="8179b-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="8179b-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="8179b-115">[Chrome](https://www.google.com/chrome/browser/desktop/): usato per il debug del front-end dell'app demo.</span><span class="sxs-lookup"><span data-stu-id="8179b-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="8179b-116">MongoDB: poiché l'app demo usa MongoDB, è necessaria un'istanza di MongoDB locale in ascolto sulla porta `27017` standard.</span><span class="sxs-lookup"><span data-stu-id="8179b-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="8179b-117">Il modo più semplice per ottenere questo risultato è eseguire questi due comandi dopo l'installazione di Docker: `docker pull mongo` seguito da `docker run -it -p 27017:27017 mongo`.</span><span class="sxs-lookup"><span data-stu-id="8179b-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="8179b-118">Configurazione del progetto</span><span class="sxs-lookup"><span data-stu-id="8179b-118">Project setup</span></span>

<span data-ttu-id="8179b-119">Per iniziare, scaricare il progetto di esempio usando la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="8179b-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="8179b-120">Aprire Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="8179b-121">Premere **&lt;F1>** per visualizzare il riquadro comandi.</span><span class="sxs-lookup"><span data-stu-id="8179b-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="8179b-122">Al prompt del riquadro comandi immettere `gitcl`, selezionare il comando **Git: Clone** e premere **&lt;Invio>**.</span><span class="sxs-lookup"><span data-stu-id="8179b-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Comando gitcl nel prompt del riquadro comandi di Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="8179b-124">Quando viene richiesto l'**URL del repository**, immettere `https://github.com/scotch-io/node-todo`, quindi premere **&lt;Invio>**.</span><span class="sxs-lookup"><span data-stu-id="8179b-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="8179b-125">Selezionare o creare la directory locale in cui si vuole clonare il progetto.</span><span class="sxs-lookup"><span data-stu-id="8179b-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Esplora risorse di Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="8179b-127">Terminale integrato</span><span class="sxs-lookup"><span data-stu-id="8179b-127">Integrated terminal</span></span>

<span data-ttu-id="8179b-128">Trattandosi di un progetto Node.js, è prima di tutto necessario verificare che tutte le dipendenze del progetto siano installate da npm.</span><span class="sxs-lookup"><span data-stu-id="8179b-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="8179b-129">Premere  **&lt;Ctrl>'** per visualizzare il terminale integrato di Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="8179b-130">Digitare `yarn` e premere **&lt;Invio>**.</span><span class="sxs-lookup"><span data-stu-id="8179b-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Esecuzione del comando yarn in Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="8179b-132">Controllo della versione integrato Git</span><span class="sxs-lookup"><span data-stu-id="8179b-132">Integrated Git version control</span></span>

<span data-ttu-id="8179b-133">Dopo l'installazione delle dipendenze dell'app tramite Yarn, viene creato un file `yarn.lock` che consente di riacquisire in modo prevedibile le stesse identiche dipendenze in futuro, senza eventi imprevisti nelle compilazioni CI (integrazione continua), nelle distribuzioni di produzione o in altri computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="8179b-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="8179b-134">La procedura seguente illustra come verificare il file `yarn.lock` nel controllo del codice sorgente:</span><span class="sxs-lookup"><span data-stu-id="8179b-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="8179b-135">In Visual Studio Code passare alla scheda integrata Git, ovvero la scheda con il logo Git.</span><span class="sxs-lookup"><span data-stu-id="8179b-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="8179b-136">Nella casella **Messaggio**, immettere un messaggio di commit e premere **&lt;Ctrl>&lt;Invio>**.</span><span class="sxs-lookup"><span data-stu-id="8179b-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![Aggiunta del file yarn.lock a Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="8179b-138">Esplorazione del progetto e del codice</span><span class="sxs-lookup"><span data-stu-id="8179b-138">Project and code navigation</span></span>

<span data-ttu-id="8179b-139">Per orientarsi nella base di codici, si esamineranno alcuni esempi di funzionalità di esplorazione messe a disposizione da Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="8179b-140">Premere **&lt;Ctrl>P**.</span><span class="sxs-lookup"><span data-stu-id="8179b-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="8179b-141">Immettere `.js` per visualizzare tutti i file JSON/JavaScript presenti nel progetto e la directory padre di ogni file</span><span class="sxs-lookup"><span data-stu-id="8179b-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![Visualizzare tutti i file con estensione js](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="8179b-143">Selezionare `server.js`, ovvero lo script di avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="8179b-144">Posizionare il mouse sulla variabile **database** importata alla riga 6 per visualizzarne il tipo.</span><span class="sxs-lookup"><span data-stu-id="8179b-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="8179b-145">La possibilità di analizzare rapidamente variabili, moduli e tipi in un file è molto utile durante lo sviluppo dei progetti.</span><span class="sxs-lookup"><span data-stu-id="8179b-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![Individuare il tipo](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="8179b-147">Facendo clic all'interno di una variabile, ad esempio **database**, è possibile vedere tutti i riferimenti a tale variabile presenti nello stesso file.</span><span class="sxs-lookup"><span data-stu-id="8179b-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="8179b-148">Per visualizzare tutti i riferimenti a una variabile nel progetto, fare clic con il pulsante destro del mouse sulla variabile e dal menu di scelta rapida scegliere **Trova tutti i riferimenti**.</span><span class="sxs-lookup"><span data-stu-id="8179b-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![Trovare i riferimenti a una variabile](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="8179b-150">Oltre a passare il mouse su una variabile per individuarne il tipo, è possibile esaminare la definizione di una variabile, anche se si trova in un altro file.</span><span class="sxs-lookup"><span data-stu-id="8179b-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="8179b-151">Per visualizzare questa azione, fare clic con il pulsante destro del mouse su **database.localUrl** (riga 12) e quindi scegliere **Visualizza definizione** dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="8179b-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![Visualizzare la definizione di una variabile](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="8179b-153">Modifica del codice e uso del completamento automatico</span><span class="sxs-lookup"><span data-stu-id="8179b-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="8179b-154">La stringa di connessione di MongoDB è hardcoded nella dichiarazione di **database.localUrl**.</span><span class="sxs-lookup"><span data-stu-id="8179b-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="8179b-155">In questa sezione verrà modificato il codice per recuperare la stringa di connessione da una variabile di ambiente e verranno illustrate informazioni sulla funzionalità di completamento automatico di Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="8179b-156">Aprire il file `server.js`</span><span class="sxs-lookup"><span data-stu-id="8179b-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="8179b-157">Sostituire il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="8179b-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="8179b-158">con questo codice:</span><span class="sxs-lookup"><span data-stu-id="8179b-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="8179b-159">Si noti che se si immette il codice manualmente (invece di copiarlo e incollarlo), quando si digita il punto dopo `process`, Visual Studio Code visualizza i membri disponibili dell'API globale **process** di Node.js.</span><span class="sxs-lookup"><span data-stu-id="8179b-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![Il completamento automatico visualizza automaticamente i membri di un'API](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="8179b-161">Il completamento automatico funziona perché Visual Studio Code usa TypeScript in background, anche per JavaScript, per fornire informazioni sui tipi che possono quindi essere usate per l'elenco di completamento durante la digitazione.</span><span class="sxs-lookup"><span data-stu-id="8179b-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="8179b-162">Visual Studio Code può rilevare che si tratta di un progetto di Node.js e quindi scarica automaticamente il file delle definizioni di tipi TypeScript per [Node.js da NPM](https://www.npmjs.com/package/@types/node).</span><span class="sxs-lookup"><span data-stu-id="8179b-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="8179b-163">Il file delle definizioni di tipi consente di ottenere il completamento automatico per altre variabili globali Node.js, ad esempio **Buffer** e **setTimeout**, oltre a tutti i moduli predefiniti, ad esempio **fs** e **http**.</span><span class="sxs-lookup"><span data-stu-id="8179b-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="8179b-164">Oltre alle API di Node.js predefinite, questa acquisizione automatica di definizioni di tipi funziona anche per oltre 2.000 moduli di terze parti, ad esempio React, Underscore ed Express.</span><span class="sxs-lookup"><span data-stu-id="8179b-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="8179b-165">Ad esempio, per impedire a Mongoose di arrestare l'app di esempio in modo anomalo se non riesce a connettersi all'istanza di database MongoDB configurata, inserire la riga di codice seguente alla riga 13:</span><span class="sxs-lookup"><span data-stu-id="8179b-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="8179b-166">Come con il codice precedente, si noterà che il completamento automatico funziona senza operazioni aggiuntive da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8179b-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![Il completamento automatico visualizza automaticamente i membri di un'API](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="8179b-168">È possibile vedere quali moduli supportano questa funzionalità di completamento automatico esplorando il progetto [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), che rappresenta la fonte gestita dalla community di tutte le definizioni di tipi TypeScript.</span><span class="sxs-lookup"><span data-stu-id="8179b-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="8179b-169">Esecuzione dell'app</span><span class="sxs-lookup"><span data-stu-id="8179b-169">Running the app</span></span>

<span data-ttu-id="8179b-170">Dopo aver esaminato il codice, eseguire l'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="8179b-171">Per eseguire l'app da Visual Studio Code premere **&lt;F5>**.</span><span class="sxs-lookup"><span data-stu-id="8179b-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="8179b-172">Quando si esegue il codice tramite  **&lt;F5>** (modalità di debug), Visual Studio Code avvia l'app e visualizza la finestra **Console di debug** con il canale stdout per l'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![Monitoraggio di stdout di un'app tramite la console di debug](./media/node-howto-e2e/console.png)

<span data-ttu-id="8179b-174">La **console di debug** è collegata all'app appena avviata, quindi è possibile digitare espressioni JavaScript che verranno valutate nell'app. È anche disponibile il completamento automatico.</span><span class="sxs-lookup"><span data-stu-id="8179b-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="8179b-175">Per un esempio pratico, digitare `process.env` nella console:</span><span class="sxs-lookup"><span data-stu-id="8179b-175">To see this in action, type `process.env` in the console:</span></span>

![Immissione del codice nella console di debug](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="8179b-177">È stato possibile premere **&lt;F5>** per eseguire l'app perché il file attualmente aperto è un file JavaScript (`server.js`).</span><span class="sxs-lookup"><span data-stu-id="8179b-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="8179b-178">Di conseguenza, Visual Studio Code presuppone che il progetto sia un'app Node.js.</span><span class="sxs-lookup"><span data-stu-id="8179b-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="8179b-179">Se si chiudono tutti i file JavaScript in Visual Studio Code e quindi si preme **&lt;F5>**, Visual Studio Code chiederà di specificare l'ambiente:</span><span class="sxs-lookup"><span data-stu-id="8179b-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![Indicazione dell'ambiente di runtime](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="8179b-181">Aprire un browser e passare a `http://localhost:8080` per vedere l'app in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8179b-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="8179b-182">Digitare un messaggio nella casella di testo e aggiungere/rimuovere alcuni elementi Todo per avere un'idea del funzionamento dell'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![App Todo in esecuzione](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="8179b-184">Debug</span><span class="sxs-lookup"><span data-stu-id="8179b-184">Debugging</span></span>

<span data-ttu-id="8179b-185">Oltre a poter eseguire l'app e interagire con essa tramite la console integrata, Visual Studio Code consente di impostare punti di interruzione direttamente all'interno del codice.</span><span class="sxs-lookup"><span data-stu-id="8179b-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="8179b-186">Premere ad esempio **&lt;Ctrl>P** per visualizzare la selezione file.</span><span class="sxs-lookup"><span data-stu-id="8179b-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="8179b-187">Dopo aver visualizzato la selezione file, digitare `route` e selezionare il file `route.js`.</span><span class="sxs-lookup"><span data-stu-id="8179b-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="8179b-188">Impostare un punto di interruzione alla riga 28, che rappresenta la route Express che viene chiamata quando l'applicazione prova ad aggiungere una voce Todo.</span><span class="sxs-lookup"><span data-stu-id="8179b-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="8179b-189">Per impostare un punto di interruzione è sufficiente fare clic sull'area a sinistra del numero di riga nell'editor come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="8179b-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Impostazione di un punto di interruzione in Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="8179b-191">Oltre ai punti di interruzione standard, Visual Studio Code supporta punti di interruzione condizionali che consentono di definire quando l'app deve sospendere l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8179b-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="8179b-192">Per impostare un punto di interruzione condizionale, fare clic con il pulsante destro del mouse a sinistra della riga in cui si vuole sospendere l'esecuzione, selezionare **Aggiungi punto di interruzione condizionale** e specificare un'espressione JavaScript (ad esempio `foo = "bar"`) o il conteggio esecuzioni che definisce la condizione che determina la sospensione dell'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8179b-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="8179b-193">Dopo aver impostato il punto di interruzione, tornare all'app in esecuzione e aggiungere una voce Todo.</span><span class="sxs-lookup"><span data-stu-id="8179b-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="8179b-194">Con l'aggiunta di una voce Todo, l'app sospende immediatamente l'esecuzione alla riga 28 in cui è stato impostato il punto di interruzione:</span><span class="sxs-lookup"><span data-stu-id="8179b-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Visual Studio Code sospende l'esecuzione nel punto di interruzione](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="8179b-196">Quando l'applicazione è stata sospesa, è possibile passare il puntatore del mouse sulle espressioni del codice per visualizzare il relativo valore corrente, controllare le variabili locali o le espressioni di controllo e lo stack di chiamate e usare la barra degli strumenti di debug per scorrere l'esecuzione del codice.</span><span class="sxs-lookup"><span data-stu-id="8179b-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="8179b-197">Premere  **&lt;F5>** per riprendere l'esecuzione dell'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="8179b-198">Debug dello stack completo</span><span class="sxs-lookup"><span data-stu-id="8179b-198">Full-stack debugging</span></span>

<span data-ttu-id="8179b-199">Come accennato in precedenza in questo argomento, l'app TODO è un'app MEAN, ovvero sia il front-end che il back-end sono scritti in JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8179b-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="8179b-200">Anche se quindi si esegue attualmente il debug del codice di back-end (Node/Express), a un certo punto potrebbe essere necessario eseguire il debug del codice di front-end (Angular).</span><span class="sxs-lookup"><span data-stu-id="8179b-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="8179b-201">A tale scopo, Visual Studio Code mette a disposizione un vastissimo ecosistema di estensioni, incluso il debug di Chrome integrato.</span><span class="sxs-lookup"><span data-stu-id="8179b-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="8179b-202">Passare alla scheda **Estensioni** e digitare `chrome` nella casella di ricerca:</span><span class="sxs-lookup"><span data-stu-id="8179b-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Estensione di debug di Chrome per Visual Studio Code](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="8179b-204">Selezionare l'estensione denominata **Debugger for Chrome** e selezionare **Installa**.</span><span class="sxs-lookup"><span data-stu-id="8179b-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="8179b-205">Dopo aver installato l'estensione di debug di Chrome, selezionare **Ricarica** per chiudere e riaprire Visual Studio Code e attivare così l'estensione.</span><span class="sxs-lookup"><span data-stu-id="8179b-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Ricaricamento di Visual Studio Code dopo l'installazione dell'estensione di debug di Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="8179b-207">Anche se è stato possibile eseguire il codice Node.js ed effettuarne il debug senza una configurazione specifica di Visual Studio Code, per eseguire il debug di un'app Web front-end è necessario generare un file `launch.json` che indica a Visual Studio Code come eseguire l'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="8179b-208">Per generare il file `launch.json`, passare alla scheda **Debug**, fare clic sull'icona dell'ingranaggio (con un puntino rosso in cima) e selezionare l'ambiente **node.js**.</span><span class="sxs-lookup"><span data-stu-id="8179b-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![Opzione di Visual Studio Code per configurare il file launch.json](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="8179b-210">Dopo la creazione, il file `launch.json` sarà simile al seguente e indicherà a Visual Studio Code come avviare e/o collegarsi all'app per eseguirne il debug.</span><span class="sxs-lookup"><span data-stu-id="8179b-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

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

<span data-ttu-id="8179b-211">Si noti che Visual Studio Code è riuscito a rilevare che lo script di avvio dell'app è `server.js`.</span><span class="sxs-lookup"><span data-stu-id="8179b-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="8179b-212">Con il file `launch.json` aperto, selezionare **Aggiungi configurazione** in basso a destra e selezionare **Chrome: Launch with userDataDir**.</span><span class="sxs-lookup"><span data-stu-id="8179b-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Aggiunta di una configurazione di Chrome a Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="8179b-214">L'aggiunta di una nuova configurazione di esecuzione per Chrome consente di eseguire il debug del codice JavaScript di front-end.</span><span class="sxs-lookup"><span data-stu-id="8179b-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="8179b-215">È possibile passare il puntatore del mouse su una qualsiasi delle impostazioni specificate per visualizzare l'indicazione della funzione dell'impostazione.</span><span class="sxs-lookup"><span data-stu-id="8179b-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="8179b-216">Si noti anche che Visual Studio Code rileva automaticamente l'URL dell'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="8179b-217">Modificare la proprietà **webRoot** in `${workspaceRoot}/public` in modo che il debugger di Chrome possa trovare gli asset front-end dell'app:</span><span class="sxs-lookup"><span data-stu-id="8179b-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

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

<span data-ttu-id="8179b-218">Per avviare/eseguire il debug del front-end e del back-end contemporaneamente, è necessario creare una configurazione di esecuzione *composta* che indichi a Visual Studio Code quale set di configurazioni eseguire in parallelo.</span><span class="sxs-lookup"><span data-stu-id="8179b-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="8179b-219">Aggiungere il frammento seguente come proprietà di primo livello nel file `launch.json`, ovvero come elemento di pari livello della proprietà **configurations** esistente.</span><span class="sxs-lookup"><span data-stu-id="8179b-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="8179b-220">I valori di stringa specificati nella matrice **compounds.configurations** si riferiscono al **nome** delle singole voci nell'elenco **configurations**.</span><span class="sxs-lookup"><span data-stu-id="8179b-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="8179b-221">Se questi nomi sono stati modificati, è necessario apportare le modifiche appropriate nella matrice.</span><span class="sxs-lookup"><span data-stu-id="8179b-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="8179b-222">Per vedere un esempio pratico, passare alla scheda Debug e impostare la configurazione su **Full-Stack** (il nome della configurazione composta), quindi premere **&lt;F5>** per eseguirla.</span><span class="sxs-lookup"><span data-stu-id="8179b-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Esecuzione di una configurazione in Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="8179b-224">Con l'esecuzione della configurazione vengono avviati l'app Node.js (come si può vedere nell'output della console di debug) e Chrome, che è configurato per passare all'app Node.js all'indirizzo `http://localhost:8080`.</span><span class="sxs-lookup"><span data-stu-id="8179b-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="8179b-225">Premere **&lt;Ctrl>P**, quindi immettere o selezionare `todos.js`, ovvero il controller Angular principale per il front-end dell'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="8179b-226">Impostare un punto di interruzione alla riga 11, ovvero nel punto di ingresso di una nuova voce Todo.</span><span class="sxs-lookup"><span data-stu-id="8179b-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="8179b-227">Tornare all'app in esecuzione e aggiungere una nuova voce Todo. Si noti che Visual Studio Code ha ora sospeso l'esecuzione nel codice Angular.</span><span class="sxs-lookup"><span data-stu-id="8179b-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Debug del codice di front-end in Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="8179b-229">Come per il debug di Node.js, è possibile posizionare il mouse su espressioni, visualizzare variabili locali/espressioni di controllo, valutare le espressioni nella console e così via.</span><span class="sxs-lookup"><span data-stu-id="8179b-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="8179b-230">Esistono due aspetti importanti da notare:</span><span class="sxs-lookup"><span data-stu-id="8179b-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="8179b-231">Il riquadro **Stack di chiamate** visualizza due stack differenti, **Node** e **Chrome**, e indica quello attualmente sospeso.</span><span class="sxs-lookup"><span data-stu-id="8179b-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="8179b-232">È possibile passare dal codice di front-end al codice di back-end e viceversa.</span><span class="sxs-lookup"><span data-stu-id="8179b-232">You can step between front and back-end code.</span></span> <span data-ttu-id="8179b-233">Per provare questa operazione, premere **&lt;F5>** per raggiungere il punto di interruzione impostato precedentemente nella route Express.</span><span class="sxs-lookup"><span data-stu-id="8179b-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="8179b-234">Con questa configurazione è possibile eseguire in modo efficiente il debug del codice JavaScript di front-end, back-end o dello stack completo direttamente da Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="8179b-235">Il concetto di debugger composto non è limitato a due processi di destinazione e non è limitato solo a JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8179b-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="8179b-236">Se quindi si usa un'app di microservizi, che è potenzialmente Polyglot, è possibile usare lo stesso flusso di lavoro dopo aver installato le estensioni appropriate per il linguaggio/framework.</span><span class="sxs-lookup"><span data-stu-id="8179b-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="8179b-237">Creazione di un contenitore Docker dell'app</span><span class="sxs-lookup"><span data-stu-id="8179b-237">Dockerizing the app</span></span>

<span data-ttu-id="8179b-238">Questa sezione è incentrata sull'esperienza offerta da Visual Studio Code per lo sviluppo con [Docker](https://www.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="8179b-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="8179b-239">Gli sviluppatori di Node.js usano Docker per fornire distribuzioni di app portabili per lo sviluppo, l'integrazione continua (CI) e gli ambienti di produzione.</span><span class="sxs-lookup"><span data-stu-id="8179b-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="8179b-240">Dato che Docker presenta una curva di apprendimento ripida per alcuni, Visual Studio Code fornisce un'estensione per semplificare l'uso di Docker nelle app.</span><span class="sxs-lookup"><span data-stu-id="8179b-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="8179b-241">Tornare alla scheda **Estensioni**, cercare `docker` e selezionare l'estensione **Docker**.</span><span class="sxs-lookup"><span data-stu-id="8179b-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="8179b-242">Installare l'estensione Docker e quindi ricaricare Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Installazione dell'estensione Docker per Visual Studio Code](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="8179b-244">L'estensione Docker per Visual Studio Code include un comando per la generazione di un *Dockerfile* e del file `docker-compose.yml` per un progetto esistente.</span><span class="sxs-lookup"><span data-stu-id="8179b-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="8179b-245">Per vedere i comandi Docker disponibili, visualizzare il riquadro comandi premendo **&lt;F1>** e quindi digitare `docker`.</span><span class="sxs-lookup"><span data-stu-id="8179b-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="8179b-246">Comandi supportati dall'estensione Docker per Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8179b-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="8179b-247">Selezionare **Docker: Add docker files to workspace** (Docker: Aggiungi file docker all'area di lavoro), selezionare **Node.js** come piattaforma dell'app e specificare che l'app espone la porta `8080`.</span><span class="sxs-lookup"><span data-stu-id="8179b-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="8179b-248">Il comando Docker genera un `Dockerfile` completo e file Docker-compose che possono essere usati immediatamente.</span><span class="sxs-lookup"><span data-stu-id="8179b-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![Dockerfile generato](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="8179b-250">Anche l'estensione Docker mette a disposizione il completamento automatico per `Dockerfiles` e i file `docker-compose.yml`.</span><span class="sxs-lookup"><span data-stu-id="8179b-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="8179b-251">Per vedere un esempio pratico, aprire il `Dockerfile` e modificare la riga 2 da:</span><span class="sxs-lookup"><span data-stu-id="8179b-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="8179b-252">A:</span><span class="sxs-lookup"><span data-stu-id="8179b-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="8179b-253">Con il cursore posizionato dopo la `t` di `mhart`, premere **&lt;Ctrl>&lt;spazio>** per visualizzare tutti i repository di immagini che `mhart` ha pubblicato su DockerHub.</span><span class="sxs-lookup"><span data-stu-id="8179b-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Completamento automatico dell'estensione Docker](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="8179b-255">Selezionare `mhart/alpine-node`, che offre tutti gli elementi di cui l'app necessita.</span><span class="sxs-lookup"><span data-stu-id="8179b-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="8179b-256">È di norma consigliabile usare immagini di piccole dimensioni perché si vuole che la compilazione e la distribuzione delle app siano il più possibile rapide, rendendo così distribuzione e ridimensionamento più veloci.</span><span class="sxs-lookup"><span data-stu-id="8179b-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="8179b-257">Ora che è stato generato il `Dockerfile` è necessario creare l'immagine effettiva di Docker.</span><span class="sxs-lookup"><span data-stu-id="8179b-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="8179b-258">Anche in questo caso è possibile usare un comando installato dall'estensione Docker in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8179b-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="8179b-259">Premere **&lt;F1>**, immettere `dockerb` nel riquadro comandi e selezionare il comando **Docker: Build Image**.</span><span class="sxs-lookup"><span data-stu-id="8179b-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="8179b-260">Scegliere il `/Dockerfile` appena generato e modificato.</span><span class="sxs-lookup"><span data-stu-id="8179b-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="8179b-261">Specificare un tag che includa il nome utente DockerHub, ad esempio `lostintangent/node`.</span><span class="sxs-lookup"><span data-stu-id="8179b-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="8179b-262">Premere **&lt;INVIO>** per avviare la finestra del terminale integrata che visualizza l'output dell'immagine Docker in fase di creazione.</span><span class="sxs-lookup"><span data-stu-id="8179b-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Stato di creazione dell'immagine Docker](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="8179b-264">Si noti che il comando ha automatizzato il processo di esecuzione di `docker build`. Si tratta di un altro esempio di strumento di incremento della produttività facoltativo. In alternativa è possibile usare direttamente l'interfaccia della riga di comando di Docker.</span><span class="sxs-lookup"><span data-stu-id="8179b-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="8179b-265">Per rendere questa immagine facilmente acquisibile per le distribuzioni, a questo punto è necessario solo effettuare il push dell'immagine in DockerHub.</span><span class="sxs-lookup"><span data-stu-id="8179b-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="8179b-266">A tale scopo, assicurarsi di avere già effettuato l'autenticazione con DockerHub eseguendo `docker login` dall'interfaccia della riga di comando e immettendo le credenziali dell'account.</span><span class="sxs-lookup"><span data-stu-id="8179b-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="8179b-267">In Visual Studio Code è quindi possibile visualizzare il riquadro comandi, immettere `dockerpush` e selezionare il comando `Docker: Push`.</span><span class="sxs-lookup"><span data-stu-id="8179b-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="8179b-268">Selezionare il tag di immagine appena creato, ad esempio `lostintangent/node`, e premere **&lt;Invio>**.</span><span class="sxs-lookup"><span data-stu-id="8179b-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="8179b-269">Il comando automatizza la chiamata di `docker push` e visualizza l'output nel terminale integrato.</span><span class="sxs-lookup"><span data-stu-id="8179b-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="8179b-270">Distribuzione dell'app</span><span class="sxs-lookup"><span data-stu-id="8179b-270">Deploying the app</span></span>

<span data-ttu-id="8179b-271">Ora che l'immagine Docker è stata creata e inserita in DockerHub, è necessario distribuire l'app nel cloud per renderla visibile.</span><span class="sxs-lookup"><span data-stu-id="8179b-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="8179b-272">A tale scopo è possibile usare il servizio app di Azure, ovvero l'offerta PaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="8179b-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="8179b-273">Il servizio app presenta due funzionalità interessanti per gli sviluppatori di Node.js:</span><span class="sxs-lookup"><span data-stu-id="8179b-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="8179b-274">Supporto per le macchine virtuali Linux, che consente di ridurre i problemi di compatibilità per le app che vengono compilate usando moduli Node nativi o altri strumenti che potrebbero non supportare Windows e/o possono comportarsi in modo diverso.</span><span class="sxs-lookup"><span data-stu-id="8179b-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="8179b-275">Supporto per le distribuzioni basate su Docker, che consente di specificare il nome dell'immagine Docker e al servizio app di eseguire il pull, distribuire e ridimensionare automaticamente l'immagine.</span><span class="sxs-lookup"><span data-stu-id="8179b-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="8179b-276">Per iniziare, aprire il terminale di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8179b-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="8179b-277">Si userà la nuova interfaccia della riga di comando di Azure 2.0 per gestire l'account Azure ed effettuare il provisioning dell'infrastruttura necessaria per eseguire l'app Todo.</span><span class="sxs-lookup"><span data-stu-id="8179b-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="8179b-278">Dopo aver effettuato l'accesso all'account dall'interfaccia della riga di comando con il comando `az login`, come indicato nei prerequisiti, eseguire questa procedura per eseguire il provisioning dell'istanza del servizio app e distribuire il contenitore dell'app Todo:</span><span class="sxs-lookup"><span data-stu-id="8179b-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="8179b-279">Creare un gruppo di risorse, che può essere considerato uno *spazio dei nomi* o una *directory* per organizzare le risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="8179b-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="8179b-280">L'opzione `-n` viene usata per specificare il nome del gruppo e può essere un valore qualsiasi.</span><span class="sxs-lookup"><span data-stu-id="8179b-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="8179b-281">L'opzione `-l` indica la posizione del gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="8179b-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="8179b-282">Nell'anteprima, il supporto del servizio app in Linux è disponibile solo in alcune aree.</span><span class="sxs-lookup"><span data-stu-id="8179b-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="8179b-283">Se quindi non ci si trova negli Stati Uniti occidentali e si vuole verificare quali altre aree sono disponibili, eseguire `az appservice list-locations --linux-workers-enabled` dall'interfaccia della riga di comando per visualizzare le opzioni per i data center.</span><span class="sxs-lookup"><span data-stu-id="8179b-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="8179b-284">Impostare il gruppo di risorse appena creato come gruppo di risorse predefinito, per poter continuare a usare l'interfaccia della riga di comando senza dover specificare esplicitamente il gruppo di risorse a ogni chiamata dell'interfaccia stessa:</span><span class="sxs-lookup"><span data-stu-id="8179b-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="8179b-285">Creare il *piano* del servizio app, che gestisce la creazione e il ridimensionamento delle macchine virtuali sottostanti nelle quali viene distribuita l'app.</span><span class="sxs-lookup"><span data-stu-id="8179b-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="8179b-286">Anche in questo caso, specificare un valore qualsiasi per l'opzione `n`.</span><span class="sxs-lookup"><span data-stu-id="8179b-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="8179b-287">L'opzione --is-linux indica che le macchine virtuali dovranno essere basate su Linux.</span><span class="sxs-lookup"><span data-stu-id="8179b-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="8179b-288">Senza questa opzione, l'impostazione predefinita dell'interfaccia della riga di comando sarà il provisioning di macchine virtuali Windows.</span><span class="sxs-lookup"><span data-stu-id="8179b-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="8179b-289">Creare l'app Web del servizio app, che rappresenta l'app Todo effettiva che verrà eseguita nel piano e nel gruppo di risorse appena creati.</span><span class="sxs-lookup"><span data-stu-id="8179b-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="8179b-290">Un'app Web può essere considerata un sinonimo di processo o contenitore, mentre il piano può essere considerato l'host della macchina virtuale/contenitore su cui questi elementi vengono eseguiti.</span><span class="sxs-lookup"><span data-stu-id="8179b-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="8179b-291">Nell'ambito della creazione dell'app Web sarà anche necessario configurare l'app per l'uso dell'immagine Docker pubblicata in DockerHub:</span><span class="sxs-lookup"><span data-stu-id="8179b-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="8179b-292">Se invece di un contenitore personalizzato si preferisce usare una distribuzione Git, vedere l'articolo [Creare un'app Web Node.js in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span><span class="sxs-lookup"><span data-stu-id="8179b-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="8179b-293">Impostare l'app Web come istanza Web predefinita:</span><span class="sxs-lookup"><span data-stu-id="8179b-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="8179b-294">Avviare l'app per visualizzare il contenitore distribuito, che sarà disponibile a un URL `*.azurewebsites.net`:</span><span class="sxs-lookup"><span data-stu-id="8179b-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![App Todo in esecuzione nel browser](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="8179b-296">Potrebbero essere necessari alcuni minuti per caricare l'app la prima volta, perché il servizio app deve effettuare il pull dell'immagine Docker da DockerHub e quindi avviarla.</span><span class="sxs-lookup"><span data-stu-id="8179b-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="8179b-297">A questo punto, l'app Todo è stata appena distribuita ed eseguita.</span><span class="sxs-lookup"><span data-stu-id="8179b-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="8179b-298">L'app Todo è ora distribuita.</span><span class="sxs-lookup"><span data-stu-id="8179b-298">You have now deployed the todo app.</span></span> <span data-ttu-id="8179b-299">L'icona della rotellina indica tuttavia che l'app non può connettersi al database.</span><span class="sxs-lookup"><span data-stu-id="8179b-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="8179b-300">Ciò è dovuto al fatto che durante lo sviluppo è stata usata un'istanza locale di MongoDB, che ovviamente non è raggiungibile dai data center di Azure.</span><span class="sxs-lookup"><span data-stu-id="8179b-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="8179b-301">Dato che l'app è stata modificata per accettare la stringa di connessione tramite una variabile di ambiente, è sufficiente avviare un server di MongoDB e riconfigurare l'istanza del servizio app perché faccia riferimento alla variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="8179b-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="8179b-302">Questa procedura è illustrata nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="8179b-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="8179b-303">Provisioning di un server di MongoDB</span><span class="sxs-lookup"><span data-stu-id="8179b-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="8179b-304">Anche se è possibile configurare un server di MongoDB o un set di repliche e gestire l'infrastruttura autonomamente, Azure mette a disposizione una soluzione denominata [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span><span class="sxs-lookup"><span data-stu-id="8179b-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="8179b-305">Cosmos DB è un database NoSQL completamente gestito, con replica geografica e prestazioni elevate, che fornisce un livello di compatibilità per MongoDB.</span><span class="sxs-lookup"><span data-stu-id="8179b-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="8179b-306">È quindi possibile puntarvi un'app MEAN esistente, oppure qualsiasi client/strumento MongoDB come [Studio 3T](https://studio3t.com/), senza dover modificare altri elementi oltre alla stringa di connessione.</span><span class="sxs-lookup"><span data-stu-id="8179b-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="8179b-307">I passaggi seguenti illustrano la procedura:</span><span class="sxs-lookup"><span data-stu-id="8179b-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="8179b-308">Dal terminale di Visual Studio Code eseguire questo comando per creare un'istanza del servizio Cosmos DB compatibile con MongoDB.</span><span class="sxs-lookup"><span data-stu-id="8179b-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="8179b-309">Sostituire il segnaposto **<NAME>** con un valore univoco globale. Cosmos DB usa questo nome per generare l'URL del server di database:</span><span class="sxs-lookup"><span data-stu-id="8179b-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="8179b-310">Recuperare la stringa di connessione MongoDB per questa istanza:</span><span class="sxs-lookup"><span data-stu-id="8179b-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="8179b-311">Aggiornare la variabile di ambiente **MONGODB_URL** dell'app Web in modo che si connetta all'istanza di Cosmos DB della quale è stato appena effettuato il provisioning, invece di provare a connettersi a un server di MongoDB eseguito in locale, che in realtà è inesistente:</span><span class="sxs-lookup"><span data-stu-id="8179b-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="8179b-312">Tornare al browser e aggiornarlo.</span><span class="sxs-lookup"><span data-stu-id="8179b-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="8179b-313">Provare ad aggiungere e rimuovere un elemento Todo. L'app ora funziona senza dover modificare nulla.</span><span class="sxs-lookup"><span data-stu-id="8179b-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="8179b-314">Impostare la variabile di ambiente sull'istanza di Cosmos DB creata, che emula completamente un database di MongoDB.</span><span class="sxs-lookup"><span data-stu-id="8179b-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![App demo dopo la connessione a un database](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="8179b-316">Quando necessario, è possibile tornare all'istanza di Cosmos DB e aumentare o ridurre la velocità effettiva riservata richiesta dall'istanza di MongoDB e sfruttare il traffico aggiunto senza dover gestire manualmente l'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="8179b-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="8179b-317">Cosmos DB indicizza anche automaticamente ogni documento e proprietà.</span><span class="sxs-lookup"><span data-stu-id="8179b-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="8179b-318">Non è quindi necessario definire query lente o ottimizzare manualmente gli indici.</span><span class="sxs-lookup"><span data-stu-id="8179b-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="8179b-319">È sufficiente eseguire il provisioning e il ridimensionamento secondo le esigenze e lasciare che Cosmos DB gestisca il resto.</span><span class="sxs-lookup"><span data-stu-id="8179b-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="8179b-320">Hosting di un registro Docker privato</span><span class="sxs-lookup"><span data-stu-id="8179b-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="8179b-321">DockerHub offre un'esperienza eccellente per la distribuzione delle immagini del contenitore, ma possono esistere scenari in cui si vuole ospitare un registro Docker privato, per obiettivi di sicurezza/governance o prestazioni.</span><span class="sxs-lookup"><span data-stu-id="8179b-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="8179b-322">A tale scopo, Azure mette a disposizione [Registro contenitori di Azure](https://azure.microsoft.com/services/container-registry/), che consente di creare rapidamente un proprio registro Docker il cui archivio di backup si trova nello stesso data center dell'app Web, rendendo il pull più veloce.</span><span class="sxs-lookup"><span data-stu-id="8179b-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="8179b-323">Registro contenitori di Azure fornisce anche il controllo completo del contenuto e dei controlli di accesso, consentendo ad esempio di definire chi può eseguire il push o pull delle immagini.</span><span class="sxs-lookup"><span data-stu-id="8179b-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="8179b-324">Il provisioning di un registro personalizzato può essere eseguito con il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="8179b-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="8179b-325">Sostituire il segnaposto **<NAME>** con un valore univoco globale, perché Registro contenitori di Azure usa il valore specificato per generare l'URL del server di accesso al registro.</span><span class="sxs-lookup"><span data-stu-id="8179b-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="8179b-326">Anche se l'esempio di questo argomento usa l'**account amministratore** per obiettivi di semplificazione, l'uso di questo account non è consigliabile per i registri di produzione.</span><span class="sxs-lookup"><span data-stu-id="8179b-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="8179b-327">Il comando `az acr create` visualizza l'URL del server di accesso (tramite la colonna `LOGIN SERVER`) usato per accedere con l'interfaccia della riga di comando di Docker, ad esempio `ninademo.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="8179b-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="8179b-328">Il comando genera anche le credenziali di amministratore usate per l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="8179b-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="8179b-329">Per recuperare tali credenziali, eseguire questo comando e annotare il nome utente e la password visualizzati:</span><span class="sxs-lookup"><span data-stu-id="8179b-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="8179b-330">Usando le credenziali del passaggio precedente e il proprio server di accesso è possibile accedere al registro tramite il flusso di lavoro standard dell'interfaccia della riga di comando di Docker.</span><span class="sxs-lookup"><span data-stu-id="8179b-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="8179b-331">È ora possibile contrassegnare il contenitore Docker per indicare che è associato al registro privato usando il comando seguente, in cui è necessario sostituire `lostintangent/node` con il nome assegnato all'immagine del contenitore.</span><span class="sxs-lookup"><span data-stu-id="8179b-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="8179b-332">Eseguire infine il push dell'immagine contrassegnata nel registro Docker privato.</span><span class="sxs-lookup"><span data-stu-id="8179b-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="8179b-333">Il contenitore è ora archiviato nel proprio registro privato e l'interfaccia della riga di comando di Docker consente di continuare a lavorare esattamente come quando si usa DockerHub.</span><span class="sxs-lookup"><span data-stu-id="8179b-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="8179b-334">Per indicare all'app Web del servizio app di effettuare il pull dal registro privato, è sufficiente eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="8179b-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="8179b-335">Aggiungere il prefisso `https://` all'inizio dell'opzione `-r`.</span><span class="sxs-lookup"><span data-stu-id="8179b-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="8179b-336">Non aggiungere tuttavia il prefisso al nome dell'immagine del contenitore.</span><span class="sxs-lookup"><span data-stu-id="8179b-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="8179b-337">Aggiornando l'app nel browser, l'aspetto e il funzionamento rimarranno invariati.</span><span class="sxs-lookup"><span data-stu-id="8179b-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="8179b-338">L'app viene ora tuttavia eseguita tramite il registro Docker privato.</span><span class="sxs-lookup"><span data-stu-id="8179b-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="8179b-339">Dopo aver aggiornato l'app, contrassegnare ed eseguire il push delle modifiche come in precedenza e aggiornare il tag nella configurazione del contenitore del servizio app.</span><span class="sxs-lookup"><span data-stu-id="8179b-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="8179b-340">Configurazione di un nome di dominio personalizzato</span><span class="sxs-lookup"><span data-stu-id="8179b-340">Configuring a custom domain name</span></span>

<span data-ttu-id="8179b-341">Anche se l'URL `*.azurewebsites.net` è un'ottima opzione per i test, può essere successivamente opportuno aggiungere un nome di dominio personalizzato all'app Web.</span><span class="sxs-lookup"><span data-stu-id="8179b-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="8179b-342">Dopo aver ottenuto un nome di dominio da un registrar, è sufficiente aggiungere al nome un record `A` che punti all'indirizzo IP esterno dell'app Web, che è in realtà un bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="8179b-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="8179b-343">Questo indirizzo IP può essere recuperato con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="8179b-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="8179b-344">Oltre ad aggiungere un record `A` è necessario aggiungere al dominio un record `TXT` che punti al dominio `*.azurewebsites.net` usato finora.</span><span class="sxs-lookup"><span data-stu-id="8179b-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="8179b-345">La combinazione dei record `A` e `TXT` consente ad Azure di verificare che si è proprietari del dominio.</span><span class="sxs-lookup"><span data-stu-id="8179b-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="8179b-346">Dopo aver creato i record e aver propagato le modifiche DNS, registrare il dominio personalizzato con Azure per indicare l'origine corretta del traffico in ingresso.</span><span class="sxs-lookup"><span data-stu-id="8179b-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="8179b-347">Il comando non funziona fino a quando le modifiche DNS non vengono propagate.</span><span class="sxs-lookup"><span data-stu-id="8179b-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="8179b-348">Aprire un browser e passare al dominio personalizzato per verificare che ora si risolva nell'app distribuita in Azure.</span><span class="sxs-lookup"><span data-stu-id="8179b-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="8179b-349">Aumentare le prestazioni e il numero di istanze</span><span class="sxs-lookup"><span data-stu-id="8179b-349">Scaling up and out</span></span>

<span data-ttu-id="8179b-350">A un certo punto, l'app Web può diventare talmente diffusa che le risorse allocate (CPU e RAM) non sono più sufficienti a gestire l'aumento del traffico e delle esigenze operative.</span><span class="sxs-lookup"><span data-stu-id="8179b-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="8179b-351">Il piano del servizio app creato in precedenza (**B1**) prevede 1 core CPU e 1,75 GB di RAM, che si esauriscono abbastanza rapidamente.</span><span class="sxs-lookup"><span data-stu-id="8179b-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="8179b-352">Il piano **B2** offre il doppio di RAM e CPU, quindi se si nota che l'app inizia a esaurire queste risorse è possibile aumentare le prestazioni della macchina virtuale sottostante eseguendo questo comando:</span><span class="sxs-lookup"><span data-stu-id="8179b-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="8179b-353">Per i dettagli e le specifiche dei prezzi dei piani app di Azure, vedere l'articolo [Prezzi di Servizio app](https://azure.microsoft.com/pricing/details/app-service/)</span><span class="sxs-lookup"><span data-stu-id="8179b-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="8179b-354">Dopo pochi istanti verrà eseguita la migrazione dell'app Web all'hardware richiesto e sarà possibile iniziare a sfruttare le risorse associate.</span><span class="sxs-lookup"><span data-stu-id="8179b-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="8179b-355">Le prestazioni possono anche essere ridotte eseguendo lo stesso comando indicato in precedenza, specificando un'opzione `--sku` che offre meno risorse a un prezzo inferiore.</span><span class="sxs-lookup"><span data-stu-id="8179b-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="8179b-356">Oltre ad aumentare le prestazioni per le macchine virtuali, finché l'app Web è senza stato, è anche possibile *aumentare il numero di istanze* aggiungendo più istanze di macchina virtuale sottostanti.</span><span class="sxs-lookup"><span data-stu-id="8179b-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="8179b-357">Il piano del servizio app creato in precedenza include una sola macchina virtuale (un *ruolo di lavoro*) e quindi tutto il traffico in ingresso è vincolato ai limiti delle risorse disponibili per quella sola istanza.</span><span class="sxs-lookup"><span data-stu-id="8179b-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="8179b-358">Se si vuole aggiungere una seconda istanza di macchina virtuale, è possibile eseguire lo stesso comando eseguito in precedenza, ma invece di aumentare lo SKU si aumenta il numero di macchine virtuali di lavoro.</span><span class="sxs-lookup"><span data-stu-id="8179b-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="8179b-359">Quando si aumenta il numero di istanze di un'app Web come questa, il carico del traffico in ingresso viene bilanciato in modo trasparente tra tutte le istanze, aumentando così immediatamente la capacità senza modifiche al codice e senza preoccuparsi dell'infrastruttura necessaria.</span><span class="sxs-lookup"><span data-stu-id="8179b-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="8179b-360">Le app Web senza stato sono considerate procedure consigliate perché rendono la scalabilità (aumento o riduzione delle prestazioni e aumento del numero di istanze) interamente deterministica, poiché nessuna macchina virtuale o istanza dell'app include uno stato necessario per il funzionamento.</span><span class="sxs-lookup"><span data-stu-id="8179b-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="8179b-361">Anche se l'esercitazione di questo argomento illustra l'esecuzione di una singola app Web nell'ambito di un piano di servizio app, è possibile creare e distribuire più app Web nello stesso piano, consentendo di effettuare il provisioning e sostenere i costi di un singolo piano.</span><span class="sxs-lookup"><span data-stu-id="8179b-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="8179b-362">Eliminazione</span><span class="sxs-lookup"><span data-stu-id="8179b-362">Clean-up</span></span>

<span data-ttu-id="8179b-363">Per evitare che vengano addebitate risorse di Azure non usate, eseguire questo comando dal terminale di Visual Studio Code per eliminare tutte le risorse delle quali è stato effettuato il provisioning durante questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="8179b-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="8179b-364">Il processo di eliminazione può richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="8179b-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="8179b-365">Al termine, il comando `az group delete` lascia l'account di Azure nello stato in cui si trovava prima di iniziare l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="8179b-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="8179b-366">La possibilità di organizzare, distribuire ed eliminare le risorse di Azure come singola unità è uno dei vantaggi principali dei gruppi di risorse.</span><span class="sxs-lookup"><span data-stu-id="8179b-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="8179b-367">Si consiglia quindi di raggruppare le risorse che si prevede abbiano la stessa durata.</span><span class="sxs-lookup"><span data-stu-id="8179b-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>