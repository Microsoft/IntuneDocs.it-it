---
title: Gestire le impostazioni dei dispositivi con i criteri
description: "Usare Intune per creare e distribuire i criteri per il controllo delle impostazioni e delle funzionalità nei dispositivi registrati gestiti dall'utente."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7943e4023344aaeb531c4a9a7fa15f00cd8a7e81
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="manage-settings-and-features-on-your-devices-with-microsoft-intune-policies"></a>Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I *criteri* di Microsoft Intune sono gruppi di impostazioni che controllano le funzionalità nei dispositivi mobili e nei computer. È possibile creare criteri usando modelli che contengono le impostazioni consigliate o personalizzate, quindi distribuire i criteri a gruppi di dispositivi o utenti.

## <a name="types-of-policies"></a>Tipi di criteri

I criteri di Intune rientrano nelle seguenti categorie. La categoria usata influisce sulla modalità di creazione e di distribuzione dei criteri.


- **Criteri di configurazione:** usati comunemente per gestire le impostazioni di sicurezza e le funzionalità dei dispositivi. Usare le informazioni in questo argomento per informazioni su come creare e distribuire tali criteri e per approfondire la conoscenza delle impostazioni disponibili.
- **Criteri di conformità dei dispositivi:** definiscono le regole e le impostazioni a cui un dispositivo si deve adeguare per essere considerato conforme ai criteri di accesso condizionale. È anche possibile usare questi criteri per monitorare e correggere la conformità dei dispositivi indipendentemente dall'accesso condizionale.
Per informazioni dettagliate vedere [Criteri di conformità dei dispositivi in Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Criteri di accesso condizionale:** consentono di proteggere la posta elettronica e altri servizi in base alle condizioni specificate dall'utente.
Per informazioni dettagliate vedere [Limitare l'accesso alla posta elettronica e ai servizi di Office 365 con Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Criteri di registrazione dei dispositivi aziendali**: per informazioni sui criteri di registrazione dei dispositivi aziendali, vedere [Configurare la gestione dei dispositivi iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Criteri di accesso alle risorse:** questi criteri interagiscono per consentire agli utenti di accedere ai file e alle risorse necessarie per svolgere le attività, ovunque si trovino.
Per informazioni dettagliate vedere [Abilitare l'accesso alle risorse aziendali con Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


Per l'elenco completo dei criteri di Intune vedere [Informazioni di riferimento sui criteri di Microsoft Intune](microsoft-intune-policy-reference.md).

## <a name="create-a-configuration-policy"></a>Creare un criterio di configurazione

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Criteri** &gt; **Criteri di configurazione** &gt; **Aggiungi**.

2.  Scegliere il criterio desiderato e scegliere di usare le impostazioni consigliate per il criterio (se disponibili; è possibile modificare queste impostazioni successivamente) oppure scegliere di creare un criterio personalizzato con le proprie impostazioni.

    > [!TIP]
    > Per suggerimenti sulla scelta dei criteri corretti, vedere [Informazioni di riferimento sui criteri di Microsoft Intune](microsoft-intune-policy-reference.md).

3.  Quando si è pronti, scegliere **Crea criterio**.

4.  Nella pagina **Crea criterio** configurare un nome e una descrizione facoltativa per il criterio.

5.  Configurare le impostazioni necessarie dei criteri, quindi scegliere **Salva criterio**.

    Se serve assistenza per le impostazioni dei criteri, scegliere il tipo di criteri dall'elenco seguente:

    - [Impostazioni per i dispositivi iOS](ios-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i dispositivi Android](android-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i dispositivi Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i dispositivi Windows 8 e Windows 8.1](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i dispositivi Windows Phone 8.1](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i dispositivi Windows 10 Desktop e mobili](windows-10-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i dispositivi Windows Team](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per l'aggiornamento delle edizioni di Windows](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i dispositivi Mac OS X](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Impostazioni per i criteri relativi a termini e condizioni](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Impostazioni generali per i dispositivi mobili (legacy)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  Nella finestra di dialogo di conferma scegliere **Sì** per distribuire subito il criterio oppure scegliere **No** per creare il criterio senza distribuirlo.

È possibile visualizzare e modificare il nuovo criterio esplorando le sezioni per ciascun tipo di criterio nell'area di lavoro **Criteri**.

Quando si crea un criterio in cui vengono usate le impostazioni consigliate, il nome del nuovo criterio è una combinazione del nome del modello, della data e dell'ora di creazione. Quando si modifica il criterio, il nome viene aggiornato con l'ora e la data della modifica.

Dopo aver creato un criterio, è possibile distribuirlo in uno o più gruppi di utenti o dispositivi.

> [!TIP]
> Non vengono distribuiti tutti i tipi di criteri. Ad esempio, i criteri di gestione di applicazioni mobili (MAM) non vengono distribuiti. Questo tipo di criteri viene invece associato a un'app, che verrà quindi distribuita.

## <a name="deploy-a-configuration-policy"></a>Distribuire un criterio di configurazione

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire e quindi scegliere **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   Per distribuire il criterio, selezionare uno o più gruppi a cui lo si vuole distribuire e quindi scegliere **Aggiungi** &gt; **OK**.

    -   Per chiudere la finestra di dialogo senza distribuire il criterio, scegliere **Annulla**.

Quando si seleziona un criterio distribuito, è possibile visualizzare altre informazioni sulla distribuzione nella parte inferiore dell'elenco di criteri.

## <a name="manage-policies"></a>Gestire i criteri

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Criteri** e quindi individuare e selezionare i criteri da gestire.

2.  Selezionare una delle azioni seguenti:

- **Modifica**: aprire le proprietà del criterio selezionato per apportare modifiche.
- **Elimina**: eliminare il criterio selezionato.<br>Quando si elimina un criterio, il criterio viene rimosso da tutti i gruppi a cui è stato distribuito.
- **Gestisci distribuzione**: selezionare il gruppo in cui si vuole distribuire il criterio, quindi scegliere **Aggiungi**.


## <a name="frequently-asked-questions-about-intune-policies"></a>Domande frequenti sui criteri Intune

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-deployed"></a>Quanto tempo è necessario ai dispositivi mobili per ottenere i criteri o le app dopo la distribuzione?
Quando viene distribuito un criterio o un'app, Intune prova immediatamente a inviare una notifica al dispositivo per avvisarlo di contattare il servizio Intune per controllare la disponibilità di aggiornamenti. Questa operazione richiede in genere meno di 5 minuti.

Se dopo l'invio della prima notifica il dispositivo non contatta il servizio per ottenere il criterio, Intune esegue altri tre tentativi.  Se il dispositivo è offline, ad esempio è spento o non è connesso a una rete, può non ricevere le notifiche. In questo caso, il dispositivo otterrà il criterio al successivo controllo pianificato con il servizio Intune, come indicato di seguito:

- iOS e Mac OS X: ogni 6 ore.
- Android: ogni 8 ore.
- Windows Phone: ogni 8 ore.
- PC Windows 8.1 e Windows 10 registrati come dispositivi: ogni 8 ore.

Se il dispositivo è stato appena registrato, la frequenza di controllo sarà maggiore, come indicato di seguito:

- iOS e Mac OS X: ogni 15 minuti per 6 ore e quindi ogni 6 ore.
- Android: ogni 3 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore.
- Windows Phone: ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore.
- PC Windows registrati come dispositivi: ogni 3 minuti per 30 minuti e quindi ogni 8 ore.

In qualsiasi momento gli utenti possono anche aprire l'app Portale aziendale e sincronizzare il dispositivo per controllare immediatamente la disponibilità di criteri.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quali azioni fanno sì che Intune invii immediatamente una notifica a un dispositivo?
I dispositivi contattano Intune quando ricevono una notifica che lo richiede o durante un controllo regolarmente pianificato.  Quando a un dispositivo o a un utente viene destinata un'azione specifica di cancellazione dati, blocco, reimpostazione del passcode, distribuzione di app, distribuzione del profilo (Wi-Fi, VPN, posta elettronica e così via) o distribuzione di criteri, Intune proverà immediatamente a inviare una notifica al dispositivo per avvisarlo di contattare il servizio Intune per ricevere tali aggiornamenti.

Altre modifiche, ad esempio un aggiornamento delle informazioni di contatto nel portale aziendale, non comportano una notifica immediata ai dispositivi.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>Se vengono distribuiti più criteri per lo stesso utente o dispositivo, come si fa a sapere quali impostazioni verranno applicate?
Quando vengono distribuiti due o più criteri per lo stesso utente o dispositivo, la valutazione dell'impostazione che verrà applicata si verifica a livello di singola impostazione:

-   Le impostazioni dei criteri di conformità hanno sempre la precedenza sulle impostazioni dei criteri di configurazione.

-   L'impostazione di un criterio di conformità più restrittivo viene applicata se viene valutata rispetto alla stessa impostazione in un criterio di conformità diverso.

-   Se un'impostazione dei criteri di configurazione è in conflitto con un'impostazione di un altro criterio di configurazione, il conflitto viene visualizzato nella console di Intune. Tali conflitti devono essere risolti manualmente.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>Cosa accade quando i criteri di gestione delle applicazioni mobili sono in conflitto tra loro? Quale verrà applicato all'app?
I valori in conflitto sono le impostazioni più restrittive disponibili in un criterio MAM, ad eccezione dei campi di immissione numerici (come il numero di tentativi di immissione del PIN prima della reimpostazione),  che verranno impostati sugli stessi valori configurati durante la creazione di un criterio MAM nella console usando l'opzione delle impostazioni consigliate.

I conflitti si verificano quando due impostazioni dei criteri sono uguali.  Ad esempio, si supponga di aver configurato due criteri MAM identici tranne che per l'impostazione di copia/incolla.  In questo scenario, l'impostazione di copia/incolla verrà impostata sul valore più restrittivo, ma il resto delle impostazioni verrà applicato come è stato configurato.

Se un criterio viene distribuito nell'app e quindi applicato, e poi viene distribuito un secondo criterio, il primo criterio avrà la precedenza e rimarrà applicato, mentre il secondo risulterà in conflitto. Se entrambi i criteri vengono applicati contemporaneamente, ovvero non esiste un criterio precedente, saranno entrambi in conflitto. Le impostazioni in conflitto verranno impostate sui valori più restrittivi.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>Cosa accade quando sono in conflitto i criteri personalizzati iOS?
Intune non valuta il payload dei file di configurazione Apple o del criterio personalizzato URI OMA (Open Mobile Alliance Uniform Resource Identifier), ma funge semplicemente da meccanismo di recapito.

Quando si distribuisce un criterio personalizzato, verificare che le impostazioni configurate non siano in conflitto con i criteri di conformità, di configurazione o con altri criteri personalizzati. Nel caso di un criterio personalizzato con impostazioni in conflitto, l'ordine in cui le impostazioni vengono applicate sarà casuale.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>Che cosa accade quando un criterio viene eliminato o non è più applicabile?
Quando si elimina un criterio o si rimuove un dispositivo da un gruppo in cui è stato distribuito un criterio, il criterio e le impostazioni vengono rimossi dal dispositivo in base alle tabelle seguenti.

#### <a name="enrolled-devices"></a>dispositivi registrati

- Profili Wi-Fi, VPN, certificato e posta elettronica: questi profili vengono rimossi da tutti i dispositivi registrati supportati.
- Tutti gli altri tipi di criteri:
    - **Dispositivi Windows e Android**: le impostazioni non vengono rimosse dal dispositivo.
    - **Dispositivi Windows Phone 8.1**: vengono rimosse le impostazioni seguenti:
        - Richiedi una password per sbloccare i dispositivi mobili
        - Consenti password semplici
        - Lunghezza minima password
        - Tipo di password richiesto
        - Scadenza password (giorni)
        - Ricorda cronologia password
        - Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo
        - Minuti di inattività prima che venga richiesta la password
        - Tipo di password richiesto - numero minimo di set di caratteri
        - Consenti dispositivo foto/video
        - Richiedi crittografia sui dispositivi mobili
        - Consenti archivi rimovibili
        - Consenti browser Web
        - Consenti archivio applicazioni
        - Consenti acquisizione schermo
        - Consenti georilevazione
        - Consenti account Microsoft
        - Consenti copia e incolla
        - Consenti tethering Wi-Fi
        - Consenti connessione automatica agli hotspot Wi-Fi gratuiti
        - Consenti creazione report degli hotspot Wi-Fi
        - Consenti ripristino impostazioni predefinite
        - Consenti Bluetooth
        - Consenti NFC
        - Consenti Wi-Fi

    - **iOS**: vengono rimosse tutte le impostazioni, ad eccezione di:
        - Consenti roaming vocale
        - Consenti dati in roaming
        - Consenti sincronizzazione automatica durante il roaming

#### <a name="windows-pcs-running-the-intune-client-software"></a>PC Windows che eseguono il software client Intune

- **Impostazioni di Endpoint Protection**: vengono ripristinati i valori consigliati delle impostazioni. L'unica eccezione a questa regola è l'impostazione **Partecipa a Microsoft Active Protection Service**, il cui valore predefinito è **No**. Per informazioni dettagliate, vedere [Proteggere i PC Windows con Endpoint Protection per Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Impostazioni degli aggiornamenti software**: le impostazioni vengono ripristinate allo stato predefinito per il sistema operativo. Per informazioni dettagliate, vedere [Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Impostazioni di Microsoft Intune Center**: tutte le informazioni di contatto per il supporto configurate dal criterio vengono eliminate dai computer.
- **Impostazioni di Windows Firewall**: le impostazioni vengono ripristinate allo stato predefinito per il sistema operativo del computer. Per informazioni dettagliate, vedere [Proteggere i PC Windows con Endpoint Protection per Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).


### <a name="how-can-i-refresh-the-policies-on-a-device-to-ensure-that-they-are-current-applies-to-windows-pcs-running-the-intune-client-software-only"></a>Come aggiornare i criteri in un dispositivo (si applica solo ai PC Windows che eseguono il software client di Intune)?

1.  In qualsiasi gruppo di dispositivi selezionare i dispositivi di cui aggiornare i criteri e quindi scegliere **Attività remote** &gt; **Aggiorna criteri**.
2.  Scegliere **Attività remote** nell'angolo inferiore destro della console di amministrazione di Intune per verificare lo stato delle attività.

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Dove è possibile trovare contenuti sulla risoluzione dei problemi?

Vedere [Risolvere i problemi relativi ai criteri in Microsoft Intune](/intune-classic/troubleshoot/troubleshoot-policies-in-microsoft-intune).
