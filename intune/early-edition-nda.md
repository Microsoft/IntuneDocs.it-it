---
title: Edizione anticipata - Microsoft Intune
titlesuffix: ''
description: Edizione anticipata di Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 35298713738c666ca19d57e647412729a85bbc4a
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112834"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>Edizione anticipata per Microsoft Intune - Dicembre 2018

> [!Note]
> Notifica sull'accordo di riservatezza: Le seguenti modifiche di Intune sono in fase di sviluppo. Queste informazioni sono condivise con accordo di riservatezza su base estremamente limitata. Non pubblicare queste informazioni nei social network o in siti Web pubblici, come Twitter, UserVoice, Reddit e così via. 

L'**edizione anticipata** fornisce un elenco di funzionalità, condivise con accordo di riservatezza, che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non inviare tweet, pubblicare in UserVoice o condividere in altro modo queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Distribuzione di app Android Enterprise APP-WE <!-- 1171203 -->
Per i dispositivi Android in uno scenario di distribuzione APP-WE (App Protection Policy Without Enrollment) non registrato, sarà possibile usare Google Play gestito per distribuire app dello Store e app LOB agli utenti. In particolare, il reparto IT può fornire agli utenti finali un catalogo di app e un'esperienza di installazione che non richiede più agli utenti finali di ridurre le condizioni di sicurezza dei propri dispositivi consentendo installazioni da origini sconosciute. Inoltre, questo scenario di distribuzione fornirà un'esperienza migliorata per gli utenti finali.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nuove opzioni per la connessione automatica e per rendere persistenti le regole quando si usano le impostazioni DNS in dispositivi con Windows 10 e versioni successive <!-- 1333665, 2999078 -->
Nei dispositivi con Windows 10 e versioni successive, sarà possibile creare un profilo di configurazione VPN che include un elenco dei server DNS per risolvere i domini, ad esempio contoso.com. Saranno incluse nuove impostazioni per la risoluzione dei nomi (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Windows 10 e versioni successive** per la piattaforma > scegliere **VPN** per il tipo di profilo > **Impostazioni DNS** >**Aggiungi**): 

- **Connetti automaticamente**: con l'impostazione **Abilitato**, il dispositivo si connette automaticamente alla rete VPN quando un dispositivo contatta un dominio immesso, ad esempio contoso.com.
- **Persistente**: per impostazione predefinita, tutte le regole della tabella dei criteri di risoluzione dei nomi di criteri (NRPT) sono attive, purché il dispositivo sia connesso con questo profilo VPN. Quando questa impostazione è **Abilitata** per una regola NRPT, la regola rimane attiva nel dispositivo, anche in caso di disconnessione della rete VPN o quando viene rimosso il profilo VPN. La regola rimane fino alla rimozione manuale, che può essere eseguita tramite PowerShell.

[Impostazioni VPN di Windows 10](vpn-settings-windows-10.md) descrive l'elenco corrente delle impostazioni. 

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642-eeready---"></a>Usare S/MIME per crittografare e firmare più dispositivi di un utente  <!-- 1333642 eeready -->
Sarà supportata la crittografia di posta elettronica S/MIME con un nuovo profilo di certificato importato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > selezionare la piattaforma > tipo di profilo **Certificato PKCS importato**). In Intune è possibile importare i certificati nel formato PFX. Intune può quindi distribuire i certificati a più dispositivi registrati da un singolo utente. Inoltre:

- Il profilo di posta elettronica iOS nativo supporta l'abilitazione della crittografia S/MIME mediante certificati importati in formato PFX.
- L'app di posta elettronica nativa nei dispositivi Windows Phone 10 usa automaticamente il certificato S/MIME.
- I certificati privati possono essere recapitati su più piattaforme. Tuttavia, non tutte le app di posta elettronica supportano S/MIME.
- In altre piattaforme potrebbe essere necessario configurare manualmente l'app di posta elettronica per abilitare S/MIME.  
- È possibile che le app di posta elettronica che supportano la crittografia S/MIME gestiscano il recupero dei certificati per la crittografia della posta elettronica S/MIME in un modo non supportato dal software MDM, ad esempio basandosi sull'archivio certificati del server di pubblicazione.

Supportato in: Windows, Windows Phone 10, macOS, iOS, Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Pagina Guida e supporto tecnico nell'app Portale aziendale di Windows <!-- 1488939 -->
Verrà aggiunta una nuova pagina all'app Portale aziendale di Windows. La pagina Guida e supporto tecnico includerà informazioni di contatto per l'help desk. Inoltre, gli utenti finali potranno inviare i log del portale aziendale nel caso in cui si verifichino problemi. La pagina include anche una sezione Domande frequenti per offrire assistenza agli utenti finali.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Usare il rilevamento delle reti attendibili per i profili VPN nei dispositivi Windows 10 <!-- 1500165 -->
Quando si usa il rilevamento delle reti attendibili, sarà possibile impedire ai profili VPN di creare automaticamente una connessione VPN quando l'utente è già in una rete attendibile. Sarà possibile aggiungere suffissi DNS per abilitare il rilevamento delle reti attendibili nei dispositivi che eseguono Windows 10 e versioni successive (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **VPN** per il tipo di profilo).
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md) sono elencate le impostazioni VPN correnti.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK supporterà le chiavi di crittografia a 256 bit <!-- 1832174 -->
Intune App SDK per iOS userà le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. L'SDK continuerà a supportare le chiavi a 128 bit per garantire la compatibilità con il contenuto e le app che usano versioni precedenti dell'SDK.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>Impostazioni per il PC condiviso abilitate nel profilo di Intune <!-- 1907917 -->
Attualmente, è possibile configurare le impostazioni del PC condiviso nei dispositivi desktop Windows 10 usando un'impostazione OMA-URI personalizzata. Verrà aggiunto un nuovo profilo per configurare le impostazioni del PC condiviso: **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Shared multi-user device** (Dispositivo multiutente condiviso).
Si applica a: Windows 10 e versioni successive, Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Aggiornamento del metodo di autenticazione e dell'installazione dell'app Portale aziendale per i criteri di Intune <!-- 1927359 -->
Intune non supporterà più l'app Portale aziendale quando viene installata dall'App Store, in alcuni dispositivi. Questa modifica è rilevante solo quando si esegue l'autenticazione con Apple Setup Assistant durante la registrazione. Questa modifica riguarda inoltre solo i dispositivi iOS registrati tramite:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

Gli utenti riceveranno un errore se installano l'app Portale aziendale dall'App Store e quindi provano a registrare i dispositivi tramite tale app. È previsto che questi dispositivi usino l'app Portale aziendale solo quando ne è stato eseguito il push automaticamente da Intune durante la registrazione. I profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Se si vuole che gli utenti dei dispositivi DEP dispongano dell'app Portale aziendale, è necessario specificare le preferenze in un profilo di registrazione. Inoltre, la schermata **Identifica il dispositivo** nell'app Portale aziendale diventerà presto obsoleta.  
Per installare l'app Portale aziendale nei dispositivi DEP già registrati, si dovrà passare a Intune > App client ed eseguirne il push come app gestita con i criteri di configurazione delle app. Informazioni dettagliate su come eseguire questi passaggi saranno disponibili in articoli futuri della documentazione.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>I non amministratori possono abilitare BitLocker nei dispositivi Windows 10 aggiunti ad Azure AD<!-- 2147379 -->
Quando si abilitano le impostazioni di BitLocker nei dispositivi Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo**  >  **Windows 10 e versioni successive** per la piattaforma > **Endpoint Protection** per il tipo di profilo > **Crittografia Windows**), si aggiungono impostazioni BitLocker. Questo aggiornamento include una nuova impostazione di BitLocker per consentire agli utenti standard (non amministratori) di abilitare la crittografia. Per visualizzare le impostazioni correnti, vedere [Impostazioni di Endpoint Protection per Windows 10](endpoint-protection-windows-10.md#windows-encryption).

### <a name="intune-app-pin----2298397---"></a>PIN dell'app Intune <!-- 2298397 -->
L'amministratore IT potrà configurare il numero di giorni di attesa per un utente finale prima che debba modificare il PIN dell'app Intune. La nuova impostazione è disponibile nel portale di Azure selezionando **Intune** > **App client** > **Criteri di protezione delle app**  >  **Crea criterio** > **Impostazioni** > **Requisiti di accesso**. Questa funzionalità sarà disponibile nei dispositivi iOS e Android. Questa impostazione supporta un valore intero positivo.

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>Nuove impostazioni per gli aggiornamenti di Windows 10 <!-- 2626030 2512994 -->
Per gli anelli di aggiornamento Windows 10, sarà possibile:
- ripristinare le impostazioni di aggiornamento automatico originali nei computer Windows 10 che eseguono l'*aggiornamento di ottobre 2018*
- configurare una nuova impostazione per gli aggiornamenti software che consente di impedire o consentire agli utenti di sospendere l'installazione degli aggiornamenti da *Impostazioni* nei loro computer. 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>I profili di posta elettronica iOS possono usare firma e crittogafia S/MIME <!-- 2662949 -->
Sarà possibile creare un profilo di posta elettronica che include impostazioni diverse. Sono incluse le impostazioni di S/MIME che possono essere usate per firmare e crittografare le comunicazioni tramite posta elettronica nei dispositivi iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **iOS** per la piattaforma > **Posta elettronica** per il tipo di profilo).

Le impostazioni correnti sono elencate in [Impostazioni del profilo di posta elettronica per dispositivi iOS](email-settings-ios.md).

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>Ignorare altre schermate di Assistente configurazione in un dispositivo DEP iOS <!-- 2687509 -->
Oltre alle schermate che è attualmente possibile ignorare, sarà possibile impostare i dispositivi DEP iOS in modo che ignorino le schermate seguenti nell'Assistente configurazione quando un utente registra il dispositivo: Segnale schermo, Privacy, Migrazione di Android, Pulsante Pagina iniziale, iMessage e FaceTime, Onboarding, Migrazione di Watch, Aspetto, Orario schermo, Aggiornamento software, Configurazione SIM.
Per scegliere le schermate da ignorare, passare a **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > scegliere un token > **Profili** > scegliere un profilo > **Proprietà** > **Personalizzazione dell'Assistente configurazione** > scegliere **Nascondi** per tutte le schermate che si vuole ignorare > **OK**.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Alcune impostazioni di BitLocker supportano l'edizione Windows 10 Pro<!-- 2727036 -->
Sarà possibile creare un profilo di configurazione che imposta le impostazioni di Endpoint Protection nei dispositivi Windows 10, incluso BitLocker. È stato aggiunto il supporto per l'edizione Windows 10 Professional per alcune impostazioni di BitLocker. Per visualizzare le impostazioni correnti per le edizioni di Windows 10, vedere [Impostazioni di Endpoint Protection per Windows 10](endpoint-protection-windows-10.md#windows-encryption).
Intune offrirà campi aggiuntivi per i report relativi ai dispositivi, tra cui produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. In Intune, questi campi saranno disponibili selezionando **App client** > **Stato protezione app** e scegliendo **Report sulla protezione dell'app: iOS, Android**. Inoltre, questi parametri consentiranno di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della versione minima della patch di sicurezza Android. 

### <a name="intune-device-reporting-fields----2748738---"></a>Campi per i report relativi ai dispositivi di Intune <!-- 2748738 -->
Intune offrirà campi aggiuntivi per i report relativi ai dispositivi, tra cui produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. In Intune, questi campi saranno disponibili selezionando **App client** > **Stato protezione app** e scegliendo **Report sulla protezione dell'app: iOS, Android**. Inoltre, questi parametri consentiranno di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della versione minima della patch di sicurezza Android. 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>L'impostazione Configurazione del dispositivo condiviso è stata rinominata Lock Screen Message (Messaggio della schermata di blocco) per i dispositivi iOS nel portale di Azure <!-- 2809362 -->
Quando si crea un profilo di configurazione per i dispositivi iOS, sarà possibile aggiungere le impostazioni **Configurazione del dispositivo condiviso** per visualizzare testo specifico nella schermata di blocco. Sono state apportate le modifiche seguenti: 

- L'impostazione **Configurazione del dispositivo condiviso** nel portale di Azure è stata rinominata "Lock Screen Message (supervised only)" (Messaggio della schermata di blocco - solo con supervisione): **Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > scegliere **iOS** per la piattaforma > scegliere **Funzionalità del dispositivo** per il tipo di profilo > **Lock Screen Message** (Messaggio della schermata di blocco).
- Quando si aggiungono messaggi della schermata di blocco, è possibile inserire un numero di serie, un nome di dispositivo o un altro valore specifico del dispositivo come variabile in **Informazioni sui tag asset**. Ad esempio, è possibile immettere `Device name: {{device name}}` o `Serial number is {{serial number}}` usando parentesi graffe. In [Token iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) sono elencati i token disponibili che possono essere usati.

[Settings to display messages on the lock screen](shared-device-settings-ios.md) (Impostazioni per visualizzare i messaggi nella schermata di blocco) elenca le impostazioni correnti.

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>Messaggi di errori più dettagliati per le restrizioni di registrazione <!-- 3111564-->
Saranno disponibili messaggi di errore più dettagliati quando non vengono soddisfatte le restrizioni di registrazione. Per visualizzare questi messaggi, passare a **Intune** > **Risoluzione dei problemi** e selezionare la tabella Errori di registrazione.

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nuove impostazioni di notifica, hint e protezione della tastiera per i dispositivi Android Enterprise in modalità proprietario del dispositivo <!-- 3201839 3201843 -->
Questo aggiornamento include numerose nuove funzionalità per i dispositivi aziendali Android quando vengono eseguiti come proprietario del dispositivo. Per usare queste funzionalità, passare a **Configurazione del dispositivo** > **Profili** > **Crea profilo** > in **Piattaforma**, scegliere **Android Enterprise** > in **Tipo di profilo**, scegliere **Solo proprietario del dispositivo** > **Limitazioni del dispositivo**.
Le nuove funzionalità includono: 
- Disabilitare la visualizzazione delle notifiche di sistema, incluse chiamate in ingresso, avvisi di sistema, errori di sistema e altro
- Suggerimenti per ignorare le esercitazioni e i consigli iniziali per le app aperte per la prima volta
- Disabilitare le impostazioni avanzate di protezione della tastiera, ad esempio fotocamera, notifiche, sblocco tramite impronta digitale e altro

Per visualizzare le impostazioni correnti, passare a [Impostazioni relative alle limitazioni per i dispositivi Android Enterprise](device-restrictions-android-for-work.md).

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>I dispositivi Android Enterprise in modalità proprietario del dispositivo possono usare le connessioni VPN sempre attive <!-- 3202194 -->
In questo aggiornamento è possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise in modalità proprietario del dispositivo. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
È possibile abilitare le connessioni VPN sempre attive in **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo** per Solo proprietario del dispositivo > **Connettività**. Per visualizzare le impostazioni correnti, passare a [Impostazioni relative alle limitazioni per i dispositivi Android Enterprise](device-restrictions-android-for-work.md).

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nuova impostazione per terminare i processi in Gestione attività nei dispositivi Windows 10 <!-- 3285177 --> 
Questo aggiornamento include una nuova impostazione per terminare i processi usando Gestione attività nei dispositivi Windows 10. Scegliere se consentire o non consentire questa impostazione usando un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > In **Piattaforma**  scegliere **Windows 10** > in **Tipo di profilo** scegliere **Limitazioni del dispositivo** > **Generale**).
Per visualizzare le impostazioni correnti, vedere [Restrizione dei dispositivi per Windows 10](device-restrictions-windows-10.md).
Si applica a: Windows 10 e versioni successive

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>I modelli amministrativi sono disponibili in anteprima pubblica e sono stati spostati nel profilo di configurazione corrispondente <!-- 3322847 -->
I modelli amministrativi in Intune (**Configurazione del dispositivo** > **Modelli amministrativi**) sono attualmente in anteprima privata. Con questo aggiornamento: i modelli amministrativi includono circa 300 impostazioni che possono essere gestite in Intune. In precedenza, queste impostazioni erano disponibili solo in Editor Criteri di gruppo.
I modelli amministrativi sono disponibili in anteprima pubblica. I modelli amministrativi vengono spostati da **Configurazione del dispositivo** > **Modelli amministrativi** a **Configurazione del dispositivo** > **Profili** >**Crea profilo** > in **Piattaforma** scegliere  **Windows 10 e versioni successive**, in **Tipo di profilo** scegliere **Modelli amministrativi**.
La creazione di report è abilitata. Si applica a: Windows 10 e versioni successive


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Usare le impostazioni consigliate da Microsoft con le baseline di sicurezza <!-- 2055484 -->
Intune si integra con altri servizi specifici per la sicurezza, inclusi Windows Defender ATP e Office 365 ATP. I clienti manifestano l'esigenza di una strategia comune e di un set integrato di flussi di lavoro di sicurezza end-to-end nei servizi di Microsoft 365. L'obiettivo è l'allineamento delle strategie per creare soluzioni in grado di conciliare le operazioni di sicurezza e le comuni attività degli amministratori. Per realizzare questo obiettivo in Intune, è stato pubblicato un set di "baseline di sicurezza" consigliate da Microsoft (**Intune** > **Baseline di sicurezza**).  Un amministratore potrà creare criteri di sicurezza direttamente da queste baseline e quindi distribuirle agli utenti. Può anche personalizzare le indicazioni sulle procedure consigliate per soddisfare le esigenze dell'organizzazione. Intune verifica che i dispositivi rimangano conformi a queste baseline e invia agli amministratori una notifica sugli utenti e i dispositivi non conformi.

### <a name="scope-tags-for-apps---1081941---"></a>Tag di ambito per le app <!--1081941 -->
Sarà possibile creare tag di ambito per limitare l'accesso alle risorse di Intune. Aggiungere un tag di ambito a un'assegnazione di ruolo e quindi aggiungere il tag di ambito a un profilo di configurazione. Il ruolo potrà accedere solo alle risorse con profili di configurazione con tag di ambito corrispondenti (o nessun tag di ambito).
Per creare un tag di ambito, scegliere **Ruoli di Intune** > **Ambito (tag)** > **Crea**.
Per aggiungere un tag di ambito a un'assegnazione di ruolo, scegliere **Ruoli di Intune** > **Tutti i ruoli** > **Policy and Profile Manager (Gestione criteri e profili)** > **Assegnazioni** > **Ambito (tag)**.
Per aggiungere un tag di ambito a un profilo di configurazione, scegliere **Configurazione del dispositivo** > **Profili** > scegliere un profilo > **Proprietà** > **Ambito (tag)**.

### <a name="tenant-health-dashboard----1124854---"></a>Dashboard sull'integrità del tenant <!-- 1124854 -->
La pagina Stato del tenant in Intune fornirà in un'unica posizione le informazioni sullo stato del tenant. La pagina è suddivisa in 4 sezioni:  
- **Dettagli del tenant**: contiene informazioni, ad esempio l'autorità MDM, il totale dei dispositivi registrati nel tenant e i conteggi delle licenze. Questa sezione indica anche la versione corrente del servizio per il tenant.
- **Stato del connettore**: contiene informazioni sui connettori configurati, ad esempio Apple VPP, Windows Store for Business e connettori di certificati. In base allo stato corrente, i connettori vengono contrassegnati come *Integro*, *Avviso* o *Non integro*.
- **Integrità del servizio Intune**: contiene gli eventi imprevisti attivi o le interruzioni del tenant. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office ([https://portal.office.com](https://portal.office.com)).
- **Novità su Intune**: contiene i messaggi attivi sul tenant, ad esempio le notifiche che informano che il tenant ha ricevuto le funzionalità di Intune più recenti. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Criteri WIP distribuiti senza registrazione dell'utente <!-- 1434452 -->
I criteri di Windows Information Protection (WIP) potranno essere distribuiti senza richiedere agli utenti MDM di registrare il dispositivo Windows 10. Questa configurazione non solo consente alle società di proteggere i documenti aziendali in base alla configurazione WIP, ma permette anche agli utenti di continuare a gestire i dispositivi Windows. Quando i documenti sono protetti da un criterio WIP, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, tutti i dati protetti tramite i criteri WIP non saranno più utilizzabili. Da Intune nel portale di Azure selezionare **App per dispositivi mobili** > **Cancellazione selettiva di app**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP Apple usato da un altro software MDM <!-- 1488946 -->
Intune rileverà e visualizzerà i dettagli se un token VPP (Volume Purchase Program) Apple viene usato sia da Intune che da un altro software MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivi ritirati nel dashboard della conformità dei dispositivi <!-- 1981119 -->
In un aggiornamento futuro i dispositivi ritirati verranno rimossi dal dashboard della conformità dei dispositivi. Questa operazione modificherà i numeri di conformità.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Modifica nel processo di aggiornamento per i connettori locali <!-- 2277554 -->
In base al feedback dei clienti, cambierà il modo in cui gli aggiornamenti vengono eseguiti nei connettori locali. Dopo aver installato un connettore locale, gli aggiornamenti verranno eseguiti automaticamente. Questa modifica inizierà con il nuovo connettore di certificati PFX per Microsoft Intune e successivamente verrà applicata ad altri tipi di connettori locali. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificare la conformità di Configuration Manager <!-- 2192052 -->
Un aggiornamento futuro includerà una nuova impostazione di conformità System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10**). Configuration Manager invia segnali per la conformità di Intune. Usando l'impostazione di Intune è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Si applica a Windows 10 e versioni successive



## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).



