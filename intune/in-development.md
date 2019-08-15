---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833556"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>In fase di sviluppo per Microsoft Intune - Agosto 2019

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

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>Controllare il comportamento di disinstallazione dell'app iOS durante l'annullamento della registrazione del dispositivo <!-- 3504144 -->
Gli amministratori saranno in grado di gestire se un'app viene rimossa o mantenuta in un dispositivo quando viene annullata la registrazione del dispositivo a livello di utente o di gruppo di dispositivi. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Categorizzare le app di Microsoft Store per le aziende <!-- 3926922 -->
Potrai categorizzare Microsoft Store per le app aziendali. A tale scopo, scegliere **app** > c**lient** diIntune >  **app**>selezionareun'appMicrosoftStoreforbusinessapp> **Categoria** > **informazioni**. Nel menu a discesa assegnare una categoria.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurare il contenuto della notifica dell'app per gli account dell'organizzazione <!-- 2576686 -->
I criteri di protezione delle app di Intune (APP) nei dispositivi Android e iOS consentiranno di controllare il contenuto delle notifiche dell'app per gli account dell'organizzazione. Questa funzionalità richiede il supporto delle applicazioni e potrebbe non essere disponibile per tutte le applicazioni abilitate per l'APP. Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Creazione di report per le app disponibili in Google Play per i profili di lavoro Android <!-- 3041956  -->
Per le installazioni di app disponibili nei dispositivi con profilo di lavoro Android, è possibile visualizzare lo stato di installazione delle app e la versione installata delle app gestite in Google Play. Per altre informazioni, vedere [Come monitorare i criteri di protezione delle app](app-protection-policies-monitor.md), [Gestire i dispositivi con profilo di lavoro Android con Intune](android-enterprise-overview.md) e [Tipo di app Google Play gestite](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Alcune restrizioni dei dispositivi iOS senza supervisione verranno supervisionate solo con la versione iOS 13,0 <!-- 4867809  -->
Alcune impostazioni verranno applicate ai dispositivi supervisionati a partire dalla versione iOS 13,0. Queste impostazioni includono:

- App Store, visualizzazione documenti, giochi
  - App Store
  - Contenuto esplicito per iTunes, musica, podcast o notizie
  - Aggiunta di amici al Game Center
  - Gioco multiplayer
- App predefinite
  - Fotocamera
    - FaceTime
  - Safari
    - Riempimento automatico
- Cloud e risorse di archiviazione
  - Backup in iCloud
  - Blocca la sincronizzazione del documento iCloud
  - Blocca la sincronizzazione Keychain con iCloud

Se queste impostazioni vengono configurate e assegnate a dispositivi non supervisionati prima della versione iOS 13,0, le impostazioni vengono comunque applicate a tali dispositivi senza supervisione. Sono comunque valide anche dopo l'aggiornamento dei dispositivi a iOS 13,0. Queste restrizioni vengono rimosse nei dispositivi senza supervisione di cui viene eseguito il backup e il ripristino. 

Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-ios.md).

Si applica a:  
- iOS 13,0 e versioni successive

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>Nuove impostazioni e modifiche alle impostazioni esistenti per limitare le funzionalità nei dispositivi iOS e macOS <!-- 4867699 4867709  -->
Sarà possibile creare profili per limitare le impostazioni nei dispositivi che eseguono iOS**e MacOS (configurazione** >   **del dispositivo profili** > **di creazione profilo**  > **iOS** o**MacOS**per il tipo di piattaforma >**restrizionideidispositivi)** . Verranno aggiunte le funzionalità seguenti:

- Nelle **restrizioni**deidispositivi > **MacOScloude**  > **archiviazione usare la nuova**impostazione dicontinuità**per** impedire agli utenti di iniziare a lavorare su un dispositivo macOS e continuare a usare un altro dispositivo macOS o iOS.
  Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-macos.md).
- Sulle **restrizioni** > deidispositivi**iOS sono state apportate alcune modifiche:**
  - **App** >  **predefinite trova il mio iPhone (solo con supervisione)** : nuova impostazione che blocca questa funzionalità nella funzionalità trova l'app. 
  - **App** >  **predefinite trovare i miei amici (solo con supervisione)** : nuova impostazione che blocca questa funzionalità nella funzionalità trova l'app. 
  - **Modifica**wireless > **dello stato Wi-Fi (solo con supervisione**): nuova impostazione che impedisce agli utenti di attivare o disattivare il Wi-Fi nel dispositivo.
  - **Tastiera e dizionario** >  **QuickPath (solo con supervisione)** : nuova impostazione che blocca la funzionalità QuickPath.
  - **Cloud e archiviazione**: **la continuazione** dell'attività è stata **rinominata come uniforme**.

  Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-ios.md).

Si applica a:  
- macOS 10,15 e versioni successive
- iOS 13 e versioni successive

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>Controllare le app, i file, i documenti e le cartelle che si aprono quando l'utente accede ai dispositivi macOS <!--3914202  -->
Sarà possibile**abilitare e configurare**  >  **le funzionalità nei dispositivi**  >  MacOS (configurazione **del dispositivo profili Crea profilo**  >  **MacOS** per le **funzionalitàdel** dispositivo > della piattaforma per il tipo di profilo). 

Sono disponibili nuove impostazioni degli elementi di accesso per controllare quali app, file, documenti e cartelle si aprono quando un utente accede al dispositivo registrato. 

Per visualizzare le impostazioni correnti, passare alle [impostazioni delle funzionalità dei dispositivi macOS in Intune](macos-device-features-settings.md).

Si applica a:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>Nuove funzionalità per dispositivi Android Enterprise dedicati in modalità multiapp <!-- 3755304 3041943 3041946  -->
Sarà possibile controllare le funzionalità e le impostazioni in un'esperienza di tipo chiosco multimediale sui dispositivi Android Enterprise dedicati. A tale scopo, scegliere **profili**   > **diconfigurazione**del dispositivo creaprofilo > **AndroidEnterprise** > **per la piattaforma** **> solo il proprietario del dispositivo** , le restrizioni del dispositivo per il tipo di profilo.

Verranno aggiunte le funzionalità seguenti:
- **Dispositividedicati** > **multiapp**:il **pulsante Home virtuale può essere visualizzato scorrendo il dispositivo o spostando lo schermo in modo che gli utenti possano spostarlo.**
- **Dispositividedicati** > **multiapp** :l'**accessoallatorciaconsenteagliutentidiusarelatorcia**. 
- **Dispositividedicati** > **multiapp** :il**controllodelvolumemultimedialeconsenteagliutentidicontrollareilvolumemultimedialedeldispositivousandoundispositivodiscorrimento.** 
- **Dispositivi** > **dedicatimultiapp**: consente di abilitare uno screensaver, caricare un'immagine personalizzata e controllare quando viene visualizzato lo screensaver.

Per visualizzare le impostazioni correnti, passare alle [impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Si applica a:  
- Dispositivi dedicati Android Enterprise

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Nuovi profili di app e configurazione per dispositivi Android Enterprise completamente gestiti <!-- 3574215  -->
Usando i profili, sarà possibile configurare le impostazioni che applicano le impostazioni VPN, di posta elettronica e Wi-Fi ai dispositivi Android Enterprise completamente gestiti. Sarà possibile:
- Usare i profili di app per distribuire le impostazioni di posta elettronica di Outlook, Gmail e Nine work.
- Usare i profili di configurazione dei dispositivi per distribuire le impostazioni del certificato radice attendibile.
- Usare i profili di configurazione dei dispositivi per distribuire le impostazioni VPN e Wi-Fi.

Gli utenti eseguiranno l'autenticazione con il nome utente e la password per i profili VPN, Wi-Fi e di posta elettronica. Attualmente, l'autenticazione basata sui certificati non è disponibile. 

Si applica a:  
- Android Enterprise completamente gestito

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Supporto per i profili VPN IKEv2 per iOS <!-- 1943438 -->
È possibile creare profili VPN per il client VPN nativo di iOS tramite il protocollo IKEv2. IKEv2 è un nuovo tipo di connessione in **Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS**  per la piattaforma > **VPN** per il tipo di profilo > **Impostazioni**.

Questi profili VPN configurano il client VPN nativo. Pertanto, non viene installata alcuna app del client VPN, e non ne viene eseguito il push, nei dispositivi gestiti. Questa funzionalità richiede che i dispositivi siano registrati in Intune (registrazione MDM).

Per visualizzare le impostazioni VPN correnti che è possibile configurare, vedere [Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune](vpn-settings-ios.md).

Si applica a: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Registrazione del dispositivo

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>Ignora altre schermate in Assistente configurazione <!--4877451 -->
Sarà possibile impostare profili di Device Enrollment Program per ignorare le schermate di Assistente configurazione seguenti: 
- Orario schermo
- Configurazione dell'ID tocco

A tale scopo, passare a **registrazione del dispositivo** >  **registrazione Apple** > token**delprogrammadiregistrazione>scegliereuntoken>** **Profili** > scegliere un profilo > **modificare** > **leproprietà**accanto **allapersonalizzazione**diAssistenteconfigurazione.
Per altre informazioni sulla personalizzazione di Assistente configurazione, [vedere creare un profilo ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)di registrazione Apple.

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Supporto per l'amministratore del dispositivo di registrazione Android <!-- 4869749  -->
L'opzione registrazione amministratore dispositivi Android verrà aggiunta alla pagina**registrazione Android (registrazione** > **del dispositivo di Intune**   > **Android registrazione**). L'amministratore del dispositivo Android sarà ancora abilitato per impostazione predefinita per tutti i tenant.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Per i dispositivi iOS, personalizzare la schermata relativa alla privacy del processo di registrazione del Portale aziendale <!-- 4394993  -->
Usando Markdown, sarà possibile personalizzare la schermata di privacy del Portale aziendale visualizzata dagli utenti finali durante la registrazione di iOS. In particolare, sarà possibile personalizzare l'elenco di elementi che l'organizzazione non può visualizzare o eseguire sul dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Numero di build incluso nella pagina hardware del dispositivo Android <!-- 4461910  -->
Una nuova voce nella pagina hardware per ogni dispositivo Android includerà il numero di build del sistema operativo del dispositivo.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni <!--4231059  -->
È possibile impostare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni (anziché il limite corrente di 90 giorni) dopo l'ultimo accesso. A tale scopo, passare a **dispositivi**  > **Intun** > **installazioneregoledi**  > **pulizia del dispositivo**.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

### <a name="default-scope-tag----3702875---"></a>Tag ambito predefinito <!-- 3702875 -->
Sarà disponibile un nuovo tag di ambito predefinito incorporato. Tutti gli oggetti di Intune senza tag che supportano i tag di ambito verranno assegnati automaticamente al tag di ambito predefinito. Il **tag** di ambito predefinito verrà aggiunto a tutte le assegnazioni di ruolo esistenti per mantenere la parità con l'esperienza di amministrazione attuale. Se non si vuole che un amministratore visualizzi gli oggetti di Intune con i tag di ambito predefiniti, rimuovere il tag di ambito predefinito dall'assegnazione di ruolo. Questa funzionalità è simile alla funzionalità ambiti di protezione in System Center Configuration Manager.

<!-- ***********************************************-->
## <a name="security"></a>Sicurezza

### <a name="import-and-export-security-baselines------3408610------------"></a>Importare ed esportare le linee di base di sicurezza    <!--3408610          -->  
È stata aggiunta la funzionalità per esportare e importare le linee di base di sicurezza. Questa funzionalità consente di eseguire le personalizzazioni e condividerle tra gli ambienti Intune.

<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).




