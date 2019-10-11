---
title: Novità di Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Informazioni sulle novità nel portale di Intune di Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 571974e1736fb78ae633c02fcfd6e6233056379b
ms.sourcegitcommit: 78f9750712c254d8b123ef15b74f30ca999aa128
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71920133"
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre ad [avvisi importanti](#notices), [versioni precedenti](whats-new-archive.md) e informazioni su [come vengono rilasciati gli aggiornamenti del servizio Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728).

> [!Note]
> La distribuzione di ogni [aggiornamento mensile](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728), che può impiegare fino a tre giorni, avviene nell'ordine seguente:
>
> - Giorno 1: Asia Pacifico
> - Giorno 2: Europa, Medio Oriente, Africa
> - Giorno 3: America del Nord
>
> Alcune funzionalità potrebbero essere implementate nel corso di settimane e potrebbero non essere disponibili a tutti i clienti nella prima settimana.
>
> Per un elenco delle funzionalità che verranno rilasciate prossimamente, vedere la [pagina delle funzionalità in fase di sviluppo](in-development.md).

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Settimana del 23 settembre 2019

#### <a name="ios-user-enrollment-in-preview----4817900---"></a>Registrazione utenti iOS in anteprima <!-- 4817900 -->
La versione di Apple iOS 13.1 include la registrazione utenti, un nuovo modulo di gestione semplificata per i dispositivi iOS. Può essere usato al posto della registrazione dei dispositivi o della registrazione automatica dei dispositivi (in precedenza Device Enrollment Program) per i dispositivi di proprietà personale. L'anteprima di Intune supporta questo set di funzionalità consentendo di:

- Riservare la registrazione utenti ai gruppi di utenti.
- Offrire agli utenti finali la possibilità di scegliere tra la registrazione utenti semplificata o la registrazione dei dispositivi avanzata quando registrano i loro dispositivi.

A partire dal 24/9/2019, con il rilascio di iOS 13.1, il processo di implementazione di questi aggiornamenti è in corso per tutti gli utenti e dovrebbe essere completato entro la fine della settimana prossima.
Si applica a:

iOS 13.1 e versioni successive

#### <a name="intune-support-for-ipados-and-ios-131-devices---5439574--"></a>Supporto di Intune per dispositivi iPadOS e iOS 13.1 <!--5439574-->
Attualmente Intune supporta la gestione dei dispositivi sia iPadOS che iOS 13.1. Per altre informazioni, vedere [questo post di blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Settimana del 16 settembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app 

#### <a name="managed-google-play-private-lob-apps----1464182----"></a>App line-of-business private in Google Play gestito <!-- 1464182  -->
Intune consente ora agli amministratori IT di pubblicare app line-of-business Android private in Google Play gestito tramite un iFrame incorporato nella console di Intune.  In precedenza gli amministratori IT dovevano pubblicare le app line-of-business direttamente nella console di pubblicazione di Google Play, operazione che richiedeva diversi passaggi ed era molto dispendiosa in termini di tempo. Questa nuova funzionalità consente di pubblicare facilmente app line-of-business con una serie di passaggi minimi, senza dover lasciare la console di Intune.  Gli amministratori non dovranno più eseguire manualmente la registrazione come sviluppatori in Google e pagare i 25 dollari di registrazione.  Tutti gli scenari di gestione con Android Enterprise che usano Google Play gestito possono trarre vantaggio da questa funzionalità: dispositivi con profilo di lavoro, dedicati, completamente gestiti e non registrati. Da Intune, selezionare **App client** > **App** > **Aggiungi**. Selezionare quindi **Google Play gestito** dall'elenco **Tipo di app**. Per altre informazioni su Google Play gestito vedere [Aggiungere app di Google Play gestito a dispositivi Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience----1473353-3598357---"></a>Uso del Portale aziendale Windows <!-- 1473353, 3598357 -->
Il Portale aziendale Windows è in fase di aggiornamento. Al suo interno sarà possibile usare più filtri nella pagina delle app. Anche la pagina dei dettagli dei dispositivi è in fase di aggiornamento con un'esperienza utente migliorata. Il processo di implementazione di questi aggiornamenti è attualmente in corso per tutti gli utenti e dovrebbe essere completato entro la fine della settimana prossima.

#### <a name="macos-support-for-web-apps----3174427---"></a>Supporto macOS per le app Web <!-- 3174427 -->
Le app Web, che consentono di aggiungere un collegamento a un URL sul Web, possono essere installate nel Dock usando il portale aziendale macOS. Gli utenti finali possono accedere all'azione **Installa** dalla pagina dei dettagli delle app Web nel Portale aziendale macOS. Per altre informazioni sul tipo di app **Collegamento Web**, vedere [Aggiungere app in Microsoft Intune](../apps/apps-add.md) e [Aggiungere app Web a Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps----3173501----"></a>Supporto macOS per app VPP <!-- 3173501  -->
Le app macOS, acquistate con Apple Business Manager, vengono visualizzate nella console quando vengono sincronizzati i token VPP Apple in Intune. È possibile assegnare, revocare e riassegnare le licenze basate su utenti e dispositivi per i gruppi usando la console di Intune. Microsoft Intune consente di gestire le app VPP acquistate per l'uso aziendale eseguendo le operazioni seguenti:

- Segnalazione delle informazioni di licenza dall'App Store.
- Verifica del numero di licenze usate.
- Blocco dell'installazione di un numero di copie dell'app superiore al numero di copie acquistate.

Per altre informazioni su Intune e VPP, vedere [Gestire le app e i libri acquistati con Volume Purchase Program con Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support----2871756----"></a>Supporto dell'iFrame di Google Play gestito <!-- 2871756  -->
Intune offre ora il supporto per l'aggiunta e la gestione di collegamenti Web direttamente nella console di Intune tramite l'iFrame di Google Play gestito.  In questo modo gli amministratori IT possono inviare un URL e una grafica di icona e quindi distribuire i collegamenti ai dispositivi come le normali app Android. Tutti gli scenari di gestione con Android Enterprise che usano Google Play gestito possono trarre vantaggio da questa funzionalità: dispositivi con profilo di lavoro, dedicati, completamente gestiti e non registrati. Da Intune, selezionare **App client** > **App** > **Aggiungi**. Selezionare quindi **Google Play gestito** dall'elenco **Tipo di app**. Per altre informazioni su Google Play gestito vedere [Aggiungere app di Google Play gestito a dispositivi Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices----4252734----"></a>Installare automaticamente app line-of-business Android in dispositivi Zebra <!-- 4252734  -->
Quando si installano app line-of-business Android in [dispositivi Zebra](../configuration/android-zebra-mx-overview.md) invece di richiedere di scaricare e installare l'app line-of-business, il sistema consente di installarle automaticamente. In Intune selezionare **App client** > **App** > **Aggiungi**. Nel riquadro **Aggiungi app** selezionare **App line-of-business**. Per altre informazioni vedere [Aggiungere un'app line-of-business Android a Microsoft Intune](../apps/lob-apps-android.md).

Attualmente, dopo il download dell'app line-of-business, viene visualizzata sul dispositivo dell'utente una notifica di **download completato**. La notifica può essere eliminata solo toccando **Deseleziona tutto** nella sfumatura della notifica. Questo problema di notifica verrà risolto in una versione successiva e l'installazione sarà completamente automatica, senza indicatori visivi.

#### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Operazioni di lettura e scrittura API Graph per app di Intune <!-- 5031704  -->
Le applicazioni possono chiamare le API Graph di Intune con operazioni di lettura e scrittura usando l'identità dell'app senza le credenziali utente. Per altre informazioni sull'accesso all'API Microsoft Graph per Intune, vedere [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) (Usare Intune in Microsoft Graph).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios----3586942----"></a>Condivisione e crittografia dei dati protetti per Intune App SDK per iOS <!-- 3586942  -->
Intune App SDK per iOS userà le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. Tutte le app dovranno avere un SDK versione 8.1.1 per consentire la condivisione protetta dei dati.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438-----"></a>Supporto per i profili VPN IKEv2 per iOS <!-- 1943438   -->
In questo aggiornamento è possibile creare profili VPN per il client VPN nativo di iOS tramite il protocollo IKEv2. IKEv2 è un nuovo tipo di connessione in **Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS**  per la piattaforma > **VPN** per il tipo di profilo > **Tipo di connessione**.

Questi profili VPN configurano il client VPN nativo, quindi nei dispositivi gestiti non viene installata alcuna app client VPN e non ne viene eseguito il push. Questa funzionalità richiede che i dispositivi siano registrati in Intune (registrazione MDM).

Per visualizzare le impostazioni VPN correnti che è possibile configurare, vedere [Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune](../configuration/vpn-settings-ios.md).

Si applica a:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161-----"></a>Le funzionalità e le restrizioni dei dispositivi e i profili di estensione per le impostazioni di iOS e macOS vengono visualizzate per tipo di registrazione <!-- 4886161   -->

In Intune è possibile creare profili per dispositivi iOS e macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Funzionalità del dispositivo**, **Limitazioni del dispositivo**, o **Estensioni** per il tipo di profilo). 

In questo aggiornamento le impostazioni disponibili nel portale di Intune sono classificate in base al tipo di registrazione a cui si applicano:

- iOS
  - Registrazione utenti
  - Registrazione del dispositivo
  - Registrazione automatica dei dispositivi (supervisione)
  - Tutti i tipi di registrazione

- macOS
  - Approvata da utente
  - Registrazione del dispositivo
  - Registrazione automatica dei dispositivi
  - Tutti i tipi di registrazione

Si applica a:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835-----"></a>Nuove impostazioni di controllo vocale per i dispositivi iOS con supervisione in esecuzione in modalità tutto schermo <!-- 4892835   -->
In Intune è possibile creare criteri per l'esecuzione di dispositivi iOS supervisionati in modalità tutto schermo o dispositivo dedicato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Modalità tutto schermo**). 

In questo aggiornamento sono disponibili nuove impostazioni che è possibile controllare:
- **Controllo vocale**: abilita il controllo vocale nel dispositivo in modalità tutto schermo.
- **Modifica del controllo vocale**: consente agli utenti di modificare l'impostazione del controllo vocale nel dispositivo in modalità tutto schermo.

Per visualizzare le impostazioni correnti, vedere le [impostazioni iOS in modalità tutto schermo](../configuration/device-restrictions-ios.md#kiosk).

Si applica a:
- iOS 13.0 e versioni successive

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175-----"></a>Usare Single Sign-On per app e siti Web nei dispositivi iOS e macOS <!-- 4893175   -->
In questo aggiornamento sono presenti nuove impostazioni Single Sign-On per dispositivi iOS e macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo).

Usare queste impostazioni per configurare Single Sign-On, in particolare per le app e i siti Web che usano l'autenticazione Kerberos. È possibile scegliere tra un'estensione dell'app Single Sign-On con credenziali generiche e un'estensione Kerberos predefinita di Apple.

Per visualizzare le funzionalità del dispositivo correnti che è possibile configurare, passare a [Funzionalità dei dispositivi iOS](../configuration/ios-device-features-settings.md) e [Funzionalità dei dispositivi macOS](../configuration/macos-device-features-settings.md).

Si applica a:
- iOS 13.0 e versioni successive
- macOS 10.15 e versioni successive

#### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079-----"></a>Associare i domini alle app nei dispositivi macOS 10.15 o versione successiva <!-- 4898079   -->
Nei dispositivi macOS è possibile configurare funzionalità diverse ed effettuare il push di queste funzionalità nei dispositivi usando criteri (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). In questo aggiornamento è possibile associare i domini alle app. Questa funzionalità consente di condividere le credenziali con i siti Web correlati all'app e può essere usata con l'estensione Single Sign-On di Apple, i collegamenti universali e il riempimento automatico delle password. 

Per visualizzare le funzionalità correnti che è possibile configurare passare alle [impostazioni delle funzionalità dei dispositivi macOS in Intune](../configuration/macos-device-features-settings.md).

Si applica a:
- macOS 10.15 e versioni successive

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474-----"></a>Usare "iTunes" e "apps" nell'URL dell'App Store di iTunes quando si visualizzano o nascondono le app nei dispositivi iOS con supervisione <!-- 4928474   --> 
In Intune è possibile creare criteri per visualizzare o nascondere le app nei dispositivi iOS supervisionati (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Mostra o nascondi le app**). 

È possibile immettere l'URL dell'App Store di iTunes, ad esempio `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. In questo aggiornamento è possibile usare sia `apps` che `itunes` nell'URL, ad esempio:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Per altre informazioni su queste impostazioni vedere [Visualizzare o nascondere le app](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Si applica a:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>I valori di tipo password dei criteri di conformità di Windows 10 sono più chiari e corrispondono a CSP<!-- 5138985 -->
Nei dispositivi Windows 10 è possibile creare criteri di conformità che richiedono funzionalità specifiche per le password (**Configurazione del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10 e versioni successive** per la piattaforma > **Sicurezza del sistema**). In questo aggiornamento:
- I valori **Tipo di password** sono più chiari e aggiornati in modo da corrispondere ai [criteri CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- L'impostazione **Scadenza password (giorni)**  è stata aggiornata per consentire i valori da 1 a 730 giorni. 

Per altre informazioni sulle impostazioni di conformità di Windows 10, vedere [Impostazioni di Windows 10 e versioni successive per contrassegnare un dispositivo come conforme o non conforme](../protect/compliance-policy-create-windows.md). 

Si applica a:
- Windows 10 e versioni successive

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access-------4092920---"></a>Interfaccia utente aggiornata per la configurazione dell'accesso locale a Microsoft Exchange    <!-- 4092920 -->  
È stata aggiornata la console in cui si [esegue la configurazione per l'accesso locale a Microsoft Exchange](../protect/conditional-access-exchange-create.md). Tutte le configurazioni per l'accesso locale a Exchange sono ora disponibili nello stesso riquadro della console in cui *viene abilitato il controllo dell'accesso locale a Exchange*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices----1109650----"></a>Consentire o limitare l'aggiunta di widget di app alla schermata iniziale nei dispositivi del profilo di lavoro Android Enterprise <!-- 1109650  --> 
Nei dispositivi Android Enterprise è possibile configurare le funzionalità nel profilo di lavoro (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo profilo di lavoro > Limitazioni del dispositivo** per il tipo di profilo). In questo aggiornamento è possibile consentire agli utenti di aggiungere widget esposti dalle app del profilo di lavoro alla schermata iniziale del dispositivo.

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:
- Profilo di lavoro di Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790-----"></a>Per impostazione predefinita i nuovi tenant non vengono gestiti dagli amministratori dei dispositivi Android <!-- 4869790   -->
Le funzionalità di amministratore dei dispositivi Android sono state sostituite da Android Enterprise. È quindi consigliabile usare Android Enterprise per le nuove registrazioni. In un aggiornamento futuro i nuovi tenant dovranno completare la procedura seguente come prerequisito per la registrazione in Android perché i dispositivi siano gestiti dagli amministratori: Accedere a **Intune** > **Registrazione dispositivi** > **Registrazione Android** > **Dispositivi personali e di proprietà aziendale con privilegi di amministratore di dispositivi** > **Usa l'amministratore di dispositivi per gestire i dispositivi**.

Gli ambienti dei tenant esistenti non subiranno alcuna modifica. 

Per altre informazioni sull'amministratore di dispositivi Android in Intune, vedere [Registrazione di tipo amministratore di dispositivi Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile----5012045-idmiss---"></a>Elenco di dispositivi DEP associati a un profilo <!-- 5012045 idmiss -->
È ora possibile visualizzare un elenco di pagine di dispositivi Apple Device Enrollment Program (DEP) associati a un profilo. È possibile eseguire ricerche nell'elenco da qualsiasi pagina. Per visualizzare l'elenco, passare a **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token > **Profili** > scegliere un profilo > **Dispositivi assegnati** (in **Monitoraggio**). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="more-android-fully-managed-support----3464667-4631425-4631440-5227935-4062195-----"></a>Supporto aumentato per dispositivi Android completamente gestiti <!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
È stato aggiunto il supporto seguente per i dispositivi Android completamente gestiti:

- I certificati SCEP per dispositivi Android completamente gestiti sono disponibili per l'autenticazione del certificato nei dispositivi gestiti come proprietario del dispositivo. I certificati SCEP sono già supportati nei dispositivi del profilo di lavoro.  Con i certificati SCEP per il proprietario del dispositivo, è possibile: <!-- 5227935 -->
    - creare il profilo SCEP nella sezione Proprietario dispositivo di Android Enterprise
    - collegare i certificati SCEP al profilo Wi-Fi Proprietario dispositivo per l'autenticazione
    - collegare i certificati SCEP ai profili VPN Proprietario dispositivo per l'autenticazione
    - collegare i certificati SCEP ai profili di posta elettronica Proprietario dispositivo per l'autenticazione (tramite AppConfig)
- Le app di sistema sono supportate nei dispositivi Android Enterprise. In Intune aggiungere un'app di sistema Android Enterprise selezionando **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** selezionare **App del sistema Android Enterprise**. Per altre informazioni, vedere [Aggiungere app di sistema Android Enterprise a Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- In **Conformità del dispositivo** > **Android Enterprise** > **Proprietario dispositivo** è possibile creare criteri di conformità che impostino il livello di attestazione Google SafetyNet.   <!-- 4631425 -->
- Nei dispositivi Android Enterprise completamente gestiti sono supportati i provider Mobile Threat Defense. In **Conformità del dispositivo** > **Android Enterprise** > **Proprietario dispositivo** è possibile scegliere un livello di minaccia accettabile. <!-- 4631440 --> [Impostazioni di Android Enterprise per contrassegnare un dispositivo come conforme o non conforme in Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) elenca le impostazioni attuali.
- Nei dispositivi Android Enterprise completamente gestiti l'app Microsoft Launcher può ora essere configurata tramite i criteri di configurazione delle app per consentire un'esperienza utente finale standardizzata nel dispositivo completamente gestito. L'app Microsoft Launcher può essere usata per personalizzare il dispositivo Android. Usando l'app insieme con un account Microsoft oppure con un account aziendale o dell'istituto di istruzione, è possibile accedere al calendario, ai documenti e alle attività recenti nel feed personalizzato. <!-- 5334044 -->

Con questo aggiornamento il supporto di Intune per i dispositivi Android Enterprise completamente gestiti è ora disponibile a livello generale.

Si applica a:

- Dispositivi completamente gestiti Android Enterprise

#### <a name="send-custom-notifications-to-a-single-device-----4928910---"></a>Inviare notifiche personalizzate a un singolo dispositivo  <!-- 4928910 -->
È ora possibile selezionare un singolo dispositivo e quindi usare un'azione del dispositivo remoto per [inviare una notifica personalizzata solo a quel dispositivo](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment----4950491---"></a>Non sono disponibili le azioni di cancellazione e reimpostazione passcode per i dispositivi iOS registrati tramite la registrazione utente <!-- 4950491 -->
La registrazione utente è un nuovo tipo di registrazione dei dispositivi Apple. Quando si registrano i dispositivi con la registrazione utente, le azioni remote di cancellazione e reimpostazione del passcode non sono disponibili per tali dispositivi.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices----4665317---"></a>Supporto di Intune per i dispositivi iOS 13 e macOS Catalina <!-- 4665317 -->
Intune ora supporta la gestione di dispositivi iOS 13 e macOS Catalina. Per altre informazioni vedere il [post del blog sul supporto di Microsoft Intune per iOS 13 e iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation-------3444125---"></a>Supporto di BitLocker per la rotazione delle password di ripristino basata su client   <!--  3444125 -->
Usare le impostazioni di Endpoint Protection di Intune per configurare la [rotazione delle password di ripristino basata su client](../protect/endpoint-protection-windows-10.md#windows-encryption) per BitLocker nei dispositivi che eseguono Windows versione 1909 o successiva.

Questa impostazione avvia l'aggiornamento delle password di ripristino basate su client dopo il ripristino di un'unità del sistema operativo, eseguito con bootmgr o WinRE, e lo sblocco delle password di ripristino in un'unità dati fissa. Questa impostazione consente di aggiornare la password di ripristino specifica che è stata usata mentre le altre password inutilizzate nel volume rimangono invariate. Per altre informazioni vedere la documentazione di BitLocker CSP per [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus-----4705448----------"></a>Protezione antimanomissione per Windows Defender Antivirus  <!-- 4705448        -->
Usare Intune per gestire la *protezione antimanomissione* per Windows Defender Antivirus. Quando si usano i profili di configurazione dei dispositivi per Windows 10 Endpoint Protection, è possibile trovare l'[impostazione per la protezione antimanomissione](../protect/endpoint-protection-windows-10.md#windows-defender-security-center) nel gruppo Microsoft Defender Security Center. È possibile impostare la protezione antimanomissione su *Attivata* per attivare le limitazioni per la protezione antimanomissione, impostare *Disabilitata* per disabilitarle o impostare *Non configurate* per lasciare la configurazione corrente dei dispositivi.  

Per altre informazioni sulla protezione antimanomissione [Bloccare le modifiche alle impostazioni di sicurezza con la protezione antimanomissione](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) nella documentazione di Windows. 

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available-----5317392---------"></a>Impostazioni avanzate per Windows Defender Firewall ora disponibili a livello generale <!--  5317392       -->  
Le [regole del firewall personalizzate per Windows Defender per Endpoint Protection](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), che è possibile configurare come parte di un profilo di configurazione del dispositivo, ora sono disponibili in anteprima pubblica e a livello generale.  È possibile usare tali regole per specificare il comportamento in entrata e in uscita di applicazioni, indirizzi di rete e porte. Queste regole sono state rilasciate a luglio come anteprima pubblica. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-now-support-terms-of-use-policies----2358863-idmiss---"></a>I tag di ambito ora supportano i criteri delle condizioni per l'utilizzo <!-- 2358863 idmiss -->
È ora possibile assegnare i [tag di ambito](scope-tags.md) ai criteri delle condizioni per l'utilizzo. A tale scopo, passare a **Intune** > **Registrazione del dispositivo** > **Termini e condizioni** > scegliere una voce nell'elenco > **Proprietà** > **Tag di ambito** > scegliere un tag di ambito.

## <a name="week-of-september-9-2019"></a>Settimana del 9 settembre 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="updates-to-microsoft-intune-app----4997846---"></a>Aggiornamenti all'app Microsoft Intune <!-- 4997846 -->
L'app Microsoft Intune per Android è stata aggiornata con i miglioramenti seguenti:
- Il layout è stato aggiornato e migliorato per includere lo spostamento inferiore per le azioni più importanti.
- È stata aggiunta un'altra pagina per il profilo dell'utente.
- È stata aggiunta la visualizzazione delle notifiche interattive nell'app per l'utente, ad esempio la necessità di aggiornare le impostazioni del dispositivo.
- È stata aggiunta la visualizzazione di notifiche push personalizzate, allineando l'app al supporto aggiunto di recente nell'app Portale aziendale per iOS e Android. Per altre informazioni, vedere [Inviare notifiche personalizzate in Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993---"></a>Per i dispositivi iOS, personalizzare la schermata relativa alla privacy del processo di registrazione del portale aziendale <!-- 4394993 -->
Usando Markdown è possibile personalizzare la schermata relativa alla privacy del portale aziendale visualizzata dagli utenti finali durante la registrazione iOS. In particolare, è possibile personalizzare l'elenco di elementi che l'organizzazione non può visualizzare o eseguire sul dispositivo. Per altre informazioni, vedere [Come configurare l'app Portale aziendale Intune](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Settimana del 2 settembre 2019

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-user-interface-update--tenant-status-dashboard-----5273210----"></a>Aggiornamento dell'interfaccia utente di Intune: dashboard Stato del tenant  <!-- 5273210  -->
È stata aggiornata l'interfaccia utente per il dashboard Stato del tenant per allinearsi agli stili dell'interfaccia utente di Azure. Per altre informazioni, vedere [Stato tenant](../tenant-status.md).


## <a name="week-of-august-26-2019"></a>Settimana del 26 agosto 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer----5228061---"></a>Configurare le impostazioni di Microsoft Edge usando i modelli amministrativi per Windows 10 e versioni successive <!-- 5228061 -->

Nei dispositivi Windows 10 e versioni successive è possibile creare modelli amministrativi per configurare le impostazioni di Criteri di gruppo in Intune. In questo aggiornamento è possibile configurare le impostazioni che si applicano a Microsoft Edge versione 77 e successive.

Per altre informazioni sui modelli amministrativi, vedere [Usare i modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune](../configuration/administrative-templates-windows.md).

Si applica a:

- Windows 10 e versioni successive (Windows RS4+)

## <a name="week-of-august-12-2019"></a>Settimana del 12 agosto 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>Controllare il comportamento di disinstallazione delle app iOS durante l'annullamento della registrazione del dispositivo <!-- 3504144   -->
Gli amministratori possono gestire la rimozione o il mantenimento di un'app in un dispositivo quando viene annullata la registrazione del dispositivo a livello di utente o di gruppo di dispositivi. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Categorizzare le app di Microsoft Store per le aziende <!-- 3926922 -->
È possibile categorizzare le app di Microsoft Store per le aziende. A tale scopo, scegliere **app** > c**lient** diIntune >  **app**>selezionareun'appMicrosoftStoreforbusinessapp> **Categoria** > **informazioni**. Nel menu a discesa assegnare una categoria.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Notifiche personalizzate per gli utenti dell'app Microsoft Intune <!-- 4843354  -->
L'app Microsoft Intune per Android supporta ora la visualizzazione di notifiche push personalizzate, in linea con il supporto aggiunto di recente nelle app Portale aziendale per iOS e Android. Per altre informazioni, vedere [Inviare notifiche personalizzate in Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>Nuove funzionalità per dispositivi Android Enterprise dedicati in modalità per più app <!-- 3755304 3041943 3041946   -->

In Intune è possibile controllare le funzionalità e le impostazioni in un'esperienza di tipo chiosco multimediale per i dispositivi dedicati Android Enterprise (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo).

In questo aggiornamento sono state aggiunte le funzionalità seguenti:

- **Dispositivi dedicati** > **Più app**: è possibile visualizzare il **pulsante Pagina iniziale virtuale** scorrendo verso l'alto nel dispositivo oppure rendendolo mobile sullo schermo in modo che gli utenti possano spostarlo.
- **Dispositivi dedicati** > **Più app**: **Accesso a Flashlight** consente agli utenti di usare la torcia. 
- **Dispositivi dedicati** > **Più app**: **Controllo volume dei file multimediali** consente agli utenti di controllare il volume dei file multimediali del dispositivo usando un dispositivo di scorrimento. 
- **Dispositivi dedicati** > **Più app**:  **Abilitare uno screen saver**, caricare un'immagine personalizzata e controllare quando viene visualizzato lo screen saver.

Per visualizzare le impostazioni correnti, passare alle [impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Si applica a:

- Dispositivi dedicati Android Enterprise

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Nuovi profili di app e configurazione per i dispositivi Android Enterprise completamente gestiti <!-- 3574215 3574238 3574235 3574232   -->
Usando i profili è possibile configurare le impostazioni che applicano le impostazioni per VPN, posta elettronica e Wi-Fi ai dispositivi (completamenti gestiti) del proprietario del dispositivo Android Enterprise. In questo aggiornamento è possibile:

- Usare i [criteri di configurazione delle app](../apps/app-configuration-policies-use-android.md) per distribuire le impostazioni di posta elettronica di Outlook, Gmail e Nine Work.
- Usare i profili di configurazione dei dispositivi per distribuire le [impostazioni dei certificati radice trusted](../protect/certificates-configure.md).
- Usare i profili di configurazione dei dispositivi per distribuire le impostazioni [VPN](../configuration/vpn-settings-android-enterprise.md) e [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Con questa funzionalità gli utenti eseguono l'autenticazione con il nome utente e la password per i profili VPN, Wi-Fi e di posta elettronica. Attualmente, l'autenticazione basata sui certificati non è disponibile.

Si applica a:  
- Proprietario del dispositivo Android Enterprise (completamente gestito)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>Controllare le app, i file, i documenti e le cartelle che si aprono quando gli utenti accedono ai dispositivi macOS <!--3914202   -->
È possibile abilitare e configurare le funzionalità per i dispositivi macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). 

In questo aggiornamento è disponibile una nuova impostazione Elementi di accesso per controllare quali app, file, documenti e cartelle si aprono quando un utente accede al dispositivo registrato. 

Per visualizzare le impostazioni correnti, passare alle [impostazioni delle funzionalità dei dispositivi macOS in Intune](../configuration/macos-device-features-settings.md).

Si applica a:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>Le scadenze sostituiscono le impostazioni di riavvio in caso di occupato per gli anelli di Windows Update   <!-- 4464404        -->
Per allinearsi alle recenti [modifiche per la manutenzione di Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing), gli anelli di Windows 10 Update di Intune [supportano ora impostazioni per le scadenze](../protect/windows-update-settings.md). Le *scadenze* determinano quando un dispositivo installa gli aggiornamenti della funzionalità e della sicurezza.  Nei dispositivi che eseguono Windows 10 1903 o versioni successive, le *scadenze* sostituiscono le configurazioni per il *riavvio in caso di occupato*.  In futuro, le *scadenze* sostituiranno il *riavvio in caso di occupato* anche nelle versioni precedenti di Windows 10.  

Quando non si configurano le *scadenze*, i dispositivi continuano a usare le impostazioni di *riavvio in caso di occupato*. Tuttavia, [in Intune il supporto per le impostazioni di riavvio in caso di occupato saranno deprecate](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) in un aggiornamento futuro.  

Pianificare l'uso delle *scadenze* per tutti i dispositivi Windows 10. Dopo aver applicato le impostazioni per le *scadenze*, è possibile modificare le configurazioni di Intune per il *riavvio in caso di occupato* su Non configurato. Con l'impostazione Non configurato Intune interrompe la gestione di tali impostazioni nei dispositivi, ma non rimuove le ultime configurazioni per l'impostazione dal dispositivo. Pertanto, le ultime configurazioni impostate per il *riavvio in caso di occupato* rimangono attive e in uso nei dispositivi fino a quando tali impostazioni non vengono modificate da un metodo diverso da Intune. In seguito, in caso di modifiche alla versione di Windows dei dispositivi o quando il supporto delle *scadenze* di Intune verrà esteso alla versione di Windows dei dispositivi, il dispositivo inizierà a usare le nuove impostazioni che sono già presenti.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>Supporto per più connettori di certificati di Microsoft Intune   <!--   4704642      -->
Intune supporta ora l'installazione e l'uso di più [connettori di certificati di Microsoft Intune per le operazioni PKCS](../protect/certficates-pfx-configure.md). Questa modifica supporta il bilanciamento del carico e la disponibilità elevata del connettore. Ogni istanza del connettore può elaborare le richieste di certificati da Intune.  Se un connettore non è disponibile, gli altri connettori continuano a elaborare le richieste. 

Per usare più connettori, non è necessario eseguire l'aggiornamento alla versione più recente del software del connettore.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>Nuove impostazioni e modifiche alle impostazioni esistenti per limitare le funzionalità nei dispositivi iOS e macOS <!-- 4867699 4867709   -->
È possibile creare profili per limitare le impostazioni nei dispositivi che eseguono iOS e macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Limitazioni del dispositivo**). Questo aggiornamento include le funzionalità seguenti:

- In **macOS** > **Limitazioni del dispositivo** > **Cloud e risorse di archiviazione** usare la nuova impostazione **Handoff** per impedire agli utenti di iniziare a lavorare su un dispositivo macOS e continuare a usare un altro dispositivo macOS o iOS.

  Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-macos.md).

- In **iOS** > **Limitazioni del dispositivo** sono presenti alcune modifiche:

  - **App predefinite** > **Trova il mio iPhone (solo con supervisione)** : nuova impostazione che blocca questa funzionalità nella funzionalità dell'app Trova il mio. 
  - **App predefinite** > **Trova amici (solo con supervisione)** : nuova impostazione che blocca questa funzionalità nella funzionalità dell'app Trova il mio. 
  - **Wireless** > **Modifica dello stato del Wi-Fi (solo con supervisione)** : nuova impostazione che impedisce agli utenti di attivare o disattivare il Wi-Fi nel dispositivo.
  - **Tastiera e dizionario** > **QuickPath (solo con supervisione)** : nuova impostazione che blocca la funzionalità QuickPath.
  - **Cloud e risorse di archiviazione**: l'impostazione **Continuazione dell'attività** è stata rinominata **Handoff**.

  Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:  
- macOS 10.15 e versioni successive
- iOS 13 e versioni successive

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>Alcune limitazioni per i dispositivi iOS senza supervisione diventeranno solo con supervisione con la versione iOS 13.0 <!-- 4867809   -->
In questo aggiornamento, alcune impostazioni si applicano ai dispositivi solo con supervisione con la versione iOS 13.0. Se queste impostazioni vengono configurate e assegnate a dispositivi senza supervisione prima della versione iOS 13.0, le impostazioni vengono comunque applicate a tali dispositivi senza supervisione. Sono comunque valide anche dopo l'aggiornamento dei dispositivi a iOS 13.0. Queste limitazioni vengono rimosse nei dispositivi senza supervisione di cui viene eseguito il backup e il ripristino. 

Queste impostazioni includono:

- App Store, visualizzazione documenti, giochi
  - App Store
  - Musica di iTunes, podcast o notizie con contenuti espliciti
  - Aggiunta di amici al Game Center
  - Gioco multiplayer
- App predefinite
  - Fotocamera
    - FaceTime
  - Safari
    - Riempimento automatico
- Cloud e risorse di archiviazione
  - Backup in iCloud
  - Blocca la sincronizzazione dei documenti di iCloud
  - Blocca la sincronizzazione Keychain con iCloud

Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:  
- iOS 13.0 e versioni successive

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>Stato del dispositivo migliorato per la crittografia macOS FileVault  <!-- 4944983         -->
Sono stati aggiornati diversi [messaggi di stato del dispositivo](../protect/encryption-monitor.md#device-encryption-status) per la crittografia FileVault nei dispositivi macOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>Alcune impostazioni di analisi di Windows Defender Antivirus nei report mostrano uno stato di errore <!-- 5119229 -->
In Intune è possibile creare criteri per usare Windows Defender Antivirus per analizzare i dispositivi Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Windows Defender Antivirus**). Le impostazioni di report **Ora di esecuzione di un'analisi veloce giornaliera** e **Tipo di analisi di sistema da eseguire** mostrano uno stato di errore, quando si tratta effettivamente di uno stato di operazione riuscita. 

Questo comportamento è stato corretto in questo aggiornamento. Le impostazioni di report **Ora di esecuzione di un'analisi veloce giornaliera** e **Tipo di analisi di sistema da eseguire** mostrano quindi uno stato di operazione riuscita quando le analisi vengono completate correttamente e uno stato di errore quando non è possibile applicare le impostazioni. 

Per altre informazioni sulle impostazioni di Windows Defender Antivirus, vedere [Impostazioni dei dispositivi Windows 10 (e versioni successive) per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus). 

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="default-scope-tags----3702875----"></a>Tag di ambito predefinito <!-- 3702875  -->
È ora disponibile un nuovo tag di ambito predefinito incorporato. A tutti gli oggetti di Intune senza tag che supportano i tag di ambito viene assegnato automaticamente il tag di ambito predefinito. Il tag di ambito **Predefinito** viene aggiunto a tutte le assegnazioni di ruolo esistenti per mantenere la parità con l'esperienza di amministrazione attuale. Se non si vuole che un amministratore visualizzi gli oggetti di Intune con il tag di ambito predefinito, rimuovere il tag di ambito predefinito dall'assegnazione di ruolo. Questa funzionalità è simile alla funzionalità degli ambiti di sicurezza in System Center Configuration Manager. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Supporto per l'amministratore del dispositivo per la registrazione Android <!-- 4869749   -->
È stata aggiunta l'opzione per la registrazione dell'amministratore di dispositivi Android alla pagina di registrazione Android (**Intune** > **Registrazione del dispositivo** > **Registrazione Android**). L'amministratore del dispositivo Android sarà ancora abilitato per impostazione predefinita per tutti i tenant.  Per altre informazioni, vedere [Registrazione di tipo amministratore di dispositivi Android](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Ignorare altre schermate in Assistente configurazione <!--4877451  -->
È possibile impostare i profili DEP (Device Enrollment Program) in modo da ignorare le schermate di Assistente configurazione seguenti:
- Per iOS
    - Aspetto
    - Express Language (Lingua rapida)
    - Lingua preferita
    - Device to Device Migration (Migrazione da dispositivo a dispositivo)
- Per macOS
    - Orario schermo
    - Touch ID Setup (Configurazione ID tocco)

Per altre informazioni sulla personalizzazione di Assistente configurazione, vedere [Creare un profilo di registrazione di Apple per iOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) e [Creare un profilo di registrazione di Apple per macOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Aggiungere una colonna utente al processo di caricamento CSV del dispositivo Autopilot <!-- 3823054 -->
È ora possibile aggiungere una colonna utente al caricamento CSV per i dispositivi Autopilot. Ciò consente di assegnare in blocco gli utenti al momento dell'importazione del file CSV. Per altre informazioni, vedere [Registrare dispositivi Windows in Intune con Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni <!--4231059  -->
È possibile impostare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni, anziché il limite precedente di 90 giorni, dall'ultimo accesso. A tale scopo, passare a **Intune** > **Dispositivi** > **Configurazione** > **Regole per la pulizia del dispositivo**.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Numero di build incluso nella pagina Hardware del dispositivo Android <!-- 4461910   -->
Una nuova voce nella pagina Hardware per ogni dispositivo Android include il numero di build del sistema operativo del dispositivo. Per altre informazioni, vedere [Visualizzare i dettagli del dispositivo in Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Settimana del 5 agosto 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Zebra Technologies è un OEM supportato per OEMConfig nei dispositivi Android Enterprise  <!-- 4843713 -->

In Intune è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android Enterprise usando OEMConfig (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **OEMConfig** per il tipo di profilo).

In questo aggiornamento, Zebra Technologies è un OEM (Original Equipment Manufacturer) supportato per OEMConfig. Per altre informazioni su OEMConfig, vedere [Usare e gestire i dispositivi Android Enterprise con OEMConfig](../configuration/android-oem-configuration-overview.md).

Si applica a:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Settimana del 22 luglio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>Notifiche personalizzate per utenti e gruppi    <!-- 16766574          -->
È possibile inviare notifiche push personalizzate dall'applicazione Portale aziendale agli utenti di dispositivi iOS e Android gestiti con Intune. Queste notifiche push per dispositivi mobili sono personalizzabili con testo libero e possono essere usate per qualsiasi scopo. È possibile destinarle a diversi gruppi di utenti dell'organizzazione. Per altre informazioni, vedere l'argomento sulle [notifiche personalizzate](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app----3041950----"></a>App controller delle norme relative ai dispositivi di Google <!-- 3041950  -->
L'app di schermata iniziale gestita ora consente l'accesso a Google Apps Device Policy per Android. L'app di schermata iniziale gestita è un'utilità di avvio personalizzata usata per i dispositivi registrati in Intune come dispositivi dedicati Android Enterprise (AE) che usano la modalità tutto schermo per più app. È possibile accedere all'app Android Device Policy o guidare gli utenti all'app Android Device Policy per fini di supporto e debug. Questa funzionalità di avvio è disponibile nel momento in cui il dispositivo viene registrato e bloccato nella schermata iniziale gestita. Per usare questa funzionalità non è necessaria alcuna installazione aggiuntiva.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>Impostazioni di protezione di Outlook per dispositivi iOS e Android <!-- 3212619 -->
È ora possibile configurare le impostazioni generali di configurazione dei dati e delle app per Outlook per iOS e Android usando i semplici controlli di amministrazione di Intune senza registrazione del dispositivo. Le impostazioni generali di configurazione delle app forniscono la parità con le impostazioni che gli amministratori possono abilitare in caso di gestione di Outlook per iOS e Android su dispositivi registrati. Per altre informazioni sulle impostazioni di Outlook, vedere [Deploying Outlook for iOS and Android app configuration settings](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) (Distribuzione di impostazioni di configurazione per Outlook per iOS e Android).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Usare le "regole di applicabilità" durante la creazione dei profili di configurazione dispositivo Windows 10 <!-- 2549910 eeready   idstaged -->

È possibile creare profili di configurazione dispositivo Windows 10 (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **Windows 10** per la piattaforma > **Regole di applicabilità**). In questo aggiornamento è possibile creare una **regola di applicabilità** in modo che il profilo si applichi solo a un'edizione o versione specifica. Creare ad esempio un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applichi solo ai dispositivi che eseguono Windows 10 Enterprise.

Per aggiungere una regola di applicabilità, vedere l'[apposito argomento](../configuration/device-profile-create.md#applicability-rules).

Si applica a: Windows 10 e versioni successive

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>Usare i token per aggiungere informazioni specifiche del dispositivo nei profili personalizzati per i dispositivi iOS e macOS <!-- 3330008  -->
È possibile usare profili personalizzati nei dispositivi iOS e macOS per configurare le impostazioni e le funzionalità non predefinite in Intune (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Personalizza** per il tipo di profilo). In questo aggiornamento è possibile aggiungere token ai file `.mobileconfig` per aggiungere informazioni specifiche del dispositivo. È ad esempio possibile aggiungere `Serial Number: {{serialnumber}}` al file di configurazione per mostrare il numero di serie del dispositivo.

Per creare un profilo personalizzato, vedere l'argomento relativo alle [impostazioni personalizzate per iOS ](../configuration/custom-settings-ios.md) o alle [impostazioni personalizzate per macOS](../configuration/custom-settings-macos.md).

Si applica a:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Nuova finestra di progettazione della configurazione quando si crea un profilo OEMConfig per Android Enterprise <!-- 3712769   -->
In Intune è possibile creare un profilo di configurazione dispositivo che usa un'app OEMConfig (Configurazione dispositivo > Profili > Crea profilo > Android Enterprise per la piattaforma > OEMConfig per il tipo di profilo). In tal caso, viene aperto un editor JSON con un modello e valori che è possibile modificare. 

Questo aggiornamento include una finestra di progettazione della configurazione con un'esperienza utente migliorata che mostra i dettagli incorporati nell'app, inclusi i titoli, le descrizioni e altro ancora. L'editor JSON è ancora disponibile e mostra tutte le modifiche apportate nella finestra di progettazione della configurazione.

Per visualizzare le impostazioni correnti, passare a [Use and manage Android Enterprise devices with OEMConfig](../configuration/android-oem-configuration-overview.md) (Usare e gestire dispositivi Android Enterprise con OEMConfig).

Si applica a: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Aggiornamento dell'interfaccia utente per la configurazione di Windows Hello  <!-- 4089576            -->
È stata aggiornata la console in cui si [configura Intune per l'uso di Windows Hello for Business](../protect/windows-hello.md). Tutte le impostazioni di configurazione sono ora disponibili nello stesso riquadro della console in cui si abilita il supporto per Windows Hello. 


#### <a name="intune-powershell-sdk----4924113---"></a>Intune PowerShell SDK <!-- 4924113 --> 
Intune PowerShell SDK, che fornisce il supporto per l'API di Intune tramite Microsoft Graph, è stato aggiornato alla versione 6.1907.1.0. L'SDK supporta ora quanto segue:
- Automazione di Azure.
- Operazioni di lettura autenticazioni per sole app. 
- Nomi descrittivi abbreviati come alias.
- Convenzioni di denominazione di PowerShell. In particolare, il parametro `PSCredential` (nel cmdlet `Connect-MSGraph`) è stato rinominato in `Credential`.
- La specifica manuale del valore dell'intestazione `Content-Type` quando si usa il cmdlet `Invoke-MSGraphRequest`.

Per altre informazioni, vedere la pagina relativa a [PowerShell SDK per l'API Graph per Microsoft Intune](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>Aggiornamenti per le restrizioni della registrazione  <!-- 2871968 -->
Le restrizioni della registrazione per i nuovi tenant sono state aggiornate in modo che i profili di lavoro di Android Enterprise siano consentiti per impostazione predefinita. I tenant esistenti non subiscono alcuna modifica. Per usare i profili di lavoro di Android Enterprise, è comunque necessario [connettere l'account Intune all'account Google Play gestito](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Aggiornamenti dell'interfaccia utente per la registrazione Apple e le restrizioni della registrazione <!--4089575, 4089579  -->
Entrambi i processi seguenti usano un'interfaccia utente in stile procedura guidata:
- Registrazione di dispositivi Apple. Per altre informazioni, vedere [Registrare automaticamente i dispositivi iOS nel programma Device Enrollment Program di Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Creazione di restrizioni della registrazione. Per altre informazioni, vedere [Impostare le restrizioni di registrazione](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Gestione della preconfigurazione degli identificatori dei dispositivi aziendali per i dispositivi Android Q <!-- 4711509  idmiss -->
In Android Q (versione 10) Google eliminerà la possibilità per gli agenti MDM nei dispositivi Android gestiti legacy (amministratore del dispositivo) di raccogliere informazioni sugli identificatori dei dispositivi.  Intune dispone di una funzionalità che consente agli amministratori IT di [preconfigurare un elenco di numeri di serie del dispositivo o IMEI](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) per contrassegnare automaticamente tali dispositivi come di proprietà dell'azienda. Questa funzionalità non è supportata sui dispositivi Android Q gestiti dall'amministratore del dispositivo.  Indipendentemente dal fatto che venga caricato il numero di serie o IMEI per il dispositivo, la proprietà sarà sempre considerata come personale durante la registrazione di Intune.  È possibile impostare manualmente la proprietà come aziendale dopo la registrazione.  Ciò ha impatto solo sulle nuove registrazioni, non sui dispositivi registrati esistenti.  Tale modifica non ha impatto sui dispositivi Android gestiti con profili di lavoro, che continueranno a funzionare come di consueto.  I dispositivi Android Q registrati come amministratore del dispositivo non saranno inoltre più in grado di segnalare il numero di serie o IMEI nella console di Intune come proprietà del dispositivo.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Sono state modificate le icone per le registrazioni di Android Enterprise (profilo di lavoro, dispositivi dedicati e dispositivi completamente gestiti) <!-- 4977730 -->
Le icone per i profili di registrazione di Android Enterprise sono state modificate. Per visualizzare le nuove icone, andare a **Intune** > **Registrazione** > **Registrazione Android** > vedere in **Profili di registrazione**.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Modifica alla raccolta dei dati di diagnostica di Windows <!-- 4113859 -->
Il valore predefinito per la raccolta dei dati di diagnostica è stato modificato per i dispositivi che eseguono Windows 10, versione 1903 e successive. A partire da Windows 10, versione 1903, la raccolta dei dati di diagnostica è abilitata per impostazione predefinita. I dati di diagnostica di Windows sono dati tecnici essenziali dei dispositivi Windows relativi al dispositivo e alle prestazioni di Windows e del software correlato. Per altre informazioni, vedere [Configure Windows diagnostic data in your organization](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization) (Configurare i dati di diagnostica di Windows nell'organizzazione). Nei dispositivi Autopilot viene inoltre dato il consenso esplicito per la raccolta dei dati di telemetria "Full", a meno che non vengano impostati diversamente nel profilo di Autopilot con [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="improve-device-location---3855417----"></a>Migliorare l'individuazione del dispositivo<!-- 3855417  -->
È possibile fare lo zoom avanti sulle coordinate esatte di un dispositivo usando l'azione **Individua il dispositivo**. Per altre informazioni sull'individuazione dei dispositivi iOS persi, vedere [Individuare dispositivi iOS persi](../remote-actions/device-locate.md).


### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Impostazioni avanzate per Windows Defender Firewall (anteprima pubblica)  <!--  1311949     -->  
È possibile usare Intune per gestire [regole del firewall personalizzate come parte di un profilo di configurazione del dispositivo](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) per Endpoint Protection in Windows 10. Le regole possono specificare il comportamento in entrata e in uscita di applicazioni, indirizzi di rete e porte. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>Aggiornamento dell'interfaccia utente per la gestione delle baseline di sicurezza   <!-- 4091125     -->
È stata aggiornata l'[esperienza di creazione e modifica](../protect/security-baselines.md#create-the-profile) nella console di Intune per le baseline di sicurezza. Le modifiche includono:

Un formato più semplice in stile procedura guidata che è stato ridotto in un singolo pannello. all'interno di un pannello. Questo nuovo design non implica lo spostamento tra pannelli che richiede ai professionisti IT di eseguire il drill-down in diversi riquadri distinti.  
È ora possibile creare assegnazioni come parte dell'esperienza di creazione e modifica, anziché dover tornare in seguito per assegnare baseline. È stato aggiunto un riepilogo delle impostazioni che è possibile visualizzare prima di creare una nuova baseline e quando se ne modifica una esistente. Al momento della modifica, il riepilogo mostra solo l'elenco di elementi impostati all'interno di una categoria di proprietà da modificare.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Settimana del 15 luglio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Icone dell'app di schermata iniziale gestita e impostazioni gestite <!-- 4918107 -->
L'icona dell'app di schermata iniziale gestita e l'icona di **impostazioni gestite** sono state aggiornate. L'app di schermata iniziale gestita è usata solo per i dispositivi registrati in Intune come dispositivi dedicati Android Enterprise (AE) eseguiti in modalità tutto schermo per più app. Per altre informazioni sull'app di schermata iniziale gestita, vedere [Configurare l'app Microsoft Managed Home Screen per Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Android Device Policy su dispositivi dedicati Android Enterprise <!-- 4918136 -->
È possibile accedere all'app Android Device Policy dalla schermata di debug dell'app di schermata iniziale gestita. L'app di schermata iniziale gestita è usata solo per i dispositivi registrati in Intune come dispositivi dedicati Android Enterprise (AE) eseguiti in modalità tutto schermo per più app. Per altre informazioni, vedere [Configurare l'app Microsoft Managed Home Screen per Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates----3902931---"></a>Aggiornamenti del Portale aziendale iOS <!-- 3902931 -->
Il nome della società nelle richieste di gestione delle app iOS sostituirà il testo "i.manage.microsoft.com" corrente. Gli utenti visualizzeranno ad esempio il nome della società anziché "i.manage.microsoft.com" quando tentano di installare un'app iOS da Portale aziendale o quando consentono la gestione dell'app. Questa funzionalità verrà implementata per tutti i clienti nei prossimi giorni.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>Gestire FileVault per macOS   <!--  3858502 + 4557986 + 1210104  -->
È possibile usare Intune per [gestire la crittografia delle chiavi FileVault](../protect/encrypt-devices.md) per i dispositivi macOS. Per crittografare i dispositivi, usare un profilo di configurazione dei dispositivi di Endpoint Protection.

Il supporto per FileVault include la crittografia dei dispositivi non crittografati, il deposito di una chiave di ripristino personale dei dispositivi, la rotazione automatica o manuale delle chiavi di crittografia personali e il recupero delle chiavi per i dispositivi aziendali. Gli utenti finali possono anche usare il sito Web Portale aziendale per ottenere la chiave di ripristino personale per i dispositivi crittografati. 

È stato inoltre espanso il report di crittografia per includere [informazioni su FileVault](../protect/encryption-monitor.md) e informazioni su BitLocker, in modo da poter visualizzare tutti i dettagli della crittografia dei dispositivi in un'unica posizione. 

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>La reimpostazione di Windows Autopilot rimuove l'utente primario del dispositivo <!-- 4156123 -->
Quando si usa la reimpostazione di Autopilot in un dispositivo, l'utente primario del dispositivo viene rimosso. L'utente successivo che accede dopo la reimpostazione verrà impostato come utente primario. Questa funzionalità verrà implementata per tutti i clienti nei prossimi giorni.

## <a name="week-of-july-8-2019"></a>Settimana dell'8 luglio 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nuove impostazioni di Office, Windows e OneDrive nei modelli amministrativi di Windows 10 <!-- 3510695 -->

È possibile creare modelli amministrativi in Intune che simulano la gestione di Criteri di gruppo locali (**Gestione dispositivi** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Modello amministrativo** per il tipo di profilo).

Questo aggiornamento include altre impostazioni di Office, Windows e OneDrive che è possibile aggiungere ai modelli. Con queste nuove impostazioni è ora possibile configurare oltre 2500 impostazioni completamente basate sul cloud.

Per altre informazioni su questa funzionalità, vedere [Usare i modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune](../configuration/administrative-templates-windows.md).

Si applica a: Windows 10 e versioni successive

## <a name="week-of-july-1-2019"></a>Settimana dell'1 luglio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>AAD e APP in dispositivi Android Enterprise <!-- 3574267 -->
Quando si esegue l'onboarding di dispositivi Android Enterprise completamente gestiti, gli utenti si registrano ora con Azure Active Directory (AAD) al momento della configurazione iniziale del dispositivo nuovo o con ripristino delle impostazioni predefinite. In precedenza, per un dispositivo completamente gestito, al termine dell'installazione l'utente doveva avviare manualmente l'app Microsoft Intune per iniziare la registrazione di AAD. Attualmente, quando l'utente accede alla pagina iniziale del dispositivo dopo la configurazione iniziale, il dispositivo risulta iscritto e registrato.

Oltre agli aggiornamenti di AAD, nei dispositivi Android Enterprise completamente gestiti sono ora supportati anche i criteri di Protezione app di Intune. Questa funzionalità diventerà disponibile al momento della relativa implementazione. Per altre informazioni, vedere [Aggiungere app di Google Play gestite a dispositivi Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Settimana del 24 giugno 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configurare il browser collegabile ai dati dell'organizzazione <!-- 3145939 -->
I criteri di Protezione app di Intune nei dispositivi Android e iOS consentono ora di trasferire i collegamenti Web dell'organizzazione in un browser specifico diverso da Intune Managed Browser o Microsoft Edge.  Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>La pagina Tutte le app identifica le app di Microsoft Store per le aziende online/offline<!--4089647 -->
La pagina **Tutte le app** include ora l'assegnazione di etichette per identificare le app di Microsoft Store per le aziende come app online o offline. Ogni app di Microsoft Store per le aziende include ora un suffisso **Online** o **Offline**. La pagina dei dettagli dell'app include anche informazioni relative a **tipo di licenza** e **supporto dell'installazione per contesto di dispositivo** (solo app con licenza offline).

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>App Portale aziendale nei dispositivi condivisi Windows <!--4393553 -->
Gli utenti possono ora accedere all'app Portale aziendale nei dispositivi condivisi Windows. Gli utenti finali visualizzeranno un'etichetta **Condiviso** nel riquadro del dispositivo. Questa funzionalità si applica all'app Portale aziendale di Windows, versione 10.3.45609.0 e successive.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Visualizzare tutte le app installate dalla nuova pagina Web del portale aziendale <!-- 4224326 -->
Nella nuova pagina **App installate** del sito Web del portale aziendale sono elencate tutte le app gestite, sia obbligatorie che disponibili, installate nei dispositivi di un utente. Oltre al tipo di assegnazione, gli utenti possono visualizzare l'editore, la data di pubblicazione o lo stato di installazione corrente dell'app. Se non sono state impostate app obbligatorie o disponibili per gli utenti, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Per visualizzare la nuova pagina sul Web, passare al [sito Web del portale aziendale](https://portal.manage.microsoft.com) e fare clic su **App installate**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>Una nuova visualizzazione consente agli utenti di vedere tutte le app gestite installate nel dispositivo <!-- 2352913 -->  
L'app Portale aziendale per Windows elenca ora tutte le app gestite, sia obbligatorie che disponibili, installate nel dispositivo dell'utente. Gli utenti possono anche visualizzare le installazioni di app tentate e in sospeso e i rispettivi stati correnti. Se non sono state impostate app obbligatorie o disponibili per gli utenti, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Per accedere alla nuova visualizzazione, passare al riquadro di spostamento dell'app Portale aziendale e selezionare **App** > **App installate**.    

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurare le impostazioni per le estensioni del kernel nei dispositivi macOS <!-- 2043024 -->
Nei dispositivi macOS è possibile creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **macOS** per la piattaforma). Questo aggiornamento include un nuovo gruppo di impostazioni che consentono di configurare e usare le estensioni del kernel nei dispositivi. È possibile aggiungere estensioni specifiche o consentire l'uso di tutte le estensioni di un partner o uno sviluppatore specifico.

Per altre informazioni su questa funzionalità, vedere gli argomenti relativi alla [panoramica delle estensioni del kernel](../configuration/kernel-extensions-overview-macos.md) e alle [impostazioni delle estensioni del kernel](../configuration/kernel-extensions-settings-macos.md).

Si applica a: macOS 10.13.2 e versioni successive

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>L'impostazione app solo dallo store per i dispositivi Windows 10 include altre opzioni di configurazione <!-- 2697002 -->
Quando si crea un profilo di limitazione del dispositivo per i dispositivi Windows è possibile usare l'impostazione **Apps from the store only** (App solo dallo store) in modo che gli utenti installino app solo dall'archivio applicazioni di Windows (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). In questo aggiornamento questa impostazione viene estesa per supportare altre opzioni. 

Per visualizzare la nuova impostazione, andare a [Impostazioni dei dispositivi Windows 10 (e versioni successive) per consentire o limitare l'uso delle funzionalità](../configuration/device-restrictions-windows-10.md#app-store).

Si applica a: Windows 10 e versioni successive

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Distribuire più profili di dispositivo per estensioni della mobilità Zebra in un dispositivo, in un gruppo di utenti o in un gruppo di dispositivi <!-- 4089955 -->
In Intune è possibile usare estensioni di mobilità Zebra (MX) in un profilo di configurazione del dispositivo per personalizzare le impostazioni dei dispositivi Zebra non predefinite in Intune. Attualmente è possibile distribuire un profilo per un dispositivo singolo. Questo aggiornamento consente di distribuire più profili in:
- Un gruppo di utenti
- Un gruppo di dispositivi
- Un dispositivo singolo

Per informazioni su come usare MX in Intune, vedere [Usare e gestire i dispositivi Zebra con Mobility Extensions di Zebra in Microsoft Intune](../configuration/android-zebra-mx-overview.md).

Si applica a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Alcune impostazioni della modalità tutto schermo nei dispositivi iOS vengono impostate usando "Blocca" che sostituisce "Consenti" <!-- 4404075  -->
Quando si crea un profilo di limitazione del dispositivo in dispositivi iOS (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Modalità tutto schermo**), si impostano **Blocco automatico**, **Commutatore suoneria**, **Rotazione schermo**, **Pulsante Sospensione schermo** e **Pulsanti volume**. 

In questo aggiornamento i valori sono **Blocca** (blocca la funzionalità) o **Non configurate** (consente la funzionalità). Per visualizzare le impostazioni, andare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità](../configuration/device-restrictions-ios.md#kiosk). 

Si applica a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>Usare Face ID per l'autenticazione della password nei dispositivi iOS <!-- 4490704 -->
Quando si crea un profilo di limitazione per i dispositivi iOS, è possibile usare l'impronta digitale come password. In questo aggiornamento le impostazioni della password tramite impronta digitale consentiranno anche il riconoscimento facciale (**Configurazione dispositivo** > **Profili** > **Crea profilo**  > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Password**). Di conseguenza, le impostazioni seguenti sono modificate:

- **Sblocco con impronta digitale** ora è **Sblocco di Touch ID e Face ID**.
- **Modifica dell'impronta digitale (solo con supervisione)** ora è **Modifica di Touch ID e Face ID (solo con supervisione)** .

Face ID è disponibile in iOS 11.0 e versioni successive. Per visualizzare le impostazioni, andare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md#password).

Si applica a: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>La limitazione di giochi e funzionalità dell'App Store nei dispositivi iOS è ora dipendente dall'area classificazioni <!-- 4593948 -->
Nei dispositivi iOS è possibile consentire o limitare le funzionalità relative a giochi, App Store e visualizzazione dei documenti (**Configurazione dispositivo** > **Profili** > **Crea profilo**  > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi**). È anche possibile scegliere l'area classificazioni, ad esempio Stati Uniti. 

In questo aggiornamento la funzionalità **App** è stata impostata come un elemento figlio di **Area classificazioni** e dipende da **Area classificazioni**. Per visualizzare le impostazioni, andare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Si applica a: iOS

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Supporto di Windows Autopilot per Aggiunta ad Azure AD ibrido <!-- 4809146-->
Windows Autopilot per i dispositivi esistenti supporta ora Aggiunta ad Azure AD ibrido (oltre al supporto di Aggiunta di Azure AD esistente). Si applica ai dispositivi con Windows 10, versione 1809 e successive. Per altre informazioni, vedere [Windows Autopilot per dispositivi esistenti](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Visualizzare il livello della patch di protezione per i dispositivi Android <!-- 4461911 -->
È ora possibile visualizzare il livello della patch di protezione per i dispositivi Android. A tale scopo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Hardware**.
Il livello di patch è elencato nella sezione **Sistema operativo**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Assegnare i tag di ambito a tutti i dispositivi gestiti in un gruppo di sicurezza <!-- 3173810 -->
È ora possibile assegnare i tag di ambito a un gruppo di sicurezza. Anche tutti i dispositivi del gruppo di sicurezza saranno associati a tali tag di ambito. Il tag di ambito verrà assegnato anche a tutti i dispositivi appartenenti ai gruppi. I tag di ambito impostati con questa funzionalità sovrascriveranno quelli impostati con il flusso di tag di ambito del dispositivo corrente. Per altre informazioni, vedere [Use RBAC and scope tags for distributed IT](scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="use-keyword-search-with-security-baselines-------"></a>Usare la ricerca di parole chiave con le baseline di sicurezza <!--  -->
Quando si creano o si modificano i [profili della baseline di sicurezza](../protect/security-baselines.md#create-the-profile), è possibile specificare parole chiave nella nuova barra di *ricerca* per filtrare i gruppi di impostazioni disponibili in base a quelli che contengono i criteri di ricerca. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>La funzionalità Baseline di sicurezza è ora disponibile a livello generale  <!-- 3785395 -->
La funzionalità **Baseline di sicurezza** non è più in fase di anteprima ed è ora disponibile a livello generale.  Tale funzionalità è pertanto pronta per l'uso nell'ambiente di produzione. I singoli modelli di baseline possono tuttavia rimanere disponibili in anteprima e vengono valutati e rilasciati a livello generale con le proprie pianificazioni.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>Il modello Baseline della sicurezza MDM è ora disponibile a livello generale   <!-- 3794072, 4217151,  3534649 -->
Il modello Baseline della sicurezza MDM non è più in fase di anteprima ed è ora disponibile a livello generale. Il modello disponibile a livello generale viene identificato come **Baseline della sicurezza MDM per maggio 2019**.  Si tratta di un nuovo modello, non di un aggiornamento dalla versione di anteprima.  È pertanto necessario rivedere le [impostazioni in esso contenute](../protect/security-baseline-settings-mdm.md) e creare quindi nuovi profili per distribuire il modello nel dispositivo in uso. Altri modelli di baseline di sicurezza possono rimanere in anteprima. Per un elenco delle baseline disponibili, vedere [Baseline di sicurezza disponibili](../protect/security-baselines.md#available-security-baselines).  

Il modello *Baseline della sicurezza MDM per maggio 2019*, oltre a essere nuovo, include le due impostazioni annunciate di recente nell'articolo relativo alle funzionalità in fase di sviluppo:  
- AboveLock. Attiva tramite voce le app dalla schermata di blocco  
- DeviceGuard. Usa la sicurezza basata sulla virtualizzazione al riavvio successivo dei dispositivi.  

*Baseline della sicurezza MDM per maggio 2019* include anche l'aggiunta di numerose nuove impostazioni, la rimozione di altre e una revisione del valore predefinito di un'impostazione. Per un elenco dettagliato delle modifiche tra versione di anteprima e versione disponibile a livello generale, vedere **What's changed in the new template** (Cosa è cambiato nel nuovo modello).

#### <a name="security-baseline-versioning-----3194322---"></a>Controllo delle versioni delle baseline di sicurezza  <!-- 3194322 -->
Le baseline di sicurezza per Intune supportano il controllo delle versioni. Al rilascio di nuove versioni di ogni baseline di sicurezza, è dunque possibile aggiornare i profili delle baseline di sicurezza esistenti in modo che usino la versione di baseline più recente, senza dover ricreare e distribuire una nuova baseline. Nella console di Intune è inoltre possibile visualizzare informazioni su ogni baseline, ad esempio il numero di profili individuali che usano la baseline, quante diverse versioni di baseline vengono usate dai profili e la versione più recente di una specifica baseline di sicurezza.  Per altre informazioni, vedere **Baseline di sicurezza**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>Spostamento dell'impostazione Usa le chiavi di sicurezza per l'accesso  <!-- 4501151 -->
L'impostazione di configurazione del dispositivo per la protezione delle identità denominata **Usa le chiavi di sicurezza per l'accesso** non è più disponibile come un'impostazione secondaria di *Configura Windows Hello for Business*. È ora un'impostazione di livello superiore sempre disponibile, anche quando non si abilita l'uso di Windows Hello for Business. Per altre informazioni, vedere [Protezione dell'identità](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>Nuove autorizzazioni per gli amministratori di gruppi assegnati   <!-- 4504437   -->
Il ruolo di amministratore dell'istituto di istruzione predefinito di Intune dispone ora di autorizzazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD) per le app gestite. Grazie a questo aggiornamento, un utente a cui è assegnato il ruolo di amministratore di gruppo in Intune per Education potrà creare, visualizzare, aggiornare ed eliminare il certificato per le notifiche push MDM iOS, i token del server MDM iOS e i token VPP iOS, oltre a [tutte le autorizzazioni esistenti di cui dispone](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Per eseguire una di queste azioni, andare a **Impostazioni del tenant** > **Gestione dei dispositivi iOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>Le applicazioni possono usare l'API Graph per chiamare le operazioni di lettura senza credenziali utente <!-- 4655885 -->
Le applicazioni possono chiamare le operazioni di lettura dell'API Graph per Intune con l'identità dell'app senza le credenziali utente. Per altre informazioni sull'accesso all'API Microsoft Graph per Intune, vedere [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) (Usare Intune in Microsoft Graph).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Applicare tag di ambito alle app di Microsoft Store per le aziende <!-- 4392555 -->
È ora possibile applicare tag di ambito alle app di Microsoft Store per le aziende. Per altre informazioni sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

## <a name="week-of-june-17-2019"></a>Settimana del 17 giugno 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="new-features-in-microsoft-intune-app"></a>Nuove funzionalità dell'app Microsoft Intune
Sono state aggiunte nuove funzionalità all'app Microsoft Intune (anteprima) per Android. Ora gli utenti di dispositivi Android completamente gestiti possono:  

* Visualizzare e gestire i dispositivi che hanno registrato tramite il Portale aziendale Intune o l'app Microsoft Intune.    
* Contattare l'organizzazione per richiedere supporto.    
* Inviare feedback a Microsoft.    
* Visualizzare termini e condizioni, se impostati dall'organizzazione.    

## <a name="week-of-june-10-2019"></a>Settimana del 10 giugno 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Nuove app di esempio che mostrano l'integrazione di Intune SDK disponibile su GitHub <!-- 2653471 -->
L'account msintuneappsdk di GitHub ha aggiunto nuove applicazioni di esempio per iOS (Swift), Android, Xamarin.iOS, Xamarin Forms e Xamarin.Android. Lo scopo di queste app è completare la documentazione esistente e fornire dimostrazioni su come integrare Intune App SDK nelle proprie app per dispositivi mobili. Gli sviluppatori di app che hanno bisogno di altre indicazioni di Intune SDK possono vedere i collegamenti agli esempi seguenti:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App): app di messaggistica istantanea nativa di iOS (Swift) che usa Azure Active Directory Authentication Library (ADAL) per l'autenticazione negoziata.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App): app di elenco attività nativa di Android che usa ADAL per l'autenticazione negoziata.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps): app di elenco attività di Xamarin.Android che usa ADAL per l'autenticazione negoziata. Questo repository contiene anche l'app Xamarin.Forms.
- [App di esempio di Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios): app di esempio di base per Xamarin.iOS.

## <a name="week-of-may-27-2019"></a>Settimana del 27 maggio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Creazione di report per app potenzialmente dannose nei dispositivi Android <!-- 4223162 -->
Intune ora offre ulteriori informazioni di report sulle app potenzialmente dannose nei dispositivi Android. 

## <a name="week-of-may-20-2019"></a>Settimana del 20 maggio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="windows-company-portal-app----3316993---"></a>App Portale aziendale Windows <!-- 3316993 -->
L'app Portale aziendale di Windows ora ha una nuova pagina con l'etichetta **Dispositivi**. La pagina **Dispositivi** visualizza per gli utenti finali tutti i loro dispositivi registrati. Gli utenti visualizzano questa modifica nel Portale aziendale quando usano la versione 10.3.4291.0 e le versioni successive. Per informazioni sulla configurazione del Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nome dell'attributo OrderID dei dispositivi Autopilot modificato in Tag di gruppo <!-- 4659453 -->

Il nome dell'attributo **OrderID** nei dispositivi Autopilot è stato modificato in **Tag di gruppo** per renderlo più intuitivo. Quando si usano file con estensione csv per caricare informazioni sui dispositivi Autopilot, è necessario usare come intestazione colonna Tag di gruppo e non OrderID.  

## <a name="week-of-may-13-2019"></a>Settimana del 13 maggio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Aggiornamento del metodo di autenticazione e dell'installazione dell'app Portale aziendale per i criteri di Intune  <!-- 1927359  -->
Nei dispositivi già registrati tramite l'Assistente configurazione con uno dei metodi di registrazione dei dispositivi aziendali di Apple, Intune non supporterà più l'app Portale aziendale se installata manualmente dagli utenti finali dall'App Store. Questa modifica è rilevante solo quando si esegue l'autenticazione con Apple Setup Assistant durante la registrazione. Questa modifica riguarda inoltre solo i dispositivi iOS registrati tramite:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

Gli utenti riceveranno un errore se installano l'app Portale aziendale dall'App Store e quindi provano a registrare i dispositivi tramite tale app. È previsto che questi dispositivi usino l'app Portale aziendale solo quando ne è stato eseguito il push automaticamente da Intune durante la registrazione. I profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Se si vuole che gli utenti dei dispositivi DEP dispongano dell'app Portale aziendale, è necessario specificare le preferenze in un profilo di registrazione. 

Inoltre, la schermata **Identifica il dispositivo** nel Portale aziendale iOS è in fase di rimozione. Di conseguenza, gli amministratori che vogliono abilitare l'accesso condizionale o distribuire le app aziendali devono aggiornare il profilo di registrazione DEP. Questo requisito si applica solo se la registrazione DEP viene autenticata con Assistente configurazione. In tal caso, è necessario eseguire il push del Portale aziendale nel dispositivo. A tale scopo, scegliere **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token > **Profili** > scegliere un profilo > **Proprietà** > impostare **Installa il Portale aziendale** su **Sì**.

Per installare il Portale aziendale nei dispositivi DEP già registrati, si dovrà passare a Intune > App client ed eseguirne il push come app gestita con i criteri di configurazione delle app. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Configurare come gli utenti finali aggiornano un'app line-of-business usando i criteri di protezione delle app <!-- 3568384 -->
È ora possibile configurare dove gli utenti finali possono ottenere una versione aggiornata di un'app line-of-business. Gli utenti finali visualizzeranno questa funzionalità nella finestra di dialogo di avvio condizionale **Versione minima dell'app**, in cui verrà chiesto loro di eseguire l'aggiornamento a una versione minima dell'app line-of-business. È necessario fornire queste informazioni dettagliate relative all'aggiornamento come parte dei criteri di protezione dell'app line-of-business (APP). Questa funzionalità è disponibile per iOS e Android. In iOS questa funzionalità richiede che l'app venga integrata (o sottoposta a wrapping tramite lo strumento di wrapping) con Intune SDK per iOS 10.0.7 o versioni successive. In Android questa funzionalità richiede la versione del Portale aziendale più recente. Per configurare il modo in cui un utente finale aggiorna un'app line-of-business, l'app necessita che venga inviato un criterio di configurazione dell'app gestita con la chiave `com.microsoft.intune.myappstore`. Il valore inviato definirà da quale archivio l'utente finale scaricherà l'app. Se l'app viene distribuita tramite il portale aziendale, il valore deve essere `CompanyPortal`. Per qualsiasi altro archivio, è necessario immettere un URL completo.

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Script di PowerShell per l'estensione di gestione di Intune  <!-- 3734186  -->
È possibile configurare gli script di PowerShell per l'esecuzione con privilegi di amministratore dell'utente nel dispositivo. Per altre informazioni, vedere [Usare gli script di PowerShell nei dispositivi Windows 10 in Intune](../apps/intune-management-extension.md) e [Gestione delle app Win32](../apps/app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Gestione delle app Android Enterprise <!-- 4459905 -->
Per facilitare la configurazione e l'uso delle funzionalità di gestione di Android Enterprise per gli amministratori IT, Intune aggiungerà automaticamente quattro app comuni correlate a Android Enterprise alla console di amministrazione di Intune. Le quattro app per Android Enterprise sono le seguenti:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usata per gli scenari di Android Enterprise completamente gestiti.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)**  - Consente di accedere agli account se si usa la verifica a due fattori.
- **[Portale aziendale di Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usare per gli scenari con criteri di protezione app e profili di lavoro di Android Enterprise.
- [Schermata iniziale gestita](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Usata per gli scenari di Android Enterprise dedicati/in modalità a schermo intero.

In precedenza, gli amministratori IT dovevano trovare e approvare manualmente queste app in [Google Play Store gestito](https://play.google.com/store/apps) durante l'installazione. Questa modifica rimuove i passaggi manuali precedenti per consentire ai clienti di usare più facilmente e velocemente le funzionalità di gestione di Android Enterprise.

Gli amministratori IT noteranno che queste quattro app vengono aggiunte automaticamente all'elenco di app di Intune in occasione della prima connessione del tenant di Intune a Google Play gestito. Per altre informazioni, vedere [Connettere l'account di Intune all'account di Google Play gestito](../enrollment/connect-intune-android-enterprise.md). Per i tenant già connessi o che usano già Android Enterprise, gli amministratori non devono eseguire alcuna operazione. Queste quattro app diventeranno disponibili automaticamente entro 7 giorni dal completamento dell'implementazione del servizio di maggio 2019.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Connettore di certificati PFX per Microsoft Intune aggiornato  <!-- 1533038 -->
È stato rilasciato un aggiornamento per il [Connettore del certificato PFX per Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) che risolve un problema a causa del quale i certificati PFX esistenti continuano a essere rielaborati e di conseguenza il connettore smette di elaborare le nuove richieste.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Attività di sicurezza di Intune per Defender ATP (in anteprima pubblica)     <!-- 3208597 -->
Nella fase di anteprima pubblica, è possibile usare Intune per gestire le [attività di sicurezza per Microsoft Defender Advanced Threat Protection (ATP)](../protect/atp-manage-vulnerabilities.md). L'integrazione con ATP aggiunge un approccio basato sui rischi per individuare, classificare e correggere gli errori di configurazione e le vulnerabilità degli endpoint, riducendo il tempo tra l'individuazione e la mitigazione.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10 <!-- 3617671   idstaged-->
Molti dispositivi Windows 10 e versioni successive hanno chipset Trusted Platform Module (TPM). Questo aggiornamento include una nuova impostazione di conformità che controlla la versione del chip TPM del dispositivo. 

Questa impostazione è descritta in [Impostazioni dei criteri di conformità per i dispositivi Windows 10 e versioni successive](../protect/compliance-policy-create-windows.md#device-security).

Si applica a: Windows 10 e versioni successive

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Impedire agli utenti finali di modificare l'hotspot personale e disabilitare la registrazione nel server Siri nei dispositivi iOS <!-- 4097904   -->  
Creare un profilo di limitazioni del dispositivo nel dispositivo iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni, che è possibile configurare:

- **App predefinite**: Registrazione lato server per i comandi di Siri
- **Wireless**: Modifica dell'utente dell'hotspot personale (solo con supervisione)

Per visualizzare queste impostazioni, passare alle [impostazioni predefinite dell'app per iOS](../configuration/device-restrictions-ios.md#built-in-apps) e alle [impostazioni wireless per iOS](../configuration/device-restrictions-ios.md#wireless).

Si applica a: iOS 12.2 e versioni successive

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nuove impostazioni di limitazione del dispositivo per l'app Classroom per i dispositivi macOS <!-- 4097905   --> 
È possibile creare un profilo di configurazione del dispositivo per i dispositivi macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni dell'app Classroom, la possibilità di bloccare gli screenshot e la possibilità di disabilitare la Libreria foto di iCloud.

Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-macos.md).

Si applica a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>L'impostazione della password iOS per l'accesso all'App Store è stata rinominata<!-- 4557891  -->
L'impostazione **Password per l'accesso all'App Store** è stata rinominata in **Require iTunes Store password for all purchases** (Richiedere password iTunes Store per tutti gli acquisti) (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi**).

Per visualizzare le impostazioni disponibili, passare alle [impostazioni iOS di App Store, visualizzazione documenti, giochi](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Si applica a: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Baseline di Microsoft Defender Advanced Threat Protection (anteprima)  <!--  3754134 -->
È stata aggiunta un'anteprima della baseline di sicurezza per le impostazioni di [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md). Questa baseline è disponibile quando l'ambiente soddisfa i prerequisiti per l'uso di [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>La pagina relativa allo stato della registrazione di Windows è ora disponibile a livello generale <!-- 3605348 -->
La pagina relativa allo stato della registrazione non è più in fase di anteprima. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Aggiornamento dell'interfaccia utente di Intune - Creazione del profilo di registrazione Autopilot  <!-- 4593669 -->
L'interfaccia utente per la creazione di un profilo di registrazione Autopilot è stata aggiornata per allinearsi agli stili dell'interfaccia utente di Azure. Per altre informazioni, vedere [Creare un profilo di distribuzione Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Più avanti, altri scenari di Intune verranno aggiornati a questo nuovo stile dell'interfaccia utente.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Abilitare Reimpostazione di AutoPilot per tutti i dispositivi Windows <!-- 4225665 -->
Reimpostazione di AutoPilot ora funziona per tutti i dispositivi Windows, anche quelli non configurati per l'uso della pagina relativa allo stato della registrazione. Se durante la registrazione iniziale del dispositivo non è stata configurata una pagina relativa allo stato della registrazione per il dispositivo, il dispositivo passerà direttamente al desktop dopo l'accesso. Potrebbero essere necessarie fino a otto ore per la sincronizzazione e la visualizzazione come conforme in Intune. Per altre informazioni, vedere [Reimpostare i dispositivi con Reimpostazione di Windows Autopilot remota](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Formato IMEI esatto non richiesto durante la ricerca in tutti i dispositivi <!--30407680 -->
Non è necessario includere spazi nei numeri IMEI quando si esegue una ricerca in **Tutti i dispositivi**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>L'eliminazione di un dispositivo nel portale Apple si rifletterà nel portale di Intune <!--2489996 -->
Se un dispositivo viene eliminato dai portali di Device Enrollment Program di Apple o Apple Business Manager, il dispositivo verrà automaticamente eliminato da Intune durante la sincronizzazione successiva.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>La pagina di stato della registrazione ora tiene traccia delle app Win32 <!-- 2714451 -->
Ciò si applica solo ai dispositivi che eseguono Windows 10 versione 1903 e successive. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Reimpostare e cancellare i dispositivi in blocco usando l'API Graph <!-- 3295288 -->
È ora possibile reimpostare e cancellare un massimo di 100 dispositivi in blocco tramite l'API Graph.


### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Il report di crittografia non è più disponibile come anteprima pubblica   <!-- 4587546      -->
Il [report per BitLocker e la crittografia dei dispositivi](../protect/encryption-monitor.md) è ora disponibile a livello generale e non più come anteprima pubblica. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Impostazioni biometriche e della firma di Outlook per dispositivi iOS e Android <!-- 4050557 -->
È ora possibile specificare se la firma predefinita è abilitata in Outlook nei dispositivi iOS e Android. Inoltre, è possibile scegliere se consentire agli utenti di modificare l'impostazione biometrica in Outlook in iOS.

## <a name="week-of-may-6-2019"></a>Settimana del 6 maggio 2019 

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Supporto del controllo di accesso alla rete per F5 Access per dispositivi iOS <!-- 4500808 -->

F5 ha rilasciato un aggiornamento di BIG-IP 13 che abilita la funzionalità di controllo di accesso alla rete per F5 Access su iOS in Intune. Per usare questa funzionalità:

- Aggiornare BIG-IP alla versione 13.1.1.5. BIG-IP 14 non è supportata.
- Integrare BIG-IP con Intune per il controllo di accesso alla rete. Vedere la procedura in [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Controllare l'impostazione di **Abilita il controllo accesso alla rete** nel profilo VPN in Intune.

Per vedere l'impostazione disponibile, passare a [Configurare le impostazioni VPN nei dispositivi iOS](../configuration/vpn-settings-ios.md).

Si applica a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Connettore di certificati PFX per Microsoft Intune aggiornato <!-- doc-vso 1521237  -->  
È stato rilasciato un aggiornamento del [connettore di certificati PFX per Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) in cui l'intervallo di polling è stato ridotto da 5 minuti a 30 secondi.

## <a name="week-of-april-22-2019"></a>Settimana del 22 aprile 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Usare Compliance Manager per creare valutazioni per Microsoft Intune<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager) (apre un altro sito Microsoft) è uno strumento di valutazione dei rischi basato su flussi di lavoro disponibile in Microsoft Service Trust Portal. Consente di tenere traccia, assegnare e verificare le attività di conformità alle normative dell'organizzazione relativamente ai servizi Microsoft. È possibile creare una valutazione personalizzata della conformità con Office 365, Azure, Dynamics, Servizi professionali e Intune. Intune include due valutazioni: FFIEC e GDPR.

Compliance Manager consente di concentrare l'attenzione analizzando in dettaglio i controlli, sia quelli gestiti da Microsoft che quelli gestiti dall'organizzazione. È possibile completare le valutazioni per poi esportarle e stamparle.

La conformità alle normative [FFIEC (Federal Financial Institutions Examination Council)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (apre un altro sito Microsoft) prevede un set di standard per l'online banking emanati da FFIEC. È la valutazione più richiesta per gli istituti finanziari che usano Intune. Interpreta in che modo Intune consente di soddisfare le linee guida per la sicurezza informatica FFIEC relative ai carichi di lavoro del cloud pubblico. La valutazione FFIEC di Intune è la seconda valutazione FFIEC in Compliance Manager.

Nell'esempio seguente è possibile visualizzare i controlli FFIEC in dettaglio. Microsoft copre 64 controlli. L'organizzazione è responsabile dei 12 controlli rimanenti.

![Esempio di valutazione di Intune per FFIEC, che include le azioni dei clienti e le azioni di Microsoft](./media/whats-new/intune-ffiec-assessment-status.png)

Il [Regolamento generale sulla protezione dei dati (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (apre un altro sito Microsoft) è una normativa dell'Unione Europea (UE) che tutela i diritti dei singoli utenti e i relativi dati personali. Il GDPR è la valutazione più richiesta per garantire la conformità con le normative sulla privacy. 

Nell'esempio seguente sono illustrati i controlli GDPR in dettaglio. Microsoft copre 49 controlli. L'organizzazione è responsabile dei 66 controlli rimanenti.

![Esempio di valutazione di Intune per il GDPR, che include le azioni dei clienti e le azioni di Microsoft](./media/whats-new/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Settimana del 15 aprile 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Crittografia OpenSSL per i criteri di protezione delle app per Android <!-- 3747362 -->
I criteri di Protezione app di Intune nei dispositivi Android usano ora una libreria di crittografia OpenSSL compatibile con FIPS 140-2. Per altre informazioni, vedere la sezione [Crittografia](../apps/app-protection-policy-settings-android.md#encryption) di [Impostazioni dei criteri di protezione delle app di Android in Microsoft Intune](../apps/app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Abilitare le dipendenze delle app Win32 <!-- 2617348  -->
Gli amministratori possono richiedere che vengano installate altre app come dipendenze prima di installare l'app Win32. In particolare, il dispositivo deve installare le app dipendenti prima di installare l'app Win32. In Intune selezionare **App client** > **App** > **Aggiungi** per visualizzare il pannello **Aggiungi app**. Selezionare **App di Windows (Win32)** come **Tipo di app**. Dopo aver aggiunto l'app, è possibile selezionare **Dipendenze** per aggiungere le app dipendenti che devono essere installate prima di poter installare l'app Win32. Per altre informazioni, vedere [Intune autonomo - Gestione di app Win32](./../apps/app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Informazioni di installazione sulla versione delle app per le app di Microsoft Store per le aziende <!-- 3537391   -->
I report di installazione delle app includono informazioni sulla versione delle app per le app di Microsoft Store per le aziende. In Intune selezionare **App client** > **App**. Selezionare un'**app di Microsoft Store per le aziende** e quindi selezionare **Stato dell'installazione del dispositivo** nella sezione **Monitoraggio**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Aggiunte alle regole relative ai requisiti delle app Win32 <!-- 3676883   -->
È possibile creare regole relative ai requisiti basate su script di PowerShell, valori del Registro di sistema e informazioni del file system. In Intune selezionare **App client** > **App** > **Aggiungi**. Quindi selezionare **App di Windows (Win32)** come **Tipo di App** nel pannello **Aggiungi app**.  Selezionare **Requisiti** > **Aggiungi** per configurare regole aggiuntive relative ai requisiti. Selezionare quindi **Tipo di file**, **Registro** o **Script** come **Tipo di requisito**. Per altre informazioni, vedere [Gestione di app Win32](./../apps/app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Configurare le app Win32 da installare in dispositivi aggiunti ad Azure AD registrati in Intune <!-- 3695227  -->
È possibile assegnare le app Win32 da installare in dispositivi aggiunti ad Azure AD registrati in Intune. Per altre informazioni sulle app Win32 in Intune, vedere [Gestione di app Win32](./../apps/app-management.md).

#### <a name="device-overview-shows-primary-user---3794259----"></a>La panoramica del dispositivo mostra l'utente primario <!--3794259  -->
Nella pagina Panoramica del dispositivo verrà visualizzato l'utente primario, detto anche utente affinità utente-dispositivo. Per visualizzare l'utente primario per un dispositivo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo. L'utente primario verrà visualizzato nella parte superiore della pagina **Panoramica**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Segnalazione app Google Play gestite per dispositivi del profilo di lavoro Android Enterprise <!-- 4105925  -->
Per le app Google Play gestite distribuite nei dispositivi del profilo di lavoro Android Enterprise, è possibile visualizzare il numero di versione specifico dell'app installata in un dispositivo. Questo vale solo per le app richieste.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Tastiere di terze parti iOS <!-- 4111843   -->
Il supporto per i criteri di protezione app di Intune per l'impostazione delle **tastiere di terze parti** per iOS non è più disponibile a causa di una modifica della piattaforma iOS. Non sarà possibile configurare questa impostazione nella console di amministrazione di Intune e non verrà applicata nel client in Intune App SDK.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Configurare le impostazioni di accesso e controllare le opzioni di riavvio nei dispositivi macOS <!-- 1210083  -->
Nei dispositivi macOS è possibile creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni della finestra di accesso, ad esempio per la visualizzazione di un banner personalizzato, la scelta della modalità di accesso di un utente, la possibilità di visualizzare o nascondere le impostazioni di risparmio energia e altro ancora.

Per visualizzare queste impostazioni, vedere [Impostazioni relative alle funzionalità dei dispositivi macOS in Intune](../configuration/macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Configurare le impostazioni Wi-Fi nei dispositivi dedicati del proprietario del dispositivo Android Enterprise in esecuzione in modalità tutto schermo con più app <!--3041940  -->
È possibile abilitare le impostazioni per il proprietario del dispositivo Android Enterprise in caso di esecuzione come dispositivo dedicato in modalità tutto schermo con più app. In questo aggiornamento è possibile consentire agli utenti di configurare e connettersi alle reti Wi-Fi (**Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo > **Dispositivi dedicati** > **Modalità tutto schermo**: **Più app** > **Configurazione Wi-Fi**). 

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a: Dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Configurare le impostazioni Bluetooth e l'associazione nei dispositivi dedicati del proprietario del dispositivo Android Enterprise in esecuzione in modalità tutto schermo con più app <!-- 3041941  -->
È possibile abilitare le impostazioni per il proprietario del dispositivo Android Enterprise in caso di esecuzione come dispositivo dedicato in modalità tutto schermo con più app. In questo aggiornamento è possibile consentire agli utenti finali di abilitare il Bluetooth e associare dispositivi tramite Bluetooth (**Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo > **Dispositivi dedicati** > **Modalità tutto schermo**: **Multi-app** > **Configurazione Bluetooth**). 

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a: Dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Creare e usare profili di configurazione dei dispositivi OEMConfig in Intune <!-- 3305883  -->
In questo aggiornamento Intune supporta la configurazione di dispositivi Android Enterprise con OEMConfig. In particolare, è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android Enterprise usando OEMConfig (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma).

Il supporto per gli OEM è attualmente su base per OEM. Se una specifica app OEMConfig non è disponibile nell'elenco delle app OEMConfig, contattare `IntuneOEMConfig@microsoft.com`.

Per altre informazioni su questa funzionalità, passare a [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](../configuration/android-oem-configuration-overview.md) (Usare e gestire i dispositivi Android Enterprise con OEMConfig in Microsoft Intune).

Si applica a: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Notifiche di Windows Update  <!-- 3316758, 3316782  -->
Sono state aggiunte due *impostazioni dell'esperienza utente* alle configurazioni degli anelli di Windows Update che è possibile gestire dalla console di Intune. È ora possibile:
- Impedire o consentire agli utenti di [verificare la disponibilità di aggiornamenti per Windows](../protect/windows-update-settings.md).
- Gestire il [livello di notifica di Windows Update](../protect/windows-update-settings.md) visibile agli utenti.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Nuove impostazioni relative alle restrizioni dei dispositivi per il proprietario del dispositivo Android Enterprise <!-- 3574254  -->
Nei dispositivi Android Enterprise è possibile creare un profilo di restrizione dei dispositivi per consentire o limitare le funzionalità, impostare regole per le password e altro ancora (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo). 

Questo aggiornamento include nuove impostazioni delle password, consente l'accesso completo alle app in Google Play Store per i dispositivi completamente gestiti e altro ancora. Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md). 

Si applica a: Dispositivi completamente gestiti Android Enterprise

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10 <!-- 3617671 -->

Questa funzionalità è in ritardo ed è pianificata per essere rilasciata più avanti.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Modifiche all'interfaccia utente aggiornate per il browser Microsoft Edge in dispositivi Windows 10 e versioni successive <!-- 3775833   -->
Quando si crea un profilo di configurazione del dispositivo, è possibile consentire o limitare l'uso delle funzionalità di Microsoft Edge in dispositivi Windows 10 e versioni successive (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma, > **Limitazioni del dispositivo** per il tipo di profilo > **Browser Microsoft Edge**). In questo aggiornamento le impostazioni di Microsoft Edge sono più descrittive e più semplici da comprendere. 

Per visualizzare queste funzionalità, passare alle [impostazioni relative alle restrizioni per i dispositivi per il browser Microsoft Edge](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

Si applica a: Windows 10 e versioni successive

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Supporto esteso per i dispositivi Android Enterprise completamente gestiti (anteprima)  <!--   3903241, 3903244, 3903246   -->
Ancora in anteprima pubblica, il supporto per i dispositivi Android Enterprise completamente gestiti ([annunciato nel gennaio 2019](whats-new.md#week-of-january-14-2019)) è stato esteso per includere le funzionalità seguenti: 

- Nei dispositivi dedicati e completamente gestiti è possibile creare [criteri di conformità](../protect/compliance-policy-create-android-for-work.md) per includere regole per le password e requisiti del sistema operativo (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android Enterprise** per la piattaforma > **Proprietario del dispositivo** per il tipo di profilo). 

  Nei dispositivi dedicati il dispositivo potrebbe essere visualizzato come **Non conforme**. L'accesso condizionale non è disponibile nei dispositivi dedicati. Assicurarsi di completare qualsiasi attività o operazione per garantire che i dispositivi dedicati siano conformi con i criteri assegnati.

- [Accesso condizionale](../protect/conditional-access.md): i criteri di accesso condizionale che si applicano ad Android sono applicabili anche ai dispositivi Android Enterprise completamente gestiti. Gli utenti possono ora registrare i propri dispositivi completamente gestiti in Azure Active Directory tramite l'**app Microsoft Intune**. Quindi, visualizzare e risolvere eventuali problemi di conformità per accedere alle risorse aziendali.

- Nuova app per l'utente finale (app Microsoft Intune): è disponibile una nuova app per l'utente finale per i dispositivi Android completamente gestiti chiamata **Microsoft Intune**. La nuova app è leggera e moderna e offre funzionalità simili a quelle dell'app Portale aziendale, ma per i dispositivi completamente gestiti. Per altre informazioni, vedere l'[app Microsoft Intune in Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Per configurare dispositivi Android completamente gestiti, passare a **Registrazione del dispositivo** > **Registrazione Android** > **Dispositivi utente completamente gestiti di proprietà aziendale**. Il supporto per i dispositivi Android completamente gestiti rimane disponibile in anteprima e alcune funzionalità di Intune potrebbero non essere completamente funzionali.  

Per altre informazioni su questa anteprima, vedere il blog [Microsoft Intune announces Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged) (Microsoft Intune annuncia la versione Preview 2 per i dispositivi Android Enterprise completamente gestiti).


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Configurare il profilo per ignorare alcune schermate durante l'esecuzione di Assistente configurazione <!-- 2276470  -->
Quando si crea un profilo di registrazione macOS, è possibile configurarlo per ignorare tutte le schermate seguenti quando un utente esegue Assistente configurazione:
- Aspetto
- Display Tone (Tono schermo)
- iCloudStorage Se si crea un nuovo profilo o si modifica un profilo, le schermate da ignorare selezionate devono essere sincronizzate con il server MDM di Apple.  Gli utenti possono eseguire una sincronizzazione manuale dei dispositivi in modo da evitare ritardi nell'aggiornamento delle modifiche del profilo.
Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS con Device Enrollment Program o Apple School Manager](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Denominazione in blocco dei dispositivi durante la registrazione di dispositivi iOS aziendali<!--3566569  -->
Quando si usa uno dei metodi di registrazione aziendali di Apple (DEP/ABM/ASM), è possibile impostare un formato del nome del dispositivo in modo da denominare automaticamente i dispositivi iOS in ingresso. È possibile specificare un formato che include il tipo di dispositivo e il numero di serie nel modello. A tale scopo, scegliere **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > **Selezionare un token** >**Crea profilo** > **Device naming format (Formato di denominazione dispositivi)** . È possibile modificare i profili esistenti, ma il nome sarà applicato solo ai dispositivi appena sincronizzati.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Messaggio di timeout predefinito aggiornato nella pagina Stato della registrazione <!-- 3959331 -->
È stato aggiornato il messaggio di timeout predefinito che gli utenti vedono quando la pagina Stato della registrazione (ESP) supera il valore di timeout specificato nel profilo ESP. Il nuovo messaggio predefinito è quello che gli utenti vedono e consente di comprendere le azioni successive da eseguire durante la distribuzione ESP.  

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Ritirare i dispositivi non conformi  <!-- 1827291   -->
Questa funzionalità è stata posticipata ed è pianificata per una versione futura.


### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Le modifiche al data warehouse di Intune V1.0 si riflettono nella versione beta <!-- 4403765 -->
Quando V1.0 è stato introdotto per la prima volta nella versione 1808, c'erano delle differenze sostanziali rispetto alla versione beta dell'API. Nella versione 1903 queste modifiche si rifletteranno nella versione beta dell'API. Se si dispone di report importanti che usano la versione beta dell'API, è consigliabile passare tali report a V1.0 per evitare modifiche significative. Per altre informazioni, vedere [Registro modifiche per l'API data warehouse di Intune](../developer/reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorare lo stato della baseline di sicurezza (anteprima pubblica) <!-- 3082047 --> 
È stata aggiunta una [visualizzazione per categoria](../protect/security-baselines-monitor.md#per-category-view) per il monitoraggio delle baseline di sicurezza (le baseline di sicurezza rimangono in anteprima). La visualizzazione per categoria consente di visualizzare ogni categoria dalla baseline con la percentuale di dispositivi che rientrano in ogni gruppo di stato per tale categoria. È ora possibile visualizzare quanti dispositivi non corrispondono alle singole categorie, non sono configurati correttamente o non sono applicabili.

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Tag di ambito per i token VPP Apple <!--2371886  -->
È ora possibile aggiungere tag di ambito per i token VPP Apple. Solo gli utenti assegnati con lo stesso tag di ambito avranno accesso al token VPP Apple con tale tag. Le app VPP e gli eBook acquistati con tale token ereditano i tag di ambito. Per altre informazioni sui tag di ambito, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Settimana del 1 aprile 2019

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Connettori di certificati aggiornati  <!-- ICM 113304612 -->
Sono stati rilasciati aggiornamenti per il [connettore di certificati di Intune e il connettore di certificati PFX per Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors). Le nuove versioni consentono di risolvere diversi problemi noti.  

### <a name="app-management"></a>Gestione delle app

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS <!-- 2536024 -->
La home page dell'app Portale aziendale per i dispositivi iOS è stata riprogettata. Con questa modifica, la home page seguirà meglio i modelli dell'interfaccia utente iOS, oltre a garantire un'individuabilità migliorata per le app e gli eBook.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Modifiche alla registrazione nel Portale aziendale per gli utenti dei dispositivi iOS 12 <!--3448635 -->  
Le schermate e i passaggi per la registrazione nel Portale aziendale per iOS sono stati aggiornati per un miglior allineamento con le modifiche della registrazione MDM rilasciate in Apple iOS 12.2. Il flusso di lavoro aggiornato richiede agli utenti di:  

* Consentire a Safari di aprire il sito Web del Portale aziendale e scaricare il profilo di gestione prima di tornare all'app Portale aziendale.  
* Aprire l'app Impostazioni per installare il profilo di gestione nel dispositivo in uso.
* Tornare all'app Portale aziendale per completare la registrazione.  

Per le schermate e i passaggi per la registrazione aggiornati, vedere [Registrare il dispositivo iOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Settimana del 25 marzo 2019

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Supporto per l'app di conformità di Power BI dal pannello Data warehouse in Microsoft Intune <!-- 4260871 -->
In precedenza, il collegamento **Scarica il file di Power BI** nel pannello **Data warehouse di Intune** consentiva di scaricare un report Data warehouse di Intune (file con estensione pbix). Questo report è stato sostituito con l'app di conformità di Power BI. L'app di conformità di Power BI non richiederà uno speciale caricamento o installazione. Verrà aperta direttamente nel portale online di Power BI e visualizzerà i dati per il tenant di Intune in base alle credenziali specificate. In Intune selezionare il collegamento **Configura il data warehouse di Intune** sul lato destro del pannello di Intune. Quindi, fare clic su **Scarica l'app Power BI**. Per altre informazioni, vedere [Connettersi al data warehouse con Power BI](../developer/reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Settimana del 18 marzo 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Distribuire Microsoft Visio e Microsoft Project <!-- 3725386  -->
È ora possibile distribuire Microsoft Visio Pro for Office 365 e il client desktop di Microsoft Project Online come app indipendenti in dispositivi Windows 10 usando Microsoft Intune, se si dispone delle licenze per queste app. Da Intune selezionare **App client** > **App** > **Aggiungi** per visualizzare il pannello **Aggiungi app**. Nel pannello **Aggiungi app** selezionare **Windows 10** come **Tipo di app**. Quindi, selezionare **Configura la suite di app** per selezionare le app da installare. Per altre informazioni sulle app di Office 365 per i dispositivi Windows 10, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 per la modifica del nome del prodotto <!-- 3593653  -->
**Microsoft Visio Pro for Office 365** sarà ora noto come **Microsoft Visio Online Piano 2**.  Per altre informazioni su Microsoft Visio, vedere [Visio Online Piano 2](https://products.office.com/visio/visio-online-plan-2). Per altre informazioni sulle app di Office 365 per i dispositivi Windows 10, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Impostazione del limite di caratteri per i criteri di Protezione app di Intune <!-- 3291302  -->
Gli amministratori di Intune possono specificare un'eccezione per l'impostazione del criterio **Limita le operazioni taglia, copia e incolla con le altre app** dell'app Intune.  L'amministratore può specificare il numero di caratteri che è possibile tagliare o copiare da un'app gestita. Questa impostazione consente la condivisione del numero specificato di caratteri in qualsiasi app, indipendentemente dall'impostazione "Limita le operazioni taglia, copia e incolla con le altre app". Si noti che la versione dell'app Portale aziendale Intune per Android richiede la versione 5.0.4364.0 o successive. Per altre informazioni, vedere le sezioni sulla [protezione dei dati iOS](../apps/app-protection-policy-settings-ios.md#data-protection) e sulla [protezione dei dati Android](../apps/app-protection-policy-settings-android.md#data-protection) ed [Esaminare i log di protezione delle app client](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Strumento di distribuzione di Office (ODT) XML per la distribuzione di Office ProPlus <!-- 3192477   -->
Sarà possibile includere lo Strumento di distribuzione di Office (ODT) XML quando si crea un'istanza di Office Pro Plus nella console di amministrazione di Intune. In questo modo si garantirà una maggiore possibilità di personalizzazione se le opzioni dell'interfaccia utente di Intune esistenti non soddisfano le proprie esigenze. Per altre informazioni, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](../apps/apps-add-office365.md) e [Opzioni di configurazione per lo Strumento di distribuzione di Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente <!-- 1429026  -->
Nell'app Portale aziendale Windows le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente in base al colore dominante dell'icona, se rilevabile. Se applicabile, questo sfondo sostituirà il bordo grigio precedentemente visibile nei riquadri delle app. Gli utenti visualizzeranno questa modifica nelle versioni del Portale aziendale successive alla 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installare le app disponibili tramite l'app Portale aziendale dopo la registrazione in blocco di Windows <!-- 2751523   -->
I dispositivi Windows registrati in Intune tramite la [registrazione in blocco di Windows](../enrollment/windows-bulk-enroll.md) (pacchetti di provisioning) potranno usare l'app Portale aziendale per installare le app disponibili. Per altre informazioni sull'app Portale aziendale, vedere [Aggiungere manualmente l'app Portale aziendale di Windows 10](../apps/store-apps-company-portal-app.md) e [Come configurare l'app Portale aziendale di Microsoft Intune](../apps/company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>L'app Microsoft Teams può essere selezionata nell'ambito della suite di app Office <!-- 3828932  -->
L'app Microsoft Teams può essere inclusa o esclusa nell'ambito dell'installazione della suite di app Office Pro Plus. Questa funzionalità può essere usata per Office Pro Plus numero di build 16.0.11328.20116+. L'utente deve disconnettersi e quindi accedere al dispositivo per completare l'installazione. In Intune selezionare **App client** > **App** > **Aggiungi**. Selezionare uno dei tipi di app **Famiglia di prodotti Office 365** e quindi selezionare **Configura la suite di app**.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Avviare automaticamente un'app durante l'esecuzione di più app in modalità tutto schermo nei dispositivi Windows 10 e versioni successive <!-- 2351390 -->

Nei dispositivi Windows 10 e versioni successive è possibile eseguire un dispositivo in modalità tutto schermo ed eseguire molte app. In questo aggiornamento è disponibile un'impostazione **Avvio automatico** (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Modalità tutto schermo** per il tipo di profilo > **Più app in modalità tutto schermo**). Usare questa impostazione per avviare automaticamente un'app quando l'utente accede al dispositivo.

Per visualizzare un elenco e una descrizione di tutte le impostazioni della modalità tutto schermo, vedere [Impostazioni dei dispositivi Windows 10 e versioni successive per l'esecuzione in modalità tutto schermo in Intune](../configuration/kiosk-settings-windows.md).

Si applica a: Windows 10 e versioni successive

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>I log operativi mostrano anche i dettagli dei dispositivi non conformi <!-- 4063755  -->
Quando si effettua il routing dei log di Intune alle funzionalità di monitoraggio di Azure, è anche possibile indirizzare i log operativi. In questo aggiornamento i log operativi forniscono anche informazioni sui dispositivi non conformi. 

Per altre informazioni su questa funzionalità, vedere [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics in Intune](../review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Indirizzare i log a Monitoraggio di Azure in altri carichi di lavoro di Intune <!-- 3804627 -->
In Intune è possibile indirizzare i log operativi e di controllo agli hub eventi, alla risorsa di archiviazione e a Log Analytics in Monitoraggio di Azure (**Intune** > **Monitoraggio** > **Impostazioni di diagnostica**). In questo aggiornamento è possibile indirizzare questi log in altri carichi di lavoro di Intune, tra cui conformità, configurazioni, app client e altro ancora. 

Per altre informazioni sul routing dei log a Monitoraggio di Azure, vedere [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics](../review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Creare e usare estensioni di mobilità nei dispositivi Android Zebra in Intune <!-- 3305880   -->
In questo aggiornamento Intune supporta la configurazione di dispositivi Android Zebra. In particolare, è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android Zebra usando i profili delle estensioni di mobilità (MX) generati da StageNow (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android** per la piattaforma > **Profilo MX (solo Zebra)** per il tipo di profilo).

Per altre informazioni su questa funzionalità, vedere [Usare e gestire i dispositivi Zebra con le estensioni di mobilità in Intune](../configuration/android-zebra-mx-overview.md).

Si applica a: Android

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Report di crittografia per i dispositivi Windows 10 (in anteprima pubblica)<!-- 2351538 -->  
Usare il nuovo [report di crittografia (anteprima)](../protect/encryption-monitor.md) per visualizzare informazioni dettagliate sullo stato della crittografia dei dispositivi Windows 10. I dettagli disponibili includono una versione TPM dei dispositivi, conformità e stato della crittografia, segnalazione errori e altro ancora.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Accedere alle chiavi di ripristino di BitLocker dal portale di Intune (in anteprima pubblica) <!-- 2351547   -->  
È ora possibile usare Intune per [visualizzare informazioni dettagliate](../protect/encryption-monitor.md) sull'ID chiave BitLocker e le chiavi di ripristino di BitLocker da Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Supporto Microsoft Edge per gli scenari di Intune nei dispositivi iOS e Android <!-- 3411007 -->
Microsoft Edge supporterà tutti gli stessi scenari di gestione di Intune Managed Browser con l'aggiunta di miglioramenti all'esperienza utente finale. Le funzionalità aziendali di Microsoft Edge che vengono abilitate dai criteri di Intune includono doppia identità, integrazione dei criteri di protezione delle app, integrazione del proxy di applicazione di Azure e collegamenti gestiti ai Preferiti e alla home page. Per altre informazioni, vedere la sezione relativa al [supporto Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Supporto deprecato di Exchange Online/Intune Connector per i dispositivi solo EAS <!--3105122  -->
La console di Intune non supporta più la visualizzazione e la gestione dei dispositivi solo EAS connessi a Exchange Online con Intune Connector. In alternativa, sono disponibili le opzioni seguenti:
- Registrare i dispositivi nella gestione dei dispositivi mobili (MDM)
- Usare i criteri di Protezione app di Intune per gestire i dispositivi
- Usare i controlli di Exchange, come descritto in [Client e dispositivi mobili in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Cercare un dispositivo specifico nella pagina Tutti i dispositivi tramite [nome] <!--4254930 -->
È ora possibile cercare un nome dispositivo esatto. Passare a **Intune** > **Dispositivi** > **Tutti i dispositivi** > nella casella di ricerca racchiudere il nome dispositivo con {} per cercare una corrispondenza esatta. Ad esempio, **{Dispositivo12345}** .

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Supporto per connettori aggiuntivi nella pagina Stato tenant <!-- 3617202  -->
La [pagina Stato tenant](../tenant-status.md) visualizza ora le informazioni sullo stato per altri connettori, tra cui *Windows Defender Advanced Threat Protection* (ATP) e altri connettori Mobile Threat Defense.

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Concedere l'accesso in sola lettura a Intune ad alcuni ruoli di Azure Active Directory <!-- 3637917  -->
È stato concesso l'accesso in sola lettura a Intune ai ruoli di Azure AD seguenti. Le autorizzazioni concesse con i ruoli di Azure AD sostituiscono quelle concesse con il controllo degli accessi in base al ruolo di Intune.

Accesso in sola lettura ai dati di controllo di Intune:

- Amministratore di conformità
- Amministratore dati di conformità

Accesso in sola lettura a tutti i dati di Intune:

- Amministratore della protezione
- Operatore di sicurezza
- Ruolo con autorizzazioni di lettura per la sicurezza

Per altre informazioni, vedere [Controllo degli accessi in base al ruolo](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Tag di ambito per i profili di provisioning delle app iOS <!--2934430   -->
È possibile aggiungere un tag di ambito a un profilo di provisioning di un'app iOS in modo che solo gli utenti al cui ruolo è già assegnato tale tag abbiano accesso al profilo di provisioning dell'app iOS. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Tag di ambito per i criteri di configurazione delle app <!--2371891   -->
È possibile aggiungere un tag di ambito a un criterio di configurazione di un'app in modo che solo gli utenti al cui ruolo è già assegnato tale tag abbiano accesso al profilo di configurazione dell'app. I criteri di configurazione delle app possono solo essere destinati o associati alle app a cui è stato assegnato lo stesso tag di ambito. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Supporto Microsoft Edge per gli scenari di Intune nei dispositivi iOS e Android <!-- 3411007 -->
Microsoft Edge supporterà tutti gli stessi scenari di gestione di Intune Managed Browser con l'aggiunta di miglioramenti all'esperienza utente finale. Le funzionalità aziendali di Microsoft Edge che vengono abilitate dai criteri di Intune includono doppia identità, integrazione dei criteri di protezione delle app, integrazione del proxy di applicazione di Azure e collegamenti gestiti ai Preferiti e alla home page. Per altre informazioni, vedere la sezione relativa al [supporto Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Settimana del 25 febbraio 2019

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="intune-powershell-module----951068----"></a>Modulo PowerShell di Intune <!-- 951068  -->
Il modulo PowerShell di Intune, che offre il supporto per l'API di Intune attraverso Microsoft Graph, è ora disponibile in [Microsoft PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Informazioni dettagliate sull'uso del modulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Esempi di scenari per l'uso del modulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Supporto migliorato per l'ottimizzazione recapito  <!--3183757  -->
È stato esteso il supporto in Intune per la configurazione dell'ottimizzazione recapito. È ora possibile configurare un elenco esteso di [impostazioni di Ottimizzazione recapito](../configuration/delivery-optimization-settings.md) per i dispositivi in uso direttamente dalla console di Intune.


## <a name="week-of-february-18-2019"></a>Settimana del 18 febbraio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune userà le API di Google Play Protect nei dispositivi Android <!-- 2577355   -->
Alcuni amministratori IT devono affrontare un panorama BYOD in cui gli utenti finali possono finire per manomettere con jailbreak o root il proprio telefono cellulare. Questo comportamento, anche se non malintenzionato, comporta che vengano ignorati molti criteri di Intune impostati per proteggere i dati dell'organizzazione nei dispositivi degli utenti finali. Intune offre quindi il rilevamento per root e jailbreak sia per i dispositivi registrati, sia per quelli non registrati. Con questa versione, Intune introduce l'uso delle API di Google Play Protect per potenziare i controlli di rilevamento per root esistenti per i dispositivi non registrati. Anche se Google non condivide la totalità dei controlli di rilevamento per root eseguiti, queste API dovrebbero essere in grado di rilevare gli utenti che, per qualsiasi motivo, hanno manomesso con root i proprio dispositivi. I motivi possono spaziare dalla personalizzazione del dispositivo alla possibilità di ricevere i nuovi aggiornamenti del sistema operativo in dispositivi meno recenti. Sarà quindi possibile impedire a questi utenti di accedere ai dati aziendali oppure cancellare i relativi account aziendali dalle app abilitate da criteri. Per un valore aggiunto, l'amministratore IT può ora contare su diversi aggiornamenti dei report all'interno del pannello Protezione app di Intune: il report "Utenti contrassegnati" visualizza gli utenti rilevati tramite l'analisi dell'API SafetyNet di Google Play Protect e il report "Potentially Harmful Apps" (App potenzialmente dannose) visualizza le app rilevate tramite l'analisi dell'API Verify Apps di Google. Questa funzionalità è disponibile per Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informazioni sulle app Win32 disponibili nel pannello Risoluzione dei problemi <!-- 2617342   -->
Nel pannello **Risoluzione dei problemi** dell'app Intune è ora possibile raccogliere i file di log di eventuali errori di installazione di un'app Win32. Per altre informazioni sulla risoluzione dei problemi di installazione delle app, vedere [Risolvere i problemi di installazione delle app](./../apps/troubleshoot-app-install.md) e [Risolvere i problemi delle app Win32](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Dettagli sullo stato dell'app per le app iOS <!-- 3761235   -->
Sono disponibili nuovi messaggi di errore di installazione delle app relativi alle situazioni seguenti:
- Errore per le app VPP durante l'installazione in iPad condiviso
- Errore quando l'App Store è disabilitato
- Licenza VPP per l'app non trovata
- Errore di installazione delle app di sistema con il provider MDM
- Errore di installazione delle app quando il dispositivo è in modalità di dispositivo perso o in modalità tutto schermo
- Errore di installazione dell'app quando l'utente non è connesso all'App Store

In Intune selezionare **App client** > **App** > "Nome app" > **Stato dell'installazione del dispositivo**. I nuovi messaggi di errore saranno disponibili nella colonna **Dettagli stato**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nuova schermata Categorie di app nell'app Portale aziendale per Windows 10<!-- 3834780  -->
È stata aggiunta una nuova schermata denominata **Categorie di app** per migliorare l'esperienza di esplorazione e selezione delle app nel Portale aziendale per Windows 10. Gli utenti vedranno ora le proprie app ordinate in categorie, ad esempio **In evidenza**, **Istruzione** e **Produttività**. Questa modifica viene visualizzata nelle versioni del Portale aziendale 10.3.3451.0 e versioni successive. Per visualizzare la nuova schermata, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md). Per altre informazioni sulle app nel Portale aziendale, vedere [Installare e condividere app nel dispositivo](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>App di conformità di Power BI <!-- 1455231 doc-work-item -->
Accedere al data warehouse di Intune in Power BI Online usando l'app di [conformità di Intune (Data warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Con questa app di Power BI, è ora possibile accedere ai report creati in precedenza e condividerli senza alcuna configurazione e senza uscire dal Web browser. Per altre informazioni, vedere [Registro modifiche - App di conformità di Power BI](../developer/reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Gli script di PowerShell possono essere eseguiti in un host a 64 bit in dispositivi a 64 bit <!-- 1862675   -->
Quando uno script di PowerShell viene aggiunto al profilo di configurazione di un dispositivo, lo script viene sempre eseguito in modalità 32 bit, anche in sistemi operativi a 64 bit. Con questo aggiornamento, un amministratore può eseguire lo script in un host di PowerShell a 64 bit in dispositivi a 64 bit (**Configurazione del dispositivo** > **Script di PowerShell** > **Aggiungi** > **Configura** > **Esegui lo script in un host di PowerShell a 64 bit**).

Per altri dettagli sull'uso di PowerShell, vedere [Script di PowerShell in Intune](../apps/intune-management-extension.md).

Si applica a: Windows 10 e versioni successive

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>Agli utenti macOS viene chiesto di aggiornare la password <!-- 1873216 -->
Intune applica l'impostazione **ChangeAtNextAuth** nei dispositivi macOS. Questa impostazione interessa gli utenti finali e i dispositivi che hanno criteri password di conformità o profili password di restrizione dei dispositivi. Agli utenti finali viene chiesto una volta di aggiornare la password. Questo prompt viene visualizzato ogni volta che un utente esegue per la prima volta un'attività che richiede l'autenticazione, ad esempio l'accesso al dispositivo. Agli utenti può essere chiesto di aggiornare la password anche quando eseguono operazioni che richiedono privilegi amministrativi, ad esempio quando si richiede l'accesso a Keychain. 

Eventuali modifiche ai criteri password nuovi o esistenti da parte dell'amministratore comportano una nuova richiesta di aggiornamento della password agli utenti finali.

Si applica a:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>Assegnare certificati SCEP a un dispositivo macOS senza utente    <!-- 2340521    -->
È possibile assegnare certificati Simple Certificate Enrollment Protocol (SCEP) usando gli attributi del dispositivo ai dispositivi macOS, inclusi quelli senza affinità utente, e associare il profilo del certificato con profili Wi-Fi o VPN. Questa funzionalità estende il supporto già disponibile per l'[assegnazione di certificati SCEP ai dispositivi con e senza affinità utente](../protect/certificates-profile-scep.md) che eseguono Windows, iOS e Android.  Questo aggiornamento aggiunge l'opzione per selezionare un certificato di tipo *Dispositivo* quando si configura un profilo del certificato SCEP per macOS.

Si applica a: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Aggiornamento dell'interfaccia utente per l'accesso condizionale di Intune   <!-- 2432313   -->
Sono stati apportati miglioramenti all'interfaccia utente per l'accesso condizionale nella console di Intune, tra cui:
- Sostituzione del pannello *Accesso condizionale* di Intune con il pannello di Azure Active Directory. Ciò consente di accedere alla gamma completa di impostazioni e configurazioni per l'[accesso condizionale](../protect/conditional-access.md) (che rimane una tecnologia di Azure AD) direttamente dalla console di Intune. 
- Ridenominazione del pannello *Accesso locale* in *Accesso ad Exchange* e ricollocamento della configurazione del *connettore del servizio Exchange* in questo pannello rinominato.  Questa modifica consolida l'area in cui si [configurano e monitorano i dettagli relativi a Exchange Online e locale](../protect/exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Le app browser in modalità tutto schermo e browser Microsoft Edge possono essere eseguite nei dispositivi Windows 10 in modalità tutto schermo <!-- 2935135   -->
È possibile usare dispositivi Windows 10 in modalità tutto schermo per eseguire una o più app. Questo aggiornamento include diverse modifiche all'uso delle app browser in modalità tutto schermo, tra cui:

- Aggiunta del browser Microsoft Edge o del browser in modalità tutto schermo per l'esecuzione come app nel dispositivo in modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **Windows 10 e versioni successive** per la piattaforma > **Modalità tutto schermo** per il tipo di profilo).
- Sono disponibili nuove funzionalità e impostazioni che è possibile consentire o limitare (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo), tra cui:

- Browser Microsoft Edge:
  - Usa la modalità tutto schermo di Microsoft Edge
  - Aggiorna il browser dopo il tempo di inattività

- Preferiti e ricerca:
  - Consenti modifiche al motore di ricerca

Per un elenco di queste impostazioni, vedere:

- [Impostazioni dei dispositivi Windows 10 e versioni successive per l'esecuzione in modalità tutto schermo](../configuration/kiosk-settings-windows.md)
- [Limitazioni del dispositivo per il browser Microsoft Edge](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [Limitazioni del dispositivo per Preferiti e ricerca](../configuration/device-restrictions-windows-10.md##favorites-and-search)

Si applica a: Windows 10 e versioni successive

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Nuove impostazioni relative alle restrizioni dei dispositivi per dispositivi iOS e macOS <!-- 3448774   -->
Nei dispositivi che eseguono iOS e macOS è possibile limitare alcune impostazioni e funzionalità (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** o **macOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento aggiunge altre funzionalità e impostazioni che è possibile controllare, tra cui l'impostazione dell'orario dello schermo, la modifica delle impostazioni dell'eSIM e dei piani per telefoni cellulari e altro ancora nei dispositivi iOS. Sono inoltre disponibili le funzionalità di ritardo della visibilità degli aggiornamenti software da parte dell'utente e di blocco della memorizzazione di contenuti nella cache nei dispositivi macOS. 

Per conoscere le funzionalità e le impostazioni che è possibile limitare, vedere:

- [Impostazioni relative alle restrizioni per i dispositivi iOS](../configuration/device-restrictions-ios.md)
- [Impostazioni relative alle restrizioni per i dispositivi macOS](../configuration/device-restrictions-macos.md)

Si applica a:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>I dispositivi "in modalità tutto schermo" sono ora chiamati "dispositivi dedicati" nei dispositivi Android Enterprise <!-- 3598402   -->
Per allinearsi con la terminologia di Android, la definizione **in modalità tutto schermo** viene cambiata in **dispositivi dedicati** per i dispositivi Android Enterprise (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > ** Android Enterprise per la piattaforma > **Solo proprietario del dispositivo** > **Limitazioni del dispositivo** > **Dispositivi dedicati**).

Per visualizzare le impostazioni disponibili, passare a [Impostazioni dei dispositivi per consentire o limitare l'uso delle funzionalità](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Si applica a:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Le impostazioni iOS per Safari e il ritardo della visibilità degli aggiornamenti software per l'utente passano all'interfaccia utente di Intune <!-- 3640850, 3803313   -->
Per i dispositivi iOS è possibile configurare le impostazioni di Safari e gli aggiornamenti software. In questo aggiornamento le impostazioni sono state spostate in diverse parti dell'interfaccia utente di Intune:

- Le impostazioni di Safari sono passate da **Safari** (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo) in **[App predefinite](../configuration/device-restrictions-ios.md#built-in-apps)** .
- L'impostazione relativa al **ritardo della visibilità degli aggiornamenti software per l'utente per i dispositivi iOS con supervisione** (**Aggiornamenti software** > **Criteri di aggiornamento per iOS**) passa in **Limitazioni del dispositivo** >  **[Generale](../configuration/device-restrictions-ios.md#general)** .  Per informazioni dettagliate sull'impatto sui criteri esistenti, vedere l'articolo sugli [aggiornamenti software iOS](../protect/software-updates-ios.md#configure-the-policy). 

Per un elenco di impostazioni, vedere:

- [Restrizioni dei dispositivi iOS](../configuration/device-restrictions-ios.md) 
- [Aggiornamenti software iOS](../protect/software-updates-ios.md)

Questa funzionalità si applica a: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>L'abilitazione delle restrizioni nelle impostazioni del dispositivo è stata rinominata in Orario schermo nei dispositivi iOS <!-- 3699164   -->
È possibile configurare **Abilitazione delle restrizioni nelle impostazioni del dispositivo** nei dispositivi iOS con supervisione (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Generale**). In questo aggiornamento l'impostazione è stata rinominata in **Orario schermo (solo con supervisione)** . 

Il comportamento è lo stesso. In particolare: 

- iOS 11.4.1 e versioni precedenti: **Blocca** impedisce agli utenti finali di impostare le proprie restrizioni nelle impostazioni del dispositivo. 
- iOS 12.0 e versioni successive: **Blocca** impedisce agli utenti finali di impostare il proprio **Orario schermo** nelle impostazioni del dispositivo, incluse le restrizioni relative al contenuto e alla privacy. Nei dispositivi aggiornati a iOS 12.0 la scheda Restrizioni non sarà più visibile nelle impostazioni del dispositivo. Queste impostazioni sono in **Orario schermo**. 

Per un elenco delle impostazioni, vedere l'articolo sulle [restrizioni dei dispositivi iOS](../configuration/device-restrictions-ios.md#general).

Si applica a: 
- iOS


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Rinominare un dispositivo Windows registrato <!-- 1911112  -->
È ora possibile rinominare un dispositivo Windows 10 (RS4 o versione successiva) registrato. A tale scopo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Rinomina dispositivo**. Questa funzionalità non supporta attualmente la ridenominazione di dispositivi Windows di Azure AD ibridi.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Assegnare automaticamente tag di ambito alle risorse create da un amministratore con quell'ambito <!-- 3173823  -->
Quando un amministratore crea una risorsa, i tag di ambito assegnati all'amministratore verranno automaticamente assegnati alle nuove risorse.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Il report delle registrazioni non riuscite passa al pannello Registrazione del dispositivo <!-- 3560202  -->
Il report delle **registrazioni non riuscite** è passato alla sezione **Monitoraggio** del pannello **Registrazione del dispositivo**. Sono state aggiunte due nuove colonne: Metodo di registrazione e Versione sistema operativo.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Il report Abbandono del Portale aziendale è stato rinominato Registrazioni utente incomplete <!--3815076 eemiss -->
Il report **Abbandono del Portale aziendale** è stato rinominato **Registrazioni utente incomplete**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Settimana del 4 febbraio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Modalità scura del Portale aziendale Intune per macOS <!-- 3300524  -->
Il portale aziendale Intune ora supporta la modalità scura per macOS. Quando si abilita la modalità scura in un dispositivo macOS 10.14 o versione successiva, il Portale aziendale regola i colori in modo da riflettere tale modalità.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Settimana del 21 gennaio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifiche di tipo avviso popup per app Win32 <!-- 3136566   -->
È possibile eliminare la visualizzazione delle notifiche di tipo avviso popup degli utenti finali per ogni assegnazione di app. In Intune selezionare **App client** > **App** > selezionare l'app > **Assegnazioni** > **Includi gruppi**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Aggiornamento dell'interfaccia utente dei criteri di Protezione app di Intune <!-- 3251427  -->
Sono state modificate le etichette per le impostazioni e i pulsanti per la protezione delle app di Intune per rendere tutto più comprensibile. Alcune delle modifiche includono:  
- I controlli sono cambiati da **sì** / **no** principalmente a **blocca** / **consenti** e **disabilita** / **abilita**. Anche le etichette sono state aggiornate.  
- Le impostazioni sono state riformattate, in modo che l'impostazione e la relativa etichetta siano affiancate nel controllo, consentendo spostamenti più efficienti.   

Le impostazioni predefinite e il numero di impostazioni rimangono uguali, ma questa modifica consente all'utente di comprendere, esplorare e utilizzare le impostazioni più facilmente per applicare i criteri di protezione delle app selezionati. Per informazioni, vedere le [impostazioni iOS](../apps/app-protection-policy-settings-ios.md) e le [impostazioni Android](../apps/app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Impostazioni aggiuntive per Outlook <!-- 3301182  -->
Ora è possibile configurare le impostazioni aggiuntive seguenti per Outlook per iOS e Android usando Intune:

- Consentire solo agli account aziendali o dell'istituto di istruzione di essere usati in Outlook su iOS o Android
- Distribuire gli account locali dell'autenticazione moderna per Office 365 e dell'autenticazione moderna ibrida
- Usare `SAMAccountName` per il campo nome utente nel profilo di posta elettronica quando è selezionata l'autenticazione di base
- Consentire di salvare i contatti
- Configurare i suggerimenti di posta elettronica per i destinatari esterni
- Configurare **Posta in arrivo evidenziata**
- Richiedere alla biometria di accedere a Outlook per iOS
- Bloccare le immagini esterne

> [!NOTE]
> Se si usano i criteri di protezione delle app di Intune per gestire l'accesso per le identità aziendali, non abilitare **Richiedi biometria**. Per altre informazioni, vedere **Richiedi credenziali aziendali per l'accesso** per le [impostazioni di accesso iOS](../apps/app-protection-policy-settings-ios.md#access-requirements) e le [impostazioni di accesso Android](../apps/app-protection-policy-settings-android.md#access-requirements).

Per altre informazioni, vedere [Impostazioni di configurazione di Microsoft Outlook](../apps/app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Eliminare app Android Enterprise <!-- 1352553 -->
È possibile eliminare da Microsoft Intune le app di Google Play gestite. Per eliminare un'app di Google Play gestita, aprire Microsoft Intune nel portale di Azure e selezionare **App client** > **App**. Nell'elenco di app selezionare i puntini di sospensione (...) a destra dell'app di Google Play gestita e quindi selezionare **Elimina** nell'elenco visualizzato. Quando si elimina un'app di Google Play gestita dall'elenco di app, l'app risulta automaticamente non approvata.

#### <a name="managed-google-play-app-type----1352580---"></a>Tipo di app Google Play gestito <!-- 1352580 -->
Il tipo di app **Google Play gestito** consentirà di aggiungere in modo specifico [app Google Play gestite](https://play.google.com/work/search?q=microsoft&c=apps) a Intune. Un amministratore di Intune può ora esplorare, cercare, approvare, sincronizzare e assegnare in Intune app di Google Play gestite approvate.  Non sarà più necessario passare alla console di Google Play separatamente e rieseguire l'autenticazione.  In Intune selezionare **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di App** selezionare **Google Play gestito** come tipo di app.

### <a name="default-android-pin-keyboard----3802457---"></a>Tastiera PIN predefinita in Android <!-- 3802457 -->
Gli utenti finali che hanno impostato un PIN di tipo 'Numerico' dei criteri di protezione delle app in Intune sui loro dispositivi Android visualizzeranno ora la tastiera Android predefinita invece dell'interfaccia utente della tastiera Android fissa progettata in precedenza. Questa modifica è stata apportata per coerenza quando si usano tastiere predefinite in Android e iOS, per entrambi i tipi PIN di 'Numerico' e/o 'Passcode'. Per altre informazioni sulle impostazioni di accesso degli utenti finali in Android, ad esempio il PIN dei criteri di protezione delle app, vedere la sezione relativa ai [requisiti di accesso Android](../apps/app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Usare le impostazioni consigliate da Microsoft con le baseline di sicurezza (anteprima pubblica) <!-- 2055484   -->

Intune si integra con altri servizi specifici per la sicurezza, inclusi Windows Defender ATP e Office 365 ATP. I clienti manifestano l'esigenza di una strategia comune e di un set integrato di flussi di lavoro di sicurezza end-to-end nei servizi di Microsoft 365. L'obiettivo è l'allineamento delle strategie per creare soluzioni in grado di conciliare le operazioni di sicurezza e le comuni attività degli amministratori. Per realizzare questo obiettivo in Intune, è stato pubblicato un set di "baseline di sicurezza" consigliate da Microsoft (**Intune** > **Baseline di sicurezza**).  Un amministratore può creare criteri di sicurezza direttamente da queste baseline e quindi distribuirle agli utenti. È anche possibile personalizzare le raccomandazioni per le procedure consigliate in modo soddisfare le specifiche esigenze dell'organizzazione. Intune verifica che i dispositivi rimangano conformi a queste baseline e invia agli amministratori una notifica sugli utenti e i dispositivi non conformi.

Questa funzionalità è disponibile in anteprima pubblica, perciò i profili di nuova creazione non verranno spostati nei modelli di baseline di sicurezza disponibili a livello generale. Non è consigliabile usare questi modelli di anteprima nell'ambiente di produzione.

Per altre informazioni sulle baseline di sicurezza, vedere [Creare una baseline di sicurezza di Windows 10 in Intune](../protect/security-baselines-monitor.md).

Questa funzionalità si applica a: Windows 10 e versioni successive

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>I non amministratori possono abilitare BitLocker nei dispositivi Windows 10 aggiunti ad Azure AD<!-- 2147379   -->
Quando si abilitano le impostazioni di BitLocker nei dispositivi Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo**  >  **Windows 10 e versioni successive** per la piattaforma > **Endpoint Protection** per il tipo di profilo > **Crittografia Windows**), si aggiungono impostazioni BitLocker. 

Questo aggiornamento include una nuova impostazione di BitLocker per consentire agli utenti standard (non amministratori) di abilitare la crittografia. 

Per visualizzare queste impostazioni, vedere [Impostazioni di Endpoint Protection per Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Verificare la conformità di Configuration Manager <!-- 2192052  eepublished  -->
Questo aggiornamento include una nuova impostazione di conformità di System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10 e versioni successive** > **Conformità di Configuration Manager**). Configuration Manager invia segnali per la conformità di Intune. Usando questa impostazione è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Questa impostazione è descritta in [Conformità di Configuration Manager](../protect/compliance-policy-create-windows.md#configuration-manager-compliance).

Si applica a: Windows 10 e versioni successive

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalizzare lo sfondo nei dispositivi iOS con supervisione con un profilo di configurazione del dispositivo <!-- 2809324   -->
Quando si crea un profilo di configurazione del dispositivo per i dispositivi iOS, è possibile personalizzare alcune funzionalità (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni di **Sfondo** che consentono a un amministratore di usare un'immagine PNG, JPG o JPEG nella schermata iniziale o nella schermata di blocco. Queste impostazioni dello sfondo si applicano solo ai dispositivi con supervisione. 

Per un elenco di queste impostazioni, vedere [Impostazioni relative alle funzionalità dei dispositivi iOS in Intune](../configuration/ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Modalità a tutto schermo di Windows 10 disponibile a livello generale <!-- 3594661  -->
In questo aggiornamento, la funzionalità Modalità tutto schermo in Windows 10 e versioni successive è disponibile a livello generale. Per informazioni su tutte le impostazioni che è possibile aggiungere e configurare, vedere le [impostazioni della modalità tutto schermo per Windows 10 (e versioni successive)](../configuration/kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>La Condivisione dei contatti tramite Bluetooth viene rimossa in Limitazioni del dispositivo > Proprietario dispositivo per Android Enterprise <!-- 3598396   -->
Quando si crea un profilo di limitazione per i dispositivi Android Enterprise, è disponibile un'impostazione **Condivisione dei contatti tramite Bluetooth**. In questo aggiornamento viene rimossa l'impostazione **Condivisione dei contatti tramite Bluetooth** (**Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo > Proprietario dispositivo** per il tipo di profilo > **Generale**). 

L'impostazione **Condivisione contatti tramite Bluetooth** non è supportata per la gestione dei proprietari di dispositivi Android Enterprise. Pertanto, la rimozione di questa impostazione non influisce su alcun dispositivo o tenant, anche se l'impostazione è abilitata e configurata nell'ambiente in uso.

Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a: Proprietario dispositivo Android Enterprise

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Supporto di cancellazione selettiva per dispositivi WIP senza registrazione <!-- 1434452 -->
Windows Information Protection senza registrazione (WIP-WE, Windows Information Protection Without Enrollment) consente ai clienti di proteggere i dati aziendali nei dispositivi Windows 10 senza la necessità di una registrazione MDM (Mobile Device Management, gestione di dispositivi mobili) completa. Quando i documenti sono protetti da criteri WIP-WE, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, si rendono inutilizzabili tutti i dati protetti tramite criteri WIP-WE. Da Intune nel portale di Azure selezionare **App per dispositivi mobili** > **Cancellazione selettiva di app**.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nuovi log operativi e possibilità di inviare i log ai servizi di Monitoraggio di Azure <!-- 3762211  -->
Intune include una funzionalità di registrazione di controllo predefinita che consente di tenere traccia degli eventi quando vengono apportate modifiche. Questo aggiornamento include nuove funzionalità di registrazione, tra cui: 
- Log operativi (anteprima) che mostrano informazioni dettagliate su utenti e dispositivi registrati, tra cui operazioni riuscite e non riuscite.
- I log di controllo e i log operativi possono essere inviati a Monitoraggio di Azure, inclusi account di archiviazione, hub eventi e Log Analytics. Questi servizi consentono di archiviare, usare funzionalità di analisi come QRadar e Splunk, nonché ottenere visualizzazioni dei dati di registrazione.

In [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics in Intune (anteprima)](../review-logs-using-azure-monitor.md) sono disponibili altre informazioni su questa funzionalità.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorare altre schermate di Assistente configurazione in un dispositivo DEP iOS <!-- 2687509  -->
Oltre alle schermate che è attualmente possibile ignorare, è possibile impostare i dispositivi DEP iOS in modo che ignorino le schermate seguenti nell'Assistente configurazione quando un utente registra il dispositivo: Segnale schermo, Privacy, Migrazione di Android, Pulsante Pagina iniziale, iMessage e FaceTime, Onboarding, Migrazione di Watch, Aspetto, Orario schermo, Aggiornamento software, Configurazione SIM.
Per scegliere le schermate da ignorare, passare a **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > scegliere un token > **Profili** > scegliere un profilo > **Proprietà** > **Personalizzazione dell'Assistente configurazione** > scegliere **Nascondi** per tutte le schermate che si vuole ignorare > **OK**.
Se si crea un nuovo profilo o si modifica un profilo, le schermate da ignorare selezionate devono essere sincronizzate con il server MDM di Apple. Gli utenti possono eseguire una sincronizzazione manuale dei dispositivi in modo da evitare ritardi nell'aggiornamento delle modifiche del profilo.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Distribuzione di app Android Enterprise APP-WE <!-- 1171203 -->
Per i dispositivi Android in uno scenario di distribuzione APP-WE (App Protection Policy Without Enrollment) non registrato, è ora possibile usare Google Play gestito per distribuire app dello Store e app LOB agli utenti. In particolare, è possibile offrire agli utenti finali un catalogo di app e un'esperienza di installazione che non richiede più agli utenti finali di ridurre il comportamento di sicurezza dei propri dispositivi consentendo installazioni da origini sconosciute. Inoltre, questo scenario di distribuzione fornirà un'esperienza migliorata per gli utenti finali.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Settimana del 14 gennaio 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Anteprima del supporto per i dispositivi aziendali Android completamente gestiti <!-- 1574342  -->
Intune ora supporta i dispositivi Android completamente gestiti, ovvero uno scenario con dispositivi di proprietà aziendale gestiti rigorosamente dal reparto IT e associati a singoli utenti. Ciò consente agli amministratori di gestire l'intero dispositivo, imporre un'ampia gamma di controlli dei criteri non disponibili per i profili di lavoro e limitare gli utenti all'installazione di app solo da Google Play gestito. Per altre informazioni, vedere [Set up Intune enrollment of Android fully managed devices](../enrollment/android-fully-managed-enroll.md) (Configurare la registrazione in Intune dei dispositivi Android completamente gestiti) ed [Enroll your dedicated devices or fully managed devices](../enrollment/android-dedicated-devices-fully-managed-enroll.md) (Registrare i dispositivi dedicati o i dispositivi completamente gestiti).  Si noti che questa funzionalità è disponibile in anteprima. Alcune funzionalità di Intune, come ad esempio i certificati, la conformità e l'accesso condizionale, non sono attualmente disponibili con i dispositivi utente Android completamente gestiti.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Settimana del 7 gennaio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-app-pin----2298397---"></a>PIN dell'app Intune <!-- 2298397 -->
Ora l'amministratore IT può configurare il numero di giorni di attesa per un utente finale prima che debba modificare il PIN dell'app Intune. La nuova impostazione è *PIN reset after number of days* (Reimpostazione PIN dopo numero di giorni) ed è disponibile nel portale di Azure selezionando **Intune** > **App client** > **Criteri di protezione delle app** > **Crea criterio** > **Impostazioni** > **Requisiti di accesso**. Disponibile per dispositivi [iOS](../apps/app-protection-policy-settings-ios.md) e [Android](../apps/app-protection-policy-settings-android.md), questa funzionalità supporta un numero intero positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campi per i report relativi ai dispositivi di Intune <!-- 2748738 -->
Intune offre campi aggiuntivi per i report relativi ai dispositivi, tra cui ID di registrazione app, produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. In Intune questi campi sono disponibili selezionando **App client** > **Stato protezione app** e scegliendo **Report sulla protezione dell'app: iOS, Android**. Inoltre, questi parametri consentiranno di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della versione minima della patch di sicurezza Android. 


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>I modelli amministrativi sono disponibili in anteprima pubblica e sono stati spostati nel profilo di configurazione corrispondente <!-- 3322847 -->

I modelli amministrativi in Intune (**Configurazione del dispositivo** > **Modelli amministrativi**) sono attualmente disponibili in anteprima pubblica. Con questo aggiornamento:

- i modelli amministrativi includono circa 300 impostazioni che possono essere gestite in Intune. In precedenza, queste impostazioni erano disponibili solo in Editor Criteri di gruppo.
- I modelli amministrativi sono disponibili in anteprima pubblica.
- I modelli amministrativi vengono spostati da **Configurazione del dispositivo** > **Modelli amministrativi** a **Configurazione del dispositivo** > **Profili** > **Crea profilo** > in **Piattaforma** scegliere  **Windows 10 e versioni successive** > in **Tipo di profilo** scegliere **Modelli amministrativi**.
- La creazione di report è abilitata

Per altre informazioni su questa funzionalità, vedere [Modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune](../configuration/administrative-templates-windows.md).

Si applica a: Windows 10 e versioni successive

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Usare S/MIME per crittografare e firmare più dispositivi per un utente  <!-- 1333642 -->
Questo aggiornamento include una crittografia di posta elettronica S/MIME con un nuovo profilo di certificato importato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > selezionare la piattaforma > tipo di profilo **Certificato PKCS importato**). In Intune è possibile importare i certificati nel formato PFX. Intune può quindi distribuire i certificati a più dispositivi registrati da un singolo utente. Inoltre:
- Il profilo di posta elettronica iOS nativo supporta l'abilitazione della crittografia S/MIME mediante certificati importati in formato PFX.
- L'app di posta elettronica nativa nei dispositivi Windows Phone 10 usa automaticamente il certificato S/MIME.
- I certificati privati possono essere recapitati su più piattaforme. Tuttavia, non tutte le app di posta elettronica supportano S/MIME.
- In altre piattaforme potrebbe essere necessario configurare manualmente l'app di posta elettronica per abilitare S/MIME.  
- È possibile che le app di posta elettronica che supportano la crittografia S/MIME gestiscano il recupero dei certificati per la crittografia della posta elettronica S/MIME in un modo non supportato dal software MDM, ad esempio basandosi sull'archivio certificati del server di pubblicazione.
Per altre informazioni su questa funzionalità, vedere [Firma e crittografia S/MIME della posta elettronica in Intune](../protect/certificates-s-mime-encryption-sign.md).
Supportato in: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nuove opzioni per la connessione automatica e per rendere persistenti le regole quando si usano le impostazioni DNS in dispositivi con Windows 10 e versioni successive <!-- 1333665, 2999078 -->
Nei dispositivi con Windows 10 e versioni successive è possibile creare un profilo di configurazione VPN che include un elenco dei server DNS per risolvere i domini, ad esempio contoso.com. Questo aggiornamento include nuove impostazioni per la risoluzione dei nomi (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Windows 10 e versioni successive** per la piattaforma > scegliere **VPN** per il tipo di profilo > **Impostazioni DNS** >**Aggiungi**): 
- **Connetti automaticamente**: con l'impostazione **Abilitato**, il dispositivo si connette automaticamente alla rete VPN quando un dispositivo contatta un dominio immesso, ad esempio contoso.com.
- **Persistente**: per impostazione predefinita, tutte le regole della tabella dei criteri di risoluzione dei nomi di criteri (NRPT) sono attive, purché il dispositivo sia connesso con questo profilo VPN. Quando questa impostazione è **Abilitata** per una regola NRPT, la regola rimane attiva nel dispositivo, anche in caso di disconnessione della rete VPN. La regola rimane fino alla rimozione del profilo VPN o fino alla rimozione manuale della regola, che può essere eseguita tramite PowerShell.
[Impostazioni VPN di Windows 10](../configuration/vpn-settings-windows-10.md) descrive le impostazioni. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Usare il rilevamento delle reti attendibili per i profili VPN nei dispositivi Windows 10 <!-- 1500165 -->
Quando si usa il rilevamento delle reti attendibili, è possibile impedire ai profili VPN di creare automaticamente una connessione VPN quando l'utente è già in una rete attendibile. Con questo aggiornamento è possibile aggiungere suffissi DNS per abilitare il rilevamento delle reti attendibili nei dispositivi che eseguono Windows 10 e versioni successive (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **VPN** per il tipo di profilo).
In [Impostazioni VPN di Windows 10](../configuration/vpn-settings-windows-10.md) sono elencate le impostazioni VPN correnti.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gestione di dispositivi Windows Holographic for Business usati da più utenti <!-- 1907917, 1063203 -->
Attualmente è possibile configurare le impostazioni del PC condiviso nei dispositivi Windows 10 e Windows Holographic for Business usando un'impostazione OMA-URI personalizzata. Con questo aggiornamento viene aggiunto un nuovo profilo per configurare le impostazioni del PC condiviso: **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Dispositivo multiutente condiviso**.
Per altre informazioni su questa funzionalità, vedere [Controllare l'accesso, gli account e le funzionalità di risparmio energia nei PC condivisi o nei dispositivi multiutente con Intune](../configuration/shared-user-device-settings.md).
Si applica a: Windows 10 e versioni successive, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nuove impostazioni per gli aggiornamenti di Windows 10 <!--2626030  2512994  -->
Per gli [anelli di aggiornamento Windows 10](../protect/windows-update-for-business-configure.md) è possibile configurare:
- **Comportamento di aggiornamento automatico**: usare la nuova opzione *Ripristina impostazione predefinita* per ripristinare le impostazioni di aggiornamento automatico originali nei computer Windows 10 che eseguono l'*aggiornamento di ottobre 2018*
- *Impedisci all'utente di sospendere gli aggiornamenti Windows*: consente di configurare una nuova impostazione per gli aggiornamenti software che impedisce o permette agli utenti di sospendere l'installazione degli aggiornamenti da **Impostazioni** nei loro computer. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>I profili di posta elettronica iOS possono usare firma e crittografia S/MIME <!-- 2662949 -->
È possibile creare un profilo di posta elettronica che include impostazioni diverse. Questo aggiornamento include le impostazioni di S/MIME che possono essere usate per firmare e crittografare le comunicazioni tramite posta elettronica nei dispositivi iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **iOS** per la piattaforma > **Posta elettronica** per il tipo di profilo).
Le impostazioni sono elencate in [Impostazioni del profilo di posta elettronica per dispositivi iOS](../configuration/email-settings-ios.md).

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Alcune impostazioni di BitLocker supportano l'edizione Windows 10 Pro<!-- 2727036 -->
È possibile creare un profilo di configurazione che imposta le impostazioni di Endpoint Protection nei dispositivi Windows 10, incluso BitLocker. Questo aggiornamento aggiunge il supporto per l'edizione Windows 10 Professional per alcune impostazioni di BitLocker. Per visualizzare queste impostazioni, vedere [Impostazioni di Endpoint Protection per Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>L'impostazione Configurazione del dispositivo condiviso è stata rinominata Messaggio della schermata di blocco per i dispositivi iOS nel portale di Azure<!-- 2809362 -->
Quando si crea un profilo di configurazione per i dispositivi iOS, è possibile aggiungere le impostazioni **Configurazione del dispositivo condiviso** per visualizzare testo specifico nella schermata di blocco. Questo aggiornamento include le modifiche seguenti: 
- L'impostazione **Configurazione del dispositivo condiviso** nel portale di Azure è stata rinominata "Lock Screen Message (supervised only)" (Messaggio della schermata di blocco - solo con supervisione): **Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > scegliere **iOS** per la piattaforma > scegliere **Funzionalità del dispositivo** per il tipo di profilo > **Lock Screen Message** (Messaggio della schermata di blocco).
- Quando si aggiungono messaggi della schermata di blocco, è possibile inserire un numero di serie, un nome di dispositivo o un altro valore specifico del dispositivo come variabile in **Informazioni sui tag asset** e **Nota a piè di pagina della schermata di blocco**. Ad esempio, è possibile immettere `Device name: {{devicename}}` o `Serial number is {{serialnumber}}` usando parentesi graffe. In [Token iOS](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) sono elencati i token disponibili che possono essere usati.
Le impostazioni sono elencate in [Aggiungere messaggi personalizzati alla schermata di blocco e alla finestra di accesso nei dispositivi iOS con Microsoft Intune](../configuration/ios-device-features-settings.md#lock-screen-message).

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nuove impostazioni di limitazione dei dispositivi App Store, visualizzazione documenti, giochi aggiunte ai dispositivi iOS <!-- 2827760-->
In **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi** sono state aggiunte le impostazioni seguenti: Allow managed apps to write contacts to unmanaged contacts accounts (Consenti alle app gestite di scrivere contatti in account di contatti non gestiti), Allow unmanaged apps to read from managed contacts accounts (Consenti alle app non gestite di leggere da account di contatti gestiti). Per vedere queste impostazioni, consultare le [limitazioni per i dispositivi iOS](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nuove impostazioni di notifica, hint e protezione della tastiera per i dispositivi Android Enterprise in modalità proprietario del dispositivo <!-- 3201839 3201843 -->
Questo aggiornamento include numerose nuove funzionalità per i dispositivi aziendali Android quando vengono eseguiti come proprietario del dispositivo. Per usare queste funzionalità, passare a **Configurazione del dispositivo** > **Profili** > **Crea profilo** > in **Piattaforma**, scegliere **Android Enterprise** > in **Tipo di profilo**, scegliere **Solo proprietario del dispositivo** > **Limitazioni del dispositivo**.

Le nuove funzionalità includono: 

- Disabilitare la visualizzazione delle notifiche di sistema, incluse chiamate in ingresso, avvisi di sistema, errori di sistema e altro.
- Suggerimenti per ignorare le esercitazioni e i consigli iniziali per le app aperte per la prima volta.
- Disabilitare le impostazioni avanzate di protezione della tastiera, ad esempio fotocamera, notifiche, sblocco tramite impronta digitale e altro.


Per visualizzare le impostazioni, passare a [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>I dispositivi Android Enterprise in modalità proprietario del dispositivo possono usare le connessioni VPN sempre attive <!-- 3202194 -->
In questo aggiornamento è possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise in modalità proprietario del dispositivo. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
È possibile abilitare le connessioni VPN sempre attive in **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo** per Solo proprietario del dispositivo > **Connettività**. Per visualizzare le impostazioni, passare a [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nuova impostazione per terminare i processi in Gestione attività nei dispositivi Windows 10 <!-- 3285177 --> 
Questo aggiornamento include una nuova impostazione per terminare i processi usando Gestione attività nei dispositivi Windows 10. Scegliere se consentire o non consentire questa impostazione usando un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > In **Piattaforma** scegliere **Windows 10** > in **Tipo di profilo** scegliere **Limitazioni del dispositivo** > **Generale**).
Per visualizzare queste impostazioni, vedere [Impostazioni relative alle limitazioni per i dispositivi Windows 10 e versioni successive in Microsoft Intune](../configuration/device-restrictions-windows-10.md).
Si applica a: Windows 10 e versioni successive

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Messaggi di errore più dettagliati per le restrizioni di registrazione <!-- 3111564 -->
Sono disponibili messaggi di errore più dettagliati quando non vengono soddisfatte le restrizioni di registrazione. Per visualizzare questi messaggi, passare a **Intune** > **Risoluzione dei problemi** e selezionare la tabella Errori di registrazione. Per altre informazioni, vedere l'[elenco degli errori di registrazione](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="tenant-status-dashboard-----1124854---"></a>Dashboard Stato del tenant  <!-- 1124854 -->
La nuova pagina [Stato del tenant](tenant-status.md) offre una posizione centralizzata in cui visualizzare lo stato del tenant e le informazioni dettagliate correlate.  Il dashboard è suddiviso in quattro aree:
- **Dettagli del tenant**: visualizza informazioni su nome e posizione del tenant, autorità MDM, totale dei dispositivi registrati nel tenant e numero di licenze. Questa sezione indica anche la versione corrente del servizio per il tenant.
- **Stato del connettore**: visualizza informazioni sui connettori disponibili configurati e può elencare anche quelli non ancora abilitati.  
   In base allo stato corrente di ogni connettore, i connettori vengono contrassegnati come Integro, Avviso o Non integro. Selezionare un connettore per eseguire il drill-through e visualizzarne i dettagli oppure per configurare informazioni aggiuntive.
- **Integrità del servizio Intune**: visualizza informazioni dettagliate sugli eventi imprevisti attivi o le interruzioni del tenant. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office.
- **Novità su Intune**: visualizza i messaggi attivi per il tenant, ad esempio le notifiche inviate quando il tenant riceve le funzionalità di Intune più recenti.  Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nuova esperienza di Guida e supporto tecnico nel Portale aziendale per Windows 10 <!-- 1488939-->
La nuova pagina Guida e supporto del Portale aziendale aiuta gli utenti a risolvere i problemi e a richiedere assistenza in merito ai problemi di accesso e relativi alle app. Da questa nuova pagina gli utenti possono inviare tramite posta elettronica i dettagli dei log degli errori e di diagnostica e possono trovare le informazioni dettagliate sul supporto tecnico della loro organizzazione. Troveranno anche una sezione di domande frequenti con collegamenti alla documentazione di Intune pertinente. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nuova esperienza di Guida e supporto tecnico per Intune   <!-- #3307080 -->
Nei prossimi giorni la nuova esperienza di Guida e supporto tecnico verrà distribuita in tutti i tenant. Questa nuova esperienza è disponibile per Intune ed è accessibile dai pannelli di Intune nel [portale di Azure](https://portal.azure.com/).
La nuova esperienza consente di descrivere il problema con parole proprie e di ricevere informazioni dettagliate per la risoluzione dei problemi e contenuti Web per la correzione. Queste soluzioni sono offerte tramite un algoritmo di apprendimento automatico basato su regole, creato in base alle indagini condotte tra gli utenti. Oltre alle indicazioni specifiche per il problema, è possibile usare il nuovo flusso di lavoro di creazione di un caso per aprire un caso di supporto tramite posta elettronica o telefono. Questa nuova esperienza sostituisce l'esperienza di Guida e supporto tecnico precedente basata su un set statico di opzioni preselezionate a seconda dell'area della console in cui ci si trova quando si apre Guida e supporto. Per altre informazioni, vedere [Come ottenere supporto per Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-for-apps----1081941---"></a>Tag di ambito per le app <!-- 1081941 -->
È possibile creare tag di ambito per limitare l'accesso per ruoli e app. È possibile aggiungere un tag di ambito a un'app in modo che solo le persone al cui ruolo è già assegnato tale tag abbiano accesso all'app. Al momento non è possibile assegnare i tag di ambito alle app aggiunte a Intune da Google Play gestito o alle app acquistate tramite Volume Purchase Program di Apple, ma questo supporto è previsto per il futuro. Per altre informazioni, vedere [Usare i tag di ambito per filtrare i criteri](scope-tags.md).

## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
