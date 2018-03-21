---
title: Impostazioni relative alle restrizioni dei dispositivi iOS in Microsoft Intune
titleSuffix: 
description: "Informazioni sulle opzioni di Intune per il controllo di impostazioni e funzionalità nei dispositivi iOS."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b0523a514eb9d6a5c0429f1a2e2fa84d1ca00de4
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="microsoft-intune-ios-device-restriction-settings"></a>Impostazioni relative alle restrizioni dei dispositivi iOS in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni relative alle restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi che eseguono iOS.

## <a name="general"></a>Generale

-   **Condividi i dati di utilizzo** - Consente o impedisce al dispositivo di inviare dati di diagnostica e di telemetria dell'utilizzo ad Apple.
-   **Invio dati di diagnostica** - Consente o impedisce al dispositivo di inviare dati di diagnostica ad Apple.
-   **Acquisizione schermo** - Consente all'utente di acquisire il contenuto della schermata come immagine.
    - **Osservazione dello schermo remoto da parte dell'app Classroom (solo con supervisione)** - Consente o blocca l'osservazione dello schermo di dispositivi iOS da parte dell'app Apple Classroom.
    - **Osservazione dello schermo non richiesta da parte dell'app Classroom (solo con supervisione)** - Se consentita, gli insegnanti possono osservare lo schermo dei dispositivi iOS degli studenti con l'app Classroom senza che questi ne siano a conoscenza.
-   **Certificati TLS non attendibili** - Consente l'uso di certificati TLS non attendibili nel dispositivo.
-   **Attendibilità dell'app aziendale** - Consente all'utente di scegliere di considerare attendibili le app che non sono state scaricate dall'App Store.
- **Modifica dell'account (solo con supervisione)** - Quando è bloccata, impedisce all'utente di modificare le impostazioni specifiche dei dispositivi dall'app delle impostazioni iOS, ad esempio creare nuovi account di dispositivo e modificare il nome utente o la password.
Questa opzione si applica anche alle impostazioni accessibili dall'app delle impostazioni iOS come Posta, Contatti, Calendario, Facebook e Twitter. Non si applica alle app con impostazioni dell'account non configurabili dall'app delle impostazioni iOS, ad esempio Microsoft Outlook.
- **Abilitazione delle restrizioni nelle impostazioni del dispositivo (solo con supervisione)** - Consente all'utente di configurare restrizioni (controllo genitori) sul dispositivo.
- **Uso dell'opzione di cancellazione di tutti i contenuti e tutte le impostazioni sul dispositivo (solo con supervisione)** - Consente all'utente di usare l'opzione di cancellazione di tutti i contenuti e le impostazioni del dispositivo.
- **Modifica del nome dispositivo (solo con supervisione)** - Consente all'utente di modificare il nome del dispositivo.
- **Modifica delle impostazioni di notifica (solo con supervisione)** - Consente all'utente di modificare le impostazioni di notifica del dispositivo.
- **Modifica dello sfondo (solo con supervisione)** - Consente all'utente di cambiare lo sfondo del dispositivo.
- **Modifica delle impostazioni di attendibilità delle app aziendali (solo con supervisione)** - Consente all'utente di scegliere di considerare attendibili le app che non sono state scaricate dall'App Store.
- **Modifiche al profilo di configurazione (solo con supervisione)** - Consente all'utente di installare profili di configurazione.
- **Blocco attivazione (solo con supervisione)** - Abilita il blocco attivazione su dispositivi iOS con supervisione.

## <a name="configurations-requiring-supervision"></a>Configurazioni che richiedono supervisione

La modalità con supervisione iOS può essere abilitata solo durante l'installazione iniziale del dispositivo tramite Device Enrollment Program di Apple o Apple Configurator. Dopo aver abilitato la modalità di supervisione, Intune può configurare un dispositivo con le funzionalità seguenti:

- Blocco dell'app (modalità app singola) 
- Proxy HTTP globale 
- Bypass del blocco attivazione 
- Modalità applicazione singola autonoma 
- Filtro contenuto Web 
- Impostazione dello sfondo e della schermata di blocco 
- Push app invisibile all'utente 
- VPN Always On 
- Installazione esclusivamente di app gestite 
- iBookstore 
- iMessages 
- Area giochi 
- AirDrop 
- AirPlay 
- Associazione di host 
- Sincronizzazione cloud 
- Ricerca Spotlight 
- Handoff 
- Cancellazione di dispositivi 
- Interfaccia utente restrizioni 
- Installazione di profili di configurazione tramite interfaccia utente 
- Notizie 
- Tasti di scelta rapida 
- Modifica del passcode 
- Modifica di nomi di dispositivo 
- Modifica dello sfondo 
- Download automatici delle app 
- Modifica dell'attendibilità delle applicazioni enterprise 
- Apple Music 
- Mail Drop 
- Associazione con Apple Watch 

> [!NOTE]
> Apple ha confermato che nel 2018 alcune impostazioni passeranno alla modalità solo con supervisione. È consigliabile usare le impostazioni interessate tenendo conto di questo aspetto, anziché attendere che Apple effettui la migrazione alla modalità solo con supervisione:
> - Installazione di app da parte degli utenti finali
> - Rimozione di app
> - FaceTime
> - Safari
> - iTunes
> - Contenuti espliciti
> - Documenti e dati iCloud
> - Gioco multiplayer
> - Aggiungi amici dell'area giochi

## <a name="password"></a>Password
-   **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
    -   **Password semplici**: consente l'uso di password semplici come 0000 e 1234.
    -   **Tipo di password richiesto**: specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.
    -   **Numero di caratteri non alfanumerici nella password** - Specifica il numero di simboli, ad esempio **#** o **@**, che è necessario includere nella password.
    -   **Lunghezza minima password** - Specifica il numero minimo di caratteri per la password.
    -   **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Specifica il numero di tentativi di accesso non riusciti prima che questa impostazione cancelli il dispositivo.
    -   **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta la password**<sup>1</sup>: specifica il tempo per il quale il dispositivo può rimanere inattivo prima che l'utente debba immettere nuovamente la password.
    -   **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**<sup>1</sup> - Specifica il numero di minuti prima che la visualizzazione del dispositivo sia disattivata.
    -   **Scadenza password (giorni)** - Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.
    -   **Impedisci riutilizzo delle password precedenti** - Specifica il numero di password usate in precedenza che il dispositivo deve ricordare.
    -   **Sblocco con impronta digitale** - Consente di usare un'impronta digitale per sbloccare i dispositivi compatibili.
- **Modifica del passcode (solo con supervisione)** - Impedisce la modifica, l'aggiunta o la rimozione del passcode.
    - **Modifica dell'impronta digitale (solo con supervisione)** - Impedisce all'utente di modificare, aggiungere o rimuovere le impostazioni del TouchID.

<sup>1</sup>Quando si configurano le impostazioni **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password** e **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**, queste vengono applicate in sequenza. Se ad esempio si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo cinque minuti e il dispositivo viene bloccato dopo altri cinque minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio il dispositivo viene bloccato cinque minuti dopo che l'utente spegne lo schermo.

## <a name="locked-screen-experience"></a>Esperienza della schermata di blocco

-   **Accesso al centro di controllo durante il blocco del dispositivo** - Consente all'utente di accedere all'app centro di controllo mentre il dispositivo è bloccato.
-   **Notifiche durante il blocco del dispositivo** - Consente all'utente di accedere alla visualizzazione delle notifiche senza sbloccare il dispositivo.
-   **Passbook durante il blocco del dispositivo** - Consente all'utente di accedere all'app Passbook mentre il dispositivo è bloccato.
-   **Visualizzazione Oggi durante il blocco del dispositivo** - Consente all'utente di vedere la visualizzazione Oggi mentre il dispositivo è bloccato.

## <a name="app-store-doc-viewing-gaming"></a>App Store, visualizzazione documenti, giochi


-   **App Store** - Blocca l'accesso all'App Store nei dispositivi con supervisione.
    - **Installazione di app dall'App Store (solo con supervisione)** - Blocca l'App Store dalla schermata iniziale dei dispositivi. Gli utenti finali possono continuare a usare iTunes o Apple Configurator per installare le app.
    - **Download automatici delle app (solo con supervisione)** -Impedisce il download nel dispositivo delle app acquistate in un altro dispositivo iOS.
-   **Password per l'accesso all'App Store** - Richiede all'utente di immettere la password prima di visitare l'App Store.
-   **Acquisti in-app** - Consente gli acquisti online dall'interno di un'app in esecuzione.
-   **Musica di iTunes, podcast o notizie con contenuti espliciti (solo con supervisione)** -Consente al dispositivo di accedere al contenuto classificato come "per adulti" dall'archivio.
-   **Scarica da iBook Store i contenuti contrassegnati come "Erotici"** - Consente all'utente di scaricare contenuti da iBook Store contrassegnati come "Erotici".
-   **Visualizzazione dei documenti aziendali nelle app non gestite** - Consente di visualizzare i documenti aziendali in qualsiasi app.<br>**Esempio:** si vuole impedire agli utenti il salvataggio di file dall'app OneDrive a Dropbox. Disabilitare questa impostazione. Dopo aver ricevuto i criteri, ad esempio dopo un riavvio, il dispositivo non consentirà più il salvataggio.
-   **Visualizzazione di documenti non aziendali nelle app aziendali** - Consente di visualizzare qualsiasi documento nelle app aziendali gestite.
-   **Considera AirDrop come destinazione non gestita** - Impedisce alle app gestite di inviare dati. AirDrop.
-   **Aggiunta di amici di Game Center (solo con supervisione)** - Consente all'utente di aggiungere amici in Game Center.
-   **Game Center (solo con supervisione)** - Impedisce o consente l'uso dell'app Game Center.
-   **Giochi multiplayer (solo con supervisione)** - Consente all'utente di partecipare a giochi multiplayer sul dispositivo.
-   **Area classificazioni** - Scegliere l'area di classificazioni per cui si desidera configurare i download consentiti, quindi scegliere le classificazioni consentite per **film** e **programmi TV**.
-   **App** - Scegliere la fascia d'età consentita per le app che gli utenti possono scaricare. In alternativa è possibile scegliere **Consenti tutte le app**.

## <a name="built-in-apps"></a>App predefinite

-   **Fotocamera** - Specifica se è consentito l'uso della fotocamera del dispositivo.
    -   **FaceTime** - Consente l'uso dell'app FaceTime sul dispositivo.
-   **Siri** - Consente l'uso dell'assistente vocale Siri sul dispositivo.
    -   **Siri quando il dispositivo è bloccato** - Consente l'uso dell'assistente vocale Siri quando il dispositivo è bloccato.
    -   **Filtro di Siri per le espressioni volgari (solo con supervisione)** - Impedisce a Siri di usare espressioni volgari.
    -   **Consenti a Siri di eseguire query sul contenuto generato dall'utente da Internet (solo con supervisione)** - Consente a Siri di accedere ai siti Web per rispondere a domande.
- **Apple News (solo con supervisione)** - Consente l'uso dell'app Apple News.
- **iBooks store (solo con supervisione)** - Consente all'utente di selezionare e acquistare libri dall'iBooks Store.
- **App Messages sul dispositivo (solo con supervisione)** - Consente di usare l'app Messages per inviare e leggere SMS.
- **Podcasts (solo con supervisione)** - Consente l'uso dell'app Podcasts.
- **Servizio Music (solo con supervisione)** - Consente l'uso dell'app Music di Apple.
- **Servizio iTunes Radio (solo con supervisione)** - Consente l'uso dell'app iTunes Radio.
- **Modifiche alle impostazioni dell'app Find My Friends (solo con supervisione)** - Consente all'utente di modificare le impostazioni per l'app Find My Friends.
- **Ricerca Spotlight per la restituzione di risultati da Internet (solo con supervisione)** -Consente alla ricerca Spotlight di connettersi a Internet per fornire ulteriori risultati.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

- Un elenco **App non consentite** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire. Agli utenti non viene impedito di installare un'app non consentita, ma se lo fanno si riceverà una segnalazione.
- Un elenco **App approvate** - Elenca le app che gli utenti sono autorizzati a installare. Gli utenti non devono installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite. Agli utenti non viene impedito di installare un'app non inclusa nell'elenco delle app approvate, ma se lo fanno si riceverà una segnalazione.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL di app nell'elenco delle app, usare il formato seguente:

Usando un motore di ricerca, trovare l'app da usare nell'App Store iTunes e aprire la pagina per l'app.
Copiare l'URL della pagina e usarlo per la configurazione dell'elenco delle app consentite o proibite o di un'app da eseguire in modalità tutto schermo.
I profili dispositivo che contengono impostazioni per app con restrizioni devono essere assegnati ai gruppi di utenti.

Esempio: cercare Microsoft Word per iPad. L'URL usato è https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> È anche possibile usare iTunes per trovare l'app e quindi il comando **Copia collegamento** per ottenere l'URL dell'app.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app con restrizioni nello stesso formato.

## <a name="show-or-hide-apps-supervised-only"></a>Mostra o nascondi le app (solo con supervisione)

Nell'elenco delle app da mostrare o nascondere è possibile configurare uno degli elenchi seguenti (richiede dispositivi con supervisore che eseguono iOS 9.3 o versione successiva).

Elenco **App nascoste**: specifica un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
Elenco **App visibili**: specifica un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL di app nell'elenco delle app, usare il formato seguente:

Usando un motore di ricerca, trovare l'app da usare nell'App Store iTunes e aprire la pagina per l'app.
Copiare l'URL della pagina e usarlo per la configurazione dell'elenco delle app consentite o proibite o di un'app da eseguire in modalità tutto schermo.

Esempio: cercare Microsoft Word per iPad. L'URL usato è https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> È possibile usare anche il software iTunes per trovare l'app e il comando **Copia collegamento** per ottenere l'URL dell'app.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app nascoste o visibili nello stesso formato.


## <a name="wireless"></a>Wireless
-   **Roaming dati** - Consente il roaming dei dati quando il dispositivo si trova su una rete cellulare.
-   **Recupero in background globale durante il roaming** - Consente al dispositivo di recuperare dati come la posta elettronica durante il roaming su una rete cellulare.
-   **Chiamata vocale** - Consente l'uso della funzionalità di composizione vocale sul dispositivo.
-   **Roaming vocale** - Consente il roaming vocale quando il dispositivo è su una rete cellulare.
-   **Modifiche alle impostazioni dell'utilizzo della rete dati dell'app (solo con supervisione)** - Consente all'utente di controllare quali applicazioni possono usare i dati del cellulare.
-   **Hotspot personale** - Non consente l'uso del dispositivo come hotspot personale. Questa impostazione potrebbe non essere compatibile con alcuni gestori.
-   **Aggiungi reti Wi-Fi solo tramite profili di configurazione (solo con supervisione)** - Consente al dispositivo di connettersi solo a reti Wi-Fi configurate con un profilo Wi-Fi di Intune.

- **Regole di utilizzo della rete cellulare (solo app gestite)** - Consente di definire i tipi di dati usabili dalle app gestite nelle reti cellulari. Scegliere tra:
    - **Blocca l'uso della rete dati** - È possibile bloccare l'uso della rete dati per ** Tutte le app gestite* oppure **scegliere app specifiche**.
    - **Blocca l'uso della rete dati durante il roaming** - È possibile bloccare l'uso della rete dati durante il roaming per ** Tutte le app gestite* oppure **scegliere app specifiche**.

## <a name="connected-devices"></a>Dispositivi connessi

-   **AirDrop (solo con supervisione)** - Consente l'uso della funzionalità AirDrop per scambiare contenuti con i dispositivi presenti nelle vicinanze.
-   **Associazione di Apple Watch (solo con supervisione)** - Consente al dispositivo di associare un Apple Watch.
-   **Rilevamento del polso per l'Apple Watch associato** - Quando l'opzione è abilitata, Apple Watch non visualizza notifiche se non è indossato.
-   **Modifica Bluetooth (solo con supervisione)** - Impedisce all'utente finale di modificare le impostazioni Bluetooth nel dispositivo.
-    **Associazione di host per controllare i dispositivi a cui può essere associato un dispositivo iOS (solo con supervisione)** - Consente l'abbinamento host in modo che l'amministratore possa controllare a quali dispositivi il dispositivo iOS può essere associato.
-   **Richiedi la password associata alle richieste AirPlay in uscita** - Richiede una password di associazione quando l'utente usa AirPlay per trasmettere i contenuti ad altri dispositivi di Apple.

## <a name="keyboard-and-dictionary"></a>Tastiera e dizionario

-   **Ricerca della definizione delle parole (solo con supervisione)** - Consente la funzionalità di iOS che consente di evidenziare una parola e cercarne la definizione.
-   **Tastiere predittive (solo con supervisione)** - Consente l'uso di tastiere predittive che suggeriscono all'utente i termini desiderati.
-   **Correzione automatica (solo con supervisione)** - Consente al dispositivo di correggere automaticamente le parole errate.
-   **Controllo ortografico tastiera (solo con supervisione)** - Consente il controllo ortografico nel dispositivo.
-   **Scelte rapida da tastiera (solo con supervisione)** - Consente l'uso dei tasti di scelta rapida.
-   **Dettatura (solo con supervisione)** - Impedisce all'utente di immettere testo con l'input vocale.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
-   **Backup in iCloud** - Consente all'utente di eseguire il backup del dispositivo su iCloud.
-   **Sincronizzazione dei documenti in iCloud (solo con supervisione)** - Consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.
-   **Sincronizzazione dello streaming foto in iCloud**: consente agli utenti di abilitare nel dispositivo la funzionalità **Il mio streaming foto**, che consente di sincronizzare le foto su iCloud in modo che siano disponibili in tutti i dispositivi degli utenti.
-   **Backup crittografato** - Richiede la crittografia di tutti i backup del dispositivo.
-   **Libreria foto di iCloud**: se impostata su **No** disabilita l'uso della libreria di foto di iCloud che consente agli utenti di archiviare foto e video nel cloud.   Eventuali foto non scaricate completamente dalla Libreria foto di iCloud nel dispositivo vengono rimosse dal dispositivo se questa opzione è impostata su **No**.
-   **Sincronizzazione delle app gestite nel cloud** - Consente alle app gestite con Intune di sincronizzare i dati con l'account iCloud dell'utente.
-   **Flusso di foto condivise** - Impostare su **No** per disabilitare **Condivisione foto di iCloud** nel dispositivo.
-   **Continuazione dell'attività** - Consente all'utente di proseguire il lavoro iniziato in un dispositivo iOS in un altro dispositivo iOS o macOS (Handoff).

## <a name="autonomous-single-app-mode-supervised-only"></a>Modalità applicazione singola autonoma (solo con supervisione)

Usare queste impostazioni per configurare dispositivi iOS in modo che eseguano specifiche app in modalità applicazione singola autonoma. Quando questa modalità è configurata e l'app è in esecuzione, il dispositivo è bloccato in modo che possa eseguire solo quell'app. Un esempio è quando si configura un'app che consente agli utenti di eseguire un test nel dispositivo. Quando le azioni dell'app sono state completate o si rimuovono questi criteri, il dispositivo torna allo stato normale.

### <a name="settings"></a>Impostazioni

- **Nome dell'app**: immettere il nome dell'app che viene visualizzato nell'elenco di app in questo pannello.
- **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per assistenza, vedere **Guida di riferimento agli ID bundle per le app iOS predefinite** in questo argomento.

Dopo aver specificato il nome di ogni app e ID, scegliere **Aggiungi** per aggiungerle all'elenco.

- **Importa**: importa un file di valori delimitati da virgole (CSV) contenente un elenco di nomi di app e di ID bundle associati.
- **Esporta**: esporta i nomi delle app e gli ID bundle associati configurati in un file con valori delimitati da virgole (CSV).

### <a name="bundle-id-reference-for-built-in-ios-apps"></a>Guida di riferimento agli ID bundle per le app iOS predefinite

Questo elenco include l'ID bundle di alcune app comuni iOS predefinite. Per l'ID bundle di altre app rivolgersi al fornitore del software.

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple


```


## <a name="kiosk-supervised-only"></a>Modalità tutto schermo (solo con supervisione)
-   **App in esecuzione in modalità tutto schermo** - Scegliere **App gestita** per selezionare un'app che è stata aggiunta a Intune o **App dello Store** per specificare l'URL di un'app dello store. Non sarà possibile eseguire altre app nel dispositivo. Per informazioni, vedere "Come specificare gli URL negli App Store" più avanti in questo argomento.
    -   **Tocco per l'accesso facilitato** - Abilita o disabilita l'impostazione di accessibilità **Tocco per l'accesso facilitato** che aiuta l'utente a eseguire sullo schermo movimenti che altrimenti risulterebbero difficili da eseguire.
    -   **Inverti colori** - Abilita o disabilita l'impostazione di accessibilità Inverti colori che consente di regolare la visualizzazione per gli utenti con problemi visivi.
    -   **Audio mono** - Abilita o disabilita l'impostazione di accessibilità Audio mono.
    -   **VoiceOver** - Abilita o disabilita l'impostazione di **VoiceOver** per la lettura a voce alta del testo sullo schermo del dispositivo.
    -   **Zoom** - Abilita o disabilita l'impostazione di accessibilità **Zoom** che consente di usare le funzionalità di tocco per ingrandire la visualizzazione del dispositivo.
    -   **Blocco automatico** - Abilita o disabilita il blocco automatico del dispositivo.
    -   **Commutatore suoneria** - Abilita o disabilita la suoneria nel dispositivo.
    -   **Rotazione dello schermo** - Abilita o disabilita la modifica dell'orientamento dello schermo quando si ruota il dispositivo.
    -   **Pulsante Sospensione schermo** - Abilita o disabilita il pulsante di sospensione dello schermo del dispositivo.
    -   **Tocco** - Abilita o disabilita il touchscreen nel dispositivo.
    -   **Pulsanti volume** - Abilita o disabilita l'uso dei pulsanti del volume nel dispositivo.
    -   **Controllo del tocco per l'accesso facilitato** - Abilita o disabilita le regolazioni del tocco per l'accesso facilitato che consentono all'utente di modificare la funzione Tocco per l'accesso facilitato.
    -   **Controllo dell'inversione colori** - Abilita o disabilita le regolazioni dell'inversione colori che consentono di modificare la funzione Inverti colori.
    -   **Pronuncia per il testo selezionato** - Abilita o disabilita l'impostazione di accessibilità Abilita selezione comandi vocali che consente di leggere a voce alta il testo selezionato.
    -   **Controllo VoiceOver** - Abilita o disabilita le regolazioni di voice over che consentono di modificare la funzione Voice over, ad esempio la velocità con cui viene letto il testo visualizzato sullo schermo.
    -   **Controllo zoom** - Abilita o disabilita le regolazioni dello zoom che consentono di modificare la funzione di zoom.

>[!NOTE]
> Prima di poter configurare un dispositivo iOS per la modalità tutto schermo, è necessario usare lo strumento Apple Configurator o il programma di registrazione dispositivi di Apple per attivare la modalità con supervisore del dispositivo. Per altre informazioni sullo strumento Apple Configurator, vedere la documentazione di Apple.
>Se l'app per iOS specificata viene installata dopo aver assegnato il profilo, il dispositivo non passerà alla modalità tutto schermo finché non viene riavviato.

## <a name="safari"></a>Safari
-   **Safari (solo con supervisione)** - Specifica se il browser Safari può essere usato nel dispositivo.
-   **Riempimento automatico** - Consente all'utente di modificare le impostazioni di completamento automatico nel browser.
-   **Cookie** - Consente l'uso dei cookie nel browser.
-   **JavaScript** - Consente l'esecuzione di script JavaScript nel browser.
-   **Avvisi illeciti** - Consente gli avvisi di illeciti nel browser.
-   **Popup** - Attiva o disattiva il blocco dei popup del browser.


## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domini di posta elettronica non contrassegnati

Nel campo **URL del dominio di posta elettronica** aggiungere uno o più URL all'elenco. Quando gli utenti finali ricevono un messaggio di posta elettronica da un dominio diverso da quelli configurati, il messaggio di posta elettronica viene contrassegnato come non attendibile nell'app di posta in iOS.


### <a name="managed-web-domains"></a>Domini Web gestiti

Nel campo **URL del dominio Web** aggiungere uno o più URL all'elenco. Quando i documenti vengono scaricati dal dominio specificato, sono considerati come gestiti. Questa impostazione si applica solo ai documenti scaricati tramite Safari.


### <a name="safari-password-autofill-domains"></a>Domini con compilazione automatica della password di Safari

Nel campo **URL del dominio** aggiungere uno o più URL all'elenco. Gli utenti possono salvare solo le password Web dagli URL in questo elenco. Questa impostazione si applica solo al browser Safari e ai dispositivi iOS 9.3 e versioni successive in modalità con supervisione. Se non si specifica nessun URL, è possibile salvare le password da tutti i siti web.
