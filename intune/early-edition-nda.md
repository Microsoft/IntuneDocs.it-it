---
title: Edizione anticipata - Microsoft Intune
titlesuffix: ''
description: Edizione anticipata di Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
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
ms.openlocfilehash: d50925d9f5422e1bfea01869233c63d6a2889109
ms.sourcegitcommit: 12f8b7f0bca1baa2c1f68dd6af4f16a4814daa11
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737503"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Edizione anticipata di Microsoft Intune: gennaio 2019

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
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>Gli script di PowerShell possono essere eseguiti in un host a 64 bit in dispositivi a 64 bit <!-- 1862675  -->
Quando uno script di PowerShell viene aggiunto al profilo di configurazione di un dispositivo, lo script viene sempre eseguito in modalità 32 bit, anche in sistemi operativi a 64 bit. Con questo aggiornamento, un amministratore può eseguire lo script in un host di PowerShell a 64 bit in dispositivi a 64 bit (**Configurazione del dispositivo** > **Script di PowerShell** > **Aggiungi** > **Configura** > **Esegui lo script in un host di PowerShell a 64 bit**).
Per altri dettagli sull'uso di PowerShell, vedere [Script di PowerShell in Intune](intune-management-extension.md).
Si applica a: Windows 10 e versioni successive

### <a name="rename-an-enrolled-windows-device----1911112----"></a>Rinominare un dispositivo Windows registrato <!-- 1911112  -->
È possibile rinominare un dispositivo Windows 10 (RS4 o versione successiva) registrato. A tale scopo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Rinomina dispositivo**.

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>Assegnare certificati SCEP a un dispositivo macOS senza utente    <!-- 2340521   -->
È possibile assegnare certificati SCEP (Simple Certificate Enrollment Protocol) a un dispositivo macOS senza utente e associare il certificato a profili Wi-Fi o VPN. Questa funzionalità estende il supporto già esistente per l'[assegnazione di certificati ai dispositivi senza utenti che eseguono Windows, iOS e Android](certificates-scep-configure.md#create-a-scep-certificate-profile).

### <a name="intune-conditional-access-ui-update------2432313----"></a>Aggiornamento dell'interfaccia utente per l'accesso condizionale di Intune   <!-- 2432313  -->
L'interfaccia utente per l'accesso condizionale nella console di Intune include alcuni miglioramenti, tra cui:
- Sostituzione del pannello *Accesso condizionale* di Intune con il pannello di Azure Active Directory. Ciò consente di accedere alla gamma completa di impostazioni e configurazioni per l'accesso condizionale che rimane una tecnologia di Azure AD.
- Riposizionamento della configurazione del *Connettore del servizio Exchange* nel pannello attualmente denominato *Accesso locale*. Questo pannello verrà inoltre rinominato in *Accesso ad Exchange*. Questa modifica consoliderà l'area in cui si configurano e monitorano i dettagli relativi a Exchange Online e locale.

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune userà le API di Google Play Protect nei dispositivi Android <!-- 2577355  -->
Alcuni amministratori IT devono affrontare un panorama BYOD in cui gli utenti finali possono finire per manomettere con jailbreak o root il proprio telefono cellulare. Questo comportamento, anche se non malintenzionato, comporta la disabilitazione di molti criteri di Intune impostati per proteggere i dati dell'organizzazione nei dispositivi degli utenti finali. Intune offre quindi il rilevamento per root e jailbreak sia per i dispositivi registrati, sia per quelli non registrati. Con questa versione, Intune introduce l'uso delle API di Google Play Protect per potenziare i controlli di rilevamento per root esistenti per i dispositivi non registrati. Anche se Google non condivide la totalità dei controlli di rilevamento per root eseguiti, queste API dovrebbero essere in grado di rilevare gli utenti che, per qualsiasi motivo, hanno manomesso con root i proprio dispositivi. I motivi possono spaziare dalla personalizzazione del dispositivo alla possibilità di ricevere i nuovi aggiornamenti del sistema operativo in dispositivi meno recenti. Sarà quindi possibile impedire a questi utenti di accedere ai dati aziendali oppure cancellare i relativi account aziendali dalle app abilitate da criteri. Per un valore aggiunto, l'amministratore IT può ora contare su diversi aggiornamenti dei report all'interno del pannello Protezione app di Intune: il report "Utenti contrassegnati" visualizza gli utenti rilevati tramite l'analisi dell'API SafetyNet di Google Play Protect e il report "Potentially Harmful Apps" (App potenzialmente dannose) visualizza le app rilevate tramite l'analisi dell'API Verify Apps di Google. Questa funzionalità è disponibile per Android. 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>Informazioni sulle app Win32 disponibili nel pannello Risoluzione dei problemi <!-- 2617342    -->
Nel pannello **Risoluzione dei problemi** dell'app di Intune è possibile raccogliere i file di log di eventuali errori di installazione di un'app Win32. Per altre informazioni sulla risoluzione dei problemi di installazione delle app, vedere [Risolvere i problemi di installazione delle app](troubleshoot-app-install.md).

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Le app browser in modalità tutto schermo e browser Microsoft Edge possono essere eseguite in dispositivi Windows 10 in modalità tutto schermo <!-- 2935135  -->
È possibile usare dispositivi Windows 10 in modalità tutto schermo per eseguire una o più app. Questo aggiornamento include diverse modifiche all'uso delle app browser in modalità tutto schermo, tra cui:

- Aggiunta del browser Microsoft Edge o del browser in modalità tutto schermo per l'esecuzione come app nel dispositivo in modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **Windows 10 e versioni successive** per la piattaforma > **Modalità tutto schermo** per il tipo di profilo).
- Limitazione di Microsoft Edge in modo che possa o non possa essere eseguito in modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Browser Microsoft Edge**). Se non viene eseguito in modalità tutto schermo, le impostazioni di Microsoft Edge possono essere modificate dagli utenti finali.

Per un elenco delle impostazioni correnti, vedere:

- [Impostazioni dei dispositivi Windows 10 e versioni successive per l'esecuzione in modalità tutto schermo](kiosk-settings-windows.md)
- [Limitazioni del dispositivo per il browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)

Si applica a: Windows 10 e versioni successive

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Assegnare automaticamente tag di ambito alle risorse create da un amministratore con quell'ambito <!-- 3173823  -->
Quando un amministratore crea una risorsa, i tag di ambito assegnati all'amministratore verranno automaticamente assegnati alle nuove risorse.

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>Nuove impostazioni relative alle restrizioni dei dispositivi per dispositivi iOS e macOS <!-- 3448774 -->
Nei dispositivi che eseguono iOS e macOS è possibile limitare alcune impostazioni e funzionalità (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** o **macOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento aggiunge altre funzionalità e impostazioni che è possibile controllare, tra cui l'impostazione dell'orario dello schermo, la modifica delle impostazioni dell'eSIM e dei piani per telefoni cellulari, il ritardo della visibilità degli aggiornamenti software da parte dell'utente, il blocco della memorizzazione di contenuti nella cache e altro ancora.
Per conoscere le funzionalità e le impostazioni correnti che è possibile limitare, vedere:
- [Impostazioni relative alle restrizioni per i dispositivi iOS](device-restrictions-ios.md)
- [Impostazioni relative alle restrizioni per i dispositivi macOS](device-restrictions-macos.md)

Si applica a:
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>Il report di registrazione non riuscita passa al pannello Registrazione del dispositivo <!-- 3560202 -->
Il report delle **registrazioni non riuscite** passerà alla sezione **Monitoraggio** del pannello **Registrazione del dispositivo**. Sono state anche aggiunte due nuove colonne: Metodo di registrazione e Versione sistema operativo.

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>Modifica di "Modalità tutto schermo" in "Dispositivi dedicati" <!-- 3598402  -->
Per allinearsi alla terminologia Android, **Modalità tutto schermo** verrà modificato in **Dispositivi dedicati** in Profili di configurazione dei dispositivi, **Android Enterprise** > **Proprietario dispositivo** > **Limitazioni del dispositivo**.

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Le impostazioni iOS per Safari e il ritardo della visibilità degli aggiornamenti software per l'utente passano all'interfaccia utente di Intune <!-- 3640850, , 3803313  -->
Per i dispositivi iOS è possibile configurare le impostazioni di Safari e gli aggiornamenti software. In questo aggiornamento le impostazioni sono state spostate in diverse parti dell'interfaccia utente di Intune:

- Le impostazioni di Safari passano da **Safari** (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo) in **App predefinite**. 
- L'impostazione relativa al **ritardo della visibilità degli aggiornamenti software per l'utente per i dispositivi iOS con supervisione** (**Aggiornamenti software** > **Criteri di aggiornamento per iOS**) passa in **Limitazioni del dispositivo** > **Generale**.

Per un elenco delle impostazioni correnti, vedere l'articolo sulle [restrizioni per i dispositivi iOS](device-restrictions-ios.md) e quello sugli [aggiornamenti del software iOS](software-updates-ios.md).

Si applica a: 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>L'abilitazione delle restrizioni nelle impostazioni del dispositivo è stata rinominata in Orario schermo nei dispositivi iOS <!-- 3699164  -->
È possibile configurare **Abilitazione delle restrizioni nelle impostazioni del dispositivo** nei dispositivi iOS con supervisione (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Generale**). In questo aggiornamento l'impostazione è stata rinominata in **Orario schermo (solo con supervisione)**. Il comportamento è lo stesso. In particolare: 

- iOS 11.4.1 e versioni precedenti: **Blocca** impedisce agli utenti finali di impostare le proprie restrizioni nelle impostazioni del dispositivo. 
- iOS 12.0 e versioni successive: **Blocca** impedisce agli utenti finali di impostare il proprio **Orario schermo** nelle impostazioni del dispositivo, incluse le restrizioni relative al contenuto e alla privacy. Nei dispositivi aggiornati a iOS 12.0 la scheda Restrizioni non sarà più visibile nelle impostazioni del dispositivo. Queste impostazioni sono in **Orario schermo**. 

Per un elenco delle impostazioni correnti, vedere l'articolo sulle [restrizioni per i dispositivi iOS](device-restrictions-ios.md).

Si applica a: 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>Dettagli sullo stato dell'app per le app iOS <!-- 3761235  -->
Saranno disponibili nuovi messaggi di errore di installazione delle app relativi alle situazioni seguenti:
- Errore per le app VPP durante l'installazione in iPad condiviso
- Errore quando l'App Store è disabilitato
- Licenza VPP per l'app non trovata
- Errore di installazione delle app di sistema con il provider MDM
- Errore di installazione delle app quando il dispositivo è in modalità di dispositivo perso o in modalità tutto schermo
- Errore di installazione dell'app quando l'utente non è connesso all'App Store

In Intune selezionare **App client** > **App** > "Nome app" > **Stato dell'installazione del dispositivo**. I nuovi messaggi di errore saranno disponibili nella colonna **Dettagli stato**.

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Distribuzione di app Microsoft Store per le aziende con licenza online <!-- 1672660  -->
Sarà possibile assegnare le app Microsoft Store per le aziende con licenza online richieste nel contesto del dispositivo. Questo tipo di distribuzione di app Microsoft Store per le aziende consentirà di installare le app per tutti gli utenti nel dispositivo. Questa opzione è disponibile solo per i dispositivi desktop Windows 10 RS4 e versioni successive. L'opzione di installazione nel contesto del dispositivo è disponibile nella pagina di assegnazione di App Client per le app con licenza online MSFB.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Distribuzione di app Android Enterprise APP-WE <!-- 1171203 -->
Per i dispositivi Android in uno scenario di distribuzione APP-WE (App Protection Policy Without Enrollment) non registrato, sarà possibile usare Google Play gestito per distribuire app dello Store e app LOB agli utenti. In particolare, il reparto IT può fornire agli utenti finali un catalogo di app e un'esperienza di installazione che non richiede più agli utenti finali di ridurre le condizioni di sicurezza dei propri dispositivi consentendo installazioni da origini sconosciute. Inoltre, questo scenario di distribuzione fornirà un'esperienza migliorata per gli utenti finali.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Aggiornamento del metodo di autenticazione e dell'installazione dell'app Portale aziendale per i criteri di Intune <!-- 1927359 -->
Nei dispositivi già registrati tramite l'Assistente configurazione con uno dei metodi di registrazione dei dispositivi aziendali di Apple, Intune non supporterà più l'app Portale aziendale se installata manualmente dagli utenti finali dall'App Store. Questa modifica è rilevante solo quando si esegue l'autenticazione con Apple Setup Assistant durante la registrazione. Questa modifica riguarda inoltre solo i dispositivi iOS registrati tramite:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

Gli utenti riceveranno un errore se installano l'app Portale aziendale dall'App Store e quindi provano a registrare i dispositivi tramite tale app. È previsto che questi dispositivi usino l'app Portale aziendale solo quando ne è stato eseguito il push automaticamente da Intune durante la registrazione. I profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Se si vuole che gli utenti dei dispositivi DEP dispongano dell'app Portale aziendale, è necessario specificare le preferenze in un profilo di registrazione. Inoltre, la schermata **Identifica il dispositivo** nell'app Portale aziendale diventerà presto obsoleta.  
Per installare l'app Portale aziendale nei dispositivi DEP già registrati, si dovrà passare a Intune > App client ed eseguirne il push come app gestita con i criteri di configurazione delle app. Informazioni dettagliate su come eseguire questi passaggi saranno disponibili in articoli futuri della documentazione.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>I modelli amministrativi sono disponibili in anteprima pubblica e sono stati spostati nel profilo di configurazione corrispondente <!-- 3322847 -->
I modelli amministrativi in Intune (**Configurazione del dispositivo** > **Modelli amministrativi**) sono attualmente in anteprima privata. Con questo aggiornamento: i modelli amministrativi includono circa 300 impostazioni che possono essere gestite in Intune. In precedenza, queste impostazioni erano disponibili solo in Editor Criteri di gruppo.
I modelli amministrativi sono disponibili in anteprima pubblica. I modelli amministrativi vengono spostati da **Configurazione del dispositivo** > **Modelli amministrativi** a **Configurazione del dispositivo** > **Profili** >**Crea profilo** > in **Piattaforma** scegliere  **Windows 10 e versioni successive**, in **Tipo di profilo** scegliere **Modelli amministrativi**.
La creazione di report è abilitata. Si applica a: Windows 10 e versioni successive

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Modalità scura del portale aziendale Intune per macOS <!-- 3300524 -->
Il portale aziendale Intune ora supporta la modalità scura per macOS. Quando si abilita la modalità scura in un dispositivo macOS 10.14 o versione successiva, il portale aziendale regola i colori in modo da riflettere tale modalità.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP Apple usato da un altro software MDM <!-- 1488946 -->
Intune rileverà e visualizzerà i dettagli se un token VPP (Volume Purchase Program) Apple viene usato sia da Intune che da un altro software MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivi ritirati nel dashboard della conformità dei dispositivi <!-- 1981119 -->
In un aggiornamento futuro i dispositivi ritirati verranno rimossi dal dashboard della conformità dei dispositivi. Questa operazione modificherà i numeri di conformità.

## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).