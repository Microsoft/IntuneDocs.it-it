---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260232"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>In fase di sviluppo per Microsoft Intune - Marzo 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Ridestinare le clip Web a Microsoft Edge nei dispositivi iOS/iPadOS<!-- 5455276 -->
Le clip Web, che fungono da app Web bloccate nei dispositivi iOS/iPadOS, dovranno essere aggiornate. Le clip Web appena distribuite verranno aperte in Microsoft Edge anziché in Intune Managed Browser, se devono essere aperte in un browser protetto. È necessario ridestinare le clip Web preesistenti per assicurarsi che per l'apertura venga usato Microsoft Edge invece di Managed Browser.

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>Aggiornamenti del Portale aziendale macOS e iOS<!-- 5779439, 5780234  -->
Il riquadro del profilo del Portale aziendale macOS e iOS verrà aggiornato in modo da includere il pulsante di disconnessione. Questo aggiornamento includerà anche i miglioramenti dell'interfaccia utente nel riquadro del profilo del Portale aziendale macOS. Per altre informazioni sul Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>Aggiornamenti apportati al riquadro Personalizzazione<!-- 5236032 -->
È in corso l'aggiornamento del riquadro di Intune attualmente denominato "Personalizzazione", a cui verranno apportati i miglioramenti seguenti:

- Il nome del riquadro, **Personalizzazione**, resterà invariato.
- Miglioramento dell'organizzazione e della progettazione delle impostazioni.
- Miglioramento del testo delle impostazioni e delle descrizioni comando.

Per trovare queste impostazioni in Intune, passare all'[Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e selezionare **Amministrazione del tenant** > **Personalizzazione**. Per informazioni sulla personalizzazione esistente, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>Configurare l'estensione dell'app SSO di Microsoft Azure AD per iOS<!-- 567534  -->
Il team di Microsoft Azure AD sta sviluppando un'estensione di app SSO (Single Sign-On) di reindirizzamento per consentire agli utenti di iOS e iPadOS 13.0 e versioni successive di accedere facilmente ad app e siti Web Microsoft con un unico accesso. Quando l'estensione dell'app SSO AAD verrà rilasciata, sarà possibile configurare l'estensione SSO con il profilo **Funzionalità del dispositivo** > **Estensione dell'app per l'accesso Single Sign-On** nella console di amministrazione con pochi clic del mouse. 

Per altre informazioni sulle estensioni delle app SSO per iOS o su come configurare le funzionalità del dispositivo, vedere [Estensione dell'app Single Sign-On](~/configuration/device-features-configure.md#single-sign-on-app-extension).

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>Portale aziendale per iOS per supportare la modalità orizzontale<!--6048329  -->
Gli utenti potranno registrare i dispositivi, trovare le app e ottenere supporto IT usando l'orientamento dello schermo preferito. L'app rileverà automaticamente l'orientamento adattandosi allo schermo in modalità verticale o orizzontale, a meno che gli utenti non blocchino lo schermo in modalità verticale. 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>Stabilire se la registrazione è disponibile nel Portale aziendale per Android e iOS<!-- 4260128 idready idstaged -->
Sarà disponibile una nuova impostazione che consente di configurare se la registrazione dei dispositivi nel Portale aziendale sui dispositivi Android e iOS è disponibile con prompt, disponibile senza prompt o non disponibile per gli utenti. Per trovare queste impostazioni in Intune, passare all'[Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e selezionare **Amministrazione del tenant** > **Personalizzazione** > **Modifica** > **Registrazione del dispositivo**. Per altre informazioni sulla personalizzazione del Portale aziendale esistente, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>Esperienza di accesso aggiornata nel Portale aziendale per Android<!-- 6103997  -->
È in corso l'aggiornamento del layout di diverse schermate di accesso nell'app Portale aziendale per Android per rendere l'esperienza più moderna, semplice e pulita per gli utenti.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profili di configurazione della rete cablata per i dispositivi macOS<!-- 3508686  -->
Sarà disponibile un nuovo profilo di configurazione del dispositivo macOS che configura le reti cablate (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **MacOS** per la piattaforma > **Rete cablata** per il tipo di profilo). Usare questa funzionalità per creare profili 802.1x per gestire le reti cablate e distribuire tali reti nei dispositivi macOS.

Si applica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>I profili VPN con connessioni VPN IKEv2 possono usare Always On con i dispositivi iOS/iPadOS <!-- 1947932  -->
Nei dispositivi iOS/iPadOS è possibile creare un profilo VPN che usa una connessione IKEv2 (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **VPN** per il tipo di profilo). In un aggiornamento futuro sarà possibile configurare Always On con IKEv2. Quando sono configurati, i profili VPN IKEv2 si connettono automaticamente e rimangono connessi (o si riconnettono rapidamente) alla rete VPN. Rimangono connessi anche quando si passa da una rete a un'altra o si riavviano i dispositivi.

In iOS/iPadOS la VPN Always On è limitata ai profili IKEv2.

Per visualizzare le impostazioni IKEv2 correnti che è possibile configurare, vedere [Aggiungere impostazioni VPN in dispositivi iOS/iPadOS in Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Si applica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>Esperienza migliorata dell'interfaccia utente per la creazione dei profili di configurazione nei dispositivi iOS/iPadOS e macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
L'esperienza per la creazione di un profilo per i dispositivi iOS/iPadOS o macOS nell'interfaccia di amministrazione di Endpoint Manager verrà aggiornata. Questa modifica ha effetto sui profili di configurazione dei dispositivi elencati di seguito (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **iOS** o **macOS** per la piattaforma):

- Personalizzata: iOS/iPadOS, macOS
- Funzionalità del dispositivo: iOS/iPadOS, macOS
- Limitazioni del dispositivo: iOS/iPadOS, macOS
- Endpoint Protection: macOS
- Estensioni: macOS
- File delle preferenze: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>Esperienza migliorata dell'interfaccia utente per la creazione dei profili di configurazione OEMConfig nei dispositivi Android Enterprise<!-- 5568645   -->
L'esperienza per la creazione o la modifica di un profilo OEMConfig per i dispositivi Android Enterprise nell'interfaccia di amministrazione di Endpoint Manager verrà aggiornata. Nell'esperienza aggiornata sarà disponibile una panoramica di riepilogo delle impostazioni configurate. Questa modifica ha effetto sul profilo di configurazione del dispositivo di OEMConfig (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **Android Enterprise** per la piattaforma > **OEMConfig** per il tipo di profilo).

Questa funzionalità si applica a:
- Android Enterprise 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>L'impostazione Modifica delle impostazioni di attendibilità delle app aziendali verrà rimossa dai profili di limitazioni dei dispositivi iOS/iPadOS<!-- 6225131  -->
Nei dispositivi iOS/iPadOS creare un profilo di limitazioni del dispositivo (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). L'impostazione **Modifica delle impostazioni di attendibilità delle app aziendali** verrà rimossa da Apple e verrà rimossa da Intune. Se questa impostazione è attualmente in uso in un profilo, non avrà alcun effetto e rimarrà nel profilo fino a quando non si creerà un nuovo profilo. Questa impostazione verrà rimossa anche dalle creazioni di report in Intune.

Si applica a:
- iOS/iPadOS

Per visualizzare le impostazioni che è possibile limitare, vedere [Impostazioni dei dispositivi iOS e iPadOS per consentire o limitare funzionalità](../configuration/device-restrictions-ios.md).

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>Le impostazioni e i valori del profilo di configurazione del dispositivo verranno aggiornati per le piattaforme Windows<!-- 4091122 -->
Quando si creano profili di configurazione dei dispositivi per le piattaforme Windows (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > qualsiasi opzione **Windows** per la piattaforma), alcune impostazioni e i relativi valori sono diversi da quelli del provider CSP e potrebbero generare confusione. I nomi delle impostazioni e i relativi valori verranno aggiornati in modo da essere più chiari.

Si applica a:

- Profilo di configurazione dei dispositivi Windows 10 e versioni successive
- Profili di configurazione dei dispositivi Windows Holographic for Business
- Profili di configurazione dei dispositivi Windows 8.1
- Profili di configurazione dei dispositivi Windows Phone 8.1

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>Esperienza migliorata dell'interfaccia utente per la creazione dei profili di limitazioni dei dispositivi in dispositivi Android e Android Enterprise<!-- 5841361 -->
L'esperienza per la creazione di un profilo per i dispositivi Android e Android Enterprise nell'interfaccia di amministrazione di Endpoint Manager verrà aggiornata. Questa modifica ha effetto sui profili di configurazione dei dispositivi seguenti (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **Amministratore di dispositivi Android** o **Android Enterprise** per la piattaforma):

- Limitazioni dei dispositivi: Amministratore dispositivo Android
- Limitazioni dei dispositivi: Proprietario del dispositivo Android Enterprise
- Limitazioni dei dispositivi: Profilo di lavoro di Android Enterprise

Per altre informazioni sulle restrizioni dei dispositivi che è possibile configurare, vedere [Amministratore di dispositivi Android](../configuration/device-restrictions-android.md) e [Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>Eliminare aggregazioni e matrici di aggregazioni nei profili di configurazione dei dispositivi OEMConfig sui dispositivi Android Enterprise<!-- 5550355  -->
Nei dispositivi Android Enterprise è possibile creare e aggiornare i profili OEMConfig. Gli utenti potranno eliminare aggregazioni e matrici di aggregazioni usando **Progettazione configurazione** in Intune.

Per altre informazioni sui profili OEMConfig, vedere [Usare e gestire i dispositivi Android Enterprise con OEMConfig in Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Questa funzionalità si applica a:
- Android Enterprise

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>Supporto per WPA e WPA2 nei profili Wi-Fi enterprise per iOS<!--6215273   -->
È in corso l'aggiunta del campo *Tipo di sicurezza* al [profilo Wi-Fi enterprise per iOS](../configuration/wi-fi-settings-ios.md) (**Dispositivi** > **Profili di configurazione** > **Crea profilo** e selezionare **iOS/iPadOS** per *Piattaforma* e quindi **Wi-Fi** per *Profilo*). È simile alle opzioni disponibili per un profilo Wi-Fi di base per iOS. Con questa modifica sarà possibile creare nuovi profili che specificano un tipo di sicurezza **WPA-Enterprise** o **WPA/WPA2-Enterprise** e quindi specificare una selezione per *Tipo EAP*.

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>Nuova esperienza utente per i profili di certificato, posta elettronica, VPN e Wi-Fi<!-- 5615208   -->
È in corso l'aggiornamento dell'[esperienza utente](../configuration/device-profile-create.md) nell'interfaccia di amministrazione di Endpoint Management (**Dispositivi** > **Profili di configurazione** > **Crea profilo**) per la creazione e la modifica dei tipi di profili seguenti. La nuova esperienza presenta le stesse impostazioni di prima, ma usa un'esperienza di tipo procedura guidata che richiede meno azioni di scorrimento orizzontale. Non è necessario modificare le configurazioni esistenti con la nuova esperienza.
- Credenziale derivata
- Posta elettronica
- Certificato PKCS
- Certificato importato PKCS
- Certificato SCEP
- Certificato attendibile
- Connessione
- Wi-Fi

**Dispositivi** > **Profili di configurazione** > **Crea profilo** e quindi per *Tipo di profilo* selezionare uno dei profili precedenti.

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>Configurare l'app Microsoft Defender ATP per macOS  <!-- 5520115  -->
A breve sarà possibile configurare le [impostazioni](../protect/endpoint-protection-macos.md) per l'app Microsoft Defender ATP per i dispositivi che eseguono macOS come parte di un profilo di configurazione di un dispositivo Endpoint Protection (**Dispositivi** > **Profili di configurazione** > **Crea profilo**, selezionare **macOS** per *Piattaforma* e quindi **Endpoint Protection** per *Tipo di profilo*). Per la configurazione del dispositivo macOS saranno presenti otto impostazioni. 

Defender ATP è supportato in macOS 10.13 (High Sierra) e versioni successive e l'app [Microsoft Defender ATP](../apps/apps-advanced-threat-protection-macos.md) deve essere distribuita nel dispositivo *dopo* l'applicazione di queste impostazioni. Le impostazioni devono essere inviate al dispositivo prima della distribuzione dell'app. Le versioni beta di macOS non saranno supportate.

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>Nuova impostazione FileVault per i criteri di configurazione del dispositivo Endpoint Protection per macOS<!-- 5459801   -->
È in corso l'aggiunta di una nuova impostazione alla categoria FileVault nel modello di [Endpoint Protection per macOS](../protect/endpoint-protection-macos.md): Nascondi la chiave di ripristino (**Dispositivi** > **Profili di configurazione** > **Crea profilo**, selezionare **macOS** per *Piattaforma* e quindi **Endpoint Protection** per *Tipo di profilo*). Questa impostazione nasconde la chiave personale all'utente finale durante la crittografia FileVault 2. Un utente di un dispositivo può visualizzare la chiave di ripristino personale in qualsiasi momento dall'app Portale aziendale di iOS o dal sito Web del portale aziendale per il dispositivo macOS crittografato. Per visualizzare la chiave di ripristino personale, può passare ai dettagli del dispositivo e fare clic su *Ottieni la chiave di ripristino*.

Questa impostazione non sarà disponibile nei criteri creati in precedenza. Per configurare questa impostazione e poterla usare, sarà necessario ricreare i criteri di FileVault. 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>Aggiornamento dell'interfaccia utente durante la configurazione dei criteri di conformità <!-- 3961639  -->
È in corso l'aggiornamento dell'interfaccia utente per la configurazione dei criteri di conformità in Microsoft Endpoint Manager (**Dispositivi** > **Criteri di conformità** > **Criteri** > **Crea criterio**). Verrà visualizzata una nuova esperienza utente con le stesse impostazioni e dettagli usati in precedenza. La nuova esperienza seguirà un processo di tipo procedura guidata per creare un criterio di conformità e includerà la pagina in cui è possibile aggiungere *Assegnazioni* come criterio e quindi una pagina *Riepilogo* in cui è possibile esaminare la configurazione prima di creare il criterio. 

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>Configurare l'agente di ottimizzazione recapito durante il download del contenuto dell'app Win32<!-- 5410945  -->
Sarà possibile configurare l'agente di ottimizzazione recapito per scaricare il contenuto dell'app Win32 in background o in primo piano in base all'assegnazione. Per le app Win32 esistenti, il contenuto continuerà a essere scaricato in background. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**. Selezionare **Windows 10 e versioni successive** come **Piattaforma**. In **Tipo di profilo** selezionare **Ottimizzazione recapito**. Per altre informazioni sull'ottimizzazione recapito, vedere [Gestione delle app Win32 - Ottimizzazione recapito](~/apps/apps-win32-app-management.md#delivery-optimization).


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Modificare l'utente primario per i dispositivi Windows <!-- 3794742 -->
Sarà possibile modificare l'utente primario per i dispositivi Windows ibridi e aggiunti ad Azure AD. A tale scopo, passare a **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo **Proprietà** > **Utente primario**. 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>Nuovo report Android nella pagina di panoramica dei dispositivi Android<!-- 5435435 -->
Verrà aggiunto un report alla console di amministrazione di Microsoft Endpoint Manager nella pagina di panoramica dei dispositivi Android che visualizza il numero di dispositivi Android registrati in ogni soluzione di gestione dei dispositivi. Questo grafico (corrispondente al grafico già presente nella console di Azure) mostra il numero di dispositivi registrati con profilo di lavoro, completamente gestiti, dedicati e con registrazione di tipo amministratore di dispositivi. Per visualizzare il report, scegliere **Dispositivi** > **Android** > **Panoramica**.

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>Supporto degli script di PowerShell per dispositivi BYOD<!-- 1862833  -->
Gli script di PowerShell supporteranno i dispositivi registrati con Azure AD in Intune. Per altre informazioni su PowerShell, vedere [Usare gli script di PowerShell nei dispositivi Windows 10 in Intune](~/apps/intune-management-extension.md). Questa funzionalità non supporta i dispositivi che eseguono Windows 10 Home Edition.

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>Proprietà aggiuntive per l'inventario dei dispositivi tramite data warehouse<!-- 6125732  -->
Le proprietà aggiuntive per l'inventario dei dispositivi saranno disponibili tramite il data warehouse di Intune. Le proprietà seguenti verranno esposte tramite la raccolta dei [dispositivi](~/developer/intune-data-warehouse-collections.md#devices):
- Capacità di archiviazione 
- Capacità di memoria
- Versione di Office 365
- modello del dispositivo

Per altre informazioni sul data warehouse, vedere [API data warehouse di Microsoft Intune](~/developer/reports-nav-intune-data-warehouse.md).

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>Guidare gli utenti dalla gestione degli amministratori dei dispositivi Android alla gestione del profilo di lavoro<!--5857738-->
È in corso il rilascio di una nuova impostazione di conformità per la piattaforma degli amministratori dei dispositivi Android. Questa impostazione consente di rendere un dispositivo non conforme se gestito con l'amministratore del dispositivo.

In questi dispositivi non conformi gli utenti visualizzeranno il messaggio **Passa alla configurazione della gestione dei nuovi dispositivi** nella pagina **Aggiorna impostazioni del dispositivo**. Toccando il pulsante **Risolvi**, verranno fornite indicazioni dettagliate su:

1. Annullamento della registrazione nella gestione degli amministratori dei dispositivi
2. Registrazione nella gestione del profilo di lavoro
3. Risoluzione dei problemi di conformità 
 
Google sta riducendo il supporto per l'amministratore di dispositivi nelle nuove versioni di Android con l'obiettivo di passare a una gestione dei dispositivi moderna, più ricca e sicura con Android Enterprise.  Intune può offrire supporto completo per i dispositivi Android gestiti dall'amministratore di dispositivi che eseguono Android 10 e versioni successive solo fino al secondo trimestre del 2020. I dispositivi gestiti dall'amministratore di dispositivi (tranne i dispositivi Samsung) che eseguono Android 10 o versione successiva in seguito non potranno più essere gestiti interamente. In particolare, i dispositivi interessati non riceveranno nuovi requisiti per le password. Per altre informazioni, vedere questo [avviso](#decreasing-support-for-android-device-administrator).

### <a name="retire-noncompliant-devices---1827291---"></a>Ritirare i dispositivi non conformi<!-- 1827291 -->
È in corso l'aggiunta di una nuova azione di conformità facoltativa per ritirare un dispositivo non conforme (**Dispositivi** > **Criteri di conformità** > **Criteri** > **Crea criterio** e quindi visualizzare le *azioni* disponibili nella pagina *Azioni per la non conformità*).  Il ritiro di un dispositivo non conforme comporta la rimozione di tutti i dati aziendali dal dispositivo e la rimozione di quest'ultimo dalla gestione di Intune. Questa azione viene eseguita quando viene raggiunto il valore configurato in giorni. Il valore minimo è 30 giorni.  Sarà necessaria l'approvazione esplicita dell'amministratore IT per ritirare i dispositivi usando la sezione *Disattiva i dispositivi non conformi*, in cui gli amministratori possono ritirare tutti i dispositivi idonei.

### <a name="new-information-in-device-details---5604099---"></a>Nuove informazioni nei dettagli del dispositivo<!-- 5604099 -->
Le informazioni seguenti saranno presenti nella pagina **Panoramica** per i dispositivi:
- Capacità di archiviazione (quantità di spazio di archiviazione fisico nel dispositivo)
- Capacità di memoria (quantità di memoria fisica nel dispositivo)

### <a name="script-support-for-macos-devices---4280361----"></a>Supporto degli script per i dispositivi macOS<!-- 4280361  -->
Sarà possibile aggiungere e distribuire script nei dispositivi macOS. Questo supporto consente di configurare i dispositivi macOS oltre le normali possibilità usando le funzionalità MDM native nei dispositivi macOS. 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>Guida e supporto per l'aggiornamento del flusso di lavoro per supportare servizi aggiuntivi<!-- 5654170 -->
È in corso l'aggiornamento della pagina Guida e supporto tecnico nell'interfaccia di amministrazione di Microsoft Endpoint Manager per poter scegliere il tipo di gestione usato e fornire così un supporto più specifico (**Risoluzione dei problemi e supporto tecnico** >  **Guida e supporto tecnico**). Con questa modifica sarà possibile scegliere tra i tipi di gestione seguenti:
- Configuration Manager (include Desktop Analytics)
- Intune
- Co-gestione

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>Sicurezza

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Supporto di credenziali derivate nei dispositivi Android COBO<!--4839592-->
Sarà possibile usare credenziali derivate nei dispositivi Android Enterprise completamente gestiti. Verrà incluso il supporto per il recupero di una credenziale derivata per Entrust Datacard, Intercede e DISA Purebred. Sarà possibile usare una credenziale derivata per l'autenticazione di app, Wi-Fi, VPN o la firma S/MIME e/o la crittografia, se supportata dalle app.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Usare i criteri antivirus per gestire le impostazioni per Microsoft Defender Antivirus e l'esperienza di Sicurezza di Windows<!--6131401 -->
Dal nodo *Sicurezza degli endpoint* sarà possibile configurare le impostazioni per l'**antivirus**. Quando si configurano i criteri per l'antivirus, si definiscono le impostazioni per i dispositivi Windows 10 tramite due tipi di profilo:

- Microsoft Defender Antivirus: consente di gestire le impostazioni per la protezione del cloud, le esclusioni dell'antivirus, la correzione, le opzioni di analisi e altro ancora.
- Esperienza di Sicurezza di Windows: consente di gestire il modo in cui gli utenti usano le impostazioni di Sicurezza di Windows nei dispositivi. Sarà possibile configurare gli elementi visualizzabili dagli utenti finali in Microsoft Defender Security Center e le notifiche ricevute.

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>Chiave di ripristino crittografata personale dell'utente<!-- 6273943 -->
Sarà disponibile una nuova funzionalità di Intune che consente agli utenti di recuperare la chiave di ripristino **FileVault** crittografata personale per i dispositivi Mac tramite l'applicazione Portale aziendale per Android o tramite l'applicazione Intune per Android. Sia nell'applicazione Portale aziendale che nell'applicazione Intune sarà disponibile un collegamento che aprirà un'istanza del browser Chrome per accedere al portale aziendale Web in cui l'utente può visualizzare la chiave di ripristino **FileVault** necessaria per accedere ai dispositivi Mac. Per altre informazioni sulla crittografia, vedere [Usare la crittografia dei dispositivi con Intune](~/protect/encrypt-devices.md).

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>Impostazioni delle preferenze per la privacy per i dispositivi macOS<!-- 2934232 --> 
Nella versione di macOS Catalina 10.15 Apple ha aggiunto nuovi miglioramenti alla sicurezza e alla privacy. Per impostazione predefinita, le applicazioni e i processi non riescono ad accedere a dati specifici senza il consenso utente. Se gli utenti non forniscono il consenso, le applicazioni e i processi potrebbero non funzionare. In Intune verrà aggiunto il supporto per le impostazioni che permettono agli amministratori IT di accettare o rifiutare il consenso per l'accesso ai dati per conto degli utenti finali nei dispositivi che eseguono macOS 10.14 e versioni successive. Queste impostazioni garantiscono che le applicazioni e i processi continuino a funzionare correttamente e riducono il numero di richieste visualizzate dagli utenti finali. 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>Testo ed etichette dell'interfaccia utente aggiornati per le impostazioni del profilo di Endpoint Protection per Windows 10<!-- 5983747 -->
È in corso l'aggiornamento del testo per le varie impostazioni configurate come profili di configurazione dei dispositivi Windows 10 per rendere più comprensibili l'uso previsto delle impostazioni e i risultati. 

Le impostazioni che verranno aggiornate includono i profili di configurazione dei dispositivi Windows 10 per: 
- [Limitazioni del dispositivo](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Microsoft Defender Antivirus  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Microsoft Defender Antivirus

Le impostazioni supportate con Intune non cambiano. Si tratta solo di un aggiornamento del testo dell'interfaccia utente dell'interfaccia di amministrazione di Microsoft Endpoint Management. 


<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).



