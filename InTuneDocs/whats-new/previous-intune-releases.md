---
title: Versioni precedenti | Documentazione Microsoft
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: c2d1a42345af3e57224578df1cc7218b3f326808
ms.lasthandoff: 04/14/2017


---

# <a name="previous-intune-releases"></a>Versioni precedenti di Intune

Questa pagina è un elenco degli annunci pubblicati in [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="july-2016"></a>Luglio 2016

### <a name="app-management"></a>Gestione delle app

__Migliorare l'esperienza di aggiornamento del profilo di provisioning dell'app__ Nelle app per dispositivi mobili line-of-business per Apple iOS sono inclusi un profilo di provisioning e un codice firmato con un certificato. Quando si esegue l'app in un dispositivo iOS, iOS conferma l'integrità dell'app e impone i criteri definiti dal profilo di provisioning.

La durata del certificato di firma dell'organizzazione usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Con questo aggiornamento, Intune offre gli strumenti per distribuire in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza, mentre il certificato è ancora valido. Per altre informazioni, vedere [ Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Usare i criteri del profilo di provisioning per dispositivi mobili iOS per mantenere aggiornate le app line-of-business)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->

__È disponibile Xamarin SDK per app Intune__ Il componente Intune App SDK Xamarin consente di abilitare le funzionalità di gestione delle app per dispositivi mobili Intune nelle app per dispositivi mobili iOS e Android compilate con Xamarin. È possibile trovare il componente nello [Store Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) o nella [pagina di GitHub di Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Gestione dei dispositivi
__Limiti aumentati di registrazione dei dispositivi__ Intune ha aumentato il limite massimo di registrazione dei dispositivi configurabili da 5 a 15 dispositivi per utente.
<!---TFS 1289896 --->

__Integrazione di TeamViewer per PC Windows che eseguono il software client Intune__
L'integrazione di [TeamViewer](https://www.teamviewer.com) per PC Windows che eseguono il client di Intune consente di avviare sessioni di assistenza remota con PC Windows per supportare i reparti Help Desk degli utenti finali. Sono inclusi Windows 7, 8, 8.1 e Windows 10. Per informazioni dettagliate, vedere [Attività comuni di gestione di PC Windows con client di Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale

__Sito Web del portale aziendale__
- **Esperienza dell'utente finale migliorata durante la registrazione di dispositivi Windows**<br/>
Quando si usa l'accesso condizionale, la procedura di registrazione per Windows 8.1, Windows 10 Desktop e Windows 10 Mobile è stata semplificata nel sito Web del portale aziendale. Gli utenti ora visualizzeranno due procedure separate, "Registrazione dispositivi" e "Aggiunta all'area di lavoro". In questo modo sarà più semplice visualizzare lo stato del dispositivo e completare il processo se l'aggiunta all'area di lavoro (WPJ) ha avuto esito negativo. Le procedure separate dovrebbero inoltre semplificare il processo di risoluzione dei problemi per gli amministratori IT. In precedenza, quando gli utenti finali tentavano di registrarsi e tutti i passaggi della registrazione avevano esito positivo eccetto l'aggiunta all'area di lavoro, il dispositivo registrato non veniva visualizzato nell'elenco dei dispositivi per l'identificazione da parte degli utenti, causando confusione.

__Android__
- **App Portale aziendale Android**<br/>
Se gli utenti finali Android visualizzano un messaggio di errore che indica che al dispositivo manca un certificato obbligatorio, è possibile toccare il pulsante per la risoluzione del problema per ottenere la [procedura](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) per l'installazione del certificato mancante. Se gli utenti completano la procedura, ma visualizzano un altro messaggio di errore che indica che manca un certificato, verrà chiesto loro di contattare l'amministratore IT e fornirgli questo [collegamento](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), che contiene la procedura che gli amministratori IT possono usare per risolvere il problema del certificato.

- **Limitare l'installazione di app con trasferimento in locale in dispositivi registrati**<br/>
Nei dispositivi Android non è più possibile installare applicazioni tramite il sito Web del portale aziendale, a meno che i dispositivi siano stati registrati in Intune tramite l'app Portale aziendale per Android.
<!---TFS 1299082--->

__iOS__
- **Modifiche agli account Manager di registrazione dei dispositivi nell'app Portale aziendale per iOS**<br/>
Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi (DEM) nel riquadro **Dispositivi personali** dell'app Portale aziendale per iOS. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale.

L'utente di DEM può eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati può essere effettuata solo dalla console di amministrazione di Intune. In Intune verrà anche deprecato l'uso degli account DEM con il programma di registrazione dispositivi di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione supportano già la registrazione senza utente per i dispositivi iOS condivisi.

Usare gli account DEM solo se non è disponibile la registrazione senza utente per i dispositivi condivisi. Per altre informazioni, vedere [Registrare i dispositivi di proprietà dell'azienda con Manager di registrazione dispositivi in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Modifica dei nomi delle funzionalità Windows
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) è ora noto come **Windows Hello for Business**.
- [Protezione dei dati aziendali](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) è ora noto come **Windows Information Protection**.


## <a name="june-2016"></a>Giugno 2016
### <a name="intune-service-health"></a>Integrità del servizio Intune
Le informazioni sull'integrità del servizio per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel portale di gestione di Office 365 in Integrità dei servizi. Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Gestione delle app
- **Esperienza avanzata di configurazione dei criteri di dati aziendali di Windows 10.** Sono stati apportati miglioramenti all'esperienza di configurazione dei criteri di protezione dei dati aziendali di Windows 10 con la creazione di regole di app, la definizione di limiti di rete e altre impostazioni di protezione dei dati aziendali. Per altre informazioni, vedere l'articolo relativo alla [creazione di un criterio di protezione dei dati aziendali con Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Gestione dei dispositivi
- **Impostazione di Windows Defender per la protezione da app potenzialmente indesiderate.** È stata aggiunta una nuova impostazione di Windows Defender denominata **Potentially Unwanted Application Detection (Rilevamento di applicazioni potenzialmente indesiderate)** ai criteri di configurazione generali per Windows 10 Desktop e Mobile. È possibile usare questa impostazione per la protezione di computer desktop Windows registrati da eventuale software in esecuzione classificato da Windows Defender come potenzialmente indesiderato. È possibile ottenere protezione da tali applicazioni in esecuzione o usare la modalità di controllo per rilevare l'installazione di un'applicazione potenzialmente indesiderata. Per altre informazioni, vedere [Impostazioni dei criteri di Windows 10 in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Accesso condizionale
- **Criteri di controllo di accesso di rete Cisco ISE per Intune.**  I clienti che usano Cisco Identity Service Engine (ISE) 2.1 e Microsoft Intune possono impostare i criteri di controllo di accesso di rete in ISE.

    Con l'uso di questi criteri, i dispositivi che devono connettersi alla rete tramite Wi-Fi o VPN devono soddisfare le condizioni seguenti prima di consentire l'accesso:

    * Devono essere gestiti da Intune
    * Devono essere compatibili con i criteri di compatibilità di Intune distribuiti

 Agli utenti finali di dispositivi non conformi verrà richiesto di eseguire la registrazione e risolvere eventuali problemi di conformità per ottenere l'accesso.
- **Accesso condizionale per il browser.** È possibile impostare un criterio di accesso condizionale per [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) in modo che siano accessibili solo dai Web browser supportati su dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere a siti di Outlook Web Access (OWA) e SharePoint e con dispositivi iOS e Android verrà richiesto di registrare il dispositivo con Intune oltre che di risolvere eventuali problemi di non conformità prima di poter completare l'accesso.
<!---TFS 1175844--->

- **Dynamics CRM Online supporta l'accesso condizionale.** È possibile impostare un criterio di accesso condizionale per [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) in modo che sia accessibile solo da dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere all'applicazione per dispositivi mobili Dynamics CRM in iOS e Android sarà chiesto di registrarsi con Intune e di risolvere eventuali problemi di non conformità per poter completare l'accesso.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Aggiornamenti del portale aziendale di Intune

__App Portale aziendale Android__

- Se gli amministratori IT applicano il nuovo criterio in base al quale i dispositivi impediscono l'installazione di app da origini sconosciute (Android 4.0 +), gli utenti finali con dispositivi Android 4.0 o versioni successive visualizzano il messaggio "L'installazione da origini sconosciute deve essere disabilitata". Gli utenti dovranno passare a  **Impostazioni** > **Sicurezza** e disattivare **Origini sconosciute**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sul messaggio e di sapere perché viene richiesta la disattivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio in base al quale i dispositivi devono abilitare la ricerca di minacce per la sicurezza nelle app (Android 4.0 +), gli utenti finali con dispositivi Android 4.0 o versioni successive visualizzano il messaggio "Cerca minacce per la sicurezza nel dispositivo". Gli utenti dovranno passare a **Impostazioni** > **Google** > **Sicurezza** e attivare **Cerca minacce per la sicurezza nel dispositivo**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sul messaggio e di sapere perché viene richiesta l'attivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio in base al quale il debug USB deve essere disabilitato (Android 4.2 +), gli utenti finali con dispositivi Android 4.2 o versioni successive visualizzano il messaggio "Il debug USB deve essere disabilitato". Gli utenti dovranno passare a **Impostazioni** > **Opzioni per gli sviluppatori** e disattivare **Debug USB**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sul messaggio e di sapere perché viene richiesta la disattivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio relativo al livello minimo di patch di protezione per Android (Android 6.0 +), gli utenti finali con dispositivi Android 6.0 o versioni successive visualizzano il messaggio "Questo dispositivo non rispetta il livello minimo di patch di protezione per Android". Gli utenti dovranno installare la patch di protezione richiesta. Un collegamento nel messaggio di conformità consente agli utenti di ottenere [informazioni](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) su come installare la patch di protezione richiesta e di vedere quale patch di protezione è attualmente installata.

__App Portale aziendale iOS__

- Durante l'installazione delle applicazioni line of business ora gli utenti finali vedranno un'esperienza di installazione delle app migliorata. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- L'app Portale aziendale di Microsoft Intune per iOS è stata aggiornata per supportare iOS versione 8.0 e successive. Questo aggiornamento significa che gli utenti finali possono installare l'app Portale aziendale e registrare i nuovi dispositivi in Intune solo se il dispositivo esegue iOS versione 8.0 o successiva. Gli utenti che hanno già iscritto dispositivi che eseguono una versione non supportata di iOS possono continuare a utilizzare l'app portale aziendale sul dispositivo.

## <a name="may-2016"></a>Maggio 2016
Tutte queste funzionalità sono supportate anche per le distribuzioni ibride (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la pagina delle [Novità per le funzionalità ibride](https://technet.microsoft.com/library/mt718155.aspx).

### <a name="documentation"></a>Documentazione
Benvenuti nella versione di anteprima di [docs.microsoft.com](https://docs.microsoft.com/intune).
Questa piattaforma moderna completamente nuova è stata progettata per rendere più semplice per i nostri clienti comprendere e usare Intune.
Per informazioni su tutte le nuove funzionalità, vedere [Introducing docs.microsoft.com (Introduzione a docs.microsoft.com)](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### <a name="intune-service-health"></a>Integrità del servizio Intune
Le informazioni sull'integrità del servizio per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) in **Integrità dei servizi**.
Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Gestione delle app
- **MAM SDK: supporto per la configurazione della lunghezza del PIN.** Sarà possibile specificare la lunghezza del PIN per le app MAM in modo simile al PIN di un dispositivo. Gli utenti finali dovranno perciò conformarsi alle nuove limitazioni imposte. Vedranno la schermata del PIN leggermente modificata per tenere conto della lunghezza del PIN. Per informazioni dettagliate, vedere [Impostazioni dei criteri di gestione delle app per dispositivi mobili Android in Microsoft Intune](/intune/deploy-use/android-mam-policy-settings) e [Impostazioni dei criteri di gestione delle app per dispositivi mobili per iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype for Business per iOS e Android.** È ora possibile scegliere come destinazione Skype for Business con [MAM senza criteri di registrazione](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Dopo la connessione degli utenti, verranno applicati i criteri MAM.

- **Sono disponibili nuove app per la gestione con criteri MAM.** Le app Microsoft Word, Excel e PowerPoint per Android possono ora essere associate a criteri MAM su dispositivi non registrati in Intune. Per visualizzare l'elenco completo delle app supportate, passare alla raccolta di applicazioni per dispositivi mobili di Microsoft Intune nella pagina dei [partner di Microsoft Intune](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).


### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale

#### <a name="android-company-portal-app"></a>App Portale aziendale Android
- **Notifiche di tipo avviso popup per l'utente finale**: per gli utenti finali che registrano un dispositivo o lo rimuovono dal Portale aziendale vengono visualizzate notifiche di tipo avviso popup dell'app Portale aziendale per Android.

- **Modifiche agli account Manager di registrazione dispositivi nell'app Portale aziendale per Android.** Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro Dispositivi personali dell'app Portale aziendale per Android. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.

#### <a name="company-portal-website"></a>Sito Web del portale aziendale
- **Sito Web del portale aziendale: il banner di identificazione del dispositivo offrirà maggiori informazioni agli utenti finali.** Gli utenti finali possono ora identificare facilmente il dispositivo selezionato durante l'uso del sito Web del portale aziendale. Se viene selezionato il dispositivo errato, gli utenti potranno selezionare il dispositivo corretto toccando il collegamento **Tocca qui** nel banner della pagina iniziale.

### <a name="service-deprecation"></a>Deprecazione del servizio
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


## <a name="april-2016"></a>Aprile 2016
Tutte queste funzionalità sono supportate anche per i clienti ibridi (Configuration Manager con Intune).

### <a name="app-management"></a>Gestione delle app
- **Conformità utente MAM.**
È ora possibile visualizzare lo [stato](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune) dei criteri di gestione delle applicazioni per ogni utente del tenant Azure Active Directory (AAD). Sono inclusi:
   - Dispositivi
   - App sul dispositivo

   Valori di stato:

   **Archiviato**: indica che il criterio è stato distribuito all'utente, l'app è stata usata nel contesto di lavoro e ha ricevuto correttamente i criteri.

    **Non archiviato**: indica che il criterio è stato distribuito all'utente, ma da quel momento l'app non è mai stata usata nel contesto di lavoro.


- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (Android).**
È disponibile una nuova impostazione per la [gestione delle applicazioni per dispositivi mobili](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) senza registrazione del dispositivo. Questa impostazione consente di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi Android. Quando l'impostazione è abilitata, le applicazioni di destinazione non possono più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, le applicazioni di destinazione possono salvare i contatti nella rubrica nativa. Quando [si cancella un dispositivo o un'app da remoto](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune), tutti i contatti che sono già stati salvati nella rubrica nativa vengono rimossi. Questa nuova impostazione è supportata inizialmente dall'applicazione Outlook sui dispositivi Android.

### <a name="device-management"></a>Gestione dei dispositivi
- **Identificazione del numero di telefono per i dispositivi aziendali.** I telefoni classificati come "aziendali" sono ora identificati con il loro numero di telefono completo quando, per esempio, si esegue un report inventario dei dispositivi mobili. I numeri di telefono BYOD continuano a essere mascherati con **** mostrando solo le ultime 4 cifre.


### <a name="company-portal-updates"></a>Aggiornamenti del Portale aziendale
Gli utenti di **app del Portale aziendale Android** che non hanno registrato il loro dispositivo in Intune e non hanno il certificato corretto installato non potranno accedere all'app del Portale aziendale Android e vedranno il messaggio "Non è possibile accedere. Manca un certificato necessario per il dispositivo". Il messaggio include il collegamento “Risoluzione del problema” che gli utenti possono usare per vedere le istruzioni per l'installazione del certificato. Per i passaggi che gli utenti finali devono eseguire per risolvere il problema vedere [Manca un certificato necessario per il dispositivo](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**App Portale aziendale iOS** È stato aggiunto il supporto per l'azione di scorrimento per aggiornare il contenuto della schermata iniziale, che include le app e i dispositivi elencati e le informazioni di contatto IT. L'azione di scorrimento per l'aggiornamento non controlla la conformità o le informazioni sui criteri, cosa che si può fare selezionando il riquadro per il dispositivo corrente e toccando il pulsante **Sincronizza**.

**App Portale aziendale per Windows 10 Mobile e Windows Phone 8.1** Il processo di installazione delle app line-of-business è stato migliorato. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo manualmente per velocizzare l'installazione delle app](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sito Web Portale aziendale** Durante l'installazione delle app line-of-business, gli utenti di Windows 10 Mobile e Windows Phone 8.1 vedranno ora i seguenti stati nuovi, che specificano maggiori dettagli sullo stato della loro installazione:

* **In attesa della sincronizzazione del dispositivo**: l'utente ha toccato “Installa” e il dispositivo ora tenta di sincronizzarsi con l'infrastruttura Intune. La sincronizzazione è necessaria per poter completare l'installazione. Il messaggio "In attesa della sincronizzazione del dispositivo" è anche un collegamento che gli utenti possono toccare per vedere le [istruzioni](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) per sincronizzare manualmente il dispositivo con Intune, se il processo di sincronizzazione impiega troppo tempo o si blocca.
* **Download in corso**: la richiesta di download dell'utente è in fase di elaborazione e il dispositivo sta scaricando e installando l'app.

Prima dell'aggiunta di questi stati, gli utenti potevano essere confusi se l'installazione di un'app impiegava molto tempo, poiché vedevano solo lo stato "Installazione in corso", che poteva rimanere visualizzata sullo schermo per ore. Grazie all'aggiunta dei nuovi stati gli utenti, invece di chiamare il supporto, possono ora toccare il collegamento "In attesa della sincronizzazione del dispositivo" e seguire le istruzioni per forzare la ripresa del processo di sincronizzazione.

>[!div class="step-by-step"]

>[&larr; **Novità in Intune**](whats-new-in-microsoft-intune.md)    

