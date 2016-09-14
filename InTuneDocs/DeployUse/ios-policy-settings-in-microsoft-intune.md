---
title: Impostazioni dei criteri di iOS | Microsoft Intune
description: "Creare criteri per il controllo delle impostazioni e delle funzionalità dei dispositivi iOS gestiti con Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cac39b60226939334032d954eb49d1417493b28d
ms.openlocfilehash: 00e3a1b65c8475384bb05e64a4ef9f5d9de348ff


---

# Impostazioni dei criteri di iOS in Microsoft Intune

Intune offre una gamma di impostazioni generali predefinite che è possibile configurare nei dispositivi iOS. È anche possibile usare lo strumento Apple Configurator per creare impostazioni personalizzate non disponibili in Intune.

## Impostazioni dei criteri di configurazione generali

Usare i **criteri di configurazione generali iOS** di Microsoft Intune per configurare:

-   **Impostazioni generali e di sicurezza del dispositivo**. Scegliere da un elenco di impostazioni predefinite che consentono di controllare una gamma di funzionalità e caratteristiche nel dispositivo.

-   **Modalità tutto schermo**. Bloccare un dispositivo per consentire solo l'uso di determinate funzionalità. Ad esempio, è possibile consentire a un dispositivo di eseguire solo un'app gestita specificata o disabilitare i pulsanti del volume in un dispositivo. Queste impostazioni potrebbero essere usate per un modello demo di un dispositivo o per un dispositivo dedicato all'esecuzione di una sola funzione, ad esempio un dispositivo POS.

-   **App conformi e non conformi**. Specificare un elenco di app conformi o non conformi rispetto ai requisiti aziendali. Nei dispositivi Android e iOS è possibile usare il **Report app non conformi** per visualizzare la conformità delle app specificate nell'elenco rispetto a quelle installate dagli utenti, senza impedire l'effettiva installazione dell'app.

> [!TIP]
> È possibile configurare i termini e le condizioni per essere sicuri che gli utenti siano informati del fatto che le app installate nel dispositivo, incluse quelle personali, verranno valutate e che le app non conformi verranno bloccate o segnalate come non conformi. Gli utenti dovranno quindi accettare questi termini e condizioni prima di poter registrare il dispositivo e usare il Portale aziendale per ottenere le app. Per altre informazioni sull'uso di termini e condizioni, vedere [Impostazioni dei criteri relativi a termini e condizioni in Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se l'impostazione che si sta cercando non viene visualizzata in questo argomento, è possibile crearla usando i criteri personalizzati iOS che consentono di importare le impostazioni create usando lo [strumento Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Per altre informazioni, vedere "Impostazioni di criteri personalizzati" più avanti in questo argomento.

### Impostazioni di sicurezza
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Richiedi una password per sbloccare i dispositivi mobili**|Specificare se l'utente deve inserire una password per accedere al proprio dispositivo.|
|**Tipo di password richiesto**|Specificare il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.|
|**Numero di caratteri complessi richiesti nella password**|Specificare il numero di simboli, ad esempio **#** o **@**, che è necessario includere nella password.|
|**Lunghezza minima password**|Specificare il numero minimo di caratteri per la password.|
|**Consenti password semplici**|Consentire l'uso di password semplici come **0000** e **1234**.|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Specificare il numero di tentativi di accesso non riusciti prima che questa impostazione cancelli il dispositivo.|
|**Minuti di inattività prima che venga richiesta la password**<sup>1</sup>|Specificare per quanto tempo il dispositivo può rimanere inattivo prima che l'utente debba immettere di nuovo la password.|
|**Scadenza password (giorni)**|Specificare il numero di giorni prima che sia necessario modificare la password del dispositivo.|
|**Ricorda cronologia password**|Specificare se l'utente può scegliere password già usate in precedenza.|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specificare il numero di password usate in precedenza che il dispositivo deve ricordare.|
|**Minuti di inattività prima dello spegnimento dello schermo**<sup>1</sup>|Specifica il numero di minuti prima dello spegnimento dello schermo del dispositivo.|
|**Consenti sblocco delle impronte digitali**|Consente di sbloccare il dispositivo con un'impronta digitale.|
<sup>1</sup> Nei dispositivi iOS, se le impostazioni **Minuti di inattività prima dello spegnimento dello schermo** e **Minuti di inattività prima che venga richiesta la password** sono configurate, vengono applicate in sequenza. Ad esempio, se si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo 5 minuti e il dispositivo viene bloccato dopo altri 5 minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio, il dispositivo viene bloccato 5 minuti dopo che l'utente spegne lo schermo.

### Impostazioni di sistema
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti screenshot**|Consentire all'utente di acquisire il contenuto della schermata come immagine.|
|**Consenti centro di controllo nella schermata di blocco**|Consentire all'utente di accedere all'app centro di controllo mentre il dispositivo è bloccato.|
|**Consenti visualizzazione notifiche nella schermata di blocco**|Consente all'utente di accedere alla visualizzazione delle notifiche senza sbloccare il dispositivo.|
|**Consenti visualizzazione Oggi nella schermata di blocco**|Consentire all'utente di visualizzare le notifiche quando il dispositivo è bloccato.|
|**Consenti certificati TLS (Transport Layer Security) non attendibili**|Consente l'uso di certificati TLS non attendibili nel dispositivo.|
|**Consenti invio dati di diagnostica**|Consente o blocca l'invio di dati di diagnostica ad Apple dal dispositivo.|
|**Consenti passbook durante il blocco**|Consente all'utente di accedere all'app Passbook mentre il dispositivo è bloccato.|

### Impostazioni cloud per documenti e dati
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti backup su iCloud**|Consentire all'utente di eseguire il backup del dispositivo su iCloud.|
|**Consenti sincronizzazione documenti su iCloud**|Consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.|
|**Consenti sincronizzazione streaming foto su iCloud**|Consente la sincronizzazione delle foto del dispositivo su iCloud.|
|**Richiedi backup crittografato**|Richiede la crittografia di tutti i backup del dispositivo.|
|**Consenti alle app gestite di sincronizzare i dati in iCloud**|Consentire alle app gestite con Intune di sincronizzare i dati con l'account iCloud dell'utente.|
|**Consenti a Handoff di continuare le attività in un altro dispositivo**|Consentire all'utente di proseguire il lavoro iniziato in un dispositivo iOS in un altro dispositivo iOS o Mac OS X.|
|**Consenti la condivisione di foto con iCloud**|Consentire l'uso della funzionalità di streaming foto condiviso iOS.|
|**Consenti la raccolta di foto con iCloud**|Consentire all'utente di archiviare le foto in iCloud. Se disabilitata, eventuali foto già archiviate in iCloud verranno rimosse.|

### Impostazioni dell'applicazione per il browser
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti Safari**|Specifica se il browser Safari può essere usato nel dispositivo.|
|**Consenti riempimento automatico**|Consentire all'utente di modificare le impostazioni di completamento automatico nel browser.|
|**Consenti blocco popup**|Attiva o disattiva il blocco dei popup del browser.|
|**Consenti cookie**|Consentire l'uso dei cookie nel browser.|
|**Consenti scripting Java**|Consente l'esecuzione di script Java nel browser.|
|**Consenti avviso illeciti**|Consentire gli avvisi di illeciti nel browser.|

### Impostazioni dell'applicazione per le app
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti l'installazione di app**|Consentire al dispositivo di accedere all'App Store e installare le app.|
|**Richiedi una password per accedere all'archivio applicazioni**|Richiedere all'utente di immettere la password prima di visitare l'App Store.|
|**Consenti acquisti in-app**|Consente gli acquisti online dall'interno di un'app in esecuzione.|
|**Consenti documenti gestiti in altre app non gestite**|Consente di visualizzare documenti aziendali in qualsiasi app.<br>**Esempio:** si vuole impedire agli utenti il salvataggio di file dall'app OneDrive a Dropbox. Disabilitare questa impostazione. Dopo aver ricevuto i criteri, ad esempio dopo un riavvio, il dispositivo non consentirà più il salvataggio.|
|**Consenti documenti non gestiti in altre app gestite**|Consente di visualizzare qualsiasi documento nelle app aziendali gestite.|
|**Consenti videoconferenza**|Consentire l'uso di applicazioni di videoconferenza come Facetime sul dispositivo.|
|**Consenti all'utente di considerare attendibili nuovi autori di app aziendali**|Consentire all'utente di scegliere di considerare attendibili le app che non sono state scaricate dall'App Store.|


### Impostazioni dell'applicazione per i giochi
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti l'aggiunta di amici al Game Center**|Consente all'utente di aggiungere amici in Game Center.|
|**Consenti modalità di gioco multiplayer**|Consente all'utente di partecipare a giochi multiplayer sul dispositivo.|

### Impostazioni dell'applicazione per i contenuti multimediali
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Area classificazioni**|Selezionare un'area, quindi selezionare la classificazione massima che gli utenti possono scaricare per **film**, **show televisivi** e **app**.|
|**Consenti contenuti per adulti nell'archivio multimediale**|Consente al dispositivo di accedere ai contenuti dell'archivio classificati come per adulti.|
|**Consenti all'utente di scaricare contenuti da iBook Store contrassegnati come 'Erotici'**|Consentire all'utente di scaricare libri della categoria "Erotici".|


### Impostazioni delle funzionalità del dispositivo per l'hardware
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti dispositivo foto/video**|Specificare se è consentito l'uso della fotocamera del dispositivo.|
|**Forza gli Apple Watch associati a usare il rilevamento del polso**|Se abilitata, l'Apple Watch non visualizza notifiche se non è indossato.|
|**Richiedi una password di associazione per le richieste AirPlay in uscita**|Richiedere una password di associazione quando l'utente usa AirPlay per trasmettere i contenuti ad altri dispositivi di Apple.|

### Impostazioni delle funzionalità del dispositivo per il cellulare
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti roaming vocale**|Consente il roaming vocale quando il dispositivo è su una rete cellulare.|
|**Consenti dati in roaming**|Consentire il roaming dei dati quando il dispositivo si trova su una rete cellulare.|
|**Consenti recupero in background globale durante il roaming**|Consente al dispositivo di recuperare dati come la posta elettronica durante il roaming su una rete cellulare.|

### Impostazioni delle funzionalità del dispositivo per le funzionalità
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti Siri**|Consente l'uso dell'assistente vocale Siri sul dispositivo.|
|**Consenti Siri quando il dispositivo è bloccato**|Consente l'uso dell'assistente vocale Siri quando il dispositivo è bloccato.|
|**Consenti composizione vocale**|Consente l'uso della funzionalità di composizione vocale sul dispositivo.|
|**Non consentire AirDrop dalle app gestite**|Impedisce alle app gestite di inviare dati tramite AirDrop.|


### Impostazioni per le app conformi e non conformi
Nell'elenco **App conformi &amp; non conformi** specificare un elenco di app conformi o non conformi usando le informazioni seguenti.

> [!NOTE]
> Un singolo criterio può contenere solo un elenco di app conformi o non conformi. Non è possibile specificare entrambi nello stesso criterio.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Segnala la mancata conformità quando gli utenti installano le app elencate**|Elencare le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire.|
|**Segnala la mancata conformità quando gli utenti installano app non elencate**|Elencare le app che gli utenti sono autorizzati a installare. Per garantire la conformità, non installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite.|
|**Aggiunta**|Aggiungere un'app all'elenco selezionato. Specificare un nome desiderato, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store. Per altre informazioni, vedere "Come specificare gli URL negli App Store" più avanti in questo argomento.|
|**Importa app**|Importare un elenco di app specificate in un file con valori delimitati da virgole. Nel file usare il formato: nome dell'applicazione, autore, URL dell'app.|
|**Modifica**|Modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Eliminare l'app selezionata dall'elenco.|

### Impostazioni della modalità tutto schermo

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo**|Scegliere **Sfoglia**, quindi specificare l'app gestita o un'app di uno Store che potrà essere eseguita quando il dispositivo è in modalità tutto schermo. Non sarà possibile eseguire altre applicazioni nel dispositivo. Per informazioni, vedere "Come specificare gli URL negli App Store" più avanti in questo argomento.|
|**Consenti tocco**|Abilitare o disabilitare il touchscreen nel dispositivo.|
|**Consenti rotazione schermo**|Abilitare o disabilitare la modifica dell'orientamento dello schermo quando si ruota il dispositivo.|
|**Consenti pulsanti volume**|Abilitare o disabilitare l'uso dei pulsanti del volume nel dispositivo.|
|**Consenti commutatore suoneria**|Abilitare o disabilitare la suoneria nel dispositivo.|
|**Consenti pulsante riattivazione sospensione schermo**|Abilitare o disabilitare il pulsante di riattivazione sospensione dello schermo del dispositivo.|
|**Consenti blocco automatico**|Abilitare o disabilitare il blocco automatico del dispositivo.|
|**Abilita audio mono**|Abilitare o disabilitare l'impostazione di accessibilità **Audio mono**.|
|**Abilita voice over**|Abilitare o disabilitare l'impostazione di **Voice over** per la lettura a voce alta del testo sullo schermo del dispositivo.|
|**Abilita regolazioni voice over**|Abilitare o disabilitare le regolazioni di voice over che consentono di modificare la funzione Voice over, ad esempio la velocità con cui viene letto il testo visualizzato sullo schermo.|
|**Abilita zoom**|Abilitare o disabilitare l'impostazione di accessibilità **Zoom** che consente di usare le funzionalità di tocco per ingrandire la visualizzazione del dispositivo.|
|**Abilita regolazioni zoom**|Abilitare o disabilitare le regolazioni dello zoom che consentono di modificare la funzione di zoom.|
|**Abilita inversione colori**|Abilitare o disabilitare l'impostazione di accessibilità **Inverti colori** che consente di regolare la visualizzazione per gli utenti con problemi visivi.|
|**Abilita regolazioni inversione colori**|Abilitare o disabilitare le regolazioni dell'inversione colori che consentono di modificare la funzione Inverti colori.|
|**Abilita tocco per l'accesso facilitato**|Abilitare o disabilitare l'impostazione di accessibilità **Tocco per l'accesso facilitato** che aiuta l'utente a eseguire sullo schermo movimenti che altrimenti risulterebbero difficili da eseguire.|
|**Abilita regolazioni del tocco per l'accesso facilitato**|Abilitare o disabilitare le regolazioni del tocco per l'accesso facilitato che consentono all'utente di modificare la funzione Tocco per l'accesso facilitato.|
|**Abilita selezione comandi vocali**|Abilitare o disabilitare l'impostazione di accessibilità **Abilita selezione comandi vocali** che consente di leggere a voce alta il testo selezionato.|
> [!NOTE]
> Le note seguenti sono valide per le impostazioni della modalità tutto schermo per i dispositivi iOS:
>
> -   Prima di poter configurare un dispositivo iOS per la modalità tutto schermo, è necessario usare lo [strumento Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) o il manager di registrazione dispositivi per inserire il dispositivo in modalità di supervisione. Per altre informazioni sullo strumento Apple Configurator, vedere la documentazione di Apple.
> -   Se l'app per iOS specificata viene installata dopo aver distribuito i criteri di configurazione, il dispositivo non passerà alla modalità tutto schermo finché non viene riavviato.

### Informazioni di riferimento per le app conformi e non conformi

Usare **Report app non conformi** per visualizzare la conformità delle app consentite e bloccate.

##### Per eseguire il report app non conformi

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Report** &gt; **Report app non conformi**.

2.  Selezionare i gruppi di dispositivi da controllare, scegliere se verificare la presenza di app conformi, di app non conformi o di entrambi i tipi di app, quindi scegliere **Visualizza report**.

#### Come specificare gli URL negli App Store
Per specificare un URL dell'app nell'elenco delle app conformi e non conformi o nell'opzione **Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo** (solo iOS), usare uno dei formati seguenti:

1. Usando un motore di ricerca, trovare l'app da usare nell'App Store iTunes e aprire la pagina per l'app.

2. Copiare l'URL della pagina e usarlo per la configurazione dell'elenco delle app conformi o non conformi o dell'app da eseguire in modalità tutto schermo.

**Esempio:** cercare **Microsoft Word per iPad**. L'URL usato sarà **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> È possibile usare anche il software iTunes per trovare l'app e il comando **Copia collegamento** per ottenere l'URL dell'app.

### Impostazioni di registrazione
Tutte le impostazioni si applicano a iOS 7.1 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti blocco attivazione quando il dispositivo è in modalità di supervisione**|Abilitare il blocco attivazione su dispositivi iOS con supervisione.|

### Impostazioni della modalità di supervisione
Nei dispositivi che eseguono iOS 7.1 e versioni successive in modalità di supervisione possono essere configurate le impostazioni seguenti.

### Impostazioni della modalità di supervisione per restrizioni del dispositivo

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti la modifica dell'account**|Consente all'utente di modificare le impostazioni dell'account, ad esempio le configurazioni di posta elettronica.|
|**Consenti le modifiche alle impostazioni dell'utilizzo della rete dati dell'app**|Consente all'utente di controllare le app che possono usare la rete dati.|
|**Consenti l'uso dell'opzione di cancellazione di tutti i contenuti e tutte le impostazioni sul dispositivo**|Consentire all'utente di usare l'opzione per cancellare tutti i contenuti e tutte le impostazioni sul dispositivo.|
|**Consenti all'utente di abilitare restrizioni nelle impostazioni del dispositivo**|Consentire all'utente di configurare restrizioni, come il controllo genitori, sul dispositivo.|
|**Consenti l'associazione di host per controllare i dispositivi a cui può essere associato un dispositivo iOS**|Consentire l'associazione di host in modo che l'amministratore possa controllare a quali dispositivi può essere associato un dispositivo iOS.|
|**Consenti all'utente di installare profili di configurazione e certificati**|Consente all'utente di installare profili di configurazione e certificati.|
|**Consenti la modifica del nome dispositivo**|Consentire all'utente di modificare il nome del dispositivo.|
|**Consenti la modifica del passcode**|Consentire l'aggiunta, la modifica o la rimozione della password del dispositivo.|
|**Consenti l'associazione di Apple Watch**|Consentire al dispositivo di associare un Apple Watch.|
|**Consenti la modifica delle impostazioni di notifica**|Consentire all'utente di modificare le impostazioni di notifica del dispositivo.|
|**Consenti la modifica dello sfondo**|Consentire all'utente di modificare lo sfondo del dispositivo.|

### Impostazioni della modalità supervisione per restrizioni delle funzionalità

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti AirDrop**|Consentire l'uso della funzionalità AirDrop per scambiare contenuti con i dispositivi presenti nelle vicinanze.|
|**Consenti a Siri di eseguire query sul contenuto generato dall'utente da Internet**|Consentire a Siri di accedere ai siti Web per rispondere alle domande.|
|**Usa il filtro di Siri per le espressioni volgari**|Impedire a Siri di usare espressioni volgari.|
|**Consenti alla ricerca Spotlight di restituire risultati da Internet**|Consentire alla ricerca Spotlight di connettersi a Internet per visualizzare altri risultati.|
|**Consenti la ricerca della definizione delle parole**|Consentire la funzionalità di iOS che permette di evidenziare una parola e cercarne la definizione.|
|**Consenti le tastiere predittive**|Consentire l'uso di tastiere predittive che suggeriscono all'utente i termini desiderati.|
|**Consenti la correzione automatica**|Consentire al dispositivo di correggere automaticamente le parole errate.|
|**Consenti il controllo ortografico tastiera**|Consentire al dispositivo di eseguire il controllo ortografico.|
|**Consenti tasti di scelta rapida**|Consentire l'uso dei tasti di scelta rapida.|

### Impostazioni della modalità supervisione per restrizioni dell'app

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti la modifica delle impostazioni di attendibilità delle app aziendali**||
|**Consentire l'installazione di app esclusivamente tramite la configurazione di Apple e iTunes**||
|**Consenti i download automatici delle app**||
|**Consenti modifiche alle impostazioni dell'app Find My Friends**|Consente all'utente di modificare le impostazioni dell'app Find My Friend.|
|**Consenti l'accesso all'iBooks Store**|Consente all'utente di selezionare e acquistare libri all'iBooks Store.|
|**Consenti l'uso dell'app Messages sul dispositivo**|Consenti l'uso dell'app Messages per inviare messaggi di testo.|
|**Consenti l'uso di podcast**|Consentire l'uso delle app di podcast.|
|**Consenti l'uso del servizio Music**|Consentire l'uso dell'app Music di Apple.|
|**Consenti il servizio iTunes Radio**|Consentire l'uso dell'app iTunes Radio.|
|**Consenti Apple News**|Consentire l'uso dell'app Apple News.|
|**Consenti Game Center**|Consente l'uso dell'app Game Center.|


### Mostrare o nascondere app

Usare **Elenco di app nascoste e mostrate** per controllare quanto riportato di seguito su dispositivi supervisionati che eseguono iOS 9.3 o versione successiva:

- Specificare un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
- Specificare un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.


#### Come creare un elenco di app nascoste o mostrate

Specificare le impostazioni seguenti:

|Nome impostazione|Dettagli|
|-|-|
|**Elenco di app nascoste e mostrate**|Abilitare questa impostazione se si vuole creare un elenco di app nascoste o mostrate.|
|**Nascondi le app elencate dagli utenti**|Selezionare questa opzione se si vuole creare un elenco di app che verranno nascoste agli utenti.|
|**Mostra solo le app elencate agli utenti**|Selezionare questa opzione se si vuole creare un elenco di app visualizzate agli utenti.<br>Quando si crea questo tipo di elenco, tutte le altre app, ad eccezione di **Impostazioni** e **Telefono** (per iPhone), vengono nascoste.<br>È inoltre necessario aggiungere all'elenco il portale aziendale e qualsiasi app distribuita e gestita con Intune.|
|**Aggiunta**|Aggiunge un'app all'elenco selezionato.<br>Per quanto riguarda l'elenco delle app nascoste, è necessario specificare **Nome**, **Autore** e **URL app o ID bundle** di ciascuna app che si vuole nascondere.<br>Per quanto riguarda l'elenco delle app mostrate, è possibile scegliere l'opzione **Selezionare un'app gestita**, che fornisce un elenco delle app gestite con Intune, oppure scegliere l'opzione Selezionare un'app dello Store. È quindi necessario specificare **Nome**, **Autore** e **URL app o ID bundle** di ciascuna app che si vuole visualizzare.|
|**Importa app**|Importa un elenco di app specificate in un file con valori delimitati da virgole. Per il file usare il formato nome applicazione, autore, URL.|
|**Modifica**|Consente di modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Elimina l'app selezionata dall'elenco.|

#### Informazioni per app iOS incorporate

Usare le informazioni riportate in questo elenco per identificare il nome, l'autore e l'ID bundle delle app iOS incorporate che si vogliono mostrare o nascondere. Se si vogliono mostrare o nascondere tutte le app dell'elenco, è possibile copiare i dati riportati di seguito in un file di testo con estensione **csv** e quindi usare l'opzione **Importa app** per importare tutte le app contemporaneamente.

```
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


```




## Impostazioni di criteri personalizzati

Usare i **criteri di configurazione personalizzati iOS** di Microsoft Intune per distribuire le impostazioni create con lo strumento [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) nei dispositivi iOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione in un criterio personalizzato iOS di Intune e distribuire le impostazioni a utenti e dispositivi nella propria organizzazione.

Questa funzionalità consente di distribuire le impostazioni di iOS che non possono essere configurate con i criteri di configurazione generali di Intune.

### Prerequisiti
Prima di iniziare, è necessario aver installato lo strumento Apple Configurator e creato un file di configurazione contenente le impostazioni da distribuire a utenti o dispositivi. È possibile scaricare e acquisire informazioni su Apple Configurator da [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> Intune non segnala la conformità delle singole impostazioni in un criterio personalizzato iOS. Tuttavia, viene segnalata la conformità generale del criterio.

### Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio personalizzato iOS, che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio personalizzato iOS e altre informazioni rilevanti per consentirne l'individuazione.|

### Impostazioni personalizzate

|Nome impostazione|Dettagli|
    |----------------|--------------------|
|**Nome del profilo di configurazione personalizzato (visualizzato agli utenti)**|Specificare il nome con cui il criterio verrà visualizzato nel dispositivo e nei report dei criteri di Intune.|
|**File del profilo di configurazione**|Scegliere **Importa**, quindi selezionare il profilo di configurazione creato usando lo strumento Apple Configurator. **Nota:** Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di iOS sui dispositivi su cui vengono distribuiti i criteri personalizzati iOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).|
    |**Dettagli del profilo di configurazione**|Visualizzare il codice XML per il profilo di configurazione importato.|

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO5-->


