# <a name="february-2017"></a>Febbraio 2017

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="modernizing-the-company-portal-website---753980--"></a>Aggiornamento del sito Web del portale aziendale <!--753980-->
Il sito Web del portale aziendale supporterà le app destinate agli utenti che non hanno dispositivi gestiti. Il sito Web verrà allineato ad altri prodotti e servizi Microsoft tramite una nuova combinazione di colori a contrasto, illustrazioni dinamiche e un "hamburger menu" ![immagine di "hamburger menu" di piccole dimensioni inserita nell'angolo superiore sinistro del sito Web del portale aziendale](/intune/whats-new/media/CP_hamburger_menu.png) che conterrà i dettagli di contatto del supporto tecnico e le informazioni sui dispositivi gestiti esistenti. La pagina di destinazione verrà riorganizzata per evidenziare le applicazioni disponibili per gli utenti, con sequenze video per le app in primo piano e aggiornate di recente. Le immagini di prima e dopo sono disponibili nella [pagina degli aggiornamenti dell'interfaccia utente](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Nuova esperienza guidata per il portale aziendale di Windows 10 <!--713927-->
A partire da marzo, il portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate e personalizzate, per la compilazione di Windows 10 in uso, che guidano l'utente nella procedura di registrazione AAD (obbligatoria per l'identificazione per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale ed è facoltativa. Gli utenti possono continuare a usare l'app anche se non completano la registrazione, ma potrebbero disporre di funzionalità limitate.

## <a name="notices"></a>Notifiche

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migrazione dei gruppi non richiederà aggiornamenti ai gruppi o ai criteri per i dispositivi iOS <!--898837-->
Per ogni gruppo di dispositivi Intune preassegnato da un profilo Registrazione di dispositivi aziendali, verrà creato un gruppo di dispositivi dinamico corrispondente in AAD basato sul nome del profilo Registrazione di dispositivi aziendali durante la migrazione ai gruppi di dispositivi di Azure Active Directory. In questo modo i dispositivi registrati vengono raggruppati automaticamente e ricevono gli stessi criteri e le stesse app del gruppo Intune originale.

Quando un tenant entra nel processo di migrazione per la creazione del gruppo e la selezione della destinazione, Intune crea automaticamente un gruppo AAD dinamico corrispondente a un gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali. Se l'amministratore Intune elimina il gruppo Intune di destinazione, il gruppo AAD dinamico corrispondente non viene eliminato. I membri del gruppo e la query dinamica vengono cancellati, ma il gruppo viene mantenuto fino a quando l'amministratore IT non lo rimuove tramite il portale AAD.

Analogamente, se l'amministratore IT modifica il gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali, Intune crea un nuovo gruppo dinamico che riflette la nuova assegnazione del profilo ma non rimuove il gruppo dinamico creato per l'assegnazione precedente.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>La gestione dei dispositivi desktop Windows avviene per impostazione predefinita tramite le impostazioni di Windows <!--663050-->
Il comportamento predefinito per la registrazione dei computer desktop di Windows 10 sta cambiando. Per le nuove registrazioni verrà usato il flusso di registrazione dell'agente MDM tipico anziché tramite l'agente per PC. Il sito Web del portale aziendale fornirà agli utenti di desktop Windows 10 istruzioni per la registrazione, che consentono di eseguire in modo guidato il processo di aggiunta di computer desktop Windows 10 come dispositivi mobili. Ciò non influirà su PC già registrati e l'organizzazione può comunque decidere di gestire i desktop Windows 10 con l'agente per PC, [se preferibile](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Miglioramento del supporto della gestione delle app per dispositivi mobili per la cancellazione selettiva <!--581242-->
Gli utenti finali riceveranno ulteriori indicazioni su come riottenere l'accesso ai dati aziendali o dell'istituto di istruzione se i dati vengono rimossi automaticamente a causa del criterio "Intervallo offline (giorni) prima della cancellazione dei dati dell'app".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>I collegamenti al portale aziendale per iOS si aprono all'interno dell'app <!--665954-->
I collegamenti all'interno dell'app Portale aziendale per iOS, inclusi quelli per la documentazione e le app, verranno aperti direttamente nell'app Portale aziendale tramite una visualizzazione in-app di Safari. Questo aggiornamento verrà fornito separatamente rispetto all'aggiornamento del servizio in gennaio.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nuovo indirizzo del server MDM per i dispositivi Windows <!--893007-->
Gli utenti di Windows e Windows Phone che tentano di registrare un dispositivo non riusciranno a eseguire la registrazione se immettono __manage.microsoft.com__ come indirizzo del server MDM (se richiesto). L'indirizzo del server MDM __manage.microsoft.com__ è sostituito da __enrollment.manage.microsoft.com__. Comunicare agli utenti di immettere __enrollment.manage.microsoft.com__ come indirizzo del server MDM per la registrazione di un dispositivo Windows o Windows Phone. Non sono necessarie modifiche alla configurazione CNAME. Per altre informazioni su questa modifica, visitare [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622-->
A partire da marzo, l'app Portale aziendale per Android seguirà le [linee guida di progettazione dei materiali](https://material.io/guidelines/material-design/introduction.html) per creare un aspetto più moderno. La nuova esperienza utente include i seguenti miglioramenti:

* __Colori__: i colori delle intestazioni delle schede possono essere impostati in base alla tavolozza dei colori personalizzata.
* __Interfaccia__: i pulsanti App in evidenza e Tutte le app sono stati aggiornati nella scheda App. Il pulsante Cerca è ora un pulsante di azione mobile.
* __Navigazione__: Tutte le app mostra una visualizzazione a schede di In evidenza, Tutte e Categorie per una navigazione più semplice.
* __Servizio__: la leggibilità delle schede Dispositivi personali e Contatta l'IT è stata migliorata.

Le immagini di prima e dopo sono disponibili nella [pagina degli aggiornamenti dell'interfaccia utente](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Associare più strumenti di gestione con Windows Store per le aziende <!--926135-->
Se si usa più di uno strumento di gestione per distribuire le app di Windows Store per le aziende, in precedenza era possibile associare soltanto un'app a Windows Store per le aziende. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager. Per informazioni dettagliate, vedere [Gestire le app acquistate in Windows Store per le aziende con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novità dell'anteprima pubblica dell'esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/whats-new).

Le novità dell'anteprima di Intune in Azure sono descritte [qui](https://docs.microsoft.com/intune-azure/introduction/whats-new).

## <a name="january-2017"></a>Gennaio 2017

### <a name="new-capabilities"></a>Nuove funzionalità

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Report nella console per MAM senza registrazione <!--677961-->
Sono stati aggiunti nuovi report relativi alla protezione delle app, sia per i dispositivi registrati che per quelli non registrati. Per altre informazioni in merito, vedere [Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

#### <a name="android-711-support---694397--"></a>Supporto per Android 7.1.1 <!--694397-->
Intune ora supporta completamente Android 7.1.1 e la relativa gestione.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Risolvere il problema laddove i dispositivi iOS non sono attivi o la console di amministrazione non riesce a comunicare con i dispositivi <!--unknown-->
Quando i dispositivi degli utenti perdono la connessione con Intune è possibile indicare nuovi passaggi per la risoluzione dei problemi per ripristinare l'accesso alle risorse aziendali. Vedere [I dispositivi sono inattivi o la console di amministrazione non è in grado di comunicare con i dispositivi](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="notices"></a>Notifiche

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>La gestione dei dispositivi desktop Windows avviene per impostazione predefinita tramite le impostazioni di Windows <!--663050-->
Il comportamento predefinito per la registrazione dei computer desktop di Windows 10 sta cambiando. Per le nuove registrazioni verrà usato il flusso di registrazione dell'agente MDM tipico anziché tramite l'agente per PC.

Il sito Web del portale aziendale fornirà agli utenti di desktop Windows 10 istruzioni per la registrazione, che consentono di eseguire in modo guidato il processo di aggiunta di computer desktop Windows 10 come dispositivi mobili. Ciò non influirà su PC già registrati e l'organizzazione può comunque decidere di gestire i desktop Windows 10 con l'agente per PC, [se preferibile](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Miglioramento del supporto della gestione delle app per dispositivi mobili per la cancellazione selettiva <!--581242-->
Gli utenti finali riceveranno ulteriori indicazioni su come riottenere l'accesso ai dati aziendali o dell'istituto di istruzione se i dati vengono rimossi automaticamente a causa del criterio "Intervallo offline (giorni) prima della cancellazione dei dati dell'app".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>I collegamenti al portale aziendale per iOS si aprono all'interno dell'app <!--665954-->
I collegamenti all'interno dell'app Portale aziendale per iOS, inclusi quelli per la documentazione e le app, verranno aperti direttamente nell'app Portale aziendale tramite una visualizzazione in-app di Safari. Questo aggiornamento verrà fornito separatamente rispetto all'aggiornamento del servizio in gennaio.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Aggiornamento del sito Web del portale aziendale <!--753980-->
A partire da febbraio, il sito Web del portale aziendale supporterà le app destinate agli utenti che non hanno dispositivi gestiti. Il sito Web verrà allineato ad altri prodotti e servizi Microsoft tramite una nuova combinazione di colori a contrasto, illustrazioni dinamiche e un "hamburger menu" ![hamburger menu del sito Web del portale aziendale](/Intune/whats-new/media/CP_hamburger_menu.png) che conterrà i dettagli di contatto del supporto tecnico e le informazioni sui dispositivi gestiti esistenti. La pagina di destinazione verrà riorganizzata per evidenziare le applicazioni disponibili per gli utenti, con sequenze video per le app in primo piano e aggiornate di recente. È possibile trovare immagini precedenti e successive all'aggiornamento nella pagina [What's new in the Intune app UI page](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui) (Novità nell'interfaccia utente dell'app Intune).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nuova documentazione per i criteri di protezione delle app <!--583398-->
È stata aggiornata la documentazione per gli amministratori e gli sviluppatori di app che vogliono abilitare i criteri di protezione delle app (noti come criteri MAM) nelle loro app iOS e Android usando lo strumento di wrapping delle app di Intune o Intune App SDK.

Sono stati aggiornati gli articoli seguenti:

* [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparare le app per iOS per la gestione delle app mobili con lo strumento di wrapping delle app di Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introduzione a Microsoft Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Manuale dello sviluppatore di Intune App SDK per iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Gli articoli seguenti sono stati aggiunti alla raccolta della documentazione:

* [Plug-in Cordova per Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Componente Xamarin per Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Indicatore di stato quando si avvia l'app Portale aziendale in iOS <!--665978-->
Nell'app Portale aziendale per iOS verrà introdotta una barra di stato nella schermata di avvio per fornire all'utente informazioni sui processi di caricamento eseguiti. L'implementazione della barra di stato in sostituzione dell'indicatore di stato rotante avverrà in modo graduale. Questo significa che alcuni utenti visualizzeranno la nuova barra di stato, mentre altri continueranno a vedere l'indicatore rotante.

## <a name="december-2016"></a>Dicembre 2016

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure <!--736542-->
All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile usando le API Graph. Prima della disponibilità generale di questo portale per tutti i tenant di Intune, siamo lieti di annunciare che verrà introdotta un'anteprima di questa nuova esperienza di amministrazione in seguito durante il mese a tenant selezionati.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, per scoprire cosa abbiamo in serbo per Microsoft Intune nel portale di Azure, vedere la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

__Integrazione con i servizi di gestione delle spese di telecomunicazione nell'anteprima pubblica del portale di Azure__ <!--747605--> Microsoft sta iniziando a presentare in anteprima l'integrazione con i servizi di gestione delle spese di telecomunicazione di terze parti nel portale di Azure. È possibile usare Intune per imporre limiti al consumo dei dati sia nazionale che in roaming. Queste integrazioni iniziano con [Saaswedo](http://www.saaswedo.com). Per abilitare questa funzionalità nel tenant di prova, [contattare il supporto tecnico Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="new-capabilities"></a>Nuove funzionalità

__Autenticazione a più fattori su tutte le piattaforme__ <!--747590--> È ora possibile imporre l'autenticazione a più fattori (MFA) per un gruppo selezionato di utenti durante la registrazione di un dispositivo iOS, Android, Windows 8.1+ o Windows Phone 8.1+ dal portale di gestione di Azure configurando MFA nell'applicazione di registrazione di Microsoft Intune in Azure Active Directory.

__Possibilità di limitare la registrazione dei dispositivi mobili__ <!--747596--> Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.
* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.
* Solo per iOS: è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

### <a name="notices"></a>Notifiche

__Trasferimento di Multi-Factor Authentication per la registrazione nel portale di Azure__ <!--VSO 750545--> Per impostare MFA per le registrazioni in Intune, gli amministratori dovevano usare in precedenza la console di Intune o Configuration Manager (prima della versione di ottobre 2016). Con questa funzionalità aggiornata è ora possibile accedere al [portale di Microsoft Azure](https://manage.windowsazure.com) con le credenziali di Intune e configurare le impostazioni di MFA tramite Azure AD. Per altre informazioni a questo proposito, vedere [qui](https://aka.ms/mfa_ad).

__App Portale aziendale per Android ora disponibile in Cina__ <!--VSO 658093--> L'app Portale aziendale per Android sta per essere pubblicata per il download in Cina. A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere l'app dai marketplace di app cinesi. L'app Portale aziendale per Android sarà disponibile per il download negli store seguenti:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

L'app Portale aziendale per Android usa i servizi Google Play per comunicare con il servizio Microsoft Intune. Dato che i servizi Google Play non sono ancora disponibili in Cina, per completare qualsiasi attività tra le seguenti possono essere richieste fino a 8 ore. 

|Console di amministrazione di Intune| App Portale aziendale di Intune per Android |Sito Web del portale aziendale di Intune|   
|---|---|---|
|Cancellazione completa| Rimozione di un dispositivo remoto| Rimozione di un dispositivo (locale e remoto)|
|Cancellazione selettiva| Reimpostazione del dispositivo| Reimpostazione del dispositivo|
|Distribuzioni di app nuove o aggiornate| Installazione delle app line-of-business disponibili| Reimpostazione del passcode del dispositivo|
|Blocco remoto|||
|Reimpostazione del passcode|||

### <a name="deprecations"></a>Elementi deprecati

__Supporto per Silverlight non più disponibile in Firefox__ <!--VSO TBA--> Mozilla rimuoverà il supporto per Silverlight nella versione 52 del [browser Firefox](https://www.mozilla.org/firefox) a partire da marzo 2017. Di conseguenza, non sarà più possibile accedere alla console di Intune esistente usando versioni di Firefox superiori alla 51. Si consiglia di usare Internet Explorer 10 o 11 per accedere alla console di amministrazione o una [versione di Firefox precedente alla versione 52](https://ftp.mozilla.org/pub/firefox/releases/). La transizione di Intune al portale di Azure consentirà di supportare una serie di [browser moderni](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices) che non dipendono da Silverlight.

__Rimozione dei criteri per le cassette postali per dispositivi portatili di Exchange Online__ <!--770687--> A partire da dicembre, gli amministratori non potranno più visualizzare né configurare i criteri per le cassette postali per dispositivi portatili di Exchange Online (EAS) all'interno della console di Intune. Questa modifica verrà distribuita in tutti i tenant di Intune nel corso di dicembre e gennaio. La configurazione di tutti i criteri esistenti rimarrà invariata. Per la configurazione dei nuovi criteri, usare Exchange Management Shell. Altre informazioni sono disponibili [qui](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

__Supporto per le app Intune AV Player, Image Viewer e PDF Viewer non più disponibile in Android__ <!--747553--> A partire dalla metà di dicembre 2016, gli utenti non potranno più usare le app Intune AV Player, Image Viewer e PDF Viewer. Queste app sono state sostituite dall'app Azure Information Protection. È possibile trovare altre informazioni sull'app Azure Information Protection [qui](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>Novembre 2016

### <a name="new-capabilities"></a>Nuove funzionalità

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__Nuovo portale aziendale di Microsoft Intune disponibile per dispositivi Windows 10__ Microsoft ha rilasciato una nuova app [Portale aziendale di Microsoft Intune per dispositivi Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Questa app, che sfrutta il nuovo formato universale di Windows 10, offrirà un'esperienza utente aggiornata all'interno dell'app ed esperienze identiche in tutti i dispositivi Windows 10, sia PC che mobili, senza variazioni alle funzionalità già in uso.

La nuova app consentirà anche agli utenti di sfruttare altre funzionalità della piattaforma come Single Sign-On (SSO) e l'autenticazione basata su certificato nei dispositivi Windows 10. L'app verrà resa disponibile come aggiornamento delle installazioni del portale aziendale di Windows 8.1 e del portale aziendale di Windows Phone 8.1 da Windows Store. Per altre informazioni, vedere [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __Aggiornamento di Intune e Android for Work__

> Se da una parte è possibile distribuire app Android for Work con un'azione di __Richiesto__, un'app può essere distribuita solo come __Disponibile__ se i gruppi di Intune sono stati migrati alla nuova esperienza dei gruppi di Azure AD.

__Il plug-in Cordova per Intune App SDK attualmente supporta la gestione di applicazioni mobili senza registrazione__ Gli sviluppatori di app possono ora usare il plug-in Cordova per Intune App SDK per abilitare funzionalità di gestione di applicazioni mobili senza registrazione del dispositivo nelle proprie app basate su Cordova per iOS e Android. Il plug-in Cordova per Intune App SDK è disponibile [qui](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__Il componente Xamarin per Intune App SDK attualmente supporta la gestione di applicazioni mobili senza registrazione__ Gli sviluppatori di app possono ora usare il componente Xamarin per Intune App SDK per abilitare funzionalità di gestione di applicazioni mobili senza registrazione del dispositivo nelle proprie app basate su Xamarin per iOS e Android. Il componente Xamarin per Intune App SDK è disponibile [qui](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Notifiche

__Il certificato di firma Symantec non richiede più un'app Portale aziendale di Windows Phone 8 firmata per il caricamento__ Per il caricamento del certificato di firma Symantec non è più necessaria un'app Portale aziendale di Windows Phone 8 firmata. Il certificato può essere caricato in modo indipendente.

###<a name="deprecations"></a>Elementi deprecati

__Supporto per l'app Portale aziendale di Windows Phone 8__ Il supporto per il portale aziendale di Windows Phone 8 sarà deprecato. Il supporto per le piattaforme Windows Phone 8 e WinRT è stato deprecato a ottobre 2016. Il supporto per il portale aziendale di Windows 8 è stato deprecato a ottobre 2016.

## <a name="october-2016"></a>Ottobre 2016

### <a name="conditional-access-for-mobile-application-management"></a>Accesso condizionale per la gestione di applicazioni mobili
Sarà possibile limitare l'accesso a Exchange Online in modo che l'accesso possa essere eseguito solo da app che supportano i criteri di gestione delle applicazioni mobili di Intune, ad esempio Outlook. [Questa nuova funzionalità](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) si abbina perfettamente con i criteri di gestione delle app per dispositivi mobili di Intune perché è possibile bloccare l'accesso ai client di posta predefiniti o ad altre app che non sono state configurate con i criteri di gestione delle app per dispositivi mobili di Intune. In questo modo gli utenti accedono ai dati dell'organizzazione con applicazioni che possono essere protette usando MAM di Intune. È possibile iniziare a usare la gestione delle app per dispositivi mobili di Intune dal portale di Azure. Cercare la nuova sezione Accesso condizionale nel pannello "Impostazioni".

### <a name="conditional-access-for-windows-pcs"></a>Accesso condizionale per i PC Windows
È ora possibile creare criteri di accesso condizionale tramite la console di amministrazione di Intune per impedire l'accesso a [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) ai PC Windows. È inoltre possibile creare criteri di accesso condizionale per bloccare l'accesso alle applicazioni universali e desktop di Office.

### <a name="android-for-work-support"></a>Supporto di Android for Work

> [!IMPORTANT]

> Se da una parte è possibile distribuire app Android for Work con un'azione di __Richiesto__, un'app può essere distribuita solo come __Disponibile__ se i gruppi di Intune sono stati migrati alla nuova esperienza dei gruppi di Azure AD.

Intune è ora incluso nel programma Android for Work (AfW). L'implementazione del supporto delle funzionalità Android for Work sarà avviata questo mese e continuerà nei prossimi mesi. Si noti che la distribuzione dell'app disponibile di AfW sfrutta la nuova esperienza di raggruppamento e targeting. Gli account del servizio Intune sottoposti a provisioning di recente potranno usare questa funzionalità non appena AfW sarà disponibile.

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. -->

[Leggere l'annuncio Microsoft relativo al supporto di Android for Work in Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Gli argomenti seguenti relativi a Intune seguenti sono nuovi o aggiornati con le informazioni su Android for Work:

Per i professionisti IT:
- [Configurare Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Limitare l'accesso alla posta elettronica per Exchange Online e il nuovo ambiente Exchange Online dedicato con Intune](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Limitare l'accesso alla posta elettronica per Exchange locale e l'ambiente legacy Exchange Online dedicato con Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Impostazioni dei criteri di conformità di Android for Work](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Come distribuire le app Android for Work](/intune/deploy-use/android-for-work-apps)
- [Configurare le app Android for Work con i criteri di configurazione delle app per dispositivi mobili](/intune/deploy-use/afw-app-configuration-policy)
- [Impostazioni dei criteri di Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

Per gli utenti finali:
- [Cosa accade quando si crea un profilo di lavoro](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Creare un profilo di lavoro e registrare il dispositivo in Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>Integrazione di Lookout per proteggere i dispositivi iOS
A ottobre Microsoft prevede di integrare la soluzione di protezione dalle minacce per dispositivi mobili Lookout per proteggere i dispositivi mobili iOS grazie al rilevamento di malware, app rischiose e altro ancora. La soluzione Lookout consente di determinare il livello di minaccia, che è configurabile. È possibile creare una regola dei criteri di conformità in Intune per determinare la conformità del dispositivo in base alla valutazione del rischio da parte di Lookout. Con i criteri di accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali in base allo stato di conformità del dispositivo.

Agli utenti finali con dispositivi iOS non conformi verrà richiesto di eseguire la registrazione e di installare l'applicazione Lookout for Work, attivare l'app e correggere le minacce segnalate nell'applicazione Lookout for Work per ottenere l'accesso ai dati aziendali. Vedere le informazioni su come [Configurare e distribuire l'app Lookout for Work](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### <a name="intune-app-wrapping-tool-for-android"></a>Strumento per la disposizione testo per app di Intune
È possibile consentire alle app di usare i criteri di gestione del app per dispositivi mobili di Intune tramite lo strumento per la disposizione testo per app di Intune. È ora disponibile il supporto per i criteri di gestione delle app per dispositivi mobili di Intune che non richiede la registrazione del dispositivo.

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>Gestire la stampa dalle app gestite con criteri di gestione delle app per dispositivi mobili
Ora è possibile impedire la stampa di dati aziendali dalle app che includono criteri di gestione delle app per dispositivi mobili. Questa impostazione è disponibile nel [portale di Azure](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) ed è supportata in dispositivi [iOS](/Intune/deploy-use/ios-mam-policy-settings) e [Android](/Intune/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Supporto per le impronte digitali nei dispositivi Android
I criteri di gestione delle app mobili (MAM) per Android consentono agli utenti di accedere a un'app con l'impronta digitale invece di digitare il PIN personale. Informazioni su questa e altre [impostazioni dei criteri di gestione delle app mobili per Android sono disponibili qui](/Intune/deploy-use/android-mam-policy-settings).

### <a name="notices"></a>Notifiche

__Compatibilità di Android Samsung KNOX con Intune__ Alcuni modelli di telefoni Samsung Galaxy Ace non possono essere gestiti da Intune come dispositivi Samsung KNOX. Quando verranno registrati con Intune, questi dispositivi verranno invece gestiti come dispositivi Android standard.

I numeri di modello interessati sono:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Non sono richieste altre azioni da parte dell'amministratore o degli utenti. Per altre informazioni, visitare il sito Web [Samsung KNOX](https://www.samsungknox.com).

__L'app Portale aziendale per Windows 8 è deprecata e il supporto per le piattaforme Windows Phone 8 e Windows RT sarà deprecato__ A partire da ottobre 2016, il supporto di Microsoft Intune per il portale aziendale di Windows 8 verrà deprecato. Verrà anche deprecato il supporto di Microsoft Intune per le piattaforme Windows Phone 8 e Windows RT. Di conseguenza, non sarà possibile registrare o aggiornare dispositivi Windows Phone 8 o Windows RT.

È possibile continuare a gestire i dispositivi Windows Phone 8, Windows RT e Windows 8 che sono già registrati. Aggiornare i dispositivi Windows Phone 8 e Windows 8 a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi senza interruzioni.

A partire da novembre 2016, il supporto per il portale aziendale di Windows Phone 8 verrà deprecato.
<!--TFS 1255391-->

### <a name="whats-coming"></a>Sviluppi futuri

__Nuovo portale aziendale di Microsoft Intune disponibile per dispositivi Windows 10__ Microsoft sta rilasciando un nuovo portale aziendale di Microsoft Intune per dispositivi Windows 10. Questa app, che sfrutta il nuovo formato universale di Windows 10, offrirà un'esperienza utente aggiornata all'interno dell'app ed esperienze identiche in tutti i dispositivi Windows 10, sia PC che mobili, senza variazioni alle funzionalità già in uso.

La nuova app consentirà anche agli utenti di sfruttare altre funzionalità della piattaforma come Single Sign-On (SSO) e l'autenticazione basata su certificato nei dispositivi Windows 10. L'app verrà resa disponibile come aggiornamento delle installazioni del portale aziendale di Windows 8.1 e del portale aziendale di Windows Phone 8.1 da Windows Store. Per altre informazioni, vedere [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

## <a name="september-2016"></a>Settembre 2016
### <a name="new-features-announcements-and-information"></a>Nuove funzionalità, annunci e informazioni
* [Accesso condizionale di Windows](#windows-conditional-access)
* [Supporto di iOS 10](#ios-10-support)
* [Lo strumento di wrapping delle app supporta MAM senza registrazione del dispositivo per Android e iOS](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [I gruppi di Intune inizieranno la transizione in Azure Active Directory a settembre](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Integrazione di Lookout per proteggere i dispositivi Android](#lookout-integration-to-protect-android-devices)
* [Aggiornamenti del portale aziendale per Android, iOS e Windows](#company-portal-updates)
* [Glossario di Intune](#intune-glossary)
* [Sviluppi futuri](#whats-coming)

### <a name="windows-conditional-access"></a>Accesso condizionale di Windows
È ora possibile creare criteri di accesso condizionale tramite la console di amministrazione di Intune per impedire l'accesso a Exchange Online e SharePoint Online ai PC Windows. È inoltre possibile creare criteri di accesso condizionale per bloccare l'accesso alle applicazioni universali e desktop di Office.

### <a name="ios-10-support"></a>Supporto di iOS 10
Gli scenari MDM e MAM Intune esistenti sono compatibili con iOS 10. Per suggerimenti, consultare il [Blog del Team di supporto Intune](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>Lo strumento di wrapping delle app supporta MAM senza registrazione del dispositivo per Android e iOS
Lo strumento di wrapping delle app Intune è uno strumento da riga di comando usato per abilitare le app line-of-business (LOB) MAM Intune per iOS e Android. È il modo più semplice per incorporare dell'SDK per MAM Intune nell'app, in modo che l'app possa applicare i criteri MAM distribuiti attraverso Intune. Usando i criteri MAM, è possibile:

1. Crittografare i dati dell'app.
2. Richiedere all'information worker di immettere un PIN quando si avvia l'app.
3. Consentire all'app di trasferire i dati solo ad altre app gestite.
4. Impedire all'app di eseguire il backup dei dati in Android, iTunes e iCloud.
5. Consentire solo Taglia, Copia e Incolla in e da altre app gestite.

L'anteprima pubblica dello strumento di wrapping delle app di Intune supporta ora MAM senza registrazione dei dispositivi nelle app LOB interne in iOS e Android. Ciò significa che gli utenti finali non devono registrare i propri dispositivi con Intune per usare le app LOB abilitate per MAM.

Chiunque può testare il software in anteprima pubblica e leggere l'utile documentazione, che si trova in GitHub ai seguenti indirizzi:

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Prima di installare e usare la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS è necessario:

* Esaminare le condizioni di licenza Microsoft per la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS
* Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android si accettano tali condizioni di licenza. Qualora l'utente non le accetti, non potrà usare il software.
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>I gruppi di Intune inizieranno la transizione in Azure Active Directory a settembre
Alcuni nuovi account di Intune useranno i gruppi di sicurezza di Azure Active Directory anziché i gruppi di utenti di Intune. Sarà possibile sapere che si lavora con i gruppi di sicurezza perché la pagina dei gruppi del portale Intune avrà un collegamento che indirizza al portale di gestione di Azure.

### <a name="lookout-integration-to-protect-android-devices"></a>Integrazione di Lookout per proteggere i dispositivi Android
Microsoft sta integrando la soluzione di protezione dalle minacce per dispositivi mobili Lookout per proteggere i dispositivi mobili Android grazie al rilevamento di malware, app rischiose e altro ancora. La soluzione Lookout consente di determinare il livello di minaccia, che è configurabile. È possibile creare una regola dei criteri di conformità in Intune per determinare la conformità del dispositivo in base alla valutazione del rischio da parte di Lookout. Con i criteri di accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali in base allo stato di conformità del dispositivo.

Agli utenti finali dei dispositivi non conformi verrà richiesto di eseguire la registrazione e sarà necessario installare l'applicazione Lookout for Work nei dispositivi Android, attivare l'app e correggere le minacce segnalate nell'applicazione Lookout for Work per ottenere l'accesso. Per altre informazioni, vedere [Limitare l'accesso in base al rischio per dispositivi, rete e applicazioni](https://docs.microsoft.com/en-us/intune/deploy-use/device-threat-protection).


### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale

__Android__

<p style="margin-left: 40px">**Aggiunta di "Notifiche" al portale aziendale per Android**<br/>
<p style="margin-left: 40px">Una nuova icona di notifica è stata aggiunta al portale aziendale per Android nella home page. Toccando l'icona si accede alla pagina delle notifiche, che visualizza per gli utenti finali tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità dei dispositivi, l'aggiornamento della registrazione e l'attivazione della registrazione. Nell'app Portale aziendale per iOS questo tipo di notifica è già in uso. Grazie alla disponibilità della nuova pagina Notifiche, l'utente non visualizzerà la pagina Configurazione dell'accesso aziendale ogni volta che avvia o riprende il portale aziendale, purché il dispositivo sia già registrato. Se si creano le proprie linee guida per l'utente finale, è consigliabile aggiornare la documentazione in modo che rifletta questa modifica. Gli screenshot aggiornati sono disponibili [qui](https://aka.ms/androidcpupdate).  

__iOS__
<p style="margin-left: 40px">**Modifiche al supporto dell'app Portale aziendale per iOS**<br/>
<p style="margin-left: 40px">Tutti gli utenti dell'app Portale aziendale di Microsoft Intune per iOS ora devono usare la versione più recente. I nuovi utenti possono scaricare solo la versione più recente e gli utenti attuali devono aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, quindi gli utenti dei dispositivi che eseguono versioni precedenti di iOS non potranno usare il portale aziendale o eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.
<!---TFS 1283165--->

<p style="margin-left: 40px">**Miglioramenti della modalità di recupero delle app per gli utenti finali di iOS**<br/>
<p style="margin-left: 40px">Le modifiche seguenti sono state apportate ai riquadri delle app nell'app Portale aziendale in modo che iOS indirizzi gli utenti con visualizzazioni diverse per tutte le app in un'unica posizione, il sito Web del portale aziendale. Le restrizioni di Apple impediscono alle app dell'app store line-of-business e gestite di essere elencate nell'app Portale aziendale e richiedono agli utenti di visitare visualizzazioni diverse per trovare le proprie app.

<p style="margin-left: 40px">Il riquadro **App aziendali** indirizzava in precedenza a un elenco di tutte le app nella scheda TUTTE del sito Web del portale aziendale e continuerà a funzionare allo stesso modo. Il nome del riquadro è diventato **Tutte le app**.

<p style="margin-left: 40px">Il riquadro **Altre app** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca tutte le app che Apple consente di visualizzare all'app Portale aziendale. Il nome del riquadro è diventato **App in evidenza** e toccandolo gli utenti verranno indirizzati alla scheda IN EVIDENZA del sito Web del portale aziendale.

<p style="margin-left: 40px">Il riquadro **Categorie** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca le categorie di app. Il nome del riquadro non è cambiato, ma ora punta alla scheda CATEGORIE del sito Web del portale aziendale. È possibile trovare [qui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186) le schermate aggiornate.
  <!---TFS 1317133--->

<p style="margin-left: 40px">**Chiedere conferma per installare l'app Managed Browser per iOS se i professionisti IT impostano tale requisito per un'app**<br/>
<p style="margin-left: 40px">Se è stata configurata l'apertura di una clip Web solo nell'app Managed Browser e questa non è installata in un dispositivo, l'app Portale aziendale sul dispositivo chiederà all'utente di installare il browser gestito prima di poter installare la clip Web.
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**È stato aggiunto un pulsante Feedback all'app Portale aziendale per Windows Phone 8.1**<br/>
<p style="margin-left: 40px">L'app Portale aziendale per Windows Phone 8.1 consente agli utenti finali di inviare commenti e suggerimenti relativi all'app usando un nuovo pulsante di invio feedback. Per trovare il pulsante, gli utenti devono toccare il menu "tre punti" nella parte inferiore destra della schermata dell'app Portale aziendale e quindi toccare **Commenti e suggerimenti**. I feedback raccolti in modo anonimo consentiranno a Microsoft di migliorare l'esperienza dell'app del portale aziendale per gli utenti.
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Glossario di Intune</br>
È stato aggiunto un nuovo [argomento glossario](https://docs.microsoft.com/intune/understand-explore/intune-glossary) alla libreria per consentire una migliore comprensione di alcuni dei termini usati nel prodotto Intune.

## <a name="august-2016"></a>Agosto 2016
### <a name="app-management"></a>Gestione delle app
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__App nascoste e mostrate per iOS 9.3__ Per i dispositivi che eseguono iOS 9.3 o versione successiva sarà possibile usare gli elenchi di app nascoste e mostrate nei criteri di configurazione generale di iOS per:
- Specificare un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
- Specificare un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.

Le app selezionabili includono sia le app distribuite che le app predefinite per iOS, ad esempio i Messaggi e Note. Per informazioni dettagliate, vedere [Impostazioni dei criteri di iOS in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).
<!---TFS 1279009 checked--->
__Criteri delle app consentite e bloccate per i dispositivi Samsung KNOX__ È ora possibile configurare un criterio personalizzato per i dispositivi Samsung KNOX che consente di creare:
- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Anche se installata, un'app definita nell'elenco delle app bloccate non può essere attivata sul dispositivo.
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. Non sarà possibile installare altre app dallo Store.

Queste impostazioni possono essere usate solo dai dispositivi con Samsung KNOX.
Per informazioni dettagliate, vedere [Use custom policies to allow and block apps for Samsung KNOX devices](https://docs.microsoft.com/en-us/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps) (Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung KNOX).
<!---TFS 1311629 checked --->

__Nuove app compatibili con i criteri di gestione di applicazioni mobili (MAM)__ L'app Yammer per [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) è ora compatibile con i [criteri di gestione di applicazioni mobili di Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) a prescindere dal fatto che il dispositivo sia registrato o meno.

Per un elenco completo di app MAM compatibili, vedere il sito dei [partner che forniscono applicazioni per Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__App visualizzatore di Intune__ Con il rilascio della nuova app RMS sharing, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
- Visualizzatore AV di Intune
- Visualizzatore PDF di Intune
- Visualizzatore immagini di Intune per Android disponibile in Google Play

Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova [app Rights Management (RMS sharing) per Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app) che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Quando l'app visualizzatore di Intune non sarà più supportata, verrà rimossa da Google Store e non sarà disponibile per l'uso futuro.

### <a name="device-management"></a>Gestione dei dispositivi
__Supporto per Android 7.0__ Intune fornirà dal "day 0" il supporto per il sistema operativo Android 7.0 per dispositivi mobili, di imminente uscita.
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Rimozione di Google della funzionalità di reimpostazione remota del passcode nei dispositivi Android 7.0
Google sta rimuovendo la possibilità per gli amministratori IT e gli utenti finali di reimpostare in modalità remota il passcode dei dispositivi Android 7.0. In precedenza, gli amministratori IT potevano reimpostare in modalità remota il passcode di un utente e gli utenti finali potevano reimpostare i propri passcode dal sito Web del portale aziendale.



### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale
__Sito Web del portale aziendale__
- **Collegamento Commenti e suggerimenti di Microsoft dal portale aziendale** <br/>
Il sito Web del portale aziendale consente agli utenti di toccare il nuovo collegamento "Commenti e suggerimenti" nella parte inferiore della pagina, per inviare un feedback a Microsoft sulla propria esperienza con il sito. I commenti raccolti in modo anonimo consentiranno a Microsoft di migliorare l'esperienza del sito Web del portale aziendale per gli utenti.
<!--- TFS 1313657 checked--->

__iOS__
- **Versione minima di Managed Browser per iOS aggiornata a 8.0**<br/>
L'app Microsoft Intune Managed Browser per iOS è stata aggiornata in modo da supportare i dispositivi che eseguono iOS 8.0 o versioni successive. I dispositivi iOS 7.1 possono ancora usare l'app Managed Browser esistente. È tuttavia consigliabile invitare gli utenti a eseguire l'aggiornamento a iOS 8.0 o versione successiva per accedere a Managed Browser e sfruttare i vantaggi delle nuove funzionalità.  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>Sviluppi futuri
__Transizione dai gruppi di Intune ai gruppi di Azure Active Directory a partire dal mese di settembre 2016__ Intune sta creando una nuova esperienza di gestione dei gruppi che usa i gruppi di sicurezza di Azure Active Directory (AAD) come gruppi di utenti e dispositivi in Intune. Questi gruppi verranno usati per la gestione dei gruppi, la distribuzione dei criteri e la distribuzione dei profili **con l'introduzione del nuovo portale di amministrazione di Intune basato su Azure**.

Questa nuova esperienza consentirà di evitare di duplicare i gruppi tra i servizi, **garantirà l'accesso ad alcune nuove funzionalità dei gruppi di Azure Active Directory Premium (AADP)** e offrirà estendibilità tramite PowerShell e Graph. Consentirà inoltre di unificare l'esperienza di gestione dei gruppi per tutta la gestione della mobilità aziendale.

Per abilitare il passaggio ai gruppi di sicurezza, la **console di amministrazione corrente** verrà sottoposta ad alcune modifiche. **Queste modifiche e l'uso dei gruppi di sicurezza di AAD saranno indicati nella documentazione di Intune**.

I clienti che non hanno familiarità con Intune visualizzeranno **alcune delle modifiche ai gruppi di sicurezza prima di dei tenant correnti**.

Oltre alle modifiche apportate alla gestione dei gruppi, **verranno deprecate le funzionalità seguenti**:
- Esclusione di membri o gruppi durante la creazione di un nuovo gruppo
- Gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati**
- **Gestisci gruppi** nel ruolo di amministratore del servizio
- Avvisi personalizzati in base al gruppo per le regole di notifica
- Calcolo pivot per gruppi nei report
<!--- TFS 1295329--->

__Aggiunta di "Notifiche" al Portale aziendale per Android__ Nel mese di settembre verrà rilasciato un aggiornamento del portale aziendale per Android che presenterà una nuova icona delle **notifiche** nella home page. Toccando l'icona si avrà accesso alla pagina delle **notifiche** in cui l'utente finale visualizzerà tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. Se si usa l'app Portale aziendale per iOS, è già possibile visualizzare l'esperienza delle notifiche. Con l'introduzione della pagina **Notifiche**, non verrà visualizzata la pagina **Configurazione dell'accesso aziendale** ogni volta che si avvia o si riprende l'esecuzione del Portale aziendale per Android, purché il dispositivo sia già registrato. Molti utenti hanno creato materiale sussidiario per gli utenti finali ed è consigliabile dare tempestiva comunicazione a Microsoft nel caso possa essere necessario aggiornare tale materiale o le relative schermate. Aggiornare la documentazione in modo che rifletta le future modifiche nell'esperienza. Per le schermate aggiornate, visitare https://aka.ms/androidcpupdate.  

### <a name="service-deprecation"></a>Deprecazione del servizio
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Modifiche al supporto dell'app Portale aziendale per iOS**<br/>
Da settembre, tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS dovranno usare la versione più recente dell'app. I nuovi utenti potranno scaricare solo la versione più recente e gli utenti attuali dovranno aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, pertanto gli utenti dei dispositivi che eseguono versioni precedenti di iOS non saranno in grado di usare il portale aziendale o di eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.  

- **Versione minima di Managed Browser per iOS aggiornata a 8.0**<br/>
Nel mese di agosto Intune rilascerà un'app aggiornata di Managed Browser di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 8.0 o versione successiva. I dispositivi iOS 7.1 saranno ancora in grado di usare l'app Managed Browser esistente, tuttavia è consigliabile invitare gli utenti a eseguire l'aggiornamento a iOS 8.0 o versione successiva per accedere a Managed Browser e sfruttare i vantaggi delle nuove funzionalità.  
<!---TFS 1313253--->

- **Le app del portale aziendale per Windows 8 e Windows Phone 8 verranno deprecate a partire da settembre 2016** <br/>
Da settembre 2016, Microsoft Intune terminerà il supporto per le app del portale aziendale di Microsoft Intune per le piattaforme Windows Phone 8 e Windows 8. Aggiornare i dispositivi a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->
