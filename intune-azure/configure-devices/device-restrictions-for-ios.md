---
title: Impostazioni relative alle restrizioni dei dispositivi per iOS
titleSuffix: Intune Azure preview
description: "Anteprima di Intune Azure: informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo con iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73590192-54ca-4833-9f1d-83e1b654399f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 01e8a6968797bc2b2b0f3bb5710ee396d9094584
ms.lasthandoff: 03/15/2017


---

# <a name="ios-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi iOS in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Generale
-     **Fotocamera** - Specifica se è consentito l'uso della fotocamera del dispositivo.     
-     **Invio dati di diagnostica** - Consente o impedisce al dispositivo di inviare dati di diagnostica ad Apple.
-     **FaceTime** - Consente l'uso dell'app FaceTime sul dispositivo.
-     **Acquisizione schermo** - Consente all'utente di acquisire il contenuto della schermata come immagine.
-     **Siri** - Consente l'uso dell'assistente vocale Siri sul dispositivo.
    -     **Siri quando il dispositivo è bloccato** - Consente l'uso dell'assistente vocale Siri quando il dispositivo è bloccato.
    -     **Filtro di Siri per le espressioni volgari (solo con supervisione)** - Impedisce a Siri di usare espressioni volgari.
    -     **Consenti a Siri di eseguire query sul contenuto generato dall'utente da Internet (solo con supervisione)** - Consente a Siri di accedere ai siti Web per rispondere a domande.
-     **Certificati TLS non attendibili** - Consente l'uso di certificati TLS non attendibili nel dispositivo.
-     **Accesso al centro di controllo durante il blocco del dispositivo** - Consente all'utente di accedere all'app centro di controllo mentre il dispositivo è bloccato.
-     **Notifiche durante il blocco del dispositivo** - Consente all'utente di accedere alla visualizzazione delle notifiche senza sbloccare il dispositivo.
-     **Passbook durante il blocco del dispositivo** - Consente all'utente di accedere all'app Passbook mentre il dispositivo è bloccato.
-     **Visualizzazione Oggi durante il blocco del dispositivo** - Consente all'utente di vedere la visualizzazione Oggi mentre il dispositivo è bloccato.
-     **Attendibilità dell'app aziendale** - Consente all'utente di scegliere di considerare attendibili le app che non sono state scaricate dall'App Store.
-     **AirDrop (solo con supervisione)** - Consente l'uso della funzionalità AirDrop per scambiare contenuti con i dispositivi presenti nelle vicinanze.
-     **Ricerca Spotlight per la restituzione di risultati da Internet (solo con supervisione)** -Consente alla ricerca Spotlight di connettersi a Internet per fornire ulteriori risultati.
-     **Ricerca della definizione delle parole (solo con supervisione)** - Consente la funzionalità di iOS che permette di evidenziare una parola e cercarne la definizione.
-     **Tastiere predittive (solo con supervisione)** - Consente l'uso di tastiere predittive che suggeriscono all'utente i termini desiderati.
-     **Correzione automatica (solo con supervisione)** - Consente al dispositivo di correggere automaticamente le parole errate.
-     **Controllo ortografico tastiera (solo con supervisione)** - Consente il controllo ortografico nel dispositivo.
-     **Scelte rapida da tastiera (solo con supervisione)** - Consente l'uso dei tasti di scelta rapida.
-     **Rilevamento del polso per l'Apple Watch associato** - Quando l'opzione è abilitata, Apple Watch non visualizza notifiche se non è indossato.
- **Richiedi la password associata alle richieste AirPlay in uscita** - Richiede una password di associazione quando l'utente usa AirPlay per trasmettere i contenuti ad altri dispositivi di Apple.
- **Modifica dell'account (solo con supervisione)** - Consente all'utente di modificare le impostazioni dell'account, ad esempio le configurazioni di posta elettronica.
- **Associazione di Apple Watch (solo con supervisione)** - Consente al dispositivo di associare un Apple Watch.
- **Modifica Bluetooth (solo con supervisione)** - Impedisce all'utente finale di modificare le impostazioni Bluetooth nel dispositivo.
- **Osservazione dello schermo remoto da parte dell'app Classroom (solo con supervisione)** - Consente o blocca l'osservazione dello schermo dei dispositivi remoti da parte dell'app Classroom.
- **Abilitazione delle restrizioni nelle impostazioni del dispositivo (solo con supervisione)** - Consente all'utente di configurare restrizioni (controllo genitori) sul dispositivo.
- **Uso dell'opzione di cancellazione di tutti i contenuti e tutte le impostazioni sul dispositivo (solo con supervisione)** - Consente all'utente di usare l'opzione di cancellazione di tutti i contenuti e le impostazioni del dispositivo.
- **Modifica del nome dispositivo (solo con supervisione)** - Consente all'utente di modificare il nome del dispositivo.
- **Modifica delle impostazioni di invio dei dati di diagnostica (solo con supervisione)** - Consente o impedisce al dispositivo di inviare dati di diagnostica ad Apple.
- **Associazione di host per controllare i dispositivi a cui può essere associato un dispositivo iOS (solo con supervisione)** - Consente l'abbinamento host in modo che l'amministratore possa controllare a quali dispositivi il dispositivo iOS può essere associato.
- **Modifica delle impostazioni di notifica (solo con supervisione)** - Consente all'utente di modificare le impostazioni di notifica del dispositivo.
- **Modifica del passcode (solo con supervisione)** - Consente di aggiungere, modificare o rimuovere la password del dispositivo.
- **Modifica dello sfondo (solo con supervisione)** - Consente all'utente di cambiare lo sfondo del dispositivo.
- **Modifica delle impostazioni di attendibilità delle app aziendali (solo con supervisione)** - Consente all'utente di scegliere di considerare attendibili le app che non sono state scaricate dall'App Store.
- **Installazione di app dall'App Store (solo con supervisione)** - Consente al dispositivo di accedere all'App Store e installare le app.
- **Modifiche alle impostazioni dell'app Find My Friends (solo con supervisione)** - Consente all'utente di modificare le impostazioni per l'app Find My Friends.
- **iBooks store (solo con supervisione)** - Consente all'utente di selezionare e acquistare libri dall'iBooks Store.
- **App Messages sul dispositivo (solo con supervisione)** - Consente di usare l'app Messages per inviare e leggere SMS.
- **Podcasts (solo con supervisione)** - Consente l'uso dell'app Podcasts.
- **Servizio Music (solo con supervisione)** - Consente l'uso dell'app Music di Apple.
- **Servizio iTunes Radio (solo con supervisione)** - Consente l'uso dell'app iTunes Radio.
- **Apple News (solo con supervisione)** - Consente l'uso dell'app Apple News.
- **Modifiche al profilo di configurazione** - Consente all'utente di installare profili di configurazione.

## <a name="password"></a>Password
-     **Password necessaria** - Richiede all'utente finale di immettere una password per accedere al dispositivo.
-     **Password semplici** - Consente l'uso di password semplici come 0000 e 1234.
-     **Tipo di password richiesto** - Specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.
-     **Numero di caratteri non alfanumerici nella password** - Specifica il numero di simboli, ad esempio **#** o **@**, che è necessario includere nella password.
-     **Lunghezza minima password** - Specifica il numero minimo di caratteri per la password.
-     **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Specifica il numero di tentativi di accesso non riusciti prima che questa impostazione cancelli il dispositivo.
-     **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta la password**<sup>1</sup> - Specifica quanto tempo il dispositivo può rimanere inattivo prima che l'utente debba immettere nuovamente la password.
-     **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**<sup>1</sup> - Specifica il numero di minuti prima che la visualizzazione del dispositivo sia disattivata.
-     **Scadenza password (giorni)** - Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.
-     **Impedisci riutilizzo delle password precedenti** - Specifica il numero di password utilizzate in precedenza che il dispositivo deve ricordare.
-     **Sblocco con impronta digitale** - Consente di usare un'impronta digitale per sbloccare i dispositivi compatibili.

<sup>1</sup>Quando si configurano le impostazioni **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password** e **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**, queste vengono applicate in sequenza. Ad esempio, se si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo 5 minuti e il dispositivo viene bloccato dopo altri 5 minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio, il dispositivo viene bloccato 5 minuti dopo che l'utente spegne lo schermo.

## <a name="app-store-doc-viewing-gaming"></a>App Store, visualizzazione documenti, giochi


-   **App Store (solo con supervisione)** - Blocca l'accesso all'App Store nei dispositivi con supervisore.
-     **Password per l'accesso all'App Store** - Richiede all'utente di immettere la password prima di visitare l'App Store.
-     **Acquisti in-app** - Consente gli acquisti online dall'interno di un'app in esecuzione.
-     **Download automatici delle app (solo con supervisione)** -
-     **Musica di iTunes, podcast o notizie con contenuti espliciti (solo con supervisione)** -Consente al dispositivo di accedere al contenuto classificato come "per adulti" dall'archivio.
-     **Scarica da iBook Store i contenuti contrassegnati come "Erotici"** - Consente all'utente di scaricare contenuti da iBook Store contrassegnati come "Erotici".
-     **Visualizzazione dei documenti aziendali nelle app non gestite** - Consente di visualizzare i documenti aziendali in qualsiasi app.<br>**Esempio:** si vuole impedire agli utenti il salvataggio di file dall'app OneDrive a Dropbox. Disabilitare questa impostazione. Dopo aver ricevuto i criteri, ad esempio dopo un riavvio, il dispositivo non consentirà più il salvataggio.
-     **Visualizzazione di documenti non aziendali nelle app aziendali** - Consente di visualizzare qualsiasi documento nelle app aziendali gestite.
-     **Considera AirDrop come destinazione non gestita** - Impedisce alle app gestite di inviare dati. AirDrop.
-     **Aggiunta di amici di Game Center (solo con supervisione)** - Consente all'utente di aggiungere amici in Game Center.
-     **Game Center (solo con supervisione)** - Impedisce o consente l'uso dell'app Game Center.
-     **Giochi multiplayer (solo con supervisione)** - Consente all'utente di partecipare a giochi multiplayer sul dispositivo.
-     **Area classificazioni** - Scegliere l'area di classificazioni per cui si desidera configurare i download consentiti, quindi scegliere le classificazioni consentite per **film** e **programmi TV**.
-     **App** - Scegliere la fascia d'età consentita per le app che gli utenti potranno scaricare oppure è possibile scegliere **Consenti tutte le app**.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

Un elenco **App non consentite** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire.
Un elenco **App approvate** - Elenca le app che gli utenti sono autorizzati a installare. Per garantire la conformità, non installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL di app nell'elenco delle app, usare il formato seguente:

Usando un motore di ricerca, trovare l'app da usare nell'App Store iTunes e aprire la pagina per l'app.
Copiare l'URL della pagina e usarlo per la configurazione dell'elenco delle app consentite o proibite o di un'app da eseguire in modalità tutto schermo.
I profili dispositivo che contengono impostazioni per app con restrizioni devono essere distribuiti ai gruppi di utenti.

Esempio: cercare Microsoft Word per iPad. L'URL utilizzato sarà https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> È possibile usare anche il software iTunes per trovare l'app e il comando **Copia collegamento** per ottenere l'URL dell'app.



### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app con restrizioni nello stesso formato.

## <a name="show-or-hide-apps"></a>Mostrare o nascondere app

Nell'elenco delle app da mostrare o nascondere è possibile configurare uno degli elenchi seguenti (richiede dispositivi con supervisore che eseguono iOS 9.3 o versione successiva).

Un elenco **App nascoste** - Specifica un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
Un elenco **App visibili** - Specifica un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL di app nell'elenco delle app, usare il formato seguente:

Usando un motore di ricerca, trovare l'app da usare nell'App Store iTunes e aprire la pagina per l'app.
Copiare l'URL della pagina e usarlo per la configurazione dell'elenco delle app consentite o proibite o di un'app da eseguire in modalità tutto schermo.

Esempio: cercare Microsoft Word per iPad. L'URL utilizzato sarà https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> È possibile usare anche il software iTunes per trovare l'app e il comando **Copia collegamento** per ottenere l'URL dell'app.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app nascoste o visibili nello stesso formato.

### <a name="app-information-for-built-in-ios-apps"></a>Informazioni per app iOS incorporate
Usare le informazioni riportate in questo elenco per identificare il nome, l'autore e l'ID bundle delle app iOS incorporate che si vogliono mostrare o nascondere. Se si vuole mostrare o nascondere tutte le app dell'elenco, è possibile copiare i dati riportati di seguito in un file di testo con estensione **.csv** e quindi usare l'opzione **Importa** per importare tutte le app contemporaneamente.


    App Store,Apple,com.apple.AppStore
    Calculator,Apple,com.apple.calculator
    Calendar,Apple,com.apple.mobilecal
    Camera,Apple,com.apple.camera
    Clock,Apple,com.apple.mobiletimer
    Compass,Apple,com.apple.compass
    Contacts,Apple,com.apple.MobileAddressBook
    FaceTime,Apple,com.apple.facetime
    Find Friends,Apple,com.apple.mobileme.fmf1
    Find iPhone,Apple,com.apple.mobileme.fmip1
    Game Center,Apple,com.apple.gamecenter
    GarageBand,Apple,com.apple.mobilegarageband
    Health,Apple,com.apple.Health
    iBooks,Apple,com.apple.iBooks
    iTunes Store,Apple,com.apple.MobileStore
    iTunes U,Apple,com.apple.itunesu
    Keynote,Apple,com.apple.Keynote
    Mail,Apple,com.apple.mobilemail
    Maps,Apple,com.apple.Maps
    Messages,Apple,com.apple.MobileSMS
    Music,Apple,com.apple.Music
    News,Apple,com.apple.news
    Notes,Apple,com.apple.mobilenotes
    Numbers,Apple,com.apple.Numbers
    Pages,Apple,com.apple.Pages
    Photo Booth,Apple,com.apple.Photo-Booth
    Photos,Apple,com.apple.mobileslideshow
    Podcasts,Apple,com.apple.podcasts
    Reminders,Apple,com.apple.reminders
    Safari,Apple,com.apple.mobilesafari
    Settings,Apple,com.apple.Preferences
    Stocks,Apple,com.apple.stocks
    Tips,Apple,com.apple.tips
    Videos,Apple,com.apple.videos
    VoiceMemos,Apple,com.apple.VoiceMemos
    Wallet,Apple,com.apple.Passbook
    Watch,Apple,com.apple.Bridge
    Weather,Apple,com.apple.weather





## <a name="cellular"></a>Cellulare
-     **Roaming dati** - Consente il roaming dei dati quando il dispositivo si trova su una rete cellulare.
-     **Recupero in background globale durante il roaming** - Consente al dispositivo di recuperare dati come la posta elettronica durante il roaming su una rete cellulare.
-     **Chiamata vocale** - Consente l'uso della funzionalità di composizione vocale sul dispositivo.
-     **Roaming vocale** - Consente il roaming vocale quando il dispositivo è su una rete cellulare.
-     **Modifiche alle impostazioni dell'utilizzo della rete dati dell'app (solo con supervisione)** - Consente all'utente di controllare quali applicazioni possono usare i dati del cellulare.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
-     **Backup in iCloud** - Consente all'utente di eseguire il backup del dispositivo su iCloud.
-     **Sincronizzazione dei documenti in iCloud (solo con supervisione)** - Consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.
-     **Sincronizzazione dello streaming foto in iCloud** - Consente agli utenti di abilitare la funzionalità **Il mio streaming foto** nel dispositivo, che permette di sincronizzare le foto su iCloud in modo che siano disponibili in tutti i dispositivi degli utenti.
-     **Backup crittografato** - Richiede la crittografia di tutti i backup del dispositivo.
-     **Libreria foto di iCloud** - Se impostata su **No**, disabilita l'uso della libreria di foto di iCloud che consente agli utenti di archiviare foto e video nel cloud.    Eventuali foto non scaricate completamente dalla Libreria foto di iCloud nel dispositivo verranno rimosse dal dispositivo se questa opzione è impostata su **No**.
-     **Sincronizzazione delle app gestite nel cloud** - Consente alle app gestite con Intune di sincronizzare i dati con l'account iCloud dell'utente.
-     **Flusso di foto condivise** - Impostare su **No** per disabilitare **Condivisione foto di iCloud** nel dispositivo.
-     **Continuazione dell'attività** - Consente all'utente di proseguire il lavoro iniziato in un dispositivo iOS in un altro dispositivo iOS o macOS (Handoff).

## <a name="kiosk"></a>Modalità tutto schermo
-     **Blocco attivazione** - Abilita il blocco attivazione su dispositivi iOS con supervisione.
-     **App in esecuzione in modalità tutto schermo** - Scegliere **App gestita** per selezionare un'app che è stata aggiunta a Intune o **App dello Store** per specificare l'URL di un'app dello store. Non sarà possibile eseguire altre applicazioni nel dispositivo. Per informazioni, vedere "Come specificare gli URL negli App Store" più avanti in questo argomento.
-     **Tocco per l'accesso facilitato** - Abilita o disabilita l'impostazione di accessibilità **Tocco per l'accesso facilitato** che aiuta l'utente a eseguire sullo schermo movimenti che altrimenti risulterebbero difficili da eseguire.
-     **Inverti colori** - Abilita o disabilita l'impostazione di accessibilità Inverti colori che consente di regolare la visualizzazione per gli utenti con problemi visivi.
-     **Audio mono** - Abilita o disabilita l'impostazione di accessibilità Audio mono.
-     **VoiceOver** - Abilita o disabilita l'impostazione di **VoiceOver** per la lettura a voce alta del testo sullo schermo del dispositivo.
-     **Zoom** - Abilita o disabilita l'impostazione di accessibilità **Zoom** che consente di usare le funzionalità di tocco per ingrandire la visualizzazione del dispositivo.
-     **Blocco automatico** - Abilita o disabilita il blocco automatico del dispositivo.
-     **Commutatore suoneria** - Abilita o disabilita la suoneria nel dispositivo.
-     **Rotazione dello schermo** - Abilita o disabilita la modifica dell'orientamento dello schermo quando si ruota il dispositivo.
-     **Pulsante Sospensione schermo** - Abilita o disabilita il pulsante di sospensione dello schermo del dispositivo.
-     **Tocco** - Abilita o disabilita il touchscreen nel dispositivo.
-     **Pulsanti volume** - Abilita o disabilita l'uso dei pulsanti del volume nel dispositivo.
-     **Controllo del tocco per l'accesso facilitato** - Abilita o disabilita le regolazioni del tocco per l'accesso facilitato che consentono all'utente di modificare la funzione Tocco per l'accesso facilitato.
-     **Controllo dell'inversione colori** - Abilita o disabilita le regolazioni dell'inversione colori che consentono di modificare la funzione Inverti colori.
-     **Pronuncia per il testo selezionato** - Abilita o disabilita l'impostazione di accessibilità Abilita selezione comandi vocali che consente di leggere a voce alta il testo selezionato.
-     **Controllo VoiceOver** - Abilita o disabilita le regolazioni di voice over che consentono di modificare la funzione Voice over, ad esempio la velocità con cui viene letto il testo visualizzato sullo schermo.
-     **Controllo zoom** - Abilita o disabilita le regolazioni dello zoom che consentono di modificare la funzione di zoom.

>[!NOTE]
> Prima di poter configurare un dispositivo iOS per la modalità tutto schermo, è necessario usare lo strumento Apple Configurator o il programma di registrazione dispositivi di Apple per attivare la modalità con supervisore del dispositivo. Per altre informazioni sullo strumento Apple Configurator, vedere la documentazione di Apple.
>Se l'app per iOS specificata viene installata dopo aver distribuito i criteri di configurazione, il dispositivo non passerà alla modalità tutto schermo finché non viene riavviato.

## <a name="safari"></a>Safari
-     **Safari (solo con supervisione)** - Specifica se il browser Safari può essere usato nel dispositivo.
-     **Riempimento automatico** - Consente all'utente di modificare le impostazioni di completamento automatico nel browser.
-     **Cookie** - Consente l'uso dei cookie nel browser.
-     **JavaScript** - Consente l'esecuzione di script JavaScript nel browser.
-     **Avvisi illeciti** - Consente gli avvisi di illeciti nel browser.
-     **Popup** - Attiva o disattiva il blocco dei popup del browser.

