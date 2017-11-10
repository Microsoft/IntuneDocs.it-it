---
title: Edizione anticipata
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d612f0e3ff3f38d51488818916479e8291c9e453
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2017
---
# <a name="the-early-edition-for-microsoft-intune---november-2017"></a>Edizione anticipata per Microsoft Intune - Novembre 2017

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non condividere queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
>Le seguenti modifiche di Intune sono in fase di sviluppo. Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure


### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Assegnare le app per dispositivi mobili Office 365 a dispositivi iOS e Android usando il tipo di app predefinito <!-- 1332318 -->
Il tipo di app **Predefinito** consente di creare e assegnare in modo semplice le app Office 365 a dispositivi iOS e Android gestiti. Le app includono le app 0365 come Word, Excel, PowerPoint e OneDrive. È possibile assegnare app specifiche al tipo di app e modificare la configurazione delle informazioni sull'app.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Supporto Single Sign-On per iOS <!-- 1333645 -->  
È possibile usare Single Sign-On per gli utenti iOS. Le app iOS codificate per la ricerca delle credenziali dell'utente nel payload Single Sign-on funzionano con questo aggiornamento della configurazione del payload. È anche possibile usare l'UPN e l'ID dispositivo di Intune per configurare il nome dell'entità e l'area di autenticazione.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API di inventario delle app iOS 11 per il rilevamento delle minacce per i dispositivi mobili<!-- 1391759 -->
Intune raccoglie le informazioni degli inventari delle app dei dispositivi personali e aziendali e le rende disponibili per i provider del servizio di rilevamento delle minacce per i dispositivi mobili (MTD, Mobile Threat Detection), ad esempio Lookout for Work. Possono essere raccolti gli inventari delle app dagli utenti di dispositivi iOS 11 e versioni successive.

**Inventario delle app**  
Gli inventari dei dispositivi aziendali e personali iOS 11 e versioni successive vengono inviati al provider del servizio MTD. I dati dell'inventario delle app includono:

 - ID dell'app
 - Versione dell'app
 - Versione breve dell'app
 - Nome dell'app
 - Dimensione del bundle dell'app
 - Dimensione dinamica dell'app
 - Indicazione sulla convalida dell'app
 - Indicazione sulla gestione dell'app

### <a name="audit-updates----1412961---"></a>Aggiornamenti dei controlli <!-- 1412961 -->  
La funzione di controllo di Intune offre un record delle operazioni di modifica correlate a Intune.  Tutte le operazioni di creazione, aggiornamento, eliminazione e attività remota vengono acquisite e conservate per un anno.  Il portale di Azure offre una visualizzazione degli ultimi 30 giorni dei dati di controllo di ogni carico di lavoro a cui è possibile applicare filtri.  Un'API Graph corrispondente consente il recupero dei dati di controllo archiviati dell'ultimo anno. 

La funzione di controllo è disponibile nel gruppo **MONITOR**. Viene visualizzata una voce di menu **Log di controllo** per ogni carico di lavoro.   

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocollo di testo consentito dalle app gestite <!-- 1414050  -->
Le app gestite da Intune App SDK possono inviare messaggi SMS.

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Riavvio remoto del dispositivo iOS (solo supervisionato) <!-- 1424595 -->
È possibile riavviare un dispositivo iOS 10.3 e versioni successive supervisionato usando un'azione del dispositivo. Per altre informazioni sull'uso dell'azione di riavvio del dispositivo, vedere [Riavviare i dispositivi in remoto con Intune](device-restart.md).

> [!Note]  
> Per eseguire questo comando sono necessari un dispositivo supervisionato e il diritto di accesso **Device Lock** (Blocco dispositivo). Il dispositivo viene riavviato immediatamente. I dispositivi iOS bloccati con passcode non si ricollegano a una rete Wi-Fi dopo il riavvio. È possibile che dopo il riavvio non siano in grado di comunicare con il server.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloccare in remoto un dispositivo macOS gestito con Intune <!-- 1437691 -->
È possibile bloccare un dispositivo macOS perso e impostare un PIN di ripristino a 6 cifre. Quando il dispositivo è bloccato, il pannello **Device overview** (Panoramica dispositivo) visualizza il PIN fino a quando non viene inviata un'altra azione del dispositivo.

Per altre informazioni, vedere [Bloccare in remoto i dispositivi gestiti con Intune](device-remote-lock.md).

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Impostazioni della frequenza di creazione di report di Windows Defender Advanced Threat Protection  <!--- 1455974  --->
Il servizio Windows Defender Advanced Threat Protection (WDATP) consente agli amministratori di gestire la frequenza di creazione di report per i dispositivi gestiti. Con la nuova opzione **Accelera la frequenza di creazione di report di telemetria**, WDATP raccoglie i dati e valuta i rischi con maggior frequenza. L'impostazione predefinita per la creazione di report ottimizza velocità e prestazioni. L'aumento della frequenza di creazione di report può essere utile per i dispositivi a rischio elevato. Questa impostazione è disponibile nel profilo **Windows Defender ATP** in **Configurazioni dispositivi**.

### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>Risoluzione dei conflitti di assegnazione modificata per le app di iOS Store <!-- 1480316 -->
Gli utenti finali potrebbero rilevare una modifica alla disponibilità delle app di iOS Store. Attualmente, un'app assegnata a due gruppi con un conflitto tra **Richiesto e disponibile** e **Non applicabile** viene risolta in **Richiesto e disponibile**. Con la modifica, un'app per la quale si verifica questo conflitto verrà risolta in **Non applicabile**.

La modifica elimina la confusione che si verifica quando la stessa app viene assegnata a più gruppi con finalità di app diverse.

Se si vuole rendere disponibile l'app nel portale di Information Worker e nel portale aziendale prima del rilascio di novembre del servizio, sono disponibili due opzioni:

1. Rimuovere l'assegnazione **Non applicabile** per il gruppo.
2. Creare un nuovo gruppo che non contiene membri con la finalità **Richiesto e disponibile** e assegnare il gruppo come **Non applicabile**.

Per altre informazioni, vedere [Come assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

> [!Note]
> Dopo il rilascio non sarà più possibile visualizzare o modificare le assegnazioni delle app MDM (Mobile Device Management) nella console classica di Intune. È possibile tuttavia usare la console di Azure o l'API Graph di Intune per eseguire le assegnazioni delle app.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Gestire i dispositivi Android for Work indipendentemente dai dispositivi Android <!-- 1490731 -->
Intune supporta la gestione della registrazione di dispositivi Android for Work indipendentemente dalla piattaforma Android. Queste impostazioni vengono gestite in **Registrazione del dispositivo** > **Restrizioni registrazione** > **Restrizioni sul tipo di dispositivi**. In precedenza erano disponibili in **Registrazione del dispositivo** > **Registrazione di Android for Work** > **Impostazioni di registrazione per Android for Work**.

Per impostazione predefinita, le impostazioni dei dispositivi Android for Work corrispondono alle impostazioni dei dispositivi Android. Tuttavia, dopo la modifica delle impostazioni Android for Work questa corrispondenza andrà persa.
 
Se si blocca la registrazione dei dispositivi Android for Work personali, solo i dispositivi Android aziendali possono essere registrati come Android for Work.

Durante l'uso delle nuove impostazioni, considerare quanto segue:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work non è mai stata caricata in precedenza
La nuova piattaforma Android for Work è bloccata nelle Restrizioni sul tipo di dispositivi predefinite. Dopo aver caricato la funzionalità, è possibile consentire la registrazione dei dispositivi con Android for Work. A tale scopo, modificare il valore predefinito o creare una nuova restrizione dei tipi di dispositivo per sostituire la restrizione predefinita.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work è stata caricata
Se la registrazione è stata caricata in precedenza, la situazione varia a seconda dell'impostazione selezionata:

| Impostazione | Stato di Android for Work nella restrizione dei tipi di dispositivo predefinita | Note |
| --- | --- | --- |
| **Gestisci tutti i dispositivi come Android** | Bloccato | Tutti i dispositivi Android devono essere registrati senza Android for Work. |
| **Gestisci i dispositivi supportati come Android for Work** | Consentito | Tutti i dispositivi Android che supportano Android for Work devono essere registrati con Android for Work. |
| **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work** | Bloccato | Per sostituire l'impostazione predefinita è stato creato un criterio Restrizione dei tipi di dispositivo separato. Questo criterio definisce i gruppi precedentemente selezionati per consentire la registrazione di Android for Work. Gli utenti inclusi nei gruppi selezionati continueranno a essere autorizzati a registrare i loro dispositivi Android for Work. A tutti gli altri utenti non è consentita la registrazione con Android for Work. |

In tutti i casi, viene mantenuto il regolamento previsto. Per mantenere l'autorizzazione globale o per i singoli gruppi di Android for Work nel proprio ambiente non è necessario eseguire alcuna operazione.

Sebbene la distribuzione di queste modifiche abbia inizio con l'aggiornamento di novembre, potrebbe richiedere del tempo per essere resa esecutiva nel proprio account. Quando queste modifiche vengono rese effettive per il proprio account, si riceverà una notifica di conferma nel portale di Office 365.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Supporto di più connettori del servizio Registrazione dispositivi di rete <!-- 1528104 -->
Il servizio Registrazione dispositivi di rete (NDES, Network Device Enrollment Service) consente ai dispositivi mobili in esecuzione senza credenziali di dominio di ottenere certificati basati sul protocollo SCEP (Simple Certificate Enrollment Protocol). Con questo aggiornamento, saranno supportati più connettori del servizio Registrazione dispositivi di rete.

### <a name="new-scep-profile-details-supported----1559808---"></a>Nuovi dettagli del profilo SCEP supportati <!-- 1559808 -->
Gli amministratori possono configurare impostazioni aggiuntive durante la creazione di un profilo SCEP nelle piattaforme Windows, iOS, macOS e Android.  Gli amministratori possono impostare IMEI, numero di serie o nome comune, inclusa la posta elettronica nel formato del nome soggetto.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurare il PIN di un'app iOS <!-- 1586774 -->
Sarà presto possibile richiedere un PIN per le app iOS di destinazione. È possibile configurare la richiesta e la data di scadenza in giorni del PIN tramite il portale di Azure. Quando necessario, all'utente viene richiesto di impostare e usare un nuovo PIN prima di ottenere l'accesso a un'app iOS. Questa funzionalità è supportata solo dalle app iOS con la protezione dell'app abilitata con Intune App SDK.

### <a name="retain-data-during-a-factory-reset-----1588489---"></a>Mantenere i dati durante il ripristino delle impostazioni predefinite  <!-- 1588489 -->
Verrà aggiunto il supporto di una nuova funzionalità al ripristino delle impostazioni predefinite di Windows. Ora gli amministratori possono specificare se la registrazione del dispositivo e altri dati di provisioning vengono mantenuti nel dispositivo quando viene eseguito il ripristino delle impostazioni predefinite. 
 
Quando viene eseguito il ripristino delle impostazioni predefinite vengono mantenuti i dati seguenti:
- Account utente associati al dispositivo
- Stato del computer (aggiunta a un dominio, AADJ)
- Registrazione MDM
- App installate OEM (app dello Store e Win32)
- Profilo utente
- Dati utente esterni al profilo utente
- Accesso automatico dell'utente
 
I dati seguenti non vengono mantenuti:
- File dell'utente
- App installate dell'utente (app dello Store e Win32)
- Impostazioni del dispositivo non predefinite 

### <a name="app-install-status-report-now-a-bar-chart----1249446---"></a>Report sullo stato di installazione delle app visualizzato come grafico a barre <!-- 1249446 -->  
Il report **Stato di installazione dell'app** accessibile per ogni app attraverso l'elenco **App** nel carico di lavoro **App per dispositivi mobili** verrà visualizzato come grafico a barre.

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Aggiungere "Trova il mio iPhone" per i dispositivi personali <!--1427287-->
Sarà possibile verificare se i dispositivi iOS hanno il Blocco attivazione attivato. Questa funzionalità era disponibile in precedenza nel portale classico di Intune.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrizioni di registrazione assegnate ai gruppi <!-- 747598 -->
L'amministratore di Intune potrà creare restrizioni di registrazione Tipo di dispositivo e Limite di dispositivi personalizzate per i gruppi di utenti.
 
Il portale di Azure di Intune consente di creare fino a 25 istanze di ogni tipo di restrizione che possono essere successivamente assegnate ai gruppi di utenti. Le restrizioni assegnate ai gruppi sostituiscono le restrizioni predefinite.
 
Tutte le istanze di un tipo di restrizione vengono mantenute in un elenco nell'ordine. L'ordine definisce un valore di priorità per la risoluzione dei conflitti. Un utente interessato da più istanze di restrizione viene limitato solo dall'istanza con il valore di priorità più alto. È possibile modificare la priorità di un'istanza specifica trascinandola in una posizione diversa nell'elenco. 
 
Questa funzionalità verrà rilasciata con la migrazione delle impostazioni di Android for Work dal menu di registrazione di Android for Work al menu Restrizioni registrazione. Poiché la migrazione può richiedere diversi giorni, è possibile che l'account venga aggiornato per altre parti del rilascio di novembre prima che l'assegnazione dei gruppi appaia abilitata per le restrizioni di registrazione.

### <a name="windows-10-update-ring-assignments-are-displayed----1621837---"></a>Assegnazioni degli anelli di aggiornamento di Windows 10 visualizzate <!-- 1621837 -->
Durante la **Risoluzione dei problemi** per l'utente visualizzato le assegnazioni degli anelli di aggiornamento di Windows 10 saranno visibili.  



<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->   
Usando Azure Active Directory (Azure AD) è possibile limitare l'accesso ai siti Web su dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure.

### <a name="troubleshoot-enrollment-issues------746324----"></a>Risolvere i problemi di registrazione  <!--- 746324 --->  
L'area di lavoro Risoluzione dei problemi visualizza i problemi di registrazione dell'utente. Informazioni dettagliate sul problema e i passaggi suggeriti per la correzione possono essere utili ad amministratori e operatori di help desk per la risoluzione dei problemi. Alcuni problemi di registrazione non vengono rilevati ed è possibile che per alcuni errori non siano disponibili suggerimenti per la correzione.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Gli amministratori possono ora configurare le impostazioni del firewall in un dispositivo usando un profilo di configurazione del dispositivo <!-- 951708 -->   
Gli amministratori possono attivare il firewall per i dispositivi e anche configurare diversi protocolli per le reti di dominio, private e pubbliche.  Le impostazioni del firewall sono disponibili nel profilo "Endpoint Protection".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard consente di proteggere i dispositivi dai siti Web non attendibili specificati dall'organizzazione <!-- 958257 -->   
Gli amministratori possono definire i siti come "attendibili" o "aziendali" usando un flusso di lavoro Windows Information Protection o il nuovo profilo "limite di rete" disponibile nelle configurazioni del dispositivo. I siti non elencati nel limite di rete attendibile del dispositivo Windows 10 a 64 bit e visualizzati con Microsoft Edge vengono invece aperti in un browser all'interno di un computer virtuale Hyper-V.

Application Guard è disponibile nei profili di configurazione del dispositivo, nel profilo "Endpoint Protection". Nel profilo gli amministratori possono configurare l'iterazione tra il browser virtualizzato e il computer host, i siti non attendibili e i siti attendibili e l'archiviazione dei dati nel browser virtualizzato. Per usare Application Guard in un dispositivo, è necessario innanzitutto configurare un limite di rete. È importante definire un solo limite di rete per dispositivo.  

### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Guard in Windows 10 Enterprise consente di considerare attendibili solo le app autorizzate <!-- 1031096 -->    
Considerate le migliaia di nuovi file dannosi creati ogni giorno, l'uso di un sistema di rilevamento antivirus basato su firma per la protezione da software dannoso potrebbe non offrire più una difesa adeguata dai nuovi attacchi. Con Windows Defender Application Guard in Windows 10 Enterprise è possibile modificare la configurazione del dispositivo passando da una modalità in cui vengono considerate attendibili tutte le app a eccezione di quelle bloccate da un antivirus o da un'altra soluzione di sicurezza a una modalità in cui il sistema operativo considera attendibili solo le app autorizzate dalla propria organizzazione. È possibile impostare le app come attendibili in Windows Defender Application Guard.

Usando Intune è possibile configurare i criteri di controllo delle applicazioni in modalità "solo controllo" o in modalità di imposizione. In modalità "solo controllo" le app non vengono bloccate. La modalità "solo controllo" registra tutti gli eventi nei log del client locali. È anche possibile specificare se autorizzare l'esecuzione solo dei componenti Windows e delle app di Windows Store o di altre app affidabili in base a quanto definito da Intelligent Security Graph.

### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Nuova pagina dello stato di registrazione per le registrazioni Windows 10 <!--1063201-->    
È ora possibile configurare un messaggio di saluto che viene visualizzato quando gli utenti registrano i dispositivi Windows 10. Usare la **schermata Stato di registrazione** per configurare un messaggio personalizzato e un collegamento ipertestuale da visualizzare agli utenti finali che registrano dispositivi Windows 10.  La **schermata Stato di registrazione** offre agli utenti finali anche una visualizzazione dello stato delle impostazioni dei criteri applicati al loro dispositivo.  

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender Exploit Guard è un nuovo set di funzionalità di prevenzione intrusioni per Windows 10 <!-- 1063615 -->   
Windows Defender Exploit Guard include regole personalizzate per ridurre la vulnerabilità agli exploit delle applicazioni, evitare le minacce di macro e script, blocca automaticamente le connessioni di rete verso indirizzi IP con reputazione negativa ed è in grado di proteggere i dati da ransomware e minacce sconosciute. Windows Defender Exploit Guard include i componenti seguenti:

- La **Riduzione della superficie di attacco** offre regole che consentono di evitare le minacce di macro, script e posta elettronica.
- L'**Accesso controllato alle cartelle** blocca automaticamente l'accesso al contenuto delle cartelle protette.
- Il **filtro di rete** blocca la connessione in uscita di tutte le app verso indirizzi IP o domini con reputazione negativa.
- La **protezione dagli exploit** offre limitazioni di memoria, flusso di controllo e criteri che è possibile usare per proteggere un'applicazione dagli exploit.

### <a name="app-conditional-launch-support----1193313---"></a>Supporto di avvio condizionale all'app <!-- 1193313 -->
Gli amministratori IT possono ora impostare un requisito usando il portale di amministrazione di Azure per applicare un passcode anziché un PIN numerico PIN attraverso la gestione delle applicazioni mobili (MAM) all'avvio dell'applicazione. Se il requisito viene configurato, all'utente viene richiesto di impostare e usare un passcode prima di accedere alle applicazioni con supporto MAM. Un passcode è un PIN numerico con almeno un carattere speciale o una lettera maiuscola o minuscola. In questa versione di Intune la funzione è abilitata **solo in iOS**. Il supporto di Intune per i passcode è simile a quello dei PIN numerici: viene impostata una lunghezza minima e sono consentiti caratteri e sequenze ripetuti. Questa funzionalità richiede il supporto delle applicazioni (WXP, Outlook, Managed Browser, Yammer) per l'integrazione di Intune APP SDK con il codice per la funzionalità in modo che le impostazioni di passcode possano essere applicate nelle applicazioni di destinazione.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Numero di versione delle app line-of-business nel report sullo stato dell'installazione del dispositivo <!-- 1233999 -->  
Il report sullo stato dell'installazione del dispositivo visualizza il numero di versione dell'app per le app line-of-business per iOS e Android. Queste informazioni possono essere usate per la risoluzioni dei problemi delle app o per individuare i dispositivi che eseguono versioni delle app non aggiornate.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Co-gestione per i dispositivi Windows 10  <!-- 1243445 -->
La co-gestione è una soluzione che rappresenta un ponte tra la gestione tradizionale e quella moderna e consente di effettuare la transizione con un approccio graduale. La co-gestione è fondamentalmente una soluzione in cui i dispositivi Windows 10 vengono gestiti contemporaneamente da Configuration Manager e Microsoft Intune e aggiunti ad Active Directory (AD) e Azure Active Directory (Azure AD).  Questa configurazione offre la possibilità di effettuare una modernizzazione graduale con un ritmo adatto alla propria organizzazione nei casi in cui una transizione immediata non è possibile.  

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Impostare l'accesso per le app mediante una patch di protezione Android minima nel dispositivo<!-- 1278463 -->   
L'amministratore può definire la patch di protezione Android minima che deve essere installata nel dispositivo per poter accedere a un'applicazione gestita in un account gestito.

> [!Note]  
> Questa funzionalità limita solo le patch di protezione rilasciate da Google nei dispositivi Android 6.0 e versioni successive.

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nuove impostazioni delle limitazioni del dispositivo per Windows 10      <!-- 1308850 -->
-    Messaggistica (solo dispositivi mobili): disabilitare il test o i messaggi MMS
-    Password: impostazioni per l'abilitazione di FIPS e l'uso dei dispositivi secondari Windows Hello per l'autenticazione 
-    Visualizzazione: impostazioni per attivare o disattivare il ridimensionamento del programma GDI per le app legacy


### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Limitazioni del dispositivo per la modalità a tutto schermo per Windows 10 <!-- 1308872 -->   
È possibile impostare una limitazione per la modalità a tutto schermo per gli utenti dei dispositivi Windows 10 che limita gli utenti a un set di app predefinite.  A tale scopo, creare un profilo di limitazione del dispositivo Windows 10 e specificare le impostazioni della modalità a tutto schermo.

La modalità a tutto schermo supporta due modalità: la modalità **applicazione singola** che consente all'utente di eseguire una sola app e la modalità **app multiple** che consente l'accesso a più app.  Definire l'account utente e il nome del dispositivo che determinano le app supportate.  Dopo aver eseguito l'accesso, l'utente sarà limitato alle app definite.  Per altre informazioni, vedere [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (Provider del servizio di configurazione AssignedAccess). 

Per la modalità a tutto schermo sono necessari i requisiti seguenti:

- Intune deve essere l'autorità MDM.
- Le app devono essere già installate nel dispositivo di destinazione.
- Il [provisioning](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions) del dispositivo deve essere stato eseguito correttamente.

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuovo profilo di configurazione del dispositivo per la creazione di limiti di rete <!-- 1311967 -->   
È stato creato un profilo di configurazione del dispositivo denominato **limite di rete** disponibile con gli altri profili di configurazione. Usare questo profilo per definire le risorse online da considerare aziendali e affidabili. È necessario definire un limite di rete per un dispositivo *prima* di usare funzionalità come Windows Defender Application Guard e Windows Information Protection nel dispositivo. È importante definire un solo limite di rete per dispositivo.

È possibile definire le risorse cloud aziendali, gli intervalli di indirizzi IP e i server proxy interni da considerare attendibili. Il limite di rete definito può essere utilizzato da altre funzionalità, ad esempio Windows Defender Application Guard e Windows Information Protection.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Due impostazioni aggiuntive per Windows Defender Antivirus <!-- 1338409 -->  
**Livello di blocco di file**

| | |
|---|---|
| Non configurato | **Non configurato** usa il livello di blocco predefinito di Windows Defender Antivirus e offre un rilevamento sicuro senza aumentare il rischio di rilevare file legittimi. |
| Alto | **Alto** applica un livello di rilevamento elevato.
| Elevato +  | **Elevato +** offre il livello Alto con misure di protezione aggiuntive che potrebbero influire sulle prestazioni del client.
| Tolleranza zero  | **Tolleranza zero** blocca tutti gli eseguibili sconosciuti. |

Sebbene sia improbabile, l'impostazione su **Alto** potrebbe causare il rilevamento di file legittimi.
È consigliabile impostare il livello di blocco di file sul valore predefinito **Non configurato**.

**Estensione del timeout per l'analisi dei file dal cloud**  

| | |
|--|--|
| Numero di secondi (0-50) | Specificare la quantità massima di tempo per la quale Windows Defender Antivirus deve bloccare un file in attesa di un risultato dal cloud. La quantità predefinita è 10 secondi: il tempo specificato con questa opzione (fino a un massimo di 50 secondi) viene aggiunto ai 10 secondi. Nella maggior parte dei casi l'analisi richiede molto meno tempo rispetto al tempo massimo. L'estensione della quantità di tempo consente al cloud di analizzare nel dettaglio i file sospetti. È consigliabile abilitare questa impostazione e specificare almeno 20 secondi aggiuntivi. |


### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Supporto dell'autorità di certificazione Symantec Cloud  <!-- 1333638 -->    
Intune supporta ora l'autorità di certificazione Symantec Cloud che consente al Connettore di certificati di Intune di rilasciare certificati PKCS dall'autorità di certificazione Symantec Cloud nei dispositivi gestiti Intune. Se si usa già il Connettore di certificati di Intune con l'autorità di certificazione Microsoft è possibile usare la configurazione esistente del Connettore di certificati di Intune per aggiungere il supporto dell'autorità di certificazione Symantec.



### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix aggiunta per i dispositivi Windows 10 <!-- 1512457 -->  
I clienti possono configurare la VPN Citrix per i dispositivi Windows 10. Durante la configurazione di una VPN per Windows 10 e versioni successive è possibile scegliere la VPN Citrix nell'elenco *Selezionare un tipo di connessione* nel pannello **VPN di base**.

> [!Note]
> Configurazione Citrix per iOS e Android.



<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Supporto di Google Play Protect in Android <!-- 908720  -->  
Con il rilascio di Android Oreo, Google introduce un gruppo di funzionalità di sicurezza denominato Google Play Protect che consente a utenti e organizzazioni di eseguire app e immagini Android sicure. Intune supporta le funzionalità di Google Play Protect, inclusa l'attestazione remota SafetyNet.  Gli amministratori possono impostare requisiti per i criteri di conformità che richiedono la configurazione e l'integrità di Google Play Protect. L'**attestazione dispositivo SafetyNet** richiede che il dispositivo si connetta a un servizio Google per verificare che il dispositivo sia integro e non compromesso. Gli amministratori possono anche definire un'impostazione del profilo di configurazione per far sì che Android for Work richieda la verifica delle app installate da parte di Google Play Services.  L'accesso condizionale può impedire agli utenti di accedere alle risorse aziendali se un dispositivo non è conforme ai requisiti di Google Play Protect. 


### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Supporto dei criteri di aggiornamento edizione di Windows 10 <!-- 903672(archived), 1119689 -->  
È possibile creare criteri di aggiornamento edizione di Windows 10 per l'aggiornamento di dispositivi Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Per informazioni dettagliate sugli aggiornamenti edizione di Windows 10, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>Azioni per la non conformità <!--730266  846515 -->     
*Azioni per la non conformità* è una nuova funzionalità dei criteri di conformità che consente di intervenire sui dispositivi non conformi. È possibile specificare una o più azioni e il periodo di tempo in cui devono essere eseguite tali azioni. Ad esempio, è possibile segnalare immediatamente agli utenti i dispositivi non conformi non appena diventano non conformi, tramite posta elettronica, oppure è possibile impedire ai dispositivi non conformi di accedere alle risorse aziendali dopo un periodo di tolleranza di 3 giorni tramite l'accesso condizionale.

### <a name="android-for-work-support-for-lookout----1087312---"></a>Supporto di Android for Work per Lookout <!-- 1087312 -->   
Il connettore di Intune con Lookout supporterà i dispositivi Android for Work quando si usa l'app Lookout for Work. È possibile distribuire l'app Lookout all'interno o all'esterno del contenitore.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Protezione app di Intune e strumenti di sviluppo MDX Citrix <!-- 709185 -->
È possibile gestire i dispositivi e le app usando in combinazione Citrix XenMobile MDX e Microsoft Intune. Ciò consente di gestire le app con i criteri di protezione delle app di Intune usando allo stesso tempo la tecnologia mVPN di Citrix.

È disponibile un repository di codice che contiene lo strumento di wrapping delle app di Intune e Intune App SDK per iOS e Android, per l'integrazione con la tecnologia mVPN MDX di Citrix.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale<!-- 676614 -->   
È possibile avere più ruoli server Accesso client per Exchange Connector locale. Ad esempio, se il server Accesso client principale smette di funzionare, Exchange Connector riceve una query per eseguire il fallback in altri server Accesso client. Questa funzionalità garantisce che il servizio non venga interrotto.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->   
Sarà disponibile il Management Pack di System Center Operations Manager per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questo Management Pack consente di eseguire il monitoraggio di Intune in diversi modi quando è necessario risolvere i problemi.





## <a name="intune-apps"></a>App di Intune

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Consentire agli utenti di usare l'app del portale aziendale per Android <!---1573324, 1573150, 1558616, 1564878--->
L'app del portale aziendale per Android include ora istruzioni per gli utenti finali per consentire di comprendere e, dove possibile, risolvere autonomamente nuovi casi d'uso. 

- Viene visualizzato un nuovo messaggio in cui viene comunicato che sono stati distribuiti nuovi criteri di conformità per la crittografia ma che il [produttore del dispositivo non esegue la crittografia del dispositivo](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android) in base a [linee guida consigliate di Google](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean).
- Gli utenti finali verranno indirizzati al (portale di Azure Active Directory)[https://account.activedirectory.windowsazure.com/r/#/profile] per la rimozione di un dispositivo se è stato raggiunto il numero massimo di dispositivi che sono autorizzati ad aggiungere. 
- Agli utenti finali verranno indicati i passaggi da eseguire per [risolvere gli errori di attivazione sui dispositivi Samsung KNOX](https://go.microsoft.com/fwlink/?linkid=859718) o per [disattivare la modalità di risparmio di energia](/intune-user-help/power-saving-mode-android). Se nessuna delle soluzioni proposte corregge il problema, verrà descritto come [inviare i log a Microsoft](/intune-user-help/send-logs-to-microsoft-ios). 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nuova azione 'Risolvi' disponibile per i dispositivi Android <!---1583480--->
L'app del portale aziendale per Android include ora una nuova azione 'Risolvi' nella pagina _Aggiorna impostazioni del dispositivo_. La selezione di questa opzione indirizza l'utente finale direttamente all'impostazione che rende il dispositivo non conforme. L'app del portale aziendale per Android supporta attualmente questa opzione per le impostazioni di [passcode del dispositivo](/intune-user-help/set-your-pin-or-password-android), [crittografia del dispositivo](/intune-user-help/encrypt-your-device-android), [debug USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [origini sconosciute](/intune-user-help/you-need-to-turn-off-unknown-sources-android). 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Reindirizzamento degli utenti macOS alla nuova app del portale aziendale <!--1380728-->   
Quando un utente finale accede al sito Web del portale aziendale per registrare il proprio dispositivo macOS, l'utente viene indirizzato al download della nuova app del portale aziendale per macOS per completare il processo. Ciò si verifica per i dispositivi macOS che usano OS X El Capitan 10.11 o versioni successive. 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Le app disponibili con o senza registrazione possono essere ora installate senza richiesta di registrazione. <!-- 1334712 -->
Le app aziendali rese disponibili con o senza registrazione nell'app del portale aziendale Android possono essere installate senza richiesta di registrazione.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Supporto di Intune Managed Browser per iOS e Android <!-- 1374196 -->
A partire da ottobre 2017, l'app Intune Managed Browser per Android supporta solo i dispositivi che eseguono Android 4.4 e versioni successive. L'app Intune Managed Browser per iOS supporta solo i dispositivi che eseguono iOS 9.0 e versioni successive. Le versioni precedenti di Android e iOS saranno in grado di continuare a usare Managed Browser, ma non sarà possibile installare nuove versioni dell'app e le funzionalità dell'app potrebbero non essere tutte disponibili. Si consiglia di eseguire l'aggiornamento di questi dispositivi a una versione supportata del sistema operativo.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Messaggio di errore migliorato quando un utente raggiunge il numero massimo di dispositivi di cui è consentita la registrazione <!-- 1270370 -->
Invece di un messaggio di errore generico, gli utenti finali vedranno un messaggio di errore descrittivo e interattivo: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin." (È stato raggiunto il numero massimo di dispositivi consentiti dall'amministratore IT. Rimuovere un dispositivo registrato o richiedere assistenza all'amministratore IT.)




## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.




### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
