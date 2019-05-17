---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587383"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>In fase di sviluppo per Microsoft Intune - Aprile 2019

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
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Configurare le impostazioni di accesso e controllare le opzioni di riavvio nei dispositivi macOS <!-- 1210083 -->
Nei dispositivi macOS è possibile creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). Le nuove impostazioni della finestra di accesso includono la visualizzazione di un banner personalizzato, la scelta della modalità di accesso di un utente, la possibilità di visualizzare o nascondere le impostazioni di risparmio energia e altro ancora.

Per visualizzare le impostazioni correnti, vedere [Impostazioni relative alle funzionalità dei dispositivi macOS in Intune](macos-device-features-settings.md).

Si applica a: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Impostazioni avanzate per Windows Defender Firewall <!-- 1311949 -->
A breve sarà possibile usare Intune per gestire le regole firewall personalizzate nei client per Windows Defender. Le regole possono specificare il comportamento in entrata e in uscita di applicazioni, indirizzi di rete e porte. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Richiedere l'accesso condizionale per la protezione dell'app  <!--1634317 -->
Sarà possibile usare *Richiedi criteri di protezione dell'app* per confermare che i criteri vengano applicati all'app di un utente prima del completamento dell'accesso, in modo da evitare che gli utenti accedano a dati protetti con l'accesso condizionale. Anche se la verifica dei criteri potrebbe rallentare l'esperienza del primo utilizzo, aiuta a proteggersi da problemi di rete, errori di configurazione amministrativi o tentativi intenzionali di contrastare i criteri di protezione dell'applicazione. 

### <a name="retire-noncompliant-devices----1827291---"></a>Ritirare i dispositivi non conformi <!-- 1827291 -->
Verrà aggiunta una nuova azione di conformità per il ritiro dei dispositivi non conformi. Il ritiro di un dispositivo non conforme comporta la rimozione di tutti i dati aziendali dal dispositivo e la rimozione di quest'ultimo dalla gestione di Intune. Questa azione viene eseguita quando viene raggiunto il valore configurato in giorni. Il valore minimo è 30 giorni. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurare le impostazioni per le estensioni del kernel nei dispositivi macOS <!-- 2043024 -->
Nei dispositivi macOS è possibile creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **macOS** per la piattaforma). Un nuovo gruppo di impostazioni consentirà di configurare e usare le estensioni del kernel nei dispositivi.

Si applica a: macOS 10.13.2 e versioni successive

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurare il profilo per ignorare alcune schermate durante l'esecuzione di Assistente configurazione <!-- 2276470 -->
Quando si crea un profilo di registrazione macOS, sarà possibile configurarlo per ignorare qualsiasi schermata seguente quando un utente esegue Assistente configurazione:
- Android Migration (Migrazione Android)
- Display Tone (Tono schermo)
- Privacy
- iCloudStorage Se si crea un nuovo profilo o si modifica un profilo, le schermate da ignorare selezionate devono essere sincronizzate con il server MDM di Apple. Gli utenti possono eseguire una sincronizzazione manuale dei dispositivi in modo da evitare ritardi nell'aggiornamento delle modifiche del profilo.
Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS con Device Enrollment Program o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gli utenti dei dispositivi potranno visualizzare tutte le app gestite che hanno installato o tentato di installare <!-- 2352913 -->
Nel Portale aziendale per Windows saranno ancora elencate tutte le app gestite&ndash; sia obbligatorie che disponibili&ndash; installate nel dispositivo dell'utente. Gli utenti potranno visualizzare le installazioni di app tentate e in sospeso e i rispettivi stati correnti. Se l'organizzazione non rende le app obbligatorie o disponibili, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Gli utenti potranno anche ordinare o filtrare le app in base allo stato di installazione.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Tag di ambito per i token VPP Apple <!--2371886 -->
Sarà possibile aggiungere tag di ambito per i token VPP Apple. Solo gli utenti assegnati con lo stesso tag di ambito avranno accesso al token VPP Apple con tale tag. Le app VPP e gli eBook acquistati con tale token ereditano i tag di ambito. Per altre informazioni sui tag di ambito, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Usare le "regole di applicabilità" durante la creazione dei profili di configurazione dispositivo Windows 10 <!-- 2549910 -->
Creare profili di configurazione dispositivo Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** per la piattaforma). Sarà possibile creare una **regola di applicabilità** in modo che il profilo si applichi solo a un'edizione o versione specifica. Creare ad esempio un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applichi solo ai dispositivi che eseguono Windows 10 Enterprise.

Si applica a: 
- Windows 10 e versioni successive

### <a name="enable-win32-app-dependencies----2617348---"></a>Abilitare le dipendenze delle app Win32 <!-- 2617348 -->
Anteprima pubblica: gli amministratori potranno richiedere che vengano installate altre app come dipendenze prima di installare l'app Win32. In particolare, il dispositivo deve installare le app dipendenti prima di installare l'app Win32. Questa funzionalità sarà disponibile solo dopo che l'agente di gestione di Intune sarà stato aggiornato alla versione 1904 (superiore alla 1.18.120.0), il che potrebbe richiedere una o due settimane aggiuntive dopo l'aggiornamento del servizio alla versione 1904. In Intune selezionare **App client** > **App** > **Aggiungi** per visualizzare il pannello **Aggiungi app**. Selezionare **App di Windows (Win32)** come **Tipo di app**. Per altre informazioni, vedere [Intune autonomo - Gestione di app Win32](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Nuova impostazione delle limitazioni del dispositivo per Android Enterprise, proprietario del dispositivo: consentire agli utenti di connettersi alle reti Wi-Fi nei dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app <!--3041940 -->
Gli amministratori potranno attivare o disattivare una nuova impostazione che consente agli utenti di configurare la funzione Bluetooth nei dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app. Per visualizzare questa impostazione nella console di Intune, scegliere **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo > **Impostazioni** > **Dispositivi dedicati** > selezionare **Più app** dal menu a discesa **Modalità tutto schermo**. Sarà disponibile per l'abilitazione un'opzione denominata **Configurazione Wi-Fi**. 

Si applica a: dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Nuova impostazione delle limitazioni del dispositivo per Android Enterprise, proprietario del dispositivo: consentire agli utenti di configurare la funzione Bluetooth e l'associazione nei dispositivi dedicati Android Enterprise <!--3041941 -->
Gli amministratori potranno attivare o disattivare una nuova impostazione che consente agli utenti di configurare la funzione Bluetooth nei dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app. Per visualizzare questa impostazione nella console di Intune, scegliere **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo > **Impostazioni** > **Dispositivi dedicati** > selezionare **Più app** dal menu a discesa **Modalità tutto schermo**. Sarà disponibile per l'abilitazione un'opzione denominata **Configurazione Bluetooth**. 

Si applica a: dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorare lo stato della baseline di sicurezza (anteprima pubblica) <!-- 3082047 --> 
Quando si monitora lo *Stato del dispositivo* per le baseline di sicurezza, la visualizzazione organizzerà lo stato in base alle categorie di baseline, ad esempio *Notifiche sulla schermata di blocco*, *BitLocker* e *Browser*. Tutte le categorie di baseline disponibili verranno rappresentate. Per ogni categoria verrà visualizzato il numero di dispositivi che non corrispondono a una categoria specifica di baseline, non sono configurati correttamente o non sono applicabili.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Attività di sicurezza di Intune per Defender ATP (in anteprima pubblica) <!-- 3208597 -->
In anteprima pubblica, a breve Intune aggiungerà attività di sicurezza per la gestione delle minacce e delle vulnerabilità di Microsoft Defender annunciate di recente.  Con questa integrazione, gli amministratori delle operazioni di sicurezza in Windows Defender ATP (WDATP) potranno comunicare in modo più efficace agli amministratori di Intune le correzioni consigliate per le minacce emergenti. L'integrazione delle attività di sicurezza aggiunge un approccio basato sui rischi per individuare, classificare e correggere gli errori di configurazione e le vulnerabilità di endpoint.

Per altre informazioni sulle attività di sicurezza in Intune, vedere il post di blog sull'[uso delle attività di sicurezza di Intune per estendere la gestione delle minacce e delle vulnerabilità di Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Creare e usare profili di configurazione dei dispositivi OEMConfig in Intune <!-- 3305883 -->
Intune supporterà la configurazione di dispositivi Android Enterprise con OEMConfig. In particolare, è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android Enterprise usando OEMConfig (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma).

Il supporto per gli OEM è attualmente su base per OEM. Se una specifica app OEMConfig non è disponibile nell'elenco delle app OEMConfig, contattare `IntuneOEMConfig@microsoft.com`.

Si applica a: 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Nuove impostazioni relative alle restrizioni dei dispositivi per il proprietario del dispositivo Android Enterprise <!-- 3574254 -->
Nei dispositivi Android Enterprise è possibile creare un profilo di restrizione dei dispositivi per consentire o limitare le funzionalità, impostare regole per le password e altro ancora (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo). 

Saranno disponibili nuove impostazioni, incluse le impostazioni delle password, per consentire l'accesso completo alle app in Google Play Store per i dispositivi completamente gestiti e altro ancora. 

Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md). 

Si applica a: dispositivi Android Enterprise completamente gestiti

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10 <!-- 3617671 -->
Molti dispositivi Windows 10 e versioni successive hanno chipset Trusted Platform Module (TPM). Una nuova impostazione di conformità verificherà se nel dispositivo è presente TPM.

La pagina delle [impostazioni dei criteri di conformità di Windows 10 e versioni successive](compliance-policy-create-windows.md) elenca le impostazioni correnti.

Si applica a: 
- Windows 10 e versioni successive

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Configurare le app Win32 da installare in dispositivi aggiunti ad Azure AD registrati in Intune <!-- 3695227 -->
Sarà possibile assegnare le app Win32 da installare in dispositivi aggiunti ad Azure AD registrati in Intune. Per altre informazioni sulle app Win32 in Intune, vedere [Gestione di app Win32](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Linea di base di Windows Defender Advanced Threat Protection <!-- 3754134 -->
Verranno aggiunge nuove baseline per aiutare l'utente nella configurazione delle impostazioni di Windows Defender Advanced Threat Protection.

### <a name="device-overview-shows-primary-user---794259---"></a>La panoramica del dispositivo mostra l'utente primario <!--794259 -->
Nella pagina Panoramica del dispositivo verrà visualizzato l'utente primario, detto anche utente affinità utente-dispositivo. Per visualizzare l'utente primario per un dispositivo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo. L'utente primario verrà visualizzato nella parte superiore della pagina **Panoramica**.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Supporto esteso per i dispositivi Android Enterprise completamente gestiti <!-- 3903241, 3903244, 3903246 -->
Verrà esteso il supporto per i dispositivi Android Enterprise completamente gestiti ([annunciato nel gennaio 2019](whats-new.md#week-of-january-14-2019)) per includere le funzionalità seguenti:
- Conformità
- Accesso condizionale
- App per nuovo utente finale

Per configurare dispositivi Android completamente gestiti, passare a **Registrazione del dispositivo** > **Registrazione Android** > **Dispositivi utente completamente gestiti di proprietà aziendale**. Il supporto per i dispositivi Android completamente gestiti rimane disponibile in anteprima e alcune funzionalità di Intune potrebbero non essere completamente funzionali. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Segnalazione app Google Play gestite per dispositivi del profilo di lavoro Android Enterprise <!-- 4105925 -->
Per le app Google Play gestite distribuite nei dispositivi del profilo di lavoro Android Enterprise, sarà possibile visualizzare il numero di versione specifico dell'app installata in un dispositivo. Questo vale solo per le app richieste. In una versione futura verrà abilitata la stessa funzionalità per le app disponibili.

### <a name="ios-third-party-keyboards----4111843---"></a>Tastiere di terze parti iOS <!-- 4111843 -->
Il supporto per i criteri di protezione app di Intune per l'impostazione delle **tastiere di terze parti** terminerà a causa di una modifica della piattaforma iOS. Non sarà possibile configurare questa impostazione nella console di amministrazione di Intune e non verrà applicata nel client in Intune App SDK.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Impedire agli utenti di cercare aggiornamenti di Windows <!-- 3316758 -->
Verrà aggiunta una nuova impostazione degli anelli di aggiornamento di Windows che potrà essere usata per impedire agli utenti di cercare gli aggiornamenti di Windows. Questa impostazione non sarà disponibile dall'interno del portale, ma potrà essere configurata tramite l'API Graph di Intune.

### <a name="windows-update-notifications----3316782---"></a>Notifiche di Windows Update <!-- 3316782 -->
Verrà integrato il supporto per le configurazioni degli anelli di aggiornamento di Windows in modo da poter configurare le notifiche di Windows Update visualizzate dagli utenti. Questa impostazione non sarà disponibile dall'interno del portale, ma potrà essere configurata tramite l'API Graph di Intune.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Accesso semplificato alle impostazioni di diagnostica <!-- 3804627 -->
Verrà aggiunta una nuova opzione al pannello **Log di controllo** in ogni carico di lavoro di Log di controllo nella console di Intune che potrà essere usata per aprire direttamente la pagina *Impostazioni di diagnostica*.

## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


