---
title: In fase di sviluppo - Microsoft Intune
titlesuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
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
ms.openlocfilehash: 3e068e2c9834290b705e8e7bc2f895636415f9ba
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675443"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>In fase di sviluppo per Microsoft Intune - aprile 2019

Per facilitare la conformità e la pianificazione, questa pagina gli elenchi di UI Intune Aggiorna e a funzionalità che in fase di sviluppo ma non ancora rilasciato. Inoltre:

- Se si prevede che è necessario intervenire prima di una modifica, è possibile pubblicare un post di centro messaggi di Office gratuito.
- Quando una funzionalità viene avviata nell'ambiente di produzione, come un'anteprima o disponibili a livello generale, la descrizione della funzionalità passerà oltre questa pagina e al [pagina delle novità](whats-new.md).
- Questa pagina e il [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere il [M365 roadmap](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per sequenze temporali e gli obiettivi strategici.

> [!Note]
> Questi elementi riflettono le aspettative di corrente di Microsoft sulle funzionalità di Intune introdotte in una versione futura. Le date e le singole funzionalità possono cambiare. Non tutti gli elementi in fase di sviluppo presentano una descrizione delle funzionalità in questa pagina.

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Configurare le impostazioni di accesso e controllo delle opzioni di riavvio nei dispositivi macOS <!-- 1210083 -->
Nei dispositivi macOS, è possibile creare un profilo di configurazione del dispositivo (**configurazione del dispositivo** > **profili** > **Crea profilo** > Scegli **macOS** piattaforma > **le funzionalità del dispositivo** per tipo di profilo). Le impostazioni della finestra nuovo account di accesso verrà includere elementi, ad esempio che mostra un banner personalizzato, scegliere come gli utenti l'accesso, visualizzare o nascondere le impostazioni di risparmio energia e altro ancora.

Per visualizzare le impostazioni correnti, passare a [impostazioni di funzionalità del dispositivo macOS](macos-device-features-settings.md).

Si applica a: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Impostazioni avanzate per Windows Defender Firewall <!-- 1311949 -->
Presto sarà possibile usare Intune per gestire le regole del firewall personalizzate nei client per Windows Defender. Le regole è possono specificare il comportamento di ingresso e in uscita per le applicazioni, gli indirizzi di rete e porte. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Richiedono l'accesso condizionale di protezione App  <!--1634317 -->
È possibile usare *dei criteri di protezione delle App richiedono*, che conferma dei criteri viene applicato a un'app dell'utente prima del completamento di accesso per impedire agli utenti di accedere ai dati protetti con l'accesso condizionale. Mentre assurance criteri potrebbe rallentare l'esperienza di uso prima, aiuta a proteggersi da problemi di rete, errori di configurazione amministrativi o intenzionali sforzi per contrastare i criteri di protezione dell'applicazione. 

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660---"></a>Distribuzione di app Microsoft Store per le aziende con licenza online <!-- 16726660 -->
Sarà possibile assegnare le app Microsoft Store per le aziende con licenza online richieste nel contesto del dispositivo. Questo tipo di distribuzione di app Microsoft Store per le aziende consentirà di installare le app per tutti gli utenti nel dispositivo. Questa opzione è disponibile solo per i dispositivi desktop Windows 10 RS4 e versioni successive. L'opzione di installazione nel contesto del dispositivo è disponibile nella pagina di assegnazione di App Client per le app con licenza online MSFB.

### <a name="include-and-exclude-mixture-of-user-groups-and-device-groups-when-assigning-policies-and-profiles----1807547---"></a>Includere ed escludere combinazione di gruppi di utenti e gruppi di dispositivi quando si assegnano i criteri e profili <!-- 1807547 -->
Quando si assegnano i criteri di conformità o i profili di configurazione, è possibile assegnarli ai gruppi di sicurezza con gli utenti o dispositivi. Attualmente, è possibile includere ed escludere solo gruppi di utenti, *o* includere ed escludere solo gruppi di dispositivi. Non è possibile includere ed escludere una combinazione di gruppi, includono, ad esempio i gruppi di utenti *e* escludere un gruppo di dispositivi.

È possibile includere ed escludere una combinazione di gruppi di utenti e gruppi di dispositivi. È possibile includere un gruppo di utenti ed escludere un gruppo di dispositivi. Ad esempio, è possibile assegnare o distribuire un profilo di configurazione del dispositivo in un gruppo di utenti, ma escludere i dispositivi personali.

[Assegnare i profili di configurazione dispositivo](device-profile-assign.md) include altre informazioni sull'assegnazione dei profili per i gruppi di utenti e gruppi di dispositivi.

Si applica a: tutte le piattaforme

### <a name="retire-noncompliant-devices----1827291---"></a>Ritirare i dispositivi non conformi <!-- 1827291 -->
Dobbiamo aggiungere una nuova azione di conformità per ritirare un dispositivo non conforme. Ritiro di un dispositivo non conforme rimuove tutti i dati aziendali da essa e rimuove anche il dispositivo che vengano gestiti da Intune. Questa azione viene eseguita quando viene raggiunto il valore configurato in giorni. Il valore minimo è 30 giorni. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurare le impostazioni per le estensioni di kernel nei dispositivi macOS <!-- 2043024 -->
Nei dispositivi macOS, è possibile creare un profilo di configurazione del dispositivo (**configurazione del dispositivo** > **profili** > **Crea profilo** > Scegli **macOS** per piattaforma). Un nuovo gruppo di impostazioni consentirà di configurare e usare le estensioni di kernel nei dispositivi.

Si applica a: macOS 10.13.2 e versioni successive

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurare il profilo per ignorare alcune schermate durante l'esecuzione di Assistente configurazione <!-- 2276470 -->
Quando si crea un profilo di registrazione macOS, sarà possibile configurarlo per ignorare qualsiasi schermata seguente quando un utente esegue Assistente configurazione:
- Android Migration (Migrazione Android)
- Display Tone (Tono schermo)
- Privacy
- iCloudStorage Se si crea un nuovo profilo o si modifica un profilo, le schermate da ignorare selezionate devono essere sincronizzate con il server MDM di Apple. Gli utenti possono eseguire una sincronizzazione manuale dei dispositivi in modo da evitare ritardi nell'aggiornamento delle modifiche del profilo.
Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS con Device Enrollment Program o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gli utenti dei dispositivi è possono visualizzare tutte le app gestite che hai installato o tentata l'installazione <!-- 2352913 -->
Portale aziendale per Windows sono elencate tutte le app gestite&ndash; sia richiesta che disponibile&ndash; che vengono installate nel dispositivo dell'utente. Gli utenti saranno in grado di visualizzazione tentata e in sospeso le installazioni di app e i relativi stati correnti. Se l'organizzazione non rende le app obbligatoria o disponibile, gli utenti vedranno un messaggio che indica che nessuna App aziendale siano stata installata. Gli utenti sarà anche possibile ordinare o filtrare le proprie App in base allo stato di installazione.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Tag di ambito per i token VPP di Apple <!--2371886 -->
È possibile aggiungere i tag di ambito per i token VPP di Apple. Solo gli utenti assegnati con lo stesso tag di ambito avrà accesso al token VPP di Apple con tale tag. Le app VPP e gli eBook acquistati con tale token ereditano i tag di ambito. Per altre informazioni sui tag di ambito, vedere [tag di ambito e usare RBAC](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilizzare "le regole di applicabilità" quando la creazione di profili di configurazione del dispositivo Windows 10 <!-- 2549910 -->
Dispositivo Windows 10 è creare i profili di configurazione (**configurazione del dispositivo** > **profili** > **Crea profilo**  >  **Windows 10** per piattaforma). È possibile creare un **regola di applicabilità** in modo che il profilo si applica solo a un'edizione specifica o una versione specifica. Ad esempio, si crea un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applica solo ai dispositivi che eseguono Windows 10 Enterprise.

Si applica a: 
- Windows 10 e versioni successive

### <a name="enable-win32-app-dependencies----2617348---"></a>Abilita le dipendenze dell'app Win32 <!-- 2617348 -->
Versione di anteprima pubblica - l'amministratore sarà in grado di richiedere che le altre App siano installata come dipendenze prima di installare l'app di Win32. In particolare, il dispositivo deve installare l'App dipendente prima di installare l'app di Win32. Questa funzionalità sarà disponibile solo dopo che l'agente di gestione di Intune è stato aggiornato alla versione 1904 (maggiore di 1.18.120.0) che potrebbe richiedere da 1 o 2 settimane aggiuntive quando si esegue l'aggiornamento del servizio su 1904. In Intune, selezionare **App Client** > **app** > **Aggiungi** per visualizzare il **Aggiungi app** pannello. Selezionare **app di Windows (Win32)** come la **tipo di App**. Per altre informazioni, vedere [Intune Standalone - gestione delle app Win32](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Nuova impostazione restrizione del dispositivo per Android Enterprise, proprietario del dispositivo: consentire agli utenti di connettersi alle reti Wi-Fi nei dispositivi aziendali Android dedicato in esecuzione in modalità tutto schermo più app <!--3041940 -->
Gli amministratori potranno attivare o disattivare una nuova impostazione che consente agli utenti di configurare Bluetooth in dispositivi Android Enterprise dedicato in esecuzione in modalità tutto schermo più app. Per visualizzare questa impostazione nella console di Intune, scegliere **Intune** > **configurazione del dispositivo** > **profili**  >  **Crea profilo** > scegliere **Android Enterprise** per la piattaforma > **solo proprietario del dispositivo, restrizioni del dispositivo** per il tipo di profilo > **impostazioni**   >  **Dedicato dispositivi** > selezionare **più app** dal **modalità tutto schermo** impostazione elenco a discesa. Un'opzione di chiamata **configurazione Wi-Fi** saranno disponibili per l'abilitazione. 

Si applica a: Android Enterprise dedicata a dispositivi che eseguono la modalità tutto schermo più app. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Nuova impostazione restrizione del dispositivo per Android Enterprise, proprietario del dispositivo: consentire agli utenti di configurare Bluetooth e associazione nei dispositivi aziendali Android dedicato <!--3041941 -->
Gli amministratori potranno attivare o disattivare una nuova impostazione che consente agli utenti di configurare Bluetooth in dispositivi Android Enterprise dedicato in esecuzione in modalità tutto schermo più app. Per visualizzare questa impostazione nella console di Intune, scegliere **Intune** > **configurazione del dispositivo** > **profili**  >  **Crea profilo** > scegliere **Android Enterprise** per la piattaforma > **solo proprietario del dispositivo, restrizioni del dispositivo** per il tipo di profilo > **impostazioni**   >  **Dedicato dispositivi** > selezionare **più app** dal **modalità tutto schermo** impostazione elenco a discesa. Un'opzione di chiamata **Bluetooth configurazione** saranno disponibili per l'abilitazione. 

Si applica a: Android Enterprise dedicata a dispositivi che eseguono la modalità tutto schermo più app. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorare lo stato di base della sicurezza (anteprima pubblica) <!-- 3082047 --> 
Quando si monitora il *lo stato del dispositivo* per le linee di base di sicurezza, la visualizzazione organizzerà lo stato per le categorie della linea di base, ad esempio *blocco sopra*, *BitLocker*e  *Browser*. Tutte le categorie disponibili della linea di base verranno rappresentate. Per ogni categoria, verrà visualizzato il numero di dispositivi non corrispondono a una categoria specifica della linea di base, non è configurate correttamente o non è applicabile.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Attività di protezione di Intune per Defender ATP (In anteprima pubblica) <!-- 3208597 -->
Presto in anteprima pubblica, Intune verrà presto aggiunto attività relative alla sicurezza per il Microsoft Threat Defender & Gestione delle vulnerabilità appena annunciate.  Con questa integrazione, gli amministratori di operazioni di sicurezza in Windows Defender ATP (WDATP) possono comunicare in modo più efficace le correzioni consigliate per le minacce emergenti per gli amministratori di Intune. L'aggiunta di attività di protezione aggiunge un approccio basato sui rischi per individuare, classificare e correggere gli errori di configurazione e le vulnerabilità di endpoint.

Per altre informazioni sulle attività relative alla sicurezza in Intune, vedere il post di blog sul [utilizza le attività di protezione di Intune per estendere Microsoft Defender ATP di minacce e gestione delle vulnerabilità](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Creare e usare i profili di configurazione di OEMConfig dispositivo in Intune <!-- 3305883 -->
Intune supporterà la configurazione di dispositivi aziendali Android con OEMConfig. In particolare, è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni per i dispositivi aziendali Android usando OEMConfig (**configurazione del dispositivo** > **profili**  >  **Crea profilo** > **Android enterprise** per piattaforma).

Supporto per gli OEM è attualmente in base al OEM. Se un'app OEMConfig desiderata non è disponibile nell'elenco di App OEMConfig, contattare il tecnico `IntuneOEMConfig@microsoft.com`.

Si applica a: 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Nuove impostazioni di restrizione di dispositivi per Android Enterprise, proprietario del dispositivo <!-- 3574254 -->
Nei dispositivi Android Enterprise, è possibile creare un profilo di restrizione del dispositivo per consentire o limitare le funzionalità, impostare regole per la password e altro ancora (**configurazione del dispositivo** > **profili**  >  **Crea profilo** > selezionare **Android Enterprise** per la piattaforma > **solo proprietario del dispositivo > restrizioni del dispositivo** per tipo di profilo). 

Le nuove impostazioni, incluse le impostazioni di password, consentendo completo accedere alle App in Google Play Store per i dispositivi completamente gestiti e saranno disponibili altri. 

Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md). 

Si applica a: dispositivi completamente gestiti di Android Enterprise

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10 <!-- 3617671 -->
Molti di Windows 10 e versioni successive hanno chipset modulo TPM (Trusted Platform). Una nuova impostazione di conformità controllerà se TPM è presente nel dispositivo.

[Windows 10 e versioni successive impostazioni dei criteri di conformità](compliance-policy-create-windows.md#windows-10-and-later-policy-settings) sono elencate le impostazioni correnti.

Si applica a: 
- Windows 10 e versioni successive

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Configurare le app di Win32 per essere installato in registrati in Intune i dispositivi aggiunti ad Azure AD <!-- 3695227 -->
Sarà in grado di dispositivi aggiunti ad assegnare le app di Win32 per essere installato in Intune registrati AD Azure. Per altre informazioni sulle App Win32 in Intune, vedere [gestione delle app Win32](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Linea di base di Windows Defender Advanced Threat Protection <!-- 3754134 -->
Dobbiamo aggiungere nuova linea di base che consentono di configurare le impostazioni di Windows Defender Advanced Threat Protection.

### <a name="device-overview-shows-primary-user---794259---"></a>Panoramica del dispositivo Mostra utente primario <!--794259 -->
Nella pagina di panoramica dispositivo verranno visualizzati l'utente primario, detto anche l'utente affinità utente dispositivo (UDA). Per visualizzare l'utente primario per un dispositivo, scegliere **Intune** > **dispositivi** > **tutti i dispositivi** > scegliere un dispositivo. L'utente primario verrà visualizzato nella parte superiore di **Panoramica** pagina.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Supporto esteso per i dispositivi aziendali Android completamente gestito <!-- 3903241, 3903244, 3903246 -->
Dobbiamo espandere il supporto dei dispositivi aziendali Android completamente gestiti ([annunciato nel gennaio del 2019](whats-new.md#week-of-january-14-2019) eseguire le operazioni seguenti:
- Conformità
- Accesso condizionale
- Nuovo utente finale App

Per configurare dispositivi Android completamente gestiti, passare a **Registrazione del dispositivo** > **Registrazione Android** > **Dispositivi utente completamente gestiti di proprietà aziendale**. Il supporto per i dispositivi Android gestiti completamente rimane disponibile in anteprima e alcune funzionalità di Intune potrebbe non essere completamente funzionale. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>App Google Play gestito altri report per dispositivi di profilo di lavoro di Android Enterprise <!-- 4105925 -->
Per Google Play gestito le app distribuite nei dispositivi di profilo di lavoro di Android Enterprise, sarà possibile visualizzare il numero di versione specifico dell'app installate in un dispositivo. Questo vale per le app necessarie. Verrà abilitata la stessa funzionalità per le app disponibili in una versione futura.

### <a name="ios-third-party-keyboards----4111843---"></a>Tastiere di terze parti iOS <!-- 4111843 -->
Supporto per i criteri di protezione app di Intune (APP) per il **tastiere di terze parti** impostazione terminerà a causa di una modifica della piattaforma iOS. Non sarà possibile configurare questa impostazione in Console di amministrazione di Intune e non verrà applicata nel client di Intune App SDK.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Impedisce agli utenti di analisi degli aggiornamenti di Windows <!-- 3316758 -->
Stiamo aggiungendo una nuova impostazione di anello di aggiornamento Windows che è possibile usare per impedire agli utenti di analisi degli aggiornamenti di Windows. Questa impostazione non sarà disponibile in all'interno del portale, ma può essere configurata tramite l'API Graph di Intune.

### <a name="windows-update-notifications----3316782---"></a>Notifiche di aggiornamento di Windows <!-- 3316782 -->
Stiamo aggiungendo il supporto per le configurazioni di anello di aggiornamento di Windows in modo sarà possibile configurare le notifiche di aggiornamento di Windows che gli utenti visualizzano. Questa impostazione non sarà disponibile in all'interno del portale, ma può essere configurata tramite l'API Graph di Intune.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Modifiche alla registrazione di portale aziendale per gli utenti dei dispositivi iOS 12 <!--3448635 --> 
Portale aziendale per iOS aggiornerà le schermate di registrazione di app e i passaggi per la compatibilità con le modifiche di registrazione MDM rilasciate in Apple iOS 12.2. Il flusso di lavoro aggiornata verrà ora richiesto agli utenti di:

- Consenti Safari aprire il sito Web portale aziendale (tramite Safari) e scaricare il profilo di gestione prima di tornare all'app portale aziendale.
- Aprire l'app impostazioni e installare il profilo di gestione sul proprio dispositivo.
- Tornare all'app portale aziendale per completare la registrazione.

Per altre informazioni su come preparare le modifiche, vedere la [post di Microsoft Tech Community](https://aka.ms/CP_changes_iOS12). Nel frattempo, per supportare le nuove registrazioni di iOS nel portale aziendale, sono state aggiornate la procedura descritta in [Enroll iOS device in Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Queste modifiche doc sarà attivate dopo il rilascio di Apple iOS versione 12.2. 

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Semplificare l'accesso alle impostazioni di diagnostica <!-- 3804627 -->
Stiamo aggiungendo una nuova opzione per la **log di controllo** Pannello di ogni carico di lavoro di Log di controllo nella console di Intune che è possibile usare per aprire direttamente la *le impostazioni di diagnostica* pagina.

## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


