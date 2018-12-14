---
title: Restrizioni dei dispositivi del profilo di lavoro Android in Microsoft Intune - Azure | Microsoft Docs
description: Nei dispositivi con profilo Android Enterprise è possibile limitare alcune impostazioni del dispositivo, tra cui copia e incolla, visualizzazione delle notifiche, autorizzazioni delle app, condivisione dei dati, lunghezza della password, errori di accesso, uso dell'impronta digitale per sbloccare, riutilizzo delle password e abilitazione della condivisione dei contatti di lavoro con Bluetooth.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5f153e738aff28cae6481c0502f0682d10b8f104
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52729093"
---
# <a name="work-device-restriction-settings-in-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Android for Work in Intune

Questo articolo illustra le impostazioni delle restrizioni dei dispositivi Microsoft Intune configurabili per i dispositivi con profilo Android Enterprise.

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
- **Condivisione dei contatti tramite Bluetooth**: scegliere **Blocca** per impedire l'accesso ai contatti di lavoro da un altro dispositivo, ad esempio un sistema per auto quando un dispositivo Android viene associato tramite Bluetooth. **Non configurata** consente l'accesso ai contatti di lavoro in un altro dispositivo Bluetooth associato al dispositivo Android.
- **Tethering e accesso a hotspot**: scegliere **Blocca** per impedire il tethering e l'accesso a hotspot portatili. **Non configurata** consente il tethering e l'accesso a hotspot portatili.
- **Archiviazione USB**: scegliere **Consenti** per consentire l'accesso all'archiviazione USB nel dispositivo. **Non configurata** impedisce l'accesso all'archiviazione USB.
- **Trasferimento di file su USB**: scegliere **Blocca** per impedire il trasferimento di file tramite USB. **Non configurata** consente il trasferimento di file.
- **Supporti esterni**: scegliere **Blocca** per impedire l'uso o la connessione di qualsiasi supporto esterno nel dispositivo. **Non configurata** consente supporti esterni nel dispositivo.
- **Trasmetti dati con NFC**: scegliere **Blocca** per impedire l'uso della tecnologia NFC (Near Field Communication) per la trasmissione di dati dalle app. **Non configurata** consente l'uso di NFC per condividere dati tra i dispositivi.
- **Funzionalità di debug**: scegliere **Consenti** per consentire agli utenti di usare le funzionalità di debug nel dispositivo. **Non configurata** impedisce agli utenti di usare le funzionalità di debug nel dispositivo.
- **Regolazione del microfono**: scegliere **Blocca** per impedire agli utenti di riattivare il microfono e regolare il volume del microfono. **Non configurata** consente all'utente di usare il microfono nel dispositivo e regolarne il volume.
- **Indirizzi di posta elettronica per la protezione dal ripristino delle impostazioni predefinite**: scegliere **Indirizzi di posta elettronica dell'account Google**. Immettere gli indirizzi di posta elettronica degli amministratori dei dispositivi che possono sbloccare il dispositivo dopo la cancellazione. Assicurarsi di separare gli indirizzi di posta elettronica con punti e virgola, ad esempio `admin1@gmail.com;admin2@gmail.com`. Se non viene immesso un indirizzo di posta elettronica, chiunque può sbloccare il dispositivo dopo il ripristino delle impostazioni predefinite.
- **Rete di emergenza**: scegliere **Abilita** per consentire agli utenti di attivare la funzionalità di rete di emergenza. Se non è possibile creare una connessione di rete in fase di avvio del dispositivo, la rete di emergenza richiede all'utente di connettersi temporaneamente a una rete per aggiornare i criteri del dispositivo. Dopo aver applicato i criteri, la rete temporanea viene dimenticata e viene ripreso l'avvio del dispositivo. Questa funzionalità consente di connettere i dispositivi a una rete se:
  - Non è disponibile una rete idonea nei criteri più recenti.
  - Il dispositivo viene avviato in un'app in modalità di attività di blocco.
  - L'utente non è in grado di raggiungere le impostazioni del dispositivo.

  **Non configurata** impedisce agli utenti di attivare la funzionalità di rete di emergenza nel dispositivo.

- **Consenti l'installazione da origini sconosciute**: scegliere **Consenti** in modo che gli utenti possano attivare **Origini sconosciute**. Questa impostazione consente l'installazione di app da origini sconosciute. **Non configurata** impedisce agli utenti di attivare **Origini sconosciute**.
- **Aggiornamento del sistema**: scegliere un'opzione per definire la modalità di gestione degli aggiornamenti in modalità wireless da parte del dispositivo:
  - **Impostazione predefinita dispositivo**: usare l'impostazione predefinita del dispositivo.
  - **Automatico**: gli aggiornamenti vengono installati automaticamente senza l'intervento dell'utente. L'impostazione del criterio consente di installare immediatamente eventuali aggiornamenti in sospeso.
  - **Posposto**: gli aggiornamenti vengono rimandati di 30 giorni. Al termine dei 30 giorni, Android chiede all'utente di installare l'aggiornamento. Ai produttori di dispositivi e ai gestori telefonici è consentito impedire il posticipo degli aggiornamenti della sicurezza. Un aggiornamento posticipato viene indicato all'utente da una notifica di sistema nel dispositivo. 
  - **Finestra di manutenzione**: installa automaticamente gli aggiornamenti in una finestra di manutenzione giornaliera impostata in Intune. L'installazione viene tentata ogni giorno per 30 giorni e può non riuscire a causa di livelli di batteria o spazio insufficienti. Dopo 30 giorni, Android chiede all'utente di eseguire l'installazione. Questa finestra viene usata anche per installare gli aggiornamenti per le app di Play. Usare questa opzione per i dispositivi dedicati, ad esempio i chioschi multimediali, in quanto consente di aggiornare le app in primo piano dei chioschi multimediali per app singola.
- **Aggiornamenti automatici delle app**: scegliere se gli aggiornamenti automatici vengono installati. Le opzioni disponibili sono:
  - **Non configurato**
  - **Scelta utente**
  - **Mai**
  - **Solo Wi-Fi**
  - **Sempre**

### <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

- **Analisi delle minacce nelle app**: specificare **Rendi obbligatorio** per imporre l'abilitazione dell'impostazione **Verifica app** per i profili di lavoro e personali.

### <a name="kiosk-settings"></a>Impostazioni della modalità tutto schermo

È possibile configurare un dispositivo per eseguire una sola app o molte app. Quando un dispositivo è in modalità tutto schermo, sono disponibili solo le app aggiunte.

**Modalità tutto schermo**: scegliere se il dispositivo eseguirà una sola app o più app.

- **App singola per chiosco multimediale**: gli utenti possono accedere a un'app singola nel dispositivo. All'avvio del dispositivo viene avviata solo l'app specifica. Gli utenti non possono aprire nuove app o modificare l'app in esecuzione.

  **Procedura**
  1. Scegliere **Selezionare un'app gestita** e selezionare l'app Google Play gestita nell'elenco. 

      Se l'elenco non include alcuna app, [aggiungere alcune app Android](apps-add-android-for-work.md) al dispositivo. Assicurarsi di [assegnare l'app al gruppo di dispositivi creato per i dispositivi in modalità tutto schermo](apps-deploy.md).

  2. Scegliere **OK** > **OK** per aggiungere l'app.

- **Più app in modalità tutto schermo**: gli utenti possono accedere a un set di app limitato nel dispositivo. All'avvio del dispositivo vengono avviate solio le app aggiunte. È anche possibile aggiungere alcuni collegamenti Web che gli utenti possono aprire. Quando viene applicato il criterio, gli utenti visualizzano le icone delle app consentite nella schermata iniziale.

  > [IMPORTANTE] Per i dispositivi con più app in modalità tutto schermo, l'[app di schermata iniziale gestita ](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) da Google Play **deve essere**:
  >   - [Aggiunta come app client](apps-add-android-for-work.md) in Intune
  >   - [Assegnata al gruppo di dispositivi](apps-deploy.md) creato per i dispositivi in modalità tutto schermo
  > 
  > Non è richiesto che l'app di **schermata iniziale gestita** sia inclusa nel profilo di configurazione, ma è necessario che venga aggiunta come app client. Quando l'app di **schermata iniziale gestita** viene aggiunta come app client, qualsiasi altra app aggiunta nel profilo di configurazione viene visualizzata come icona nell'app di **schermata iniziale gestita**. 

  - Scegli **Aggiungi** e selezionare le app nell'elenco.

    Se l'app di **schermata iniziale gestita** non è inclusa nell'elenco, [aggiungerla da Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Assicurarsi di [assegnare l'app](apps-deploy.md) al gruppo di dispositivi creato per i dispositivi in modalità tutto schermo.

    È anche possibile aggiungere al dispositivo altre [app Android](apps-add-android-for-work.md) e [app Web](web-app.md) create dall'organizzazione. Assicurarsi di [assegnare l'app al gruppo di dispositivi creato per i dispositivi in modalità tutto schermo](apps-deploy.md).

  - **Pulsante Pagina iniziale virtuale**: scegliere **Abilita** per visualizzare un pulsante Pagina iniziale nel dispositivo in modalità tutto schermo. Quando questo pulsante è visualizzato, riporta l'utente alla schermata iniziale del dispositivo in modo che possa cambiare facilmente app. In alcuni dispositivi Android, è possibile che gli utenti debbano scorrere velocemente verso l'alto sullo schermo per visualizzare il pulsante Pagina iniziale. **Disabilita** non mostra un pulsante Pagina iniziale e gli utenti devono quindi usare il pulsante Indietro per spostarsi tra le app.
  - **Esci dalla modalità tutto schermo**: scegliere **Abilita** per consentire agli amministratori di sospendere temporaneamente la modalità tutto schermo per aggiornare il dispositivo. Per usare questa funzionalità, l'amministratore esegue le operazioni seguenti: 
  
    1. Continuare a selezionare il pulsante Indietro fino a quando non viene visualizzato il pulsante "Exit Kiosk" (Esci da modalità tutto schermo). 
    2. Selezionare il pulsante e immettere il PIN per **Codice di uscita dalla modalità tutto schermo**.
    3. Al termine delle modifiche, selezionare l'app di **schermata iniziale gestita**. Questo passaggio blocca di nuovo il dispositivo in modalità tutto schermo con più app. 
    
    **Disabilita** non offre la possibilità di sospendere la modalità tutto schermo. Se l'amministratore continua a selezionare il pulsante Indietro e seleziona il pulsante "Exit Kiosk" (Esci da modalità tutto schermo), un messaggio segnala che è richiesto un passcode.
    
    - **Codice di uscita dalla modalità tutto schermo**: immettere un PIN numerico da 4-6 cifre. L'amministratore usa questo PIN per sospendere temporaneamente la modalità tutto schermo.
 
  - **Imposta uno sfondo personalizzato per l'URL**: immettere un URL per personalizzare la schermata di sfondo nel dispositivo in modalità tutto schermo.

### <a name="device-password-settings"></a>Impostazioni della password del dispositivo mobile

- **Protezione della tastiera**: scegliere **Disabilita** per impedire agli utenti di usare la funzionalità della schermata di blocco di protezione della tastiera nel dispositivo. **Non configurata** consente all'utente di usare le funzionalità di protezione della tastiera.
- **Tipo di password richiesto**: definire il tipo di password richiesta per il dispositivo. Le opzioni disponibili sono:
  - **Almeno numerico**
  - **Complessa numerica**: i numeri consecutivi o ripetuti (ad esempio, "1111" o "1234") non sono consentiti.
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**
- **Lunghezza minima password**: immettere la lunghezza minima della password che l'utente deve configurare (da 4 a 16 caratteri).
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: immettere il numero di errori di accesso consentiti prima della cancellazione del dispositivo (da 1 a 11).

### <a name="power-settings"></a>Impostazioni di risparmio energia

- **Time to lock screen** (Tempo per schermata di blocco): impostare la quantità di tempo di inattività necessaria affinché il dispositivo venga bloccato.
- **Screen on while device plugged in** (Schermata attiva con dispositivo alimentato): scegliere i tipi di alimentazione che mantengono attiva la schermata del dispositivo alimentato.

### <a name="users-and-accounts-settings"></a>Impostazioni di utenti e account

- **Aggiungi nuovi utenti**: scegliere **Blocca** per impedire agli utenti di aggiungere nuovi utenti. Ogni utente dispone di uno spazio personale nel dispositivo per schermate iniziali, account, app e impostazioni personalizzati. **Non configurata** consente agli utenti di aggiungere altri utenti nel dispositivo.
- **Rimozione degli utenti**: scegliere **Blocca** per impedire agli utenti di rimuovere gli utenti. **Non configurata** consente agli utenti di rimuovere altri utenti dal dispositivo.
- **Modifiche all'account**: scegliere **Blocca** per impedire agli utenti di modificare gli account. **Non configurata** consente agli utenti di aggiornare gli account utente nel dispositivo.

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

#### <a name="work-profile-password"></a>Password del profilo di lavoro

- **Richiedi la password del profilo di lavoro**: si applica ad Android 7.0 e versioni successive con il profilo di lavoro abilitato. Scegliere **Rendi obbligatorio** per immettere criteri di passcode validi solo per le app nel profilo di lavoro. Per impostazione predefinita, l'utente finale può usare i due PIN definiti separatamente oppure scegliere di combinarli nel PIN più complesso. **Non configurata** consente all'utente di usare le app di lavoro, senza immettere una password.
- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono avere (**4**-**16**).
- **Numero massimo di minuti di inattività fino al blocco del profilo di lavoro**: selezionare la quantità di tempo che deve trascorrere prima che il profilo di lavoro si blocchi. L'utente deve quindi immettere le credenziali per riottenere l'accesso.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che il profilo di lavoro venga cancellato dal dispositivo.
- **Scadenza password (giorni)**: immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**) .
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
- **Scadenza password (giorni)**: immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**)
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
  >  - Il client VPN scelto deve essere installato nel dispositivo e deve supportare la VPN per app nei profili di lavoro. In caso contrario si verificherà un errore. 
  >  - È necessario approvare l'app client VPN in **Google Play Store gestito**, sincronizzare l'app con Intune e distribuire l'app nel dispositivo. Al termine di queste operazioni, l'app viene installata nel profilo di lavoro dell'utente.
  >  - Esistono problemi noti quando si usa una VPN per app con F5 Access per Android 3.0.3. Per altre informazioni, vedere le [note sulla versione di F5 per F5 Access per Android 3.0.3](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-3.html#relnotes_known_issues_f5_access_android).

- **Lockdown mode** (Modalità di blocco): **Abilita** forza tutto il traffico di rete a usare il tunnel VPN. Se non viene stabilita una connessione alla VPN, il dispositivo non avrà accesso alla rete.

  Scegliere **Non configurata** per consentire al traffico di passare attraverso il tunnel VPN o la rete per dispositivi mobili.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili in modalità tutto schermo per dispositivi [Android](device-restrictions-android.md#kiosk) e [Windows 10](kiosk-settings.md).
