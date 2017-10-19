---
title: Edizione anticipata
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: abb5612545174e3fd134c38fb763e02d379b50d0
ms.sourcegitcommit: b330045a4f9a807e6e2772c4ed4e1e1148e1f1f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2017
---
# <a name="the-early-edition-for-microsoft-intune---october-2017"></a>Edizione anticipata per Microsoft Intune - Ottobre 2017

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

### <a name="co-management-for-windows-10-devices-----124445---"></a>Co-gestione per i dispositivi Windows 10  <!-- 124445 -->
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
| Alta | **Alto** applica un livello di rilevamento elevato.
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


### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Miglioramenti del flusso di lavoro di installazione dei dispositivi nel Portale aziendale <!--1490692-->  
È stato migliorato il flusso di lavoro di configurazione dei dispositivi nell'app Portale aziendale per Android. Il linguaggio è più semplice e specifico della società e verranno inserite schermate dove possibile. 

### <a name="block-unsupported-samsung-knox-device-activation------1490695----"></a>Bloccare l'attivazione di dispositivi Samsung Knox non supportata <!--- 1490695 --->  
L'app Portale aziendale tenta l'attivazione Samsung KNOX durante la registrazione MDM solo se il dispositivo da attivare è presente nell'[elenco dei dispositivi KNOX supportati](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Questa limitazione consente di evitare errori di attivazione KNOX che impediscono la registrazione MDM. I dispositivi che non supportano l'attivazione Samsung KNOX vengono registrati come dispositivi Android standard. Tra i dispositivi Samsung, non tutti hanno un numero di modello che supporta KNOX. Verificare la compatibilità Knox presso il rivenditore del dispositivo prima dell'acquisto e della distribuzione di dispositivi Samsung.

I modelli Samsung presenti nell'elenco seguente non supportano KNOX e vengono registrati come dispositivi Android nativi dall'app Portale aziendale per Android.

| **Nome dispositivo** | **Numeri modello dispositivo** |
| --- | --- |
| Galaxy A3 | SM-A300G<br>SM-A310Y<br>SM-A320FL |
| Galaxy A5 | SM-A500G |
| Galaxy Alpha | SM-G850M |
| Galaxy Avant | SM-G386T |
| Galaxy C9/C9 Pro | SM-C900F |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime | SM-G530M |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M<br>SM-J320W8 |
| Galaxy J5 | SM-J500G |
| Galaxy J7 | SM-J710F |
| Galaxy J7 Prime | SM-J727T1 |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 5 | SM-N920G<br>SM-N920I<br>SM-N920W8 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy NotePRO 12.2&quot; | SM-P902 |
| Galaxy On5 | SM-G570MSM-G570Y |
| Galaxy On7 | SM-G600FY<br>SM-G610M<br>SM-G610Y |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Active | GT-I9295 |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W<br>SM-G900M |
| Galaxy S5 Neo | SM-G903M |
| Galaxy S6 Edge | 404SCSM-G925I<br>SM-G928G |
| Galaxy Tab A 7.0&quot; | SM-T280SM-T285 |
| Galaxy Tab A 9.7&quot; | SM-P555M |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116SM-T210SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |


### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix aggiunta per i dispositivi Windows 10 <!-- 1512457 -->  
I clienti possono configurare la VPN Citrix per i dispositivi Windows 10. Durante la configurazione di una VPN per Windows 10 e versioni successive è possibile scegliere la VPN Citrix nell'elenco *Selezionare un tipo di connessione* nel pannello **VPN di base**.

> [!Note]
> Configurazione Citrix per iOS e Android.





<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Supporto di Google Play Protect in Android <!-- 908720  -->  
Con il rilascio di Android Oreo, Google introduce un gruppo di funzionalità di sicurezza denominato Google Play Protect che consente a utenti e organizzazioni di eseguire app e immagini Android sicure. Intune supporta le funzionalità di Google Play Protect, inclusa l'attestazione remota SafetyNet.  Gli amministratori possono impostare requisiti per i criteri di conformità che richiedono la configurazione e l'integrità di Google Play Protect. L'**attestazione dispositivo SafetyNet** richiede che il dispositivo si connetta a un servizio Google per verificare che il dispositivo sia integro e non compromesso. Gli amministratori possono anche definire un'impostazione del profilo di configurazione per far sì che Android for Work richieda la verifica delle app installate da parte di Google Play Services.  L'accesso condizionale può impedire agli utenti di accedere alle risorse aziendali se un dispositivo non è conforme ai requisiti di Google Play Protect. 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo <!-- 1333292 -->
È possibile usare [criteri personalizzati per dispositivi Android](custom-settings-android.md) per impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo.
A tale scopo, configurare criteri personalizzati di Android impostando l'URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange, su **TRUE** e quindi assegnandolo ai gruppi necessari.

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visualizzare le assegnazioni dei criteri di protezione delle app per la risoluzione dei problemi <!--  1475003 -->
In questa versione futura verrà aggiunta un'opzione per i **criteri di protezione delle app** all'elenco a discesa **Assegnazioni** disponibile nel pannello della risoluzione dei problemi. Sarà ora possibile selezionare Criteri di protezione delle app per visualizzare i criteri assegnati agli utenti selezionati.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creare app iOS limitate ad Apple App Store di aree specifiche<!-- 1281692 -->
Sarà possibile specificare le impostazioni locali del paese durante la creazione di un'app gestita da Apple App Store.

> [!NOTE]  
> Attualmente è possibile creare solo app gestite di Apple App Store presenti nello Store degli Stati Uniti.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selezionare l'Apple Store del paese per la sincronizzazione delle app VPP <!-- 1332311 -->  
È possibile configurare lo Store del paese per il Volume Purchase Program (VPP) quando si carica il token VPP. Intune sincronizza le app VPP per tutte le impostazioni locali dello Store del paese VPP specificato.

> [!NOTE]  
> Attualmente Intune sincronizza solo le app VPP dello Store VPP del paese corrispondenti all'impostazione locale di Intune in cui è stato creato il tenant di Intune.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Aggiornare le app VPP iOS concesse in licenza a utenti e dispositivi <!-- 1305564 -->  
Sarà possibile configurare il token VPP iOS per aggiornare tutte le app acquistate per tale token tramite il servizio Intune. Intune rileverà gli aggiornamenti delle app VPP nell'App Store e li invierà automaticamente al dispositivo quando questo si connette.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team <!--- 1308838  -->
Sono state aggiunte molte nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team per la gestione dei dispositivi Surface Hub.
Per altre informazioni su questo profilo, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Supporto dei criteri di aggiornamento edizione di Windows 10 <!-- 903672(archived), 1119689 -->  
È possibile creare criteri di aggiornamento edizione di Windows 10 per l'aggiornamento di dispositivi Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Per informazioni dettagliate sugli aggiornamenti edizione di Windows 10, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Supporto remoto per dispositivi Windows e Windows Mobile <!-- 1070473 -->    
Intune potrà usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per poter offrire assistenza remota agli utenti che eseguono dispositivi Windows e Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analizzare dispositivi con Windows Defender <!-- 1280988  1280990   -->
Sarà possibile eseguire un'**analisi veloce**, un'**analisi completa** e **aggiornare le firme** con Windows Defender Antivirus nei dispositivi Windows 10 gestiti. Dal pannello della panoramica del dispositivo, scegliere l'azione da eseguire nel dispositivo. Verrà chiesto di confermare l'azione prima che il comando venga inviato al dispositivo. 

**Analisi veloce**: l'analisi veloce analizza i percorsi in cui il malware si registra per l'avvio, ad esempio le chiavi del Registro di sistema e le cartelle di avvio di Windows note. L'analisi veloce richiede in media cinque minuti. Unita all'impostazione della **protezione in tempo reale Always On** che analizza i file quando vengono aperti, chiusi e ogni volta che un utente passa a una cartella, l'analisi veloce consente di fornire protezione da software dannoso che potrebbe trovarsi nel sistema o nel kernel. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Analisi completa**: l'analisi completa può essere utile nei dispositivi in cui sono state riscontrate minacce malware per identificare se sono presenti componenti inattivi che richiedono una pulizia più approfondita ed è utile per l'esecuzione di analisi su richiesta. L'analisi completa può richiedere un'ora. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Aggiornare le firme**: il comando di aggiornamento delle firme aggiorna le definizioni e le firme malware di Windows Defender Antivirus, garantendo l'efficacia nel rilevamento di malware. Questa funzionalità è applicabile solo ai dispositivi Windows 10 con connettività Internet. 

### <a name="bitlocker-device-configuration----1397398---"></a>Configurazione di BitLocker per il dispositivo <!-- 1397398 -->  
**Crittografia di Windows > Impostazioni di base** includerà la nuova impostazione **Avviso per la crittografia dischi di altro tipo** che consente di disabilitare il [prompt di avviso](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) per crittografie disco di altro tipo che possono essere in uso nel dispositivo dell'utente.  Il prompt di avviso richiede il consenso dell'utente prima di configurare BitLocker nel dispositivo e blocca la configurazione di BitLocker fino alla conferma dell'utente finale.  La nuova impostazione disabilita l'avviso per l'utente finale.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Passaggio del portale aziendale per Windows 8.1 e Windows Phone 8.1 alla modalità di mantenimento <!--1428681-->
A partire da ottobre 2017, le app del portale aziendale per Windows 8.1 e Windows Phone 8.1 passeranno alla modalità di mantenimento. Le app e gli scenari esistenti, ad esempio la registrazione e la conformità, continueranno a essere supportati per queste piattaforme. Queste app rimarranno disponibili per il download tramite i canali di rilascio esistenti, ad esempio Microsoft Store. 

Nella modalità di mantenimento, queste app ricevono solo aggiornamenti della sicurezza critici. Non verranno rilasciati altri aggiornamenti o funzionalità per queste app. Per le nuove funzionalità è consigliabile aggiornare i dispositivi a Windows 10 o Windows 10 Mobile. 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloccare la funzionalità di copia e incolla tra i profili di lavoro e i profili personali in Android for Work <!-- 1098994 -->   
È possibile configurare il profilo di lavoro di Android for Work per bloccare l'operazione di copia e incolla tra le app di lavoro e le app personali. Questa nuova impostazione è disponibile nel profilo **Limitazioni del dispositivo** per la piattaforma **Android for Work** in **Impostazioni del profilo di lavoro**.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuovi comportamenti dell'app del portale aziendale per Android con i profili di lavoro <!---1485783--->
Quando si registra un dispositivo Android for Work con un profilo di lavoro, è l'app del portale aziendale nel profilo di lavoro a eseguire attività di gestione nel dispositivo. A meno che non si usi un'app abilitata per MAM nel profilo personale, l'app del portale aziendale per Android non è più utile. Per migliorare l'esperienza con i profili di lavoro, Intune nasconderà automaticamente l'app del portale aziendale personale dopo la registrazione del profilo di lavoro.

L'app del portale aziendale per Android può essere abilitata in qualsiasi momento nel profilo personale passando al [portale aziendale in Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e selezionando **Abilita**.

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Componenti aggiuntivi MAM di Intune e Outlook per Android <!-- 1450688 -->
Tra alcune settimane, il team di Office annuncerà componenti aggiuntivi per Outlook in Android. Questo set di funzionalità aggiuntive è già presente in Outlook in Windows, iOS, Web e Mac. Poiché i componenti aggiuntivi vengono gestiti tramite Exchange, gli utenti potranno condividere dati e messaggi in Outlook e applicazioni aggiuntive non gestite, a meno che l'accesso ai componenti aggiuntivi non venga disattivato dall'amministratore di Exchange. 

Per gestire le autorizzazioni di accesso ai componenti aggiuntivi, rivolgersi all'amministratore di Exchange per verificare che i criteri di protezione dati MAM vengano applicati ai componenti aggiuntivi.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se i criteri di Exchange sono già impostati per impedire il caricamento o l'installazione di componenti aggiuntivi da parte dell'utente, non proseguire la lettura. I criteri MAM verranno applicati come previsto. Se in MAM sono stati tuttavia impostati criteri per limitare le operazioni Taglia, Copia e Incolla all'interno di Outlook in Android e i criteri per i componenti aggiuntivi non sono stati impostati in Exchange, gli utenti potranno installare componenti aggiuntivi in Outlook per impostazione predefinita. Questi componenti aggiuntivi possono accedere al corpo del messaggio, all'oggetto e ad altre proprietà del messaggio. Per impedire all'utente di installare componenti aggiuntivi, l'amministratore di Exchange deve rimuovere i ruoli "App del Marketplace" e "App personalizzate".

La modifica dell'impostazione in Exchange verrà applicata ad Outlook in Windows, iOS, Web, Mac e Mobile. 

#### <a name="what-do-i-need-to-do"></a>Cosa fare
Verificare subito i criteri di Exchange. Informare lo staff IT e il supporto tecnico. Contattare il team di supporto per eventuali dubbi o domande specifiche. 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Raccolta di entità di associazione dei dispositivi degli utenti aggiunta al modello di dati di Data Warehouse di Intune<!-- 1187917 -->
Sarà possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi. Il modello di dati è accessibile tramite il file di Power BI (PBIX) recuperato dalla pagina Data warehouse di Intune, tramite l'endpoint OData oppure sviluppando un client personalizzato.




<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>Azioni per la non conformità <!--730266  846515 -->     
*Azioni per la non conformità* è una nuova funzionalità dei criteri di conformità che consente di intervenire sui dispositivi non conformi. È possibile specificare una o più azioni e il periodo di tempo in cui devono essere eseguite tali azioni. Ad esempio, è possibile segnalare immediatamente agli utenti i dispositivi non conformi non appena diventano non conformi, tramite posta elettronica, oppure è possibile impedire ai dispositivi non conformi di accedere alle risorse aziendali dopo un periodo di tolleranza di 3 giorni tramite l'accesso condizionale.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuovo report che elenca i dispositivi iOS con versioni precedenti di iOS <!-- 1352223 -->
Il report **Out-of-date iOS Devices** (Dispositivi iOS non aggiornati) sarà disponibile dall'area di lavoro **Aggiornamenti software**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento di iOS e con aggiornamenti disponibili. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente. 

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10
<!--- 978575, 1308849, -->
Sono state aggiunte nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 nella categoria Windows Defender SmartScreen.

Per informazioni dettagliate sul profilo di restrizione dei dispositivi Windows 10, vedere [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).

### <a name="android-for-work-support-for-lookout----1087312---"></a>Supporto di Android for Work per Lookout <!-- 1087312 -->   
Il connettore di Intune con Lookout supporterà i dispositivi Android for Work quando si usa l'app Lookout for Work. È possibile distribuire l'app Lookout all'interno o all'esterno del contenitore.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Protezione app di Intune e strumenti di sviluppo MDX Citrix <!-- 709185 -->
È possibile gestire i dispositivi e le app usando in combinazione Citrix XenMobile MDX e Microsoft Intune. Ciò consente di gestire le app con i criteri di protezione delle app di Intune usando allo stesso tempo la tecnologia mVPN di Citrix.

È disponibile un repository di codice che contiene lo strumento di wrapping delle app di Intune e Intune App SDK per iOS e Android, per l'integrazione con la tecnologia mVPN MDX di Citrix.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuovo partner di Mobile Threat Defense  <!-- 954681 -->
È ora possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Zimperium, una soluzione di Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Zimperium. È possibile configurare criteri di accesso condizionale EMS in base alla valutazione dei rischi di Zimperium abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale<!-- 676614 -->   
È possibile avere più ruoli server Accesso client per Exchange Connector locale. Ad esempio, se il server Accesso client principale smette di funzionare, Exchange Connector riceve una query per eseguire il fallback in altri server Accesso client. Questa funzionalità garantisce che il servizio non venga interrotto.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->   
Sarà disponibile il Management Pack di System Center Operations Manager per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questo Management Pack consente di eseguire il monitoraggio di Intune in diversi modi quando è necessario risolvere i problemi.


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fine del supporto per Android 4.3 e versioni precedenti <!---1171127, 1326920 --->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati prima dell'inizio del mese di ottobre non potranno accedere al Portale aziendale o a tali app. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.


## <a name="intune-apps"></a>App di Intune

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Miglioramento delle linee guida per la richiesta di accesso ai contatti nei dispositivi Android <!--1484985-->   
L'app Portale aziendale per Android richiede spesso all'utente finale di accettare l'autorizzazione per i contatti. Se un utente finale rifiuta l'accesso, viene visualizzata una notifica in-app che avvisa dell'autorizzazione per l'accesso condizionale.

### <a name="secure-startup-remediation-for-android---1490712--"></a>Correzione dell'avvio sicuro per Android <!--1490712-->     
Gli utenti finali con dispositivi Android potranno selezionare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema.


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Reindirizzamento degli utenti macOS alla nuova app del portale aziendale <!--1380728-->   
Quando un utente finale accede al sito Web del portale aziendale per registrare il proprio dispositivo macOS, l'utente viene indirizzato al download della nuova app del portale aziendale per macOS per completare il processo. Ciò si verifica per i dispositivi macOS che usano OS X El Capitan 10.11 o versioni successive. 

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Supporto dell'autenticazione basata sui certificati nel portale aziendale per iOS <!--1029830-->
È stato aggiunto il supporto dell'autenticazione basata sui certificati (CBA) nell'app del portale aziendale per iOS. Gli utenti con autenticazione basata sui certificati immettono il nome utente e quindi toccano il collegamento "Sign in with a certificate" (Accedi con un certificato). L'autenticazione basata sui certificati è già supportata nelle app del portale aziendale per Android e Windows. Altre informazioni sono disponibili nella pagina di [accesso all'app del portale aziendale](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

<!-- the following are present prior to 1710 -->

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>Migliorare la ricerca per il sito Web Portale aziendale <!--1331697-->  
Stiamo migliorando la funzionalità di ricerca dell'app, a partire dal [sito Web Portale aziendale](https://portal.manage.microsoft.com). Le ricerche verranno ora eseguite sulle categorie di app, oltre ai campi nome e descrizione. I risultati verranno ordinati, per impostazione predefinita, in ordine decrescente di rilevanza. 

Gli utenti di iOS riceveranno anche questa modifica, dato che il sito Web Portale aziendale è usato anche come parte dell'app del Portale aziendale per iOS. Le app del Portale aziendale per Android e Windows riceveranno aggiornamenti simili nei prossimi mesi.

Stiamo ancora ottimizzando il modo in cui viene tenuta traccia della rilevanza. Per comunicarci come sta andando, usare il collegamento "Commenti e suggerimenti" nella parte inferiore del sito Web del Portale aziendale.

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Azione di aggiornamento aggiunta all'app del portale aziendale per Windows 10 <!--1132468-->  
L'app del portale aziendale per Windows 10 consentirà agli utenti di aggiornare i dati nell'app trascinando verso il basso oppure, nei sistemi desktop, premendo F5.


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Le app disponibili con o senza registrazione possono essere ora installate senza richiesta di registrazione. <!-- 1334712 -->
Le app aziendali rese disponibili con o senza registrazione nell'app del portale aziendale Android possono essere installate senza richiesta di registrazione.

### <a name="ios-company-portal-display-large-icons----1454593---"></a>Il portale aziendale iOS visualizza icone grandi <!-- 1454593 -->
È in corso la correzione di un problema noto relativo alla visualizzazione delle icone nel riquadro app del portale aziendale iOS. Se si caricano icone di app di almeno 120 x 120 pixel, le icone vengono ora visualizzate nel [sito Web del portale aziendale] (https://portal.manage.microsoft.com) e nelle pagine delle app del portale aziendale iOS occupando l'intero riquadro app.

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Supporto di Intune Managed Browser per iOS e Android <!-- 1374196 -->
A partire da ottobre 2017, l'app Intune Managed Browser per Android supporta solo i dispositivi che eseguono Android 4.4 e versioni successive. L'app Intune Managed Browser per iOS supporta solo i dispositivi che eseguono iOS 9.0 e versioni successive. Le versioni precedenti di Android e iOS saranno in grado di continuare a usare Managed Browser, ma non sarà possibile installare nuove versioni dell'app e le funzionalità dell'app potrebbero non essere tutte disponibili. Si consiglia di eseguire l'aggiornamento di questi dispositivi a una versione supportata del sistema operativo.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Messaggio di errore migliorato quando un utente raggiunge il numero massimo di dispositivi di cui è consentita la registrazione <!-- 1270370 -->
Invece di un messaggio di errore generico, gli utenti finali vedranno un messaggio di errore descrittivo e interattivo: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin." (È stato raggiunto il numero massimo di dispositivi consentiti dall'amministratore IT. Rimuovere un dispositivo registrato o richiedere assistenza all'amministratore IT.)




## <a name="notices"></a>Notifiche

### <a name="device-and-app-management-integration----677972---"></a>Integrazione della gestione delle applicazioni e dei dispositivi <!-- 677972 -->   
Ora che la gestione di dispositivi mobili (MDM) e la gestione di applicazioni mobili (MAM) di Intune sono entrambe accessibili dal portale di Azure, in Intune è stata iniziata l'integrazione dell'esperienza di amministrazione IT nella gestione delle applicazioni e dei dispositivi. Queste modifiche hanno lo scopo di rendere più semplice l'esperienza di gestione dei dispositivi e delle app.

Per altre informazioni sulle modifiche MDM e MAM annunciate, vedere il [blog del team di supporto di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->   
A partire dalla primavera 2017, Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).


### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Nuovo percorso per i dispositivi gestiti nell'API Graph <!-- 1586728 -->  
Nella versione di ottobre del servizio Intune è stata apportata una modifica al percorso usato per accedere ai dispositivi gestiti nella versione beta dell'API Graph.

| | |
|--|--|
| Percorso corrente |  https://graph.microsoft.com/beta/managedDevices |
| Nuovo percorso | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Entrambi i percorsi funzioneranno per l'intero mese di ottobre. Successivamente alla versione di ottobre, sarà possibile usare solo il nuovo percorso.  Se si usa l'API Graph per accedere ai dispositivi gestiti, aggiornare e verificare gli script e le applicazioni con il nuovo percorso. Per altre modifiche, controllare il [log delle modifiche mensile dell'API Graph](https://developer.microsoft.com/en-us/graph/docs/concepts/changelog).

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
