---
title: "Novità dell&quot;anteprima di Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Novità dell&quot;anteprima di Intune in Azure"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8d36543aac7eb441d99fb4917d7d25b3dc553da6
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novità dell'anteprima di Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Con il progresso dell'anteprima pubblica e l'aggiunta di altre funzionalità, verrà inviata notifica qui.

> [!Note]
> È in corso l'implementazione delle modifiche elencate in questa pagina per il portale di anteprima di Azure. Queste modifiche, tuttavia, potrebbero non essere disponibili immediatamente a causa della modalità di aggiornamento del servizio Intune.  Alcuni componenti del servizio devono essere aggiornati in sequenza prima che le nuove funzionalità del portale siano disponibili. Cercare le modifiche a mano a mano che verranno implementate nel corso del mese.

## <a name="april-2017"></a>Aprile 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Supporto per la gestione dell'app Classroom Apple

È ora possibile gestire l'app Classroom iOS nei dispositivi iPad. Configurare l'app Classroom nell'iPad degli insegnanti con la classe e i dati sugli studenti corretti, quindi configurare gli iPad degli studenti registrati in una classe, in modo da poterli controllare tramite l'app.
Per altri dettagli, vedere [Configurare le impostazioni di iOS relative alla formazione](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Supporto per le opzioni di configurazione gestita per le app Android <!-- 621621 -->

Le app Android nel Play Store che supportano le opzioni di configurazione gestita ora possono essere configurate da Intune.  Questa funzionalità consente ai responsabili IT di visualizzare l'elenco dei valori di configurazione supportati da un'app e fornisce un'interfaccia utente guidata avanzata per consentire la configurazione di tali valori.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nuovi criteri Android per PIN complessi <!-- 722069 -->

È ora possibile impostare una [password](device-restrictions-android.md#password) obbligatoria di tipo Complessa numerica in un profilo di dispositivo Android per i dispositivi che eseguono Android 5.0 e versioni successive.  Usare questa impostazione per impedire agli utenti dei dispositivi di creare un PIN contenente numeri ripetuti o consecutivi, ad esempio 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Supporto aggiuntivo per i dispositivi Android for Work

- **Gestire le impostazioni delle password e dei profili di lavoro** <!-- 612808 -->

  Questo nuovo criterio di restrizione dei dispositivi Android for Work ora consente di gestire le impostazioni delle password e dei profili di lavoro nei dispositivi Android for Work gestiti.

- **Consentire la condivisione dei dati tra i profili di lavoro e personali** <!-- 1045102 -->

Questo profilo di restrizione dei dispositivi Android for Work ora offre nuove opzioni che consentono di configurare la condivisione dei dati tra i profili di lavoro e quelli personali.

- **Limitare il copia e incolla tra i profili di lavoro e personali** <!-- 1046094 -->

  Un nuovo profilo di dispositivo personalizzato per i dispositivi Android for Work consente ora di limitare le operazioni di copia e incolla tra app di lavoro e personali.

Per altre informazioni, vedere l'articolo sulle [restrizioni dei dispositivi per Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Assegnazione di app LOB a dispositivi iOS e Android <!-- 1057568 -->

È ora possibile assegnare a utenti o dispositivi app line-of-business (LOB) per [iOS](lob-apps-ios.md) (file con estensione ipa) e per [Android](lob-apps-android.md) (file con estensione apk).

###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nuovi criteri dei dispositivi per iOS <!-- 723774, 723815, 723826, 723830 -->

- **App nella schermata iniziale**: stabilisce quali sono le app visualizzate dagli utenti nella [schermata iniziale dei loro dispositivi iOS](home-screen-settings-ios.md). Questo criterio modifica il layout della schermata iniziale, ma non distribuisce le app che l'utente ha specificato come non installate.

- **Connessioni ai dispositivi AirPrint**: specifica i [dispositivi AirPrint](air-print-settings-ios-macos.md) (stampanti di rete) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Connessioni ai dispositivi AirPlay**: specifica i [dispositivi AirPlay](airplay-settings-ios.md) (come Apple TV) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Messaggio personalizzato della schermata di blocco**: consente di configurare un messaggio personalizzato che gli utenti visualizzeranno nella schermata di blocco del loro dispositivo iOS, in sostituzione del messaggio della schermata di blocco predefinito. Per altre informazioni, vedere le [azioni del dispositivo disponibili](device-management.md#available-device-actions)


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Limitazione delle notifiche push per le app per iOS <!-- 723767 -->

In un profilo di restrizione del dispositivo di Intune è possibile configurare le [impostazioni di notifica](app-notification-settings-ios.md) seguenti per i dispositivi iOS:

- Attivare o disattivare completamente la notifica per un'app specificata.
- Attivare o disattivare la notifica nel Centro notifiche per un'app specificata.
- Specificare il tipo di avviso, ovvero **Nessuno**, **Banner** o **Modal Alert** (Avviso modale).
- Specificare se sono consentite le notifiche per questa app.
- Specificare se sono consentite le notifiche audio.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurazione delle app per iOS per l'esecuzione in modo autonomo in Modalità applicazione singola <!-- 737837 -->

È possibile usare un profilo di dispositivo di Intune per configurare i dispositivi iOS per l'esecuzione delle applicazioni specificate in [Modalità applicazione singola autonoma](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quando questa modalità è configurata e l'app è in esecuzione, il dispositivo è bloccato in modo che possa eseguire solo quell'app. Un esempio è quando si configura un'app che consente agli utenti di eseguire un test nel dispositivo. Quando le operazioni dell'app sono state completate o si rimuove questo criterio, il dispositivo torna allo stato normale.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurazione di domini trusted per posta elettronica ed esplorazione Web nei dispositivi iOS <!-- 723765 -->

Da un profilo di restrizione del dispositivo iOS è ora possibile configurare le [impostazioni di dominio](device-restrictions-ios.md#domains) seguenti:

- **Domini di posta elettronica non contrassegnati**: i messaggi inviati o ricevuti dall'utente che non corrispondono ai domini specificati qui verranno contrassegnati come non attendibili.

- **Domini Web gestiti**: i documenti scaricati dagli URL specificati qui verranno considerati gestiti (solo Safari).  

- **Domini con riempimento automatico della password di Safari**: gli utenti possono salvare le password in Safari solo dagli URL corrispondenti ai modelli specificati qui. Per usare questa impostazione, il dispositivo deve essere in modalità con supervisione e non deve essere configurato per più utenti (iOS 9.3 e versioni successive).


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>App VPP disponibili nel portale aziendale iOS <!-- 748782 -->

È ora possibile assegnare app per iOS acquistate con Volume Purchase Program (VPP) come installazioni **disponibili** per gli utenti finali. Gli utenti finali avranno bisogno di un account Apple Store per installare l'app.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizzazione di eBook dallo Store VPP di Apple <!-- 800878 -->

È ora possibile [sincronizzare i libri](vpp-apps-ios.md) acquistati nello store Apple Volume Purchase Program con Intune e assegnarli agli utenti.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestione di più utenti per i dispositivi Samsung KNOX Standard <!-- 971988 -->

I dispositivi che eseguono Samsung KNOX Standard sono ora supportati per la [gestione multiutente](android-enroll.md) in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure Active Directory e il dispositivo è gestito centralmente indipendentemente dal fatto che sia o meno in uso.  Quando gli utenti finali eseguono l'accesso, possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Altre impostazioni relative alle restrizioni dei dispositivi per Windows <!-- 818566 -->

Sono ora supportate altre [impostazioni di restrizione dei dispositivi per Windows](device-restrictions-windows-10.md) come maggiore supporto per il browser Edge, personalizzazione della schermata di blocco del dispositivo, personalizzazioni del menu Start, sfondo per la ricerca Windows Spotlight e impostazione del proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Supporto multiutente per Windows 10 Creators Update <!-- 822547 -->

È stato aggiunto il supporto per la [gestione multiutente](windows-enroll.md) per i dispositivi che eseguono Windows 10 Creators Update e sono aggiunti al dominio di Azure Active Directory. Ciò significa che quando utenti standard diversi accedono al dispositivo con le rispettive credenziali di Azure AD, riceveranno tutte le app e i criteri assegnati al loro nome utente. Gli utenti non possono attualmente usare il portale aziendale per scenari self-service come l'installazione di app.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start per i PC Windows 10<!-- 1004830 -->

È ora disponibile una nuova [azione del dispositivo Fresh Start](device-management.md#available-device-actions) per i PC Windows 10.  Quando si esegue questa azione, vengono rimosse tutte le app precedentemente installate nel PC e il computer è aggiornato automaticamente alla versione più recente di Windows. Questa funzionalità può essere usata per rimuovere le app OEM che spesso sono preinstallate in un nuovo PC. È possibile configurare se i dati utente devono essere conservati quando si esegue questa azione del dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Percorsi di aggiornamento aggiuntivi per Windows 10 <!-- 903672 -->

È ora possibile creare [criteri di aggiornamento dell'edizione per aggiornare i dispositivi](edition-upgrade-configure-windows-10.md) alle seguenti edizioni aggiuntive di Windows 10:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Registrazione in blocco di dispositivi Windows 10 <!-- 747607 -->

È ora possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune con Windows Configuration Designer (WCD). Per abilitare la [registrazione MDM in blocco](windows-bulk-enroll.md) del tenant di Azure AD, creare un pacchetto di provisioning che aggiunga i dispositivi al tenant di Azure AD usando Windows Configuration Designer e applicare il pacchetto ai dispositivi di proprietà dell'azienda che si vuole registrare e gestire in blocco. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento non sono supportati scenari self-service o con il portale aziendale.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nuove impostazioni MAM per PIN e percorsi di archiviazione gestita <!-- 581122, 736644 -->

Sono ora disponibili due nuove impostazioni dell'app per semplificare gli scenari di gestione di applicazioni mobili (MAM):

- **Disabilitare il PIN dell'app quando il PIN del dispositivo è gestito**: consente di rilevare se nel dispositivo registrato è presente un PIN del dispositivo e, in tal caso, di ignorare il PIN dell'app attivato dai criteri di protezione delle app. Questa impostazione consentirà di ridurre il numero di volte in cui gli utenti visualizzeranno un prompt di richiesta del PIN all'apertura di un'applicazione abilitata per MAM in un dispositivo registrato. Questa funzionalità è disponibile per sia per Android che per iOS.

- **Selezionare i servizi di archiviazione in cui è possibile salvare i dati aziendali**: consente di specificare i percorsi di archiviazione in cui salvare i dati aziendali. Gli utenti possono eseguire il salvataggio nei servizi di posizione di archiviazione selezionati, il che significa che tutti gli altri servizi di posizione di archiviazione non elencati verranno bloccati.

  I servizi di posizione di archiviazione supportati sono i seguenti:

  - OneDrive
  - Business SharePoint Online
  - Archiviazione locale

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portale del Supporto tecnico per la risoluzione dei problemi <!-- 907448 -->

Il nuovo [portale per la risoluzione dei problemi](help-desk-operators.md) consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare utenti e dispositivi e di eseguire attività per la risoluzione dei problemi tecnici di Intune.

## <a name="march-2017"></a>Marzo 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Supporto per la modalità di dispositivo perso di iOS <!--431695-->

Per i dispositivi iOS 9.3 e versioni successive, Intune ha aggiunto il supporto per la **modalità di dispositivo perso**. È ora possibile bloccare un dispositivo per impedirne l'uso e visualizzare un messaggio e un numero di telefono di contatto nella schermata di blocco del dispositivo.

L'utente finale non sarà in grado di sbloccare il dispositivo finché la modalità di dispositivo perso non verrà disabilitata da un amministratore. Quando la modalità di dispositivo perso è abilitata, è possibile usare l'azione **Individua il dispositivo** per visualizzare la posizione geografica del dispositivo su una mappa nella console di Intune.

Deve trattarsi di un dispositivo iOS di proprietà dell'azienda, registrato con DEP, in cui sia attiva la modalità con supervisione.

Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).

### <a name="improvements-to-device-actions-report---677150--"></a>Miglioramenti al report Azioni del dispositivo <!--677150-->

Le prestazioni del report Azioni del dispositivo sono state migliorate. È inoltre possibile filtrare il report in base allo stato. Si possono ad esempio mostrare solo le azioni del dispositivo che sono state completate.

### <a name="actions-for-non-compliance---730266--"></a>Azioni per la mancata conformità <!--730266-->

Le **azioni per la mancata conformità** sono una nuova funzionalità dei criteri di conformità che consente di intervenire sui dispositivi non conformi. È possibile specificare una o più azioni e il periodo di tempo in cui devono essere eseguite tali azioni. Ad esempio, è possibile segnalare immediatamente agli utenti i dispositivi non conformi non appena diventano non conformi, tramite posta elettronica, oppure è possibile impedire ai dispositivi non conformi di accedere alle risorse aziendali dopo un periodo di tolleranza di 3 giorni tramite l'accesso condizionale.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->

È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Assegnare app line-of-business agli utenti con dispositivi non registrati <!--748823-->

È ora possibile assegnare app line-of-business dallo store agli utenti, indipendentemente dal fatto che i loro dispositivi siano registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale.

### <a name="new-compliance-reports---846671--"></a>Nuovi report di conformità <!--846671-->

Sono ora disponibili report di conformità che definiscono il comportamento di conformità dei dispositivi in ambito aziendale e consentono di risolvere rapidamente i problemi correlati alla conformità riscontrati dagli utenti. È possibile visualizzare le informazioni seguenti:

- Stato di conformità generale dei dispositivi
- Stato di conformità per una singola impostazione
- Stato di conformità per singoli criteri

È inoltre possibile usare questi report per eseguire il drill-down in un singolo dispositivo e visualizzare impostazioni e criteri specifici che influiscono su tale dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->

Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di anteprima di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.


## <a name="february-2017"></a>Febbraio 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilità di limitare la registrazione di dispositivi mobili <!--747600, 795782-->
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.

* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.  
* Solo per iOS e Android è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Visualizzare tutte le azioni nei dispositivi gestiti <!--677150-->
Il nuovo report __Azioni del dispositivo__ mostra gli utenti che hanno eseguito azioni remote come il ripristino delle impostazioni predefinite nei dispositivi e lo stato dell'azione. Vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](https://docs.microsoft.comdevice-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->
Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="display-device-categories---814654--"></a>Visualizzare le categorie di dispositivi <!--814654-->
È ora possibile visualizzare la categoria dei dispositivi come colonna dell'elenco dei dispositivi. È inoltre possibile modificare la categoria nella sezione delle proprietà del pannello delle proprietà del dispositivo. Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurare le impostazioni di Windows Update for Business <!--776716-->

Windows as a Service è il nuovo modo per distribuire gli aggiornamenti per Windows 10. A partire da Windows 10, i nuovi aggiornamenti qualitativi e delle funzionalità includeranno il contenuto di tutti gli aggiornamenti precedenti. Ciò significa che, una volta installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 sono perfettamente aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Usando Windows Update for Business, è possibile semplificare l'esperienza di gestione degli aggiornamenti in modo da non dover approvare singoli aggiornamenti per gruppi di dispositivi. È comunque possibile gestire i rischi nei propri ambienti configurando una strategia di implementazione degli aggiornamenti. In questo modo, Windows Update verificherà che gli aggiornamenti vengano installati al momento opportuno. Microsoft Intune offre la possibilità di configurare le impostazioni di aggiornamento sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. Per gli aggiornamenti i dispositivi accedono direttamente a Windows Update. Usare Intune per configurare e gestire gli **anelli di aggiornamento di Windows 10**. Un anello di aggiornamento contiene un gruppo di impostazioni che definiscono quando e come vengono installati gli aggiornamenti di Windows 10. Per informazioni dettagliate, vedere [Configurare le impostazioni di Windows Update for Business](windows-update-for-business-configure.md).

## <a name="january-2017"></a>Gennaio 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Assegnare app line-of-business indipendentemente dalla registrazione dei dispositivi <!--748823-->
È ora possibile assegnare app line-of-business e app dallo store agli utenti, indipendentemente dal fatto che i loro dispositivi siano o meno registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale. Vedere [Che cos'è la gestione delle app?](app-management.md)

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Risolvere il problema nel caso in cui i dispositivi iOS non sono attivi o la console di amministrazione non è in grado di comunicare con i dispositivi
Quando i dispositivi degli utenti perdono la connessione con Intune è possibile indicare nuovi passaggi per la risoluzione dei problemi per ripristinare l'accesso alle risorse aziendali. Vedere [I dispositivi sono inattivi o la console di amministrazione non è in grado di comunicare con i dispositivi](enrollment-troubleshoot.md#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Dicembre 2016 (versione iniziale)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integrazione della gestione delle spese di telecomunicazione nell'anteprima pubblica del portale di Azure<!--747605-->
Stiamo iniziando a presentare in anteprima l'integrazione con i servizi di gestione delle spese di telecomunicazione di terze parti nel portale di Azure. È possibile usare Intune per imporre limiti al consumo dei dati sia nazionale che in roaming. Queste integrazioni iniziano con [Saaswedo](http://www.saaswedo.com). Per abilitare questa funzionalità nel tenant di prova, [contattare il supporto tecnico Microsoft](https://docs.microsoft.com/intune-classic/troubleshoot/get-support).

- Distribuire e gestire le applicazioni da un archivio su dispositivi iOS, Android e Windows
- Distribuire e gestire le app line-of-business (LOB) su dispositivi iOS, Android e Windows
- Distribuire e gestire le app acquistate con Volume Purchase Program su dispositivi iOS e Windows
- Distribuire e gestire le app Web su dispositivi Android, iOS e Windows
- Profili di configurazione app gestiti da iOS
- Configurare i criteri di protezione delle app e distribuire app line-of-business su dispositivi non registrati su Intune
- Profili VPN, VPN per app, Wi-Fi, posta elettronica e profili di certificato
- Criteri di conformità
- Accesso condizionale per Azure AD
- Accesso condizionale per Exchange locale
- Registrazione del dispositivo
- Controllo di accesso in base ai ruoli

## <a name="deprecated-features-in-the-azure-portal"></a>Funzionalità deprecate nel portale di Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Supporto per la revisione riga per riga degli identificatori di hardware
Il portale di Azure non supporta la revisione riga per riga di ID hardware per numeri IMEI e numeri di serie Apple. Nella console di Intune classica è possibile importare informazioni da un file con estensione CSV e sovrascrivere i dettagli esistenti con gli identificatori hardware singoli. Il portale di Azure prevede un'unica ed efficiente opzione che sovrascrive in automatico i dettagli per tutti gli identificatori hardware o ignora i nuovi dettagli per gli identificatori esistenti.

#### <a name="how-this-affects-you"></a>Conseguenza sull'utente
Nel portale di Azure l'utente non sarà in grado di decidere, riga per riga, quale IMEI aggiornare. La console di Intune classica continuerà a supportare questa funzionalità.

#### <a name="how-to-get-ready-for-this-change"></a>Come prepararsi a questo cambiamento
Forniamo questa informazione in anticipo in modo tale che, se l'utente ne è interessato, può comunicare il cambiamento ai propri amministratori del supporto. Questa modifica coinciderà con la migrazione al portale di Azure, prevista per la prima metà del 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Supporto per i profili predefiniti di registrazione di dispositivi aziendali in DEP di Apple
Il portale di Azure non supporta il profilo di registrazione di dispositivi aziendali "predefinito" per i numeri di serie del dispositivo DEP di Apple. Questa funzionalità, disponibile nella console di Intune classica, è stata sospesa per evitare che i profili venissero assegnati involontariamente. Nel portale di Azure i numeri di serie sincronizzati da un account DEP di Apple non saranno inizialmente assegnati a un profilo di registrazione di dispositivi aziendali.

#### <a name="how-this-affects-you"></a>Conseguenza sull'utente
Nel portale di Azure non sarà possibile impostare un criterio di profilo predefinito per tutti i dispositivi Apple. La console di Intune classica continuerà a supportare questa funzionalità.

#### <a name="how-to-get-ready-for-this-change"></a>Come prepararsi a questo cambiamento
Forniamo questa informazione in anticipo in modo tale che, se l'utente ne è interessato, può comunicare il cambiamento ai propri amministratori del supporto. Questa modifica coinciderà con la migrazione al portale di Azure, prevista per la prima metà del 2017.

