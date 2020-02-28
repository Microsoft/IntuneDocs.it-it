---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514566"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>In fase di sviluppo per Microsoft Intune - Febbraio 2020

Per supportare gli utenti nella preparazione e pianificazione, questa pagina illustra gli aggiornamenti e le funzionalità dell'interfaccia utente di Intune che sono in fase di sviluppo ma non ancora rilasciati. Oltre alle informazioni contenute in questa pagina: 

- Se sono previste azioni prima di una modifica, verrà pubblicato un post complementare nel Centro messaggi di Office.
- Quando una funzionalità entra in produzione, sia in versione anteprima sia disponibile a livello generale, la descrizione della funzionalità viene spostata da questa pagina alla [pagina delle novità](whats-new.md).
- Questa pagina e la [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere la [roadmap di Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per informazioni sulle sequenze temporali e i risultati finali strategici.

> [!NOTE]
> Questa pagina riflette le attuali aspettative sulle funzionalità di Intune che verranno introdotte in una versione futura. Le date e le singole funzionalità potrebbero cambiare. Questa pagina non descrive tutte le funzionalità in fase di sviluppo.

**Feed RSS**: è possibile sapere quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Visualizzare le notifiche per l'app Portale aziendale in Windows<!-- 1808082  -->
L'app Portale aziendale nei dispositivi Windows verrà aggiornata in modo da visualizzare le notifiche di tipo avviso popup agli utenti, anche quando l'applicazione è chiusa. L'aggiornamento mostrerà le notifiche per le app disponibili solo quando lo stato dell'installazione è completato o non riuscito. L'app Portale aziendale non mostrerà le notifiche relative alle applicazioni richieste. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visualizzare i messaggi di stato dell'installazione per l'app Portale aziendale<!-- 2514416  -->
L'app Portale aziendale mostrerà i messaggi aggiuntivi sullo stato dell'installazione dell'app per gli utenti finali. Alle nuove funzionalità di dipendenza Win32 verranno applicate le condizioni seguenti:
- Non è stato possibile installare l'app. Le dipendenze definite dall'amministratore non sono state soddisfatte.

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Ridestinare le clip Web a Microsoft Edge nei dispositivi iOS/iPadOS<!-- 5455276 -->
Le clip Web, che fungono da app Web bloccate nei dispositivi iOS/iPadOS, dovranno essere aggiornate. Le clip Web appena distribuite verranno aperte in Microsoft Edge anziché in Intune Managed Browser, se devono essere aperte in un browser protetto. È necessario ridestinare le clip Web preesistenti per assicurarsi che per l'apertura venga usato Microsoft Edge invece di Managed Browser.

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>Miglioramenti dell'esperienza utente per Portale aziendale macOS<!-- 5568987 -->
Sono stati apportati miglioramenti all'esperienza di registrazione dei dispositivi macOS e all'app Portale aziendale per Mac. I miglioramenti previsti sono i seguenti:
- Una migliore esperienza di Microsoft **AutoUpdate** durante la registrazione che garantirà agli utenti di disporre della versione più recente dell'app Portale aziendale.
- Un passaggio di controllo della conformità migliorato durante la registrazione.
- Supporto per la copia degli ID di evento imprevisto, in modo che gli utenti possano inviare più velocemente errori dai propri dispositivi al team di supporto tecnico aziendale.

Per altre informazioni sulla registrazione e sull'app Portale aziendale per Mac, vedere Registrare il dispositivo macOS usando l'app Portale aziendale (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp). 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Schermata rimossa da Portale aziendale, registrazione del profilo di lavoro Android<!--6103987 -->
La schermata **Passaggi successivi** verrà rimossa dal flusso di registrazione del profilo di lavoro Android in Portale aziendale per semplificare l'esperienza utente. Passare a [Eseguire la registrazione con il profilo di lavoro Android]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile) per visualizzare il flusso di registrazione del profilo di lavoro Android corrente.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>App Microsoft Defender Advanced Threat Protection (ATP) per macOS<!-- 5424518 idready -->
Intune fornirà un modo semplice per distribuire l'app Microsoft Defender Advanced Threat Protection (ATP) per macOS nei dispositivi Mac gestiti. Per altre informazioni, vedere [Microsoft Defender Advanced Threat Protection per Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac). 

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profili di configurazione della rete cablata per i dispositivi macOS<!-- 3508686  -->
Sarà disponibile un nuovo profilo di configurazione del dispositivo macOS che configura le reti cablate (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **MacOS** per la piattaforma > **Rete cablata** per il tipo di profilo). Usare questa funzionalità per creare profili 802.1x per gestire le reti cablate e distribuire tali reti nei dispositivi macOS.

Si applica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>I profili VPN con connessioni VPN IKEv2 possono usare Always On con i dispositivi iOS/iPadOS <!-- 1947932 idready -->
Nei dispositivi iOS/iPadOS è possibile creare un profilo VPN che usa una connessione IKEv2 (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **VPN** per il tipo di profilo). In un aggiornamento futuro sarà possibile configurare Always On con IKEv2. Quando sono configurati, i profili VPN IKEv2 si connettono automaticamente e rimangono connessi (o si riconnettono rapidamente) alla rete VPN. Rimangono connessi anche quando si passa da una rete a un'altra o si riavviano i dispositivi.

In iOS/iPadOS la VPN Always On è limitata ai profili IKEv2.

Per visualizzare le impostazioni IKEv2 correnti che è possibile configurare, vedere [Aggiungere impostazioni VPN in dispositivi iOS/iPadOS in Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Si applica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Esperienza migliorata dell'interfaccia utente per la creazione dei profili di configurazione nei dispositivi iOS/iPadOS e macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
L'esperienza per la creazione di un profilo per i dispositivi iOS/iPadOS o macOS nell'interfaccia di amministrazione di Endpoint Manager verrà aggiornata. Questa modifica ha effetto sui profili di configurazione dei dispositivi elencati di seguito (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **iOS** o **macOS** per la piattaforma):

- Personalizzata: iOS/iPadOS, macOS
- Funzionalità del dispositivo: iOS/iPadOS, macOS
- Limitazioni del dispositivo: iOS/iPadOS, macOS
- Endpoint Protection: macOS
- Estensioni: macOS
- File delle preferenze: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Esperienza migliorata dell'interfaccia utente per la creazione dei profili di configurazione OEMConfig nei dispositivi Android Enterprise<!-- 5568645 idready  -->
L'esperienza per la creazione o la modifica di un profilo OEMConfig per i dispositivi Android Enterprise nell'interfaccia di amministrazione di Endpoint Manager verrà aggiornata. Nell'esperienza aggiornata sarà disponibile una panoramica di riepilogo delle impostazioni configurate. Questa modifica ha effetto sul profilo di configurazione del dispositivo di OEMConfig (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **Android Enterprise** per la piattaforma > **OEMConfig** per il tipo di profilo).

Questa funzionalità si applica a:
- Android Enterprise 


<!-- ***********************************************-->
<!--## Device enrollment-->


<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Modificare l'utente primario per i dispositivi Windows <!-- 3794742 -->
Sarà possibile modificare l'utente primario per i dispositivi Windows ibridi e aggiunti ad Azure AD. A tale scopo, passare a **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo **Proprietà** > **Utente primario**. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Numero di serie nella pagina Certificato push MDM Apple<!--5947765 -->
Nella pagina Certificato push MDM Apple verrà visualizzato il numero di serie. Il numero di serie è necessario per ottenere nuovamente l'accesso al certificato per le notifiche push MDM Apple in caso di impossibilità di accedere all'ID Apple usato per creare il certificato. Per visualizzare il numero di serie, passare a **Dispositivi** > **iOS** > **Registrazione iOS** > **Certificato push MDM Apple**.

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>Scegliere gli aggiornamenti di iOS/iPadOS di cui eseguire il push nei dispositivi registrati<!--5879689 -->
Sarà possibile scegliere un aggiornamento specifico di iOS/iPadOS per eseguire il push nei dispositivi registrati tramite Apple Business Manager o Apple School Manager. Per i dispositivi di questo tipo devono essere impostati criteri di configurazione del dispositivo per ritardare la visibilità degli aggiornamenti software per un determinato numero di giorni. Per visualizzare questa funzionalità, passare a MEM > **Dispositivi** > **iOS** > **Criteri di aggiornamento per iOS/iPadOS** > **Crea profilo**.

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>Nuove opzioni di pianificazione degli aggiornamenti per il push degli aggiornamenti del sistema operativo nei dispositivi iOS/iPadOS registrati<!--5879689-->
Quando si pianificano gli aggiornamenti del sistema operativo per i dispositivi iOS/iPadOS, sarà possibile scegliere tra le opzioni seguenti. Ciò vale per i dispositivi che hanno usato i tipi di registrazione Apple Business Manager o Apple School Manager.
- Aggiorna alla sincronizzazione successiva
- Aggiorna durante l'orario pianificato
- Aggiorna in orari diversi da quello pianificato

Per le ultime due opzioni, è possibile creare più finestre temporali.

Per visualizzare le nuove opzioni, passare a MEM > **Dispositivi** > **iOS** > **Criteri di aggiornamento per iOS/iPadOS** > **Crea profilo**.


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoraggio e risoluzione dei problemi

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Ottimizzazione dell'esperienza di creazione di report di Intune<!-- 3791418 idready -->
Intune offre ora un'esperienza ottimizzata per la creazione dei report, inclusi i nuovi tipi, una migliore organizzazione dei report, visualizzazioni più mirate, funzionalità avanzate per i report, nonché dati più coerenti e tempestivi. L'esperienza di creazione di report passerà dalla versione di anteprima pubblica alla versione disponibile a livello generale. Inoltre, la versione disponibile a livello generale fornirà supporto per la localizzazione, correzioni di bug, miglioramenti della progettazione e dati di conformità dei dispositivi aggregati nei riquadri nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

I nuovi tipi di report sono incentrati sugli elementi seguenti:
- **Operativo**: contiene record aggiornati concentrati sugli stati negativi dell'integrità. 
- **Organizzativo**: offre un riepilogo più ampio dello stato generale.
- **Cronologico**: offre modelli e tendenze nell'arco di un determinato periodo di tempo.
- **Specialistico**: consente di usare i dati non elaborati per creare i propri report personalizzati.

Il primo set di nuovi report è incentrato sulla conformità del dispositivo. Per altre informazioni, vedere il [post di blog sul framework di reporting di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) e [Report di Intune](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Modifiche all'interfaccia utente dei ruoli di Intune presto disponibili<!--5801612 idready-->
L'esperienza utente per [Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Amministrazione del tenant** > **Ruoli** sarà più semplice e intuitiva. La nuova esperienza fornisce le stesse impostazioni e gli stessi dettagli attualmente presenti, ma consentirà di visualizzare e definire i ruoli tramite un processo simile a una procedura guidata.


<!-- ***********************************************-->
## <a name="security"></a>Sicurezza

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Supporto di credenziali derivate nei dispositivi Android COBO<!--4839592-->
Sarà possibile usare credenziali derivate nei dispositivi Android Enterprise completamente gestiti. Verrà incluso il supporto per il recupero di una credenziale derivata per Entrust Datacard, Intercede e DISA Purebred. Sarà possibile usare una credenziale derivata per l'autenticazione di app, Wi-Fi, VPN o la firma S/MIME e/o la crittografia, se supportata dalle app.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Usare i criteri antivirus per gestire le impostazioni per Microsoft Defender Antivirus e l'esperienza di Sicurezza di Windows<!--6131401 -->
Dal nodo *Sicurezza degli endpoint* sarà possibile configurare le impostazioni per l'**antivirus**. Quando si configurano i criteri per l'antivirus, si definiscono le impostazioni per i dispositivi Windows 10 tramite due tipi di profilo:

- Microsoft Defender Antivirus: consente di gestire le impostazioni per la protezione del cloud, le esclusioni dell'antivirus, la correzione, le opzioni di analisi e altro ancora.
- Esperienza di Sicurezza di Windows: consente di gestire il modo in cui gli utenti usano le impostazioni di Sicurezza di Windows nei dispositivi. Sarà possibile configurare gli elementi visualizzabili dagli utenti finali in Microsoft Defender Security Center e le notifiche ricevute. 

<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


