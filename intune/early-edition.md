---
title: Edizione anticipata
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 973408b292261b86f0a49bfaf4c786d6a6dacf28
ms.sourcegitcommit: b8d3f8da6d8c2bd5d6140d538193a02d5875aefb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
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

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Zimperium. È possibile configurare criteri di accesso condizionale EMS in base alla valutazione dei rischi di Zimperium abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale<!-- 676614 -->   
È possibile avere più ruoli server Accesso client per Exchange Connector locale. Ad esempio, se il server Accesso client principale smette di funzionare, Exchange Connector riceve una query per eseguire il fallback in altri server Accesso client. Questa funzionalità garantisce che il servizio non venga interrotto.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->   
Sarà disponibile il Management Pack di System Center Operations Manager per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questo Management Pack consente di eseguire il monitoraggio di Intune in diversi modi quando è necessario risolvere i problemi.


## <a name="intune-apps"></a>App di Intune


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Reindirizzamento degli utenti macOS alla nuova app del portale aziendale <!--1380728-->   
Quando un utente finale accede al sito Web del portale aziendale per registrare il proprio dispositivo macOS, l'utente viene indirizzato al download della nuova app del portale aziendale per macOS per completare il processo. Ciò si verifica per i dispositivi macOS che usano OS X El Capitan 10.11 o versioni successive. 

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Supporto dell'autenticazione basata sui certificati nel portale aziendale per iOS <!--1029830-->
È stato aggiunto il supporto dell'autenticazione basata sui certificati (CBA) nell'app del portale aziendale per iOS. Gli utenti con autenticazione basata sui certificati immettono il nome utente e quindi toccano il collegamento "Sign in with a certificate" (Accedi con un certificato). L'autenticazione basata sui certificati è già supportata nelle app del portale aziendale per Android e Windows. Altre informazioni sono disponibili nella pagina di [accesso all'app del portale aziendale](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Le app disponibili con o senza registrazione possono essere ora installate senza richiesta di registrazione. <!-- 1334712 -->
Le app aziendali rese disponibili con o senza registrazione nell'app del portale aziendale Android possono essere installate senza richiesta di registrazione.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Supporto di Intune Managed Browser per iOS e Android <!-- 1374196 -->
A partire da ottobre 2017, l'app Intune Managed Browser per Android supporta solo i dispositivi che eseguono Android 4.4 e versioni successive. L'app Intune Managed Browser per iOS supporta solo i dispositivi che eseguono iOS 9.0 e versioni successive. Le versioni precedenti di Android e iOS saranno in grado di continuare a usare Managed Browser, ma non sarà possibile installare nuove versioni dell'app e le funzionalità dell'app potrebbero non essere tutte disponibili. Si consiglia di eseguire l'aggiornamento di questi dispositivi a una versione supportata del sistema operativo.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Messaggio di errore migliorato quando un utente raggiunge il numero massimo di dispositivi di cui è consentita la registrazione <!-- 1270370 -->
Invece di un messaggio di errore generico, gli utenti finali vedranno un messaggio di errore descrittivo e interattivo: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin." (È stato raggiunto il numero massimo di dispositivi consentiti dall'amministratore IT. Rimuovere un dispositivo registrato o richiedere assistenza all'amministratore IT.)




## <a name="notices"></a>Notifiche

### <a name="device-and-app-management-integration----677972---"></a>Integrazione della gestione delle applicazioni e dei dispositivi <!-- 677972 -->   
Ora che la gestione di dispositivi mobili (MDM) e la gestione di applicazioni mobili (MAM) di Intune sono entrambe accessibili dal portale di Azure, in Intune è stata iniziata l'integrazione dell'esperienza di amministrazione IT nella gestione delle applicazioni e dei dispositivi. Queste modifiche hanno lo scopo di rendere più semplice l'esperienza di gestione dei dispositivi e delle app.

Per altre informazioni sulle modifiche MDM e MAM annunciate, vedere il [blog del team di supporto di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).




### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
