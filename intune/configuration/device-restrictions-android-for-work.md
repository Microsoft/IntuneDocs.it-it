---
title: Impostazioni dei dispositivi Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Nei dispositivi Android Enterprise o Android for Work limitare le impostazioni del dispositivo, tra cui copia e incolla, visualizzazione delle notifiche, autorizzazioni delle app, condivisione dei dati, lunghezza della password, errori di accesso, uso dell'impronta digitale per sbloccare, riutilizzo delle password e abilitazione della condivisione dei contatti di lavoro con Bluetooth. Configurare i dispositivi come chiosco multimediale dedicato del dispositivo per eseguire una sola app o più App.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a58eefffac670a12fc1d1a065534b4c1a4505426
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734947"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi Android Enterprise. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, eseguire app in dispositivi dedicati, controllare le impostazioni di sicurezza e altro ancora.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Solo proprietario del dispositivo

### <a name="general-settings"></a>Impostazioni generali

- **Acquisizione schermo**: scegliere **Blocca** per impedire screenshot o acquisizioni di schermate nel dispositivo. Impedisce anche la visualizzazione del contenuto nei dispositivi di visualizzazione privi di output video protetto. **Non configurata** consente all'utente di acquisire il contenuto dello schermo come immagine.
- **Fotocamera**: scegliere **Blocca** per impedire l'accesso alla fotocamera nel dispositivo. **Non necessaria** consente l'accesso alla fotocamera del dispositivo.
- **Criteri di autorizzazione predefiniti**: questa impostazione definisce i criteri di autorizzazione predefiniti delle richieste delle autorizzazioni di runtime. I valori possibili includono:
  - **Impostazione predefinita dispositivo**: usare l'impostazione predefinita del dispositivo.
  - **Messaggio di richiesta**: all'utente viene richiesto di approvare l'autorizzazione.
  - **Concedi automaticamente**: le autorizzazioni vengono concesse automaticamente.
  - **Nega automaticamente**: le autorizzazioni vengono negate automaticamente.
- **Modifiche a data e ora**: scegliere **Blocca** per impedire agli utenti di impostare manualmente la data e ora. **Non configurata** consente agli utenti di impostare data e ora nel dispositivo.
- **Modifiche al volume**: scegliere **Blocca** per impedire agli utenti di modificare il volume del dispositivo. **Non configurata** consente l'uso delle impostazioni del volume nel dispositivo.
- **Ripristino delle impostazioni predefinite**: scegliere **Blocca** per impedire agli utenti di usare l'opzione per il ripristino delle impostazioni predefinite nel dispositivo. **Non configurata** consente agli utenti di usare questa impostazione nel dispositivo.
- **Modalità provvisoria**: scegliere **Blocca** per impedire agli utenti di riavviare il dispositivo in modalità provvisoria. **Non configurata** consente agli utenti di riavviare il dispositivo in modalità sicura.
- **Barra di stato**: scegliere **Blocca** per impedire l'accesso alla barra di stato, incluse le notifiche e le impostazioni rapide. **Non configurata** consente agli utenti di accedere alla barra di stato.
- **Servizi per dati in roaming**: scegliere **Blocca** per impedire il roaming dei dati nella rete cellulare. **Non configurata** consente il roaming dati quando il dispositivo si trova in una rete cellulare.
- **Modifiche alle impostazioni Wi-Fi**: scegliere **Blocca** per impedire agli utenti di modificare le impostazioni Wi-Fi create dal proprietario del dispositivo. Gli utenti possono creare configurazioni Wi-Fi personalizzate. **Non configurata** consente agli utenti di modificare le impostazioni Wi-Fi nel dispositivo.
- **Configurazione del punto di accesso Wi-Fi**: scegliere **Blocca** per impedire agli utenti di creare o modificare configurazioni Wi-Fi. **Non configurata** consente agli utenti di modificare le impostazioni Wi-Fi nel dispositivo.
- **Configurazione Bluetooth**: scegliere **Blocca** per impedire agli utenti di configurare Bluetooth nel dispositivo. **Non configurata** consente di usare Bluetooth nel dispositivo.
- **Tethering e accesso a hotspot**: scegliere **Blocca** per impedire il tethering e l'accesso a hotspot portatili. **Non configurata** consente il tethering e l'accesso a hotspot portatili.
- **Archiviazione USB**: scegliere **Consenti** per consentire l'accesso all'archiviazione USB nel dispositivo. **Non configurata** impedisce l'accesso all'archiviazione USB.
- **Trasferimento di file su USB**: scegliere **Blocca** per impedire il trasferimento di file tramite USB. **Non configurata** consente il trasferimento di file.
- **Supporti esterni**: scegliere **Blocca** per impedire l'uso o la connessione di qualsiasi supporto esterno nel dispositivo. **Non configurata** consente supporti esterni nel dispositivo.
- **Trasmetti dati con NFC**: scegliere **Blocca** per impedire l'uso della tecnologia NFC (Near Field Communication) per la trasmissione di dati dalle app. **Non configurata** consente l'uso di NFC per condividere dati tra i dispositivi.
- **Funzionalità di debug**: scegliere **Consenti** per consentire agli utenti di usare le funzionalità di debug nel dispositivo. **Non configurata** impedisce agli utenti di usare le funzionalità di debug nel dispositivo.
- **Regolazione del microfono**: scegliere **Blocca** per impedire agli utenti di riattivare il microfono e regolare il volume del microfono. **Non configurata** consente all'utente di usare il microfono nel dispositivo e regolarne il volume.
- **Indirizzi di posta elettronica per la protezione dal ripristino delle impostazioni predefinite**: scegliere **Indirizzi di posta elettronica dell'account Google**. Immettere gli indirizzi di posta elettronica degli amministratori dei dispositivi che possono sbloccare il dispositivo dopo la cancellazione. Assicurarsi di separare gli indirizzi di posta elettronica con punti e virgola, ad esempio `admin1@gmail.com;admin2@gmail.com`. Se non viene immesso un indirizzo di posta elettronica, chiunque può sbloccare il dispositivo dopo il ripristino delle impostazioni predefinite. Questi messaggi di posta elettronica si applicano solo quando viene eseguito un ripristino delle impostazioni predefinite dell'utente, ad esempio l'esecuzione di un ripristino delle impostazioni predefinite tramite il menu ripristino.
- **Rete di emergenza**: scegliere **Abilita** per consentire agli utenti di attivare la funzionalità di rete di emergenza. Se non è possibile creare una connessione di rete in fase di avvio del dispositivo, la rete di emergenza richiede all'utente di connettersi temporaneamente a una rete per aggiornare i criteri del dispositivo. Dopo aver applicato i criteri, la rete temporanea viene dimenticata e viene ripreso l'avvio del dispositivo. Questa funzionalità consente di connettere i dispositivi a una rete se:
  - Non è disponibile una rete idonea nei criteri più recenti.
  - Il dispositivo viene avviato in un'app in modalità di attività di blocco.
  - L'utente non è in grado di raggiungere le impostazioni del dispositivo.

  **Non configurata** impedisce agli utenti di attivare la funzionalità di rete di emergenza nel dispositivo.

- **Aggiornamento del sistema**: scegliere un'opzione per definire la modalità di gestione degli aggiornamenti in modalità wireless da parte del dispositivo:
  - **Impostazione predefinita dispositivo**: usare l'impostazione predefinita del dispositivo.
  - **Automatico**: gli aggiornamenti vengono installati automaticamente senza l'intervento dell'utente. L'impostazione del criterio consente di installare immediatamente eventuali aggiornamenti in sospeso.
  - **Posposto**: gli aggiornamenti vengono rimandati di 30 giorni. Al termine dei 30 giorni, Android chiede all'utente di installare l'aggiornamento. Ai produttori di dispositivi e ai gestori telefonici è consentito impedire il posticipo degli aggiornamenti della sicurezza. Un aggiornamento posticipato viene indicato all'utente da una notifica di sistema nel dispositivo. 
  - **Finestra di manutenzione**: installa automaticamente gli aggiornamenti in una finestra di manutenzione giornaliera impostata in Intune. L'installazione viene tentata ogni giorno per 30 giorni e può non riuscire a causa di livelli di batteria o spazio insufficienti. Dopo 30 giorni, Android chiede all'utente di eseguire l'installazione. Questa finestra viene usata anche per installare gli aggiornamenti per le app di Play. Usare questa opzione per i dispositivi dedicati, ad esempio i chioschi multimediali, in quanto consente di aggiornare le app in primo piano dei dispositivi dedicati per app singola.

- **Finestre di notifica**: se l'opzione è impostata su **Disabilita**, le notifiche, tra cui avvisi popup, chiamate in ingresso, chiamate in uscita, avvisi di sistema ed errori di sistema, non vengono visualizzate nel dispositivo. Se è impostata su **Non configurata**, vengono usate le impostazioni predefinite del sistema operativo, che potrebbero mostrare le notifiche.
- **Ignora suggerimenti al primo utilizzo**: scegliere **Abilita** per nascondere o ignorare i suggerimenti delle app che richiedono di eseguire le esercitazioni o leggere i suggerimenti iniziali quando viene avviata l'app. Se l'opzione è impostata su **Non configurata**, vengono usate le impostazioni predefinite del sistema operativo, che potrebbero mostrare questi suggerimenti quando viene avviata l'app.

### <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

- **Analisi delle minacce nelle app**: **Richiedi** (impostazione predefinita) consente a Google Play Protect di analizzare le app prima e dopo la loro installazione. Se rileva una minaccia, può richiedere all'utente di rimuovere l'app dal dispositivo. **Non configurata** non attivare o esegue Google Play Protect per analizzare le app.

### <a name="dedicated-device-settings"></a>Impostazioni dedicate del dispositivo

Utilizzare queste impostazioni per configurare un'esperienza di tipo chiosco multimediale nei dispositivi dedicati. È possibile configurare un dispositivo per eseguire una sola app o per eseguire molte app. Quando un dispositivo è impostato in modalità tutto schermo, sono disponibili solo le app aggiunte. Queste impostazioni si applicano ai dispositivi dedicati Android Enterprise. Non si applicano ai dispositivi Android Enterprise completamente gestiti.

**Modalità tutto schermo**: scegliere se il dispositivo eseguirà una sola app o più app.

- **App singola**: gli utenti possono accedere solo a un'app singola nel dispositivo. All'avvio del dispositivo viene avviata solo l'app specifica. Gli utenti non possono aprire nuove app o modificare l'app in esecuzione.

  - **Selezionare un'app gestita**: selezionare l'app Google Play gestita nell'elenco.

    Se l'elenco non include alcuna app, [aggiungere alcune app Android](../apps/apps-add-android-for-work.md) al dispositivo. Assicurarsi di [assegnare l'app al gruppo di dispositivi creato per i dispositivi dedicati](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > Quando si usa la modalità tutto schermo a app singola, le app del comparatore/telefono potrebbero non funzionare correttamente. 
  
- **Più app**: gli utenti possono accedere a un set di app limitato nel dispositivo. All'avvio del dispositivo vengono avviate solio le app aggiunte. È anche possibile aggiungere alcuni collegamenti Web che gli utenti possono aprire. Quando viene applicato il criterio, gli utenti visualizzano le icone delle app consentite nella schermata iniziale.

  > [!IMPORTANT]
  > Per i dispositivi dedicati con più app, l'[app di schermata iniziale gestita](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) da Google Play **deve essere**:
  >   - [Aggiunta come app client](../apps/apps-add-android-for-work.md) in Intune
  >   - [Assegnata al gruppo di dispositivi](../apps/apps-deploy.md) creato per i dispositivi dedicati
  > 
  > Non è richiesto che l'app di **schermata iniziale gestita** sia inclusa nel profilo di configurazione, ma è necessario che venga aggiunta come app client. Quando l'app di **schermata iniziale gestita** viene aggiunta come app client, qualsiasi altra app aggiunta nel profilo di configurazione viene visualizzata come icona nell'app di **schermata iniziale gestita**. 
  >
  > Quando si usa la modalità tutto schermo per più app, le app del servizio di connessione/telefono potrebbero non funzionare correttamente. 

  - **Aggiungi**: selezionare le app dall'elenco.

    Se l'app di **schermata iniziale gestita** non è inclusa nell'elenco, [aggiungerla da Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Assicurarsi di [assegnare l'app](../apps/apps-deploy.md) al gruppo di dispositivi creato per i dispositivi dedicati.

    È anche possibile aggiungere al dispositivo altre [app Android](../apps/apps-add-android-for-work.md) e [app Web](../apps/web-app.md) create dall'organizzazione. Assicurarsi di [assegnare l'app al gruppo di dispositivi creato per i dispositivi dedicati](../apps/apps-deploy.md).

  - **Pulsante Home virtuale**: un pulsante del tasto softkey che restituisce gli utenti alla schermata iniziale gestita in modo che gli utenti possano passare tra le app. Le opzioni disponibili sono:

    - **Non configurato** (impostazione predefinita): non viene visualizzato un pulsante Home. Gli utenti devono usare il pulsante indietro per spostarsi tra le app.
    - **Scorri verso l'alto**: un pulsante Home viene visualizzato quando un utente scorre il dispositivo.
    - **Floating**: Mostra un pulsante Home permanente e mobile sul dispositivo.

  - **Esci dalla modalità tutto schermo**: scegliere **Abilita** per consentire agli amministratori di sospendere temporaneamente la modalità tutto schermo per aggiornare il dispositivo. Per utilizzare questa funzionalità, l'amministratore esegue le operazioni seguenti:
  
    1. Continua a selezionare il pulsante Indietro fino a quando non viene visualizzato il pulsante **Exit kiosk** (Esci da modalità tutto schermo). 
    2. Seleziona il pulsante **Exit kiosk** (Esci da modalità tutto schermo) e immette il PIN per **Codice di uscita dalla modalità tutto schermo**.
    3. Al termine, selezionare l'app **Home Screen gestita** . Questo passaggio blocca di nuovo il dispositivo in modalità tutto schermo con più app.

      Se impostato su **non configurato**, gli amministratori non possono sospendere la modalità tutto schermo. Se l'amministratore continua a selezionare il pulsante Indietro e seleziona il pulsante **Exit kiosk** (Esci da modalità tutto schermo), un messaggio segnala che è richiesto un passcode.

    - **Codice di uscita dalla modalità tutto schermo**: immettere un PIN numerico da 4-6 cifre. L'amministratore usa questo PIN per sospendere temporaneamente la modalità tutto schermo.

  - **Imposta uno sfondo personalizzato per l'URL**: immettere un URL per personalizzare la schermata di sfondo nel dispositivo dedicato.

    > [!NOTE]
    > Nella maggior parte dei casi, è consigliabile iniziare almeno con immagini delle dimensioni seguenti:
    >
    > - Telefono: 1920 x 1080 pixel
    > - Tablet: 1920 x 1080 pixel
    >
    > Per ottenere la migliore esperienza e nitidezza dei dettagli, è consigliabile procedere alla creazione di asset per ogni immagine del dispositivo in base alle specifiche di visualizzazione.
    >
    > Gli schermi moderni hanno maggiori densità di pixel e consentono di visualizzare immagini con definizione equivalente a 2K/4K.

  - **Configurazione Wi-Fi**: **Abilita** Mostra il controllo Wi-Fi nella schermata iniziale gestita e consente agli utenti finali di connettere il dispositivo a diverse reti Wi-Fi. L’abilitazione di questa funzionalità attiva anche la posizione del dispositivo. **Non configurato** (impostazione predefinita) non Visualizza il controllo Wi-Fi nella schermata iniziale gestita. Impedisce agli utenti di connettersi alle reti Wi-Fi usando la schermata iniziale gestita.

  - **Configurazione Bluetooth**: **Abilita** Mostra il controllo Bluetooth nella schermata iniziale gestita e consente agli utenti finali di associare i dispositivi tramite Bluetooth. L’abilitazione di questa funzionalità attiva anche la posizione del dispositivo. **Non configurato** (impostazione predefinita) non Visualizza il controllo Bluetooth nella schermata iniziale gestita. Impedisce agli utenti di configurare i dispositivi Bluetooth e di associazione usando la schermata iniziale gestita.

  - **Torcia Access**: **Abilita** Mostra il controllo torcia sulla schermata iniziale gestita e consente agli utenti finali di attivare o disattivare la torcia. **Non configurato** (impostazione predefinita) non Visualizza il controllo torcia nella schermata iniziale gestita. Impedisce agli utenti di usare la torcia durante l'uso della schermata iniziale gestita.

  - **Controllo volume multimediale**: **Abilita** Mostra il controllo volume multimediale nella schermata iniziale gestita e consente agli utenti finali di modificare il volume multimediale del dispositivo usando un dispositivo di scorrimento. **Non configurato** (impostazione predefinita) non Visualizza il controllo volume multimediale nella schermata iniziale gestita. Impedisce agli utenti di modificare il volume multimediale del dispositivo durante l'uso della schermata iniziale gestita, a meno che i pulsanti hardware non lo supportino. 

  - **Modalità screen saver**: **Abilita** Mostra uno screensaver nella schermata iniziale gestita quando il dispositivo è bloccato o si verifica un timeout. **Non configurato** (impostazione predefinita) non mostra uno screen saver nella schermata iniziale gestita.

    Se abilitata, configurare anche:

    - **Imposta immagine screen saver personalizzata**: immettere l'URL di un'immagine personalizzata. Ad esempio, immettere:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.html`

      Se non si immette un URL, viene utilizzata l'immagine predefinita del dispositivo, se è presente un'immagine predefinita.

    - **Numero di secondi durante i quali il dispositivo visualizza screen saver prima**della disattivazione dello schermo: scegliere per quanto tempo il dispositivo Visualizza lo screensaver. Immettere un valore compreso tra 0-9999999 secondi. Il valore predefinito è `0` secondi. Quando viene lasciato vuoto o impostato su zero (`0`), il screen saver è attivo fino a quando un utente interagisce con il dispositivo.
    - **Numero di secondi di inattività del dispositivo prima di visualizzare screen saver**: scegliere per quanto tempo il dispositivo è inattivo prima di visualizzare lo screensaver. Immettere un valore compreso tra 1-9999999 secondi. Il valore predefinito è `30` secondi. È necessario immettere un numero maggiore di zero (`0`).
    - **Rileva supporto prima di iniziare screen saver**: **Abilita** (impostazione predefinita) non Mostra l'screen saver se l'audio o il video è in riproduzione sul dispositivo. **Non configurata** mostra il screen saver, anche se la riproduzione audio o video viene eseguita.

### <a name="device-password-settings"></a>Impostazioni della password del dispositivo mobile

- **Disabilita la schermata di blocco**: scegliere **Disabilita** per impedire agli utenti di usare la funzionalità della schermata di blocco di protezione della tastiera nel dispositivo. **Non configurata** consente all'utente di usare le funzionalità di protezione della tastiera.
- **Funzionalità disabilitate della schermata di blocco**: se la protezione della tastiera è abilitata sul dispositivo, scegliere quali funzionalità disabilitare. Ad esempio, se è selezionata l'opzione **Secure camera** (Fotocamera sicura), la funzionalità fotocamera è disabilitata nel dispositivo. Le funzionalità non selezionate sono abilitate nel dispositivo.

  Queste funzionalità sono disponibili per gli utenti quando il dispositivo è bloccato. Gli utenti non potranno visualizzare o accedere alle funzionalità che sono selezionate.

- **Tipo di password richiesto**: definire il tipo di password richiesta per il dispositivo. Le opzioni disponibili sono:
  - **Impostazione predefinita dispositivo**
  - **Password obbligatoria, nessuna restrizione**
  - **Biometria vulnerabile**: [biometrica complessa rispetto alla vulnerabile](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (apre il sito Web di Android)
  - **Numerica**: la password contiene solo numeri, ad esempio `123456789`. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
  - **Complessa numerica**: i numeri consecutivi o ripetuti (ad esempio, "1111" o "1234") non sono consentiti. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
  - **Alfabetica**: è obbligatorio utilizzare le lettere dell'alfabeto. Numeri e simboli non sono richiesti. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
  - **Alfanumerica**: include lettere maiuscole, lettere minuscole e caratteri numerici. Immettere la **lunghezza minima password** che deve essere compresa tra 4 e 16 caratteri.
  - **Alfanumerico con simboli**: include lettere maiuscole, lettere minuscole, caratteri numerici, segni di punteggiatura e simboli. Specificare anche:

    - **Lunghezza minima password**: immettere la lunghezza minima per la password che deve essere compresa tra da 4 e 16 caratteri.
    - **Numero di caratteri richiesti**: immettere il numero di caratteri deve contenere la password, compreso tra 0 e 16 caratteri.
    - **Numero di caratteri minuscoli obbligatori**: immettere il numero di caratteri minuscoli compreso tra 0 e 16 che la password deve contenere.
    - **Numero di caratteri maiuscoli obbligatori**: immettere il numero di caratteri maiuscoli compreso tra 0 e 16 che la password deve contenere.
    - **Numero di caratteri diversi da lettere obbligatori**: immettere il numero di caratteri (diversi dalle lettere dell'alfabeto) compreso tra 0 e 16 caratteri che la password deve contenere.
    - **Numero di caratteri numerici obbligatori**: immettere il numero di caratteri numerici (`1`, `2`, `3` e così via) compreso tra 0 e 16 caratteri che la password deve contenere.
    - **Numero di caratteri di tipo simbolo obbligatori**: immettere il numero di caratteri di tipo simbolo (`&`, `#`, `%` e così via) compreso tra 0 e 16 caratteri che la password deve contenere.

- **Numero di giorni rimanenti prima della scadenza della password**: immettere il numero di giorni che devono trascorrere tra 1 e 365 prima che sia necessario modificare la password del dispositivo. Ad esempio, per modificare la password dopo 60 giorni, immettere `60`. Quando la password scade, agli utenti viene chiesto di creare una nuova password.
- **Numero di password obbligatorie prima che un utente possa riutilizzare una password**: immettere il numero di password recenti tra 1 e 24 che non può essere riutilizzato. Usare questa impostazione per impedire all'utente di creare password già usate in precedenza.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: immettere il numero tra 4 e 11 di errori di accesso consentiti prima che i dati vengano cancellati dal dispositivo.

### <a name="power-settings"></a>Impostazioni di risparmio energia

- **Time to lock screen** (Tempo per schermata di blocco): impostare la quantità di tempo di inattività necessaria affinché il dispositivo venga bloccato.
- **Screen on while device plugged in** (Schermata attiva con dispositivo alimentato): scegliere i tipi di alimentazione che mantengono attiva la schermata del dispositivo alimentato.

### <a name="users-and-accounts-settings"></a>Impostazioni di utenti e account

- **Aggiungi nuovi utenti**: scegliere **Blocca** per impedire agli utenti di aggiungere nuovi utenti. Ogni utente dispone di uno spazio personale nel dispositivo per schermate iniziali, account, app e impostazioni personalizzati. **Non configurata** consente agli utenti di aggiungere altri utenti nel dispositivo.
- **Rimozione degli utenti**: scegliere **Blocca** per impedire agli utenti di rimuovere gli utenti. **Non configurata** consente agli utenti di rimuovere altri utenti dal dispositivo.
- **Modifiche all'account**: scegliere **Blocca** per impedire agli utenti di modificare gli account. **Non configurata** consente agli utenti di aggiornare gli account utente nel dispositivo.

  > [!NOTE]
  > Questa impostazione non è rispettata nei dispositivi proprietari del dispositivo (completamente gestiti). Se si configura questa impostazione, l'impostazione viene ignorata e non ha alcun effetto.

### <a name="applications"></a>Applicazioni

- **Consenti l'installazione da origini sconosciute**: scegliere **Consenti** in modo che gli utenti possano attivare **Origini sconosciute**. Questa impostazione consente di installare app da origini sconosciute, tra cui origini diverse da Google Play Store. **Non configurata** impedisce agli utenti di attivare **Origini sconosciute**.
- **Consenti l'accesso a tutte le app in Google Play Store**: se impostata su **Consenti**, gli utenti possono accedere a tutte le app in Google Play Store. Non possono accedere alle app bloccate dall'amministratore in [App client](../apps/apps-add-android-for-work.md). **Non configurata** impone agli utenti di accedere solo alle app che l'amministratore rende disponibile in Google Play Store o le app richieste in [App client](../apps/apps-add-android-for-work.md).
- **Aggiornamenti automatici delle app**: scegliere se gli aggiornamenti automatici vengono installati. Le opzioni disponibili sono:
  - **Non configurato**
  - **Scelta utente**
  - **Mai**
  - **Solo Wi-Fi**
  - **Sempre**

### <a name="connectivity"></a>Connettività

- **Always-on VPN** (VPN sempre attiva): scegliere **Abilita** per impostare un client VPN in modo che si connetta e riconnetta automaticamente alla VPN. Le connessioni VPN sempre attive rimangono connesse o si connettono immediatamente quando l'utente blocca il dispositivo, il dispositivo viene riavviato o la rete wireless viene modificata. 

  Scegliere **Non configurata** per disabilitare la VPN sempre attiva per tutti i client VPN.

  > [!IMPORTANT]
  > Assicurarsi di distribuire una sola policy VPN sempre attiva in un singolo dispositivo. La distribuzione di più policy VPN sempre attiva in un singolo dispositivo non è supportata.

- **VPN client** (Client VPN): scegliere un client VPN che supporta Always On. Le opzioni disponibili sono:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizzato
    - **ID pacchetto**: immettere l'ID pacchetto dell'app in Google Play Store. Se ad esempio l'URL per l'app in Play Store è `https://play.google.com/store/details?id=com.contosovpn.android.prod`, l'ID pacchetto è `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Il client VPN scelto deve essere installato nel dispositivo e deve supportare la VPN per app nei profili di lavoro. In caso contrario si verificherà un errore. 
  > - È necessario approvare l'app client VPN in **Google Play Store gestito**, sincronizzare l'app con Intune e distribuire l'app nel dispositivo. Al termine di queste operazioni, l'app viene installata nel profilo di lavoro dell'utente.
  > - Possono esistere problemi noti quando si usa una VPN per app con F5 Access per Android 3.0.4. Per altre informazioni, vedere le [note sulla versione di F5 per F5 Access per Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Lockdown mode** (Modalità di blocco): scegliere **Abilita** per forzare tutto il traffico di rete a usare il tunnel VPN. Se non viene stabilita una connessione alla VPN, il dispositivo non avrà accesso alla rete.

  Scegliere **Non configurata** per consentire al traffico di passare attraverso il tunnel VPN o la rete per dispositivi mobili.

## <a name="work-profile-only"></a>Solo profilo di lavoro 

### <a name="work-profile-settings"></a>Impostazioni del profilo di lavoro

#### <a name="general"></a>Generale

- **Copia e incolla tra il profilo di lavoro e il profilo personale**: scegliere **Blocca** per impedire le operazioni di copia e incolla tra app aziendali e personali. **Non configurata** consente agli utenti di condividere i dati tramite copia e incolla con le app nel profilo personale 
- **Condivisione dei dati tra i profili di lavoro e personali**: scegliere se le app nel profilo di lavoro possono condividere dati con le app nel profilo personale. Ad esempio, è possibile controllare le azioni di condivisione all'interno delle applicazioni, come l'opzione **Condividi** nell'app browser Chrome. Questa impostazione non si applica al comportamento di copia/incolla degli Appunti. Opzioni per la condivisione:
  - **Restrizioni predefinite per la condivisione**: comportamento di condivisione predefinito del dispositivo che varia in base alla versione di Android. Per impostazione predefinita, la condivisione dal profilo personale al profilo di lavoro è consentita. Per impostazione predefinita, la condivisione dal profilo di lavoro al profilo personale è bloccata. Questa impostazione impedisce la condivisione di dati dal profilo di lavoro al profilo personale. Nei dispositivi che eseguono la versione 6.0 e successive Google non blocca la condivisione dal profilo personale al profilo di lavoro.
  - **Le app nel profilo di lavoro possono gestire una richiesta di condivisione dal profilo personale**: questa opzione abilita la funzionalità Android predefinita che consente la condivisione dal profilo personale al profilo di lavoro. Quando questa opzione è abilitata, una richiesta di condivisione da un'app nel profilo personale supporta la condivisione con app nel profilo di lavoro. Questa impostazione rappresenta il comportamento predefinito per i dispositivi Android che eseguono versioni precedenti alla 6.0.
  - **Consenti la condivisione tra limiti**: abilita la condivisione tra i limiti del profilo di lavoro in entrambe le direzioni. Quando si seleziona questa impostazione, le app nel profilo di lavoro possono condividere dati con app senza badge nel profilo personale. Questa impostazione consente la condivisione tra le app gestite nel profilo di lavoro e le app nella parte non gestita del dispositivo. Usare quindi questa impostazione con cautela.

- **Notifiche del profilo di lavoro durante il blocco del dispositivo**: controlla se le app del profilo di lavoro possono visualizzare dati nelle notifiche quando il dispositivo è bloccato. **Blocca** impedisce la visualizzazione dei dati. **Non configurata** consente di visualizzare i dati.
- **Autorizzazioni delle app predefinite**: imposta i criteri di autorizzazione predefiniti per tutte le app del profilo di lavoro. A partire da Android 6, all'utente viene richiesto di concedere alcune autorizzazioni richieste dalle app, all'avvio dell'app. Questa impostazione dei criteri consente di decidere se richiedere agli utenti di concedere autorizzazioni per tutte le app nel profilo di lavoro. Ad esempio, si può assegnare al profilo di lavoro un'app che richiede l'accesso alla posizione. In genere, un'app di questo tipo richiede all'utente di concedere o negare l'accesso alla posizione all'app. Usare questo criterio per concedere o negare automaticamente le autorizzazioni senza richiesta oppure per lasciar decidere all'utente finale. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Messaggio di richiesta**
  - **Concedi automaticamente**
  - **Nega automaticamente**

  È anche possibile usare un criterio di configurazione dell'app per concedere le autorizzazioni per le singole app (**App client** > **Criteri di configurazione dell'app**).

- **Aggiungi e rimuovi account**: scegliere **Blocca** per impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro. Ad esempio, quando si distribuisce l'app Gmail in un profilo di lavoro Android, è possibile impedire agli utenti finali di aggiungere o rimuovere account in questo profilo di lavoro. **Non configurata** consente di aggiungere account nel profilo di lavoro.  

- **Condivisione dei contatti tramite Bluetooth**: abilita l'accesso ai contatti di lavoro da un altro dispositivo, ad esempio un'automobile, che viene associato tramite Bluetooth. Per impostazione predefinita, questa impostazione non è configurata e i contatti dei profili di lavoro non sono visualizzati. Selezionare **Abilita** per consentire la condivisione e visualizzare i contatti dei profili di lavoro. Questa impostazione si applica ai dispositivi dei profili di lavoro Android in sistemi operativi Android 6.0 e versioni successive. L'abilitazione di questa impostazione può consentire a determinati dispositivi Bluetooth di memorizzare nella cache i contatti di lavoro al momento della prima connessione. Se si disabilita questo criterio dopo un'associazione/sincronizzazione iniziale, i contatti di lavoro potrebbero non essere rimossi da un dispositivo Bluetooth.

- **Acquisizione schermo**: scegliere **Blocca** per impedire screenshot o acquisizioni di schermate nel dispositivo nel profilo di lavoro. Impedisce anche la visualizzazione del contenuto nei dispositivi di visualizzazione privi di output video protetto. **Non configurata** consente l'acquisizione di screenshot.

- **Visualizzare l'ID chiamante del contatto di lavoro nel profilo personale**: se abilitata (**Non configurata**), i dettagli del chiamante del contatto di lavoro vengono visualizzati nel profilo personale. Se impostata su **Blocca**, il numero del chiamante del contatto di lavoro non viene visualizzato nel profilo personale. Si applica ai sistemi operativi Android 6.0 e versioni successive.

- **Cerca contatti di lavoro dal profilo personale**: scegliere **Blocca** per impedire agli utenti di cercare i contatti di lavoro nelle app nel profilo personale. **Non necessario** consente di cercare i contatti di lavoro nel profilo personale.

- **Fotocamera**: scegliere **Blocca** per impedire l'accesso alla fotocamera nel dispositivo nel profilo di lavoro. Questa impostazione non interessa la fotocamera nel profilo personale. **Non necessario** consente l'accesso alla fotocamera nel profilo di lavoro.

- **Consenti i widget dalle app del profilo di lavoro**: **Abilita** consente agli utenti finali di inserire i widget esposti dalle app nella schermata iniziale. L'impostazione **Non configurata** (predefinita) disabilita questa funzionalità.

  Ad esempio, Outlook viene installato nei profili di lavoro degli utenti. Quando l'impostazione è **abilitata**, gli utenti possono inserire il widget agenda nella schermata iniziale del dispositivo.

#### <a name="work-profile-password"></a>Password del profilo di lavoro

- **Richiedi la password del profilo di lavoro**: si applica ad Android 7.0 e versioni successive con il profilo di lavoro abilitato. Scegliere **Rendi obbligatorio** per immettere criteri di passcode validi solo per le app nel profilo di lavoro. Per impostazione predefinita, l'utente finale può usare i due PIN definiti separatamente oppure scegliere di combinarli nel PIN più complesso. **Non configurata** consente all'utente di usare le app di lavoro, senza immettere una password.
- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono avere (**4**-**16**).
- **Numero massimo di minuti di inattività fino al blocco del profilo di lavoro**: selezionare la quantità di tempo che deve trascorrere prima che il profilo di lavoro si blocchi. L'utente deve quindi immettere le credenziali per riottenere l'accesso.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che il profilo di lavoro venga cancellato dal dispositivo.
- **Scadenza password (giorni)** : immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**) .
- **Tipo di password richiesto**: selezionare il tipo di password che deve essere impostato nel dispositivo. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Richiesto**
  - **Almeno numerico**
  - **Complessa numerica**: i numeri consecutivi o ripetuti, ad esempio "1111" o "1234", non sono consentiti
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**
- **Impedisci il riutilizzo delle password precedenti**: immettere il numero di nuove password da usare prima che una password precedente possa essere usata di nuovo (da **1**-**24**).
- **Sblocco con impronta digitale**: scegliere **Blocca** per impedire agli utenti finali di usare lo scanner di impronta digitale del dispositivo per sbloccarlo. **Non configurata** consente agli utenti di sbloccare i dispositivi con un'impronta digitale nel profilo di lavoro.
- **Smart Lock e altri agenti di attendibilità**: scegliere **Blocca** per impedire a Smart Lock o altri agenti di attendibilità di modificare le impostazioni della schermata di blocco nei dispositivi compatibili. Questa funzionalità, nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se il dispositivo si trova in una posizione attendibile. Ad esempio, ignorare la password del profilo di lavoro quando il dispositivo è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. Usare questa impostazione per impedire agli utenti di configurare Smart Lock.

### <a name="device-password"></a>Password del dispositivo

Queste impostazioni per le password si applicano ai profili personali nei dispositivi che usano un profilo di lavoro.

- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono avere (**4**-**14**).
- **Numero massimo di minuti di inattività fino al blocco dello schermo**: selezionare il periodo di tempo che deve trascorrere prima che un dispositivo inattivo si blocchi automaticamente
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che i dati vengano cancellati dal dispositivo
- **Scadenza password (giorni)** : immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**)
- **Tipo di password richiesto**: selezionare il tipo di password che deve essere impostato nel dispositivo. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Richiesto**
  - **Almeno numerico**
  - **Complessa numerica**: i numeri consecutivi o ripetuti, ad esempio "1111" o "1234", non sono consentiti
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**
- **Impedisci il riutilizzo delle password precedenti**: immettere il numero di nuove password da usare prima che una password precedente possa essere usata di nuovo (da **1**-**24**).
- **Sblocco con impronta digitale**: scegliere **Blocca** per impedire all'utente finale di usare lo scanner di impronta digitale del dispositivo per sbloccarlo. **Non configurata** consente all'utente di sbloccare il dispositivo tramite impronta digitale.
- **Smart Lock e altri agenti di attendibilità**: scegliere **Blocca** per impedire a Smart Lock o altri agenti di attendibilità di modificare le impostazioni della schermata di blocco nei dispositivi compatibili. Questa funzionalità, nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se il dispositivo si trova in una posizione attendibile. Ad esempio, ignorare la password del profilo di lavoro quando il dispositivo è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. Usare questa impostazione per impedire agli utenti di configurare Smart Lock.

### <a name="system-security"></a>Protezione del sistema

- **Analisi delle minacce nelle app**: specificare **Rendi obbligatorio** per imporre l'abilitazione dell'impostazione **Verifica app** per i profili di lavoro e personali.

   > [!Note]
   > Questa impostazione funziona solo per i dispositivi Android O e versioni successive.

### <a name="connectivity"></a>Connettività

- **Always-on VPN** (VPN sempre attiva): scegliere **Abilita** per impostare un client VPN in modo che si connetta e riconnetta automaticamente alla VPN. Le connessioni VPN sempre attive rimangono connesse o si connettono immediatamente quando l'utente blocca il dispositivo, il dispositivo viene riavviato o la rete wireless viene modificata. 

  Scegliere **Non configurata** per disabilitare la VPN sempre attiva per tutti i client VPN.

  > [!IMPORTANT]
  > Assicurarsi di distribuire una sola policy VPN sempre attiva in un singolo dispositivo. La distribuzione di più policy VPN sempre attiva in un singolo dispositivo non è supportata.

- **VPN client** (Client VPN): scegliere un client VPN che supporta Always On. Le opzioni disponibili sono:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizzato
    - **ID pacchetto**: immettere l'ID pacchetto dell'app in Google Play Store. Se ad esempio l'URL per l'app in Play Store è `https://play.google.com/store/details?id=com.contosovpn.android.prod`, l'ID pacchetto è `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Il client VPN scelto deve essere installato nel dispositivo e deve supportare la VPN per app nei profili di lavoro. In caso contrario si verificherà un errore. 
  > - È necessario approvare l'app client VPN in **Google Play Store gestito**, sincronizzare l'app con Intune e distribuire l'app nel dispositivo. Al termine di queste operazioni, l'app viene installata nel profilo di lavoro dell'utente.
  > - Possono esistere problemi noti quando si usa una VPN per app con F5 Access per Android 3.0.4. Per altre informazioni, vedere le [note sulla versione di F5 per F5 Access per Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Lockdown mode** (Modalità di blocco): scegliere **Abilita** per forzare tutto il traffico di rete a usare il tunnel VPN. Se non viene stabilita una connessione alla VPN, il dispositivo non avrà accesso alla rete.

  Scegliere **Non configurata** per consentire al traffico di passare attraverso il tunnel VPN o la rete per dispositivi mobili.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili in modalità tutto schermo per dispositivi dedicati [Android](device-restrictions-android.md#kiosk) e [Windows 10](kiosk-settings.md).

## <a name="see-also"></a>Vedere anche

[Configurazione e risoluzione dei problemi dei dispositivi aziendali Android in Microsoft Intune](https://support.microsoft.com/help/4476974)
