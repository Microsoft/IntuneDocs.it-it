---
title: Edizione anticipata | Microsoft Docs
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: d7f25657fc7cfb9298809f76f198810718e58c39
ms.lasthandoff: 04/27/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>Edizione anticipata per Microsoft Intune - Aprile 2017

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
> Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Stato di installazione delle app migliorato per l'app Portale aziendale di Windows 10 <!--676495-->

Nell'app Portale aziendale di Windows 10 è ora disponibile un indicatore di stato per tutte le installazioni di app moderne avviate dal portale aziendale. È possibile visualizzare i nuovi messaggi di stato per l'app Portale aziendale per Windows 10 nella [pagina delle novità dell'interfaccia utente di Intune](whats-new-in-intune-app-ui.md).

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Messaggi di stato migliorati nell'app Portale aziendale per iOS <!--744866-->

All'interno dell'app Portale aziendale per iOS verranno ora visualizzati nuovi messaggi di errore più specifici per fornire informazioni più accessibili su ciò che accade nei dispositivi. Questi casi di errore erano precedentemente inclusi in un messaggio di errore generale analogo a "Portale aziendale temporaneamente non disponibile". Inoltre, se un utente avvia il portale aziendale in iOS in assenza di una connessione Internet, ora verrà visualizzata una barra di stato permanente nella home page con il messaggio "Nessuna connessione Internet".

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps disponibile per Managed Browser <!--822308, 822303-->

Microsoft MyApps dispone ora di un supporto migliorato all'interno di Managed Browser. Gli utenti di Managed Browser che non sono assegnati alla gestione saranno indirizzati direttamente al servizio MyApps, da dove potranno accedere alle loro app SaaS con provisioning dell'amministratore. Gli utenti assegnati alla gestione di Intune continueranno a essere in grado di accedere a MyApps dal segnalibro di Managed Browser predefinito.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nuove icone per Managed Browser e il portale aziendale <!--918433, 918431-->

Managed Browser disporrà di icone aggiornate per le versioni Android e iOS dell'app. La nuova icona conterrà il logo di Intune aggiornato, in modo da renderla più coerente con le altre app in Enterprise Mobility + Security (EM+S). È possibile visualizzare la nuova icona per Managed Browser nella [pagina delle novità dell'interfaccia utente di Intune](whats-new-in-intune-app-ui.md).

Il portale aziendale disporrà inoltre di icone aggiornate per le versioni Android, iOS e Windows dell'app, per migliorare la coerenza con le altre app in EM+S. Queste icone verranno rilasciate gradualmente tra le piattaforme da aprile a fine maggio.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Supporto Single Sign-On dal portale aziendale per IOS ad Outlook per iOS <!--834012-->

Gli utenti non devono più eseguire l'accesso all'app di Outlook se sono già connessi all'app Portale aziendale per IOS sullo stesso dispositivo con lo stesso account. Quando gli utenti avviano l'app di Outlook, potranno selezionare il loro account e accedere automaticamente. Si prevede di aggiungere questa funzionalità anche per altre app Microsoft.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicatore di stato dell'accesso al portale aziendale Android <!--953374-->

Un aggiornamento all'app Portale aziendale Android mostra un indicatore di stato dell'accesso quando l'utente avvia o riprende l'app. L'indicatore indica una progressione attraverso nuovi stati, a partire da "Connessione in corso...", ad "Accesso in corso..." e infine "Verifica dei requisiti di sicurezza in corso..." prima di consentire all'utente di accedere all'app. È possibile visualizzare le nuove schermate per l'app del portale aziendale per Android nella [pagina delle novità dell'interfaccia utente di Intune](whats-new-in-intune-app-ui.md).


## <a name="notices"></a>Notifiche

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->

A partire dalla primavera 2017, Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->

Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di anteprima di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Sviluppi futuri per Appx in Intune in Azure <!-- 1000270 -->

Nell'ambito della migrazione a Intune in Azure, saranno apportate tre modifiche alle app appx:

1. Aggiunta di un nuovo tipo di app appx nella console di Intune classica distribuibile solo a dispositivi registrati MDM.
2. Reimpiego del tipo di app appx esistente per essere destinata solo a PC gestiti tramite l'agente PC di Intune.
3. Conversione di tutte le app appx esistenti in app appx MDM con la migrazione.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?

Questa modifica non avrà alcun impatto sulle distribuzioni esistenti ai dispositivi gestiti tramite l'agente PC di Intune. Tuttavia, dopo la migrazione, non sarà più possibile distribuire queste app appx migrate a eventuali nuovi dispositivi gestiti tramite l'agente PC di Intune che non siano stati previsti in precedenza.

#### <a name="what-action-do-i-need-to-take"></a>Quali misure è necessario adottare?

Dopo la migrazione, sarà necessario caricare nuovamente l'app appx come app appx per PC se si vuole procedere a nuove distribuzioni su PC. Per altre informazioni, vedere [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Modifiche ad Appx in Intune in Azure) nel blog del team di supporto Intune.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Supporto per le opzioni di configurazione gestita per le app Android <!-- 621621 -->

Le app Android nel Play Store che supportano le opzioni di configurazione gestita possono essere configurate da Intune.  Questa funzionalità consente ai responsabili IT di visualizzare l'elenco dei valori di configurazione supportati da un'app e fornisce un'interfaccia utente guidata avanzata per consentire la configurazione di tali valori.

### <a name="remote-assistance-for-android-devices----675418---"></a>Assistenza remota per i dispositivi Android <!-- 675418 -->

Intune userà il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per consentire agli amministratori di offrire assistenza remota agli utenti che eseguono dispositivi Android.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nuovi criteri Android per PIN complessi <!-- 722069 -->

È possibile impostare un tipo di password richiesto di tipo Complessa numerica in un profilo di dispositivo Android per i dispositivi che eseguono Android 5.0 e versioni successive.  Usare questa impostazione per impedire agli utenti dei dispositivi di creare un PIN contenente numeri ripetuti o consecutivi, ad esempio 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Supporto aggiuntivo per i dispositivi Android for Work

- **Gestire le impostazioni delle password e dei profili di lavoro** <!-- 612808 -->

  È stato aggiunto un nuovo criterio di restrizione dei dispositivi Android for Work che consente di gestire le impostazioni delle password e dei profili di lavoro nei dispositivi Android for Work gestiti.

- **Consentire la condivisione dei dati tra i profili di lavoro e personali** <!-- 1045102 -->

  L'impostazione **Condivisione dei dati tra i profili di lavoro e personali** in un profilo di restrizione dei dispositivi Android for Work è stata aggiornata con nuove opzioni che consentono di configurare la condivisione dei dati tra profili di lavoro e personali.

- **Limitare il copia e incolla tra i profili di lavoro e personali** <!-- 1046094 -->

  Quando si gestiscono dispositivi Android for Work con Intune, sono consentite operazioni di copia e incolla tra app di lavoro e personali. Ora è stato aggiunto un profilo di dispositivo personalizzato per i dispositivi Android for Work che consente di limitare le operazioni di copia e incolla tra app di lavoro e personali.

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Assegnazione di app LOB a dispositivi iOS e Android <!-- 1057568 -->

È possibile assegnare a utenti o dispositivi app line-of-business per iOS (file con estensione ipa) e per Android (file con estensione apk).

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>Nuovi criteri per i dispositivi iOS <!-- 723774, 723815, 723826, 723830, 723832 -->

- **App nella schermata iniziale**: è possibile usare un criterio dei dispositivi per controllare quali sono le app visualizzate dagli utenti nella schermata iniziale dei loro dispositivi iOS. Questo criterio modifica il layout della schermata iniziale, ma non distribuisce le app che l'utente ha specificato come non installate.

- **Connessioni ai dispositivi AirPrint**: i criteri dei dispositivi di Intune possono essere usati per controllare a quali dispositivi AirPrint (stampanti di rete) possono connettersi gli utenti finali del dispositivo iOS.

- **Connessioni ai dispositivi AirPlay**: i criteri dei dispositivi di Intune possono essere usati per controllare a quali dispositivi AirPlay (come Apple TV) possono connettersi gli utenti finali del dispositivo iOS.

- **Messaggio personalizzato della schermata di blocco**: è possibile configurare un messaggio personalizzato che gli utenti visualizzeranno nella schermata di blocco del loro dispositivo iOS, in sostituzione del messaggio della schermata di blocco predefinito.

- **Filtro dei contenuti Web**: è possibile controllare quali siti Web possono visitare gli utenti dei dispositivi iOS tramite uno dei due metodi seguenti:

  - Aggiungere URL consentiti e bloccati tramite il filtro predefinito dei contenuti Web di Apple.
  - Consentire l'accesso dal browser Safari solo ai siti Web specificati. Per ogni sito specificato verrà creato il segnalibro corrispondente in Safari.


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Limitazione delle notifiche push per le app per iOS <!-- 723767 -->

In un profilo di restrizione del dispositivo di Intune è possibile configurare le impostazioni di notifica seguenti per i dispositivi iOS:

- Attivare o disattivare completamente la notifica per un'app specificata.
- Attivare o disattivare la notifica nel Centro notifiche per un'app specificata.
- Specificare il tipo di avviso, ovvero **Nessuno**, **Banner** o **Modal Alert** (Avviso modale).
- Specificare se sono consentite le notifiche per questa app.
- Specificare se sono consentite le notifiche audio.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurazione delle app per iOS per l'esecuzione in modo autonomo in Modalità applicazione singola <!-- 737837 -->

È possibile usare un profilo di dispositivo di Intune per configurare i dispositivi iOS per l'esecuzione delle applicazioni specificate in Modalità applicazione singola autonoma. Quando questa modalità è configurata e l'app è in esecuzione, il dispositivo è bloccato in modo che possa eseguire solo quell'app. Un esempio è quando si configura un'app che consente agli utenti di eseguire un test nel dispositivo. Quando le operazioni dell'app sono state completate o si rimuove questo criterio, il dispositivo torna allo stato normale.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurazione di domini trusted per posta elettronica ed esplorazione Web nei dispositivi iOS <!-- 723765 -->

Da un profilo di restrizione del dispositivo iOS è possibile configurare le impostazioni di dominio seguenti:

- **Domini di posta elettronica non contrassegnati**: i messaggi inviati o ricevuti dall'utente che non corrispondono ai domini specificati qui verranno contrassegnati come non attendibili.

- **Domini Web gestiti**: i documenti scaricati dagli URL specificati qui verranno considerati gestiti (solo Safari).  

- **Domini con riempimento automatico della password di Safari**: gli utenti possono salvare le password in Safari solo dagli URL corrispondenti ai modelli specificati qui. Per usare questa impostazione, il dispositivo deve essere in modalità con supervisione e non deve essere configurato per più utenti (iOS 9.3 e versioni successive).


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>App VPP disponibili nel portale aziendale iOS <!-- 748782 -->

È possibile assegnare app per iOS acquistate con Volume Purchase Program (VPP) come installazioni **disponibili** per gli utenti finali. Gli utenti finali avranno bisogno di un account Apple Store per installare l'app.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizzazione di eBook dallo Store VPP di Apple <!-- 800878 -->

È possibile sincronizzare gli eBook acquistati dallo Store Volume-Purchase Program di Apple con Intune e assegnarli agli utenti.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestione di più utenti per i dispositivi Samsung KNOX Standard <!-- 971988 -->

I dispositivi che eseguono Samsung KNOX Standard sono ora supportati per la gestione di più utenti in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure Active Directory e il dispositivo è gestito centralmente indipendentemente dal fatto che sia o meno in uso.  Quando gli utenti finali eseguono l'accesso, possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Altre impostazioni relative alle restrizioni dei dispositivi per Windows <!-- 818566 -->

Sono ora supportate ulteriori impostazioni di restrizione dei dispositivi per Windows come maggiore supporto per il browser Edge, personalizzazione della schermata di blocco del dispositivo, personalizzazioni del menu Start, sfondo per la ricerca Windows Spotlight e impostazione del proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Supporto multiutente per Windows 10 Creators Update <!-- 822547 -->

È stato aggiunto il supporto per la gestione multiutente per i dispositivi che eseguono Windows 10 Creators Update e sono aggiunti al dominio di Azure Active Directory. Ciò significa che quando utenti standard diversi accedono al dispositivo con le rispettive credenziali di Azure AD, accederanno alle app e ai criteri che sono stati assegnati al loro nome utente. Gli utenti non possono attualmente usare il portale aziendale per scenari self-service come l'installazione di app.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start per i PC Windows 10<!-- 1004830 -->

In questa versione è stata aggiunta una nuova azione del dispositivo Fresh Start per i PC Windows 10.  Quando si esegue questa azione, vengono rimosse tutte le app precedentemente installate nel PC e il computer è aggiornato automaticamente alla versione più recente di Windows. Questa funzionalità può essere usata per rimuovere le app OEM che spesso sono preinstallate in un nuovo PC. È possibile configurare se i dati utente devono essere conservati quando si esegue questa azione del dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Percorsi di aggiornamento aggiuntivi per Windows 10 <!-- 903672 -->

È ora possibile creare criteri di aggiornamento dell'edizione per aggiornare i dispositivi alle edizioni di Windows 10 seguenti:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Registrazione in blocco di dispositivi Windows 10 <!-- 747607 -->

È possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune tramite Windows Configuration Designer (WCD). Per abilitare la registrazione MDM automatica del tenant di Azure AD, creare un pacchetto di provisioning per l'aggiunta dei dispositivi al tenant di Azure AD usando Windows Configuration Designer e applicare il pacchetto ai dispositivi di proprietà aziendale che si vuole registrare e gestire in blocco. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento non sono supportati scenari self-service o con il portale aziendale.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>Nuove impostazioni MAM per PIN e percorsi di archiviazione gestita <!-- 58112, 736644 -->

Sono disponibili due nuove impostazioni dell'app per semplificare gli scenari di gestione di applicazioni mobili (MAM):

- **Disabilitare il PIN dell'app quando il PIN del dispositivo è gestito**: consente di rilevare se nel dispositivo registrato è presente un PIN del dispositivo e, in tal caso, di ignorare il PIN dell'app attivato dai criteri di protezione delle app. Questa impostazione consentirà di ridurre il numero di volte in cui gli utenti visualizzeranno un prompt di richiesta del PIN all'apertura di un'applicazione abilitata per MAM in un dispositivo registrato. Questa funzionalità è disponibile per sia per Android che per iOS.

- **Selezionare i servizi di archiviazione in cui è possibile salvare i dati aziendali**: consente di specificare i percorsi di archiviazione in cui salvare i dati aziendali. Gli utenti possono eseguire il salvataggio nei servizi di posizione di archiviazione selezionati, il che significa che tutti gli altri servizi di posizione di archiviazione non elencati verranno bloccati.

  I servizi di posizione di archiviazione supportati sono i seguenti:

  - OneDrive
  - Business SharePoint Online
  - Archiviazione locale


### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).

