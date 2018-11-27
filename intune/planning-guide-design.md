---
title: Creare una progettazione
titlesuffix: Microsoft Intune
description: Questo articolo semplifica la creazione di una progettazione per un'implementazione di Microsoft Intune in configurazione solo cloud.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.openlocfilehash: 1d8ccd4e432623cf7d0ce4ce66651a95e13b8473
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186495"
---
# <a name="create-a-design"></a>Creare una progettazione

La progettazione di Intune è basata sulle informazioni raccolte e sulle decisioni prese durante il completamento delle altre [sezioni di questa guida](planning-guide.md). Consente di riunire:

-   Ambiente corrente

-   Opzioni per la distribuzione di Intune

-   Requisiti di identità per le dipendenze esterne

-   Considerazioni sulle piattaforme per i dispositivi

-   Requisiti da soddisfare  

Anche se i requisiti dell'infrastruttura locale sono minimi, definire un piano di progettazione è comunque utile per essere certi di disporre della soluzione di gestione dei dispositivi mobili più adatta per gli scopi, gli obiettivi e i requisiti dell'organizzazione.

Esaminiamo ognuna di queste aree più in dettaglio. 

## <a name="record-your-current-environment"></a>Registrare l'ambiente corrente
Inoltre, spesso vengono apportate modifiche di progettazione durante le fasi di implementazione e di test. Usare il piano di progettazione per documentare queste modifiche e le motivazioni corrispondenti.

L'ambiente corrente può influenzare le decisioni di progettazione e deve essere documentato e tenuto presente quando si prendono altre decisioni sulla progettazione di Intune. Di seguito sono riportati alcuni esempi di come registrare l'ambiente corrente:

-   **Identità nel cloud**

    -   Viene usato DirSync o Azure Active Directory (Azure AD) Connect?

    -   L'ambiente è federato?

    -   È abilitato per l'autenticazione a più fattori?

-   **Ambiente di posta elettronica**

    -   Si usa Exchange? In locale o nel cloud?

    -   È in corso un progetto per la migrazione di Exchange nel cloud?

-   **Soluzione corrente di gestione dei dispositivi mobili (MDM)**

    -   Vengono attualmente usate altre soluzioni MDM?

    -   Quali soluzioni MDM vengono usate per gli scenari dei casi d'uso aziendali e BYOD?

    -   Quali funzionalità vengono usate (ad esempio: impostazioni per le app dei dispositivi, configurazioni Wi-Fi)?

    -   Quali piattaforme per i dispositivi sono supportate?

    -   Quali gruppi e quanti utenti usano la soluzione MDM?

-   **Soluzione per i certificati**

    -   È stata implementata una soluzione per i certificati?

    -   Che tipo di certificati vengono usati?

-   **Gestione dei sistemi**

    -   Come viene gestito l'ambiente PC e server?

    -   Si usa System Center Configuration Manager? Viene usata una piattaforma di gestione dei sistemi di terze parti?

-   **Soluzione VPN**

    -   Quale soluzione VPN viene usata?

    -   Questa soluzione viene usata sia per gli scenari dei casi d'uso aziendali che BYOD?

Durante la registrazione dell'ambiente MDM corrente, assicurarsi di prendere nota di eventuali progetti o altri piani che potrebbero influire sull'ambiente. Di seguito è riportato un esempio di come registrare l'ambiente corrente durante la creazione della progettazione per Intune:

| **Area di soluzioni** | **Ambiente corrente** | **Commenti** |
|---|---|---|
| **Identità** | Azure AD, Azure AD Connect, non federato, senza autenticazione a più fattori | Progetto per abilitare l'autenticazione a più fattori entro la fine dell'anno |                 
| **Ambiente di posta elettronica** | Exchange locale, Exchange Online | Migrazione in corso da Exchange locale a Exchange Online. È stata eseguita la migrazione del 75% delle cassette postali. La migrazione dell'ultimo 25% verrà eseguita prima dell'avvio del progetto pilota di Intune. |                
| **SharePoint** | SharePoint locale | Nessun piano per la migrazione a SharePoint Online |  
| **Soluzione MDM corrente** | Exchange ActiveSync |  |
| **Soluzione per i certificati** | Microsoft Server 2012 R2, Servizi certificati Active Directory | Uso di PKI solo per i server del sito Web |
| **Gestione dei sistemi** | System Center Configuration Manager CB 1606 | Potrebbe essere utile valutare una soluzione ibrida Intune |
| **Soluzione VPN** | Cisco AnyConnect |  |


Per sviluppare il piano della progettazione di Intune, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

## <a name="choose-an-intune-deployment-option"></a>Scegliere un'opzione di distribuzione per Intune

Intune offre due opzioni di distribuzione: versione autonoma e configurazione ibrida. La versione autonoma si riferisce al servizio Intune in esecuzione nel cloud, mentre la configurazione ibrida si riferisce all'integrazione di Intune con System Center Configuration Manager. Questa guida è destinata principalmente all'uso della versione autonoma. [Decidere quale opzione è più adatta per i requisiti aziendali](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

## <a name="intune-tenant-location"></a>Posizione del tenant Intune

Se l'organizzazione ha una presenza globale, assicurarsi di pianificare la posizione del tenant al momento della sottoscrizione del servizio. Il paese viene definito quando ci si iscrive per la prima volta per ottenere una sottoscrizione di Intune ed è associato alle aree internazionali elencate di seguito:

-   America del Nord

-   Europa, Medio Oriente e Africa

-   Asia e Pacifico

>[!IMPORTANT]
> Non è possibile modificare il paese e la posizione del tenant in un secondo momento.

## <a name="external-dependencies"></a>Dipendenze esterne

Le dipendenze esterne sono servizi e prodotti distinti da Intune, ma che rappresentano un requisito per Intune o che possono essere integrati con Intune. È importante identificare i requisiti per le dipendenze esterne e il modo in cui devono essere configurati. Alcuni esempi di dipendenze esterne comuni sono:

-   Identità

-   Gruppi di utenti e dispositivi

-   Infrastruttura a chiave pubblica (PKI)

Queste dipendenze esterne comuni sono illustrate più in dettaglio di seguito

### <a name="identity"></a>Identità

L'identità è il modo in cui vengono identificati gli utenti che appartengono all'organizzazione e che eseguono la registrazione di un dispositivo. Intune richiede Azure Active Directory (Azure AD) come provider di identità utente. Se si usa già questo servizio, è possibile usare l'identità esistente già presente nel cloud. Inoltre, Azure AD Connect è lo strumento consigliato per la sincronizzazione delle identità utente locali con i servizi cloud Microsoft. Se l'organizzazione usa già Office 365, è importante che Intune usi lo stesso ambiente Azure AD.

Altre informazioni sui requisiti di identità di Intune seguenti:

- [Requisiti di identità](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions).

- [Requisiti di sincronizzazione delle directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

- [Requisiti dell'autenticazione a più fattori](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

### <a name="user-and-device-groups"></a>Gruppi di utenti e dispositivi

I gruppi di utenti e dispositivi determinano la destinazione di una distribuzione, inclusi criteri, applicazioni e profili. È necessario determinare quali gruppi di utenti e dispositivi saranno richiesti.

È consigliabile creare tutti i gruppi in Active Directory locale, quindi sincronizzarli con Azure AD. Altre informazioni sulla pianificazione e la creazione di gruppi di utenti e dispositivi:

-   [Pianificare i gruppi di utenti e dispositivi](users-add.md).

-   [Creare gruppi di utenti e dispositivi](groups-add.md).

### <a name="public-key-infrastructure-pki"></a>Infrastruttura a chiave pubblica (PKI)
L'infrastruttura a chiave pubblica fornisce certificati a dispositivi o utenti per consentire l'autenticazione sicura in un servizio. Intune supporta un'infrastruttura PKI Microsoft. Possono essere emessi certificati utente e dispositivo per un dispositivo mobile per soddisfare i requisiti dell'autenticazione basata su certificati. Prima di usare i certificati, è necessario determinare se sono richiesti, se l'infrastruttura di rete può supportare l'autenticazione basata su certificati e se sono attualmente in uso certificati nell'ambiente esistente.

Se si prevede di usare certificati con profili VPN, Wi-Fi o di posta elettronica con Intune, assicurarsi di disporre di un'[infrastruttura PKI](certificates-configure.md) supportata, pronta per la creazione e la distribuzione dei profili certificato.

Inoltre, se verranno emessi certificati SCEP, è necessario determinare quale server ospiterà la funzionalità Servizio Registrazione dispositivi di rete (NDES) e come avverrà la comunicazione.

Sono disponibili altre informazioni su:

-   [Come configurare i profili certificato di Intune](certificates-configure.md)

-   [Come configurare l'infrastruttura di certificazione per SCEP](certificates-scep-configure.md)

-   [Come configurare l'infrastruttura di certificazione per PFX](certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>Considerazioni sulle piattaforme per i dispositivi

È opportuno valutare attentamente gli aspetti seguenti dei dispositivi per comprendere come gestirli in modo corretto.

-   Piattaforme per dispositivi supportate

-   Dispositivi

-   Proprietà del dispositivo

-   Registrazione in blocco

Esaminiamo queste aree più in dettaglio.

### <a name="determine-supported-device-platforms"></a>Determinare le piattaforme per dispositivi supportate

Durante la creazione della progettazione, è necessario sapere quali dispositivi saranno presenti nell'ambiente e verificare se sono supportati o meno da Intune. Intune supporta le piattaforme iOS, Android e Windows.

[Elenco completo dei dispositivi supportati da Intune](supported-devices-browsers.md).

### <a name="devices"></a>Dispositivi

Intune gestisce i dispositivi mobili per proteggere i dati aziendali e consentire agli utenti finali di lavorare da diverse posizioni. Intune supporta molte piattaforme, pertanto è consigliabile documentare i dispositivi e le piattaforme e le versioni per i sistemi operativi che saranno supportati nella progettazione dell'organizzazione. Ad esempio:

| **Piattaforma per i dispositivi** | **Versioni del sistema operativo** |
|:---:|:---:|
| iOS - iPhone | 10.0+ |                
| iOS - iPad | 10.0+ |               
| Android - Samsung Knox Standard | 4.0+ |
| Tablet Windows 10 | 10+ |


Per creare l'elenco dei dispositivi, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
### <a name="device-ownership"></a>Proprietà del dispositivo

Intune supporta sia dispositivi di proprietà dell'azienda che personali. Un dispositivo è considerato di proprietà dell'azienda se viene registrato da un manager di registrazione dispositivi o da un programma di registrazione dispositivi. Ad esempio, un dispositivo viene registrato tramite il programma DEP (Device Enrollment Program) di Apple, contrassegnato come aziendale e inserito in un gruppo di dispositivi che riceve criteri e app aziendali mirati.

Per altre informazioni sui casi d'uso aziendali e BYOD, fare riferimento a [Sezione 3: Determinare i requisiti degli scenari per i casi d'uso](planning-guide-requirements.md).

### <a name="bulk-enrollment"></a>Registrazione in blocco

 È possibile registrare i dispositivi in blocco in diversi modi a seconda della piattaforma. Se è richiesta la registrazione in blocco, è innanzitutto necessario [determinare il metodo di registrazione in blocco](device-enrollment.md) e incorporarlo nella progettazione.

## <a name="feature-requirements"></a>Requisiti per le funzionalità

In queste sezioni vengono descritte le seguenti caratteristiche e funzionalità, allineate con i requisiti degli scenari dei casi d'uso:

-   Criteri di termini e condizioni

-   Criteri di configurazione

-   Profili di risorse

-   App

-   Criteri di conformità

-   Accesso condizionale

Esaminiamo ognuna di queste aree più in dettaglio.

### <a name="terms-and-conditions-policies"></a>Criteri di termini e condizioni

[Termini e condizioni](terms-and-conditions-create.md) possono essere usati per descrivere i criteri o le condizioni che un utente finale deve accettare prima di poter registrare un dispositivo. Intune supporta la possibilità di aggiungere e distribuire più criteri di termini e condizioni per i gruppi di utenti.

È necessario determinare se sono richiesti criteri di termini e condizioni. In questo caso, occorre stabilire chi sarà responsabile di fornire queste informazioni all'interno dell'organizzazione. Di seguito è riportato un esempio di come documentare i criteri di termini e condizioni.

| **Nome termini e condizioni** | **Caso d'uso** | **Gruppo di destinazione** |
|:---:|:---:|:---:|
| Termini e condizioni aziendali | Aziendale | Utenti aziendali |                 
| Termini e condizioni BYOD | BYOD | Utenti BYOD |                


Per creare una mappa di termini e condizioni associati ai vari gruppi di utenti, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

### <a name="configuration-policies"></a>Criteri di configurazione

Usare i criteri di configurazione per gestire le impostazioni di sicurezza e le funzionalità in un dispositivo. Quando si progettano i criteri di configurazione, fare riferimento alla sezione relativa ai requisiti per i casi d'uso per determinare le configurazioni necessarie per i dispositivi Intune. Documentare le impostazioni e come deve essere configurate. Documentare anche a quali gruppi di utenti o dispositivi sono destinate.

È necessario creare almeno un criterio di configurazione per ogni piattaforma. Se necessario, è possibile creare più criteri di configurazione per ogni piattaforma. Di seguito è riportato un esempio di progettazione di quattro criteri di configurazione diversi per differenti piattaforme e casi d'uso.

| **Nome criterio** | **Piattaforma per i dispositivi** | **Impostazioni** | **Gruppo di destinazione** |   
|:---:|:---:|:---:|:---:|
| Aziendale - iOS | iOS | PIN obbligatorio, lunghezza: 6, limitazione del backup cloud | Dispositivi aziendali |                                                           
| Aziendale - Android | Android | PIN obbligatorio, lunghezza: 6, limitazione del backup cloud | Dispositivi aziendali |                                                           
| BYOD - iOS  | iOS | PIN obbligatorio, lunghezza: 4 | Dispositivi BYOD |
| BYOD - Android  | Android | PIN obbligatorio, lunghezza: 4 | Dispositivi BYOD |


Per determinare le esigenze specifiche a livello di criteri di configurazione, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

### <a name="profiles"></a>Profiles

Usare i profili per consentire all'utente finale di connettersi ai dati aziendali. Intune supporta diversi tipi di profili. Fare riferimento ai casi d'uso e ai requisiti per determinare quando verranno configurati i profili. Tutti i profili dispositivo devono essere classificati in base al tipo di piattaforma e inclusi nella documentazione della progettazione.

-   Profili certificato

-   Profilo Wi-Fi

-   Profilo VPN

-   Profilo di posta elettronica

Esaminiamo ogni tipo di profilo più in dettaglio.

#### <a name="certificate-profiles"></a>Profili certificato

I profili certificato consentono a Intune di emettere un certificato per un utente o un dispositivo. Intune supporta:

-   Simple Certificate Enrollment Protocol (SCEP)

-   Certificato radice attendibile

-   Certificato PFX.

È consigliabile documentare quale gruppo di utenti richiede un certificato, quanti profili certificato sono necessari e a quali gruppi di utenti distribuirli.

>[!NOTE]
> Tenere presente che il certificato radice attendibile è necessario per il certificato SCEP, pertanto verificare che tutti gli utenti a cui è assegnato il certificato SCEP ricevano anche un certificato radice attendibile. Se sono necessari certificati SCEP, progettare e documentare i modelli di certificato SCEP necessari.

Di seguito è riportato un esempio di come documentare i certificati durante la progettazione:

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| CA radice | CA radice aziendale | Android, iOS, Windows Mobile | Aziendale, BYOD  |                                                           
| SCEP | Certificato utente | Android, iOS, Windows Mobile | Aziendale, BYOD |                                                           


Per determinare le esigenze specifiche a livello di profili di certificato, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

#### <a name="wi-fi-profile"></a>Profilo Wi-Fi

I profili Wi-Fi vengono usati per connettere automaticamente un dispositivo mobile a una rete wireless. Intune supporta la distribuzione di profili Wi-Fi per tutte le piattaforme supportate. Altre informazioni sul [supporto di Intune per i profili Wi-Fi.](wi-fi-settings-configure.md)

Di seguito è riportato un esempio di progettazione di un profilo Wi-Fi:

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Profilo Wi-Fi Asia | Android | Aziendale, BYOD Asia|                                                           
| Wi-Fi | Profilo Wi-Fi America del Nord | Android, iOS, Windows 10 Mobile | Aziendale, BYOD America del Nord |                                                           


Per determinare le esigenze specifiche a livello di profili Wi-Fi, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

#### <a name="vpn-profile"></a>Profilo VPN

I profili VPN consentono agli utenti di accedere in modo sicuro alla rete da posizioni remote. Intune supporta i profili VPN di connessioni VPN native e fornitori di terze parti. Altre informazioni su [profili VPN e fornitori supportati da Intune](vpn-settings-configure.md).

Di seguito è riportato un esempio di come documentare la progettazione di un profilo VPN.

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Connessione | Profilo VPN Cisco AnyConnect | Android, iOS, Windows 10 Mobile | Aziendale, BYOD America del Nord e Germania|                                                           
| Connessione | Pulse Secure | Android | Aziendale, BYOD Asia |                                                           


Per determinare le esigenze specifiche a livello di profili VPN, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
#### <a name="email-profile"></a>Profilo di posta elettronica

I profili di posta elettronica consentono la configurazione automatica di un client di posta elettronica con le informazioni di connessione e la configurazione della posta elettronica. Intune supporta i profili di posta elettronica in alcuni dispositivi. Altre informazioni sui [profili di posta elettronica e le piattaforme supportate](email-settings-configure.md).

Di seguito è riportato un esempio di come documentare la progettazione dei profili di posta elettronica:

| **Tipo** | **Nome profilo** | **Piattaforma per i dispositivi** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Profilo di posta elettronica | Profilo di posta elettronica iOS | iOS | Aziendale - BYOD information worker |                                                           
| Profilo di posta elettronica | Profilo di posta elettronica Android Knox | Android Knox | BYOD |


Per determinare le esigenze specifiche a livello di profili di posta elettronica, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
### <a name="apps"></a>App

È possibile usare Intune per distribuire app a utenti o dispositivi in diversi modi. I tipi di applicazione includono app di programmi di installazione di software, app di un app store pubblico, collegamenti esterni o app iOS gestite. Oltre a distribuire singole app, è possibile gestire e distribuire le app acquistate tramite i programmi Volume Purchase Program per iOS e Windows. Sono disponibili altre informazioni su:

-   [Tipi di app che è possibile distribuire](app-management.md)

-   [VPP (Volume Purchase Program) per le aziende per iOS](vpp-apps-ios.md)

-   [App di Microsoft Store per le aziende](windows-store-for-business.md)

#### <a name="app-type-requirements"></a>Requisiti per il tipo di app

Poiché è possibile distribuire app a utenti e dispositivi, è consigliabile decidere quali applicazioni verranno gestite da Intune. Durante la compilazione dell'elenco, provare a rispondere alle domande seguenti:

-   Le app richiedono l'integrazione con i servizi cloud?

-   Per gli utenti BYOD saranno disponibili tutte le app?

-   Quali sono le opzioni di distribuzione disponibili per queste app?

-   La società ha l'esigenza di consentire l'accesso ai dati di SaaS (Software as a Service) ai propri partner?

-   Le app richiedono l'accesso a Internet dai dispositivi degli utenti?

-   Le app sono disponibili in un app store pubblico o sono app line-of-business (LOB) personalizzate?


#### <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione delle app consentono di ridurre al minimo le perdite di dati, definendo le modalità di gestione dei dati aziendali nell'applicazione. Intune supporta i criteri di protezione delle app per qualsiasi applicazione progettata per il funzionamento con le soluzioni di gestione delle app per dispositivi mobili. Durante la progettazione dei criteri di protezione delle app, è necessario decidere quali restrizioni si vogliono applicare ai dati aziendali in una determinata app. È consigliabile consultare le informazioni sul funzionamento dei [criteri di protezione delle app](app-protection-policy.md). Di seguito è riportato un esempio di come documentare le applicazioni esistenti e la protezione richiesta.

| **Applicazione** | **Scopo** | **Piattaforme** | **Caso d'uso** | **Criterio di protezione dell'app** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Disponibile | iOS | Aziendale - Dirigenti | Non può essere jailbroken, crittografia dei file |                                                         
| Word | Disponibile | iOS, Android - Samsung Knox, non Knox, Windows 10 Mobile | Aziendale, BYOD | Non può essere jailbroken, crittografia dei file |                                                         


Per determinare le esigenze specifiche a livello di criteri di protezione delle app, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
#### <a name="compliance-policies"></a>Criteri di conformità

I criteri di conformità determinano se un dispositivo è conforme a determinati requisiti. Intune usa i criteri di conformità per determinare se un dispositivo è considerato conforme o meno. Lo stato di conformità può quindi essere usato per limitare o consentire l'accesso alle risorse aziendali. Se è necessario l'accesso condizionale, è consigliabile progettare i [criteri di conformità dei dispositivi](device-compliance.md).

Fare riferimento ai requisiti e casi d'uso per determinare quanti criteri di conformità dei dispositivi sono necessari e quali sono i gruppi di utenti di destinazione. È inoltre necessario decidere per quanto tempo un dispositivo può restare offline senza collegarsi prima che venga considerato non conforme.

Di seguito è riportato un esempio di come progettare i criteri di conformità:

| **Nome criterio** | **Piattaforma per i dispositivi** | **Impostazioni** | **Gruppo di destinazione** |   
|:---:|:---:|:---:|:---:|
| Criteri di conformità | iOS, Android - Samsung Knox, non Knox, Windows 10 Mobile | PIN - obbligatorio, non può essere jailbroken | Aziendale, BYOD |


Per determinare le esigenze specifiche a livello di criteri di conformità, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
#### <a name="conditional-access-policies"></a>Criteri di accesso condizionale

L'accesso condizionale viene usato per consentire solo ai dispositivi conformi di accedere alla posta elettronica e ad altre risorse aziendali. Intune interagisce con Enterprise Mobility + Security (EMS) per controllare l'accesso alle risorse aziendali. È necessario decidere se è richiesto l'accesso condizionale e quali elementi devono essere protetti. Altre informazioni sull'[accesso condizionale](conditional-access.md).

Per l'accesso online, decidere le piattaforme e i gruppi di utenti a cui saranno destinati i criteri di accesso condizionale. Stabilire inoltre se è necessario installare o configurare Intune Service to Service Connector per Exchange Online o Exchange locale. Altre informazioni su come installare e configurare i connettori Service to Service Connector di Intune: <!---these links are correct--->

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange locale](exchange-connector-install.md)

Di seguito è riportato un esempio di come documentare i criteri di accesso condizionale:

| **Servizio** | **Piattaforme per l'autenticazione moderna** | **Autenticazione base** | **Casi d'uso** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS, Android | Blocca i dispositivi non conformi sulle piattaforme supportate da Microsoft Intune | Aziendale, BYOD |
| SharePoint Online | iOS, Android |  | Aziendale, BYOD |

Per determinare le esigenze specifiche a livello di criteri di accesso condizionale, è possibile [scaricare un modello della tabella qui sopra](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

## <a name="next-steps"></a>Passaggi successivi

Nella sezione successiva vengono fornite indicazioni sul [processo di implementazione di Intune](planning-guide-onboarding.md).
