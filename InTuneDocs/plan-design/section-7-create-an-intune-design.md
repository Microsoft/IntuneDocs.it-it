---
title: Creare una progettazione per Intune | Documentazione Microsoft
description: Questo articolo semplifica la creazione di una progettazione per un&quot;implementazione di Microsoft Intune in configurazione solo cloud.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 70be873367edccdefd724b6aa6959eb67b377bdd
ms.openlocfilehash: 92dedcd165ffec47f6c5b818533fce08ed04b1a0


---

# <a name="create-an-intune-design"></a>Creare una progettazione per Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Questa sezione della guida deve essere usata in parallelo con gli altri argomenti nella sezione 2. La progettazione sarà basata sulle informazioni raccolte e sulle decisioni prese durante il completamento delle sezioni precedenti di questa guida. In questa sezione relativa alla progettazione ci concentreremo sulla versione autonoma di Intune, che è un servizio Microsoft basato sul cloud.

Anche se i requisiti dell'infrastruttura locale sono minimi, è comunque consigliabile definire un piano di progettazione per essere certi di disporre della soluzione di gestione dei dispositivi mobili più adatta per gli scopi, gli obiettivi e i requisiti dell'organizzazione.

Inoltre, spesso vengono apportate modifiche di progettazione durante le fasi di implementazione e di test: è importante assicurarsi di documentare tutte queste modifiche e i motivi per cui vengono apportate. Verranno descritte le aree seguenti:

-   Ambiente corrente

-   Opzioni per la distribuzione di Intune

-   Requisiti di identità per le dipendenze esterne

-   Considerazioni sulle piattaforme per i dispositivi

-   Requisiti da soddisfare  

Esaminiamo ognuna di queste aree più in dettaglio. 

## <a name="record-your-environment"></a>Registrare l'ambiente

Per poter creare la progettazione, il primo passaggio è registrare l'ambiente corrente. L'ambiente corrente può influenzare le decisioni di progettazione e deve essere documentato e tenuto presente quando si prendono altre decisioni sulla progettazione di Intune. Di seguito sono riportati alcuni esempi di come registrare l'ambiente corrente:

-   **Identità nel cloud**

    -   Viene usato DirSync o Azure Active Directory (AAD) Connect?

    -   L'ambiente è federato?

    -   L'autenticazione a più fattori è abilitata?

-   **Ambiente di posta elettronica**

    -   Viene usato Exchange? È in locale o nel cloud?

    -   È in corso un progetto per la migrazione di Exchange nel cloud?

-   **Soluzione MDM corrente**

    -   Vengono attualmente usate altre soluzioni MDM?

    -   Quali soluzioni MDM vengono usate per gli scenari dei casi d'uso aziendali e BYOD?

    -   Quali funzionalità vengono usate (impostazioni per le app dei dispositivi, configurazioni Wi-Fi e così via)?

    -   Quali piattaforme per i dispositivi sono supportate?

    -   Quali gruppi e quanti utenti usano la soluzione MDM?

-   **Soluzione per i certificati**

    -   È stata implementata una soluzione per i certificati?

    -   Che tipo di certificati vengono usati?

-   **Gestione dei sistemi**

    -   Come viene gestito l'ambiente PC e server?

    -   Viene usato System Center Configuration Manager? Viene usata una piattaforma di gestione dei sistemi di terze parti?

-   **Soluzione VPN**

    -   Quale soluzione VPN viene usata?

    -   Viene impiegata sia per gli scenari dei casi d'uso aziendali che BYOD?

Durante la registrazione dell'ambiente MDM corrente, assicurarsi di prendere nota di eventuali progetti o altri piani che potrebbero apportare modifiche all'ambiente. Di seguito è riportato un esempio di come registrare l'ambiente corrente per agevolare la creazione della progettazione per Intune:

| **Area di soluzioni** | **Ambiente corrente** | **Commenti** |
|:---:|:---:|:---:|
| **Identità** | Azure AD, Azure AD Connect, non federato, senza autenticazione a più fattori | Progetto per abilitare l'autenticazione a più fattori entro la fine dell'anno |                 
| **Ambiente di posta elettronica** | Exchange locale, Exchange Online | Migrazione in corso da Exchange locale a Exchange Online. È stata eseguita la migrazione del&75;% delle cassette postali. La migrazione dell'ultimo 25% verrà eseguita prima dell'avvio del progetto pilota di Intune. |                
| **SharePoint** | SharePoint locale | Nessun piano per la migrazione a SharePoint Online |  
| **Soluzione MDM corrente** | Exchange ActiveSync |  |
| **Soluzione per i certificati** | Microsoft Server 2012 R2, Servizi certificati Active Directory | Uso di PKI solo per i server del sito Web |
| **Gestione dei sistemi** | System Center Configuration Manager CB 1606 | Potrebbe essere utile valutare una soluzione ibrida Intune |
| **Soluzione VPN** | Cisco AnyConnect |  |

## <a name="choose-an-intune-deployment-option"></a>Scegliere un'opzione di distribuzione per Intune

Intune offre due opzioni di distribuzione: versione autonoma e configurazione ibrida. È necessario decidere quale opzione è più adatta per i requisiti aziendali. La versione autonoma si riferisce al servizio Intune in esecuzione nel cloud, mentre la configurazione ibrida si riferisce all'integrazione di Intune con System Center Configuration Manager.

- Altre informazioni su [come scegliere tra Microsoft Intune autonomo e la gestione di dispositivi mobili ibrida con System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)

## <a name="intune-tenant-location"></a>Posizione del tenant Intune

Se l'organizzazione ha una presenza globale, assicurarsi di pianificare la posizione del tenant al momento della sottoscrizione al servizio. Il paese è definito quando ci si iscrive per la prima volta per ottenere una sottoscrizione Intune ed è associato alle aree geografiche elencate di seguito:

-   America del Nord

-   Europa, Medio Oriente e Africa

-   Asia e Pacifico

>[!IMPORTANT]
> Non è possibile modificare la posizione del paese/tenant in un secondo momento.

## <a name="external-dependencies"></a>Dipendenze esterne

Le dipendenze esterne sono servizi e prodotti distinti da Intune, ma che rappresentano un requisito per Intune o che possono essere integrati con Intune. È importante identificare i requisiti per le dipendenze esterne e il modo in cui devono essere configurate. Di seguito sono riportati alcuni esempi di dipendenze esterne comuni.

-   Identità

-   Gruppi di utenti e dispositivi

-   PKI

Queste dipendenze esterne comuni sono illustrate più in dettaglio di seguito

### <a name="identity"></a>Identità

L'identità è il modo in cui vengono identificati gli utenti che appartengono all'organizzazione e che eseguono la registrazione di un dispositivo. Intune richiede Azure Active Directory (Azure AD) come provider di identità utente. Se si usa già questo servizio, è possibile sfruttare l'identità esistente già presente nel cloud. Inoltre, Azure AD Connect è lo strumento consigliato per la sincronizzazione delle identità utente locali con i servizi cloud Microsoft. Se l'organizzazione usa già Office 365, è importante che Intune usi lo stesso ambiente Azure Active Directory.

È possibile trovare altre informazioni sui requisiti di identità per Intune di seguito.

-   Altre informazioni sui [i requisiti di identità](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Altre informazioni sui [requisiti di sincronizzazione delle directory](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Altre informazioni sui [requisiti dell'autenticazione a più fattori](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

### <a name="user-and-device-groups"></a>Gruppi di utenti e dispositivi

I gruppi di utenti e dispositivi determinano la destinazione di una distribuzione, ad esempio per i criteri, le applicazioni e i profili. Intune in configurazione solo cloud supporta gruppi di utenti e dispositivi: è necessario determinare quali gruppi di utenti e dispositivi saranno richiesti. È consigliabile creare tutti i gruppi in Active Directory locale, quindi sincronizzarli con Azure Active Directory. È possibile trovare altre informazioni sulla pianificazione e la creazione dei gruppi di utenti e dispositivi di seguito.

-   Altre informazioni sulla [pianificazione dei gruppi di utenti e dispositivi](https://docs.microsoft.com/intune/deploy-use/plan-your-user-and-device-groups).

-   Informazioni su [come creare gruppi di utenti e dispositivi](https://docs.microsoft.com/en-us/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

### <a name="public-key-infrastructure-pki"></a>Infrastruttura a chiave pubblica (PKI)

L'infrastruttura a chiave pubblica fornisce certificati a dispositivi o utenti per consentire l'autenticazione sicura in un servizio. Intune supporta un'infrastruttura PKI Microsoft. Possono essere emessi certificati utente e dispositivo per un dispositivo mobile per soddisfare i requisiti dell'autenticazione basata su certificati. Prima di implementare i certificati, è necessario determinare se sono richiesti certificati, se l'infrastruttura di rete può supportare l'autenticazione basata su certificati e se sono attualmente in uso certificati nell'ambiente esistente.

Se si prevede di usare certificati con profili VPN, Wi-Fi o di posta elettronica con Intune, è necessario assicurarsi di disporre di un'[infrastruttura PKI](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles) supportata, pronta per la creazione e la distribuzione dei profili certificato.

Inoltre, se verranno emessi certificati SCEP, è necessario determinare quale server ospiterà la funzionalità Servizio Registrazione dispositivi di rete (NDES) e come avverrà la comunicazione.

Altre informazioni sulla configurazione dei certificati in Intune:

-   [Come configurare l'infrastruttura di certificazione per SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep).

-   [Come configurare l'infrastruttura di certificazione per PFX](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx).

-   [Come configurare i profili certificato di Intune](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles).

-   [Come configurare i criteri di accesso alle risorse](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

## <a name="device-platform-considerations"></a>Considerazioni sulle piattaforme per i dispositivi

È necessario esaminare più da vicino i dispositivi per comprendere come gestirli correttamente.

-   Determinare le piattaforme per dispositivi supportate

-   Dispositivi

-   Proprietà del dispositivo

-   Registrazione in blocco

Esaminiamo queste aree più in dettaglio.

### <a name="determine-supported-device-platforms"></a>Determinare le piattaforme per dispositivi supportate

Durante la creazione della progettazione, è necessario sapere quali dispositivi saranno presenti nell'ambiente e verificare se sono supportati o meno da Intune. Intune supporta le piattaforme iOS, Android e Windows.

-   Altre informazioni sui [dispositivi supportati da Intune](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers).

### <a name="devices"></a>Dispositivi

Intune gestisce i dispositivi mobili per proteggere i dati aziendali e consentire agli utenti finali di lavorare da diverse posizioni. Intune supporta più piattaforme, pertanto è consigliabile documentare i dispositivi e le piattaforme per i sistemi operativi che saranno supportati nella progettazione dell'organizzazione. Questo elenco verrà ampliato in base ai dispositivi e alle piattaforme creati nella sezione relativa ai requisiti per i casi d'uso.

È inoltre consigliabile conoscere le versioni, per fare riferimento all'elenco durante il controllo delle funzionalità dei dispositivi in base alla piattaforma per il sistema operativo e alla versione. Di seguito è riportato un esempio:

| **Piattaforma per i dispositivi** | **Versioni del sistema operativo** |
|:---:|:---:|
| iOS - iPhone | 9.0+ |                
| iOS - iPad | 8.0+ |               
| Android - Samsung Knox Standard | 4.0+ |
| Tablet Windows 10 | 10+ |

### <a name="device-ownership"></a>Proprietà del dispositivo

Intune supporta sia i dispositivi di proprietà aziendale che i dispositivi BYOD. Un dispositivo è considerato di proprietà aziendale se è registrato da un manager di registrazione dispositivi o da un programma di registrazione dispositivi. Ad esempio, un dispositivo può essere registrato tramite il servizio DEP di Apple, contrassegnato come aziendale e inserito in un gruppo di dispositivi che riceve criteri e app aziendali mirati.

Per altre informazioni sui casi d'uso aziendali e BYOD, fare riferimento a [Sezione 3: Determinare i requisiti degli scenari per i casi d'uso](section-3-determine-use-case-requirements.md).

### <a name="bulk-enrollment"></a>Registrazione in blocco

Sono disponibili diverse opzioni per la registrazione di un dispositivo in Intune, in aggiunta alla registrazione self-service tramite il portale aziendale. La registrazione in blocco può essere eseguita in diversi modi a seconda della piattaforma. Se sarà richiesta la registrazione in blocco, è innanzitutto necessario determinare il metodo di registrazione in blocco e incorporarlo nella progettazione. È possibile trovare altre informazioni sui diversi metodi di registrazione in blocco di seguito.

-   Altre informazioni sulla [registrazione in blocco](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

## <a name="feature-requirements"></a>Requisiti per le funzionalità

In queste sezioni verranno descritte le seguenti caratteristiche e funzionalità, allineate con i requisiti degli scenari dei casi d'uso:

-   Criteri di termini e condizioni

-   Criteri di configurazione

-   Profili di risorse

-   App

-   Criteri di conformità

-   Accesso condizionale

Esaminiamo ognuna di queste aree più in dettaglio.

### <a name="terms-and-conditions-policies"></a>Criteri di termini e condizioni

Termini e condizioni possono essere usati per descrivere i criteri o le condizioni che un utente finale deve accettare prima della registrazione. Intune supporta la possibilità di aggiungere e distribuire più criteri di termini e condizioni per i gruppi di utenti. È necessario determinare se sono richiesti criteri di termini e condizioni. In questo caso, occorre stabilire chi sarà responsabile di fornire queste informazioni all'interno dell'organizzazione.

-   Informazioni su [come creare criteri di termini e condizioni](https://docs.microsoft.com/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune) in Intune. Di seguito è riportato un esempio di come documentare i criteri di termini e condizioni.

| **Nome termini e condizioni** | **Caso d'uso** | **Gruppo di destinazione** |
|:---:|:---:|:---:|
| Termini e condizioni aziendali | Aziendale | Utenti aziendali |                 
| Termini e condizioni BYOD | BYOD | Utenti BYOD |                

### <a name="configuration-policies"></a>Criteri di configurazione

I criteri di configurazione sono usati per gestire le impostazioni di sicurezza e le funzionalità in un dispositivo. Quando si progettano i criteri di configurazione, fare riferimento alla sezione relativa ai requisiti per i casi d'uso per determinare le configurazioni necessarie per i dispositivi Intune. Documentare le impostazioni, come devono essere configurate e a quali gruppi di utenti o dispositivi sono destinate.

È necessario creare almeno un criterio di configurazione per ogni piattaforma. Se necessario, è possibile creare più criteri di configurazione per ogni piattaforma. Di seguito è riportato un esempio di progettazione di quattro criteri di configurazione diversi per differenti piattaforme e casi d'uso.

| **Nome criterio** | **Piattaforma per i dispositivi** | **Impostazioni** | **Gruppo di destinazione** |   
|:---:|:---:|:---:|:---:|
| Aziendale - iOS | iOS | PIN obbligatorio, lunghezza: 6, limitazione del backup cloud | Dispositivi aziendali |                                                           
| Aziendale - Android | Android | PIN obbligatorio, lunghezza: 6, limitazione del backup cloud | Dispositivi aziendali |                                                           
| BYOD - iOS  | iOS | PIN obbligatorio, lunghezza: 4 | Dispositivi BYOD |
| BYOD - Android  | Android | PIN obbligatorio, lunghezza: 4 | Dispositivi BYOD |

### <a name="profiles"></a>Profiles

I profili vengono usati per consentire all'utente finale di connettersi ai dati aziendali. Intune supporta diversi tipi di profili. Fare riferimento ai casi d'uso e ai requisiti per determinare quando verranno configurati i [profili](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune). Tutti i profili dispositivo devono essere classificati per tipo di piattaforma e inclusi nella documentazione della progettazione.

-   Profili certificato

-   Profilo Wi-Fi

-   Profilo VPN

-   Profilo di posta elettronica

Esaminiamo ogni tipo di profilo più in dettaglio.

##### <a name="certificate-profiles"></a>Profili certificato

I profili certificato consentono a Intune di emettere un certificato per un utente o un dispositivo. Intune supporta:

-   Simple Certificate Enrollment Protocol (SCEP)

-   Certificato radice attendibile

-   Certificato PFX.

È consigliabile documentare quale gruppo di utenti richiede un certificato, quanti profili certificato saranno necessari e a quali gruppi di utenti distribuirli.

>[!NOTE]
> Tenere presente che il certificato radice attendibile è necessario per il certificato SCEP, pertanto verificare che tutti gli utenti a cui è assegnato il certificato SCEP ricevano anche un certificato radice attendibile. Se sono richiesti certificati SCEP, progettare e documentare i modelli di certificato SCEP che saranno necessari.

Di seguito è riportato un esempio di come documentare i certificati durante la progettazione:

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| CA radice | CA radice aziendale | Android, iOS, Windows Mobile | Aziendale, BYOD  |                                                           
| SCEP | Certificato utente | Android, iOS, Windows Mobile | Aziendale, BYOD |                                                           

##### <a name="wi-fi-profile"></a>Profilo Wi-Fi

I profili Wi-Fi vengono usati per connettere automaticamente un dispositivo mobile a una rete wireless. Intune supporta la distribuzione di profili Wi-Fi per tutte le piattaforme supportate.

-   Altre informazioni sul [supporto di Intune per i profili Wi-Fi.](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune)

Di seguito è riportato un esempio di progettazione di un profilo Wi-Fi:

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Profilo Wi-Fi Asia | Android | Aziendale, BYOD Asia|                                                           
| Wi-Fi | Profilo Wi-Fi America del Nord | Android, iOS, Windows 10 Mobile | Aziendale, BYOD America del Nord |                                                           

##### <a name="vpn-profile"></a>Profilo VPN

I profili VPN consentono agli utenti di accedere in modo sicuro alla rete da posizioni remote. Intune supporta i profili VPN di connessioni VPN native e fornitori di terze parti.

-   Altre informazioni su [profili VPN e fornitori supportati da Intune](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune).

Di seguito è riportato un esempio di come documentare la progettazione di un profilo VPN.

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Connessione | Profilo VPN Cisco AnyConnect | Android, iOS, Windows 10 Mobile | Aziendale, BYOD America del Nord e Germania|                                                           
| Connessione | Pulse Secure | Android | Aziendale, BYOD Asia |                                                           

##### <a name="email-profile"></a>Profilo di posta elettronica

I profili di posta elettronica consentono la configurazione automatica di un client di posta elettronica con le informazioni di connessione e la configurazione della posta elettronica. Intune supporta i profili di posta elettronica in alcuni dispositivi.

-   Altre informazioni sui [profili di posta elettronica](https://docs.microsoft.com/en-us/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) e sulle piattaforme supportate.

Di seguito è riportato un esempio di come documentare la progettazione dei profili di posta elettronica:

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Profilo di posta elettronica | Profilo di posta elettronica iOS | iOS | Aziendale - BYOD information worker |                                                           
| Profilo di posta elettronica | Profilo di posta elettronica Android Knox | Android Knox | BYOD |

### <a name="apps"></a>App

Intune supporta la distribuzione di app a utenti o dispositivi in diversi modi. È possibile distribuire app di programmi di installazione di software, app di un app store pubblico, collegamenti esterni o app iOS gestite. Oltre a distribuire singole app, è possibile gestire e distribuire le app acquistate tramite i programmi Volume Purchase Program per iOS e Windows. Di seguito sono riportate altre informazioni sul supporto di Intune per le app e i programmi Volume Purchase Program.

-   Altre informazioni sui [i tipi di app](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)

-   Altre informazioni sulle [licenze VPP (Volume Purchase Program per le aziende) per iOS](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune).

-   Altre informazioni su [Windows Store per le aziende](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune).

#### <a name="app-type-requirements"></a>Requisiti per il tipo di app

Poiché è possibile distribuite app a utenti e dispositivi, è consigliabile decidere quali applicazioni verranno gestite da Intune. Durante la compilazione dell'elenco, provare a rispondere alle domande seguenti:

-   Le app richiedono l'integrazione con i servizi cloud?

-   Per gli utenti BYOD saranno disponibili tutte le app?

-   Quali sono le opzioni di distribuzione disponibili per queste app?

-   La società ha l'esigenza di consentire l'accesso ai dati delle applicazioni SaaS (Software as a Service) ai propri partner?

-   Le app richiedono l'accesso a Internet dai dispositivi degli utenti?

-   Le app sono disponibili in un app store pubblico o sono app line-of-business personalizzate?


>[!TIP]
> Informazioni sui [diversi tipi di applicazioni supportate da Intune](https://docs.microsoft.com/intune/deploy-use/add-apps).

#### <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione delle app consentono di ridurre al minimo le perdite di dati, definendo le modalità di gestione dei dati aziendali nell'applicazione. Intune supporta i criteri di protezione delle app per qualsiasi applicazione progettata per il funzionamento con le soluzioni di gestione delle app per dispositivi mobili. Durante la progettazione dei criteri di protezione delle app, è necessario determinare quali restrizioni verranno applicate ai dati aziendali in una determinata app. È consigliabile consultare informazioni sul funzionamento dei [criteri di protezione delle app](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune). Di seguito è riportato un esempio di come documentare le applicazioni esistenti e la protezione richiesta.

| **Applicazione** | **Scopo** | **Piattaforme** | **Caso d'uso** | **Criterio di protezione dell'app** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Disponibile | iOS | Aziendale - Dirigenti | Non può essere jailbroken, crittografia dei file |                                                         
| Word | Disponibile | iOS, Android - Samsung Knox, non Knox, Windows 10 Mobile | Aziendale, BYOD | Non può essere jailbroken, crittografia dei file |                                                         

#### <a name="compliance-policies"></a>Criteri di conformità

I criteri di conformità determinano se un dispositivo è conforme a determinati requisiti. Intune usa i criteri di conformità per determinare se un dispositivo è considerato conforme o meno. Lo stato di conformità può quindi essere usato per limitare l'accesso alle risorse aziendali. Se è necessario l'accesso condizionale, è consigliabile progettare i [criteri di conformità dei dispositivi](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). Fare riferimento ai requisiti e casi d'uso per determinare quanti criteri di conformità dei dispositivi sono necessari e quali sono i gruppi di utenti di destinazione. È inoltre necessario determinare per quanto tempo un dispositivo può restare offline senza collegarsi prima che venga considerato non conforme.

Di seguito è riportato un esempio di come progettare i criteri di conformità:

| **Nome criterio** | **Piattaforma per i dispositivi** | **Impostazioni** | **Gruppo di destinazione** |   
|:---:|:---:|:---:|:---:|
| Criteri di conformità | iOS, Android - Samsung Knox, non Knox, Windows 10 Mobile | PIN - obbligatorio, non può essere jailbroken | Aziendale, BYOD |

#### <a name="conditional-access-policies"></a>Criteri di accesso condizionale

L'accesso condizionale viene usato per consentire solo ai dispositivi conformi di accedere alle risorse aziendali. Intune interagisce con Enterprise Mobility + Security (EMS) per controllare l'accesso alle risorse aziendali. È necessario determinare se è richiesto l'accesso condizionale e quali elementi devono essere protetti.

-   Altre informazioni sull'[accesso condizionale](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

Per l'accesso online, determinare a quali piattaforme e gruppi di utenti applicare i criteri di accesso condizionale.

Occorre inoltre stabilire se è necessario installare/configurare Intune Service to Service Connector per Exchange Online o Exchange locale.

Altre informazioni su come installare e configurare i connettori Service to Service Connector di Intune:

-   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange locale](https://docs.microsoft.com/intune/deploy-use/intune-on-premises-exchange-connector)

Di seguito è riportato un esempio di come documentare i criteri di accesso condizionale:

| **Servizio** | **Piattaforme per l'autenticazione moderna** | **Autenticazione base** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS, Android | Blocca i dispositivi non conformi sulle piattaforme supportate da Microsoft Intune | Aziendale, BYOD |
| SharePoint Online | iOS, Android |  | Aziendale, BYOD |

## <a name="next-section"></a>Sezione successiva

Nella sezione successiva vengono fornite indicazioni sul [processo di implementazione di Intune](section-8-onboarding-process.md).



<!--HONumber=Jan17_HO3-->


