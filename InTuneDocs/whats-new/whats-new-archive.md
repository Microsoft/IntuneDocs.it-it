---
title: "Archivio novità | Microsoft Intune"
description: "Annunci archiviati delle novità per Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa8fe81b6a9f6b11bba9c15ede36d9df9cd2e0da
ms.openlocfilehash: 72a2f8026d1a67a3a49111daa9a7b8380b0cb088


---
# <a name="whats-new---archive"></a>Novità - Archivio

Questa pagina è un archivio degli annunci recenti pubblicati in [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).

## <a name="october-2016"></a>Ottobre 2016

### <a name="conditional-access-for-mobile-application-management"></a>Accesso condizionale per la gestione di applicazioni mobili
Sarà possibile limitare l'accesso a Exchange Online in modo che l'accesso possa essere eseguito solo da app che supportano i criteri di gestione delle applicazioni mobili di Intune, ad esempio Outlook. [Questa nuova funzionalità](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) si abbina perfettamente con i criteri di gestione delle app per dispositivi mobili di Intune perché è possibile bloccare l'accesso ai client di posta predefiniti o ad altre app che non sono state configurate con i criteri di gestione delle app per dispositivi mobili di Intune. In questo modo gli utenti accedono ai dati dell'organizzazione con app che possono essere protette con MAM Intune. Per un'introduzione alla gestione delle app per dispositivi mobili Intune, visitare il portale di Azure. Cercare la nuova sezione Accesso condizionale nel pannello "Impostazioni".

### <a name="conditional-access-for-windows-pcs"></a>Accesso condizionale per i PC Windows
È ora possibile creare criteri di accesso condizionale tramite la console di amministrazione di Intune per impedire l'accesso a [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) ai PC Windows. È inoltre possibile creare criteri di accesso condizionale per bloccare l'accesso alle applicazioni universali e desktop di Office.

### <a name="android-for-work-support"></a>Supporto di Android for Work

> [!IMPORTANT]

> Se da una parte è possibile distribuire app Android for Work con un'azione di __Richiesto__, un'app può essere distribuita solo come __Disponibile__ se i gruppi di Intune sono stati migrati alla nuova esperienza dei gruppi di Azure AD.

Intune è ora incluso nel programma Android for Work (AfW). L'implementazione del supporto delle funzionalità Android for Work sarà avviata questo mese e continuerà nei prossimi mesi. Si noti che la distribuzione dell'app disponibile di AfW sfrutta la nuova esperienza di raggruppamento e targeting. Gli account del servizio Intune sottoposti a provisioning di recente potranno usare questa funzionalità non appena AfW sarà disponibile.

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. Any questions on grouping and targeting timelines, please contact our [migration team](mailto:intunegrps@microsoft.com).-->

[Leggere l'annuncio Microsoft relativo al supporto di Android for Work in Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Gli argomenti seguenti relativi a Intune seguenti sono nuovi o aggiornati con le informazioni su Android for Work:

Per i professionisti IT:
- [Configurare Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Limitare l'accesso alla posta elettronica per Exchange Online e il nuovo ambiente Exchange Online dedicato con Intune](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Limitare l'accesso alla posta elettronica per Exchange locale e l'ambiente legacy Exchange Online dedicato con Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Impostazioni dei criteri di conformità di Android for Work](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Come distribuire le app Android for Work](/intune/deploy-use/android-for-work-apps)
- [Configurare le app Android for Work con i criteri di configurazione delle app per dispositivi mobili](/intune/deploy-use/afw-app-configuration-policy)
- [Impostazioni dei criteri di Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

Per gli utenti finali:
- [Cosa accade quando si crea un profilo di lavoro](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Creare un profilo di lavoro e registrare il dispositivo in Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>Integrazione di Lookout per proteggere i dispositivi iOS
A ottobre Microsoft prevede di integrare la soluzione di protezione dalle minacce per dispositivi mobili Lookout per proteggere i dispositivi mobili iOS grazie al rilevamento di malware, app rischiose e altro ancora. La soluzione Lookout consente di determinare il livello di minaccia, che è configurabile. È possibile creare una regola dei criteri di conformità in Intune per determinare la conformità del dispositivo in base alla valutazione del rischio da parte di Lookout. Con i criteri di accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali in base allo stato di conformità del dispositivo.

Agli utenti finali con dispositivi iOS non conformi verrà richiesto di eseguire la registrazione e di installare l'applicazione Lookout for Work, attivare l'app e correggere le minacce segnalate nell'applicazione Lookout for Work per ottenere l'accesso ai dati aziendali. Vedere le informazioni su come [Configurare e distribuire l'app Lookout for Work](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### <a name="intune-app-wrapping-tool-for-android"></a>Strumento per la disposizione testo per app di Intune
È possibile consentire alle app di usare i criteri di gestione del app per dispositivi mobili di Intune tramite lo strumento per la disposizione testo per app di Intune. È ora disponibile il supporto per i criteri di gestione delle app per dispositivi mobili di Intune che non richiede la registrazione del dispositivo.

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>Gestire la stampa dalle app gestite con criteri di gestione delle app per dispositivi mobili
Ora è possibile impedire la stampa di dati aziendali dalle app che includono criteri di gestione delle app per dispositivi mobili. Questa impostazione è disponibile nel [portale di Azure](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) ed è supportata in dispositivi [iOS](/Intune/deploy-use/ios-mam-policy-settings) e [Android](/Intune/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Supporto per le impronte digitali nei dispositivi Android
I criteri di gestione delle app mobili (MAM) per Android consentono agli utenti di accedere a un'app con l'impronta digitale invece di digitare il PIN personale. Informazioni su questa e altre [impostazioni dei criteri di gestione delle app mobili per Android sono disponibili qui](/Intune/deploy-use/android-mam-policy-settings).

### <a name="notices"></a>Notifiche

__Compatibilità di Android Samsung KNOX con Intune__ Alcuni modelli di telefoni Samsung Galaxy Ace non possono essere gestiti da Intune come dispositivi Samsung KNOX. Quando verranno registrati con Intune, questi dispositivi verranno invece gestiti come dispositivi Android standard.

I numeri di modello interessati sono:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Non sono richieste altre azioni da parte dell'amministratore o degli utenti. Per altre informazioni, visitare il sito Web [Samsung KNOX](https://www.samsungknox.com).

__L'app Portale aziendale per Windows 8 è deprecata e il supporto per le piattaforme Windows Phone 8 e Windows RT sarà deprecato__ A partire da ottobre 2016, il supporto di Microsoft Intune per il portale aziendale di Windows 8 verrà deprecato. Verrà anche deprecato il supporto di Microsoft Intune per le piattaforme Windows Phone 8 e Windows RT. Di conseguenza, non sarà possibile registrare o aggiornare dispositivi Windows Phone 8 o Windows RT.

È possibile continuare a gestire i dispositivi Windows Phone 8, Windows RT e Windows 8 che sono già registrati. Aggiornare i dispositivi Windows Phone 8 e Windows 8 a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi senza interruzioni.

A partire da novembre 2016, il supporto per il portale aziendale di Windows Phone 8 verrà deprecato.
<!--TFS 1255391-->

### <a name="whats-coming"></a>Sviluppi futuri

__Nuovo portale aziendale di Microsoft Intune disponibile per dispositivi Windows 10__ Microsoft sta rilasciando un nuovo portale aziendale di Microsoft Intune per dispositivi Windows 10. Questa app, che sfrutta il nuovo formato universale di Windows 10, offrirà un'esperienza utente aggiornata all'interno dell'app ed esperienze identiche in tutti i dispositivi Windows 10, sia PC che mobili, senza variazioni alle funzionalità già in uso.

La nuova app consentirà anche agli utenti di sfruttare altre funzionalità della piattaforma come Single Sign-On (SSO) e l'autenticazione basata su certificato nei dispositivi Windows 10. L'app verrà resa disponibile come aggiornamento delle installazioni del portale aziendale di Windows 8.1 e del portale aziendale di Windows Phone 8.1 da Windows Store. Per altre informazioni, vedere [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

## <a name="september-2016"></a>Settembre 2016
### <a name="new-features-announcements-and-information"></a>Nuove funzionalità, annunci e informazioni
* [Accesso condizionale di Windows](#windows-conditional-access)
* [Supporto di iOS 10](#ios-10-support)
* [Lo strumento di wrapping delle app supporta MAM senza registrazione del dispositivo per Android e iOS](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [I gruppi di Intune inizieranno la transizione in Azure Active Directory a settembre](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Integrazione di Lookout per proteggere i dispositivi Android](#lookout-integration-to-protect-android-devices)
* [Aggiornamenti del portale aziendale per Android, iOS e Windows](#company-portal-updates)
* [Glossario di Intune](#intune-glossary)
* [Sviluppi futuri](#whats-coming)

### <a name="windows-conditional-access"></a>Accesso condizionale di Windows
È ora possibile creare criteri di accesso condizionale tramite la console di amministrazione di Intune per impedire l'accesso a Exchange Online e SharePoint Online ai PC Windows. È inoltre possibile creare criteri di accesso condizionale per bloccare l'accesso alle applicazioni universali e desktop di Office.

### <a name="ios-10-support"></a>Supporto di iOS 10
Gli scenari MDM e MAM Intune esistenti sono compatibili con iOS 10. Per suggerimenti, consultare il [Blog del Team di supporto Intune](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>Lo strumento di wrapping delle app supporta MAM senza registrazione del dispositivo per Android e iOS
Lo strumento di wrapping delle app Intune è uno strumento da riga di comando usato per abilitare le app line-of-business (LOB) MAM Intune per iOS e Android. È il modo più semplice per incorporare dell'SDK per MAM Intune nell'app, in modo che l'app possa applicare i criteri MAM distribuiti attraverso Intune. Usando i criteri MAM, è possibile:

1. Crittografare i dati dell'app.
2. Richiedere all'information worker di immettere un PIN quando si avvia l'app.
3. Consentire all'app di trasferire i dati solo ad altre app gestite.
4. Impedire all'app di eseguire il backup dei dati in Android, iTunes e iCloud.
5. Consentire solo Taglia, Copia e Incolla in e da altre app gestite.

L'anteprima pubblica dello strumento di wrapping delle app di Intune supporta ora MAM senza registrazione dei dispositivi nelle app LOB interne in iOS e Android. Ciò significa che gli utenti finali non devono registrare i propri dispositivi con Intune per usare le app LOB abilitate per MAM.

Chiunque può testare il software in anteprima pubblica e leggere l'utile documentazione, che si trova in GitHub ai seguenti indirizzi:

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Prima di installare e usare la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS è necessario:

* Esaminare le condizioni di licenza Microsoft per la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS
* Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android si accettano tali condizioni di licenza. Qualora l'utente non le accetti, non potrà usare il software.
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>I gruppi di Intune inizieranno la transizione in Azure Active Directory a settembre
Alcuni nuovi account di Intune useranno i gruppi di sicurezza di Azure Active Directory anziché i gruppi di utenti di Intune. Sarà possibile sapere che si lavora con i gruppi di sicurezza perché la pagina dei gruppi del portale Intune avrà un collegamento che indirizza al portale di gestione di Azure.

### <a name="lookout-integration-to-protect-android-devices"></a>Integrazione di Lookout per proteggere i dispositivi Android
Microsoft sta integrando la soluzione di protezione dalle minacce per dispositivi mobili Lookout per proteggere i dispositivi mobili Android grazie al rilevamento di malware, app rischiose e altro ancora. La soluzione Lookout consente di determinare il livello di minaccia, che è configurabile. È possibile creare una regola dei criteri di conformità in Intune per determinare la conformità del dispositivo in base alla valutazione del rischio da parte di Lookout. Con i criteri di accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali in base allo stato di conformità del dispositivo.

Agli utenti finali dei dispositivi non conformi verrà richiesto di eseguire la registrazione e sarà necessario installare l'applicazione Lookout for Work nei dispositivi Android, attivare l'app e correggere le minacce segnalate nell'applicazione Lookout for Work per ottenere l'accesso. Per altre informazioni, vedere [Limitare l'accesso in base al rischio per dispositivi, rete e applicazioni](restrict-access-based-on-device-network-app-risk.md).


### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale

__Android__

<p style="margin-left: 40px">**Aggiunta di "Notifiche" al portale aziendale per Android**<br/>
<p style="margin-left: 40px">È stata aggiunta una nuova icona Notifiche al portale aziendale per Android nella home page. Toccando l'icona si accede alla pagina Notifiche in cui gli utenti finali possono visualizzare tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. L'app del portale aziendale iOS dispone già di questa funzionalità delle notifiche. Con la nuova pagina Notifiche, all'utente non verrà visualizzata la pagina Configurazione dell'accesso aziendale ogni volta che avvia o riprende l'esecuzione del portale aziendale, a condizione che il dispositivo sia già registrato. Se si crea una propria guida per l'utente, aggiornare la documentazione per riportare questa modifica. Gli screenshot aggiornati sono disponibili [qui](https://aka.ms/androidcpupdate).  

__iOS__
<p style="margin-left: 40px">**Modifiche al supporto dell'app Portale aziendale per iOS**<br/>
<p style="margin-left: 40px">Tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS devono ora usare la versione più recente dell'app. I nuovi utenti possono scaricare solo la versione più recente e gli utenti attuali devono aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, quindi gli utenti dei dispositivi che eseguono versioni precedenti di iOS non potranno usare il portale aziendale o eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.
<!---TFS 1283165--->

<p style="margin-left: 40px">**Miglioramenti della modalità di recupero delle app per gli utenti finali di iOS**<br/>
<p style="margin-left: 40px">Le modifiche seguenti sono state apportate ai riquadri delle app nell'app Portale aziendale in modo che iOS indirizzi gli utenti con visualizzazioni diverse per tutte le app in un'unica posizione, il sito Web del portale aziendale. Le restrizioni di Apple impediscono alle app dell'app store line-of-business e gestite di essere elencate nell'app Portale aziendale e richiedono agli utenti di visitare visualizzazioni diverse per trovare le proprie app.

<p style="margin-left: 40px">Il riquadro **App aziendali** indirizzava in precedenza a un elenco di tutte le app nella scheda TUTTE del sito Web del portale aziendale e continuerà a funzionare allo stesso modo. Il nome del riquadro è diventato **Tutte le app**.

<p style="margin-left: 40px">Il riquadro **Altre app** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca tutte le app che Apple consente di visualizzare all'app Portale aziendale. Il nome del riquadro è diventato **App in evidenza** e toccandolo gli utenti verranno indirizzati alla scheda IN EVIDENZA del sito Web del portale aziendale.

<p style="margin-left: 40px">Il riquadro **Categorie** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca le categorie di app. Il nome del riquadro non è cambiato, ma ora punta alla scheda CATEGORIE del sito Web del portale aziendale. È possibile trovare [qui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186) le schermate aggiornate.
  <!---TFS 1317133--->

<p style="margin-left: 40px">**Chiedere conferma per installare l'app Managed Browser per iOS se i professionisti IT impostano tale requisito per un'app**<br/>
<p style="margin-left: 40px">Se è stata configurata l'apertura di una clip Web solo nell'app Managed Browser e questa non è installata in un dispositivo, l'app Portale aziendale sul dispositivo chiederà all'utente di installare il browser gestito prima di poter installare la clip Web.
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**È stato aggiunto un pulsante Feedback all'app Portale aziendale per Windows Phone 8.1**<br/>
<p style="margin-left: 40px">L'app del portale aziendale di Windows Phone 8.1 consente agli utenti di inviare feedback relativi all'app con il nuovo pulsante Invia il feedback. Per visualizzare il pulsante, gli utenti toccano il menu "tre punti" nella parte inferiore destra della schermata dell'app del portale aziendale e quindi toccano **Invia il feedback**. I feedback raccolti in modo anonimo consentiranno a Microsoft di migliorare l'esperienza dell'app del portale aziendale per gli utenti.
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Glossario di Intune</br>
È stato aggiunto un nuovo [argomento glossario](https://docs.microsoft.com/intune/understand-explore/intune-glossary) alla libreria per consentire una migliore comprensione di alcuni dei termini usati nel prodotto Intune.

## <a name="august-2016"></a>Agosto 2016
### <a name="app-management"></a>Gestione delle app
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__App nascoste e mostrate per iOS 9.3__ Per i dispositivi che eseguono iOS 9.3 o versione successiva sarà possibile usare gli elenchi di app nascoste e mostrate nei criteri di configurazione generale di iOS per:
- Specificare un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
- Specificare un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.

Le app selezionabili includono sia le app distribuite che le app predefinite per iOS, ad esempio i Messaggi e Note. Per informazioni dettagliate, vedere [Impostazioni dei criteri di iOS in Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).
<!---TFS 1279009 checked--->
__Criteri delle app consentite e bloccate per i dispositivi Samsung KNOX__ È ora possibile configurare un criterio personalizzato per i dispositivi Samsung KNOX che consente di creare:
- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Anche se installata, un'app presente nell'elenco delle app bloccate non può essere attivata nel dispositivo.
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. Le altre app dello Store non possono essere installate.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung KNOX.
Per informazioni dettagliate, vedere [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md) (Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung KNOX).
<!---TFS 1311629 checked --->
__Nuove app compatibili con i criteri di gestione di applicazioni mobili (MAM)__ L'app Yammer per [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) è ora compatibile con i [criteri di gestione di applicazioni mobili di Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) a prescindere dal fatto che il dispositivo sia registrato o meno.

Per un elenco completo di app MAM compatibili, vedere il sito dei [partner che forniscono applicazioni per Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__App visualizzatore di Intune__ Con il rilascio della nuova app RMS sharing, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
- Visualizzatore AV di Intune
- Visualizzatore PDF di Intune
- Visualizzatore immagini di Intune per Android disponibile in Google Play

Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova [app Rights Management (RMS sharing) per Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app) che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Quando l'app visualizzatore di Intune non sarà più supportata, verrà rimossa da Google Store e non sarà disponibile per l'uso futuro.

### <a name="device-management"></a>Gestione dei dispositivi
__Supporto per Android 7.0__ Intune fornirà dal "day 0" il supporto per il sistema operativo Android 7.0 per dispositivi mobili, di imminente uscita.
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Rimozione di Google della funzionalità di reimpostazione remota del passcode nei dispositivi Android 7.0
Google sta rimuovendo la possibilità per gli amministratori IT e gli utenti finali di reimpostare in modalità remota il passcode dei dispositivi Android 7.0. In precedenza, gli amministratori IT potevano reimpostare in modalità remota il passcode di un utente e gli utenti finali potevano reimpostare i propri passcode dal sito Web del portale aziendale.



### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale
__Sito Web del portale aziendale__
- **Collegamento Commenti e suggerimenti di Microsoft dal portale aziendale** <br/>
Il sito Web del portale aziendale consente agli utenti finali di toccare un nuovo collegamento "Commenti e suggerimenti" nella parte inferiore della pagina per inviare commenti e suggerimenti a Microsoft relativamente alla propria esperienza con il sito. I commenti raccolti in modo anonimo consentiranno a Microsoft di migliorare l'esperienza del sito Web del portale aziendale per gli utenti.
<!--- TFS 1313657 checked--->

__iOS__
- **Versione minima di Managed Browser per iOS aggiornata a 8.0**<br/>
L'app Managed Browser di Microsoft Intune per iOS è stata aggiornata per il supporto di dispositivi che eseguono iOS 8.0 o versione successiva. I dispositivi iOS 7.1 possono ancora usare l'app Managed Browser esistente. È tuttavia consigliabile invitare gli utenti a eseguire l'aggiornamento a iOS 8.0 o versione successiva per accedere a Managed Browser e sfruttare i vantaggi delle nuove funzionalità.  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>Sviluppi futuri
__Transizione dai gruppi di Intune ai gruppi di Azure Active Directory a partire dal mese di settembre 2016__ Intune sta creando una nuova esperienza di gestione dei gruppi che usa i gruppi di sicurezza di Azure Active Directory (AAD) come gruppi di utenti e dispositivi in Intune. Questi gruppi verranno usati per la gestione dei gruppi, la distribuzione dei criteri e la distribuzione dei profili **con l'introduzione del nuovo portale di amministrazione di Intune basato su Azure**.

Questa nuova esperienza consentirà di evitare di duplicare i gruppi tra i servizi, **garantirà l'accesso ad alcune nuove funzionalità dei gruppi di Azure Active Directory Premium (AADP)** e offrirà estendibilità tramite PowerShell e Graph. Consentirà inoltre di unificare l'esperienza di gestione dei gruppi per tutta la gestione della mobilità aziendale.

Per abilitare il passaggio ai gruppi di sicurezza, la **console di amministrazione corrente** verrà sottoposta ad alcune modifiche. **Queste modifiche e l'uso dei gruppi di sicurezza di AAD saranno indicati nella documentazione di Intune**.

I clienti che non hanno familiarità con Intune visualizzeranno **alcune delle modifiche ai gruppi di sicurezza prima di dei tenant correnti**.

Oltre alle modifiche apportate alla gestione dei gruppi, **verranno deprecate le funzionalità seguenti**:
- Esclusione di membri o gruppi durante la creazione di un nuovo gruppo
- Gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati**
- **Gestisci gruppi** nel ruolo di amministratore del servizio
- Avvisi personalizzati in base al gruppo per le regole di notifica
- Calcolo pivot per gruppi nei report
<!--- TFS 1295329--->

__Aggiunta di "Notifiche" al Portale aziendale per Android__ Nel mese di settembre verrà rilasciato un aggiornamento del portale aziendale per Android che presenterà una nuova icona delle **notifiche** nella home page. Toccando l'icona si avrà accesso alla pagina delle **notifiche** in cui l'utente finale visualizzerà tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. Se si usa l'app Portale aziendale per iOS, è già possibile visualizzare l'esperienza delle notifiche. Con l'introduzione della pagina **Notifiche**, non verrà visualizzata la pagina **Configurazione dell'accesso aziendale** ogni volta che si avvia o si riprende l'esecuzione del Portale aziendale per Android, purché il dispositivo sia già registrato. Molti utenti hanno creato materiale sussidiario per gli utenti finali ed è consigliabile dare tempestiva comunicazione a Microsoft nel caso possa essere necessario aggiornare tale materiale o le relative schermate. Aggiornare la documentazione in modo che rifletta le future modifiche nell'esperienza. Per le schermate aggiornate, visitare https://aka.ms/androidcpupdate.  

### <a name="service-deprecation"></a>Deprecazione del servizio
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Modifiche al supporto dell'app Portale aziendale per iOS**<br/>
Da settembre, tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS dovranno usare la versione più recente dell'app. I nuovi utenti potranno scaricare solo la versione più recente e gli utenti attuali dovranno aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, pertanto gli utenti dei dispositivi che eseguono versioni precedenti di iOS non saranno in grado di usare il portale aziendale o di eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.  

- **Versione minima di Managed Browser per iOS aggiornata a 8.0**<br/>
Nel mese di agosto Intune rilascerà un'app aggiornata di Managed Browser di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 8.0 o versione successiva. I dispositivi iOS 7.1 saranno ancora in grado di usare l'app Managed Browser esistente, tuttavia è consigliabile invitare gli utenti a eseguire l'aggiornamento a iOS 8.0 o versione successiva per accedere a Managed Browser e sfruttare i vantaggi delle nuove funzionalità.  
<!---TFS 1313253--->

- **Le app del portale aziendale per Windows 8 e Windows Phone 8 verranno deprecate a partire da settembre 2016** <br/>
Da settembre 2016, Microsoft Intune terminerà il supporto per le app del portale aziendale di Microsoft Intune per le piattaforme Windows Phone 8 e Windows 8. Aggiornare i dispositivi a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## <a name="july-2016"></a>Luglio 2016
### <a name="app-management"></a>Gestione delle app

__Migliorare l'esperienza di aggiornamento del profilo di provisioning dell'app__ Nelle app per dispositivi mobili line-of-business per Apple iOS sono inclusi un profilo di provisioning e un codice firmato con un certificato. Quando si esegue l'app in un dispositivo iOS, iOS conferma l'integrità dell'app e impone i criteri definiti dal profilo di provisioning.

La durata del certificato di firma dell'organizzazione usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Con questo aggiornamento, Intune offre gli strumenti per distribuire in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza, mentre il certificato è ancora valido. Per altre informazioni, vedere [ Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Usare i criteri del profilo di provisioning per dispositivi mobili iOS per mantenere aggiornate le app line-of-business)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->

__È disponibile Xamarin SDK per app Intune__ Il componente Intune App SDK Xamarin consente di abilitare le funzionalità di gestione delle app per dispositivi mobili Intune nelle app per dispositivi mobili iOS e Android compilate con Xamarin. È possibile trovare il componente nello [Store Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) o nella [pagina di GitHub di Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Gestione dei dispositivi
__Limiti aumentati di registrazione dei dispositivi__ Intune ha aumentato il limite massimo di registrazione dei dispositivi configurabili da 5 a 15 dispositivi per utente.
<!---TFS 1289896 --->

__Integrazione di TeamViewer per PC Windows che eseguono il software client Intune__
L'integrazione di [TeamViewer](https://www.teamviewer.com) per PC Windows che eseguono il client di Intune consente di avviare sessioni di assistenza remota con PC Windows per supportare i reparti Help Desk degli utenti finali. Sono inclusi Windows 7, 8, 8.1 e Windows 10. Per informazioni dettagliate, vedere [Attività comuni di gestione di PC Windows con client di Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale

__Sito Web del portale aziendale__
- **Esperienza dell'utente finale migliorata durante la registrazione di dispositivi Windows**<br/>
Quando si usa l'accesso condizionale, la procedura di registrazione per Windows 8.1, Windows 10 Desktop e Windows 10 Mobile è stata semplificata nel sito Web del portale aziendale. Gli utenti ora visualizzeranno due procedure separate, "Registrazione dispositivi" e "Aggiunta all'area di lavoro". In questo modo sarà più semplice visualizzare lo stato del dispositivo e completare il processo se l'aggiunta all'area di lavoro (WPJ) ha avuto esito negativo. Le procedure separate dovrebbero inoltre semplificare il processo di risoluzione dei problemi per gli amministratori IT. In precedenza, quando gli utenti finali tentavano di registrarsi e tutti i passaggi della registrazione avevano esito positivo eccetto l'aggiunta all'area di lavoro, il dispositivo registrato non veniva visualizzato nell'elenco dei dispositivi per l'identificazione da parte degli utenti, causando confusione.

__Android__
- **App Portale aziendale Android**<br/>
Se gli utenti finali Android visualizzano un messaggio di errore che indica che al dispositivo manca un certificato obbligatorio, è possibile toccare il pulsante per la risoluzione del problema per ottenere la [procedura](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) per l'installazione del certificato mancante. Se gli utenti completano la procedura, ma visualizzano un altro messaggio di errore che indica che manca un certificato, verrà chiesto loro di contattare l'amministratore IT e fornirgli questo [collegamento](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), che contiene la procedura che gli amministratori IT possono usare per risolvere il problema del certificato.

- **Limitare l'installazione di app con trasferimento in locale in dispositivi registrati**<br/>
Nei dispositivi Android non è più possibile installare applicazioni tramite il sito Web del portale aziendale, a meno che i dispositivi siano stati registrati in Intune tramite l'app Portale aziendale per Android.
<!---TFS 1299082--->

__iOS__
- **Modifiche agli account Manager di registrazione dei dispositivi nell'app Portale aziendale per iOS**<br/>
Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi (DEM) nel riquadro **Dispositivi personali** dell'app Portale aziendale per iOS. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale.

L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune. Intune deprecherà anche l'uso degli account Manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi.

Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile. Per altre informazioni, vedere [Registrare i dispositivi di proprietà dell'azienda con Manager di registrazione dispositivi in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Modifica dei nomi delle funzionalità Windows
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) è ora noto come **Windows Hello for Business**.
- [Protezione dei dati aziendali](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) è ora noto come **Windows Information Protection**.

## <a name="june-2016"></a>Giugno 2016
### <a name="intune-service-health"></a>Integrità del servizio Intune
Le informazioni sull'integrità del servizio per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel portale di gestione di Office 365 in Integrità dei servizi. Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Gestione delle app
- **Esperienza avanzata di configurazione dei criteri di dati aziendali di Windows 10.** Sono stati apportati miglioramenti all'esperienza di configurazione dei criteri di protezione dei dati aziendali di Windows 10 con la creazione di regole di app, la definizione di limiti di rete e altre impostazioni di protezione dei dati aziendali. Per altre informazioni, vedere l'articolo relativo alla [creazione di un criterio di protezione dei dati aziendali con Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Gestione dei dispositivi
- **Impostazione di Windows Defender per la protezione da app potenzialmente indesiderate.** È stata aggiunta una nuova impostazione di Windows Defender denominata **Potentially Unwanted Application Detection (Rilevamento di applicazioni potenzialmente indesiderate)** ai criteri di configurazione generali per Windows 10 Desktop e Mobile. È possibile usare questa impostazione per la protezione di computer desktop Windows registrati da eventuale software in esecuzione classificato da Windows Defender come potenzialmente indesiderato. È possibile ottenere protezione da tali applicazioni in esecuzione o usare la modalità di controllo per rilevare l'installazione di un'applicazione potenzialmente indesiderata. Per altre informazioni, vedere [Impostazioni dei criteri di Windows 10 in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Accesso condizionale
- **Criteri di controllo di accesso di rete Cisco ISE per Intune.**  I clienti che usano Cisco Identity Service Engine (ISE) 2.1 e Microsoft Intune possono impostare i criteri di controllo di accesso di rete in ISE.

    Con l'uso di questi criteri, i dispositivi che devono connettersi alla rete tramite Wi-Fi o VPN devono soddisfare le condizioni seguenti prima di consentire l'accesso:

    * Devono essere gestiti da Intune
    * Devono essere compatibili con i criteri di compatibilità di Intune distribuiti

 Agli utenti finali di dispositivi non conformi verrà richiesto di eseguire la registrazione e risolvere eventuali problemi di conformità per ottenere l'accesso.
- **Accesso condizionale per il browser.** È possibile impostare un criterio di accesso condizionale per [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) in modo che siano accessibili solo dai Web browser supportati su dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere a siti di Outlook Web Access (OWA) e SharePoint e con dispositivi iOS e Android verrà richiesto di registrare il dispositivo con Intune oltre che di risolvere eventuali problemi di non conformità prima di poter completare l'accesso.
<!---TFS 1175844--->

- **Dynamics CRM Online supporta l'accesso condizionale.** È possibile impostare un criterio di accesso condizionale per [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) in modo che sia accessibile solo da dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere all'applicazione per dispositivi mobili Dynamics CRM in iOS e Android sarà chiesto di registrarsi con Intune e di risolvere eventuali problemi di non conformità per poter completare l'accesso.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Aggiornamenti del portale aziendale di Intune

__App Portale aziendale Android__

- Se gli amministratori IT applicano il nuovo criterio in base al quale i dispositivi impediscono l'installazione di app da origini sconosciute (Android 4.0 +), gli utenti finali con dispositivi Android 4.0 o versioni successive visualizzano il messaggio "L'installazione da origini sconosciute deve essere disabilitata". Gli utenti dovranno passare a  **Impostazioni** > **Sicurezza** e disattivare **Origini sconosciute**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sul messaggio e di sapere perché viene richiesta la disattivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio in base al quale i dispositivi devono abilitare la ricerca di minacce per la sicurezza nelle app (Android 4.0 +), gli utenti finali con dispositivi Android 4.0 o versioni successive visualizzano il messaggio "Cerca minacce per la sicurezza nel dispositivo". Gli utenti dovranno passare a **Impostazioni** > **Google** > **Sicurezza** e attivare **Cerca minacce per la sicurezza nel dispositivo**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sul messaggio e di sapere perché viene richiesta l'attivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio in base al quale il debug USB deve essere disabilitato (Android 4.2 +), gli utenti finali con dispositivi Android 4.2 o versioni successive visualizzano il messaggio "Il debug USB deve essere disabilitato". Gli utenti dovranno passare a **Impostazioni** > **Opzioni per gli sviluppatori** e disattivare **Debug USB**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sul messaggio e di sapere perché viene richiesta la disattivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio relativo al livello minimo di patch di protezione per Android (Android 6.0 +), gli utenti finali con dispositivi Android 6.0 o versioni successive visualizzano il messaggio "Questo dispositivo non rispetta il livello minimo di patch di protezione per Android". Gli utenti dovranno installare la patch di protezione richiesta. Un collegamento nel messaggio di conformità consente agli utenti di ottenere [informazioni](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) su come installare la patch di protezione richiesta e di vedere quale patch di protezione è attualmente installata.

__App Portale aziendale iOS__

- Durante l'installazione delle applicazioni line of business ora gli utenti finali vedranno un'esperienza di installazione delle app migliorata. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- L'app Portale aziendale di Microsoft Intune per iOS è stata aggiornata per supportare iOS versione 8.0 e successive. Questo aggiornamento significa che gli utenti finali possono installare l'app Portale aziendale e registrare i nuovi dispositivi in Intune solo se il dispositivo esegue iOS versione 8.0 o successiva. Gli utenti che hanno già iscritto dispositivi che eseguono una versione non supportata di iOS possono continuare a utilizzare l'app portale aziendale sul dispositivo.


## <a name="may-2016"></a>Maggio 2016
Tutte queste funzionalità sono supportate anche per le distribuzioni ibride (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la pagina delle [Novità per le funzionalità ibride](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### <a name="documentation"></a>Documentazione
Benvenuti nella versione di anteprima di [docs.microsoft.com](https://docs.microsoft.com/en-us/intune).
Questa piattaforma moderna completamente nuova è stata progettata per rendere più semplice per i nostri clienti comprendere e usare Intune.
Per informazioni su tutte le nuove funzionalità, vedere [Introducing docs.microsoft.com (Introduzione a docs.microsoft.com)](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### <a name="intune-service-health"></a>Integrità del servizio Intune
Le informazioni sull'integrità del servizio per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) in **Integrità dei servizi**.
Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### <a name="app-management"></a>Gestione delle app
- **MAM SDK: supporto per la configurazione della lunghezza del PIN.** Sarà possibile specificare la lunghezza del PIN per le app MAM in modo simile al PIN di un dispositivo. Gli utenti finali dovranno perciò conformarsi alle nuove limitazioni imposte. Vedranno la schermata del PIN leggermente modificata per tenere conto della lunghezza del PIN. Per informazioni dettagliate, vedere [Impostazioni dei criteri di gestione delle app per dispositivi mobili Android in Microsoft Intune](/intune/deploy-use/android-mam-policy-settings) e [Impostazioni dei criteri di gestione delle app per dispositivi mobili per iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype for Business per iOS e Android.** È ora possibile scegliere come destinazione Skype for Business con [MAM senza criteri di registrazione](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Dopo la connessione degli utenti, verranno applicati i criteri MAM.

- **Sono disponibili nuove app per la gestione con criteri MAM.** Le app Microsoft Word, Excel e PowerPoint per Android possono ora essere associate a criteri MAM su dispositivi non registrati in Intune. Per visualizzare l'elenco completo delle app supportate, passare alla raccolta di applicazioni per dispositivi mobili di Microsoft Intune nella pagina dei [partner di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale

#### <a name="android-company-portal-app"></a>App Portale aziendale Android
- **Notifiche di tipo avviso popup per l'utente finale**: per gli utenti finali che registrano un dispositivo o lo rimuovono dal Portale aziendale vengono visualizzate notifiche di tipo avviso popup dell'app Portale aziendale per Android.

- **Modifiche agli account Manager di registrazione dispositivi nell'app Portale aziendale per Android.** Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro Dispositivi personali dell'app Portale aziendale per Android. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.

#### <a name="company-portal-website"></a>Sito Web del portale aziendale
- **Sito Web del portale aziendale: il banner di identificazione del dispositivo offrirà maggiori informazioni agli utenti finali.** Gli utenti finali possono ora identificare facilmente il dispositivo selezionato durante l'uso del sito Web del portale aziendale. Se viene selezionato il dispositivo errato, gli utenti potranno selezionare il dispositivo corretto toccando il collegamento **Tocca qui** nel banner della pagina iniziale.

### <a name="service-deprecation"></a>Deprecazione del servizio
- **App visualizzatore di Intune.** Con il rilascio della nuova app di condivisione RMS, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
    - Visualizzatore AV di Intune
    - Visualizzatore PDF di Intune
    - Visualizzatore immagini di Intune per Android disponibile in Google Play

  Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova app Rights Management (condivisione RMS) per Android che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Sono disponibili altre informazioni sull'app di condivisione RMS con collegamento alla documentazione.

- **Rimozione della capacità di scegliere gruppi personalizzati come destinazione delle regole di notifica.**
Le regole di notifica di Intune definiscono i destinatari degli avvisi di posta elettronica inviati da Intune. Attualmente è possibile configurare regole di notifica per inviare messaggi di posta elettronica a tutti gli utenti dei dispositivi di un gruppo di dispositivi di Intune creato. A partire dal 1° giugno 2016, la configurazione dei gruppi creati dagli utenti come destinazione non sarà più supportata.

    Attualmente, per impostare come destinazione di una regola di notifica un gruppo creato dalla console di amministrazione di Microsoft Intune, è necessario eseguire i passaggi seguenti:

    Nell'area di lavoro **Amministrazione** fare clic su **Regole di notifica** > **Crea nuova regola**

    Nel secondo passaggio della procedura guidata di creazione di una regola di notifica selezionare i gruppi di dispositivi di destinazione della regola. Il passaggio "Seleziona gruppi di dispositivi" verrà rimosso dalla console di Intune.

    La sequenza temporale preliminare di questa modifica sarà la seguente:
    - Nel giugno 2016 per i nuovi tenant non verrà visualizzato il secondo passaggio della procedura guidata di creazione di una regola di notifica. I tenant esistenti non sono interessati dalla modifica.
    - In agosto 2016 per alcuni tenant esistenti non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.
    - In ottobre 2016 per tutti i tenant non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.


- **Modifiche al supporto dell'app Portale aziendale per iOS**. Nei prossimi mesi verrà eseguito un aggiornamento dell'app Portale aziendale di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 8.0 o versione successiva. Gli utenti non potranno più registrare nuovi dispositivi che eseguono versioni precedenti a iOS 8.0. I dispositivi registrati che eseguono versioni precedenti a iOS 8.0 continueranno a essere gestiti e potranno, per un periodo di tempo limitato, continuare a usare l'app Portale aziendale. È necessario tuttavia che i dispositivi eseguano iOS 8.0 o versione successiva per accedere alle versioni più recenti dell'app Portale aziendale. È consigliabile richiedere agli utenti di eseguire l'aggiornamento a iOS 8.0 o versione successiva per poter usare al meglio le nuove funzionalità di Intune.  


## <a name="april-2016"></a>Aprile 2016
Tutte queste funzionalità sono supportate anche per i clienti ibridi (Configuration Manager con Intune).

### <a name="app-management"></a>Gestione delle app
- **Conformità utente MAM.**
È ora possibile visualizzare lo [stato](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune) dei criteri di gestione delle applicazioni per ogni utente del tenant Azure Active Directory (AAD). Sono inclusi:
   - Dispositivi
   - App sul dispositivo

   Valori di stato:

   **Archiviato**: indica che il criterio è stato distribuito all'utente, l'app è stata usata nel contesto di lavoro e ha ricevuto correttamente i criteri.

    **Non archiviato**: indica che il criterio è stato distribuito all'utente, ma da quel momento l'app non è mai stata usata nel contesto di lavoro.


- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (Android).**
È disponibile una nuova impostazione per la [gestione delle applicazioni per dispositivi mobili](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) senza registrazione del dispositivo. Questa impostazione consente di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi Android. Quando l'impostazione è abilitata, le applicazioni di destinazione non possono più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, le applicazioni di destinazione possono salvare i contatti nella rubrica nativa. Quando [si cancella un dispositivo o un'app da remoto](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune), tutti i contatti che sono già stati salvati nella rubrica nativa vengono rimossi. Questa nuova impostazione è supportata inizialmente dall'applicazione Outlook sui dispositivi Android.

### <a name="device-management"></a>Gestione dei dispositivi
- **Identificazione del numero di telefono per i dispositivi aziendali.** I telefoni classificati come "aziendali" sono ora identificati con il loro numero di telefono completo quando, per esempio, si esegue un report inventario dei dispositivi mobili. I numeri di telefono BYOD continuano a essere mascherati con **** mostrando solo le ultime 4 cifre.


### <a name="company-portal-updates"></a>Aggiornamenti del Portale aziendale
Gli utenti di **app del Portale aziendale Android** che non hanno registrato il loro dispositivo in Intune e non hanno il certificato corretto installato non potranno accedere all'app del Portale aziendale Android e vedranno il messaggio "Non è possibile accedere. Manca un certificato necessario per il dispositivo". Il messaggio include il collegamento “Risoluzione del problema” che gli utenti possono usare per vedere le istruzioni per l'installazione del certificato. Per i passaggi che gli utenti finali devono eseguire per risolvere il problema vedere [Manca un certificato necessario per il dispositivo](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**App Portale aziendale iOS** È stato aggiunto il supporto per l'azione di scorrimento per aggiornare il contenuto della schermata iniziale, che include le app e i dispositivi elencati e le informazioni di contatto IT. L'azione di scorrimento per l'aggiornamento non controlla la conformità o le informazioni sui criteri, cosa che si può fare selezionando il riquadro per il dispositivo corrente e toccando il pulsante **Sincronizza**.

**App Portale aziendale per Windows 10 Mobile e Windows Phone 8.1** Il processo di installazione delle app line-of-business è stato migliorato. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo manualmente per velocizzare l'installazione delle app](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sito Web Portale aziendale** Durante l'installazione delle app line-of-business, gli utenti di Windows 10 Mobile e Windows Phone 8.1 vedranno ora i seguenti stati nuovi, che specificano maggiori dettagli sullo stato della loro installazione:

* **In attesa della sincronizzazione del dispositivo**: l'utente ha toccato “Installa” e il dispositivo ora tenta di sincronizzarsi con l'infrastruttura Intune. La sincronizzazione è necessaria per poter completare l'installazione. Il messaggio "In attesa della sincronizzazione del dispositivo" è anche un collegamento che gli utenti possono toccare per vedere le [istruzioni](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) per sincronizzare manualmente il dispositivo con Intune, se il processo di sincronizzazione impiega troppo tempo o si blocca.
* **Download in corso**: la richiesta di download dell'utente è in fase di elaborazione e il dispositivo sta scaricando e installando l'app.

Prima dell'aggiunta di questi stati, gli utenti potevano essere confusi se l'installazione di un'app impiegava molto tempo, poiché vedevano solo lo stato "Installazione in corso", che poteva rimanere visualizzata sullo schermo per ore. Grazie all'aggiunta dei nuovi stati gli utenti, invece di chiamare il supporto, possono ora toccare il collegamento "In attesa della sincronizzazione del dispositivo" e seguire le istruzioni per forzare la ripresa del processo di sincronizzazione.



### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Nov16_HO3-->


