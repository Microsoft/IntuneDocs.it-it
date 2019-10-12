---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999315"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>In fase di sviluppo per Microsoft Intune - Ottobre 2019

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
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestione delle app

### <a name="additional-app-configuration-variable-available----4969237----"></a>Variabile di configurazione dell'app aggiuntiva disponibile <!-- 4969237  -->
Quando si creano criteri di configurazione delle app, è possibile includere la variabile di configurazione `AAD Device ID` come parte delle impostazioni di configurazione. In Intune selezionare **App client** > **Criteri di configurazione dell'app** > **Aggiungi**. Immettere i dettagli dei criteri di configurazione e selezionare **le impostazioni di configurazione** per visualizzare il pannello **impostazioni di configurazione** .

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>Modalità scura per iOS Portale aziendale <!-- 4911422  -->
La modalità scura è progettata per il Portale aziendale iOS. Scaricare le app aziendali, gestire i dispositivi e ottenere supporto IT nella combinazione di colori scelta. Per altre informazioni sul Portale aziendale iOS, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Impedisci l'installazione di app da origini sconosciute nei dispositivi Android Enterprise <!-- 4760025  -->
Per un dispositivo Android Enterprise profile, non è mai possibile per gli utenti finali installare le app da origini sconosciute nel profilo di lavoro. È possibile estendere facoltativamente questa restrizione anche al profilo personale. Se si abilita questa restrizione, anche agli utenti finali nei dispositivi del profilo di lavoro di Android Enterprise verrà impedito di caricare le app da origini sconosciute sul lato personale del dispositivo. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Aggiornare l'interfaccia utente per la protezione delle app e l'interfaccia utente di provisioning <!-- 4102027, 4102029  -->
L'interfaccia utente per creare e modificare i criteri di protezione delle app e i profili di provisioning delle app iOS in Intune verrà aggiornata. Le modifiche dell'interfaccia utente includono:
- Un'esperienza semplificata usando un formato di tipo procedura guidata ridotto in un pannello. 
- Aggiornamento del flusso di creazione per includere le assegnazioni.
- Pagina riepilogata di tutti gli elementi impostati durante la visualizzazione delle proprietà, prima della creazione di un nuovo criterio o della modifica di una proprietà. Inoltre, quando si modificano le proprietà, nel riepilogo verrà visualizzato solo un elenco di elementi della categoria di proprietà modificate.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Creare gruppi di oggetti di gestione denominati set di criteri <!-- 3762880  -->
I set di criteri consentono di creare un bundle di riferimenti a entità di gestione già esistenti che devono essere identificate, mirate e monitorate come una singola unità concettuale. I set di criteri non sostituiscono i concetti o gli oggetti esistenti. Un amministratore può continuare a assegnare singoli oggetti, come avviene oggi. Un set di criteri fa riferimento a singoli oggetti. Pertanto, tutte le modifiche apportate ai singoli oggetti verranno riflesse nel set di criteri.  In Intune è possibile selezionare i **set di criteri** > **create** per creare un nuovo set di criteri. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>App Win32 in dispositivi in modalità Windows 10 S <!-- 3747604  --> 
Sarà possibile installare ed eseguire app Win32 in dispositivi gestiti in modalità Windows 10 S. Sarà possibile creare uno o più criteri aggiuntivi per la modalità S usando gli strumenti di PowerShell per il controllo delle applicazioni di Windows Defender (WDAC). Firmare i criteri supplementari con il portale di firma di Device Guard e quindi caricare e distribuire i criteri tramite Intune. In Intune è possibile trovare questa funzionalità selezionando **app Client** > **criteri aggiuntivi di Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Impostare la disponibilità delle app in base a una data e un'ora <!-- 3510685  -->
In qualità di amministratore, sarà possibile configurare l'ora di inizio e l'ora di scadenza per un'app richiesta. All'ora di inizio, l'estensione di gestione di Intune avvierà il download del contenuto dell'app e lo memorizza nella cache. L'app verrà installata alla data di scadenza. Per le app disponibili, l'ora di inizio impone quando l'app è visibile in Portale aziendale. In Intune selezionare **App client** > **App**. Selezionare quindi un'app specifica dall'elenco o selezionare **Aggiungi** per aggiungere una nuova app. Nel pannello dell'app selezionare **assegnazioni** > **Aggiungi gruppo**. Impostare **tipo di assegnazione** su **richiesto** , quindi selezionare **gruppi inclusi**. Impostare **rendere questa app obbligatoria per tutti gli utenti** su **Sì** e selezionare **modifica** per modificare le opzioni dell' **esperienza utente finale** . Nel pannello **esperienza utente finale** impostare il **tempo disponibile software** in base alle esigenze. Per altre informazioni sull'aggiunta di app, vedere [Aggiungere app in Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Richiedi riavvio delle app Win32 <!-- 3136567  -->
Sarà possibile richiedere che un'app Win32 venga riavviata dopo una corretta installazione. Inoltre, sarà possibile scegliere la quantità di tempo (periodo di tolleranza) prima che il riavvio debba essere eseguito.

### <a name="company-portal-app-on-windows----1808082----"></a>App Portale aziendale in Windows <!-- 1808082  -->
L'app Portale aziendale nei dispositivi Windows verrà aggiornata per visualizzare le notifiche di tipo avviso popup agli utenti, anche quando l'applicazione viene chiusa. L'aggiornamento visualizzerà solo le notifiche per le app disponibili quando lo stato dell'installazione è completato o non riuscito. L'app Portale aziendale non visualizzerà le notifiche per le applicazioni obbligatorie.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Messaggi di stato di installazione dell'app Portale aziendale <!-- 2514416  -->
L'app Portale aziendale visualizzerà messaggi di stato di installazione dell'app aggiuntivi per gli utenti finali. Alle nuove funzionalità di dipendenza Win32 verranno applicate le condizioni seguenti:
- Non è stato possibile installare l'app. Le dipendenze definite dall'amministratore non sono state soddisfatte.
- L'app è stata installata correttamente, ma è necessario un riavvio.
- È in corso l'installazione dell'app, ma è necessario riavviare per continuare.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Assegnare Microsoft Edge beta per macOS <!-- 4678761  -->
Sarà possibile aggiungere e assegnare la versione più recente di Microsoft Edge beta a Intune per i dispositivi macOS. Da Intune selezionare app **Client** > **app** > **aggiungere app** > **Microsoft Edge-MacOS**. Quindi, assegnare Microsoft Edge beta ai gruppi desiderati. Microsoft AutoUpdate (MAU) mantiene Microsoft Edge aggiornato. Per altre informazioni su Microsoft Edge, vedere [gestire l'accesso Web tramite Microsoft Edge con Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurare il contenuto della notifica dell'app per gli account dell'organizzazione <!-- 2576686 -->
I criteri di protezione delle app di Intune (APP) nei dispositivi Android e iOS consentiranno di controllare il contenuto delle notifiche dell'app per gli account dell'organizzazione. Questa funzionalità richiede il supporto delle applicazioni e potrebbe non essere disponibile per tutte le applicazioni abilitate per l'APP. Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Creazione di report per le app disponibili in Google Play per i profili di lavoro Android <!-- 3041956  -->
Per le installazioni di app disponibili nei dispositivi con profilo di lavoro Android, è possibile visualizzare lo stato di installazione delle app e la versione installata delle app gestite in Google Play. Per altre informazioni, vedere [Come monitorare i criteri di protezione delle app](../apps/app-protection-policies-monitor.md), [Gestire i dispositivi con profilo di lavoro Android con Intune](../enrollment/android-enterprise-overview.md) e [Tipo di app Google Play gestite](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Nuove impostazioni di configurazione del dispositivo per dispositivi iOS e iPad supervisionati <!-- 5199328  -->
Nei dispositivi iOS e iPados è possibile creare un profilo per limitare le funzionalità e le impostazioni nei dispositivi **(configurazione del dispositivo** > **profili** > **creare il profilo** > **iOS/ipados** per la piattaforma > **dispositivo restrizioni** per il tipo di profilo. Saranno disponibili nuove impostazioni che è possibile controllare: 
- Accesso all'unità di rete nell'app file  
- Accesso all'unità USB nell'app file 
- Wi-Fi sempre acceso 

Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:
- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Connetti automaticamente l'impostazione viene rimossa nei profili Wi-Fi in Android e Android Enterprise <!-- 5021055  -->
Nei dispositivi Android e Android Enterprise è possibile creare un profilo Wi-Fi per configurare impostazioni diverse (**configurazione del dispositivo** > **profili** > **creare il profilo** > **Android** o **Android Enterprise** per la piattaforma > **Wi-Fi** per il tipo di profilo). L'impostazione **connessione automatica** verrà rimossa, perché non è [supportata da Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Se si usa questa impostazione in un profilo Wi-Fi, è possibile notare che **Connect** non funzionerà automaticamente. Non è necessario eseguire alcuna azione, ma è necessario tenere presente che questa impostazione è stata rimossa nell'interfaccia utente di Intune.

Per visualizzare le impostazioni correnti, passare a impostazioni [Wi-Fi Android](../configuration/wi-fi-settings-android.md) o [Impostazioni Wi-Fi Enterprise Android](../configuration/wi-fi-settings-android-enterprise.md).

Si applica a:
- Android
- Android Enterprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Creare un proxy HTTP globale nei dispositivi Android Enterprise Device Owner <!-- 4816339  -->
Nei dispositivi Android Enterprise è possibile configurare un proxy HTTP globale per soddisfare gli standard di esplorazione Web dell'organizzazione (**configurazione del dispositivo** >  **profili** > **creare il profilo** > **Android Enterprise** per piattaforma > **proprietario del dispositivo > restrizioni del dispositivo** per il tipo di profilo > la **connettività**). Una volta configurata, tutto il traffico HTTP utilizzerà questo proxy.

Si applica a:
- Proprietario dispositivo Android Enterprise

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Nuovo profilo di interfaccia di configurazione del firmware del dispositivo per dispositivi Windows 10 e versioni successive <!-- 2266073  -->
In Windows 10 e versioni successive è possibile creare un profilo di configurazione del dispositivo per controllare le impostazioni e le funzionalità (**configurazione del dispositivo** > **profili** > **creare il profilo** > **Windows 10 e versioni successive** per la piattaforma). Sarà disponibile un nuovo tipo di profilo dell'interfaccia di configurazione del firmware del dispositivo che consente a Intune di gestire le impostazioni del BIOS (UEFI).

Per una panoramica di tutte le impostazioni correnti che è possibile configurare, vedere [applicare le funzionalità e le impostazioni nei dispositivi usando i profili di dispositivo in Microsoft Intune](../configuration/device-profiles.md).

Si applica a:
- Windows 10 RS5 (1809) e versioni successive nei dispositivi selezionati

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>Certificati PKCS per macOS  <!-- 1333650                -->
Verrà aggiunto il supporto completo per i certificati PKCS nei dispositivi che eseguono macOS. Gli utenti saranno in grado di distribuire certificati per utenti e dispositivi con campi oggetto personalizzazione e nome alternativo oggetto. Sarà anche disponibile una nuova impostazione Consenti l'accesso a tutte le app, che abilitando consente a tutte le app associate di accedere alla chiave privata. Per altri dettagli su questa impostazione, vedere la documentazione di Apple seguente: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Credenziali derivate per il provisioning di dispositivi mobili con certificati      <!--  1736036, 1736037, 1772050      --> 
Verrà aggiunto il supporto per le credenziali derivate, che supportano lo standard *NIST (National Institute of Standards and Technology) 800-157* per la distribuzione dei certificati nei dispositivi.  Le credenziali derivate si basano sull'uso di una scheda di verifica dell'identità personale (PIV) o di una scheda di accesso comune (CAC), ad esempio una smart card. Gli utenti eseguono l'autenticazione con la smart card in un computer e quindi inviano una richiesta di un certificato per il dispositivo gestito in base al processo richiesto dal provider di credenziali derivato.   

Il processo di utilizzo delle credenziali derivate per ottenere un certificato è diverso rispetto all'uso di profili certificato SCEP o PKCS, ma il risultato finale è lo stesso, ovvero i dispositivi mobili con certificati per l'autenticazione che possono essere usati per l'autenticazione di app, VPN, Wi-Fi o posta elettronica profili.   

Per ulteriori informazioni, vedere [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) in www.nccoe.NIST.gov.

La versione iniziale delle credenziali derivate supporterà Entrust Datacard, intercedi e DISA purosangue in iOS. Le piattaforme aggiuntive e i provider di credenziali derivati saranno supportati nelle versioni successive.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Registrazione del dispositivo

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>Specificare le versioni del sistema operativo del dispositivo Android registrate con il profilo di lavoro o la registrazione dell'amministratore del dispositivo <!-- 4350697 -->
Con le restrizioni del tipo di dispositivo Intune, sarà possibile usare la versione del sistema operativo del dispositivo per specificare quali dispositivi utente utilizzeranno la registrazione del profilo di lavoro di Android Enterprise o la registrazione dell'amministratore del dispositivo Android. A tale scopo, passare a **Intune** > **registrazione del dispositivo** > **restrizioni di registrazione** >  creare una**restrizione** > **restrizione del tipo di dispositivo** >  impostazioni della**piattaforma**.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Modificare il valore del nome dispositivo per i dispositivi Autopilot <!-- 4816775 -->
Sarà possibile modificare il valore del nome dispositivo per Azure AD dispositivi Autopilot aggiunti. A tale scopo, passare a **Intune** > **registrazione del dispositivo** > **registrazione Windows** > **windows Autopilot** > **dispositivi** > scegliere il dispositivo > modificare il valore nome dispositivo nel riquadro destro > **Salva** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Per i dispositivi iOS, personalizzare la schermata relativa alla privacy del processo di registrazione del portale aziendale <!-- 4394993  -->
Usando il markdown è possibile personalizzare la schermata relativa alla privacy del portale aziendale visualizzata dagli utenti finali durante la registrazione iOS. In particolare, è possibile personalizzare l'elenco di elementi che l'organizzazione non può visualizzare o eseguire sul dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Modificare il valore del tag di gruppo per i dispositivi Autopilot<!-- 4816775 -->
Sarà possibile modificare il valore del tag di gruppo per i dispositivi Autopilot. A tale scopo, passare a **Intune** > **registrazione del dispositivo** > **registrazione Windows** > **windows Autopilot** > **dispositivi** > scegliere il dispositivo > modificare il valore del tag di gruppo nel riquadro destro > **Salva** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Aggiornamento dell'interfaccia utente per la creazione e la modifica di anelli di aggiornamento di Windows 10  <!-- 4099089          -->   
Verrà implementata un'esperienza di creazione e modifica dell'interfaccia utente aggiornata per gli anelli di aggiornamento di Windows 10 per Intune.  Le modifiche all'interfaccia utente includono:  
- Semplifica l'esperienza esistente usando un formato di tipo procedura guidata ridotto in un pannello. Questo aggiornamento dell'interfaccia utente eseguirà l'espansione del pannello che richiede ai professionisti IT di eseguire il drill-down nei percorsi di pannelli profondi.   
- Modificare il flusso di creazione per includere le assegnazioni.  
- Aggiunta di una pagina riepilogata di tutti gli elementi impostati durante la visualizzazione delle proprietà, prima della creazione di un nuovo anello di aggiornamento e durante la modifica di una proprietà. Al momento della modifica, il riepilogo visualizzerà solo l'elenco di elementi impostati all'interno di una categoria di proprietà da modificare.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Aggiornamento dell'interfaccia utente per la creazione e la modifica degli aggiornamenti software iOS  <!-- 4099090        -->   
Verrà implementata un'esperienza di creazione e modifica dell'interfaccia utente aggiornata per gli aggiornamenti software iOS in Intune. Le modifiche all'interfaccia utente includono:
- Semplifica l'esperienza esistente usando un formato di tipo procedura guidata ridotto in un pannello. Questo aggiornamento dell'interfaccia utente eseguirà l'espansione del pannello che richiede ai professionisti IT di eseguire il drill-down nei percorsi di pannelli profondi.  
- Il flusso di creazione dei criteri di aggiornamento software iOS viene aggiornato in modo da includere le assegnazioni 
- I criteri di aggiornamento software iOS includeranno una pagina riepilogativa di tutti gli elementi impostati durante la visualizzazione delle proprietà, prima di creare un nuovo criterio e quando si modifica una proprietà. Al momento della modifica, il riepilogo visualizzerà solo l'elenco di elementi impostati all'interno di una categoria di proprietà da modificare.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Gruppi di utenti macOS di destinazione per richiedere la gestione JAMF <!-- 4061739 -->
Sarà possibile fare riferimento a gruppi di utenti specifici per richiedere che i dispositivi macOS siano gestiti da JAMF. Questa impostazione consente di applicare l'integrazione della conformità JAMF a un subset di dispositivi macOS mentre altri dispositivi continuano a essere gestiti da Intune. Consente inoltre di migrare gradualmente i dispositivi degli utenti da una MDM all'altra.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Nuove restrizioni per rinominare i dispositivi Windows <!-- 3478938 -->
I nomi dei dispositivi dovranno rispettare le regole seguenti:
- 15 caratteri o meno (deve essere minore o uguale a 63 byte, escluso il valore NULL finale)
- Stringa diversa da Null o vuota
- ASCII consentito: lettere (a-z, A-Z), numeri (0-9) e trattini
- Allowed Unicode: characters > = 0x80, deve essere un valore UTF8 valido, deve essere IDN-mappabili (RtlIdnToNameprepUnicode ha esito positivo; vedere RFC 3492)
- I nomi non devono contenere solo numeri o iniziare con un numero
- Nessun spazio nel nome
- Caratteri non consentiti: {|} ~ [\] ^':; < = >? & @! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Distribuire gli aggiornamenti software nei dispositivi macOS <!-- 3194876 -->
Sarà possibile distribuire gli aggiornamenti software a gruppi di dispositivi macOS. Questa funzionalità include l'errore critico, il firmware, il file di configurazione e altri aggiornamenti. Sarà possibile inviare aggiornamenti durante l'archiviazione del dispositivo successivo oppure selezionare una pianificazione settimanale per distribuire gli aggiornamenti in o fuori dal tempo di Windows impostati. Questa funzionalità è utile quando si desidera aggiornare i dispositivi al di fuori delle ore di lavoro standard o quando il help desk è completamente al personale. Si otterrà anche un report dettagliato di tutti i dispositivi macOS con aggiornamenti distribuiti. È possibile esaminare il report per ogni singolo dispositivo per visualizzare gli Stati di determinati aggiornamenti.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>Nuovo report Android nella pagina Panoramica dispositivi <!-- 2984353  -->
Verrà aggiunto un nuovo report alla pagina Panoramica dispositivi in cui viene visualizzato il numero di dispositivi Android registrati in ogni soluzione di gestione dei dispositivi. Questo grafico mostra il profilo di lavoro, il numero di dispositivi registrati, completamente gestiti, dedicati e dell'amministratore del dispositivo. Per visualizzare il report, scegliere **Intune** > **Devices** > **Overview**.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Report di distribuzione di Windows AutoPilot <!-- 3856172  -->
In un nuovo report vengono illustrati in dettaglio ogni dispositivo distribuito tramite Windows Autopilot. Questi dati saranno disponibili per 30 giorni dopo la distribuzione. Per visualizzare il report, passare a **Intune** > **registrazione del dispositivo** > **monitorare** > **distribuzioni Autopilot**.

### <a name="updated-support-experience-------5012398------"></a>Esperienza di supporto aggiornata   <!--  5012398    -->
Nell'ambito dei miglioramenti continui, l'esperienza di supporto nella console per Intune verrà aggiornata.  Verranno migliorati la ricerca e il feedback nella console per i problemi comuni e verrà semplificato il flusso di lavoro per contattare il supporto tecnico.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).




