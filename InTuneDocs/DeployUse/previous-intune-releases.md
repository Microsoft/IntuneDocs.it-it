---
title: Versioni precedenti | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: 3080d23f464e96315ed9e5fd59774ba9f1b2dd86
ms.openlocfilehash: 65d582958d77150091880cce72e079b87308209f


---

# Versioni precedenti di Intune
## Maggio 2016

Tutte queste funzionalità sono supportate anche per le distribuzioni ibride (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la pagina delle [Novità per le funzionalità ibride](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Documentazione
Benvenuti nella versione di anteprima di [docs.microsoft.com](https://docs.microsoft.com/en-us/intune).
Questa piattaforma moderna completamente nuova è stata progettata per rendere più semplice per i nostri clienti comprendere e usare Intune.
Per informazioni su tutte le nuove funzionalità, vedere [Introducing docs.microsoft.com (Introduzione a docs.microsoft.com)](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Integrità del servizio Intune
Le informazioni sull'integrità del servizio per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) in **Integrità dei servizi**.
Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Gestione delle app
- **MAM SDK: supporto per la configurazione della lunghezza del PIN.** Sarà possibile specificare la lunghezza del PIN per le app MAM in modo simile al PIN di un dispositivo. Gli utenti finali dovranno perciò conformarsi alle nuove limitazioni imposte. Vedranno la schermata del PIN leggermente modificata per tenere conto della lunghezza del PIN. Per informazioni dettagliate, vedere gli articoli relativi alle [impostazioni dei criteri MAM per Android](/intune/deploy-use/android-mam-policy-settings) e alle [impostazioni dei criteri MAM per iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype for Business per iOS e Android.** È ora possibile scegliere come destinazione Skype for Business con [MAM senza criteri di registrazione](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Dopo la connessione degli utenti, verranno applicati i criteri MAM.

- **Sono disponibili nuove app per la gestione con criteri MAM.** Le app Microsoft Word, Excel e PowerPoint per Android possono ora essere associate a criteri MAM su dispositivi non registrati in Intune. Per visualizzare l'elenco completo delle app supportate, passare alla raccolta di applicazioni per dispositivi mobili di Microsoft Intune nella pagina dei [partner di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### Aggiornamenti del portale aziendale

#### App Portale aziendale Android
- **Notifiche di tipo avviso popup per l'utente finale**: per gli utenti finali che registrano un dispositivo o lo rimuovono dal Portale aziendale vengono visualizzate notifiche di tipo avviso popup dell'app Portale aziendale per Android.

- **Modifiche agli account Manager di registrazione dispositivi nell'app Portale aziendale per Android.** Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro Dispositivi personali dell'app Portale aziendale per Android. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.

#### Sito Web del portale aziendale
- **Sito Web del portale aziendale: il banner di identificazione del dispositivo offrirà maggiori informazioni agli utenti finali.** Gli utenti finali possono ora identificare facilmente il dispositivo selezionato durante l'uso del sito Web del portale aziendale. Se viene selezionato il dispositivo errato, gli utenti potranno selezionare il dispositivo corretto toccando il collegamento **Tocca qui** nel banner della pagina iniziale.

## Sviluppi futuri
- **Caricamento dell'interfaccia utente del centro messaggi**. Come parte della migrazione di Intune nel [portale di gestione di Office 365](https://portal.office.com/), inizieremo a sfruttare il suo centro messaggi per comunicare le nuove funzionalità e altre notifiche. Inoltre, installando l'app complementare per dispositivi mobili Office 365 Admin, è possibile ricevere notifiche sul cellulare e inoltrare facilmente qualsiasi messaggio agli utenti o a un alias di distribuzione.
Inizieremo a usare il centro messaggi con la nostra versione di maggio per notificare quando gli aggiornamenti sono completati e includeremo informazioni sulle funzionalità di Intune nuove e migliorate. Visitare il centro messaggi oggi stesso eseguendo l'accesso al [portale di gestione di Office 365](https://portal.office.com/) e scegliendo l'opzione Centro messaggi nel riquadro di spostamento a sinistra.

- **Modifiche agli account Manager di registrazione dispositivi**. Per migliorare le prestazioni e la scalabilità, Intune non visualizza più **tutti** i dispositivi dei manager di registrazione dispositivi nel riquadro **Dispositivi personali** dell'app Portale aziendale iOS. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune. Intune deprecherà anche l'uso degli account Manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi. Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile.

### Guida di orientamento per il cloud
Per ottenere informazioni sugli sviluppi futuri per Intune, vedere la [guida di orientamento Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Deprecazione del servizio
- **App visualizzatore di Intune.** Con il rilascio della nuova app di condivisione RMS, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
    - Visualizzatore AV di Intune
    - Visualizzatore PDF di Intune
    - Visualizzatore immagini di Intune per Android disponibile in Google Play

  Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova app Rights Management (condivisione RMS) per Android che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Sono disponibili altre informazioni sull'app di condivisione RMS con collegamento alla documentazione.

- **Rimozione della capacità di scegliere gruppi personalizzati come destinazione delle regole di notifica.**
Le regole di notifica di Intune definiscono i destinatari degli avvisi di posta elettronica inviati da Intune. Attualmente è possibile configurare regole di notifica per inviare messaggi di posta elettronica a tutti gli utenti dei dispositivi di un gruppo di dispositivi di Intune creato. A partire dal 1° giugno 2016, la configurazione dei gruppi creati dagli utenti come destinazione non sarà più supportata.

    Attualmente, per impostare come destinazione di una regola di notifica un gruppo creato dalla console di amministrazione di Microsoft Intune, è necessario eseguire i passaggi seguenti:

    Nell'area di lavoro **Amministrazione** fare clic su **Regole di notifica** > **Crea nuova regola**

    Nel secondo passaggio della procedura guidata di creazione di una regola di notifica selezionare i gruppi di dispositivi di destinazione della regola. Il passaggio "Seleziona gruppi di dispositivi" verrà rimosso dalla console di Intune.

    La sequenza temporale preliminare di questa modifica sarà la seguente:
    - Nel giugno 2016 per i nuovi tenant non verrà visualizzato il secondo passaggio della procedura guidata di creazione di una regola di notifica. I tenant esistenti non sono interessati dalla modifica.
    - In agosto 2016 per alcuni tenant esistenti non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.
    - In ottobre 2016 per tutti i tenant non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.


- **Modifiche al supporto dell'app Portale aziendale per iOS**. Nei prossimi mesi verrà eseguito un aggiornamento dell'app Portale aziendale di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 8.0 o versione successiva. Gli utenti non potranno più registrare nuovi dispositivi che eseguono versioni precedenti a iOS 8.0. I dispositivi registrati che eseguono versioni precedenti a iOS 8.0 continueranno a essere gestiti e potranno, per un periodo di tempo limitato, continuare a usare l'app Portale aziendale. È necessario tuttavia che i dispositivi eseguano iOS 8.0 o versione successiva per accedere alle versioni più recenti dell'app Portale aziendale. È consigliabile richiedere agli utenti di eseguire l'aggiornamento a iOS 8.0 o versione successiva per poter usare al meglio le nuove funzionalità di Intune.  


## Aprile 2016
Tutte queste funzionalità sono supportate anche per i clienti ibridi (Configuration Manager con Intune).
### Gestione delle app
- **Conformità utente MAM.**
È ora possibile visualizzare lo [stato](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) dei criteri di gestione delle applicazioni per ogni utente del tenant Azure Active Directory (AAD). Sono inclusi:
   - Dispositivi
   - App sul dispositivo

   Valori di stato:

   **Archiviato**: indica che il criterio è stato distribuito all'utente, l'app è stata usata nel contesto di lavoro e ha ricevuto correttamente i criteri.

    **Non archiviato**: indica che il criterio è stato distribuito all'utente, ma da quel momento l'app non è mai stata usata nel contesto di lavoro.


- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (Android).**
È disponibile una nuova impostazione per la [gestione delle applicazioni per dispositivi mobili](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) senza registrazione del dispositivo. Questa impostazione consente di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi Android. Quando l'impostazione è abilitata, le applicazioni di destinazione non possono più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, le applicazioni di destinazione possono salvare i contatti nella rubrica nativa. Quando [si cancella un dispositivo o un'app da remoto](wipe-managed-company-app-data-with-Microsoft-Intune.md), tutti i contatti che sono già stati salvati nella rubrica nativa vengono rimossi. Questa nuova impostazione è supportata inizialmente dall'applicazione Outlook sui dispositivi Android.

### Gestione dei dispositivi
- **Identificazione del numero di telefono per i dispositivi aziendali.** I telefoni classificati come "aziendali" sono ora identificati con il loro numero di telefono completo quando, per esempio, si esegue un report inventario dei dispositivi mobili. I numeri di telefono BYOD continuano a essere mascherati con **** mostrando solo le ultime 4 cifre.


### Aggiornamenti del Portale aziendale
Gli utenti di **app del Portale aziendale Android** che non hanno registrato il loro dispositivo in Intune e non hanno il certificato corretto installato non potranno accedere all'app del Portale aziendale Android e vedranno il messaggio "Non è possibile accedere. Manca un certificato necessario per il dispositivo". Il messaggio include il collegamento “Risoluzione del problema” che gli utenti possono usare per vedere le istruzioni per l'installazione del certificato. Per i passaggi che gli utenti finali devono eseguire per risolvere il problema vedere [Manca un certificato necessario per il dispositivo](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**App Portale aziendale iOS** È stato aggiunto il supporto per l'azione di scorrimento per aggiornare il contenuto della schermata iniziale, che include le app e i dispositivi elencati e le informazioni di contatto IT. L'azione di scorrimento per l'aggiornamento non controlla la conformità o le informazioni sui criteri, cosa che si può fare selezionando il riquadro per il dispositivo corrente e toccando il pulsante **Sincronizza**.

**App Portale aziendale per Windows 10 Mobile e Windows Phone 8.1** Il processo di installazione delle app line-of-business è stato migliorato. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo manualmente per velocizzare l'installazione delle app](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sito Web Portale aziendale** Durante l'installazione delle app line-of-business, gli utenti di Windows 10 Mobile e Windows Phone 8.1 vedranno ora i seguenti stati nuovi, che specificano maggiori dettagli sullo stato della loro installazione:

* **In attesa della sincronizzazione del dispositivo**: l'utente ha toccato “Installa” e il dispositivo ora tenta di sincronizzarsi con l'infrastruttura Intune. La sincronizzazione è necessaria per poter completare l'installazione. Il messaggio "In attesa della sincronizzazione del dispositivo" è anche un collegamento che gli utenti possono toccare per vedere le [istruzioni](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) per sincronizzare manualmente il dispositivo con Intune, se il processo di sincronizzazione impiega troppo tempo o si blocca.
* **Download in corso**: la richiesta di download dell'utente è in fase di elaborazione e il dispositivo sta scaricando e installando l'app.

Prima dell'aggiunta di questi stati, gli utenti potevano essere confusi se l'installazione di un'app impiegava molto tempo, poiché vedevano solo lo stato "Installazione in corso", che poteva rimanere visualizzata sullo schermo per ore. Grazie all'aggiunta dei nuovi stati gli utenti, invece di chiamare il supporto, possono ora toccare il collegamento "In attesa della sincronizzazione del dispositivo" e seguire le istruzioni per forzare la ripresa del processo di sincronizzazione.


## Marzo 2016
### Novità a partire dal 29 marzo 2016
Fatta eccezione per l'aggiornamento dei criteri di configurazione generale di Windows 10, tutte le funzionalità della versione del 29 marzo 2016 sono supportate anche per i clienti ibridi (Configuration Manager con Intune). Il supporto ibrido per l'aggiornamento dei criteri di configurazione generale di Windows 10 sarà presto disponibile. Tenere presente che alcune di queste funzionalità richiedono l'ultima versione di Configuration Manager.

### Gestione delle app
- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (iOS).** È disponibile una nuova impostazione per la gestione delle applicazioni mobili senza registrazione del dispositivo. Questa impostazione consente di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi iOS. Quando l'impostazione è abilitata, l'applicazione non potrà più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, l'applicazione potrà salvare i contatti nella rubrica nativa. Quando si cancella un dispositivo in modo selettivo, tutti i contatti che sono già stati salvati nella rubrica nativa vengono rimossi. Questa nuova impostazione è supportata dall'applicazione Outlook sui dispositivi iOS. Per informazioni dettagliate su questa e altre impostazioni, vedere [Creare e distribuire i criteri MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Controllo di accesso
- **Skype for Business Online supporta l'accesso condizionale.** È possibile impostare un criterio di accesso condizionale per Skype for Business Online in modo che sia accessibile solo da dispositivi iOS e Android gestiti e conformi. Agli utenti finali che tentano di accedere all'applicazione per dispositivi mobili Skype for Business in iOS e Android sarà chiesto di registrarsi con Intune e di risolvere eventuali problemi di non conformità per poter completare l'accesso. Per informazioni dettagliate, vedere [Gestione dell'accesso a Skype for Business Online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Gestione dei dispositivi
- **Supporto Intune per iOS 9.3.** Lunedì 21 marzo Apple ha annunciato la disponibilità di iOS 9.3. Microsoft ha dedicato il massimo impegno a garantire la compatibilità di Microsoft Intune con la versione più recente del sistema operativo mobile di Apple ed [è lieta di annunciare che Intune supporta la gestione dei dispositivi iOS 9.3](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Tutte le funzionalità Intune esistenti attualmente disponibili per la gestione dei dispositivi iOS continueranno a funzionare senza problemi quando gli utenti aggiorneranno i dispositivi a iOS 9.3. Inoltre, iOS 9.3 è oggi supportato anche per i clienti ibridi (Configuration Manager con Intune).

- **I criteri di configurazione generale di Windows 10 includono ora impostazioni per la gestione di Windows Defender su PC Windows 10 registrati.** Per informazioni dettagliate vedere [Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Portale aziendale

- **Pacchetti delle app Windows disponibili direttamente dal Portale aziendale.** Gli utenti dei PC Windows 8, Windows 8.1 e Windows RT possono ora installare i pacchetti delle app Windows (con estensione appx) direttamente dal sito Web del portale aziendale. In precedenza era necessario eseguire la distribuzione, oppure, per poter installare le app, gli utenti dovevano installare l'app Portale aziendale sui loro dispositivi.

- **Gli utenti possono bloccare il dispositivo da remoto dal portale aziendale.** Al sito Web del portale aziendale è stata aggiunta una nuova opzione di blocco remoto che consente agli utenti finali di bloccare da remoto il dispositivo dal portale in caso di furto o smarrimento. Vedere le [istruzioni per l'utente](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). La tabella seguente riporta i dettagli di supporto della piattaforma relativi al blocco remoto per Intune Standalone e Intune con Configuration Manager.

|Piattaforma | Dettagli sul supporto|
|---------|----------------|
|Android |Supportato|
|iOS |Supportato|
|Windows 10 Mobile |Supportato solo se per il telefono è impostato un passcode|
|Windows 10 Desktop |Non supportato|
|Windows Phone 8.1 |Supportato solo se per il telefono è impostato un passcode|
|Windows Phone 8.0 |Non supportato|
|PC (Windows 8.0 e versioni precedenti) |Non supportato|
|PC (Windows 8.1) |Non supportato|

### Novità a partire dal 10 marzo 2016

### Gestione delle app

- **Vantaggi della gestione "Open-In" di iOS per dispositivi registrati in una soluzione MDM di terze parti** È possibile usare il proprio fornitore di gestione dei dispositivi mobili di terze parti (MDM) per godere dei vantaggi della gestione "Open-In"di iOS. È possibile impostare le restrizioni nelle impostazioni del profilo di configurazione e distribuire l'app usando le istruzioni in [Gestire il trasferimento di dati tra app iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

     Questo approccio presenta due vantaggi principali:

     1. Gli utenti devono accedere con l'account aziendale prima di ottenere l'accesso a tutti i dati aziendali dai servizi cloud o da altre app. Ciò garantisce la disponibilità dei criteri di gestione di applicazioni mobili (MAM) quando si accede ai dati.

     2. I profili di posta elettronica gestiti e altre app gestite distribuite con una soluzione MDM di terze parti possono condividere file e dati con le app che hanno criteri MAM di Intune.

- **Gestire l'app Microsoft Outlook con criteri MAM per dispositivi non registrati in Intune** Ora è possibile gestire l'app Microsoft Outlook su dispositivi non registrati in Intune con i criteri di gestione delle applicazioni mobili di Intune. L'app Microsoft Outlook aggiornata con le funzionalità MAM è disponibile per i dispositivi [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook). Usare le istruzioni nell'argomento [Creare e distribuire i criteri di gestione delle app per dispositivi mobili](https://technet.microsoft.com/library/mt627829.aspx) per creare un criterio MAM.  


- **I criteri di configurazione delle app per dispositivi mobili offrono più flessibilità per specificare i dettagli utente per le app iOS** È possibile specificare le impostazioni utente che possono risultare necessarie a un'app iOS quando viene aperta. Ad esempio, è possibile specificare una porta di rete o un nome utente. Per informazioni dettagliate vedere [Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Distribuire Adobe Reader per Microsoft Intune nei dispositivi iOS aziendali gestiti da Intune** Ora è possibile gestire l'app Adobe Reader iOS su dispositivi registrati con i criteri di gestione delle applicazioni mobili di Intune.

- **Verificare che le clip Web distribuite vengano aperte in Managed Browser** È possibile distribuire clip Web specifiche che possono essere aperte solo con Managed Browser nei dispositivi iOS e Android. Ad esempio, se si distribuiscono i collegamenti alle risorse aziendali con il portale aziendale, quando gli utenti accedono ai collegamenti li aprono direttamente in Managed Browser, dove possono essere protetti con i criteri MAM. Per informazioni dettagliate vedere [Distribuire le app](deploy-apps.md).


- **Trovare, gestire e distribuire app Windows Store for Business per dispositivi Windows 10 dalla console di amministrazione di Intune** In Intune è disponibile il supporto per Windows Store for Business, che consente di trovare, gestire e distribuire app ai dispositivi Windows 10 gestiti. Windows Store per le aziende consente di gestire il processo di distribuzione e monitoraggio di queste app dalla console di amministrazione di Intune, la stessa console usata per gestire le altre app. In particolare, Windows Store per le aziende gestisce i contenuti e le licenze delle app con licenze online. Per informazioni dettagliate vedere [Gestire le app acquistate in Windows Store for Business](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Gestione dei dispositivi
- **Distribuzione di certificati PFX per dispositivi iOS** Gli amministratori di Intune possono creare e distribuire certificati PFX di iOS per Wi-Fi, posta elettronica e autenticazione VPN nei dispositivi iOS. Questa funzionalità è già disponibile per i dispositivi Android e Windows 10. Per informazioni dettagliate vedere [Abilitare l'accesso alle risorse aziendali usando i profili certificato](secure-resource-access-with-certificate-profiles.md).


- **Applicare app e criteri a gruppi di dispositivi diversi in base alla selezione di categorie utente** Gli amministratori di Intune possono ora definire categorie di dispositivi personalizzate selezionabili dagli utenti durante la registrazione. Ad esempio, gli amministratori possono consentire agli utenti di specificare se il dispositivo che stanno registrando viene usato per operazioni relative a "Registratore di cassa", "Camion per le consegne" o "Inventario". La selezione della categoria comporta l'inserimento del dispositivo come membro di un gruppo di dispositivi di Intune, che può essere usato per la distribuzione di diverse app e criteri al dispositivo registrato. Per informazioni dettagliate vedere [Classificare i dispositivi con il mapping del gruppo di dispositivi](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Modifiche e aggiornamenti del portale aziendale Microsoft
In questa versione sono state apportate le modifiche seguenti al portale aziendale.

**App Portale aziendale Android**

* Quando gli utenti avviano un'app gestita da Gestione di applicazioni mobili (MAM), visualizzeranno un messaggio di notifica che informa che l'applicazione è gestita dalla propria società. Gli utenti possono ora toccare un collegamento "Altre informazioni" per ottenere [altre informazioni](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) su cosa significa "app gestite". È anche possibile toccare "Non mostrare più" in modo che il messaggio non sia più visualizzato quando si avvia l'applicazione.
* Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
* I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.


**App del portale aziendale iOS**
* Quando gli utenti avviano un'app gestita da Gestione di applicazioni mobili (MAM), visualizzeranno un messaggio di notifica che informa che l'applicazione è gestita dalla propria società. Gli utenti possono ora toccare un collegamento "Altre informazioni" per ottenere [altre informazioni](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) su cosa significa "app gestite". È anche possibile toccare "Non mostrare più" in modo che il messaggio non sia più visualizzato quando si avvia l'applicazione.
* Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).
* I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.




## Febbraio 2016
### Modifiche e aggiornamenti del portale aziendale Microsoft

In questa versione sono state apportate le modifiche seguenti al portale aziendale.

#### App Portale aziendale Android
- Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
- I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.

#### App del portale aziendale iOS
 - Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).

 - I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.


## Gennaio 2016

### Sfruttare le funzionalità di Windows 10
* **Accesso condizionale con il servizio di attestazione dell'integrità** Gli amministratori possono ora visualizzare lo stato di attestazione dell'integrità dei dispositivi Windows 10 nella console di amministrazione di Intune. L'attestazione dell'integrità dei dispositivi consente all'amministratore di assicurare che i computer client dispongano di configurazioni attendibili di BIOS, TPM e software di avvio. Per supportare l'attestazione dell'integrità dei dispositivi, i dispositivi client devono eseguire Windows 10 con TPM 2 abilitato. L'attestazione dell'integrità dei dispositivi visualizza il numero di dispositivi abilitati per ognuno degli elementi seguenti:
    * Antimalware ad esecuzione anticipata
    * BitLocker
    * Avvio protetto
    * Integrità del codice

    Per altre informazioni sull'attestazione dell'integrità del dispositivo, sui punti dati raccolti e sul report di attestazione dell'integrità, leggere [Gestire i criteri di conformità del dispositivo per Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md). L'articolo relativo al [servizio HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) ne illustra le caratteristiche in modo approfondito.

* **Criteri Passport for Work e gestione dei certificati in Windows 10** Con Intune è possibile [eseguire l'integrazione con Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), un metodo di accesso alternativo per Windows 10 che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale. Passport consente di eseguire l'accesso usando un movimento dell'utente, anziché una password. Un movimento dell'utente può essere un PIN semplice, l'autenticazione biometrica come Windows Hello o un dispositivo esterno come un lettore di impronte digitali.

* **VPN per app specifiche** È possibile selezionare app che si connettono automaticamente alla rete aziendale tramite VPN. Creare l'elenco di app quando si configura il profilo VPN, come descritto in Consentire agli utenti di connettersi al proprio lavoro tramite profili VPN con Microsoft Intune.

* **Supporto della cancellazione completa di Windows 10** È ora possibile eseguire una cancellazione remota completa nei dispositivi desktop Windows 10 registrati in Intune con la console di amministrazione di Intune. La cancellazione completa di Windows 10 esegue un ripristino delle impostazioni predefinite del dispositivo.


### Aggiornamento di Volume Purchase Program (VPP) di Apple
Intune consente ora di [gestire le app acquistate attraverso il Volume Purchase Program (VPP) di Apple per aziende](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Ciò include la sincronizzazione delle informazioni di licenza tra Apple e Intune e la verifica del numero di copie di ogni app distribuito.

### Usare i numeri IMEI per identificare i dispositivi di proprietà dell'azienda
È ora possibile [importare i numeri IMEI (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) per le piattaforme per dispositivi mobili dotate di un numero IMEI per identificare i dispositivi mobili aziendali. Una volta registrati in Intune, i dispositivi con numeri IMEI importati vengono contrassegnati come aziendali, che possono essere usati per l'applicazione di criteri diversi da quelli applicati ai dispositivi personali.

### Un numero maggiore di app è ora compatibile con i criteri MAM di Intune
Le app aggiuntive dei partner Microsoft sono ora compatibili con i criteri di gestione di applicazioni mobili di Intune (MAM) per i dispositivi gestiti da Intune:
* Box for EMM (di Box Inc): solo iOS
* Adobe Reader (di Adobe): solo Android
* Foxit PDF Reader (di Foxit Corporation): iOS e Android


### Il supporto di Internet Explorer 9 termina a gennaio
A partire da febbraio 2016, Internet Explorer 9 non verrà più supportato come browser ufficiale per l'accesso al sito Web del portale aziendale di Microsoft Intune, al portale per gli account di Intune e alla console di amministrazione di Intune. Sarà necessario eseguire la migrazione a Internet Explorer 10 o versioni successive.

## Dicembre 2015
### Modifiche e aggiornamenti del portale aziendale Microsoft
In questa versione sono state apportate le modifiche seguenti al portale aziendale.

**App Portale aziendale Android**

Sono state apportate le modifiche seguenti ai fini della conformità con i nuovi requisiti di Google. Nei dispositivi con Android 6.0 e versioni successive, vengono visualizzati due nuovi messaggi agli utenti:
* Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?
* Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?

Per informazioni dettagliate su questi due messaggi vedere le tabelle seguenti.



Testo del messaggio  |Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?  
---------|---------
Significato del messaggio     |  Consente l'invio del numero di telefono e del codice IMEI del dispositivo dell'utente al servizio Intune e la relativa visualizzazione nella console di amministrazione nella pagina Hardware.   </br></br>**NOTA: l'app Portale aziendale non effettua o gestisce mai chiamate telefoniche.** Il testo del messaggio è controllato da Google e non può essere modificato. </br></br>Per visualizzare la pagina **Hardware**, accedere a **Gruppi** > **Tutti i dispositivi mobili** > **Dispositivi**. Selezionare il dispositivo dell'utente e passare a **Visualizza proprietà** > **Hardware**.    
Dove e quando viene visualizzato il messaggio  | Il messaggio viene visualizzato quando l'utente accede per la prima volta all'app Portale aziendale per iniziare la registrazione del dispositivo.|         
Cosa accade se gli utenti consentono l'accesso  |  Il numero di telefono e il codice IMEI del dispositivo verranno visualizzati nella pagina Hardware nella console di amministrazione. |         
Cosa accade se gli utenti negano l'accesso     | Possono continuare a usare l'app Portale aziendale e registrare il dispositivo, ma il numero di telefono e il codice IMEI del loro dispositivo non compariranno nella pagina Hardware nella console di amministrazione.       </br></br> Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio.</br></br>Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato al successivo accesso all'app Portale aziendale dopo la registrazione.</br></br>Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.
Altre informazioni     |  Per gli utenti: [Accedere al Portale aziendale](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>Per i professionisti IT: le informazioni contenute in questa tabella sono disponibili anche in [Aiutare gli utenti a comprendere i messaggi dell'app Portale aziendale](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   

Testo del messaggio  |Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?  
---------|---------
Significato del messaggio     |  Consente al dispositivo di scrivere log di dati nella scheda SD del dispositivo, in modo da rendere possibile lo spostamento dei log tramite un cavo USB.   </br></br>**NOTA: l'app Portale aziendale non accede mai a foto, elementi multimediali e file degli utenti.** Il testo del messaggio è controllato da Google e non può essere modificato.     
Dove e quando viene visualizzato il messaggio  | Il messaggio viene visualizzato quando gli utenti toccano **Invia dati** per inviare i log di dati al loro amministratore IT.|         
Cosa accade se gli utenti consentono l'accesso  |  I log verranno copiati nella scheda SD. |         
Cosa accade se gli utenti negano l'accesso     | Possono comunque inviare i log di dati, ma questi non verranno copiati nella scheda SD del dispositivo.       </br></br> Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio.</br></br>Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato al successivo tentativo di invio dei log.</br></br>Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Archiviazione** e quindi attivare l'autorizzazione.
Altre informazioni     |  Per gli utenti: [Inviare i log dei dati di diagnostica all'amministratore IT tramite posta elettronica](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>Per i professionisti IT: le informazioni contenute in questa tabella sono disponibili anche in [Aiutare gli utenti a comprendere i messaggi dell'app Portale aziendale](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   


**App del portale aziendale iOS**
* Gli utenti possono ora usare Microsoft Outlook o altre app di posta elettronica per inviare i log di diagnostica all'amministratore IT. In precedenza, era possibile usare solo l'app nativa.
* Il supporto è stato migliorato per i dispositivi del programma di registrazione dispositivi (DEP) di Apple e per i dispositivi registrati dall'azienda. Per informazioni dettagliate, vedere [Viene richiesto di identificare il dispositivo durante il tentativo di registrazione](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* Nell'elenco dei dispositivi registrati dell'utente viene ora visualizzato un segno di spunta verde accanto al dispositivo attualmente in uso. Prima dell'aggiunta del segno di spunta, non era possibile per gli utenti stabilire quale dispositivo registrato stavano usando.

**App Portale aziendale Windows**

Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso del Portale aziendale per migliorare prodotti e servizi Microsoft. Gli utenti finali possono disattivare la raccolta dati tramite l'impostazione relativa ai dati di uso del dispositivo. Tuttavia, gli amministratori non dispongono di controllo sulla raccolta dati e non possono modificare la selezione dell'utente relativa a questa impostazione.



## Novembre 2015
### Gestione delle app
Intune supporta criteri di gestione delle applicazioni mobili (MAM) che consentono di impedire la divulgazione dei dati aziendali alle app o ai servizi consumer. In passato, questi criteri venivano applicati solo nelle app mobili in esecuzione nei dispositivi che erano registrati anche per la gestione dei dispositivi mobili (MDM) in Intune.

Con l'aggiornamento di questo mese, Intune estende le sue funzionalità MAM a nuove classi di dispositivi. Oltre ai dispositivi registrati in Intune, è possibile ora applicare i criteri MAM in:
* dispositivi gestiti da qualsiasi altra soluzione di gestione dei dispositivi (MDM)
* dispositivi che non sono registrati in nessun sistema di gestione del dispositivo, in genere dispositivi personali (BYO)

Altre informazioni su queste nuove funzionalità MAM sono disponibili nei seguenti post di blog:
* [Miglioramento della produttività dei dispositivi mobili gestiti](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Annuncio delle nuove funzionalità di Microsoft Enterprise Mobility](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Di seguito sono evidenziate e ulteriormente illustrate alcune funzionalità MAM di Intune:
* I dati aziendali sono isolati dai dati consumer all'interno di applicazioni abilitate per Intune, tra cui App Office Mobile, app di terze parti che hanno adottato l'SDK di Intune o app line-of-business integrate in Intune.
* I dati aziendali possono essere condivisi (**Taglia/Copia/Incolla**) tra le app aziendali, impedendo la condivisione dei dati aziendali in app personali. Per altre informazioni, leggere [Protezione dei dati delle app con i criteri MAM](https://technet.microsoft.com/library/mt627825.aspx). Questo scenario di esempio, [Uso dell'app Microsoft Word per attività professionali e personali](https://technet.microsoft.com/library/mt627827.aspx), illustra come impedire la condivisione di dati aziendali nelle app personali.
* Criteri chiave di prevenzione della perdita di dati, come PIN per app, controlli salvataggio con nome e condivisione di dati gestiti tra app. Per vedere un elenco di tutti i criteri, leggere [Creare e distribuire i criteri di gestione delle app mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Word, Excel, PowerPoint, Outlook, OneNote e OneDrive for Business sono tutti dotati di queste nuove funzionalità e possono essere gestiti con o senza la registrazione del dispositivo. Le funzionalità di protezione dalla perdita di dati sono incorporate in modo nativo nelle app Office standard nell'Apple Store o in Google Play Store e non richiedono il wrapping o il sideload delle app.
* Per informazioni su come iniziare, vedere [Introduzione ai criteri di gestione delle app mobili nel portale di Azure](https://technet.microsoft.com/library/mt627830.aspx). Per informazioni su come configurare e distribuire i criteri di gestione di applicazioni mobili, vedere [Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Quando gli utenti finali si autenticano nell'app con le proprie credenziali aziendali, le funzionalità di protezione da perdita di dati vengono configurate automaticamente. L'argomento [Esperienza dell'utente finale per le app associate ai criteri di gestione delle app per dispositivi mobili di Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx) contiene alcuni scenari di esempio di accesso a OneDrive nei dispositivi iOS e Android.
* Funziona nei dispositivi iOS e Android.

L'elenco delle [app Microsoft che è possibile usare con i criteri di gestione delle applicazioni mobili di Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx) è stato aggiornato con le app più recenti.

### Gestione dei dispositivi
 **Gestione dei dispositivi Mac OS X** Con Intune ora è possibile registrare e gestire i dispositivi Mac OS X. Con i dispositivi Mac OS X è possibile eseguire le operazioni seguenti:
* Registrare i dispositivi da gestire in Intune. Vedere [Configurare la gestione dei dispositivi iOS con Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx).
* Controllare le impostazioni del dispositivo con un criterio di configurazione generale. Vedere [Impostazioni dei criteri di configurazione di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Distribuire le impostazioni di Mac OS X create con Apple Configurator. Vedere [Impostazioni dei criteri personalizzati di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Raccogliere l'inventario hardware e software dai dispositivi Mac OS X. Vedere [Informazioni sui dispositivi con inventario in Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx).
* Eseguire nuovi report che mostrino i dettagli sui dispositivi Mac OS X gestiti. Vedere [Comprendere le operazioni di Microsoft Intune con l'uso dei report](https://technet.microsoft.com/library/dn646977.aspx).

**Nuove impostazioni del browser Edge per i dispositivi Windows 10** Sono state aggiunte ai criteri di configurazione generale di Windows 10 nuove impostazioni che consentono di gestire le impostazioni e le funzionalità del browser Microsoft Edge. Vedere [Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx).

**Profili di posta elettronica** È stato aggiunto un nuovo criterio dei profili di posta elettronica per i dispositivi Windows 10 Desktop e Windows 10 Mobile. Vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](https://technet.microsoft.com/library/dn646984.aspx).

**Nuove impostazioni dei criteri di conformità** Sono state aggiunte le seguenti nuove impostazioni di sicurezza e dei criteri di sistema all'elenco dei criteri di conformità:
* Per accertarsi che nei dispositivi con Windows 8.1 o versioni successive che accedono alle risorse aziendali siano installati gli ultimi aggiornamenti, usare l'impostazione **Richiedi aggiornamenti automatici**. È anche possibile specificare il tipo di aggiornamenti da installare automaticamente, contrassegnandoli tutti come importanti o consigliati. Per l'elenco completo delle impostazioni dei criteri di conformità, vedere [Gestire criteri di conformità del dispositivo per Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx).
* La nuova impostazione **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività** combinata all'impostazione **Minuti di inattività prima che venga richiesta la password** esistente consente di creare un'impostazione di conformità che richiede all'utente finale di immettere una password per usare un dispositivo che è rimasto inattivo per un determinato periodo di tempo.

**Nuove opzioni dei criteri di accesso condizionale** È possibile applicare criteri di accesso condizionale a **tutti gli utenti** nei criteri di accesso condizionale nuovi o esistenti. A tutti gli utenti con licenza per Intune e Office 365 verrà richiesto di registrare i propri dispositivi e, se la piattaforma del dispositivo non è supportata da Intune, l'accesso è bloccato per le applicazioni client che usano [l'accesso basato sull'autenticazione di Active Directory (autenticazione moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/).

È anche possibile specificare che venga applicato il criterio di accesso condizionale a **tutte le piattaforme**.  Tutte le applicazioni client che usano l'[accesso basato sull'autenticazione di Active Directory (autenticazione moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) sono soggette ai criteri di accesso condizionale e, se la piattaforma non è supportata da Intune, verranno bloccate.

### Modifiche e aggiornamenti del portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale:

* **Android**: è stata aggiunta una schermata di benvenuto all'app del portale aziendale Android per aiutare gli utenti a comprenderne lo scopo. Questa schermata mira a ridurre i download dell'app da parte degli utenti le cui le aziende non sono sottoscrittori Intune.

* **iOS**: Intune supporta ora la registrazione di dispositivi Mac OS X con il [sito Web del portale aziendale](https://portal.manage.microsoft.com). Per istruzioni, vedere [Registrare il dispositivo Mac OS X in Intune](https://technet.microsoft.com/library/mt598622.aspx).

* **Sito Web del portale aziendale**: gli utenti che hanno registrato il dispositivo in Intune possono ora reimpostare il passcode con l'opzione **Reimposta passcode** nel sito Web del portale aziendale. In precedenza, solo gli amministratori IT potevano ripristinare i passcode degli utenti. L'opzione Reimposta passcode non è supportata nei dispositivi Windows 8.1 e Windows RT e viene visualizzata solo quando i dispositivi sono registrati in una soluzione di gestione dei dispositivi mobili (MDM) o in MDM con Exchange ActiveSync. Per istruzioni per gli utenti, vedere [Reimpostare il passcode](https://technet.microsoft.com/library/mt590895.aspx).

### Modifiche alle licenze degli amministratori globali
Nel mese di ottobre, è stato annunciato che gli amministratori globali (noti anche come amministratori tenant) potevano continuare a eseguire attività di ordinaria amministrazione senza una licenza separata di Intune o Enterprise Mobility Suite (EMS). Tuttavia, se gli amministratori globali vogliono usare il servizio, ad esempio per registrare il proprio dispositivo, un dispositivo aziendale oppure usare il portale aziendale di Intune, avranno bisogno di una licenza Intune o EMS, esattamente come qualsiasi altro utente. Di seguito sono riportati alcuni dettagli aggiuntivi.
* Nel portale aziendale di Intune gli utenti finali possono:
    * iscrivere il proprio dispositivo
    * visualizzare lo stato del dispositivo
    * scaricare il software distribuito da un amministratore globale all'organizzazione
    * trovare i collegamenti pubblicati dall'amministratore globale per informazioni su come contattare il reparto IT

    [Altre informazioni sul portale aziendale](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) e su [come personalizzare il portale aziendale](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* La persona che effettua l'iscrizione per l'acquisto di Intune o EMS per conto di un'organizzazione diventa automaticamente il primo amministratore globale nel tenant. Quest'autunno, Intune ha iniziato ad assegnare automaticamente una licenza di Intune o EMS al primissimo amministratore globale, come parte del passaggio al [portale di Office 365](http://portal.office.com/) e la disattivazione del [Portale per gli account di Intune](http://account.manage.microsoft.com/). Tutti gli altri amministratori globali aggiunti possono continuare a usare l'amministrazione quotidiana senza una licenza separata di Intune o EMS. Agire da utente finale e registrare il dispositivo personale (o aziendale) o scaricare software dal portale aziendale comporterà la necessità di una licenza, esattamente come qualsiasi altro utente.
* La modifica verrà gradualmente implementata a partire da gennaio 2016.
* Per i Partner Microsoft, questa modifica non dovrebbe incidere sulla possibilità di amministrare il servizio per conto dei clienti. Per le attività dell'utente finale, un utente dovrà avere una licenza Intune o EMS per poter registrare un dispositivo e accedere al software o scaricarlo dal portale aziendale.

In caso di domande su questa modifica, è possibile contattare il team di supporto di Intune:
* [Canali di supporto di Microsoft Intune](https://technet.microsoft.com/library/jj839713.aspx)
* [Supporto della community](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Per commenti generali su Microsoft Intune, tra cui la creazione di richieste di modifica del design (DCR, Design Change Request) o di bug, visitare l'apposito [sito per i commenti degli utenti di Intune](https://microsoftintune.uservoice.com/).


### Novità nella documentazione di Intune - Novembre 2015
**Nuovo contenuto**
* [Impostazioni dei criteri di configurazione di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): come controllare le impostazioni e le funzionalità dei dispositivi Mac OS X.
* [Impostazioni dei criteri personalizzati di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): come distribuire le impostazioni del dispositivo Mac OS X create con lo strumento Apple Configurator.
* [Configurare i criteri delle app per la prevenzione della perdita di dati con Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): contiene informazioni sugli scenari supportati dai criteri di gestione delle app mobili e sul funzionamento dei criteri per la protezione dei dati.
* [Introduzione ai criteri di gestione delle app per dispositivi mobili nel portale di Azure](https://technet.microsoft.com/library/mt627830.aspx): informazioni necessarie per iniziare a usare il portale di anteprima di Azure per i criteri di gestione delle app mobili.
* [Creare e distribuire i criteri di gestione delle app mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): contiene una procedura dettagliata su come creare criteri di gestione delle app mobili nel portale di anteprima di Azure.
* [Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): informazioni su come è possibile monitorare i criteri di gestione delle app mobili con il portale di anteprima di Azure.
* [Criteri di gestione delle app per dispositivi mobili di Microsoft Intune e funzionalità Open In di iOS](https://technet.microsoft.com/library/mt627821.aspx): informazioni sul funzionamento dei criteri di gestione delle app mobili con la funzionalità Open In di iOS.
* [Esperienza dell'utente finale per le app associate ai criteri di gestione delle app per dispositivi mobili di Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx): informazioni sull'esperienza dell'utente finale quando si usano le app associate ai criteri di gestione delle app mobili.
* [Cancellare i dati dell'app aziendale gestita con Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): come è possibile rimuovere i dati dall'app aziendale.

**Contenuto aggiornato**
* [Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): aggiunte le nuove impostazioni del browser Edge.
* [Configurare la gestione dei dispositivi iOS con Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): aggiunte informazioni su come registrare i dispositivi Mac OS X.
* [Informazioni sui dispositivi con inventario in Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): aggiunte informazioni sull'inventario raccolto dai dispositivi Mac OS X. Aggiornato anche l'argomento con le ultime informazioni per tutte le piattaforme per dispositivi.
* [Comprendere le operazioni di Microsoft Intune con l'uso dei report](https://technet.microsoft.com/library/dn646977.aspx): aggiunte informazioni sui due nuovi report usati per visualizzare informazioni sui dispositivi Mac OS X gestiti.
* [Gestire i criteri di conformità del dispositivo per Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): aggiunte informazioni sui nuovi criteri di conformità per richiedere aggiornamenti automatici e la password quando un dispositivo torna attivo dopo uno stato di inattività.
* [Gestire l'accesso alla posta elettronica con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): aggiunte informazioni sulla capacità di applicare i criteri di accesso condizionale a tutte le piattaforme e a tutti gli utenti.
* [Gestire l'accesso a SharePoint Online con Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): aggiunte informazioni sulla capacità di applicare i criteri di accesso condizionale a tutte le piattaforme e a tutti gli utenti.

## Ottobre 2015

### Aggiornamenti all'accesso condizionale per Exchange locale
**È ora possibile consentire l'accesso alla posta elettronica di Exchange Active Sync per i dispositivi conformi registrati in Intune quando la regola globale di Exchange è impostata su blocco o quarantena** Fino ad ora, per consentire l'accesso alla posta elettronica nei dispositivi registrati e conformi era necessario impostare la regola globale di Exchange predefinita su **Consenti**.

Grazie a questo aggiornamento del servizio, tale impostazione non è più un requisito per l'accesso condizionale. Se l'ambiente Exchange richiede che la regola globale predefinita sia impostata su **Blocco/Quarantena**, è sufficiente selezionare la casella di controllo **Override regola predefinita** nella pagina dei criteri di Exchange locale per l'accesso condizionale. L'argomento [ Gestire l'accesso alla posta elettronica con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) include informazioni dettagliate sulle regole e le notifiche risultanti per l'utente finale.

**Nuova esperienza della quarantena in un solo clic** È stata semplificata l'esperienza per il messaggio di posta elettronica di quarantena in modo da consentire la registrazione in un solo clic. Grazie a questo aggiornamento del servizio, gli utenti finali possono fare clic su un singolo collegamento nel messaggio di posta elettronica di quarantena per completare il processo di registrazione nell'app Portale aziendale.
### Aggiornamenti per la gestione di dispositivi mobili e app
**Android** Tutte le funzionalità di gestione di Intune supportano ora Android 6.0 (Marshmallow) come descritto in questo post di blog relativo al [supporto di 0 giorni di Microsoft Intune per Android Marshmallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)

**iOS** Non è più possibile creare nuove distribuzioni di app nei dispositivi iOS che eseguono una versione precedente a iOS 7.1. Tutte le distribuzioni nei dispositivi che eseguono una versione precedente a iOS 7.1 continueranno a funzionare e ad essere gestite da Intune.

**Windows 10** Intune supporta ora la distribuzione a Windows 10 Universal con il tipo di programma di installazione software **Pacchetto app Windows**. Per informazioni dettagliate e requisiti vedere [Introduzione alla distribuzione dell'app in Microsoft Intune](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Modifiche e aggiornamenti alle app del Portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale: **iOS** Sono stati aggiunti nuovi pulsanti all'app Portale aziendale per rendere più facile agli utenti l'invio di log di diagnostica agli amministratori IT:

|Nome pulsante|Posizione di visualizzazione|
|------------|---------------|
|Report|Messaggi di avviso errore|
|Invia report di diagnostica|Schermata Informazioni dell'app Portale aziendale|


>[!div class="step-by-step"]

>[&larr; **[!div class="step-by-step"]**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Jul16_HO1-->


