---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows 10
titlesuffix: Azure portal
description: "Informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo in dispositivi Windows 10.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/8/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc50d6f5c4b0350d0117b5d68a0b9ac3e9ec3ab3
ms.sourcegitcommit: 2c7794848777e73d6a9502b4e1000f0b07ac96bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows 10 e versioni successive in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>Generale
- **Acquisizione di schermata (solo dispositivi mobili)**: consente all'utente di acquisire la schermata del dispositivo come immagine.
- **Copia e incolla (solo dispositivi mobili)** - Consente le azioni di copia e incolla tra app sul dispositivo.
- **Annullamento manuale della registrazione** - Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.
- **Installazione manuale del certificato radice (solo per dispositivi mobili)**: impedisce all'utente di installare manualmente i certificati radice e i certificati intermedi CAP.
- **Invio dati di diagnostica** - I valori possibili sono:
    - **No**: non vengono inviati dati a Microsoft
    - **Di base**: vengono inviate a Microsoft informazioni limitate
    - **Avanzati**: vengono inviati a Microsoft dati di diagnostica avanzati
    - **Completi** Invia gli stessi dati di Avanzati, più dati aggiuntivi sullo stato del dispositivo
- **Fotocamera** - Consente o blocca l'uso della fotocamera sul dispositivo.
- **Sincronizzazione dei file di OneDrive**: impedisce al dispositivo di sincronizzare i file in OneDrive.
- **Archivi rimovibili**: specifica se è possibile usare con il dispositivo supporti di archiviazione esterni come le schede SD.
- **Georilevazione** - Specifica se il dispositivo può usare le informazioni dei servizi di posizione.
- **Internet condiviso** - Consente l'uso della condivisione della connessione Internet sul dispositivo.
- **Ripristino del telefono** - Controlla se l'utente può eseguire un ripristino delle impostazioni predefinite nel dispositivo.
- **Connessione USB (solo per dispositivi mobili)**: controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni tramite una connessione USB.
- **Modalità antifurto (solo per dispositivi mobili)**: configura l'attivazione della modalità antifurto di Windows.
- **Cortana** - Abilita o disabilita l'assistente vocale Cortana.
- **Registrazione voce (solo per dispositivi mobili)**: consente o impedisce l'uso del registratore vocale del dispositivo.
- **Modifica del nome del dispositivo**: impedisce all'utente finale di modificare il nome del dispositivo (solo Windows 10 Mobile).
- **Aggiungi pacchetti di provisioning**: blocca l'agente di configurazione di runtime che installa pacchetti di provisioning.
- **Rimuovi i pacchetti di provisioning**: blocca l'agente di configurazione di runtime che rimuove pacchetti di provisioning.
- **Individuazione dei dispositivi**: blocca l'individuazione di un dispositivo da parte di altri dispositivi.
- **Cambio modalità per l'attività (solo dispositivi mobili)**: blocca il cambio modalità per l'attività nel dispositivo.
- **Finestra di dialogo di errore per la scheda SIM (solo dispositivi mobili)**: blocca la visualizzazione di un messaggio di errore nel dispositivo se non viene rilevata alcuna scheda SIM.
- **Ridistribuzione automatica**: consente agli utenti con diritti amministrativi di eliminare tutti i dati utente e tutte le impostazioni utente tramite **CTRL+tasto WINDOWS+R** nella schermata di blocco del dispositivo. Il dispositivo viene automaticamente riconfigurato e registrato di nuovo nella gestione.


## <a name="password"></a>Password
-   **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
    -   **Tipo di password richiesto** - Consente di specificare se la password deve essere solo numerica o alfanumerica.
    -   **Lunghezza minima password** Si applica solo a Windows 10 Mobile.
    -   **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Per i dispositivi che eseguono Windows 10: se nel dispositivo è abilitato BitLocker, viene attivata la modalità di ripristino BitLocker se l'accesso ha esito negativo per il numero di volte specificato. Se nel dispositivo non è abilitato BitLocker, questa impostazione non si applica.
Per i dispositivi che eseguono Windows 10 Mobile: se l'accesso ha esito negativo per il numero di volte specificato, il dispositivo viene cancellato.
    -   **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il periodo di tempo per cui un dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.
    -   **Scadenza password (giorni)** - Specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo.
    -   **Impedisci riutilizzo delle password precedenti** - Specifica il numero di password utilizzate in precedenza che il dispositivo deve ricordare.
    -   **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività (solo Mobile)** - Specifica che l'utente deve inserire una password per sbloccare il dispositivo (solo Windows 10 Mobile).
    -   **Password semplici**: consente di autorizzare l'uso di password semplici come 1111 o 1234. Questa impostazione consente o blocca anche l'uso delle password grafiche di Windows.
-   **Crittografia**: consente di abilitare la crittografia nei dispositivi di destinazione.

## <a name="personalization"></a>Personalization

- **URL dell'immagine di sfondo del desktop (solo desktop)**: consente di specificare l'URL di un'immagine in formato JPEG, PNG o JPG che verrà usata come sfondo del desktop di Windows. Gli utenti non possono modificare questa impostazione.

## <a name="privacy"></a>Privacy

-   **Personalizzazione dell'input**: non consente l'uso di servizi di riconoscimento vocale basati sul cloud per Cortana, app di dettatura o app di Microsoft Store. Se si consentono questi servizi, Microsoft potrebbe raccogliere dati vocali per migliorare il servizio.
-   **Accettazione automatica delle richieste di associazione e di consenso utente sulla privacy**: consente a Windows di accettare automaticamente messaggi di associazione e consenso sulla privacy durante l'esecuzione di app.

È possibile definire le informazioni accessibili per tutte le app nel dispositivo. È possibile definire eccezioni per le singole app tramite **Eccezioni alla privacy per app**.

### <a name="exceptions"></a>Eccezioni

- **Informazioni account** - Specificare se l'app può accedere a nome utente, immagine e altre informazioni di contatto.
- **App in background** - Specificare se l'app può essere eseguita in background.
- **Calendario** - Specificare se l'app può accedere al calendario.
- **Registro chiamate** - Specificare se l'app può accedere al registro delle chiamate personale.
- **Fotocamera** - Specificare se l'app può accedere alla fotocamera.
- **Contatti** - Specificare se l'app può accedere ai contatti.
- **Posta elettronica** - Specificare se l'app può accedere alla posta elettronica e inviare messaggi.
- **Posizione** - Specificare se l'app può accedere a informazioni sulla posizione.
- **Messaggistica** - Specificare se l'app può leggere o inviare SMS o MMS.
- **Microfono** - Specificare se l'app può usare il microfono.
- **Movimento** - Specificare se l'app può accedere a informazioni sul movimento dei dispositivi.
- **Notifiche** - Specificare se l'app può accedere alle notifiche.
- **Telefono** - Specificare se l'app può accedere al telefono.
- **Radio** Alcune app usano le radio nel dispositivo, ad esempio Bluetooth, per inviare e ricevere i dati e devono attivare o disattivare queste radio. Specificare se l'app può controllare queste radio.
- **Attività** - Specificare se l'app può accedere alle attività personali.
- **Dispositivi attendibili** - Specificare se l'app può usare dispositivi attendibili, ovvero hardware già connesso o fornito con il PC, il tablet o il telefono in uso. Ad esempio: TV, proiettori e così via.
- **Commenti e diagnostica** - Specificare se l'app può accedere alle informazioni di diagnostica.
- **Sincronizza con i dispositivi** - Specificare se l'app può condividere e sincronizzare automaticamente le informazioni con dispositivi wireless non associati in modo esplicito a questo PC, tablet o telefono.

## <a name="per-app-privacy-exceptions"></a>Eccezioni alla privacy per app

È possibile aggiungere app che devono avere un comportamento diverso in relazione alla privacy da quello definito in "Privacy predefinita".

- **Nome pacchetto** - Nome della famiglia di pacchetti dell'app.
- **Nome dell'app** - Nome dell'app.

### <a name="exceptions"></a>Eccezioni

- **Informazioni account** - Specificare se l'app può accedere a nome utente, immagine e altre informazioni di contatto.
- **App in background** - Specificare se l'app può essere eseguita in background.
- **Calendario** - Specificare se l'app può accedere al calendario.
- **Registro chiamate** - Specificare se l'app può accedere al registro delle chiamate personale.
- **Fotocamera** - Specificare se l'app può accedere alla fotocamera.
- **Contatti** - Specificare se l'app può accedere ai contatti.
- **Posta elettronica** - Specificare se l'app può accedere alla posta elettronica e inviare messaggi.
- **Posizione** - Specificare se l'app può accedere a informazioni sulla posizione.
- **Messaggistica** - Specificare se l'app può leggere o inviare SMS o MMS.
- **Microfono** - Specificare se l'app può usare il microfono.
- **Movimento** - Specificare se l'app può accedere a informazioni sul movimento dei dispositivi.
- **Notifiche** - Specificare se l'app può accedere alle notifiche.
- **Telefono** - Specificare se l'app può accedere al telefono.
- **Radio** Alcune app usano le radio nel dispositivo, ad esempio Bluetooth, per inviare e ricevere i dati e devono attivare o disattivare queste radio. Specificare se l'app può controllare queste radio.
- **Attività** - Specificare se l'app può accedere alle attività personali.
- **Dispositivi attendibili** - Specificare se l'app può usare dispositivi attendibili, ovvero hardware già connesso o fornito con il PC, il tablet o il telefono in uso. Ad esempio: TV, proiettori e così via.
- **Commenti e diagnostica** - Specificare se l'app può accedere alle informazioni di diagnostica.
- **Sincronizza con i dispositivi** - Specificare se l'app può condividere e sincronizzare automaticamente le informazioni con dispositivi wireless non associati in modo esplicito a questo PC, tablet o telefono.

## <a name="locked-screen-experience"></a>Esperienza della schermata bloccata

- **Notifiche del centro notifiche (solo per dispositivi mobili)**: consente la visualizzazione delle notifiche del centro notifiche nella schermata di blocco del dispositivo (solo Windows 10 Mobile).
- **URL dell'immagine della schermata bloccata (solo desktop)**: specifica l'URL di un'immagine in formato JPEG, PNG o JPG che verrà usata come sfondo della schermata bloccata di Windows. Gli utenti non possono modificare questa impostazione.
-   **Timeout dello schermo configurabile dall'utente (solo dispositivi mobili)**: consente agli utenti di configurare il timeout. 
-   **Cortana nella schermata di blocco (solo desktop)**: non consente all'utente di interagire con Cortana quando è attiva la schermata di blocco del dispositivo (solo Windows 10 Desktop).
-   **Notifiche di tipo avviso popup nella schermata di blocco**: blocca la visualizzazione dei messaggi di avviso nella schermata di blocco del dispositivo.
-   **Timeout dello schermo (solo dispositivi mobili)**: specifica il tempo in secondi tra il blocco e lo spegnimento dello schermo.



## <a name="app-store"></a>App Store

-   **App Store (solo dispositivi mobili)** - Consente o blocca l'uso dell'App Store nei dispositivi Windows 10 Mobile.
-   **Aggiorna automaticamente le app dallo Store**: consente l'aggiornamento automatico delle app installate da Microsoft Store.
-   **Installazione di app attendibile**: consente il trasferimento locale delle app con certificato attendibile.
-   **Sblocco dallo sviluppatore**: consente la modifica delle impostazioni da parte degli sviluppatori Windows, ad esempio consentire all'utente finale di modificare le app trasferite localmente.
-   **Dati app utente condivisi**: consente alle app di condividere dati tra utenti diversi dello stesso dispositivo.
-   **Usa solo lo Store privato**: consente agli utenti finali di scaricare app da uno Store privato.
-   **Avvio di app originate dallo Store**: disabilita tutte le app preinstallate nel dispositivo o scaricate da Microsoft Store.
-   **Installa i dati dell'app nel volume di sistema**: impedisce alle app di archiviare dati nel volume di sistema del dispositivo.
-   **Installa le app nell'unità di sistema**: impedisce alle app di archiviare dati nell'unità di sistema del dispositivo.
-   **Game DVR (solo desktop)**: configura se la registrazione e la trasmissione dei giochi sono consentite.
-   **App solo dallo Store**: specifica se gli utenti possono installare le app da posizioni diverse dall'App Store.



## <a name="edge-browser"></a>Browser Edge

-   **Browser Microsoft Edge (solo dispositivi mobili)** - Consente l'uso del browser Web Edge sul dispositivo.
-   **Elenco a discesa della barra degli indirizzi (solo desktop)**: usare questa opzione per impedire a Microsoft Edge di visualizzare suggerimenti in un elenco a discesa durante la digitazione. Ciò consente di ridurre al minimo l'uso di larghezza di banda tra Microsoft Edge e i servizi Microsoft.
-   **Sincronizza i Preferiti tra i browser Microsoft (solo desktop)**: consente la sincronizzazione dei Preferiti tra Microsoft Edge e Internet Explorer in Windows.
-   **Invia intestazioni DNT (Do Not Track)** - Configura il browser Microsoft Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti.
-   **Cookie** - Consente al browser di salvare i cookie di Internet per il dispositivo.
-   **JavaScript** - Consente di eseguire script, ad esempio Javascript, nel browser Microsoft Edge.
-   **Pop-up**: blocca le finestra popup del browser (si applica solo a Windows 10 Desktop).
-   **Suggerimenti per la ricerca** - Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca.
-   **Invia traffico Intranet a Internet Explorer**: consente agli utenti di aprire siti Web della Intranet in Internet Explorer (solo per Windows 10 Desktop).
-   **Riempimento automatico**: consente agli utenti di modificare le impostazioni di completamento automatico nel browser (solo per Windows 10 Desktop).
-   **Strumento per la gestione delle password** - Abilita o disabilita la funzione di gestione password di Microsoft Edge.
-   **Posizione elenco siti modalità Enterprise** - Specifica dove trovare l'elenco dei siti Web che si aprono in modalità Enterprise. L'elenco non è modificabile dagli utenti.<br>Solo Windows 10 Desktop.
-   **Strumenti di sviluppo**: impedisce all'utente finale di aprire gli strumenti di sviluppo di Microsoft Edge.
-   **Estensioni**: consente all'utente finale di installare le estensioni di Microsoft Edge nel dispositivo.
-   **InPrivate Browsing**: impedisce all'utente finale di aprire sessioni InPrivate Browsing.
-   **Mostra la pagina alla prima esecuzione**: impedisce la visualizzazione della pagina introduttiva quando si esegue Microsoft Edge per la prima volta.
    -   **URL della prima esecuzione**: specifica l'URL della pagina che viene visualizzata quando l'utente esegue Microsoft Edge per la prima volta (solo Windows 10 Mobile).
-   **Home page**: aggiunge un elenco dei siti da usare come home page nel browser Microsoft Edge (solo desktop).
-   **Modifiche alla pagina iniziale**: consente agli utenti di modificare la scelta delle pagine iniziali visualizzate all'avvio di Microsoft Edge. Usare l'impostazione Home page per creare la pagina o l'elenco di pagine che viene aperta all'avvio di Microsoft Edge.
-   **Blocca l'accesso ai flag Informazioni su**: impedisce all'utente finale di accedere alla pagina di "flag Informazioni su" in Microsoft Edge che contiene impostazioni sperimentali e di sviluppo.
-   **Indirizzo IP localhost WebRtc**: blocca la visualizzazione dell'indirizzo IP localhost IP quando si effettuano telefonate tramite il protocollo RTC Web.
-   **Motore di ricerca predefinito**: specifica il motore di ricerca predefinito da usare. Gli utenti finali possono modificare questo valore in qualsiasi momento.
-   **Cancella i dati di esplorazione all'uscita**: cancella la cronologia e i dati di esplorazione quando l'utente esce da Microsoft Edge.
-   **Raccolta di dati per il riquadro animato**: interrompe la raccolta di informazioni dal riquadro animato quando gli utenti aggiungono un sito al menu Start da Microsoft Edge.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen per Microsoft Edge**: abilita SmartScreen di Edge per l'accesso al sito e i download di file.
- **Accesso a siti dannosi**: impedisce agli utenti di ignorare gli avvisi del filtro SmartScreen di Windows Defender e impedisce loro di passare al sito.
- **Download di file non verificati**: impedisce agli utenti di ignorare gli avvisi del filtro SmartScreen di Windows Defender e impedisce loro di scaricare file non verificati.

## <a name="search"></a>Cerca
- **Ricerca sicura (solo dispositivi mobili)**: controlla come Cortana filtra il contenuto per adulti nei risultati della ricerca. È possibile selezionare **Strict**, **Moderate** o consentire all'utente finale di scegliere le proprie impostazioni.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
-   **Account Microsoft** - Consente all'utente di associare un account Microsoft con il dispositivo.
-   **Account non Microsoft** - Consente all'utente di aggiungere account di posta elettronica al dispositivo che non sono associati con un account Microsoft.
-   **Sincronizzazione delle impostazioni per l'account Microsoft** - Consente che le impostazioni del dispositivo e delle app associate con un account Microsoft vengano sincronizzate fra i dispositivi.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività

-   **Canale per rete dati**: impedisce agli utenti di usare dati, ad esempio di navigare nel Web, mentre sono connessi a una rete dati. 
-   **Roaming dati** - Consente il roaming tra reti quando si accede ai dati.
-   **VPN nella rete cellulare** - Controlla se il dispositivo può accedere a connessioni VPN quando è collegato a una rete cellulare.
-   **Roaming VPN nella rete cellulare** - Controlla se il dispositivo può accedere a connessioni VPN quando è in roaming su una rete cellulare.
-   **Bluetooth** - Controlla se l'utente può abilitare e configurare Bluetooth nel dispositivo.
-   **Individuabilità di Bluetooth** - Consente che il dispositivo sia scoperto da altri dispositivi con la funzione Bluetooth attivata.
-   **Pre-associazione Bluetooth**: consente di configurare dispositivi Bluetooth specifici per l'associazione automatica con un dispositivo host.
-   **Annunci con Bluetooth** - Consente al dispositivo di ricevere annunci tramite Bluetooth.
-   **Servizio dispositivi connessi**: specifica se consentire il servizio dispositivi connessi, che abilita l'individuazione e la connessione ad altri dispositivi Bluetooth.
-   **NFC** - Consente all'utente di attivare e configurare funzionalità Near Field Communications sul dispositivo.
-   **Wi-Fi** - Consente all'utente di attivare e configurare le funzionalità Wi-Fi del dispositivo (solo Windows 10 Mobile).
-   **Connetti automaticamente a hotspot Wi-Fi** - Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione.
-   **Configurazione Wi-Fi manuale** - Controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi (solo Windows 10 Mobile).
-   **Intervallo di analisi Wi-Fi**: specifica la frequenza con cui i dispositivi ricercano le reti Wi-Fi. Specificare un valore compreso tra 1 (ricerca più frequente) e 500 (ricerca meno frequente).
-   **Servizi Bluetooth consentiti**: specifica sotto forma di stringhe esadecimali un elenco di profili e servizi Bluetooth consentiti.


## <a name="control-panel-and-settings"></a>Pannello di controllo e impostazioni

-   **App Impostazioni**: blocca l'accesso all'app Impostazioni di Windows.
    -   **Sistema**: blocca l'accesso all'area di sistema dell'app Impostazioni.
        -   **Modifica delle impostazioni di risparmio energia e sospensione (solo desktop)**: impedisce all'utente finale di modificare le impostazioni di risparmio energia e sospensione del dispositivo.
    -   **Dispositivi**: blocca l'accesso all'area dei dispositivi dell'app Impostazioni.
    -   **Rete Internet**: blocca l'accesso all'area rete e Internet dell'app Impostazioni.
    -   **Personalizzazione**: blocca l'accesso all'area di personalizzazione dell'app Impostazioni.
    -   **Account**: blocca l'accesso all'area degli account dell'app Impostazioni.
    -   **Ora e lingua**: blocca l'accesso all'area dell'ora e della lingua dell'app Impostazioni.
        -   **Modifica dell'ora di sistema**: impedisce all'utente finale di modificare la data e l'ora del dispositivo.
        -   **Modifica delle impostazioni dell'area (solo desktop)**: impedisce all'utente finale di modificare le impostazioni dell'area del dispositivo.
        -   **Modifiche alle impostazioni della lingua (solo desktop)**: impedisce all'utente finale di modificare le impostazioni della lingua del dispositivo.
    -   **Giochi**: blocca l'accesso all'app Giochi in Impostazioni.
    -   **Accessibilità**: blocca l'accesso all'area accessibilità dell'app Impostazioni.
    -   **Riservatezza**: blocca l'accesso all'area riservatezza dell'app Impostazioni.
    -   **Aggiornamento e sicurezza** : blocca l'accesso all'area Aggiornamento e sicurezza dell'app Impostazioni.

## <a name="start"></a>Avvia

- **Rimuovi le app dalla barra della applicazioni**: impedisce all'utente di rimuovere app dal menu Start.
- **Documenti nel menu Start**: nasconde o mostra la cartella Documenti nel menu Start di Windows.
- **Download nel menu Start**: nasconde o mostra la cartella Download nel menu Start di Windows.
- **Esplora file nel menu Start**: nasconde o mostra l'app Esplora file nel menu Start di Windows.
- **Gruppo Home nel menu Start**: nasconde o mostra la cartella Gruppo Home nel menu Start di Windows.
- **Musica nel menu Start**: nasconde o mostra la cartella Musica nel menu Start di Windows.
- **Rete nel menu Start**: nasconde o mostra la cartella Rete nel menu Start di Windows.
- **Cartella Personale nel menu Start**: nasconde o mostra la cartella Personale nel menu Start di Windows.
- **Immagini nel menu Start**: nasconde o mostra la cartella delle immagini nel menu Start di Windows.
- **Impostazioni nel menu Start**: nasconde o mostra l'app Impostazioni nel menu Start di Windows.
- **Video nel menu Start**: nasconde o mostra la cartella dei video nel menu Start di Windows.

## <a name="display"></a>Schermo

- **Attiva il ridimensionamento del programma GDI per le app**
- **Disattiva il ridimensionamento del programma GDI per le ap**

  Il ridimensionamento DPI del programma GDI consente alle app non sensibili ai valori DPI di diventare sensibili ai valori DPI per monitor. Specificare le app legacy con ridimensionamento DPI del programma GDI attivato. Quando il ridimensionamento DPI del programma GDI è configurato sia per l'attivazione che per la disattivazione in un'app, il ridimensionamento è disattivato per l'app.

## <a name="kiosk-preview"></a>Modalità tutto schermo (anteprima)

-   **Modalità tutto schermo**: identifica il tipo di [modalità tutto schermo](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc) supportata dai criteri. Le opzioni includono:

      - **Non configurata** (impostazione predefinita): il criterio non abilita la modalità tutto schermo. 
      - **App singola per chiosco multimediale**: il profilo abilita il dispositivo come app singola per chiosco multimediale.
      - **App multiple per chiosco multimediale**: il profilo abilita il dispositivo come app multiple per chiosco multimediale.

    Le app singole per chiosco multimediale richiedono le seguenti impostazioni:

      - **Account utente**: specifica l'account utente locale (per il dispositivo) o l'account di accesso di Azure AD associato all'app per chiosco multimediale. Per gli account aggiunti ai domini di Azure AD, specificare l'account nel formato `domain\\username@tenant.org`.

         Per i dispositivi in ambienti pubblici, usare account con privilegi minimi per evitare attività non autorizzate.  

      - **ID modello utente applicazione (AUMID, Application User Model ID) dell'app**: specifica l'AUMID dell'app per chiosco multimediale. Per altre informazioni, vedere [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Trovare l'ID modello utente dell'applicazione di un'app installata).

    Per più app chiosco multimediale è richiesta una configurazione per chiosco multimediale. Usare il pulsante **Aggiungi** per creare una configurazione per chiosco multimediale o selezionarne una esistente.

    Le configurazioni per chiosco multimediale con più app includono le impostazioni seguenti:

    - **Nome della configurazione per chiosco multimediale**: nome descrittivo usato per identificare una determinata configurazione.

    - Una o più **App chiosco multimediale** costituite da:

        - **Tipo di app** che specifica il tipo dell'app chiosco multimediale.  I valori supportati includono:   

            - **App Win32**: app desktop tradizionale. È necessario il nome del percorso completo del file eseguibile, relativo al dispositivo.

            - **App UWP**: app Windows universale. È necessario l'[AUMID per l'app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

        - **Identificatore dell'app**: specifica il nome del percorso completo del file eseguibile (app Win32) o l'[AUMID dell'app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (app UWP).

    - **Barra delle applicazioni** indica se la barra delle applicazioni viene visualizzata (**Abilitata**) o nascosta (**Non configurata**) sul chiosco multimediale.

    - **Layout del menu Start**: specifica un file XML che descrive come le app [vengono visualizzate nel menu Start](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file).

    - **Utenti assegnati**: specifica uno o più account utente associati alla configurazione per chiosco multimediale. L'account può essere locale nel dispositivo o in un account di accesso di Azure AD associato all'app per chiosco multimediale. Specificare gli account appartenenti a un dominio nel formato `domain\\username@tenant.org`.

## <a name="windows-defender-antivirus"></a>Windows Defender Antivirus

-   **Monitoraggio in tempo reale** - Abilita l'analisi in tempo reale per malware, spyware e altro software indesiderato.
-   **Monitoraggio del comportamento** - Consente a Defender di controllare la presenza di modelli noti di attività sospette nei dispositivi.
-   **Network Inspection System (NIS)**: consente di proteggere i computer dagli exploit basati sulla rete. Usa le firme delle vulnerabilità note da Microsoft Endpoint Protection Center per consentire di rilevare e bloccare il traffico dannoso.
-   **Analizza tutti i download** - Controlla se Defender deve analizzare tutti i file scaricati da Internet.
-   **Analizza gli script caricati nei Web browser Microsoft** - Consente a Defender di analizzare gli script utilizzati in Internet Explorer.
-   **Accesso dell'utente finale a Defender** - Controlla se l'interfaccia utente di Windows Defender è nascosta agli utenti finali.
Quando questa impostazione viene modificata, ha effetto dal successivo avvio del PC dell'utente finale.
-   **Intervallo di aggiornamento della firma (in ore)**: specifica l'intervallo con il quale Defender controllerà i nuovi file di firma.
-   **Monitora l'attività di file e programmi** - Consente a Defender di monitorare l'attività di file e programmi nei dispositivi.
-   **Giorni di attesa prima dell'eliminazione di malware in quarantena** - Consente a Defender di continuare a monitorare il malware risolto per il numero di giorni specificato, in modo che sia possibile controllare manualmente i dispositivi colpiti in precedenza. Se si imposta il numero di giorni su **0**, il malware rimane nella cartella della quarantena e non viene rimosso automaticamente.
-   **Limite di utilizzo della CPU durante un'analisi** - Consente di limitare la quantità di CPU utilizzata per le analisi (da **1** a **100**).
-   **Analizza file di archivio** - Consente a Defender di analizzare i file archiviati come i file con estensione .zip o .cab.
-   **Analizza i messaggi di posta in arrivo** - Consente a Defender di analizzare i messaggi di posta elettronica non appena arrivano sul dispositivo.
-   **Analizza le unità rimovibili durante un'analisi completa** - Consente a Defender di analizzare le unità rimovibili come le chiavi USB.
-   **Analizza le unità di rete mappate durante un'analisi completa** - Consente a Defender di analizzare i file nelle unità di rete mappate.<br>Se i file sull'unità sono di sola lettura, Defender non può rimuovere il malware rilevato in tali file.
-   **Analizza file aperti da cartelle di rete**: consente a Defender di analizzare i file sulle unità di rete condivise, ad esempio i file a cui si accede da un percorso UNC.
Se i file sull'unità sono di sola lettura, Defender non può rimuovere il malware rilevato in tali file.
-   **Protezione cloud** - Consente o blocca la ricezione di informazioni sull'attività del malware da parte di Microsoft Active Protection Service dai dispositivi gestiti. Queste informazioni vengono usate per migliorare il servizio in futuro.
-   **Richiedi conferma all'utente prima dell'invio di campioni**: determina se i file potenzialmente dannosi che potrebbero richiedere ulteriore analisi vengono inviati automaticamente a Microsoft.
-   **Ora di esecuzione di un'analisi veloce giornaliera** - Consente di pianificare un'analisi veloce che viene eseguita giornalmente all'ora selezionata.
-   **Tipo di analisi di sistema da eseguire**: consente di specificare il livello di analisi implementato quando si pianifica un'analisi del sistema.
-   **Rileva applicazioni potenzialmente indesiderate**: scegliere il livello di protezione quando Windows rileva applicazioni potenzialmente indesiderate:
        - **Bloccato**
        - **Modalità di controllo** Per altre informazioni sulle app potenzialmente indesiderate, vedere [questo argomento](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
-   **Azioni per le minacce malware rilevate**: abilitare questa opzione per specificare le azioni che Defender esegue a seconda del livello di minaccia rilevato (Basso, Moderato, Alto o Grave). Le azioni che è possibile eseguire sono:
    -   **Pulisci**
    -   **Quarantena**
    -   **Rimuovi**
    -   **Consentito**
    -   **Definito dall'utente**
    -   **Bloccato**



### <a name="windows-defender-antivirus-exclusions"></a>Esclusioni di Windows Defender Antivirus

-   **File e cartelle da escludere dalle analisi e dalla protezione in tempo reale** - Aggiunge uno o più file e cartelle come **C:\Percorso** o **%ProgramFiles%\Percorso\nomefile.exe** all'elenco delle esclusioni. Questi file e cartelle non sono inclusi nelle analisi in tempo reale o pianificate.
-   **Estensioni di file da escludere dalle analisi e dalla protezione in tempo reale** - Aggiunge una o più estensioni di file come **.jpg** o **.txt** all'elenco delle esclusioni. I file con queste estensioni non sono inclusi nelle analisi in tempo reale o pianificate.
-   **Processi da escludere dalle analisi e dalla protezione in tempo reale** - Aggiunge uno o più processi del tipo **.exe**, **. com** o **. scr** all'elenco delle esclusioni. Questi processi non sono inclusi nelle analisi in tempo reale o nelle analisi pianificate.


## <a name="network-proxy"></a>Proxy di rete

-   **Rileva automaticamente impostazioni proxy**: se questa opzione è attivata il dispositivo cerca il percorso di uno script PAC.
-   **Usa lo script proxy**: selezionare questa opzione se si vuole specificare un percorso a uno script PAC per configurare il server proxy.
    -   **URL dell'indirizzo dello script di installazione**: immettere l'URL di uno script PAC che si vuole usare per configurare il server proxy.
-   **Usa il server proxy manuale**: selezionare questa opzione se si vogliono specificare manualmente le informazioni del server proxy.
    -   **Indirizzo**: immettere il nome o l'indirizzo IP del server proxy.
    -   **Numero porta**: immettere il numero della porta del server proxy.
    -   **Eccezione del proxy**: immettere gli URL che non devono usare il server proxy. Per separare ogni elemento, usare un punto e virgola.
    -   **Ignora il server proxy per l'indirizzo locale**: abilitare questa opzione se non si vuole usare il server proxy per gli indirizzi locali della rete Intranet.


## <a name="windows-spotlight"></a>Contenuti in evidenza di Windows


- **Contenuti in evidenza di Windows**: usare questa impostazione per bloccare tutte le funzionalità di Contenuti in evidenza di Windows nei dispositivi Windows 10. Se si blocca questa impostazione, le impostazioni seguenti non sono disponibili.
    - **Windows Spotlight nella schermata di blocco**: blocca la visualizzazione di Contenuti in evidenza di Windows nella schermata di blocco del dispositivo.
    - **Suggerimenti di terze parti in Windows Spotlight**: blocca i suggerimenti relativi a contenuti di terzi in Contenuti in evidenza di Windows.
    - **Funzionalità consumer**: consente di bloccare le funzionalità consumer, ad esempio i suggerimenti per il menu Start e le notifiche di appartenenza.
    - **Suggerimenti di Windows**: consente di bloccare la visualizzazione dei suggerimenti popup in Windows.
    - **Centro notifiche di Windows Spotlight**: blocca la visualizzazione di suggerimenti di Contenuti in evidenza di Windows (quali nuove app o contenuti di protezione) nel Centro notifiche di Windows.
    - **Personalizzazione di Windows Spotlight**: impedisce a Contenuti in evidenza di Windows la personalizzazione dei risultati a seconda dell'uso di un dispositivo.
    - **Esperienza di Configurazione e personalizzazione di Windows**: blocca l'Esperienza di Configurazione e personalizzazione di Windows, che visualizza informazioni su funzionalità nuove o aggiornate.


## <a name="projection"></a>Proiezione

- **Input degli utenti da ricevitori di schermo wireless**: blocca l'input degli utenti da ricevitori di schermo wireless.
- **Proiezione per questo computer**: blocca l'individuazione della proiezione di questo computer da parte di altri dispositivi.
- **Richiedi il PIN per l'associazione**: richiede un PIN durante la connessione a un dispositivo di proiezione.

## <a name="cloud-printer"></a>Stampante cloud

- **URL di individuazione stampanti**: endpoint per l'individuazione delle stampanti nel cloud.
- **URL dell'autorità per l'accesso alle stampanti**: endpoint di autenticazione per l'acquisizione di token OAuth.
- **GUID dell'app client nativa di Azure**: GUID che identifica l'applicazione client autorizzata a recuperare token OAuth da OAuthAuthority.
- **URI della risorsa del servizio di stampa**: URI della risorsa OAuth per il servizio di stampa come configurato nel portale di Azure.
- **Numero massimo di stampanti da sottoporre a query (solo dispositivi mobili)**: numero massimo di stampanti da sottoporre a query da un endpoint di individuazione.
- **URI della risorsa del servizio di individuazione**: URI della risorsa OAuth per il servizio di individuazione delle stampanti come configurato nel portale di Azure.

## <a name="reporting-and-telemetry"></a>Creazione di report e telemetria

- **Condividi i dati di utilizzo**: selezionare il livello di invio dei dati diagnostici.
- **Server proxy di telemetria**

  Specificare il nome di dominio completo (FQDN) o l'indirizzo IP di un server proxy per l'inoltro delle richieste Esperienze utente connesse e telemetria, tramite una connessione Secure Sockets Layer (SSL). Il formato di questa impostazione è *server*:*porta*. In caso di errore del proxy denominato oppure se non è specificato alcun proxy quando questo criterio è abilitato, i dati Esperienze utente connesse e telemetria non vengono trasmessi e rimangono nel dispositivo locale.

   Formati di esempio:

   IPv4: 192.246.246.106:100<br>
 IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100<br> FQDN: www.contoso.com:345

## <a name="messaging"></a>Messaggistica

- **Sincronizzazione di messaggi (solo dispositivi mobili)**: disabilitare i messaggi su qualsiasi dispositivo e il backup e il ripristino di SMS.
- **MMS (solo dispositivi mobili)** - disabilitare la funzionalità di invio/ricezione di MMS nel dispositivo.
- **RCS (solo dispositivi mobili)** - disabilitare la funzionalità di invio/ricezione di RCS (Rich Communication Services) nel dispositivo.












