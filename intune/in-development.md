---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bd5392abba3ea22127cb9bcbbb53ec4929f2d5e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166349"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>In fase di sviluppo per Microsoft Intune - Settembre 2019

Per supportare gli utenti nella preparazione e pianificazione, questa pagina illustra gli aggiornamenti e le funzionalità dell'interfaccia utente di Intune che sono in fase di sviluppo ma non ancora rilasciati. Inoltre:

- Se sono previste azioni prima di una modifica, verrà pubblicato un post complementare nel Centro messaggi di Office.
- Quando una funzionalità viene avviata nell'ambiente di produzione, sia in versione anteprima sia disponibile a livello generale, la descrizione della funzionalità verrà spostata da questa pagina alla [pagina delle novità](whats-new.md).
- Questa pagina e la [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere la [Roadmap di Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per informazioni sulle sequenze temporali e i risultati finali strategici.

> [!Note]
> Questi elementi riflettono le aspettative correnti di Microsoft sulle funzionalità di Intune introdotte in una versione futura. Le date e le singole funzionalità possono cambiare. Questa pagina non include una descrizione della funzione per tutti gli elementi in fase di sviluppo.

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestione delle app

### <a name="managed-google-play-private-lob-apps----1464182----"></a>App LOB private Google Play gestite <!-- 1464182  -->
Intune consente agli amministratori IT di pubblicare app LOB per Android private in Google Play gestite tramite un iframe incorporato nella console di Intune.  Attualmente gli amministratori IT devono pubblicare app LOB direttamente nella console di pubblicazione di Google Play, che richiede molti passaggi ed è molto dispendiosa in termini di tempo.  Questa nuova funzionalità consente di pubblicare facilmente app LOB con una serie di passaggi minima senza dover lasciare la console di Intune.  Uno degli scenari di gestione aziendale Android che usano Google Play gestiti può trarre vantaggio da questa funzionalità (profilo di lavoro, dispositivi dedicati, completamente gestiti e non registrati).  Da Intune, selezionare **App client** > **App** > **Aggiungi**. Quindi, selezionare **managed Google Play** dall'elenco **tipo di app** . Per altre informazioni sulle app Google Play gestite, vedere [aggiungere app Google Play gestite a dispositivi Android Enterprise con Intune](apps-add-android-for-work.md).

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Messaggi di stato di installazione dell'app Portale aziendale <!-- 2514416  -->
L'app Portale aziendale visualizzerà messaggi di stato di installazione dell'app aggiuntivi per gli utenti finali. Alle nuove funzionalità di dipendenza Win32 verranno applicate le condizioni seguenti:
- Non è stato possibile installare l'app. Le dipendenze definite dall'amministratore non sono state soddisfatte.
- L'app è stata installata correttamente, ma è necessario un riavvio.
- È in corso l'installazione dell'app, ma è necessario riavviare per continuare.

### <a name="managed-google-play-iframe-support----2871756----"></a>Supporto di iframe Google Play gestiti <!-- 2871756  -->
Intune fornirà supporto per l'aggiunta e la gestione di collegamenti Web direttamente nella console di Intune tramite l'iframe gestito del Google Play.  In questo modo gli amministratori IT inviano un URL e un'icona grafica e quindi distribuiscono i collegamenti ai dispositivi come le normali app Android. Uno degli scenari di gestione aziendale Android che usano Google Play gestiti può trarre vantaggio da questa funzionalità (profilo di lavoro, dispositivi dedicati, completamente gestiti e non registrati).  Da Intune, selezionare **App client** > **App** > **Aggiungi**. Quindi, selezionare **managed Google Play** dall'elenco **tipo di app** . Per altre informazioni sulle app Google Play gestite, vedere [aggiungere app Google Play gestite a dispositivi Android Enterprise con Intune](apps-add-android-for-work.md).

### <a name="macos-support-for-vpp-apps----3173501----"></a>Supporto macOS per app VPP <!-- 3173501  -->
Le app macOS acquistate con Apple Business Manager verranno visualizzate nella console quando vengono sincronizzati i token VPP Apple in Intune. È possibile assegnare, revocare e riassegnare le licenze basate su utenti e dispositivi per i gruppi usando la console. Microsoft Intune consente di gestire le app VPP acquistate per l'uso aziendale eseguendo le operazioni seguenti:
- Segnalazione delle informazioni di licenza dall'App Store.
- Verifica del numero di licenze usate.
- Blocco dell'installazione di un numero di copie dell'app superiore al numero di copie acquistate.
Per altre informazioni su Intune e VPP, vedere [Gestire le app e i libri acquistati con Volume Purchase Program con Microsoft Intune](vpp-apps.md).

### <a name="macos-support-for-web-apps----3174427----"></a>Supporto macOS per le app Web <!-- 3174427  -->
Sarà possibile installare nel Dock le app Web che consentono di aggiungere un collegamento a un URL sul Web usando il portale aziendale macOS. Gli utenti finali possono accedere all'azione **Installa** dalla pagina dei dettagli di un'app Web nel portale aziendale macOS. Per altre informazioni sul tipo di app di **collegamento Web** , vedere [aggiungere app a Microsoft Intune](apps-add.md).

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Assegnare Microsoft Edge beta per macOS <!-- 4678761  -->
Sarà possibile aggiungere e assegnare la versione più recente di Microsoft Edge beta a Intune per i dispositivi macOS. Da Intune selezionare app **client** > **app** > **Aggiungi app** > **Microsoft Edge-MacOS**. Quindi, assegnare Microsoft Edge beta ai gruppi desiderati. Microsoft AutoUpdate (MAU) mantiene Microsoft Edge aggiornato. Per altre informazioni su Microsoft Edge, vedere [gestire l'accesso Web tramite Microsoft Edge con Microsoft Intune](manage-microsoft-edge.md).

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Operazioni di lettura e scrittura API Graph per le app di Intune <!-- 5031704  -->
Le applicazioni saranno in grado di chiamare il API Graph Intune con operazioni di lettura e scrittura usando l'identità dell'app senza credenziali utente. Per altre informazioni sull'accesso all'API Microsoft Graph per Intune, vedere [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) (Usare Intune in Microsoft Graph).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurare il contenuto della notifica dell'app per gli account dell'organizzazione <!-- 2576686 -->
I criteri di protezione delle app di Intune (APP) nei dispositivi Android e iOS consentiranno di controllare il contenuto delle notifiche dell'app per gli account dell'organizzazione. Questa funzionalità richiede il supporto delle applicazioni e potrebbe non essere disponibile per tutte le applicazioni abilitate per l'APP. Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Creazione di report per le app disponibili in Google Play per i profili di lavoro Android <!-- 3041956  -->
Per le installazioni di app disponibili nei dispositivi con profilo di lavoro Android, è possibile visualizzare lo stato di installazione delle app e la versione installata delle app gestite in Google Play. Per altre informazioni, vedere [Come monitorare i criteri di protezione delle app](app-protection-policies-monitor.md), [Gestire i dispositivi con profilo di lavoro Android con Intune](android-enterprise-overview.md) e [Tipo di app Google Play gestite](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>Le funzionalità del dispositivo, le restrizioni dei dispositivi e i profili di estensione per le impostazioni di iOS e macOS sono visualizzate per tipo di registrazione <!-- 4886161  -->

In Intune è possibile creare i profili per i dispositivi iOS e MacOS (i**profili** > di**configurazione** > dei dispositivi**creano il profilo** > **iOS** o **MacOS** per le funzionalità della piattaforma > **dispositivo** , **Restrizioni del dispositivo**o **estensioni** per il tipo di profilo). Attualmente, le impostazioni disponibili in questi profili sono elencate. 

In un aggiornamento futuro le impostazioni disponibili nel portale di Intune saranno categorizzate in base al tipo di registrazione a cui si applicano:

- iOS
  - Tutti i tipi di registrazione
  - Registrazione del dispositivo e registrazione automatica dei dispositivi
  - Registrazione automatica dei dispositivi

- macOS
  - Tutti i tipi di registrazione
  - Registrazione del dispositivo
  - Registrazione del dispositivo approvata dall'utente e automatizzata
  - Registrazione automatica dei dispositivi

Si applica a:

- iOS
  - [Funzionalità dei dispositivi](ios-device-features-settings.md)
  - [Restrizioni dei dispositivi](device-restrictions-ios.md)

- macOS
  - [Funzionalità dei dispositivi](macos-device-features-settings.md)
  - [Restrizioni dei dispositivi](device-restrictions-macos.md)
  - [Estensioni](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>Nuove impostazioni di controllo vocale per i dispositivi iOS con supervisione in esecuzione in modalità tutto schermo <!-- 4892835  -->

In Intune è possibile creare criteri per l'esecuzione di dispositivi iOS supervisionati come chiosco multimediale o dispositivo dedicato (i**profili** > di**configurazione** > dei dispositivi**creano un profilo** > **iOS** per la piattaforma >  **Restrizioni del dispositivo** per il tipo di profilo > **chiosco (solo con supervisione)** ). 

In un aggiornamento futuro saranno disponibili nuove impostazioni che è possibile controllare:

- **Controllo vocale**: Abilita il controllo vocale sul dispositivo in modalità tutto schermo.
- **Modifica del controllo vocale**: consente agli utenti di modificare l'impostazione del controllo vocale nel dispositivo in modalità tutto schermo.

Per visualizzare le impostazioni correnti, passare a [impostazioni del chiosco iOS (solo con supervisione)](device-restrictions-ios.md#kiosk).

Si applica a:

- iOS 13.0 e versioni successive

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>Usare Single Sign-On per app e siti Web nei dispositivi iOS e macOS <!-- 4893175  -->
In un aggiornamento futuro saranno disponibili alcune nuove impostazioni Single Sign-on per i dispositivi iOS e MacOS (i**profili** > di**configurazione** > dei dispositivi**creano il profilo** > **iOS** o **MacOS** per funzionalità del **dispositivo** > piattaforma per il tipo di profilo).

Usare queste impostazioni per configurare un'esperienza di Single Sign-On, in particolare per le app e i siti Web che usano l'autenticazione Kerberos. È possibile scegliere tra una credenziale generica Single Sign-On estensione dell'app e l'estensione Kerberos predefinita di Apple.

Per visualizzare le funzionalità correnti del dispositivo che è possibile configurare, passare a funzionalità del dispositivo [iOS](ios-device-features-settings.md) e [funzionalità del dispositivo MacOS](macos-device-features-settings.md).

Si applica a:

- iOS 13.0 e versioni successive
- macOS 10.15 e versioni successive

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>Associare i domini alle app nei dispositivi macOS 10.15 + <!-- 4898079  -->
Nei dispositivi MacOS è possibile configurare funzionalità diverse ed effettuare il push di queste funzionalità nei dispositivi usando un criterio (i**profili** > di**configurazione** > dei dispositivi**creano il profilo** > **MacOS** per funzionalità del **dispositivo** > piattaforma per il tipo di profilo). In un aggiornamento futuro sarà possibile associare i domini alle app. Questa funzionalità consente di condividere le credenziali con i siti Web correlati all'app e può essere usata con l'estensione Single Sign-On di Apple, i collegamenti universali e il riempimento automatico delle password. 

Per visualizzare le funzionalità correnti che è possibile configurare, passare a [impostazioni delle funzionalità del dispositivo MacOS in Intune](macos-device-features-settings.md).

Si applica a:

- macOS 10.15 e versioni successive

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>Usare "iTunes" e "app" nell'URL di iTunes App Store quando si visualizzano o nascondono le app nei dispositivi iOS con supervisione <!-- 4928474  --> 
In Intune è possibile creare criteri per mostrare o nascondere le app nei dispositivi iOS supervisionati (i**profili** > di**configurazione** > dei dispositivi**creano il profilo** > **iOS** per la piattaforma > **dispositivo restrizioni** per il tipo di profilo > **mostrare o nascondere le app (solo con supervisione)** ). 

È possibile immettere l'URL di iTunes App Store, ad `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`esempio. In un aggiornamento futuro, sarà possibile usare sia `apps` che `itunes` nell'URL, ad esempio:

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Per altre informazioni su queste impostazioni, vedere [mostrare o nascondere le app](device-restrictions-ios.md#show-or-hide-apps).

Si applica a:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Supporto per i profili VPN IKEv2 per iOS <!-- 1943438 -->
È possibile creare profili VPN per il client VPN nativo di iOS tramite il protocollo IKEv2. IKEv2 è un nuovo tipo di connessione in **Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS**  per la piattaforma > **VPN** per il tipo di profilo > **Impostazioni**.

Questi profili VPN configurano il client VPN nativo. Pertanto, non viene installata alcuna app del client VPN, e non ne viene eseguito il push, nei dispositivi gestiti. Questa funzionalità richiede che i dispositivi siano registrati in Intune (registrazione MDM).

Per visualizzare le impostazioni VPN correnti che è possibile configurare, vedere [Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune](vpn-settings-ios.md).

Si applica a: iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>Registrazione del dispositivo

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Per impostazione predefinita, i nuovi tenant sono lontani dalla gestione amministratore dispositivi Android <!-- 4869790  -->
Le funzionalità di amministratore dei dispositivi Android sono state sostituite da Android Enterprise. È quindi consigliabile usare Android Enterprise per le nuove registrazioni. In un aggiornamento futuro, i nuovi tenant dovranno completare i seguenti passaggi dei prerequisiti nella registrazione di Android per l'uso della gestione degli amministratori dei dispositivi: passare a **Intune** > registrazione del**dispositivo registrazione** > **Android** I dispositivi **personali e di proprietà dell'azienda con privilegi** > di amministrazione dei dispositivi**usano l'amministratore del dispositivo per gestire i dispositivi**.  > 

I tenant esistenti non subiscono alcuna modifica nei propri ambienti. 

Per altre informazioni sull'amministratore del dispositivo Android in Intune, vedere [registrazione dell'amministratore del dispositivo Android](android-enroll-device-administrator.md).

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Per i dispositivi iOS, personalizzare la schermata relativa alla privacy del processo di registrazione del portale aziendale <!-- 4394993  -->
Usando il markdown è possibile personalizzare la schermata relativa alla privacy del portale aziendale visualizzata dagli utenti finali durante la registrazione iOS. In particolare, è possibile personalizzare l'elenco di elementi che l'organizzazione non può visualizzare o eseguire sul dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Distribuire gli aggiornamenti software nei dispositivi macOS <!-- 3194876 -->
Sarà possibile distribuire gli aggiornamenti software a gruppi di dispositivi macOS. Questa funzionalità include l'errore critico, il firmware, il file di configurazione e altri aggiornamenti. Sarà possibile inviare aggiornamenti durante l'archiviazione del dispositivo successivo oppure selezionare una pianificazione settimanale per distribuire gli aggiornamenti in o fuori dal tempo di Windows impostati. Questo consente di aggiornare i dispositivi al di fuori delle ore di lavoro standard o quando il help desk è completamente al personale. Si otterrà anche un report dettagliato di tutti i dispositivi macOS con aggiornamenti distribuiti. È possibile esaminare il report per ogni singolo dispositivo per visualizzare gli Stati di determinati aggiornamenti.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>Inviare notifiche personalizzate a un dispositivo <!-- 4928910  -->
Sarà possibile inviare notifiche personalizzate a dispositivi specifici in cui è installata l'app Portale aziendale o Intune. A tale scopo, passare a**dispositivi** >  **Intune** > **tutti i dispositivi** > scegliere un dispositivo **> più** > **Invia notifica personalizzata**. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Aggiornamenti alle funzionalità completamente gestite di Android Enterprise <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Verrà aggiunto il supporto seguente per i dispositivi Android completamente gestiti:

- I certificati SCEP per Android completamente gestiti saranno disponibili per l'autenticazione del certificato nei dispositivi gestiti come proprietario del dispositivo. I certificati SCEP sono già supportati nei dispositivi del profilo di lavoro.  Con i certificati SCEP per il proprietario del dispositivo, sarà possibile: <!-- 5227935 -->
    - Crea il profilo SCEP nella sezione DO di Android Enterprise
    - Collegare i certificati SCEP per il profilo Wi-Fi per l'autenticazione
    - Collegare i certificati SCEP per eseguire i profili VPN per l'autenticazione
    - Collegare i certificati SCEP per eseguire i profili di posta elettronica per l'autenticazione (tramite la configurazione dell'app)
- Le app di sistema saranno supportate nei dispositivi Android Enterprise. In Intune si aggiungerà un'app Android Enterprise System selezionando app **client** > **app** > **Aggiungi**. Nell'elenco **tipo di app** selezionare **Android Enterprise System app**. Per altre informazioni sull'aggiunta di app a Intune, vedere [Aggiungere app in Microsoft Intune](apps-add.md). <!-- 4062195 -->
- In **Device Compliance** > **Android Enterprise** > **Device Owner**, sarà possibile creare un criterio di conformità che imposta il livello di attestazione di Google SafetyNET.   <!-- 4631425 -->
- Nei dispositivi Android Enterprise completamente gestiti, i provider Mobile Threat Defense saranno supportati. In **Device Compliance** > **Android Enterprise** > **Device Owner**è possibile scegliere un livello di minaccia accettabile. <!-- 4631440 --> [Impostazioni di Android Enterprise per contrassegnare un dispositivo come conforme o non conforme in Intune](compliance-policy-create-android-for-work.md#device-owner) elenca le impostazioni attuali.


Si applica a: 
- Dispositivi completamente gestiti Android Enterprise

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

### <a name="updated-support-experience-------5012398------"></a>Esperienza di supporto aggiornata   <!--  5012398    -->
Nell'ambito dei miglioramenti continui, l'esperienza di supporto nella console per Intune verrà aggiornata.  Verranno migliorati la ricerca e il feedback nella console per i problemi comuni e verrà semplificato il flusso di lavoro per contattare il supporto tecnico.     

<!-- ***********************************************-->
## <a name="security"></a>Sicurezza

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Protezione dalle manomissioni per Windows Defender Antivirus  <!-- 4705448       -->
Verrà aggiunta la *protezione dalle manomissioni* alle impostazioni che Intune può gestire per Windows Defender Antivirus. Sarà possibile usare un profilo di configurazione del dispositivo per Windows 10 Endpoint Protection per attivare o disattivare la protezione dalle manomissioni.  Per altre informazioni sulla protezione dalle manomissioni, vedere [impedire modifiche alle impostazioni di sicurezza con la protezione dalle manomissioni](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) nella documentazione di Windows. 


<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).




