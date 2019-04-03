---
title: Impostazioni dei dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere, configurare o creare le impostazioni nei dispositivi iOS per limitare l'uso delle funzionalità, tra cui impostare i requisiti per le password, controllare la schermata di blocco, usare le app predefinite, aggiungere app con restrizioni o approvate, gestire i dispositivi Bluetooth, connettersi al cloud per backup e archiviazione, abilitare la modalità a schermo intero, aggiungere domini e controllare il modo in cui gli utenti interagiscono con il Web browser Safari in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5106a4f147828310fc1b4a41ef4065d10bdaeecf
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490727"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi iOS. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, impostare regole per le password, consentire o limitare l'uso di app specifiche e altro ancora.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi iOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione dispositivo restrizioni](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Generale

- **Condividi i dati di utilizzo**: scegliere **Blocca** per impedire al dispositivo di inviare dati di diagnostica e di utilizzo ad Apple. **Non configurato** (impostazione predefinita) consente l'invio di questi dati.
  - **Modifica impostazioni di invio dei dati di diagnostica (solo con supervisionata)**: **Block** impedisce all'utente di modificare la presentazione e app analitica le impostazioni di diagnostica in **diagnostica e utilizzo**(impostazioni del dispositivo). **Non configurato** (impostazione predefinita) consente all'utente di modificare queste impostazioni del dispositivo.

    Questa funzionalità si applica a:  
    - iOS 9.3.2 e versioni successive

- **Acquisizione schermo**: scegliere **Blocca** per impedire screenshot o acquisizioni di schermate nel dispositivo. In iOS 9.0 e versioni successive, include anche le registrazioni dello schermo di blocco. **Non configurato** (impostazione predefinita) consente all'utente di acquisire il contenuto dello schermo come immagine o come video.
  - **Osservazione dello schermo remoto da parte dell'app Classroom (solo con supervisione)**: scegliere **Blocca** per impedire all'app Classroom di visualizzare lo schermo del dispositivo da remoto. **Non configurato** (impostazione predefinita) consente all'app Classroom di Apple di visualizzare lo schermo.

    Questa funzionalità si applica a:  
    - iOS 9.3 e versioni successive

  - **Osservazione dello schermo non richiesta da parte dell'app Classroom (solo con supervisione)**: se impostata su **Consenti**, gli insegnanti possono osservare lo schermo dei dispositivi iOS degli studenti con l'app Classroom senza che questi ne siano a conoscenza. I dispositivi degli studenti registrati in una classe con l'app Classroom concedono automaticamente l'autorizzazione al docente del corso. **Non configurato** (impostazione predefinita) impedisce questa funzionalità.
- **Certificati TLS non attendibili**: scegliere **Blocca** per non consentire certificati TLS (Transport Layer Security) non attendibili nel dispositivo. **Non configurato** (impostazione predefinita) consente i certificati TLS.
- **Attendibilità dell'app aziendale**: scegliere **Blocca** per rimuovere il pulsante **Attendibilità di Enterprise Developer** in Impostazioni > Generale > Gestione di profili e dispositivi nel dispositivo. **Non configurato** (impostazione predefinita) consente all'utente di scegliere di considerare attendibili le app che non vengono scaricate da App Store.
- **Modifica dell'account (solo con supervisione)**: se impostata su **Blocca**, l'utente non può aggiornare le impostazioni specifiche del dispositivo dall'app delle impostazioni iOS. Ad esempio, l'utente non può creare nuovi account di dispositivo o modificare il nome utente o la password. **Non configurato** (impostazione predefinita) consente agli utenti di modificare queste impostazioni.

  Questa funzionalità si applica anche alle impostazioni accessibili dall'app delle impostazioni iOS, ad esempio Posta elettronica, Contatti, Calendario, Twitter e altro ancora. Non si applica alle app con impostazioni dell'account non configurabili dall'app delle impostazioni iOS, ad esempio Microsoft Outlook.
- **Schermata di tempo (solo con supervisionato)**: scegliere **blocco** impedire agli utenti di impostare le proprie restrizioni nel tempo dello schermo (impostazioni di dispositivo). **Non configurato** consente all'utente di configurare restrizioni (ad esempio controllo genitori o contenuto e le restrizioni sulla privacy) nel dispositivo.

  Questa impostazione, è stata rinominata **abilitazione delle restrizioni nelle impostazioni del dispositivo**. Impatto della modifica:  
  
  - iOS 11.4.1 e versioni precedenti: **Blocca** impedisce agli utenti finali di impostare le proprie restrizioni nelle impostazioni del dispositivo. Questa è la stessa. e non sono presenti modifiche per gli utenti finali.
  - iOS 12.0 e versioni successive: **blocco** impedisce agli utenti finali di impostano le loro **schermata ora** nelle impostazioni del dispositivo (Impostazioni > generali > dello schermo ora), incluse le restrizioni di contenuto e la privacy. Dispositivi aggiornati a iOS 12.0 non verranno visualizzata la scheda restrizioni nelle impostazioni del dispositivo più (Impostazioni > generali > Gestione dispositivo > profilo di gestione > restrizioni). Queste impostazioni sono in **Orario schermo**.
  
- **Uso dell'opzione di cancellazione di tutti i contenuti e tutte le impostazioni sul dispositivo (solo con supervisione)**: scegliere **Blocca** in modo che gli utenti non possano usare l'opzione per cancellare tutto il contenuto e tutte le impostazioni nel dispositivo (solo con supervisione). **Non configurato** (impostazione predefinita) consente agli utenti di accedere a queste impostazioni.
- **Modifica del nome dispositivo (solo con supervisione)**: scegliere **Blocca** in modo che il nome del dispositivo non possa essere modificato. **Non configurato** (impostazione predefinita) consente all'utente di modificare il nome del dispositivo.
- **Modifica delle impostazioni di notifica (solo con supervisione)**: scegliere **Blocca** in modo che le impostazioni di notifica non possano essere modificate. **Non configurato** (impostazione predefinita) consente all'utente di modificare le impostazioni di notifica del dispositivo.
- **Modifica dello sfondo (solo con supervisione)**: **Blocca** impedisce la modifica dello sfondo. **Non configurato** (impostazione predefinita) consente all'utente di modificare lo sfondo del dispositivo.
- **Modifica delle impostazioni di attendibilità delle app aziendali (solo con supervisione)**: **Blocca** impedisce all'utente di modificare le impostazioni di attendibilità delle app aziendali nei dispositivi con supervisione. **Non configurato** (impostazione predefinita) consente all'utente di considerare attendibili le app che non vengono scaricate da App Store.
- **Modifiche al profilo di configurazione (solo con supervisione)**: **Blocca** impedisce modifiche al profilo di configurazione nel dispositivo. **Non configurato** (impostazione predefinita) consente all'utente di installare profili di configurazione.
- **Blocco attivazione (solo con supervisione)**: scegliere **Consenti** per abilitare il blocco attivazione nei dispositivi iOS con supervisione. Blocco attivazione rende più difficile la riattivazione di un dispositivo perso o rubato.
- **Blocca la rimozione di app (solo con supervisione)**: scegliere **Blocca** per impedire agli utenti di rimuovere le app. **Non configurato** (impostazione predefinita) consente agli utenti di rimuovere le app dal dispositivo.
- **Blocca la modalità USB con restrizioni (solo con supervisione)**: scegliere **Blocca** per disabilitare la modalità USB con restrizioni nei dispositivi con supervisione. La modalità USB con restrizioni impedisce agli accessori USB di scambiare dati con un dispositivo bloccato per più di un'ora. **Non configurato** (impostazione predefinita) consente la modalità USB con restrizioni.
- **Imponi data e ora automatiche (solo con supervisione)**: **Rendi obbligatorio** forza l'impostazione automatica di data e ora nei dispositivi con supervisione. Il fuso orario del dispositivo viene aggiornato quando il dispositivo dispone di connessioni alla rete cellulare o Wi-Fi con i servizi di posizione abilitati.
- **Richiedi agli studenti di chiedere l'autorizzazione per lasciare un corso Classroom (solo con supervisione)**: **Rendi obbligatorio** impone agli studenti registrati in un nuovo corso non gestito con l'app Classroom di richiedere l'autorizzazione al docente per lasciare il corso. **Non configurato** (impostazione predefinita) non impone agli studenti di richiedere l'autorizzazione.

  Questa funzionalità si applica a:  
  - iOS 11.3 e versioni successive

- **Consenti Classroom bloccare a un'app e bloccare il dispositivo senza chiedere conferma (solo con supervisione)**: **abilitare** consente a docenti bloccare le app o bloccare il dispositivo con l'app Classroom senza chiedere conferma dello studente. Blocco significa che le app di dispositivo può solo le app specificate per docenti l'accesso. **Non configurato** (impostazione predefinita) impedisce ai docenti di blocco app o dispositivo con l'app Classroom senza chiedere conferma dello studente. 

  Questa funzionalità si applica a:  
  - iOS 11.0 e versioni successive

- **Creare un join automatico Classroom dell'utente senza chiedere conferma (solo con supervisione)**: **abilitare** automaticamente consente agli studenti di partecipare a una classe che si trova nell'app Classroom senza chiedere conferma docente. **Non configurato** (impostazione predefinita) richiede l'insegnante che gli studenti da unire in join di una classe che è l'app Classroom.

  Questa funzionalità si applica a:  
  - iOS 11.0 e versioni successive

- **Consenti gli aggiornamenti PKI in modalità wireless**: **Consenti** consente agli utenti di ricevere gli aggiornamenti software senza dover connettere i propri dispositivi a un computer.
- **Limita il rilevamento annunci**: scegliere **Limita** per disabilitare l'identificatore di annunci pubblicitari del dispositivo. **Non configurato** (impostazione predefinita) mantiene sia abilitato.
- **Blocca la creazione di VPN (solo con supervisione)**: **Blocca** impedisce agli utenti di creare le impostazioni di configurazione VPN. **Non configurato** (impostazione predefinita) consente agli utenti di creare VPN nel dispositivo.
- **Modifica delle impostazioni di eSIM (solo con supervisionate)**: **blocco** impedisce agli utenti di rimozione o aggiunta di un piano cellulare di eSIM nel dispositivo. **Non configurato** (impostazione predefinita) consente agli utenti di modificare queste impostazioni.

  Questa funzionalità si applica a:  
  - iOS 12.1 e versioni successive

- **Rinvia gli aggiornamenti software (solo con supervisionati)**: se impostata su **non configurata** (impostazione predefinita), gli aggiornamenti software vengono visualizzati nel dispositivo non appena vengono rilasciati da Apple. Ad esempio, se ottiene rilasciato un aggiornamento di iOS di Apple in una data specifica, quindi tale aggiornamento naturalmente viene visualizzato nel dispositivo attorno alla data di rilascio.

  **Abilitare** consente all'utente per il ritardo quando vengono visualizzati gli aggiornamenti software nei dispositivi, da 0 a 90 giorni. Questa impostazione non controlla gli aggiornamenti o quando non sono installati. 

  - **Ritardare la visibilità degli aggiornamenti software**: immettere un valore da 0 a 90 giorni. Quando l'intervallo di ritardo scade, gli utenti ricevono una notifica per l'aggiornamento alla versione del sistema operativo meno recente disponibile quando è stato attivato il ritardo.

    Ad esempio, se iOS 12.a è disponibile nel **il 1 ° gennaio**, e **ritardare la visibilità** è impostata su **5 giorni**, quindi iOS 12.a non viene visualizzata come un aggiornamento disponibile nei dispositivi degli utenti finali. Nel **sesto giorno** successivi al rilascio, che è disponibile un aggiornamento e gli utenti finali possono eseguirne l'installazione.

    Questa impostazione si applica a:  
    - iOS 11.3 e versioni successive

## <a name="password"></a>Password

- **Password**: impostare **Rendi obbligatorio** per richiedere all'utente finale di immettere una password per accedere al dispositivo. **Non configurata** consente agli utenti di accedere al dispositivo senza immettere una password.
  - **Password semplici**: scegliere **Blocca** per richiedere password più complesse. **Non configurata** consente password semplici, ad esempio `0000` e `1234`.
  - **Tipo di password richiesto**: scegliere il tipo di password richiesto dall'organizzazione. Le opzioni disponibili sono:
    - **Impostazione predefinita dispositivo**
    - **Numerica**
    - **Alfanumerica**
  - **Numero di caratteri non alfanumerici nella password**: immettere il numero di simboli, ad esempio `#` o `@`, che è necessario includere nella password.
  - **Lunghezza minima password**: immettere la lunghezza minima che l'utente deve immettere (da 4 a 14 caratteri).
  - **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: immettere il numero di errori di accesso consentiti prima della cancellazione del dispositivo (da 1 a 11).
  - **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta la password**<sup>1</sup>: immettere il tempo per il quale il dispositivo rimane inattivo prima che l'utente debba immettere nuovamente la password. Se il tempo immesso è più lungo dell'impostazione corrente nel dispositivo, il dispositivo ignora il tempo immesso. Supportata in iOS 8.0 e nei dispositivi più recenti.
  - **Numero massimo di minuti di inattività fino al blocco dello schermo**<sup>1</sup>: immettere il numero massimo di minuti di inattività consentiti nel dispositivo prima del blocco dello schermo. Se il tempo immesso è più lungo dell'impostazione corrente nel dispositivo, il dispositivo ignora il tempo immesso.
  - **Scadenza password (giorni)**: immettere il numero di giorni prima che sia necessario modificare la password del dispositivo.
  - **Impedisci il riutilizzo delle password precedenti**: immettere il numero di nuove password da usare prima che una password precedente possa essere usata di nuovo.
  - **Sblocco dell'impronta digitale**: scegliere **Blocca** per impedire l'uso di un'impronta digitale per sbloccare il dispositivo. **Non configurata** consente all'utente di sbloccare il dispositivo tramite impronta digitale.
- **Modifica del passcode (solo con supervisione)**: scegliere **Blocca** per impedire la modifica, l'aggiunta o la rimozione del passcode. Le modifiche alle restrizioni del passcode vengono ignorate nei dispositivi con supervisione dopo il blocco di questa funzionalità. **Non configurato** (impostazione predefinita) consente l'aggiunta, la modifica o la rimozione dei passcode.

  - **Modifica dell'impronta digitale (solo con supervisione)**: **Blocca** impedisce all'utente di modificare, aggiungere o rimuovere le impronte digitali TouchID. **Non configurato** (impostazione predefinita) consente all'utente di aggiornare le impronte digitali TouchID nel dispositivo.

- **Blocca il riempimento automatico delle password (solo con supervisione)**: scegliere **Blocca** per impedire l'uso della funzionalità di riempimento automatico delle password in iOS. La scelta di **Blocca** ha anche le conseguenze seguenti:

  - Agli utenti non viene richiesto di usare una password salvata in Safari o in qualsiasi app.
  - Le password complesse automatiche sono disabilitate e non vengono consigliate password complesse agli utenti.

  **Non configurato** (impostazione predefinita) consente queste funzionalità.

- **Blocca le richieste di prossimità password (solo con supervisione)**: scegliere **Blocca** in modo che il dispositivo di un utente non richieda password dai dispositivi nelle vicinanze. **Non configurato** (impostazione predefinita) consente queste richieste di password.
- **Blocca la condivisione delle password (solo con supervisione)**: **Blocca** impedisce la condivisione delle password tra i dispositivi tramite AirDrop. **Non configurato** (impostazione predefinita) consente di condividere le password.
- **Richiedere l'autenticazione di Touch ID oppure Face ID per le informazioni di carta di credito o password riempimento automatico (solo con supervisionato)**: se impostata su **richiedono**, gli utenti devono autenticarsi usando touch ID oppure FaceID prima le password o carta di credito le informazioni possono essere compilato in Safari e altre App automaticamente. **Non configurato** (impostazione predefinita) consente agli utenti di controllare questa funzionalità nelle impostazioni del dispositivo.

  Questa funzionalità si applica a:  
  - iOS 11.0 e versioni successive

<sup>1</sup>Quando si configurano le impostazioni **Numero massimo di minuti di inattività fino al blocco dello schermo** e **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**, queste vengono applicate in sequenza. Ad esempio, se si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo cinque minuti e il dispositivo viene bloccato dopo altri cinque minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio il dispositivo viene bloccato cinque minuti dopo che l'utente spegne lo schermo.

## <a name="locked-screen-experience"></a>Esperienza della schermata di blocco

- **Accesso al centro di controllo durante il blocco del dispositivo**: scegliere **Blocca** per impedire l'accesso all'app Centro di controllo quando il dispositivo è bloccato. **Non configurata** consente agli utenti di accedere all'app Centro di controllo quando il dispositivo è bloccato.
- **Notifiche durante il blocco del dispositivo**: **Blocca** impedisce l'accesso alle notifiche quando il dispositivo è bloccato. **Non configurata** consente all'utente di accedere alle notifiche senza sbloccare il dispositivo.
- **Notifiche di Portafoglio durante il blocco del dispositivo**: **Blocca** impedisce l'accesso all'app Portafoglio quando il dispositivo è bloccato. **Non configurata** consente all'utente di accedere all'app Portafoglio mentre il dispositivo è bloccato.
- **Visualizzazione Oggi durante il blocco del dispositivo**: **Blocca** impedisce l'accesso alla visualizzazione Oggi quando il dispositivo è bloccato. **Non configurata** consente all'utente di accedere alla visualizzazione Oggi quando il dispositivo è bloccato.

## <a name="app-store-doc-viewing-gaming"></a>App Store, visualizzazione documenti, giochi

- **App Store**: **Blocca** impedisce l'accesso all'App Store nei dispositivi con supervisione. **Non configurata** consente l'accesso.
  - **Installazione di app dall'App Store (solo con supervisione)**: scegliere **Blocca** per bloccare l'App Store dalla schermata iniziale dei dispositivi. Gli utenti finali possono continuare a usare iTunes o Apple Configurator per installare le app. **Non configurata** consente App Store nella schermata iniziale.
  - **Download automatici delle app (solo con supervisione)**: scegliere **Blocca** per impedire il download automatico delle app acquistate in altri dispositivi. Non influisce sugli aggiornamenti delle app esistenti. **Non configurata** consente di scaricare nel dispositivo app acquistate in altri dispositivi iOS.
- **Password per l'accesso all'App Store**: **Rendi obbligatorio** per richiedere all'utente di immettere la password prima di visitare l'App Store. **Non configurata** consente l'accesso all'App Store senza dover immettere una password.
- **Acquisti in-app**: scegliere **Blocca** per impedire gli acquisti in-app dallo Store. **Non configurata** consente gli acquisti dallo Store dall'interno di un'app in esecuzione.
- **Musica di iTunes, podcast o notizie con contenuti espliciti (solo con supervisione)**: scegliere **Blocca** per impedire musica di iTunes, podcast o notizie con contenuti espliciti. **Non configurata** consente al dispositivo di accedere ai contenuti classificati come per adulti dallo Store.
- **Scarica da iBook Store i contenuti contrassegnati come 'Erotici'**: scegliere **Blocca** per impedire agli utenti di scaricare contenuti multimediali da iBook Store contrassegnati come erotici. **Non configurata** consente all'utente di scaricare libri della categoria "Erotici".
- **Visualizzazione dei documenti aziendali nelle app non gestite**: **Blocca** impedisce la visualizzazione di documenti aziendali nelle app non gestite. **Non configurata** consente di visualizzare documenti aziendali in qualsiasi app. Ad esempio, può essere necessario impedire agli utenti il salvataggio di file dall'app OneDrive a Dropbox. Configurare questa impostazione come **Blocca**. Dopo aver ricevuto i criteri, ad esempio dopo un riavvio, il dispositivo non consente più il salvataggio.
  - **Consentire alle App gestite di scrivere contatti contatti non gestito e account**: se impostata su **Consenti**, gli utenti possono aggiungere o sincronizzare informazioni di contatto Outlook qualsiasi persona, inclusi a business e i contatti aziendali, il app dei contatti predefinite nel dispositivo. Quando è impostata su **Non configurata**, gli utenti non possono aggiungere contatti di Outlook all'app Contatti incorporata nel dispositivo.
  
    Per usare questa impostazione, impostare **Visualizzazione dei documenti aziendali nelle app non gestite** su **Blocca**.
  
- **Visualizzazione di documenti non aziendali nelle app aziendali**: **Blocca** impedisce la visualizzazione di documenti non aziendali nelle app aziendali. **Non configurata** consente di visualizzare qualsiasi documento nelle app aziendali gestite.
  - **Consentire alle App non gestite per la lettura dagli account gestito contatti**: se impostata su **Consenti**, gli utenti possono aggiungere iContacts app le informazioni di contatto qualsiasi persona in Outlook. **Non configurata** impedisce la lettura, inclusa la rimozione di duplicati, dall'app Contatti incorporata nel dispositivo.
  
    Per usare questa impostazione, impostare **Visualizzazione di documenti non aziendali nelle app aziendali** su **Blocca**.
  
- **Considera AirDrop come destinazione non gestita**: **Rendi obbligatorio** consente di considerare AirDrop come obiettivo di rilascio non gestito. Impedisce alle app gestite di inviare dati tramite Airdrop. 
- **Aggiunta di amici al Game Center (solo con supervisione)**: **Blocca** impedisce agli utenti di aggiungere amici al Game Center. **Non configurata** consente all'utente di aggiungere amici in Game Center.
- **Game Center (solo con supervisione)**: **Blocca** impedisce o consente l'uso dell'app Game Center. **Non configurata** consente l'uso dell'app Game Center nel dispositivo.
- **Gioco multiplayer (solo con supervisione)**: scegliere **Blocca** per impedire il gioco multiplayer. **Non configurata** consente all'utente di partecipare a giochi multiplayer nel dispositivo.
- **Area classificazioni**: scegliere l'area di classificazioni da usare per i download consentiti. Scegliere quindi le classificazioni consentite per **Film** e **Programmi TV**.
- **App**: scegliere la fascia d'età consentita per le app che gli utenti possono scaricare. In alternativa è possibile scegliere **Consenti tutte le app**.

## <a name="built-in-apps"></a>App predefinite

- **Fotocamera**: scegliere **Blocca** per impedire l'accesso alla fotocamera nel dispositivo. **Non configurata** consente l'accesso alla fotocamera del dispositivo.
  - **FaceTime**: **Blocca** per impedire l'accesso all'app FaceTime. **Non configurata** consente l'accesso all'app FaceTime nel dispositivo.
- **Siri**: **Blocca** impedisce l'accesso a Siri. **Non configurata** consente l'uso dell'assistente vocale Siri nel dispositivo.
  - **Siri durante il blocco del dispositivo**: scegliere **Blocca** per impedire l'accesso a Siri quando il dispositivo è bloccato. **Non configurata** consente l'uso dell'assistente vocale Siri nel dispositivo quando è bloccato.
  - **Filtro di Siri per le espressioni volgari (solo con supervisione)**: **Rendi obbligatorio** impedisce a Siri di usare espressioni volgari.
  - **Consenti a Siri di eseguire query sul contenuto generato dall'utente da Internet (solo con supervisione)**: **Blocca** impedisce a Siri di accedere a siti Web per rispondere a domande. **Non configurata** consente a Siri di accedere al contenuto generato dall'utente da Internet.
- **Apple News (solo con supervisione)**: scegliere **Blocca** per impedire l'accesso all'app Apple News nel dispositivo. **Non configurata** consente l'uso dell'app Apple News.
- **iBooks Store (solo con supervisione)**: **Blocca** impedisce l'accesso all'iBooks Store. **Non configurata** consente agli utenti di individuare e acquistare libri da iBooks Store.
- **App Messages sul dispositivo (solo con supervisione)**: scegliere **Blocca** in modo che gli utenti non possano usare l'app Messages nel dispositivo. **Non configurata** consente l'uso delle app Messages per inviare e leggere SMS.
- **Podcasts (solo con supervisione)**: **Blocca** impedisce agli utenti di usare l'app Podcasts. **Non configurata** consente l'uso dell'app Podcasts.
- **Servizio Music (solo con supervisione)**: **Blocca** ripristina la modalità classica per l'app Music e disabilita il servizio Music. **Non configurata** consente l'uso dell'app Apple Music.
- **Servizio iTunes Radio (solo con supervisione)**: **Blocca** impedisce agli utenti di usare l'app iTunes Radio. **Non configurata** consente l'uso dell'app iTunes Radio.
- **Modifiche alle impostazioni dell'app Find My Friends (solo con supervisione)**: **Blocca** impedisce modifiche alle impostazioni per l'app Find My Friends. **Non configurata** consente all'utente di modificare le impostazioni per l'app Find My Friends.
- **Ricerca Spotlight per la restituzione di risultati da Internet (solo con supervisione)**: **Blocca** impedisce a Spotlight di restituire risultati da una ricerca in Internet. **Non configurata** consente alla ricerca Spotlight di connettersi a Internet per fornire i risultati della ricerca.
- **Impedisci la rimozione di app di sistema dal dispositivo (solo con supervisione)**: scegliere **Blocca** per disabilitare la possibilità di rimuovere le app di sistema dal dispositivo. **Non configurata** consente agli utenti di rimuovere le app di sistema.

#### <a name="safari"></a>Safari

- **Safari**: **Blocca** impedisce l'uso del browser Safari nel dispositivo. **Non configurata** consente agli utenti di usare il browser Safari.
- **Riempimento automatico**: **Blocca** disabilita la funzionalità di riempimento automatico in Safari nel dispositivo. **Non configurata** consente agli utenti di modificare le impostazioni di completamento automatico nel browser.
- **Cookie**: scegliere come vengono gestiti i cookie nel dispositivo. Le opzioni disponibili sono:
  - Consenti
  - Blocca tutti i cookie
  - Consenti i cookie dai siti Web visitati
  - Consenti i cookie dal sito Web corrente
- **JavaScript**: **Blocca** impedisce l'esecuzione nel dispositivo degli script Java nel browser. **Non configurata** consente gli script Java.
- **Avvisi illeciti**: **Rendi obbligatorio** per abilitare la visualizzazione degli avvisi di illeciti nel Web browser nel dispositivo. **Non configurata** disabilita questa funzionalità.
- **Popup**: **Blocca** per disabilitare il blocco popup nel Web browser. **Non configurata** consente il blocco popup.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

- **App non consentite**: un elenco di app non gestite da Intune di cui si vuole evitare l'installazione nel dispositivo. Se un utente installa un'app da questo elenco, si riceverà una notifica da Intune.
- **App approvate**: un elenco di app che gli utenti sono autorizzati a installare. Per mantenere la conformità, gli utenti non devono installare altre app. Le app gestite da Intune sono automaticamente consentite. Se un utente installa un'app da questo elenco, si riceverà una notifica da Intune.

Per aggiungere app a questi elenchi, è possibile:

- Scegliere **Aggiungi** per aggiungere l'URL dell'App Store iTunes dell'app desiderata. Ad esempio, per aggiungere l'app Cartelle di lavoro Microsoft, immettere `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Per trovare l'URL di un'app, aprire iTunes App Store e cercare l'app. Ad esempio, cercare `Microsoft Remote Desktop` o `Microsoft Word`. Selezionare l'app e copiare l'URL.

  È anche possibile usare iTunes per trovare l'app e quindi usare l'attività **Copia collegamento** per ottenere l'URL dell'app.

- Importare un file CSV con i dettagli sull'app, incluso l'URL. Usare il formato `<app url>, <app name>, <app publisher>`. In alternativa, esportare un elenco esistente che include l'elenco delle app con restrizioni nello stesso formato.

> [!IMPORTANT]
> I profili dispositivo che usano le impostazioni per app con restrizioni devono essere assegnati ai gruppi di utenti.

## <a name="show-or-hide-apps-supervised-only"></a>Mostra o nascondi le app (solo con supervisione)

Nell'elenco delle app da mostrare o nascondere è possibile configurare uno degli elenchi seguenti nei dispositivi con supervisione che eseguono iOS 9.3 o versione successiva.

- **App nascoste**: immettere un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o aprire queste app.
- **App visibili**: immettere un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.

Per aggiungere app a questi elenchi, è possibile:

- Scegliere **Aggiungi** per aggiungere l'URL dell'App Store iTunes dell'app desiderata. Ad esempio, per aggiungere l'app Cartelle di lavoro Microsoft, immettere `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Per trovare l'URL di un'app, aprire iTunes App Store e cercare l'app. Ad esempio, cercare `Microsoft Remote Desktop` o `Microsoft Word`. Selezionare l'app e copiare l'URL.

  È anche possibile usare iTunes per trovare l'app e quindi usare l'attività **Copia collegamento** per ottenere l'URL dell'app.

- Importare un file CSV con i dettagli sull'app, incluso l'URL. Usare il formato `<app url>, <app name>, <app publisher>`. In alternativa, esportare un elenco esistente che include l'elenco delle app con restrizioni nello stesso formato.

## <a name="wireless"></a>Wireless

- **Dati in roaming**: scegliere **Blocca** per impedire il roaming dei dati nella rete cellulare. **Non configurato** (impostazione predefinita) consente il roaming dati quando il dispositivo si trova in una rete cellulare.
- **Recupero in background globale durante il roaming**: **Blocca** impedisce l'uso della funzionalità di recupero in background globale durante il roaming nella rete cellulare. **Non configurato** (impostazione predefinita) consente al dispositivo di recuperare dati, ad esempio messaggi di posta elettronica, durante il roaming in una rete cellulare.
- **Chiamata vocale**: scegliere **Blocca** per impedire agli utenti di usare la funzionalità di chiamata vocale nel dispositivo. **Non configurato** (impostazione predefinita) consente la chiamata vocale nel dispositivo.
- **Roaming vocale**: scegliere **Blocca** per impedire il roaming vocale nella rete cellulare. **Non configurato** (impostazione predefinita) consente il roaming vocale quando il dispositivo si trova in una rete cellulare.
- **Modifiche alle impostazioni dell'utilizzo della rete dati dell'app (solo con supervisione)**: scegliere **Blocca** per impedire modifiche alle impostazioni per l'utilizzo della rete dati dell'app. **Non configurato** (impostazione predefinita) consente all'utente di controllare le app che possono usare la rete dati.
- **Le modifiche alle impostazioni di piano cellulare (solo con supervisionate)**: **blocco** impedisce agli utenti di modificare le impostazioni nel piano di cellulare. **Non configurato** (impostazione predefinita) consente agli utenti di apportare modifiche.

  Questa funzionalità si applica a:  
  - iOS 11.0 e versioni successive

- **Hotspot personale**: **blocco** consente di disattivare l'hotspot personale nel dispositivo degli utenti con ogni sincronizzazione del dispositivo. Questa impostazione potrebbe non essere compatibile con alcuni gestori. **Non configurato** (impostazione predefinita) mantiene la configurazione hotspot personale come impostazione predefinita impostata dall'utente.
- **Aggiungi reti Wi-Fi solo tramite profili di configurazione (solo con supervisione)**: **Rendi obbligatorio** impone al dispositivo l'uso esclusivo delle reti Wi-Fi impostate tramite profili di configurazione di Intune. **Non configurato** (impostazione predefinita) consente al dispositivo di usare altre reti Wi-Fi.
- **Regole di utilizzo della rete cellulare (solo app gestite)**: definire i tipi di dati usabili dalle app gestite nelle reti cellulari. Le opzioni disponibili sono:
  - **Blocca l'uso della rete dati**: bloccare l'uso della rete dati per **Tutte le app gestite** oppure **Scegliere app specifiche**.
  - **Blocca l'uso della rete dati durante il roaming**: bloccare l'uso della rete dati durante il roaming per **Tutte le app gestite** oppure **Scegliere app specifiche**.

## <a name="connected-devices"></a>Dispositivi connessi

- **AirDrop (solo con supervisione)**: **Blocca** impedisce l'uso di AirDrop nel dispositivo. **Non configurato** (impostazione predefinita) consente l'uso della funzionalità AirDrop per scambiare contenuti con dispositivi vicini.
- **Associazione di Apple Watch (solo con supervisione)**: **Blocca** impedisce l'associazione con un Apple Watch. **Non configurato** (impostazione predefinita) consente al dispositivo l'associazione con un Apple Watch.
- **Rilevamento del polso per l'Apple Watch associato**: **Rendi obbligatorio** impone l'uso del rilevamento del polso a un Apple Watch associato. Se richiesto, l'Apple Watch non visualizza notifiche se non è indossato. 
- **Modifica Bluetooth (solo con supervisione)**: **Blocca** impedisce all'utente finale di modificare le impostazioni Bluetooth nel dispositivo. **Non configurato** (impostazione predefinita) consente all'utente di modificare queste impostazioni.
- **Associazione di host per controllare i dispositivi a cui può essere associato un dispositivo iOS (solo con supervisione)**: **Non configurato** (impostazione predefinita) consente l'associazione di host in modo che l'amministratore possa controllare a quali dispositivi può essere associato un dispositivo iOS. **Blocca** impedisce l'associazione di host.
- **Richiedi la password associata alle richieste AirPlay in uscita**: **Rendi obbligatorio** richiede una password di associazione quando l'utente usa AirPlay per trasmettere i contenuti ad altri dispositivi di Apple. **Non configurato** (impostazione predefinita) consente all'utente di trasmettere i contenuti con AirPlay senza immettere una password.
- **Blocca AirPrint(solo con supervisione)**: scegliere **Blocca** per impedire l'uso della funzionalità AirPrint nel dispositivo. **Non configurato** (impostazione predefinita) consente all'utente di usare AirPrint.
  - **Impedisci l'archiviazione di credenziali AirPrint in Keychain (solo con supervisione)**: **Blocca** impedisce l'uso dell'archiviazione Keychain per nome utente e password nel dispositivo. **Non configurato** (impostazione predefinita) consente l'archiviazione di nome utente e password per AirPrint nell'app Keychain.
  - **Richiedi un certificato TLS attendibile per AirPrint (solo con supervisione)**: **Rendi obbligatorio** impone al dispositivo l'uso di certificati attendibili per le comunicazioni di stampa TLS.
  - **Impedisci l'individuazione iBeacon delle stampanti AirPrint (solo con supervisione)**: **Blocca** impedisce il phishing del traffico di rete tramite beacon AirPrint Bluetooth dannosi. **Non configurato** (impostazione predefinita) consente l'annuncio delle stampanti AirPrint nel dispositivo.
- **Bloccare l'impostazione di nuovi vicino i dispositivi (solo con supervisionati)**: **blocco** disabilita il prompt per impostare i nuovi dispositivi vicini. **Non configurato** (impostazione predefinita) consente istruzioni agli utenti di connettersi ad altri dispositivi di Apple nelle vicinanze.

  Questa funzionalità si applica a:  
  - iOS 11.0 e versioni successive

## <a name="keyboard-and-dictionary"></a>Tastiera e dizionario

- **Ricerca della definizione delle parole (solo con supervisione)**: **Blocca** impedisce all'utente di evidenziare una parola e quindi di cercarne la definizione nel dispositivo. **Non configurata** consente l'accesso alla funzionalità di ricerca della definizione.
- **Tastiere predittive (solo con supervisione)**: **Non configurata** consente l'uso di tastiere predittive per suggerire le parole che l'utente potrebbe voler scrivere. **Blocca** impedisce questa funzionalità.
- **Correzione automatica (solo con supervisione)**: **Non configurata** consente al dispositivo di correggere automaticamente le parole errate. **Blocca** impedisce l'uso della correzione automatica.
- **Controllo ortografico tastiera (solo con supervisione)**: **Non configurata** consente l'uso del controllo ortografico nel dispositivo. **Blocca** non consente il correttore ortografico.
- **Scelte rapida da tastiera (solo con supervisione)**: **Non configurata** consente l'uso di scelte rapida da tastiera nel dispositivo. **Blocca** impedisce all'utente di usare scelte rapida da tastiera.
- **Dettatura (solo con supervisione)**: **Blocca** impedisce all'utente di immettere testo con l'input vocale. **Non configurata** consente all'utente di usare l'input con dettatura.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione

- **Backup in iCloud**: **Non configurata** consente all'utente di eseguire il backup del dispositivo in iCloud. **Blocca** impedisce all'utente di eseguire il backup del dispositivo in iCloud.
- **Block iCloud Document sync** (Blocca sincronizzazione dei documenti in iCloud): **Non configurato** consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud. **Blocca** impedisce a iCloud di sincronizzare documenti e dati.
- **Sincronizzazione dello streaming foto in iCloud**: **Non configurata** consente agli utenti di abilitare nel dispositivo la funzionalità **Il mio streaming foto** per sincronizzare le foto in iCloud in modo che siano disponibili in tutti i dispositivi degli utenti. **Blocca** impedisce la sincronizzazione dello streaming foto in iCloud.
- **Backup crittografato**: **Rendi obbligatorio** in modo che i backup del dispositivo debbano essere crittografati.
- **Libreria foto di iCloud**: impostare su **Blocca** per disabilitare l'uso della libreria foto di iCloud per archiviare foto e video nel cloud. Eventuali foto non scaricate completamente dalla Libreria foto di iCloud nel dispositivo vengono rimosse dal dispositivo. **Non configurata** consente l'uso della libreria foto iCloud.
- **Sincronizzazione delle app gestite nel cloud**: **Non configurata** consente alle app gestite di Intune di sincronizzare i dati con l'account iCloud dell'utente. **Blocca** impedisce la sincronizzazione dei dati in iCloud.
- **Flusso di foto condivise**: scegliere **Blocca** per disabilitare **Condivisione foto di iCloud** nel dispositivo. **Non configurata** consente flussi di foto condivise.
- **Continuazione dell'attività**: **Non configurata** consente all'utente di proseguire il lavoro iniziato in un dispositivo iOS in un altro dispositivo iOS o macOS (handoff). **Blocca** impedisce l'handoff.
- **Blocca la sincronizzazione Keychain con iCloud**: scegliere **Blocca** per disabilitare la sincronizzazione delle credenziali archiviate in Keychain su iCloud. **Non configurata** consente agli utenti di sincronizzare queste credenziali.
- **Blocca il backup di libri aziendali**: scegliere **Blocca** per impedire agli utenti di eseguire un backup di libri aziendali. **Non configurata** consente agli utenti di eseguire il backup di questi libri.
- **Blocca la sincronizzazione di metadati di libri aziendali (note e informazioni di rilievo)**: **Blocca** impedisce la sincronizzazione di note ed evidenziazioni nei libri aziendali. **Non configurata** consente la sincronizzazione.

## <a name="autonomous-single-app-mode-supervised-only"></a>Modalità applicazione singola autonoma (solo con supervisione)

Usare queste impostazioni per configurare i dispositivi iOS in modo che eseguano specifiche app in modalità app singola autonoma. Quando è configurata questa modalità e l'app viene eseguita, il dispositivo è bloccato e può eseguire solo tale app. Ad esempio, aggiungere un'app che consente agli utenti di eseguire un test nel dispositivo. Quando le azioni dell'app sono state completate o si rimuovono questi criteri, il dispositivo torna allo stato normale.

Per aggiungere le app, è possibile:

- Immettere **Nome app** e **ID bundle dell'app**, quindi selezionare **Aggiungi**. [ID bundle per le app iOS predefinite](#bundle-ids-for-built-in-ios-apps) (in questo articolo) include alcune app con i relativi ID.
- **Importare** un file CSV con l'elenco dei nomi di app e i relativi ID bundle. Oppure **esportare** un elenco esistente che include le app.

## <a name="kiosk-supervised-only"></a>Modalità tutto schermo (solo con supervisione)

- **App da eseguire in modalità tutto schermo**: scegliere il tipo di app da eseguire in modalità tutto schermo. Le opzioni disponibili sono:
  - **Non configurato**: non vengono applicate le impostazioni modalità tutto schermo. Il dispositivo non viene eseguita in modalità tutto schermo.
  - **App Store**: immettere l'URL di un'app in iTunes App Store.
  - **App gestita**: scegliere un'app aggiunta a Intune.
  - **App predefinita**: immettere il [ID bundle](#bundle-ids-for-built-in-ios-apps) (in questo articolo) dell'app predefinita.

- **Tocco per l'accesso facilitato**: **Rendi obbligatorio** per richiedere la presenza dell'impostazione di accessibilità Tocco per l'accesso facilitato nel dispositivo. Questa funzionalità offre supporto agli utenti per i movimenti sullo schermo che potrebbero risultare difficili. **Non configurata** non consente di eseguire o abilitare questa funzionalità in modalità tutto schermo.
- **Inverti colori**: **Rendi obbligatorio** consente di rendere disponibile l'impostazione di accessibilità Inverti colori in modo che gli utenti con problemi visivi possano modificare quanto visualizzato sullo schermo. **Non configurata** non consente di eseguire o abilitare questa funzionalità in modalità tutto schermo.
- **Audio mono**: **Rendi obbligatorio** consente di rendere disponibile l'impostazione di accessibilità Audio mono nel dispositivo. **Non configurata** non consente di eseguire o abilitare questa funzionalità in modalità tutto schermo.
- **VoiceOver**: **Rendi obbligatorio** consente di rendere disponibile l'impostazione di accessibilità VoiceOver nel dispositivo per leggere a voce alta il testo sullo schermo. **Non configurata** non consente di eseguire o abilitare questa funzionalità in modalità tutto schermo.
- **Zoom**: **Rendi obbligatorio** consente di rendere disponibile l'impostazione Zoom nel dispositivo per consentire agli utenti di usare il tocco per ingrandire la schermata. **Non configurata** non consente di eseguire o abilitare questa funzionalità in modalità tutto schermo.
- **Blocco automatico**: **Consenti** per abilitare il blocco automatico del dispositivo. **Non configurata** disabilita questa funzionalità.
- **Commutatore suoneria**: **Consenti** per abilitare il commutatore della suoneria (muto) nel dispositivo. **Non configurata** disabilita questa funzionalità.
- **Rotazione dello schermo**: **Consenti** per abilitare la modifica dell'orientamento dello schermo quando si ruota il dispositivo. **Non configurata** disabilita questa funzionalità.
- **Pulsante Sospensione schermo**: scegliere **Consenti** per disabilitare il pulsante di riattivazione dalla sospensione dello schermo nel dispositivo. **Non configurata** abilita questa funzionalità.
- **Tocca**: **Blocca** disabilita il touchscreen nel dispositivo. **Non configurata** consente all'utente di usare il touchscreen.
- **Pulsanti volume**: **Consenti** per abilitare l'uso dei pulsanti del volume nel dispositivo. **Non configurata** disabilita i pulsanti del volume.
- **Controllo del tocco per l'accesso facilitato**: **Consenti** per consentire agli utenti di usare la funzione tocco per l'accesso facilitato. **Non configurata** disabilita questa funzionalità.
- **Controllo dell'inversione colori**: **Consenti** per consentire modifiche dell'inversione colori e permettere agli utenti di modificare la funzione di inversione colori. **Non configurata** disabilita questa funzionalità.
- **Pronuncia per il testo selezionato**: **Consenti** per rendere disponibile le impostazioni di accessibilità Selezione comandi vocali nel dispositivo. Questa funzionalità legge il testo selezionato dall'utente. **Non configurata** disabilita questa funzionalità.
- **Controllo VoiceOver**: **Consenti** per consentire le modifiche del VoiceOver in modo che gli utenti possano modificare la funzione VoiceOver, ad esempio la velocità con cui viene letto il testo sullo schermo. **Non configurata** impedisce modifiche al VoiceOver.
- **Controllo dello zoom**: **Consenti** per consentire all'utente di modificare lo zoom. **Non configurata** impedisce la modifica dello zoom.

> [!NOTE]
> Prima di poter configurare un dispositivo iOS per la modalità tutto schermo, è necessario usare lo strumento Apple Configurator o il programma di registrazione dispositivi di Apple per attivare la modalità con supervisore del dispositivo. Vedere la Guida di Apple sull'uso dello strumento Apple Configurator.
> Se l'app per iOS specificata viene installata dopo aver assegnato il profilo, il dispositivo attiva la modalità tutto schermo solo dopo il riavvio.

## <a name="domains"></a>Domains

- **Domini di posta elettronica non contrassegnati** > **URL di dominio di posta elettronica**: aggiungere uno o più URL all'elenco. Quando gli utenti finali ricevono un messaggio di posta elettronica da un dominio diverso da quelli immessi, il messaggio di posta elettronica viene contrassegnato come non attendibile nell'app di posta in iOS.

- **Domini web gestiti** > **URL del dominio Web**; Aggiungere uno o più URL all'elenco. Quando i documenti vengono scaricati dai domini immessi, sono considerati come gestiti. Questa impostazione si applica solo ai documenti scaricati tramite Safari.

- **Domini riempimento automatico della password di Safari** > **URL del dominio**: aggiungere uno o più URL all'elenco. Gli utenti possono salvare solo le password Web dagli URL in questo elenco. Questa impostazione si applica solo al browser Safari e ai dispositivi iOS 9.3 e versioni successive in modalità con supervisione. Se non si specifica nessun URL, è possibile salvare le password da tutti i siti web.

## <a name="bundle-ids-for-built-in-ios-apps"></a>ID bundle per le app iOS predefinite

L'elenco seguente include l'ID bundle di alcune app comuni iOS predefinite. Per l'ID bundle di altre app rivolgersi al fornitore del software.

| ID bundle                   | Nome dell'app     | Pubblicazione |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calcolatrice   | Apple     |
| com.apple.mobilecal         | Calendario     | Apple     |
| com.apple.camera            | Fotocamera       | Apple     |
| com.apple.mobiletimer       | Orologio        | Apple     |
| com.apple.compass           | Bussola      | Apple     |
| com.apple.MobileAddressBook | Contatti     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | File        | Apple     |
| com.apple.mobileme.fmf1     | Trova amici | Apple     |
| com.apple.mobileme.fmip1    | Trova il mio iPhone  | Apple     |
| com.apple.gamecenter        | Area giochi  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Integrità       | Apple     |
| com.apple.Home              | Home         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Maps         | Apple     |
| com.apple.MobileSMS         | Messaggi     | Apple     |
| com.apple.Music             | Musica        | Apple     |
| com.apple.news              | Notizie         | Apple     |
| com.apple.mobilenotes       | Note        | Apple     |
| com.apple.Numbers           | Numeri      | Apple     |
| com.apple.Pages             | .NET        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Foto       | Apple     |
| com.apple.podcasts          | Podcast     | Apple     |
| com.apple.reminders         | Reminders    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Impostazioni     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Stocks       | Apple     |
| com.apple.tips              | Suggerimenti         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Video       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Video        | Apple     |
| com.apple.weather           | Weather      | Apple     |

## <a name="settings-that-require-supervised-mode"></a>Le impostazioni che richiedono la modalità di supervisione

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
- Download automatici delle app 
- Modifica dell'attendibilità delle applicazioni enterprise 
- Apple Music 
- Mail Drop 
- Associazione con Apple Watch 

> [!NOTE]
> Apple ha confermato che nel 2019 alcune impostazioni passeranno alla modalità solo con supervisione. È consigliabile usare le impostazioni interessate tenendo conto di questo aspetto, anziché attendere che Apple effettui la migrazione alla modalità solo con supervisione:
> - Installazione di app da parte degli utenti finali
> - Rimozione di app
> - FaceTime
> - Safari
> - iTunes
> - Contenuti espliciti
> - Documenti e dati iCloud
> - Gioco multiplayer
> - Aggiungi amici dell'area giochi
> - Siri

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È inoltre possibile limitare le funzionalità del dispositivo e le impostazioni sul [macOS](device-restrictions-macos.md) dispositivi.
