---
title: Novità dei mesi precedenti in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Rileggere gli annunci precedenti dalla pagina delle novità di Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/8/2019
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9748e48175590b1f4b1069c2b6f70dbf8bbeb9ab
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71302640"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novità di Microsoft Intune - mesi precedenti

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

<!-- ########################## -->
## <a name="december-2018"></a>Dicembre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="updates-for-application-transport-security----748318---"></a>Aggiornamenti per Application Transport Security <!-- 748318 -->

Microsoft Intune supporta Transport Layer Security (TLS) 1.2+ per offrire la migliore crittografia, per garantire una maggiore sicurezza per Intune per impostazione predefinita e per allinearsi agli altri servizi Microsoft, ad esempio Microsoft Office 365. Per poter soddisfare questo requisito, i portali aziendali iOS e macOS applicheranno i requisiti di Application Transport Security (ATS) aggiornati di Apple per cui è obbligatorio l'uso di TLS 1.2+. Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale iOS e macOS. Per altre informazioni, vedere il [blog del supporto tecnico di Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK supporterà le chiavi di crittografia a 256 bit <!-- 1832174 -->
Intune App SDK per Android usa ora le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. L'SDK continuerà a supportare le chiavi a 128 bit per garantire la compatibilità con il contenuto e le app che usano versioni precedenti dell'SDK.

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Microsoft Auto Update versione 4.5.0 obbligatorio per i dispositivi macOS <!-- 3503442 -->
Per continuare a ricevere gli aggiornamenti per il portale aziendale e le altre applicazioni di Office, è necessario aggiornare i dispositivi macOS gestiti da Intune a Microsoft Auto Update 4.5.0. Gli utenti potrebbero avere già questa versione per le app di Office.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune richiede macOS 10.12 o versione successiva <!-- 2827778 -->
Intune richiede ora macOS versione 10.12 o successiva. I dispositivi che usano versioni precedenti di macOS non possono usare il portale aziendale per la registrazione in Intune. Per ricevere assistenza e nuove funzionalità, gli utenti devono aggiornare il dispositivo a macOS 10.12 o versione successiva e aggiornare l'app Portale aziendale alla versione più recente.






<!-- ########################## -->
## <a name="november-2018"></a>Novembre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Disinstallazione di app in dispositivi iOS con supervisione di proprietà dell'azienda <!-- 1281677 -->
È possibile rimuovere qualsiasi app nei dispositivi iOS con supervisione di proprietà dell'azienda. È possibile rimuovere qualsiasi app specificando come destinazione gruppi di utenti o dispositivi con un tipo di assegnazione **Disinstalla**. Per i dispositivi iOS personali o senza supervisione, sarà ancora possibile rimuovere solo le app installate usando Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Download del contenuto dell'app Win32 Intune <!-- 2617320 -->
I client Windows 10 RS3 e versioni successive scaricheranno contenuto dell'app Win32 Intune mediante un componente Ottimizzazione recapito nel client Windows 10. Ottimizzazione recapito offre funzionalità peer-to-peer attivate per impostazione predefinita. Attualmente è possibile configurare Ottimizzazione recapito tramite Criteri di gruppo. Per altre informazioni, vedere [Ottimizzazione recapito per Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Dispositivo dell'utente finale e menu di scelta rapida delle app <!-- 2771453 -->
Gli utenti finali possono ora usare il menu di scelta rapida nel dispositivo e nelle app per attivare azioni comuni come la ridenominazione di un dispositivo o il controllo della conformità.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Impostare lo sfondo personalizzato nell'app di schermata iniziale gestita  <!-- 3041945 -->
Verrà aggiunta un'impostazione che consente di personalizzare l'aspetto dello sfondo dell'app di schermata iniziale gestita nei dispositivi Android Enterprise in modalità tutto schermo per più app.  Per configurare lo **sfondo personalizzato per l'URL**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Salvataggio e applicazione dell'assegnazione dei criteri di protezione dell'app <!-- 3104570 -->
È disponibile un maggiore controllo sulle [assegnazioni dei criteri di protezione dell'app](app-protection-policies.md#deploy-a-policy-to-users). Quando si seleziona *Assegnazioni* per impostare o modificare le assegnazioni dei criteri, è necessario scegliere **Salva** per salvare la configurazione prima che la modifica venga applicata. Usare **Annulla** per cancellare tutte le modifiche apportate senza salvare le modifiche agli elenchi di inclusione o esclusione.  Con la scelta obbligatoria di Salva o Annulla, i criteri di protezione delle app vengono assegnati solo agli utenti previsti.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nuove impostazioni del browser Microsoft Edge per Windows 10 e versioni successive <!-- 3174639 -->
Questo aggiornamento include nuove impostazioni per controllare e gestire il browser Microsoft Edge nei dispositivi. Per un elenco di queste impostazioni correnti, vedere [Restrizione dei dispositivi per Windows 10 (e versioni successive)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Supporto di nuove app con criteri di protezione delle app <!-- 3330037 -->
È ora possibile gestire le app seguenti con i [criteri di protezione delle app di Intune](app-protection-policies.md):
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Usare i criteri di protezione delle app per proteggere i dati aziendali e controllare il trasferimento dei dati per queste app, come per le altre app gestite dai criteri di Intune. Nota: se Flow non è ancora visibile nella console, è possibile aggiungere Flow quando si creano o modificano i criteri di protezione delle app. A tale scopo, usare l'opzione **+ Altre app** e quindi specificare l'*ID app* per Flow nel campo di input. Per Android usare *com.microsoft.flow* e per iOS usare *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Supporto per iOS 12 OAuth nei profili di posta elettronica iOS <!--2155106 -->
I profili di posta elettronica iOS di Intune supportano iOS 12 Open Authorization (OAuth). Per visualizzare questa funzionalità, creare un nuovo profilo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Posta elettronica** per il tipo di profilo), oppure aggiornare un profilo di posta elettronica iOS esistente. Se la funzionalità OAuth viene abilitata in un profilo che è già stato distribuito, agli utenti verrà richiesto di ripetere l'autenticazione e di scaricare nuovamente il messaggio di posta elettronica.

Nella pagina sui [profili di posta elettronica iOS](email-settings-ios.md) sono disponibili altre informazioni sull'uso di OAuth in un profilo di posta elettronica.

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Supporto del controllo accesso alla rete per Citrix SSO per iOS <!-- 3259404 -->
Citrix ha rilasciato un aggiornamento di Citrix Gateway per supportare il controllo accesso alla rete per Citrix SSO per iOS in Intune. È possibile acconsentire esplicitamente per includere un ID dispositivo all'interno di un profilo VPN in Intune e quindi eseguire il push del profilo nei dispositivi iOS. Sarà necessario installare l'aggiornamento più recente di Citrix Gateway per usare questa funzionalità.

In [Configurare le impostazioni VPN nei dispositivi iOS](vpn-settings-ios.md#base-vpn-settings) sono disponibili altre informazioni sull'uso del controllo accesso alla rete, tra cui alcuni requisiti aggiuntivi. 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Vengono visualizzati i numeri di versione e di build di iOS e macOS <!-- 1892471 -->
In **Conformità del dispositivo** > **Conformità del dispositivo** vengono visualizzate le versioni del sistema operativo iOS e macOS che possono essere usate nei criteri di conformità. Questo aggiornamento include il numero di build configurabile per entrambe le piattaforme.
Quando vengono rilasciati aggiornamenti della sicurezza, Apple lascia in genere il numero di versione invariato, ma aggiorna il numero di build. Il numero di build nei criteri di conformità consente di verificare facilmente se è installato l'aggiornamento di una vulnerabilità.
Per usare questa funzionalità, vedere i criteri di conformità di [iOS](compliance-policy-create-ios.md#device-health) e [macOS](compliance-policy-create-mac-os.md#device-properties).

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Gli anelli di aggiornamento verranno sostituiti con le impostazioni di Ottimizzazione recapito per Windows 10 e versioni successive <!-- 2753807 -->
Ottimizzazione recapito è un nuovo profilo di configurazione per Windows 10 e versioni successive. Questa funzionalità offre un'esperienza semplificata per recapitare gli aggiornamenti software ai dispositivi nell'organizzazione. Questo aggiornamento consente anche di distribuire le impostazioni in anelli di aggiornamento nuovi ed esistenti tramite un profilo di configurazione.
Per configurare un profilo di configurazione di ottimizzazione recapito, vedere [Windows 10 (and newer) delivery optimization settings](delivery-optimization-windows.md).(Impostazioni di ottimizzazione recapito di Windows 10 e versioni successive).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Nuove impostazioni relative alle limitazioni dei dispositivi aggiunte ai dispositivi iOS e macOS <!-- 2827760 -->
Questo aggiornamento include nuove impostazioni per i dispositivi iOS e macOS che vengono rilasciati con iOS 12:

**Impostazioni iOS**: 
- Generale: blocca la rimozione di app (solo con supervisione)
- Generale: blocca la modalità USB con restrizioni (solo con supervisione)
- Generale: imponi data e ora automatiche (solo con supervisione)
- Password: blocca il riempimento automatico delle password (solo con supervisione)
- Password: blocca le richieste di prossimità password (solo con supervisione)
- Password: blocca la condivisione delle password (solo con supervisione)

**Impostazioni macOS**: 
- Password: blocca riempimento automatico password
- Password: blocca le richieste di prossimità password
- Password: blocca la condivisione delle password

Per altre informazioni su queste impostazioni, vedere le impostazioni relative alle limitazioni dei dispositivi [iOS](device-restrictions-ios.md) e [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Supporto di Autopilot per i dispositivi ibridi aggiunti ad Azure Active Directory (anteprima) <!-- 1048100-->
È ora possibile configurare i dispositivi ibridi aggiunti ad Azure Active Directory usando Autopilot. I dispositivi devono essere aggiunti alla rete dell'organizzazione per usare la funzionalità ibrida di Autopilot. Per altre informazioni, vedere [Distribuire dispositivi aggiunti ad Azure AD ibrido con Intune e Windows Autopilot](windows-autopilot-hybrid.md).
Questa funzionalità verrà implementata nella base di utenti nei prossimi giorni. Di conseguenza, sarà possibile seguire questa procedura solo dopo l'implementazione nel proprio account.

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selezionare le app registrate nella pagina Stato di registrazione<!-- 2531007 -->
È possibile scegliere le app di cui tenere traccia nella pagina Stato di registrazione. Fino a quando non vengono installate queste app, l'utente non può usare il dispositivo. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Cercare dispositivi Autopilot in base al numero di serie <!--2595788 -->
È ora possibile cercare i dispositivi Autopilot in base al numero di serie. A tale scopo, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > digitare un numero di serie nella casella **Cerca per numero di serie** > premere INVIO.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Tenere traccia dell'installazione di Office ProPlus <!--2620217 -->
Gli utenti possono tenere traccia dello stato dell'installazione di [Office ProPlus](apps-add-office365.md) tramite la pagina [Stato di registrazione](windows-enrollment-status.md). Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invierà un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Supporto di Device Enrollment Program di macOS per gli account Apple School Manager <!--3006133 -->
Intune supporta ora l'uso di Device Enrollment Program nei dispositivi macOS per gli account Apple School Manager.  Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS con Device Enrollment Program o Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="new-intune-device-subscription-sku---3312071--"></a>Nuovo SKU per la sottoscrizione del dispositivo Intune <!--3312071-->
È ora disponibile un nuovo SKU per la sottoscrizione basato sul dispositivo che consente alle organizzazioni di ridurre i costi di gestione dei dispositivi. Questo SKU per dispositivo Intune viene concesso in licenza per ogni dispositivo su base mensile. Il prezzo varia in base al programma di licenza. È disponibile direttamente tramite l'interfaccia di amministrazione di Microsoft 365 e tramite il [Contratto Enterprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2), il [Contratto per i Prodotti e i Servizi Microsoft](https://www.microsoft.com/licensing/mpsa/default), i [contratti Microsoft Open](https://partner.microsoft.com/licensing/licensing-agreements) e [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Sospendere temporaneamente la modalità tutto schermo nei dispositivi Android per apportare modifiche <!-- 3041935 -->
Quando si usano dispositivi Android in modalità tutto schermo per più app, un amministratore IT potrebbe aver bisogno di apportare modifiche al dispositivo. Questo aggiornamento include nuove impostazioni della modalità tutto schermo per più app che consentono a un amministratore IT di sospendere temporaneamente la modalità tutto schermo tramite un PIN e di ottenere l'accesso all'intero dispositivo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Abilitare il pulsante Pagina iniziale virtuale nei dispositivi in modalità tutto schermo di Android Enterprise  <!-- 3042021 -->
Una nuova impostazione consentirà agli utenti di toccare un pulsante softkey nel dispositivo per passare dall'app di schermata iniziale gestita alle altre app assegnate nel dispositivo in modalità tutto schermo per più app. Questa impostazione è particolarmente utile negli scenari in cui l'app in modalità tutto schermo di un utente non risponde in modo corretto al pulsante "Indietro". Sarà possibile configurare questa impostazione per i dispositivi Android monouso di proprietà dell'azienda. Per abilitare o disabilitare il **pulsante Pagina iniziale virtuale**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).




<!-- ########################## -->
## <a name="october-2018"></a>Ottobre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Accedere alle proprietà principali del profilo tramite l'app Portale aziendale <!-- 772203 -->
Gli utenti finali possono ora accedere alle proprietà e alle azioni principali per l'account, come la reimpostazione della password, dall'app Portale aziendale. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune possono impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non saranno visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Accesso agli account utente delle app Intune nei dispositivi gestiti iOS e Android <!-- 1248496 -->
L'amministratore di Microsoft Intune può controllare gli account utente che vengono aggiunti alle applicazioni di Microsoft Office nei dispositivi gestiti. Può limitare l'accesso agli account utente consentiti dell'organizzazione e bloccare gli account personali nei dispositivi registrati. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Criteri di configurazione delle app di Outlook iOS e Android <!--1828527 -->
È ora possibile creare criteri di configurazione delle app per Outlook per iOS e Android per gli utenti locali che usano l'autenticazione di base con il protocollo ActiveSync. Ulteriori impostazioni di configurazione verranno aggiunte non appena abilitate per Outlook per iOS e Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire sarà possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

#### <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Estensioni file delle app line-of-business (LOB) di Windows <!-- 1884873 -->
Le estensioni file delle app line-of-business di Windows ora includono *msi*, *appx*, *appxbundle*, *msix* e *msixbundle*. È possibile aggiungere un'app in Microsoft Intune selezionando **App client** > **App** > **Aggiungi**. Viene visualizzato il riquadro **Aggiungi app** che consente di selezionare il **Tipo di app**. Per le app line-of-business di Windows, selezionare il tipo di app **App line-of-business**, selezionare il **File del pacchetto dell'app** e quindi specificare un file di installazione con l'estensione appropriata.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Distribuzione di app di Windows 10 con Intune <!-- 2309001 -->
Basandosi sul supporto esistente per le app line-of-business e le app di Microsoft Store per le aziende, gli amministratori possono usare Intune per distribuire la maggior parte delle applicazioni esistenti dell'organizzazione per gli utenti finali in dispositivi Windows 10. Gli amministratori possono aggiungere, installare e disinstallare le applicazioni per gli utenti di Windows 10 in una vasta gamma di formati, ad esempio MSI, Setup.exe o MSP. Intune valuterà le regole dei requisiti prima del download e dell'installazione, notificando agli utenti finali lo stato o i requisiti di riavvio tramite il centro notifiche di Windows 10. Questa funzionalità sbloccherà di fatto le organizzazioni interessate a spostare questo carico di lavoro in Intune e nel cloud. Questa funzionalità è attualmente disponibile in anteprima pubblica e si prevede che verranno aggiunte nuove importanti funzioni nei prossimi mesi. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Dispositivo dell'utente finale e menu di scelta rapida delle app <!-- 2771453 -->
Gli utenti finali possono ora usare il menu di scelta rapida in un dispositivo e nelle app per attivare azioni comuni come la ridenominazione di un dispositivo o la verifica della conformità. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Tasti di scelta rapida del portale aziendale di Windows <!-- 2771518 -->
Gli utenti finali possono usare tasti di scelta rapida per eseguire azioni sulle app e sui dispositivi nell'app Portale aziendale di Windows.

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Richiedere un PIN non biometrico dopo un timeout specificato <!-- 1506985 -->
Se si richiede un PIN non biometrico dopo un timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App client** > **Criteri di protezione delle app** > **Aggiungi criteri** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche. Per informazioni sulle impostazioni di accesso, vedere [Impostazioni iOS](app-protection-policy-settings-ios.md#access-requirements) e [Impostazioni Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Impostazioni per il trasferimento dei dati delle app Intune nei dispositivi iOS registrati in MDM <!-- 2244713 -->
È possibile separare il controllo delle impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM dall'impostazione dell'identità dell'utente registrato, nota anche come nome dell'entità utente (UPN). Gli amministratori che non usano IntuneMAMUPN non noteranno alcuna variazione di comportamento. Quando questa funzionalità è disponibile, gli amministratori che usano IntuneMAMUPN per controllare il trasferimento dei dati nei dispositivi registrati dovranno esaminare le nuove impostazioni e aggiornare le impostazioni dell'app di conseguenza.

#### <a name="windows-10-win32-apps----2617325---"></a>App Win32 di Windows 10 <!-- 2617325 -->
È possibile configurare le app Win32 in modo che vengano installate nel contesto utente per i singoli utenti oppure per tutti gli utenti del dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>App Win32 di Windows e script di PowerShell <!-- 2617330 -->
Gli utenti finali non devono più eseguire l'accesso al dispositivo per installare le app Win32 o eseguire gli script di PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Risoluzione dei problemi di installazione delle app client <!-- 1363711 -->
È possibile risolvere i problemi relativi all'installazione delle app client esaminando la colonna con l'etichetta **Installazione dell'app** nel pannello **Risoluzione dei problemi**. Per visualizzare il pannello **Risoluzione dei problemi**, nel portale di Intune selezionare **Risoluzione dei problemi** in **Guida e supporto tecnico**.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Creare suffissi DNS nei profili di configurazione VPN per i dispositivi che eseguono Windows 10<!-- 1333668 -->
Quando si crea un profilo di configurazione del dispositivo VPN (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo**VPN**) è necessario immettere alcune impostazioni DNS. Con questo aggiornamento, è anche possibile immettere più **suffissi DNS** in Intune. Quando si usano i suffissi DNS, è possibile cercare una risorsa di rete usando il relativo nome breve anziché il nome di dominio completo (FQDN). Questo aggiornamento consente inoltre di modificare l'ordine dei suffissi DNS in Intune.
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md#dns-settings) sono elencate le impostazioni DNS correnti.
Si applica ai dispositivi Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Supporto dei profili di lavoro per le connessioni VPN sempre attive in Android Enterprise <!-- 1333705 -->
In questo aggiornamento è possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise con profili di lavoro gestiti. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
È possibile abilitare la VPN sempre attiva in **Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Android Enterprise** > **Limitazioni del dispositivo** > **Connettività**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emettere certificati SCEP per i dispositivi senza utenti <!-- 1744554 -->
Attualmente, i certificati vengono rilasciati agli utenti. Con questo aggiornamento, è possibile emettere certificati SCEP per i dispositivi, anche i dispositivi senza utente, come quelli con modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Windows 10 e versioni successive** > profilo **Certificato SCEP**). Altri aggiornamenti includono:
- La proprietà **Oggetto** di un profilo SCEP è ora una casella di testo personalizzata e può includere nuove variabili. 
- La proprietà **Nome alternativo del soggetto** di un profilo SCEP è ora un formato di tabella e può includere nuove variabili. Nella tabella un amministratore può aggiungere un attributo e inserire il valore in una casella di testo personalizzata. Nome alternativo del soggetto supporterà gli attributi seguenti: 
  - DNS
  - Indirizzo di posta elettronica
  - UPN

  Queste nuove variabili possono essere aggiunte con testo statico in una casella di testo personalizzata. Ad esempio, l'attributo DNS può essere aggiunto come `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Le parentesi graffe, il punto e virgola e la barra verticale "{} ; |" non funzioneranno nel testo statico di Nome alternativo del soggetto. Per essere accettate per `Subject` o `Subject alternative name`, le parentesi graffe devono racchiudere solo una delle nuove variabili del certificato dispositivo. 

Nuove variabili del certificato dispositivo:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
> - `{{FullyQualifiedDomainName}}` funziona solo per i dispositivi Windows e aggiunti a un dominio. 
> - Quando si specificano proprietà del dispositivo, ad esempio IMEI, numero di serie e nome di dominio completo, nell'oggetto o nel nome alternativo del soggetto per un certificato del dispositivo, tenere presente che queste proprietà possono essere falsificate da una persona con accesso al dispositivo. 

In [Creare un profilo certificato SCEP](certificates-profile-scep.md#create-a-scep-certificate-profile) sono elencate le variabili correnti per la creazione di un profilo di configurazione SCEP. 

Si applica a: Windows 10 e versioni successive e iOS, è supportato per Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Bloccare in remoto i dispositivi non conformi <!-- 2064495 -->
È possibile creare un'azione nei criteri di conformità che blocca in modalità remota il dispositivo non conforme. In Intune > **Conformità del dispositivo** creare un nuovo criterio o selezionare un criterio esistente > **Proprietà**. Selezionare **Azioni per la non conformità** > **Aggiungi** e scegliere di bloccare in remoto il dispositivo.
Supportato in: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e versioni successive 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Miglioramenti del profilo per la modalità tutto schermo per Windows 10 e versioni successive nel portale di Azure <!-- 2748224 -->
Questo aggiornamento include i miglioramenti seguenti per il profilo di configurazione del dispositivo per modalità tutto schermo per Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo**Modalità tutto schermo (anteprima)** ): 
- Attualmente, è possibile creare più profili per modalità tutto schermo sullo stesso dispositivo. Con questo aggiornamento, Intune supporterà un solo un profilo per modalità tutto schermo per ogni dispositivo. Se servono più profili per modalità tutto schermo in un singolo dispositivo, usare un URI personalizzato.
- In un profilo **Più app in modalità tutto schermo** è possibile selezionare le dimensioni del riquadro dell'applicazione e l'ordine del **layout del menu Start** nella griglia dell'applicazione. Se si desidera un maggiore livello di personalizzazione, è possibile continuare a caricare un file XML.
- Le impostazioni del browser in modalità tutto schermo sono state spostate in **Modalità tutto schermo**. Attualmente, le impostazioni **Web browser in modalità tutto schermo** dispongono di una propria categoria nel portale di Azure.
Si applica a: Windows 10 e versioni successive

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Richiesta del PIN quando si modificano le impronte digitali o l'ID del viso in un dispositivo iOS  <!-- 2637704  -->
Agli utenti viene ora richiesto un PIN dopo la modifica dei dati biometrici nel proprio dispositivo iOS. Sono incluse le modifiche per le impronte digitali registrate o l'ID viso. La tempistica della richiesta dipende dalla configurazione del timeout per *Controlla di nuovo i requisiti di accesso dopo (minuti)* .  Se non è impostato alcun PIN, all'utente viene richiesto di configurarne uno. 
 
Questa funzionalità è disponibile solo per iOS e richiede la partecipazione delle applicazioni che integrano Intune APP SDK per iOS, versione 9.0.1 o successive. L'integrazione dell'SDK è necessaria in modo che il comportamento possa essere applicato nelle applicazioni di destinazione. Questa integrazione avviene sistematicamente e dipende dai team delle applicazioni specifiche. Tra le app partecipanti sono inclusi WXP, Outlook, Managed Browser e Yammer.

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Supporto del controllo di accesso alla rete nei client VPN iOS <!-- 1333693 -->
Con questo aggiornamento, è disponibile una nuova impostazione per abilitare il controllo di accesso alla rete quando si crea un profilo di configurazione VPN per Cisco AnyConnect, F5 Access e Citrix SSO per iOS. Questa impostazione consente di includere l'ID controllo di accesso alla rete del dispositivo nel profilo VPN. Non sono attualmente disponibili client VPN o soluzioni partner di controllo di accesso alla rete che supportano questo nuovo ID di controllo di accesso alla rete, ma quando lo saranno, verrà comunicato tramite il [post di blog del supporto](ttps://aka.ms/iOS12_and_vpn).

Per usare il controllo di accesso alla rete, sarà necessario:
1. Acconsentire esplicitamente per permettere a Intune di includere gli ID dei dispositivi nei profili VPN
2. Aggiornare il firmware/software del provider del controllo di accesso alla rete, usando le indicazioni del provider del controllo di accesso alla rete

Per informazioni su questa impostazione in un profilo VPN iOS, vedere [Aggiungere le impostazioni VPN sui dispositivi iOS in Microsoft Intune](vpn-settings-ios.md). Per altre informazioni sul controllo di accesso alla rete, vedere [Integrazione del controllo di accesso alla rete (NAC) con Intune](network-access-control-integrate.md). 

Si applica a: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Rimuovere un profilo di posta elettronica da un dispositivo, anche quando è presente un solo profilo di posta elettronica <!-- 1818139 -->
In precedenza non era possibile rimuovere un profilo di posta elettronica da un dispositivo *se* era l'unico profilo disponibile. Con questo aggiornamento, il comportamento cambia. Ora è possibile rimuovere un profilo di posta elettronica anche se è l'unico profilo di posta elettronica presente nel dispositivo. Per i dettagli, vedere [Add email settings to devices using Intune](email-settings-configure.md) (Aggiungere impostazioni di posta elettronica ai dispositivi con Intune).

#### <a name="powershell-scripts-and-aad----2309469---"></a>Script di PowerShell e AAD <!-- 2309469 -->
Gli script di PowerShell in Intune possono essere destinati ai gruppi di sicurezza dei dispositivi AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nuova impostazione predefinita "Tipo di password richiesto" per Android, Android Enterprise<!-- 2649963 -->
Quando si crea un nuovo criterio di conformità (**Intune** > **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android** o **Android Enterprise** per Piattaforma > Sicurezza del sistema),il valore predefinito di **Tipo di password richiesto** viene modificato:

Da Impostazione predefinita dispositivo ad Almeno numerico

Si applica a: Android, Android Enterprise

Per visualizzare queste impostazioni, vedere [Android](compliance-policy-create-android.md) e [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usare una chiave precondivisa in un profilo Wi-Fi di Windows 10 <!-- 2662938 -->
Con questo aggiornamento, è possibile usare una chiave precondivisa con il protocollo di sicurezza WPA/WPA2-Personal per autenticare un profilo di configurazione Wi-Fi per Windows 10. È anche possibile specificare la configurazione dei costi per una rete a consumo per i dispositivi nell'aggiornamento di Windows 10 di ottobre 2018.

Attualmente, per poter usare una chiave precondivisa è necessario importare un profilo Wi-Fi o creare un profilo personalizzato. In [Impostazioni Wi-Fi per Windows 10](wi-fi-settings-windows.md) sono elencate le impostazioni correnti. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Rimuovere i certificati PKCS e SCEP dai dispositivi <!-- 3218390 -->
In alcuni scenari i certificati PKCS e SCEP rimangono nei dispositivi, anche quando si rimuove un criterio da un gruppo, si elimina una distribuzione di configurazione o conformità o un amministratore aggiorna un profilo SCEP o PKCS esistente. Questo aggiornamento modifica il comportamento. Esistono alcuni scenari in cui i certificati PKCS e SCEP vengono rimossi dai dispositivi e alcuni scenari in cui i certificati rimangono nel dispositivo. Per informazioni su questi scenari, vedere [Rimuovere i certificati SCEP e PKCS in Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Usare Gatekeeper nei dispositivi macOS per la conformità <!-- 2504381 -->
Questo aggiornamento include macOS Gatekeeper per valutare la conformità dei dispositivi. Per impostare la proprietà di Gatekeeper, [aggiungere criteri di conformità per i dispositivi macOS](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Applicare il profilo Autopilot ai dispositivi Windows 10 iscritti ma non ancora registrati per Autopilot <!-- 1558983 -->
È possibile applicare il profilo Autopilot ai dispositivi Windows 10 iscritti che non sono stati ancora registrati per Autopilot. Nel profilo di Autopilot, scegliere l'opzione **Converti tutti i dispositivi interessati in Autopilot** per registrare automaticamente i dispositivi non Autopilot con il servizio di distribuzione Autopilot. L'elaborazione della registrazione può richiedere fino a 48 ore. Quando la registrazione viene annullata e il dispositivo viene reimpostato, Autopilot eseguirà il provisioning.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Creare e assegnare vari profili della pagina Stato registrazione ai gruppi di Azure AD <!-- 2526564 -->
È ora possibile [creare e assegnare](windows-enrollment-status.md) vari profili di pagina relativa allo stato della registrazione ai gruppi di Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migrazione da Device Enrollment Program ad Apple Business Manager in Intune <!--2748613-->
Apple Business Manager (ABM) funziona in Intune ed è possibile aggiornare l'account da Device Enrollment Program (DEP) ad ABM. Il processo in Intune è lo stesso. Per aggiornare l'account Apple da DEP ad ABM, passare a [https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Schede per gli avvisi e lo stato di registrazione nella pagina di panoramica di registrazione del dispositivo <!--2748656-->
Gli avvisi e gli errori di registrazione vengono ora visualizzati in schede separate nella pagina di panoramica di registrazione del dispositivo.

#### <a name="enrollment-abandonment-report----1382924---"></a>Report sull'abbandono delle registrazioni <!-- 1382924 -->
Un nuovo report con i dettagli sulle registrazioni abbandonate è disponibile in **Registrazione del dispositivo** > **Monitoraggio**. Per altre informazioni, vedere [Report Abbandono del portale aziendale](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nuova funzionalità Condizioni per l'utilizzo di Azure Active Directory <!-- 2870393 -->
Azure Active Directory ha una funzionalità Condizioni per l'utilizzo che è possibile usare al posto delle condizioni di Intune esistenti. La funzionalità Condizioni per l'utilizzo di Azure AD offre maggiore flessibilità sule condizioni da visualizzare e su quando visualizzarle, un migliore supporto della localizzazione, maggiore controllo sul rendering delle condizioni e creazione di report migliorata. La funzionalità Condizioni per l'utilizzo di Azure AD richiede Azure Active Directory Premium P1 che fa parte della suite Enterprise Mobility + Security E3. Per altre informazioni, vedere l'articolo [Gestire termini e condizioni aziendali per l'accesso degli utenti](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Supporto della modalità Proprietario dispositivo Android <!--3188762-->
Per Samsung Knox Mobile Enrollment, Intune supporta ora la registrazione dei dispositivi nella modalità di gestione Proprietario dispositivo Android. Gli utenti connessi a reti Wi-Fi o cellulari possono eseguire la registrazione con pochi tocchi quando accendono il dispositivo per la prima volta. Per altre informazioni, vedere [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Registrare automaticamente i dispositivi Android usando Samsung Knox Mobile Enrollment).

### <a name="device-management"></a>Gestione dei dispositivi
#### <a name="new-settings-for-software-updates------1907869---"></a>Nuove impostazioni per gli aggiornamenti software   <!-- 1907869 -->  
- È ora possibile configurare alcune notifiche per avvisare gli utenti finali della necessità di un riavvio per completare l'installazione degli aggiornamenti software più recenti.   
- È ora possibile configurare una richiesta di avviso per i riavvii che vengono eseguiti al di fuori dell'orario di lavoro. Tali richieste supportano gli scenari BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Raggruppare i dispositivi registrati con Windows Autopilot per ID correlatore <!-- 2075110 -->
Intune supporta ora il raggruppamento dei dispositivi Windows per ID correlatore quando vengono registrati usando [Autopilot per i dispositivi esistenti](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) tramite Configuration Manager. L'ID correlatore è un parametro del file di configurazione di Autopilot. Intune imposterà automaticamente l'[attributo del dispositivo Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) su "OfflineAutopilotprofile-<correlator ID>. In questo modo sarà possibile creare gruppi dinamici di Azure AD arbitrari in base all'ID correlatore tramite l'attributo enrollmentprofileName per le registrazioni di Autopilot offline. Per altre informazioni, vedere [Windows Autopilot per dispositivi esistenti](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Criteri di Protezione app di Intune <!-- 2984657 -->
I criteri di protezione delle app di Intune consentono di configurare varie impostazioni di protezione dei dati per le app protette da Intune, ad esempio Microsoft Outlook e Microsoft Word. È stato modificato l'aspetto di queste impostazioni sia per [iOS](app-protection-policy-settings-ios.md) che per [Android](app-protection-policy-settings-android.md) in modo che sia più facile trovare le singole impostazioni. Sono tre le categorie di impostazioni dei criteri:
- **Rilocazione dei dati**: questo gruppo include i controlli di prevenzione della perdita dei dati, ad esempio le restrizioni relative alle operazioni Taglia, Copia, Incolla e Salva con nome. Queste impostazioni determinano la modalità con cui gli utenti interagiscono con i dati nelle app.
- **Requisiti di accesso**: questo gruppo contiene le opzioni PIN per ogni app che determinano in che modo l'utente finale accede alle app in un contesto aziendale.  
- **Avvio condizionale**: questo gruppo contiene impostazioni come le impostazioni minime del sistema operativo, il rilevamento di jailbreak e dispositivi rooted e i periodi di prova offline.  
  
La funzionalità delle impostazioni non cambia, ma sarà più semplice trovarle quando si usa il flusso di creazione dei criteri.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Limitare le app e bloccare l'accesso alle risorse aziendali nei dispositivi Android <!-- 2451462  -->  
In **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android** > **Sicurezza del sistema** è presente una nuova impostazione nella sezione *Sicurezza dei dispositivi*, denominata **App con restrizioni**. L'impostazione **App con restrizioni** usa un criterio di conformità per impedire l'accesso alle risorse aziendali se determinate app vengono installate nel dispositivo. Il dispositivo è considerato non conforme fino a quando non vengono rimosse le app con restrizioni dal dispositivo.
Si applica a: 
- Android

### <a name="intune-apps"></a>App di Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune supporterà una dimensione massima dei pacchetti pari a 8 GB per le app line-of-business <!-- 1727158 -->
Intune ha aumentato le dimensioni massime consentite per i pacchetti a 8 GB per le app line-of-business. Per altre informazioni, vedere [Aggiungere app a Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Aggiungere l'immagine del marchio personalizzata per l'app Portale aziendale <!-- 1916266 -->
Gli amministratori di Microsoft Intune possono caricare un'immagine del marchio personalizzata da visualizzare come sfondo nella pagina del profilo utente nell'app Portale aziendale di iOS. Per altre informazioni sulla configurazione dell'app Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune manterrà la lingua localizzata di Office durante gli aggiornamenti di Office nei computer degli utenti finali <!-- 2971030 -->
Quando Intune installa Office nei computer dell'utente finale, i Language Pack sono gli stessi usati nelle precedenti installazioni di Office MSI. Per altre informazioni, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nuova esperienza di supporto di Intune nel portale di Gestione dei dispositivi per Microsoft 365 <!-- 3076965 -->
Verrà implementata una nuova esperienza di Guida e supporto tecnico per Intune nel [portale di Gestione dei dispositivi per Microsoft 365]( http://devicemanagement.microsoft.com). La nuova esperienza consente di descrivere il problema con parole proprie e di ricevere informazioni dettagliate per la risoluzione dei problemi e contenuti Web per la correzione. Queste soluzioni sono offerte tramite un algoritmo di apprendimento automatico basato su regole, creato in base alle indagini condotte tra gli utenti.  

Oltre alle indicazioni specifiche per il problema, è anche possibile usare il nuovo flusso di lavoro di creazione di un caso per aprire un caso di supporto tramite posta elettronica o telefono.  

Per i clienti che fanno parte dell'implementazione, questa nuova esperienza sostituisce l'esperienza di Guida e supporto tecnico corrente basata su un set statico di opzioni preselezionate a seconda dell'area della console usata quando si apre Guida e supporto tecnico.  

*Questa nuova esperienza di Guida e supporto tecnico verrà implementata solo in alcuni tenant ed è disponibile nel portale di gestione dei dispositivi. I partecipanti a questa nuova esperienza vengono selezionati casualmente tra i tenant di Intune disponibili. Con l'espansione dell'implementazione, verranno aggiunti nuovi tenant.*  

Per altre informazioni, vedere [Nuova esperienza di Guida e supporto tecnico](get-support.md#help-and-support-experience) in Come ottenere supporto per Microsoft Intune.  

#### <a name="powershell-module-for-intune--preview-available----951068---"></a>Modulo di PowerShell per Intune: anteprima disponibile <!-- 951068 -->
Un nuovo modulo di PowerShell, che offre il supporto per l'API di Intune attraverso Microsoft Graph, è ora disponibile in anteprima in [GitHub]( https://aka.ms/intunepowershell). Per informazioni dettagliate sull'uso di questo modulo, vedere il file Leggimi in tale percorso. 


<!-- ########################## -->
## <a name="september-2018"></a>Settembre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Rimuovere la duplicazione dei riquadri Stato di protezione dell'app <!-- 3083391 -->
I riquadri **Stato utente per iOS** e **Stato utente per Android** erano presenti nella pagina **App client - Panoramica** e anche nella pagina **App client - Stato di protezione dell'app**. I riquadri dello stato sono stati rimossi dalla pagina **App client - Panoramica** per evitare la duplicazione. 

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Supporto per un maggior numero di autorità di certificazione di terze parti <!-- 3093107 -->
Utilizzando il Simple Certificate Enrollment Protocol (SCEP), è ora possibile rilasciare nuovi certificati e rinnovare i certificati esistenti su dispositivi mobili con Windows, iOS, Android e macOS.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune supporta iOS 10 e versioni successive <!-- 2454656 -->  
Il servizio di registrazione di Intune, l'app Portale aziendale e Managed Browser ora supportano solo dispositivi iOS che eseguono iOS 10 e versioni successive. Per cercare i dispositivi o gli utenti interessati nell'organizzazione, passare a Intune nel portale di Azure > **Dispositivi** > **Tutti i dispositivi**. Filtrare in base al sistema operativo e quindi fare clic su **Colonne** per visualizzare i dettagli della versione del sistema operativo. Chiedere a questi utenti di aggiornare i dispositivi a una versione supportata del sistema operativo.  

Con i dispositivi inclusi nell'elenco seguente o se si vuole registrare un dispositivo tra quelli elencati, tenere presente che questi supportano solo iOS 9 e versioni precedenti.  Per continuare ad accedere al Portale aziendale Intune, è necessario aggiornare questi dispositivi a dispositivi che supportano iOS 10 o versioni successive:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (terza generazione) 
* iPad Mini (prima generazione)  

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Interfaccia di amministrazione di Gestione dispositivi Microsoft 365 <!-- 3078424 -->
Tra le promesse di Microsoft 365 c'è quella di semplificare l'amministrazione pertanto, nel corso degli anni, i servizi di Microsoft 365 back-end sono stati integrati per offrire scenari end-to-end, ad esempio l'accesso condizionale di Intune e Azure AD. La nuova [interfaccia di amministrazione di Microsoft 365](http://devicemanagement.microsoft.com) è il centro in cui consolidare, semplificare e integrare l'esperienza di amministrazione. Quest'area di lavoro specializzata per la gestione dei dispositivi consente di accedere facilmente a tutte le informazioni e attività per la gestione dei dispositivi e delle app che servono all'organizzazione. Prevediamo che diventerà l'area di lavoro cloud principale per i team informatici degli utenti finali.


<!-- ########################## -->
## <a name="august-2018"></a>Agosto 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Supporto del tunnel di pacchetti per profili VPN per app iOS per i tipi di connessione personalizzata e Pulse Secure <!-- 1520957 -->
Quando si usano i profili VPN per app iOS, è possibile usare il tunneling a livello di app (proxy delle app) o il tunneling a livello di pacchetto (tunnel di pacchetti). Queste opzioni sono disponibili con i tipi di connessione seguenti:
- VPN personalizzata
- Pulse Secure Se non si conosce il valore da usare, consultare la documentazione del provider VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Ritardo quando vengono visualizzati gli aggiornamenti del software iOS sul dispositivo <!-- 1949583 -->
In Intune > **Aggiornamenti software** > **Criteri di aggiornamento per iOS** è possibile configurare i giorni e gli orari in cui i dispositivi non devono installare aggiornamenti. In un aggiornamento futuro sarà possibile rimandare il momento in cui visualizzare un aggiornamento software sul dispositivo, da 1 a 90 giorni. 
Per le impostazioni correnti, vedere [Configurare i criteri di aggiornamento per iOS in Microsoft Intune](software-updates-ios.md).

#### <a name="office-365-proplus-version----2213968---"></a>Versione di Office 365 ProPlus <!-- 2213968 -->
Durante l'assegnazione delle app di Office 365 ProPlus ai dispositivi Windows 10 con Intune, sarà possibile selezionare la versione di Office. Nel portale di Azure selezionare **Microsoft Intune** > **App** > **Aggiungi app**. Selezionare quindi **Office 365 ProPlus Suite (Windows 10)** nell'elenco a discesa **Tipo**. Selezionare **Impostazioni della suite di app** per visualizzare il pannello associato. Impostare **Canale di aggiornamento** su un valore, ad esempio **Ogni mese**. Rimuovere facoltativamente l'altra versione di Office (MSI) dai dispositivi degli utenti finali selezionando **Sì**. Selezionare **Specifica** per installare una versione specifica di Office per il canale selezionato nei dispositivi degli utenti finali. A questo punto, è possibile selezionare la **versione specifica** di Office da usare. Le versioni disponibili cambieranno nel corso del tempo. Quando si crea una nuova distribuzione, le versioni disponibili potrebbero quindi essere più recenti e alcune versioni precedenti potrebbero non essere disponibili. Le distribuzioni correnti continueranno a distribuire la versione precedente, ma l'elenco delle versioni verrà continuamente aggiornato per ogni canale. Per altre informazioni, vedere [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Supporto per l'impostazione di registrazione DNS per VPN di Windows 10 <!-- 2282852 -->
Con questo aggiornamento sarà possibile configurare i profili VPN di Windows 10 per registrare in modo dinamico gli indirizzi IP assegnati all'interfaccia VPN con il DNS interno, senza dover usare profili personalizzati.
Per informazioni sulle impostazioni dei profili VPN disponibili, vedere [Impostazioni VPN di Windows 10 in Intune](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>Il programma di installazione del Portale aziendale di macOS ora include il numero di versione nel nome del file del programma di installazione <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>Aggiornamenti dell'app iOS automatici <!-- 2729759 -->
Gli aggiornamenti automatici delle app funzionano sia per le app con licenza per dispositivo che per utente per iOS versione 11.0 e versioni successive.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello avrà come destinazione utenti e dispositivi <!-- 1106609 -->
Quando si crea un criterio di [Windows Hello for Business](windows-hello.md), questo viene applicato a tutti gli utenti dell'organizzazione (a livello di tenant). Con questo aggiornamento, il criterio può essere applicato anche a utenti specifici o a dispositivi specifici usando un criterio di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Identity Protection** > **Windows Hello for Business**).
In Intune nel portale di Azure la configurazione e le impostazioni di Windows Hello ora esistono sia in **Registrazione del dispositivo** che in **Configurazione del dispositivo**. **Registrazione del dispositivo** è associato all'intera organizzazione (a livello di tenant) e supporta Windows AutoPilot (Configurazione guidata). **Configurazione del dispositivo** è associato a dispositivi e utenti tramite un criterio applicato durante l'archiviazione.
Questa funzionalità si applica a:  
- Windows 10 e versioni successive
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler è una connessione disponibile per i profili VPN in iOS <!-- 1769858 -->
Quando si crea un profilo di configurazione del dispositivo VPN iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **iOS** > tipo di profilo **VPN**), sono disponibili diversi tipi di connessione, inclusi Cisco, Citrix e altri. Questo aggiornamento aggiunge Zscaler come tipo di connessione. 
Per i tipi di connessione disponibili, vedere [Impostazioni VPN per i dispositivi che eseguono iOS](vpn-settings-ios.md).

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Modalità FIPS per i profili Wi-Fi aziendale per Windows 10 <!-- 1879077 -->
È ora possibile abilitare la modalità Federal Information Processing Standards (FIPS) per i profili Wi-Fi aziendale per Windows 10 nel portale di Intune di Azure. Assicurarsi che la modalità FIPS sia abilitata nell'infrastruttura Wi-Fi se è necessario attivarla nei profili Wi-Fi.
Vedere [Impostazioni Wi-Fi per dispositivi Windows 10 e versioni successive in Intune](wi-fi-settings-windows.md) per informazioni su come creare un profilo Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Controllare la modalità S in dispositivi Windows 10 e versioni successive - anteprima pubblica <!-- 1958649 -->
Con questo aggiornamento di funzionalità è possibile creare un profilo di configurazione del dispositivo per disattivare la modalità S in un dispositivo Windows 10 o impedire agli utenti di disattivare la modalità S nel dispositivo. Questa funzionalità è disponibile in Intune > **Configurazione del dispositivo** > **Profili** >  **Windows 10 e versioni successive** > **Edition upgrade and mode switch** (Aggiornamento edizione e cambio modalità).
Per altre informazioni sulla modalità S, vedere [Ti presentiamo Windows 10 in modalità S](https://www.microsoft.com/windows/s-mode).
Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Pacchetto di configurazione Windows Defender ATP aggiunto automaticamente al profilo di configurazione <!-- 2144658 -->
Quando vengono usati [Advanced Threat Protection e l'onboarding](advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile) in Intune, è necessario prima eseguire il download di un pacchetto di configurazione da aggiungere al profilo di configurazione. Con questo aggiornamento Intune ottiene il pacchetto automaticamente da Windows Defender Security Center e lo aggiunge al profilo.
Si applica a Windows 10 e versioni successive.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Richiedere agli utenti di connettersi durante la configurazione del dispositivo <!--2311457-->
Ora è possibile configurare i profili del dispositivo in modo da richiedere che il dispositivo si connetta a una rete prima di passare oltre la pagina Rete durante la configurazione di Windows 10. Quando questa funzionalità è disponibile in anteprima, è necessaria una build 1809 o successiva di Windows Insider per usare questa impostazione.
Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Limitare le app e bloccare l'accesso alle risorse aziendali nei dispositivi iOS e Android Enterprise <!-- 2451462 -->
In **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **iOS** > **Sicurezza del sistema** è disponibile una nuova impostazione **Restricted applications** (Applicazioni con restrizioni). Questa nuova impostazione usa un criterio di conformità per impedire l'accesso alle risorse aziendali se determinate app vengono installate nel dispositivo. Il dispositivo è considerato non conforme fino a quando non vengono rimosse le app con restrizioni dal dispositivo.
Si applica a: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Aggiornamenti del supporto della VPN moderna per iOS <!-- 2459928, 1819876, and 2650856 -->
L'aggiornamento aggiunge il supporto per i client VPN iOS seguenti: 
- F5 Access (versione 3.0.1 e successive)
- Citrix SSO
- Palo Alto Networks GlobalProtect (versione 5.0 e successive) Sempre in questo aggiornamento:
- Il tipo di connessione esistente **F5 Access** è stato rinominato **F5 Access Legacy** per iOS.
- Il tipo di connessione **Palo Alto Networks GlobalProtect** esistente è stato rinominato **Palo Alto Networks GlobalProtect (legacy)** per iOS.
I profili esistenti con questi tipi di connessione continuano a funzionare con il client VPN legacy relativo. Se si usa Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN o Palo Alto Networks GlobalProtect versione 4.1 e versioni precedenti con iOS, è consigliabile passare alle nuove app. Effettuare questo passaggio il prima possibile per assicurarsi che l'accesso VPN sia disponibile per i dispositivi iOS quando viene eseguito l'aggiornamento a iOS 12.
Per altre informazioni su iOS 12 e i profili VPN, vedere il [blog del team di supporto di Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Esportare i criteri di conformità dal portale di Azure classico per ricrearli nel portale di Intune di Azure <!-- 2469637 -->
I criteri di conformità creati nel portale di Azure classico saranno deprecati. È possibile rivedere ed eliminare i criteri di conformità esistenti ma non aggiornarli. Se è necessario eseguire la migrazione di criteri di conformità al portale di Intune di Azure, è possibile esportare i criteri come file con valori delimitati da virgole (file con estensione *csv*). In seguito, usare i dettagli del file per ricreare i criteri nel portale di Intune di Azure.

> [!IMPORTANT]
> Quando il portale di Azure classico verrà ritirato, non sarà più possibile accedere ai criteri di conformità né visualizzarli. Assicurarsi quindi di esportarli e ricrearli nel portale di Azure prima che il portale di Azure classico venga ritirato.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile: un nuovo partner di Mobile Threat Defense <!-- 22662717 -->
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi eseguita da Better Mobile, una soluzione Mobile Threat Defense integrata in Microsoft Intune.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloccare il Portale aziendale nella modalità app singola fino all'accesso dell'utente <!--1067692 --> 
Ora è possibile eseguire Portale aziendale in modalità app singola se si autentica un utente tramite Portale aziendale invece che tramite Assistente configurazione durante la registrazione DEP. Questa opzione blocca il dispositivo immediatamente dopo il completamento di Assistente configurazione così che un utente deve effettuare l'accesso per accedere al dispositivo. Questo processo assicura che il dispositivo completi l'onboarding e non rimanga orfano in uno stato senza utenti associati.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Assegnare un utente e un nome descrittivo a un dispositivo di Autopilot <!--1346521 -->
Ora è possibile [assegnare un utente a un dispositivo Autopilot singolo](enrollment-autopilot.md). Gli amministratori potranno anche assegnare nomi descrittivi per rivolgersi all'utente quando configura il dispositivo con Autopilot.
Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Usare le licenze di dispositivo VPP per effettuare il provisioning anticipato del Portale aziendale durante la registrazione DEP <!-- 1608345 -->
È ora possibile usare le licenze di dispositivo Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante le registrazioni DEP (Device Enrollment Program). A tale scopo, quando si [crea o si modifica un profilo di registrazione](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), specificare il token VPP che si vuole usare per installare il portale aziendale. Assicurarsi che il token non abbia una scadenza e di avere un numero sufficiente di licenze per l'app del portale aziendale. Se il token ha una scadenza o se il numero di licenze è insufficiente, Intune esegue il push del portale aziendale dell'App Store (che richiederà l'immissione di un ID Apple).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Conferma richieste per l'eliminazione del token VPP usato per il provisioning anticipato del Portale aziendale <!-- 2237634 -->
Viene ora richiesta la conferma dell'eliminazione di un token VPP (Volume Purchase Program) se il token viene usato per il provisioning anticipato del Portale aziendale durante la registrazione DEP.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloccare le registrazioni dei dispositivi personali Windows <!-- 1849498 -->
È possibile [bloccare la registrazione di dispositivi personali Windows](windows-enroll.md) con la [gestione di dispositivi mobili](enrollment-restrictions-set.md) in Intune. I dispositivi registrati con l'[agente del computer di Intune](manage-windows-pcs-with-microsoft-intune.md) non possono essere bloccati con questa funzionalità. Questa funzionalità verrà implementata nelle prossime due settimane e potrebbe non apparire immediatamente nell'interfaccia utente.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Specificare i modelli di nome computer in un profilo di Autopilot <!--1849855-->
È possibile [specificare un modello di nome computer](enrollment-autopilot.md#create-an-autopilot-deployment-profile) per generare e impostare il [nome computer](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante la registrazione di Autopilot. Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Per i profili di Windows Autopilot, nascondere le opzioni per cambiare l'account nella pagina di accesso aziendale e nella pagina degli errori di dominio <!--1901669 -->
Sono disponibili [nuove opzioni del profilo di Windows Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) che consentono agli amministratori di nascondere le opzioni per cambiare l'account nelle pagine di accesso aziendale e degli errori di dominio. Per nascondere queste opzioni, è necessario configurare le informazioni personalizzate distintive dell'azienda in Azure Active Directory. Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Supporto macOS per il Device Enrollment Program di Apple <!-- 747651 -->
Intune supporta ora la registrazione dei dispositivi macOS nel Device Enrollment Program (DEP) di Apple. Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS nel programma Device Enrollment Program di Apple](device-enrollment-program-enroll-macos.md).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="delete-jamf-devices----2653306--"></a>Eliminare i dispositivi Jamf <!-- 2653306-->
È possibile eliminare i dispositivi gestiti da JAMF tramite **Dispositivi** > scegliere il dispositivo Jamf > **Elimina**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Modifica delle terminologia in "ritirare" e "cancellare" <!-- 2175759 -->
Per garantire la coerenza con l'API Graph, nell'interfaccia utente e nella documentazione di Intune sono stati modificati i termini seguenti:
- **Rimuovi i dati aziendali** viene modificato in "ritirare"
- **Ripristino delle impostazioni predefinite** verrà cambiato in **cancellare**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Finestra di dialogo di conferma se l'amministratore tenta di eliminare un certificato push MDM <!-- 297909500-->
Se si tenta di eliminare un certificato push MDM di Apple, viene visualizzata una finestra di dialogo di conferma con il numero dei dispositivi iOS e macOS correlati. Se il certificato viene eliminato, i dispositivi dovranno essere registrati nuovamente.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Impostazioni di protezione aggiuntive per Windows Installer <!-- 2282430 -->
Gli utenti possono controllare l'installazione delle app. Se l'opzione è abilitata, le installazioni che a causa di una violazione della protezione verrebbero arrestate possono precedere. È possibile indicare a Windows Installer di usare privilegi elevati durante l'installazione di un qualsiasi programma in un sistema. È anche possibile indicizzare gli elementi Windows Information Protection e archiviare i relativi metadati in una posizione non crittografata. Quando i criteri sono disabilitati, gli elementi protetti da WIP non vengono indicizzati e non appaiono nei risultati di Cortana o Esplora file. Le funzionalità per queste opzioni sono disabilitate per impostazione predefinita. 

#### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nuovo aggiornamento dell'esperienza utente per il sito Web Portale aziendale <!--2000968 -->
Sono state aggiunte nuove funzionalità, in base ai suggerimenti dei clienti, al sito Web Portale aziendale. Si noterà un miglioramento significativo delle funzionalità esistenti e dell'usabilità dei dispositivi. Diverse aree del sito, come ad esempio i dettagli del dispositivo, i commenti e suggerimenti, il supporto e la panoramica del dispositivo, presentano una nuova progettazione, moderna e reattiva. Saranno inoltre disponibili:

- Flussi di lavoro semplificati in tutte le piattaforme per dispositivi
- Flussi di identificazione e registrazione dei dispositivi ottimizzati
- Messaggi di errore più utili
- Linguaggio più semplice con meno gergo tecnico
- Possibilità di condividere collegamenti diretti alle app
- Miglioramento delle prestazioni per i cataloghi di app di grandi dimensioni
- Maggiore accessibilità per tutti gli utenti  

La [documentazione di sito Web Portale aziendale di Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) è stata aggiornata per riflettere tali modifiche. Per visualizzare un esempio dei miglioramenti apportati alle app, vedere [Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Rilevamento delle manomissioni con jailbreak migliorato nel report sulla conformità<!-- 2198738 -->
Gli stati delle impostazioni del rilevamento delle manomissioni con jailbreak migliorato ora vengono visualizzati nel report di conformità nella console di amministrazione.

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-for-policies---1081974---"></a>Tag di ambito per i criteri <!--1081974 -->
È possibile [creare tag di ambito](scope-tags.md) per limitare l'accesso alle risorse di Intune. Aggiungere un tag di ambito a un'assegnazione di ruolo e quindi aggiungere il tag di ambito a un profilo di configurazione. Il ruolo potrà accedere solo alle risorse con profili di configurazione con tag di ambito corrispondenti (o nessun tag di ambito).





<!-- ########################## -->
## <a name="july-2018"></a>Luglio 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Supporto di app line-of-business (LOB) per macOS <!-- 1895847 -->
Microsoft Intune consente la distribuzione di app line-of-business per macOS come app **obbligatorie** o **disponibili con registrazione**. Gli utenti finali possono ottenere le app distribuite come app **disponibili** tramite il Portale aziendale per macOS o il [sito Web del Portale aziendale](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Supporto app integrato di iOS per modalità tutto schermo <!-- 2051098 -->
Oltre alle App Store e App gestite, è ora possibile selezionare un'App predefinita, ad esempio, Safari, da eseguire in modalità tutto schermo in un dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modificare le distribuzioni delle app di Office 365 Pro Plus <!-- 2150145 -->
Per l'amministratore di Microsoft Intune è più facile modificare le distribuzioni delle app di Office 365 Pro Plus. Inoltre, non è più necessario eliminare le distribuzioni per modificare le proprietà del gruppo. Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App**. Selezionare la famiglia di prodotti Office 365 Pro Plus dall'elenco delle applicazioni.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>Versione aggiornata di Intune App SDK per Android ora disponibile <!-- 2744271-->
È disponibile una versione aggiornata di Intune App SDK per Android per il supporto della versione Android P. Gli sviluppatori di app che usano Intune SDK per Android devono installare la versione aggiornata di Intune App SDK per garantire che le funzionalità di Intune nelle app Android continuino a funzionare come previsto nei dispositivi Android P. Questa versione di Intune App SDK offre un plug-in predefinito che esegue gli aggiornamenti dell'SDK. Non occorre riscrivere il codice esistente integrato. Per informazioni dettagliate, vedere [Intune SDK per Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Se si usa il vecchio stile con lo scudo per Intune, è consigliabile usare l'icona a forma di valigetta. Per informazioni dettagliate sulla personalizzazione, vedere [questo repository GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Più opportunità di sincronizzazione nell'app Portale aziendale per Windows  
L'app Portale aziendale per Windows ora consente di avviare la sincronizzazione direttamente dalla barra delle applicazioni Windows e dal menu Start. Questa funzionalità è particolarmente utile se l'unica attività eseguita è sincronizzare i dispositivi e ottenere l'accesso alle risorse aziendali. Per accedere alla nuova funzionalità, fare clic sull'icona del portale aziendale che è stata aggiunta alla barra delle applicazioni o al menu Start. Nelle opzioni di menu, elemento detto anche jump list, selezionare **Sync this device** (Sincronizzare il dispositivo). Verrà aperta la pagina **Impostazioni** del portale aziendale e inizierà la sincronizzazione. Per esaminare le nuove funzionalità, vedere [Novità dell'interfaccia utente](whats-new-app-ui.md).   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nuove esperienze di esplorazione nell'app Portale aziendale per Windows  
Durante l'esplorazione o la ricerca di app nell'app Portale aziendale per Windows, ora è possibile passare dalla visualizzazione **Riquadri** alla nuova visualizzazione **Dettagli** e viceversa. La nuova visualizzazione elenca i dettagli dell'applicazione, ad esempio il nome, l'editore, la data di pubblicazione e lo stato di installazione.  

La visualizzazione **Installata** della pagina **App** consente di visualizzare i dettagli sulle installazioni completate e in corso. Per vedere come appare la nuova vista, vedere [Novità dell'interfaccia utente](whats-new-app-ui.md).  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Esperienza dell'app Portale aziendale migliorata per gli utenti del manager di registrazione dispositivi  
Quando un manager di registrazione dispositivi accede all'app Portale aziendale per Windows, ora l'app elenca solo il dispositivo in esecuzione corrente. Questo miglioramento ridurrà i timeout che in precedenza si verificavano quando l'app tentava di mostrare tutti i dispositivi registrati nel manager di registrazione dispositivi.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloccare l'accesso dell'app in base ai fornitori e ai modelli non approvati del dispositivo  <!-- 1425689 ! -->
L'amministratore IT di Intune può applicare un elenco specifico di produttori Android e/o di modelli iOS tramite i criteri di Protezione app di Intune. L'amministratore IT può fornire un elenco delimitato da punto e virgola di produttori per i criteri Android e di modelli di dispositivo per i criteri iOS. I criteri di Protezione app di Intune sono solo per Android e iOS. Su questo elenco specifico è possibile eseguire due azioni distinte:
- Blocco dell'accesso delle app nei dispositivi non specificati.
- Cancellazione selettiva dei dati aziendali nei dispositivi non specificati. 

L'utente non potrà accedere all'applicazione di destinazione se non vengono soddisfatti i requisiti definiti tramite i criteri. In base alle impostazioni, è possibile che l'utente venga bloccato o che i dati aziendali nell'app vengano cancellati in modo selettivo. Nei dispositivi iOS è necessario integrare Intune APP SDK tramite applicazioni specifiche (ad esempio WXP, Outlook, Managed Browser, Yammer) perché sia possibile applicare questa funzionalità con le applicazioni di destinazione. Questa integrazione avviene progressivamente e dipende dai team delle applicazioni specifiche. In Android questa funzionalità richiede il portale aziendale più recente. 

Nei dispositivi degli utenti finali il client Intune esegue un'azione basata su una semplice corrispondenza delle stringhe specificate nel pannello Intune per i criteri di protezione delle applicazioni. Ciò dipende completamente dal valore segnalato dal dispositivo. Di conseguenza, è opportuno che l'amministratore IT si assicuri che il comportamento previsto sia accurato. A tale scopo, è possibile testare questa impostazione con svariati produttori di dispositivi e modelli destinati a un piccolo gruppo di utenti. In Microsoft Intune selezionare **App client** > **Criteri di protezione delle app** per visualizzare e aggiungere criteri di protezione delle app. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md) e [Cancellare i dati in modo selettivo usando le azioni di accesso per i criteri di protezione delle app in Intune](app-protection-policies-access-actions.md).

#### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Accesso alla build in versione non definitiva di Portale aziendale macOS <!-- 1734766 -->
Con Microsoft AutoUpdate è possibile iscriversi e ricevere le build anticipatamente partecipando al programma Insider. L'iscrizione consente di usare il portale aziendale aggiornato prima che sia disponibile per gli utenti finali. Per altre informazioni, vedere il [blog su Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Creare criteri di conformità dei dispositivi usando le impostazioni del firewall nei dispositivi macOS <!-- 1497640 -->
Quando si creano nuovi criteri di conformità per macOS, in **Conformità del dispositivo** > **Criteri** > **Crea criteri** > **Piattaforma: macOS** > **Protezione del sistema**, sono disponibili alcune nuove impostazioni del **firewall**: 

- **Firewall**: configurare in che modo le connessioni in ingresso devono essere gestite nell'ambiente in uso.
- **Connessioni in ingresso**: **bloccare** tutte le connessioni in ingresso tranne quelle necessarie per i servizi Internet di base, ad esempio DHCP, Bonjour e IPSec. Questa impostazione consente inoltre di bloccare tutti i servizi di condivisione.
- **Modalità mascheramento**: **abilitare** questa modalità per impedire che il dispositivo risponda alle richieste di probe. Il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate.

Si applica a: macOS 10.12 e versioni successive

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nuovo profilo di configurazione del dispositivo Wi-Fi per Windows 10 e versioni successive <!-- 1879077 -->
Attualmente, è possibile importare ed esportare i profili Wi-Fi usando i file XML. In questo aggiornamento è possibile creare un profilo di configurazione del dispositivo Wi-Fi direttamente in Intune, come in alcune altre piattaforme.

Per creare il profilo, aprire **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Wi-Fi**. 

Si applica a Windows 10 e versioni successive.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>La Modalità tutto schermo - Obsoleta appare disattivata e non può essere modificata <!-- 2149998 -->
La funzionalità Modalità tutto schermo (anteprima) (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Limitazioni del dispositivo**) è obsoleta e sostituita dalle [impostazioni di modalità tutto schermo per Windows 10 e versioni successive](kiosk-settings.md). In questo aggiornamento la funzionalità **Modalità tutto schermo obsoleta** appare disattivata e l'interfaccia utente non potrà essere modificata o aggiornata. 

Per abilitare la modalità tutto schermo, vedere [Impostazioni relative alla modalità tutto schermo per Windows 10 e versioni successive](kiosk-settings.md).

Si applica a Windows 10 e versioni successive, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API per l'uso delle autorità di certificazione di terze parti <!-- 2184013 -->
In questo aggiornamento è disponibile un'API Java che consente l'integrazione delle autorità di certificazione di terze parti con Intune e SCEP. Gli utenti potranno quindi aggiungere il certificato SCEP a un profilo e applicarlo ai dispositivi usando il software MDM.

Attualmente Intune supporta [le richieste SCEP con Servizi certificati Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Visualizzare o nascondere il pulsante Termina sessione in un browser in modalità tutto schermo <!-- 2455253 -->
Ora è possibile specificare se visualizzare o nascondere il pulsante Termina sessione nei browser in modalità tutto schermo. Il controllo è disponibile in **Configurazione del dispositivo** > **Modalità tutto schermo (anteprima)**  > **Web browser in modalità tutto schermo**. Se è abilitato, quando un utente fa clic sul pulsante, l'app richiede di confermare se terminare la sessione. Se si conferma, il browser cancella tutti i dati di navigazione e torna all'URL predefinito.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Creare un profilo di configurazione cellulare eSIM <!-- 2564077 -->
In **Configurazione del dispositivo** è possibile creare un profilo cellulare eSIM. È possibile importare un file contenente i codici di attivazione cellulare forniti dall'operatore di telefonia mobile. È quindi possibile distribuire i profili nei dispositivi Windows 10 con eSIM LTE, ad esempio Surface Pro LTE e altri dispositivi che supportano eSIM.

Verificare se i [dispositivi supportano i profili eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Si applica a Windows 10 e versioni successive.

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Selezionare le categorie di dispositivi usando le impostazioni per l'accesso all'azienda o all'istituto di istruzione <!-- 1058963 eenotready --> 
Se è stato abilitato il [mapping del gruppo di dispositivi](device-group-mapping.md), agli utenti di Windows 10 sarà ora richiesto di selezionare una categoria di dispositivi dopo la registrazione usando il pulsante **Connetti** in **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usare sAMAccountName come nome utente dell'account per i profili di posta elettronica <!-- 1500307 -->
È possibile usare l'oggetto **sAMAccountName** locale come nome utente dell'account per i profili di posta elettronica per Android, iOS e Windows 10. È anche possibile ottenere il dominio dall'attributo `domain` o `ntdomain` in Azure Active Directory (Azure AD). In alternativa, immettere un dominio personalizzato statico.

Per usare questa funzionalità, è necessario sincronizzare l'attributo `sAMAccountName` dell'ambiente Active Directory locale con Azure AD.

Si applica a: [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 e versioni successive](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Visualizzare i profili di configurazione del dispositivo in conflitto <!-- 1556983 -->
In **Configurazione del dispositivo** viene visualizzato un elenco dei profili esistenti. Con questo aggiornamento viene aggiunta una nuova colonna che fornisce informazioni dettagliate sui profili con un conflitto. È possibile selezionare una riga di conflitto per visualizzare l'impostazione e il profilo che presenta il conflitto. 

Altre informazioni sulla [gestione dei profili di configurazione ](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nuovo stato per i dispositivi nella conformità del dispositivo <!-- 2308882 -->
In **Conformità del dispositivo** > **Criteri** > selezionare un criterio > **Panoramica**. Verranno aggiunti i nuovi stati seguenti:
- riuscito
- Errore
- conflitto
- in sospeso
- non applicabile Viene visualizzata anche un'immagine che illustra il conteggio dei dispositivi di un'altra piattaforma. Ad esempio, se si sta consultando un profilo iOS, il nuovo riquadro indica il numero di dispositivi non iOS assegnati a questo profilo. Vedere [Criteri di conformità dei dispositivi](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>La conformità del dispositivo supporta soluzioni antivirus di terze parti <!-- 2325484 -->
Quando si creano criteri di conformità del dispositivo in **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Piattaforma: Windows 10 e versioni successive** > **Impostazioni** > **Sicurezza del sistema** sono disponibili nuove opzioni in **[Sicurezza del dispositivo](compliance-policy-create-windows.md)** : 
- **Antivirus**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando soluzioni antivirus registrate nel Centro sicurezza PC Windows, ad esempio Symantec e Windows Defender. 
- **Antispyware**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando le soluzioni antispyware registrate nel Centro sicurezza PC Windows, ad esempio Symantec e Windows Defender. 

Si applica a: Windows 10 e versioni successive 

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Contrassegnare automaticamente i dispositivi Android registrati usando Samsung Knox Mobile Enrollment come "aziendali". <!-- 2404851 -->
Per impostazione predefinita, ora i dispositivi Android registrati usando Samsung Knox Mobile Enrollment vengono contrassegnati come **Aziendale** in **Proprietà del dispositivo**. Non è necessario identificare manualmente i dispositivi aziendali utilizzando i numeri IMEI o seriali prima della registrazione mediante Knox Mobile Enrollment.

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Dispositivi senza la colonna relativa ai profili nell'elenco di token DEP <!-- 1853904 -->
Nell'elenco di token DEP è disponibile una nuova colonna in cui viene indicato il numero di dispositivi che non hanno un profilo assegnato. Gli amministratori possono così assegnare un profilo a tali dispositivi prima di consegnarli agli utenti. Per visualizzare la nuova colonna, passare a **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP**.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminare in blocco i dispositivi nel pannello Dispositivi <!-- 1793693 -->
È possibile eliminare più dispositivi contemporaneamente nel pannello Dispositivi. Scegliere **Dispositivi** > **Tutti i dispositivi** > selezionare i dispositivi da eliminare > **Elimina**. Per i dispositivi che non possono essere eliminati, viene visualizzato un avviso.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Modifiche del nome Google per Android for Work e Play for Work <!--842873 -->
Intune ha aggiornato la terminologia di "Android for Work" in modo da riflettere le modifiche di personalizzazione di Google. I termini "Android for Work" e "Play for Work" non vengono più usati. Viene usata un'altra terminologia in base al contesto:
- "Android Enterprise" si riferisce allo stack di gestione per Android moderno nel suo insieme.
- "Profilo di lavoro" o "Proprietario del profilo" fa riferimento ai dispositivi BYOD gestiti con i profili di lavoro.
- "Google Play gestito" si riferisce al Google Play Store.

#### <a name="rules-for-removing-devices----1609459---"></a>Regole di rimozione dei dispositivi <!-- 1609459 -->
Sono disponibili nuove regole che consentono di rimuovere automaticamente i dispositivi che non si sono connessi per un numero di giorni specificato. Per visualizzare la nuova regola, passare al riquadro **Intune**, selezionare **Dispositivi** e selezionare **Regole di pulizia del dispositivo**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Supporto monouso di proprietà dell'azienda per i dispositivi Android <!-- 1630973 -->

Intune ora supporta i dispositivi Android con gestione avanzata, bloccati e in modalità tutto schermo. Questo consente agli amministratori di limitare ulteriormente l'uso di un dispositivo a una sola app o un piccolo gruppo di app e impedire agli utenti di abilitare altre app o eseguire altre azioni nel dispositivo. Per impostare la modalità tutto schermo Android, passare a Intune > **Registrazione del dispositivo** > **Registrazione Android**  > **Registrazioni dei dispositivi per uso in modalità tutto schermo e per attività**. Per altre informazioni, vedere [Set up enrollment of Android enterprise kiosk devices](android-kiosk-enroll.md) (Configurare la registrazione dei dispositivi Android per modalità tutto schermo).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Revisione riga per riga degli identificatori duplicati caricati per i dispositivi aziendali <!-- 2203794-->
Quando si caricano gli ID aziendali, Intune ora presenta un elenco di tutti i duplicati e offre la possibilità di sostituire o mantengono le informazioni esistenti. Viene visualizzato un report se sono presenti duplicati dopo che sono state scelte le opzioni **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi identificatori**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Aggiungere manualmente gli identificatori dei dispositivi aziendali <!-- 2203803 -->
È ora possibile aggiungere manualmente gli ID dei dispositivi aziendali. Scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi**. 


<!-- ########################## -->
## <a name="june-2018"></a>Giugno 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Supporto di Microsoft Edge in dispositivi mobili per i criteri di protezione delle app di Intune <!-- 1817882 -->
Il browser Microsoft Edge per i dispositivi mobili supporta ora i criteri di protezione delle app definiti in Intune.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Recuperare l'ID modello utente dell'app associato per le app di Microsoft Store per le aziende in modalità tutto schermo <!-- 1560077 ! -->
Intune può ora recuperare gli ID modello utente dell'app per le app di Microsoft Store per le aziende per offrire una configurazione ottimizzata del profilo in modalità tutto schermo.

Per altre informazioni sulle app di Microsoft Store per le aziende, vedere [Gestire le app di Microsoft Store per le aziende](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nuova pagina di personalizzazione del Portale aziendale <!-- 1916370 -->
La pagina di personalizzazione del Portale aziendale ha layout, messaggi e descrizioni comandi nuovi.


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo: nuovo partner di Mobile Threat Defense <!-- 1169249 -->
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi eseguita da Pradeo, una soluzione Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Usare la modalità FIPS con NDES Connector per i certificati <!-- 1333688 -->
Quando si installa NDES Connector per i certificati in un computer con la modalità FIPS (Federal informazioni Processing Standard) abilitata, l'emissione e la revoca dei certificati non funzionano come previsto. Con questo aggiornamento, il supporto per FIPS è incluso con NDES Connector per i certificati. 

Questo aggiornamento include anche:

- NDES Connector per i certificati richiede .NET Framework 4.5, incluso automaticamente in Windows Server 2016 e Windows Server 2012 R2. In precedenza, la versione minima richiesta era.NET Framework 3.5.
- Il supporto di TLS 1.2 è incluso con NDES Connector per i certificati. Pertanto, se il server in cui è installato NDES Connector per i certificati supporta TLS 1.2, viene usato TLS 1.2. Se il server non supporta TLS 1.2, viene usato TLS 1.1. Attualmente, TLS 1.1 viene usato per l'autenticazione tra i dispositivi e il server.

Per altre informazioni, vedere [Configurare e usare i certificati SCEP con Intune](certificates-scep-configure.md) e [Configurare e usare i certificati PKCS con Intune](certficates-pfx-configure.md).

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Supporto per i profili VPN di Palo Alto Networks GlobalProtect <!-- 1333680 ! -->
Con questo aggiornamento, è possibile scegliere Palo Alto Networks GlobalProtect come tipo di connessione VPN per i profili VPN in Intune (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Tipo di profilo** > **VPN**). In questa versione sono supportate le piattaforme seguenti: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Aggiunte alle impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1403702 -->
È ora possibile configurare impostazioni aggiuntive per le opzioni di sicurezza dei dispositivi locali Windows 10. Le impostazioni aggiuntive sono disponibili per le aree relative ai client di rete Microsoft, ai server di rete Microsoft, all'accesso e alla sicurezza di rete e all'accesso interattivo. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Abilitare la modalità tutto schermo nei dispositivi Windows 10 <!-- 1560072 ! -->
Nei dispositivi Windows 10 è possibile creare un profilo di configurazione e abilitare la modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** > **Restrizioni del dispositivo** > **Modalità tutto schermo**). In questo aggiornamento l'impostazione **Modalità tutto schermo (anteprima)** viene rinominata **Chiosco multimediale (obsoleto)** . Non è più consigliabile usare **Chiosco multimediale (obsoleto)** , che tuttavia continuerà a funzionare fino all'aggiornamento di luglio. **Chiosco multimediale (obsoleto)** viene sostituito dal nuovo tipo di profilo **Modalità tutto schermo** (**Crea profilo** > **Windows 10** > **Modalità tutto schermo (anteprima)** ), che conterrà le impostazioni per configurare le modalità tutto schermo in Windows 10 RS4 e versioni successive.

Si applica a Windows 10 e versioni successive.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Grafico utente del profilo del dispositivo nuovamente disponibile <!-- 2160133 -->
Durante il miglioramento dei conteggi numerici visualizzati nel grafico del profilo del dispositivo (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**), il grafico utente è stato temporaneamente rimosso.

Con questo aggiornamento, il grafico utente è di nuovo disponibile e visibile nel portale di Azure.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Supporto per la registrazione di Windows Autopilot senza l'autenticazione utente <!-- 1165118 -->
Intune ora supporta la registrazione di Windows Autopilot senza l'autenticazione utente. Si tratta della nuova opzione del profilo di distribuzione di Windows Autopilot "Modalità di distribuzione Autopilot" che viene impostata sulla distribuzione automatica.  Il dispositivo deve eseguire Windows 10 Insider Preview Build 17672 o versione successiva e possedere un chip TPM 2.0 per completare questo tipo di registrazione. Poiché non è necessaria l'autenticazione utente, è consigliabile assegnare questa opzione solo ai dispositivi su cui si ha controllo fisico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nuova impostazione per lingua/area quando si configura la Configurazione guidata per Autopilot <!-- 1821766 -->
È disponibile una nuova impostazione di configurazione per impostare la lingua e l'area dei profili di Autopilot durante la Configurazione guidata. Per visualizzare questa nuova impostazione, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo** > **Modalità di distribuzione** = **Self-deploying (Distribuzione automatica)**  > **Impostazioni predefinite configurate**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuova impostazione per configurare la tastiera del dispositivo <!-- 1821768 -->
Sarà disponibile una nuova impostazione per configurare la tastiera per i profili di Autopilot durante la Configurazione guidata. Per visualizzare questa nuova impostazione, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo** > **Modalità di distribuzione** = **Self-deploying (Distribuzione automatica)**  > **Impostazioni predefinite configurate**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Spostamento dei profili AutoPilot nei gruppi di destinazione <!-- 1877935 -->
I profili di distribuzione di AutoPilot possono essere assegnati ai gruppi di Azure AD contenenti dispositivi AutoPilot.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="set-compliance-by-device-location----851881----"></a>Impostare la conformità in base al percorso del dispositivo <!-- 851881 ! -->
In alcuni casi, potrebbe essere necessario limitare l'accesso alle risorse aziendali a un percorso specifico, definito da una connessione di rete. È ora possibile creare un criterio di conformità (**Conformità del dispositivo** > **Percorsi**) basato sull'indirizzo IP del dispositivo. Se il dispositivo non è più compreso nell'intervallo di IP, non può accedere alle risorse aziendali.

Si applica a: dispositivi Android 6.0 e versioni successive, con l'app Portale aziendale aggiornata

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitare app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot<!-- 1621980 -->
Sarà possibile impedire l'installazione di app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot. Per vedere questa funzionalità, passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Piattaforma** = **Windows 10 o versione successiva** > **Tipo di profilo** = **Limitazioni del dispositivo** > **Configura** > **Windows Spotlight** > **Funzionalità consumer**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Disinstallare gli aggiornamenti più recenti dagli aggiornamenti software di Windows 10 <!-- 1732948 -->
Nel caso si riscontrasse un problema rilevante nei computer Windows 10, è possibile scegliere di disinstallare (ripristinare lo stato precedente) l'ultimo aggiornamento delle funzionalità o l'ultimo aggiornamento qualitativo. La disinstallazione di un aggiornamento delle funzionalità o di un aggiornamento qualitativo è disponibile solo per il canale di manutenzione su cui è attivo il dispositivo. La disinstallazione attiverà un criterio per il ripristino dell'aggiornamento precedente nei computer Windows 10. In particolare per gli aggiornamenti delle funzionalità, è possibile limitare a un intervallo di giorni compreso tra 2 e 60 la disinstallazione dell'ultima versione. Per impostare le opzioni di disinstallazione dell'aggiornamento software, selezionare **Aggiornamenti software** dal pannello **Microsoft Intune** nel portale di Azure. Nel pannello **Aggiornamenti software** selezionare **Anelli di aggiornamento di Windows 10**. È quindi possibile scegliere l'opzione di **disinstallazione** nella sezione **Panoramica**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Cercare in tutti i dispositivi codici IMEI e numeri di serie <!-- 1793685 -->
Nel pannello Tutti i dispositivi è ora possibile cercare codici IMEI e numeri di serie (sono ancora disponibili posta elettronica, UPN, nome del dispositivo e nome di gestione). In Intune scegliere **Dispositivi** > **Tutti i dispositivi** > e immettere la ricerca nella casella di ricerca.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Il campo Nome di gestione sarà modificabile <!-- 1875989 -->
È ora possibile modificare il campo Nome di gestione nel pannello **Proprietà** di un dispositivo. Per modificare questo campo, scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Proprietà**. È possibile usare il campo Nome di gestione per identificare in modo univoco un dispositivo.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nuovo filtro per Tutti i dispositivi: Categoria del dispositivo <!-- 1878520 -->
È ora possibile filtrare l'elenco **Tutti i dispositivi** per categoria di dispositivi. A tale scopo, scegliere **Dispositivi** > **Tutti i dispositivi** > **Filtro** > **Categoria del dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Usare TeamViewer per condividere lo schermo dei dispositivi iOS e MacOS <!-- 1985547 -->
Gli amministratori ora possono connettersi a [TeamViewer](teamviewer-support.md) e avviare un sessione di condivisione dello schermo con i dispositivi iOS e macOS. Gli utenti di iPhone, iPad e macOS possono condividere gli schermi in tempo reale con altri dispositivi mobili o desktop. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Supporto di Exchange Connector multipli <!-- 2070451 -->
Non è più previsto il limite di un Microsoft Intune Exchange Connector per tenant. Intune ora supporta più Exchange Connector per consentire la configurazione dell'accesso condizionale in Intune per più organizzazioni di Exchange locali.

Con un On-premises Exchange Connector di Intune è possibile gestire l'accesso dei dispositivi alle cassette postali di Exchange locali in base al fatto che i dispositivi siano registrati o meno in Intune e siano conformi ai criteri di conformità dei dispositivi di Intune. Per configurare un connettore, scaricare l'On-premises Exchange Connector di Intune dal portale di Azure e installarlo in un server dell'organizzazione di Exchange. Nel dashboard di Microsoft Intune scegliere **Accesso locale**, quindi nella sezione **Installazione**, scegliere **Connettore per Exchange ActiveSync**. Scaricare l'On-premises Exchange Connector e installarlo in un server della propria organizzazione di Exchange. Ora che non vige più il limite di Exchange Connector per tenant, gli utenti che hanno più organizzazioni di Exchange possono seguire lo stesso processo per scaricare e installare un connettore per ogni organizzazione di Exchange aggiuntiva.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nuovo dettaglio hardware del dispositivo: CCID <!-- 2156657 -->
Sono ora disponibili per ogni dispositivo informazioni CCID (Chip Card Interface Device). Per visualizzare queste informazioni, scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Hardware**> controllare le informazioni in **Dettagli di rete**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Assegnare tutti gli utenti e tutti i dispositivi come gruppi ambito <!-- 2196803 -->
È ora possibile assegnare tutti gli utenti, tutti i dispositivi, tutti gli utenti e tutti i dispositivi nei gruppi ambito. A tale scopo, scegliere **Ruoli di Intune** > **Tutti i ruoli** > **Policy and Profile Manager** >  (Gestione criteri e profili) **Assegnazioni** > scegliere un'assegnazione **Ambito (gruppi)** .

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>Informazioni UDID ora incluse per dispositivi iOS e macOS <!-- 2219806 -->
Per visualizzare le informazioni UDID (Unique Device Identifier) per i dispositivi iOS e macOS, passare a **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Hardware**. Le informazioni UDID sono disponibili solo per i dispositivi aziendali (come impostato in **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Proprietà** > **Proprietà del dispositivo**).

### <a name="intune-apps"></a>App di Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Miglioramento della risoluzione dei problemi di installazione delle app <!-- 928990 -->
Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. È in corso la distribuzione di un'anteprima pubblica delle funzionalità di risoluzione dei problemi delle app. Sotto ogni singolo dispositivo si noterà un nuovo nodo denominato **App gestite**, che elenca le app distribuite tramite MDM di Intune. Nel nodo è visibile un elenco di stati di installazione delle app. Se si seleziona una singola app, si noterà la visualizzazione relativa alla risoluzione dei problemi per l'app specifica. In tale visualizzazione è presente il ciclo di vita end-to-end dell'app, ad esempio quando l'app è stata creata, modificata, specificata come destinazione e distribuita in un dispositivo. Se l'installazione dell'app non è riuscita, saranno anche disponibili il codice di errore e un messaggio sulla causa dell'errore. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Criteri di protezione delle app di Intune e Microsoft Edge <!-- 1818968 -->
Il browser Microsoft Edge per dispositivi mobili (iOS e Android) ora supporta i criteri di protezione delle app di Microsoft Intune. Gli utenti di dispositivi iOS e Android che accedono con gli account Azure AD aziendali nell'applicazione Microsoft Edge saranno protetti da Intune. Nei dispositivi iOS il criterio **Require managed browser for web content** (Richiedi Managed Browser per contenuti Web) consentirà agli utenti di aprire i collegamenti in Microsoft Edge quando è gestito.

<!-- ########################## -->
## <a name="may-2018"></a>Maggio 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configurazione dei criteri di protezione delle app <!-- 2144597 Part 2 -->

Nel portale di Azure anziché passare al pannello del servizio Protezione app di Intune ora è possibile accedere a Intune. Ora è disponibile un solo percorso per i criteri di protezione delle app in Intune. Si noti che tutti i criteri di protezione delle app si trovano nel pannello **App per dispositivi mobili** in Intune in **Criteri di protezione delle app**. Questa integrazione contribuisce alla semplificazione dell'amministrazione della gestione del cloud. Tenere presente che tutti i criteri di protezione delle app sono già presenti in Intune ed è possibile modificare tutti i criteri configurati in precedenza. I criteri di protezione delle app e di accesso condizionale di Intune ora sono in **Accesso condizionale**, che si trova nella sezione **Gestisci** del pannello **Microsoft Intune** o nella sezione **Sicurezza** del pannello **Azure Active Directory**. Per altre informazioni sulla modifica dei criteri di accesso condizionale, vedere [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Richiedere l'installazione di criteri, app e profili di certificato e di rete <!-- 1553555 -->
Gli amministratori possono impedire agli utenti finali di accedere al desktop di Windows 10 RS4 finché Intune non avrà installato criteri, app e profili di certificato e di rete durante il provisioning dei dispositivi AutoPilot. Per altre informazioni, vedere [Configurare la registrazione dei dispositivi Windows](windows-enrollment-status.md).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Supporto della registrazione per dispositivi mobili Samsung Knox <!--1112863-->
Quando si usa Intune con Samsung Knox Mobile Enrollment (KME), è possibile registrare un numero elevato di dispositivi Android di proprietà della società. Gli utenti connessi a reti Wi-Fi o cellulari possono eseguire la registrazione con pochi tocchi quando accendono il dispositivo per la prima volta. Quando si usa l'app Knox Deployment, è possibile registrare i dispositivi tramite Bluetooth o NFC. Per altre informazioni, vedere [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Registrare automaticamente i dispositivi Android usando Samsung Knox Mobile Enrollment).

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi 

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Richiesta di assistenza in Portale aziendale per Windows 10 <!-- 1874137 -->
Portale aziendale per Windows 10 invia ora i log delle app direttamente a Microsoft quando l'utente avvia il flusso di lavoro per visualizzare la Guida per un problema. In questo modo sarà più semplice risolvere i problemi inoltrati a Microsoft.

<!-- ########################## -->
## <a name="april-2018"></a>Aprile 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Supporto di passcode per PIN MAM in Android<!-- 1438086 -->

Gli amministratori di Intune possono impostare un requisito di avvio delle applicazioni per imporre un passcode anziché un PIN MAM numerico. Se il requisito viene configurato, all'utente viene richiesto di impostare e usare un passcode prima di accedere alle applicazioni con supporto MAM. Un passcode è un PIN numerico con almeno un carattere speciale o una lettera maiuscola o minuscola. Il supporto di Intune per i passcode è simile a quello esistente per il PIN numerico, con la possibilità di impostare una lunghezza minima e consentendo la ripetizione di caratteri e sequenze tramite la console di amministrazione. Questa funzionalità richiede la versione più recente di Portale aziendale in Android. Questa funzionalità è già disponibile per iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Supporto di app line-of-business (LOB) per macOS <!-- 1473977 -->
Microsoft Intune offrirà la possibilità di installare app LOB (line-of-business) macOS dal portale di Azure. Sarà possibile aggiungere un'app LOB macOS a Intune dopo una pre-elaborazione effettuata dallo strumento disponibile in GitHub. Nel portale di Azure scegliere **App client** dal pannello **Intune**. Nel pannello **App client** scegliere **App** > **Aggiungi**. Nel pannello **Aggiungi app** selezionare **App line-of-business**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Gruppi predefiniti Tutti gli utenti e Tutti i dispositivi per l'assegnazione di app del profilo di lavoro di Android Enterprise <!-- 1813073 -->
È possibile usare i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi** per l'assegnazione di app del profilo di lavoro di Android Enterprise. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune reinstallerà le app richieste disinstallate dagli utenti <!-- 1947010 -->
Se un utente finale disinstalla un'app richiesta, Intune reinstalla automaticamente l'app entro 24 ore invece di attendere il ciclo di rivalutazione di 7 giorni.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Aggiornare la posizione in cui configurare i criteri di protezione dell'app <!-- 2144597 -->

Nel portale di Azure, nell'ambito del servizio Microsoft Intune, si verrà temporaneamente reindirizzati dal pannello del servizio **Protezione app di Intune** al pannello **App per dispositivi mobili**. Si noti che tutti i criteri di protezione delle app sono già nel pannello **App per dispositivi mobili** in Intune sotto la configurazione delle app. Invece di andare a Protezione app di Intune, si passerà a Intune. Ad aprile 2018 il reindirizzamento verrà arrestato e il pannello del servizio **Protezione app di Intune** verrà completamente rimosso. All'interno di Intune sarà quindi disponibile una sola posizione per i criteri di protezione delle app. 

**Quali sono le conseguenze di questa modifica?**
Questa modifica avrà effetto sia sui clienti di Intune autonomi che sui clienti ibridi (Intune con Configuration Manager). Questa integrazione consentirà di semplificare l'amministrazione della gestione del cloud.

**Operazioni di preparazione alla modifica**
Contrassegnare come preferito **Intune** anziché il pannello del servizio **Protezione app di Intune** e assicurarsi di avere dimestichezza con il flusso di lavoro Criterio di protezione dell'app nel pannello **App per dispositivi mobili** all'interno di Intune. Il reindirizzamento durerà per un breve periodo di tempo e quindi il pannello **Protezione app** verrà rimosso. Tenere presente che tutti i criteri di protezione delle app sono già presenti in Intune ed è possibile modificare tutti i criteri di accesso condizionale. Per altre informazioni sulla modifica dei criteri di accesso condizionale, vedere [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md) 

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Visualizzazione di tutti i dispositivi di un gruppo nel grafico dei profili e nell'elenco dello stato dei dispositivi <!-- 1449153 -->
Quando si configura il profilo di un dispositivo (**Configurazione del dispositivo** > **Profili**), si sceglie il profilo del dispositivo, ad esempio iOS. Il profilo viene assegnato a un gruppo che include dispositivi iOS e non iOS. Il conteggio del grafico indica che il profilo viene applicato ai dispositivi iOS *e* non iOS (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**). Quando si seleziona il grafico nella scheda **Panoramica**, **Stato dispositivo** elenca tutti i dispositivi del gruppo, anziché solo i dispositivi iOS. 

Con questo aggiornamento, il grafico (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**) visualizza solo il conteggio relativo al profilo dispositivo specifico. Se ad esempio il profilo di configurazione si applica ai dispositivi iOS, il grafico elencherà solo il conteggio dei dispositivi iOS. Selezionando il grafico e aprendo **Stato dispositivo** si vedranno elencati solo i dispositivi iOS.

In attesa di questo aggiornamento, il grafico utente è stato temporaneamente rimosso. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN Always On per Windows 10 <!--1333666 -->

Attualmente, è possibile usare [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) nei dispositivi Windows 10 tramite un profilo di rete privata virtuale (VPN, Virtual Private Network) personalizzato creato con un URI OMA.

Con questo aggiornamento, gli amministratori possono abilitare profili VPN Always On per Windows 10 direttamente in Intune nel portale di Azure. I profili VPN Always On si connetteranno automaticamente quando:

- Gli utenti accedono ai propri dispositivi
- La rete del dispositivo cambia
- Lo schermo del dispositivo si riattiva dopo essere stato disattivato

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nuove impostazioni della stampante per i profili di formazione <!-- 1308900 -->

Per i profili di formazione, le nuove impostazioni sono disponibili nella categoria **Stampanti**: **Stampanti**, **Stampante predefinita**, **Aggiungi nuove stampanti**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Visualizzare l'ID chiamante nel profilo personale - Profilo di lavoro di Android Enterprise <!--1098984 -->
Quando si usa un profilo personale in un dispositivo, è possibile che gli utenti finali non visualizzino i dettagli dell'ID del chiamante da un contatto di lavoro. 

Dopo questo aggiornamento, sarà presente una nuova impostazione in **Android Enterprise** > **Limitazioni del dispositivo** > **Impostazioni del profilo di lavoro**:
- Visualizzare l'ID chiamante del contatto di lavoro nel profilo personale

Se abilitati (non configurati), i dettagli del chiamante del contatto di lavoro vengono visualizzati nel profilo personale. Se bloccato, il numero del chiamante del contatto di lavoro non viene visualizzato nel profilo personale. 

Si applica a: dispositivi di profilo di lavoro Android in sistemi operativi Android 6.0 e versioni successive

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nuove impostazioni di Windows Defender Credential Guard aggiunte alle impostazioni di Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Con questo aggiornamento, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configurazione del dispositivo** > **Profili** > **Endpoint Protection**) include le impostazioni seguenti: 

- **Windows Defender Credential Guard**: attiva Credential Guard con la sicurezza basata su virtualizzazione. Questa funzionalità, se abilitata, consente di proteggere le credenziali al riavvio successivo quando il **livello di sicurezza della piattaforma con avvio protetto** e la **sicurezza basata sulla virtualizzazione** sono entrambi abilitati. Le opzioni includono:
  - **Disabilitato**: se Credential Guard è stato attivato in precedenza con l'opzione **Abilitato senza blocco**, disattiva Credential Guard in modalità remota.

  - **Abilita con blocco UEFI**: garantisce che Credential Guard non possa essere disabilitato con una chiave del Registro di sistema o con Criteri di gruppo. Per disabilitare Credential Guard dopo avere usato questa impostazione, è necessario impostare Criteri di gruppo su "Disabilitato", quindi rimuovere la funzionalità di sicurezza da ogni computer, con un utente fisicamente presente. Questi passaggi cancellano la configurazione permanente in UEFI. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

  - **Abilita senza blocco**: consente di rimuovere Credential Guard in modalità remota usando Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 (versione 1511 o successiva).

Quando si configura Credential Guard vengono automaticamente abilitate le tecnologie dipendenti seguenti: 

- **Abilita la sicurezza basata su virtualizzazione**: attiva la sicurezza basata su virtualizzazione al riavvio successivo. La sicurezza basata sulla virtualizzazione usa Windows Hypervisor per offrire il supporto per i servizi di sicurezza e richiede Avvio protetto.
- **Avvio protetto con Direct Memory Access (DMA)** : attiva la sicurezza basata sulla virtualizzazione con Avvio protetto e Direct Memory Access. La protezione DMA richiede supporto hardware e viene abilitata solo nei dispositivi configurati correttamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Usare un nome oggetto personalizzato sul certificato SCEP <!-- 2064190 -->
È possibile usare **OnPremisesSamAccountName**, il nome comune in un oggetto personalizzato in un profilo certificato SCEP. È ad esempio possibile usare `CN={OnPremisesSamAccountName})`.

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Bloccare la fotocamera e l'acquisizione di schermate nei profili di lavoro di Android Enterprise <!-- 1098977 -->
Sono disponibili due nuove proprietà di blocco utilizzabili durante la configurazione delle restrizioni per i dispositivi Android: 
- Fotocamera: blocca l'accesso a tutte le fotocamere del dispositivo
- Acquisizione schermo: blocca l'acquisizione di schermate e impedisce anche la visualizzazione del contenuto nei dispositivi di visualizzazione privi di output video protetto

Si applica ai profili di lavoro di Android Enterprise.

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Usare il client Cisco AnyConnect per iOS <!-- 1333708 -->

Quando si crea un nuovo profilo VPN per iOS, ora sono disponibili due opzioni: **Cisco AnyConnect** e **Cisco Legacy AnyConnect**. I profili di Cisco AnyConnect supportano le versioni 4.0.7x e successive. I profili VPN di Cisco AnyConnect per iOS esistenti vengono contrassegnati con la dicitura **Cisco Legacy AnyConnect** e continuano a funzionare con Cisco AnyConnect 4.0.5x e versioni precedenti come accade oggi.

> [!NOTE]
> Questa modifica si applica solo a iOS. Continua a esistere una sola opzione Cisco AnyConnect per la piattaforma Android, i profili di lavoro di Android Enterprise e per la piattaforma macOS.


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nuovi passaggi di registrazione degli utenti per i dispositivi con macOS High Sierra 10.13.2 e versioni successive <!--1734567 -->
macOS high Sierra 10.13.2 ha introdotto il concetto di registrazione MDM "approvata dall'utente". Le registrazioni approvate consentono a Intune di gestire alcune impostazioni relative alla sicurezza. Per altre informazioni, vedere la documentazione del supporto Apple all'indirizzo https://support.apple.com/HT208019.

I dispositivi registrati tramite il portale aziendale macOS vengono considerati "approvati dall'utente" solo se l'utente finale apre Preferenze di Sistema e dichiara l'approvazione manualmente. A tal fine, il portale aziendale macOS ora indica agli utenti che usano macOS 10.13.2 e versioni successive di approvare manualmente la registrazione al termine dell'esecuzione di questa. La console di amministrazione di Intune indicherà se un dispositivo registrato è approvato dall'utente.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>I dispositivi macOS registrati in Jamf ora possono essere registrati con Intune <!-- 2370684 -->
Le versioni 1.3 e 1.4 del portale aziendale di macOS non registravano correttamente i dispositivi Jamf con Intune. Questo problema è stato risolto con la versione 1.4.2 del portale di macOS.

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Esperienza Guida aggiornata nell'app Portale aziendale per Android <!-- 1631531 -->
L'esperienza Guida nell'app Portale aziendale per Android è stata aggiornata e adattata alle procedure consigliate per la piattaforma Android. Ora quando si verifica un problema nell'app, gli utenti possono toccare **Menu** > **Guida** e:
- Caricare i log di diagnostica in Microsoft.
- Inviare un messaggio di posta elettronica con la descrizione del problema e l'ID evento imprevisto a un addetto del supporto aziendale.  

Per provare l'esperienza Guida aggiornata, vedere [Inviare i log tramite posta elettronica](/intune-user-help/send-logs-to-your-it-admin-by-email-android) e [Inviare gli errori a Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuovo grafico di tendenza degli errori di registrazione e tabella dei motivi degli errori <!-- 1471783 -->
Nella pagina di panoramica delle registrazioni è possibile visualizzare la tendenza degli errori di registrazione e le prime cinque cause di errore. Facendo clic sul grafico o sulla tabella è possibile espandere i dettagli per trovare consigli sulla risoluzione dei problemi e suggerimenti per la correzione.


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Advanced Threat Protection (ATP) e Intune sono completamente integrati <!-- 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) indica il livello di rischio dei dispositivi Windows 10. In Windows Defender Security Center (portale ATP) è possibile creare una connessione a Microsoft Intune. Dopo averla creata, vengono usati i criteri di conformità di Intune per determinare un livello di minaccia accettabile. Se il livello di minaccia viene superato, i criteri di accesso condizionale di Azure Active Directory (AD) possono bloccare l'accesso a diverse app all'interno dell'organizzazione.

Questa funzionalità consente ad ATP di analizzare i file, rilevare le minacce e segnalare eventuali rischi nei dispositivi Windows 10.

Vedere [Abilitare ATP con l'accesso condizionale in Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Supporto per dispositivi senza utente associato <!-- 1637553 -->
Intune supporta la possibilità di valutare la conformità nei dispositivi senza utente associato, ad esempio Microsoft Surface Hub. I criteri di conformità potranno avere come destinazione dispositivi specifici. Sarà quindi possibile determinare la conformità (e la mancata conformità) dei dispositivi senza un utente associato.

#### <a name="delete-autopilot-devices----1713650---"></a>Eliminare dispositivi di AutoPilot <!-- 1713650 -->
Gli amministratori di Intune possono [eliminare i dispositivi AutoPilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Miglioramento dell'esperienza di eliminazione di dispositivi <!--1832333 -->
Non è più necessario rimuovere i dati aziendali o eseguire il ripristino delle impostazioni predefinite in un dispositivo prima di [eliminare quest'ultimo da Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Per visualizzare la nuova esperienza, accedere a Intune e selezionare **Dispositivi** > **Tutti i dispositivi** > nome del dispositivo > **Elimina**.

Se si vuole comunque la conferma di cancellazione/ritiro, è possibile usare il percorso standard del ciclo di vita del dispositivo tramite i comandi **Rimuovi i dati aziendali** e **Ripristino delle impostazioni predefinite** prima di **Elimina**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Riprodurre suoni in iOS in modalità di dispositivo perso <!-- 1947769 -->
Quando un dispositivo iOS sotto supervisione si trova in [Modalità di dispositivo perso](device-lost-mode.md) della gestione di dispositivi mobili (MDM), è possibile [riprodurre un suono](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo iOS > **Panoramica** > **Altro**). Il suono continua finché la modalità di dispositivo perso non viene cambiata o un utente non disabilita il suono dal dispositivo. Si applica ai dispositivi iOS 9.3 e successivi.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloccare o consentire i risultati Web nelle ricerche eseguite in un dispositivo Intune <!--1972804-->

Gli amministratori ora possono bloccare i risultati Web dalle ricerche eseguite in un dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Miglioramento della messaggistica per gli errori di caricamento del certificato push MDM Apple <!-- 2172331 -->

Il messaggio di errore spiega che per rinnovare un certificato MDM esistente è necessario usare lo stesso ID Apple.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testare il Portale aziendale per macOS nelle macchine virtuali <!-- 2216679 -->

Sono state pubblicate indicazioni per consentire agli amministratori IT di testare l'app Portale aziendale per macOS su macchine virtuali in Parallels Desktop e VMware Fusion. Per altre informazioni, vedere [Registrare le macchine virtuali macOS per i test](macos-enroll.md#enroll-virtual-macos-machines-for-testing).

### <a name="intune-apps"></a>App di Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS <!--1412866 -->
È stato rilasciato un aggiornamento dell'esperienza utente principale per l'app Portale aziendale per iOS. L'aggiornamento prevede una riprogettazione visiva completa che include un aspetto visivo e una modalità di interazione più moderni. È stata mantenuta la funzionalità dell'app aumentando la facilità di utilizzo e l'accessibilità.  

Saranno inoltre disponibili:
- Supporto per iPhone X.
- Avvio delle app e caricamento più veloci per consentire agli utenti di risparmiare tempo.
- Indicatori di stato aggiuntivi per offrire agli utenti le informazioni sullo stato più aggiornate.
- Miglioramenti della modalità di caricamento dei log. Se si verificano problemi, è più semplice segnalarlo.  

Per visualizzare l'aspetto aggiornato, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Proteggere i dati di Exchange locali usando i criteri di protezione delle app e l'accesso condizionale di Intune <!-- 1056954 -->
È ora possibile usare i criteri di protezione delle app e l'accesso condizionale di Intune per proteggere l'accesso ai dati di Exchange locali con Outlook Mobile. Per aggiungere o modificare i criteri di protezione delle app nel portale di Azure, selezionare **Microsoft Intune** > **App client** > **Criteri di protezione delle app**. Prima di usare questa funzionalità, assicurarsi che siano soddisfatti i [requisiti di Outlook per iOS e Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx).


### <a name="user-interface"></a>Interfaccia utente

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Riquadri di dispositivo migliorati nel Portale aziendale di Windows 10 <!--2213364 -->

I riquadri sono stati aggiornati per essere più accessibili agli utenti con problemi di ipovisione e per offrire prestazioni migliori per gli strumenti di lettura dello schermo.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Inviare i report di diagnostica nell'app Portale aziendale per macOS <!-- 2216677 -->
L'app Portale aziendale per i dispositivi macOS è stata aggiornata per migliorare il modo in cui gli utenti segnalano gli errori relativi a Intune. Dall'app Portale aziendale gli utenti possono:

- Caricare i report di diagnostica direttamente al team di sviluppo Microsoft.
- Inviare tramite posta elettronica l'ID evento imprevisto al team di supporto IT della società.

Per altre informazioni, vedere [Inviare gli errori per macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune si adatta a Fluent Design System nell'app Portale aziendale per Windows 10 <!-- 1195010 -->
L'app Portale aziendale Intune per Windows 10 è stata aggiornata con la [visualizzazione della navigazione di Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). A lato dell'app si noterà un elenco verticale statico di tutte le pagine di primo livello. Fare clic su un collegamento per visualizzare rapidamente tutte le pagine e passare da una all'altra. Questo è il primo di molti aggiornamenti che saranno resi disponibili come parte del continuo impegno per creare un'esperienza più adattiva, empatica e familiare in Intune. Per visualizzare l'aspetto aggiornato, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

<!-- ########################## -->
## <a name="march-2018"></a>Marzo 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Avvisi per le app line-of-business (LOB) iOS in scadenza per Microsoft Intune <!-- 748789 -->

Intune segnala nel portale di Azure le app line-of-business iOS che stanno per scadere. Dopo che una nuova versione dell'app line-of-business iOS è stata caricata, Intune rimuove la notifica di scadenza dall'elenco delle app. La notifica di scadenza sarà attiva solo per le app line-of-business iOS caricate di recente. Viene visualizzato un avviso 30 giorni prima della scadenza del profilo di provisioning dell'app line-of-business iOS. Dopo la scadenza, l'avviso viene sostituito dall'indicazione Scaduto.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalizzare i temi del Portale aziendale con codici esadecimali <!--1049561 -->

È possibile personalizzare il colore del tema nelle app Portale aziendale usando codici esadecimali. Quando si immette il codice esadecimale, Intune determina il colore del testo che offre il livello di contrasto massimo tra colore del testo e colore di sfondo. È possibile visualizzare in anteprima un confronto tra il colore del testo e il logo della società e il colore in **App client** > **Portale aziendale**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusione ed esclusione dell'assegnazione delle app in base ai gruppi per Android Enterprise <!-- 1813081 -->

Android Enterprise (denominato in precedenza Android for Work) supporta l'inclusione e l'esclusione di gruppi, ma non supporta i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi**. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestione dei dispositivi

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome----2258071---"></a>Esportare tutti i dispositivi in file CSV in Internet Explorer, Microsoft Edge o Chrome <!-- 2258071 -->
In **Dispositivi** > **Tutti i dispositivi** è possibile **esportare** i dispositivi in un elenco in formato CSV. Gli utenti di Internet Explorer (IE) con più di 10.000 dispositivi possono esportare i propri dispositivi in più file. Ogni file include fino a 10.000 dispositivi.

Gli utenti di Microsoft Edge e Chrome con più di 30.000 dispositivi possono esportare i propri dispositivi in più file. Ogni file include fino a 30.000 dispositivi.

[Gestire dispositivi](device-management.md) offre ulteriori dettagli sulle operazioni eseguibili con i dispositivi gestiti.

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nuovi miglioramenti della sicurezza nel servizio Intune  <!-- 1637539 -->   

È stato introdotto un tasto di alternanza in Intune in Azure che i clienti autonomi di Intune possono usare per gestire i dispositivi senza criteri assegnati come **conformi** (funzionalità di sicurezza disattivata) o **non conformi** (funzionalità di sicurezza attivata). Ciò garantirà l'accesso alle risorse solo dopo la valutazione della conformità del dispositivo.

Questa funzionalità ha effetti diversi a seconda che siano già stati assegnati o meno i criteri di conformità.

- Per gli account nuovi o esistenti in cui non sono assegnati criteri di conformità ai dispositivi, il tasto di alternanza è impostato automaticamente su **Conforme**. La funzionalità è disattivata nella console per impostazione predefinita. Non c'è alcun impatto sull'utente finale.
- Per gli account esistenti in cui sono assegnati criteri di conformità ai dispositivi, il tasto di alternanza è impostato automaticamente su **Non conforme**. La funzionalità è attivata per impostazione predefinita, a partire dall'implementazione dell'aggiornamento di marzo.

Se si usano criteri di conformità con accesso condizionale e la funzionalità è attivata, tutti i dispositivi senza alcun criterio di conformità assegnato vengono bloccati dall'accesso condizionale. Gli utenti finali associati a questi dispositivi e in precedenza autorizzati ad accedere alla posta elettronica perdono l'accesso, a meno che a tutti i dispositivi non venga assegnato almeno un criterio di conformità.   

Si noti che sebbene lo stato del tasto di alternanza predefinito venga visualizzato immediatamente nell'interfaccia utente con gli aggiornamenti di marzo del servizio Intune, lo stato non viene applicato immediatamente. Eventuali modifiche apportate al tasto di alternanza non influiscono sulla conformità del dispositivo fino a quando non viene distribuito in anteprima un tasto di alternanza funzionante per l'account. Al termine della distribuzione in anteprima, verrà inviata una comunicazione tramite il Centro messaggi. L'operazione potrebbe richiedere alcuni giorni dopo l'aggiornamento di marzo del servizio Intune.

**Informazioni aggiuntive**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Rilevamento ottimizzato per jailbreak <!-- 846515 -->

Il rilevamento ottimizzato per jailbreak è una nuova impostazione di conformità che migliora la valutazione dei dispositivi jailbroken da parte di Intune. L'impostazione usa i servizi di posizione per attivare con maggiore frequenza l'archiviazione del dispositivo con Intune. Ciò può influire sull'utilizzo della batteria.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Reimpostare le password per i dispositivi Android O <!-- 1238299 -->
Sarà possibile reimpostare le password per i dispositivi Android 8.0 registrati con profili di lavoro. Quando si invia una richiesta "Reimposta password" a un dispositivo Android 8.0, viene impostata una nuova password di sblocco del dispositivo o una nuova richiesta di verifica del profilo gestito per l'utente corrente. La password o la richiesta viene inviata e diventa immediatamente effettiva.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Assegnazione dei criteri di conformità a dispositivi in gruppi di dispositivi <!--1307012 -->

È possibile assegnare i criteri di conformità agli utenti in gruppi utenti. Con questo aggiornamento è possibile assegnare i criteri di conformità ai dispositivi in gruppi di dispositivi. I dispositivi inclusi in gruppi di dispositivi non riceveranno azioni di conformità.

#### <a name="new-management-name-column----1333586---"></a>Nuova colonna Nome di gestione <!-- 1333586 -->
 Una nuova colonna denominata **Nome di gestione** è disponibile nel pannello Dispositivi. Si tratta di un nome generato automaticamente e non modificabile assegnato a ogni dispositivo, in base alla formula seguente:
- Nome predefinito per tutti i dispositivi: <username><em><devicetype></em><enrollmenttimestamp>
- Per i dispositivi aggiunti in blocco: < PackageId/ProfileId ><em><DeviceType></em><EnrollmentTime>

Questa colonna è facoltativa nel pannello Dispositivi. Non è disponibile per impostazione predefinita ed è possibile accedervi solo tramite il selettore di colonna. Il nome del dispositivo non è interessato da questa nuova colonna.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>Ai dispositivi iOS viene richiesto un codice PIN ogni 15 minuti <!--1550837 -->
Dopo l'applicazione di criteri di conformità o configurazione a un dispositivo iOS, agli utenti viene richiesto di impostare un PIN ogni 15 minuti. La richiesta verrà visualizzata continuamente fino a quando non verrà impostato un PIN.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Pianificare gli aggiornamenti automatici <!--1805514 -->
Intune offre un controllo sull'installazione di aggiornamenti automatici mediante [le impostazioni degli anelli di Windows Update](windows-update-for-business-configure.md). Dopo questo aggiornamento sarà possibile pianificare gli aggiornamenti ricorrenti, nonché la settimana, il giorno e l'ora.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Usare il nome distinto completo come soggetto per il certificato SCEP <!--2221763 -->
Quando si crea un profilo certificato SCEP, immettere il nome del soggetto. Dopo questo argomento, sarà possibile usare il nome distinto completo come soggetto. Per **Nome soggetto**, selezionare **Personalizzato** e immettere `CN={{OnPrem_Distinguished_Name}}`. Usare la variabile `{{OnPrem_Distinguished_Name}}`, assicurarsi di sincronizzare l'attributo utente `onpremisesdistingishedname` usando [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Attivare la condivisione dei contatti Bluetooth - Android for Work <!--1098983 -->
Per impostazione predefinita, Android non consente la sincronizzazione dei contatti nel profilo di lavoro con i dispositivi Bluetooth. Di conseguenza, i contatti del profilo di lavoro non vengono visualizzati nell'ID chiamante per i dispositivi Bluetooth.

Dopo questo aggiornamento, sarà presente una nuova impostazione in **Android for Work** > **Limitazioni del dispositivo** > **Impostazioni del profilo di lavoro**:
- Contact sharing via Bluetooth (Contatto condivisione tramite Bluetooth)

L'amministratore di Intune può configurare queste impostazioni per abilitare la condivisione. Ciò è utile quando si associa un dispositivo a un dispositivo Bluetooth da usare in macchina che visualizza l'ID chiamante per l'uso del viva voce. Quando l'impostazione è abilitata, i contatti del profilo di lavoro vengono visualizzati. Quando l'impostazione non è abilitata, i contatti del profilo di lavoro non vengono visualizzati.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Configurare Gatekeeper per controllare l'origine del download delle app macOS <!-- 1690459 -->

È possibile configurare Gatekeeper per la protezione dei dispositivi controllando da dove possono essere scaricate le app. È possibile configurare le origini di download seguenti: **Mac App Store**, **Mac App Store e sviluppatori identificati** o **Ovunque**. È anche possibile specificare se gli utenti possono installare un'app usando CTRL+clic per eseguire l'override di questi controlli di Gatekeeper.

Queste impostazioni sono disponibili in **Configurazione del dispositivo** -> **Crea profilo** -> **macOS** -> **Endpoint protection**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurare il firewall dell'applicazione Mac <!-- 1690461 -->

È possibile configurare il firewall dell'applicazione Mac. Usare questa impostazione per controllare le connessioni in base all'applicazione, anziché in base alla porta. Questo rende più semplice ottenere i vantaggi della protezione con firewall e contribuisce a impedire che app indesiderate assumano il controllo delle porte di rete aperte per app legittime.

Questa funzione è disponibile in **Configurazione del dispositivo** -> **Crea profilo** -> **macOS** -> **Endpoint protection**.

Dopo aver abilitato l'impostazione del firewall, configurare il firewall utilizzando una delle due strategie seguenti:

- Bloccare tutte le connessioni in ingresso

   Vengono bloccate tutte le connessioni in ingresso per i dispositivi di destinazione. Se si sceglie questa opzione, le connessioni in ingresso vengono bloccate per tutte le app.

- Consentire o bloccare app specifiche

   È possibile consentire o bloccare la ricezione di connessioni in ingresso per app specifiche. È inoltre possibile abilitare la modalità mascheramento per impedire l'invio di risposte alle richieste di probe.

#### <a name="detailed-error-codes-and-messages----1376342---"></a>Messaggi e codici di errore dettagliati <!-- 1376342 -->

Nella configurazione del dispositivo sono disponibili per la visualizzazione più messaggi di errore e codici di errore dettagliati. Con questo miglioramento della creazione di report, vengono visualizzati le impostazioni, lo stato delle impostazioni e i dettagli sulla risoluzione dei problemi.

##### <a name="more-information"></a>Altre informazioni

- Bloccare tutte le connessioni in ingresso

   Con questa opzione si impedisce a tutti i servizi di condivisione, ad esempio Condivisione file e Condivisione schermo, di ricevere le connessioni in ingresso. I servizi di sistema che rimangono autorizzati a ricevere connessioni in ingresso sono:
  - configd: implementa DHCP e altri servizi di configurazione di rete
  - mDNSResponder: implementa Bonjour
  - racoon - implements IPSec

    Per utilizzare i servizi di condivisione, assicurarsi che **Connessioni in ingresso** sia impostata su **Non configurato** e non **Blocca**.

- Modalità mascheramento

   Abilitare questa modalità per impedire che il computer risponde alle richieste di probe. Il computer risponde comunque alle richieste in ingresso provenienti da app autorizzate. Le richieste impreviste, ad esempio le richieste ICMP (ping), vengono ignorate.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Disabilitare i controlli al riavvio del dispositivo <!--1805490 -->
Intune consente di [gestire gli aggiornamenti software](windows-update-for-business-configure.md). Con questo aggiornamento, la proprietà <strong>Verifiche al riavvio</strong> è disponibile e abilitata per impostazione predefinita. Per ignorare i controlli che vengono eseguiti generalmente quando si riavvia un dispositivo, come ad esempio gli utenti attivi, i livelli di batteria e così via, selezionare <strong>Ignora</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nuovi canali Windows 10 Insider Preview disponibili per gli anelli di distribuzione <!-- 1746293 -->
Durante la creazione di un anello di distribuzione Windows 10 è ora possibile selezionare i canali di servizio Windows 10 Insider Preview seguenti:
- Build di Windows Insider &#8208; Veloce
- Build di Windows Insider &#8208; Lenta
- Versione della build di Windows Insider 

Per altre informazioni su questi canali, vedere [Gestire le build Insider Preview](https://insider.windows.com/for-business-organization-admin/).   
Per altre informazioni sulla creazione di canali di distribuzione in Intune, vedere [Gestire gli aggiornamenti software](windows-update-for-business-configure.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Nuove impostazioni di Windows Defender Exploit Guard <!-- 1631893 -->

Sono ora disponibili sei nuove impostazioni di <strong>Riduzione della superficie di attacco</strong> e funzionalità <strong>Accesso controllato alle cartelle: Protezione delle cartelle</strong> avanzate. Queste impostazioni sono disponibili in: Configurazione del dispositivo\Profili\
Crea profilo\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco

|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Protezione ransomware avanzata|Abilitato, Controllo, Non configurato|Usare una protezione ransomware aggressiva.|
|Flag della sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows|Abilitato, Controllo, Non configurato|Impostare flag per la sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows (lsass.exe).|
|Creazione di processi dai comandi PSExec e WMI|Blocca, Controllo, Non configurato|Bloccare le creazioni di processi originate dai comandi PSExec e WMI.|
|Processi non attendibili e non firmati eseguiti da USB|Blocca, Controllo, Non configurato|Bloccare i processi non attendibili e non firmati eseguiti da USB.|
|File eseguibili che non soddisfano i criteri di prevalenza, età o elenco attendibile|Blocca, Controllo, Non configurato|Bloccare l'esecuzione dei file eseguibili se non soddisfano i criteri di prevalenza, età o elenco attendibile.|

#### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

|              Nome impostazione               |                                                              Opzioni di impostazione                                                              | Descrizione |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protezione delle cartelle (già implementata) | Non configurato, Abilita, Solo controllo (già implementata)<br><br> <strong>Nuove</strong><br>Blocco della modifica del disco, controllo della modifica del disco |             |

Proteggere file e cartelle da modifiche non autorizzate eseguite da applicazioni non compatibili.<br><br>**Abilitare**: impedire alle app non attendibili di modificare o eliminare file nelle cartelle protette e di scrivere nei settori del disco.<br><br>
**Bloccare solo la modifica del disco**:<br>Impedire alle app non attendibili di scrivere nei settori del disco. Le app non attendibili possono ancora modificare o eliminare i file nelle cartelle protette.|

### <a name="intune-apps"></a>App di Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->

Tramite Azure Active Directory (Azure AD) è ora possibile limitare l'accesso ai siti Web nei dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure. Per altre informazioni, vedere [Controlli di accesso nell'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Aggiornamenti di elementi visivi nell'app Portale aziendale per Android <!--976944 -->

L'app Portale aziendale per Android è stata aggiornata e resa conforme alle linee guida di Android [Material Design](https://material.io/). È possibile visualizzare le immagini delle nuove icone nell'articolo [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Registrazione con il Portale aziendale migliorata <!-- 1874230 eeready-->
Gli utenti che registrano un dispositivo tramite il portale aziendale in Windows 10 build 1703 e successive possono ora completare il primo passaggio della registrazione senza uscire dall'app.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens e Surface Hub vengono ora visualizzati nell'elenco dei dispositivi <!--1725868 -->
È stato aggiunto il supporto per la visualizzazione dei dispositivi HoloLens e Surface Hub registrati in Intune nell'app del portale aziendale per Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Categorie libro personalizzate per eBook di Volume Purchase Program (VPP) <!-- 1488911 -->
È possibile creare categorie eBook personalizzate a cui assegnare eBook VPP. Gli utenti finali potranno vedere le categorie eBook appena create e i libri a esse assegnati. Per altre informazioni, vedere [Gestire le app e i libri acquistati con Volume Purchase Program con Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Modifiche al supporto per l'app Portale aziendale per l'opzione di invio di commenti e suggerimenti di Windows <!-- 2070166 -->
A partire dal 30 aprile 2018, l'opzione **Invia commenti e suggerimenti** nell'app Portale aziendale per Windows funziona solo per i dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 (1607) e versioni successive. L'opzione Invia commenti e suggerimenti non è più supportata se si usa l'app Portale aziendale per Windows con:  
- Windows 10, versione 1507  
- Windows 10, versione 1511  
- Windows Phone 8.1 

Se il dispositivo esegue Windows 10 RS1 o versione successiva, scaricare la versione più recente dell'app Portale aziendale di Windows dallo Store. Se si esegue una versione non supportata, è possibile continuare a inviare commenti e suggerimenti tramite i canali seguenti: 
- App hub di commenti e suggerimenti in Windows 10
- Posta elettronica: WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nuove impostazioni di Windows Defender Application Guard <!-- 1631890 -->

- **Abilitare l'accelerazione grafica**: gli amministratori possono attivare un processore di grafica virtuale per Windows Defender Application Guard. Questa impostazione consente alla CPU di passare il rendering della grafica alla vGPU. Ciò può migliorare le prestazioni durante l'uso di siti Web con molta grafica o la riproduzione di video all'interno del contenitore.

- **Salvare i file su host**: gli amministratori possono consentire il passaggio dei file da Microsoft Edge in esecuzione nel contenitore al file system dell'host. L'attivazione di questa impostazione consente agli utenti di scaricare i file da Microsoft Edge nel contenitore nel file system dell'host.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Criteri di protezione MAM assegnati in base allo stato di gestione <!-- 1665993 -->
È possibile assegnare i criteri MAM in base allo stato di gestione del dispositivo:
- **Dispositivi Android**: è possibile includere i dispositivi non gestiti, i dispositivi gestiti da Intune e i profili Android Enterprise gestiti da Intune (in precedenza denominato Android for Work).
- **Dispositivi iOS**: è possibile includere i dispositivi non gestiti (solo MAM) o i dispositivi gestiti da Intune.

    > [!NOTE]
    > - Il supporto iOS per questa funzionalità verrà implementato in aprile 2018.

Per altre informazioni, vedere [Target app protection policies based on device management state](app-protection-policies.md) (Assegnare i criteri di protezione delle app in base allo stato di gestione del dispositivo).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Miglioramenti del linguaggio dell'app del Portale aziendale per Windows <!-- 1683758 -->
È stato migliorato il linguaggio del Portale aziendale per Windows 10 per risultare più intuitivo e specifico per l'azienda. Per visualizzare alcune immagini delle novità, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Nuove aggiunte alla documentazione sulla privacy dell'utente <!-- 1440709 -->
Per offrire agli utenti finali un maggior controllo sui dati e sulla privacy, sono stati pubblicati aggiornamenti alla documentazione che descrivono come visualizzare e rimuovere i dati archiviati in locale dalle app del portale aziendale. Questi aggiornamenti sono disponibili in:

- **Android**: [Come annullare la registrazione del dispositivo Android da Intune](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, se l'utente ha rifiutato le condizioni per l'utilizzo**: [Annullare la registrazione del dispositivo se sono state rifiutate le Condizioni per l'utilizzo](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**: [Annullare la registrazione del dispositivo iOS da Intune](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**: [Annullare la registrazione del dispositivo Windows da Intune](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>Febbraio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 -->

Intune supporta ora la registrazione di dispositivi da un massimo di 100 account [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) o [Apple School Manager](apple-school-manager-set-up-ios.md) diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Visualizzare le restrizioni di registrazione per i singoli utenti <!-- 1634444 eeready wnready -->
Nel pannello **Risoluzione dei problemi** è ora possibile visualizzare le [restrizioni di registrazione](enrollment-restrictions-set.md) applicate per ogni utente selezionando **Restrizioni registrazione** nell'elenco **Assegnazioni**.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nuova opzione per l'autenticazione utente per la registrazione in blocco Apple <!-- 747625 eeready -->

> [!NOTE]
> I nuovi tenant la vedono immediatamente. Per i tenant esistenti, questa funzionalità verrà implementata nel corso del mese di aprile. Fino al termine dell'implementazione, non è possibile accedere a queste nuove funzionalità.

Intune offre ora la possibilità di autenticare i dispositivi con l'app Portale aziendale per i metodi di registrazione seguenti:

- Programma di registrazione del dispositivo mobile di Apple
- Apple School Manager
- Registrazione di Apple Configurator

Quando si usa l'opzione Portale aziendale, l'autenticazione a più fattori di Azure Active Directory può essere applicata senza bloccare questi metodi di registrazione.

Quando si usa l'opzione Portale aziendale, Intune ignora l'autenticazione utente nell'Assistente configurazione di iOS per la registrazione dell'affinità utente. Questo significa che il dispositivo viene inizialmente registrato come dispositivo senza utente e pertanto non riceve le configurazioni o i criteri dei gruppi utenti, ma solo le configurazioni e i criteri per i gruppi di dispositivi. Tuttavia, Intune installerà automaticamente l'app Portale aziendale nel dispositivo. Il primo utente che avvia l'app Portale aziendale e vi accede verrà associato al dispositivo in Intune. A questo punto, l'utente riceverà le configurazioni e i criteri dei gruppi utenti. L'associazione dell'utente non può essere modificata senza eseguire di nuovo la registrazione.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 eeready -->

Intune supporta ora la registrazione di dispositivi da un massimo di 100 account Apple Device Enrollment Program (DEP) o Apple School Manager diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Stampa remota su una rete protetta <!-- 1709994  -->
Le soluzioni di stampa mobile wireless di PrinterOn consentiranno agli utenti di eseguire stampe in modalità remota da qualsiasi posizione e in qualsiasi momento tramite una rete protetta. PrinterOn verrà integrato in Intune APP SDK sia per iOS che per Android. Sarà possibile assegnare i criteri di protezione delle app a questa app tramite il pannello **Criteri di protezione delle app** di Intune nella console di amministrazione. Gli utenti finali potranno scaricare l'app 'PrinterOn per Microsoft' tramite Play Store o iTunes da usare all'interno del loro ecosistema di Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Supporto del Portale aziendale macOS per le registrazioni che usano il manager di registrazione dispositivi <!-- 1352411 -->

Gli utenti ora possono usare il manager di registrazione dispositivi durante la registrazione con il portale aziendale macOS.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Report sullo stato di integrità e lo stato delle minacce di Windows Defender <!--854704 -->

Per gestire i PC Windows è di fondamentale importanza comprendere l'integrità e lo stato di Windows Defender.  Con questo aggiornamento Intune aggiunge nuovi report e azioni per lo stato e l'integrità dell'agente Windows Defender. Usando un report di rollup dello stato nel [carico di lavoro Conformità del dispositivo](compliance-policy-monitor.md) è possibile visualizzare i dispositivi per i quali è necessario:
- un aggiornamento della firma
- Riavvia
- un intervento manuale
- un'analisi completa
- un intervento per altri stati dell'agente

Un report di analisi per ogni categoria di stato elenca i singoli PC che richiedono attenzione o quelli per i quali è indicato **Pulisci**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nuove impostazioni di privacy per le restrizioni dei dispositivi <!--1308926 -->
Sono ora disponibili [due nuove impostazioni di privacy](device-restrictions-windows-10.md#privacy) per i dispositivi:
- **Pubblica le attività utente**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità per l'attività.
- **Solo attività locali**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità solo per l'attività locale.

#### <a name="new-settings-for-the-microsoft-edge-browser---1469166---"></a>Nuove impostazioni per il browser Microsoft Edge <!--1469166 -->
Sono ora disponibili [due nuove impostazioni](device-restrictions-windows-10.md#microsoft-edge-browser) per il **percorso del file dei Preferiti** e le **modifiche a Preferiti** per i dispositivi con browser Microsoft Edge.

### <a name="app-management"></a>Gestione delle app

#### <a name="protocol-exceptions-for-applications---1035509---"></a>Eccezioni di protocollo per le applicazioni <!--1035509 -->

Ora è possibile creare eccezioni ai criteri di trasferimento dati della gestione di applicazioni mobili (MAM) di Intune per aprire specifiche applicazioni non gestite. Le applicazioni devono essere considerate attendibile da IT. A differenza delle eccezioni create, il trasferimento dati rimane limitato alle applicazioni gestire da Intune quando i criteri di trasferimento dati sono impostati **solo per le app gestite**. È possibile creare le restrizioni tramite protocolli (iOS) o pacchetti (Android).

Ad esempio, è possibile aggiungere il pacchetto Webex come eccezione ai criteri di trasferimento dati MAM. In questo modo i collegamenti Webex in un messaggio di posta elettronica di Outlook gestito possono essere aperti direttamente nell'applicazione Webex. Il trasferimento dati rimarrà limitato nelle altre applicazioni non gestite. Per altre informazioni, vedere [Eccezioni dei criteri di trasferimento dei dati per le app](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dati crittografati di Windows Information Protection (WIP) nei risultati di ricerca di Windows <!-- 1469193 -->
Un'impostazione nei criteri di Windows Information Protection (WIP) consente ora di controllare se i dati crittografati WIP vengono inclusi nei risultati di ricerca di Windows. Impostare questa opzione dei criteri di protezione dell'app selezionando l'impostazione che **consente all'indicizzatore di Ricerca di Windows di cercare gli elementi crittografati** nelle **impostazioni avanzate** dei criteri di Windows Information Protection. I criteri di protezione dell'app devono essere impostati sulla piattaforma *Windows 10* e lo **stato di registrazione** dei criteri dell'app deve essere impostato su **Con registrazione**. Per altre informazioni, vedere [Consentire all'indicizzatore di Ricerca di Windows di cercare elementi crittografati](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurazione di un'app MSI per dispositivi mobili con aggiornamento automatico <!-- 1740840 -->
È possibile configurare un'app MSI per dispositivi mobili con aggiornamento automatico nota in modo che ignori il processo di controllo delle versioni. Questa funzionalità consente di evitare una race condition. Ad esempio, questo tipo di race condition può verificarsi quando l'app viene aggiornata automaticamente dallo sviluppatore di app e anche da Intune. In entrambi i casi è possibile che si tenti di imporre una versione dell'app in un client di Windows creando un conflitto. Per queste app MSI con aggiornamento automatico, è possibile configurare l'impostazione **Ignora la versione dell'app** nel pannello **Informazioni sull'app**. Se questa impostazione viene cambiata in **Sì**, Microsoft Intune ignorerà la versione dell'app installata nel client Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Insiemi correlati di licenze per le app supportati in Intune <!-- 1864117 -->
Intune nel portale di Azure ora supporta gli insiemi correlati di licenze per le app come elemento app singolo nell'interfaccia utente. Inoltre, tutte le app con licenza offline sincronizzate da Microsoft Store per le aziende verranno consolidate in una singola voce di app e verrà eseguita la migrazione di tutti i dettagli di distribuzione dei singoli pacchetti nella singola voce. Per visualizzare gli insiemi correlati di licenze per le app nel portale di Azure, selezionare **App licenses** (Licenze app) dal pannello **App client**.

### <a name="device-configuration"></a>Configurazione del dispositivo
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Estensioni di file di Windows Information Protection (WIP) per la crittografia automatica <!-- 1463582 -->
Un'impostazione nei criteri di Windows Information Protection (WIP) ora consente di specificare le estensioni di file che vengono automaticamente crittografate quando si esegue la copia da una condivisione di Server Message Block (SMB) all'interno dell'azienda, come definito nei criteri di WIP.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurare le impostazioni dell'account della risorsa per i dispositivi Surface Hub

Ora è possibile configurare in modalità remota le impostazioni dell'account della risorsa per i dispositivi Surface Hub.

L'account della risorsa viene usato dal dispositivo Surface Hub per l'autenticazione con Skype/Exchange per poter partecipare a una riunione.
Creare un account della risorsa univoco in modo che il dispositivo Surface Hub compaia nella riunione come sala riunioni.
Ad esempio, l'account della risorsa potrebbe essere visualizzato come **Sala riunioni B41/6233**.

> [!NOTE]
> - Se non si specifica alcun valore nei campi, gli attributi configurati in precedenza sul dispositivo verranno sostituiti.
>
> - Le proprietà dell'account della risorsa possono essere modificate dinamicamente nel dispositivo Surface Hub. Ad esempio, nel caso in cui sia attivata la rotazione delle password. Di conseguenza, è possibile che i valori nella console di Azure non riflettano immediatamente la realtà del dispositivo.
>
>   Per individuare la configurazione corrente nel dispositivo Surface Hub, i dati dell'account della risorsa possono essere inclusi nell'inventario hardware (per il quale è già impostato un intervallo di 7 giorni) o come proprietà di sola lettura. Per una maggior precisione dopo l'esecuzione dell'azione remota, è possibile ottenere lo stato dei parametri subito dopo l'esecuzione dell'azione per aggiornare l'account e i parametri nel dispositivo Surface Hub.

##### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco

|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Esecuzione dalla posta elettronica del contenuto eseguibile protetto da password|Blocca, Controllo, Non configurato|Evitare l'esecuzione dei file eseguibili protetti da password scaricati usando la posta elettronica.|
|Protezione ransomware avanzata|Abilitato, Controllo, Non configurato|Usare una protezione ransomware aggressiva.|
|Flag della sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows|Abilitato, Controllo, Non configurato|Impostare flag per la sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows (lsass.exe).|
|Creazione di processi dai comandi PSExec e WMI|Blocca, Controllo, Non configurato|Bloccare le creazioni di processi originate dai comandi PSExec e WMI.|
|Processi non attendibili e non firmati eseguiti da USB|Blocca, Controllo, Non configurato|Bloccare i processi non attendibili e non firmati eseguiti da USB.|
|File eseguibili che non soddisfano i criteri di prevalenza, età o elenco attendibile|Blocca, Controllo, Non configurato|Bloccare l'esecuzione dei file eseguibili se non soddisfano i criteri di prevalenza, età o elenco attendibile.|

##### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

|              Nome impostazione               |                                                              Opzioni di impostazione                                                              | Descrizione |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protezione delle cartelle (già implementata) | Non configurato, Abilita, Solo controllo (già implementata)<br><br> <strong>Nuove</strong><br>Blocco della modifica del disco, controllo della modifica del disco |             |

Proteggere file e cartelle da modifiche non autorizzate eseguite da applicazioni non compatibili.<br><br>**Abilitare**: impedire alle app non attendibili di modificare o eliminare file nelle cartelle protette e di scrivere nei settori del disco.<br><br>
**Bloccare solo la modifica del disco**:<br>Impedire alle app non attendibili di scrivere nei settori del disco. Le app non attendibili possono ancora modificare o eliminare i file nelle cartelle protette.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Nuove impostazioni di sicurezza del sistema per Windows 10 e nuovi criteri di conformità <!--1704133-->

Sono ora disponibili nuove impostazioni di conformità di Windows 10, inclusa la richiesta di Firewall e Windows Defender Antivirus.

### <a name="intune-apps"></a>App di Intune

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Supporto per le app offline da Microsoft Store per le aziende <!--1222672-->
Le app offline acquistate da Microsoft Store per le aziende ora vengono sincronizzate nel portale di Azure. È quindi possibile distribuire le app ai gruppi di dispositivi o ai gruppi di utenti. Le app offline vengono installate da Intune, non dallo Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro <!-- 1728700 -->

Quando si distribuisce l'app Gmail in un profilo Android for Work, è ora possibile impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro usando l'impostazione **Aggiungi o rimuovi account** nel profilo delle restrizioni per dispositivi Android for Work.

<!-- ########################## -->
## <a name="january-2018"></a>Gennaio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Avvisi per i token scaduti e i token che scadranno a breve <!-- 1639263 -->
Nella pagina di panoramica vengono visualizzati ora avvisi per i token scaduti e i token che scadranno a breve. Facendo clic su un avviso per un singolo token si passerà alla pagina dei dettagli del token.  Se si fa clic su un avviso con più token, verrà visualizzato un elenco di tutti i token con il relativo stato. Gli amministratori devono rinnovare i relativi token prima della scadenza.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Supporto del comando di cancellazione remoto per dispositivi macOS <!-- 1438084 -->

Gli amministratori possono eseguire un comando di cancellazione in remoto da dispositivi macOS.

> [!IMPORTANT]
> Il comando di cancellazione non può essere annullato e deve essere usato con cautela.

Il comando di cancellazione rimuove tutti i dati, incluso il sistema operativo, da un dispositivo. Rimuove anche il dispositivo dalla gestione di Intune. Non viene visualizzato alcun avviso all'utente e la cancellazione viene eseguita immediatamente.

È necessario configurare un PIN di ripristino di 6 cifre. Questo PIN può essere usato per sbloccare il dispositivo cancellato e a quel punto verrà avviata la reinstallazione del sistema operativo. Dopo l'avvio della cancellazione, il PIN viene visualizzato in una barra di stato nel pannello della panoramica del dispositivo in Intune. Il PIN verrà mantenuto per tutta la durata del processo di cancellazione. Dopo il completamento della cancellazione, il dispositivo scompare del tutto dalla gestione di Intune. Assicurarsi di registrare il PIN di ripristino in modo che possa essere usato da chiunque esegua il ripristino del dispositivo.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revocare le licenze per un token Volume Purchasing Program iOS <!-- 820870 -->
È possibile revocare la licenza di tutte le app Volume Purchasing Program (VPP) iOS per un determinato token VPP.

### <a name="app-management"></a>Gestione delle app

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revoca delle app Volume Purchase Program iOS  <!-- 820863 -->
Per un dispositivo specifico con una o più app Volume Purchase Program (VPP) iOS, è possibile revocare la licenza per app basata su dispositivo associata al dispositivo stesso. La revoca di una licenza per app non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. Per altre informazioni, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Assegnare le app per dispositivi mobili Office 365 a dispositivi iOS e Android usando il tipo di app predefinito <!-- 1332318 -->
Il tipo di app **Predefinito** consente di creare e assegnare in modo semplice le app Office 365 a dispositivi iOS e Android gestiti. Le app includono le app 0365 come Word, Excel, PowerPoint e OneDrive. È possibile assegnare app specifiche al tipo di app e modificare la configurazione delle informazioni sull'app.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusione ed esclusione per l'assegnazione di app in base ai gruppi <!-- 1406920 -->

Durante l'assegnazione di app e dopo aver selezionato un tipo di assegnazione, è possibile selezionare i gruppi da includere, così come i gruppi da escludere.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>È possibile assegnare un criterio di configurazione dell'applicazione ai gruppi includendo ed escludendo le assegnazioni  <!-- 1480316 -->

È possibile assegnare un criterio di configurazione dell'applicazione a un gruppo di utenti e dispositivi tramite una combinazione di assegnazioni di inclusione ed esclusione. È possibile scegliere le assegnazioni come selezione personalizzata di gruppi o come gruppo virtuale. Un gruppo virtuale può includere **Tutti gli utenti**, **Tutti i dispositivi** o **Tutti gli utenti + Tutti i dispositivi**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Supporto dei criteri di aggiornamento edizione di Windows 10   <!-- 903672(archived), 1119689 -->  
È possibile creare criteri di aggiornamento edizione di Windows 10 per l'aggiornamento di dispositivi Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Per informazioni dettagliate sugli aggiornamenti edizione di Windows 10, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>I criteri di accesso condizionale per Intune sono disponibili solo dal portale di Azure  <!-- 1737088 1634311 -->

A partire da questa versione, è necessario configurare e gestire i criteri di accesso condizionale nel [portale di Azure](https://portal.azure.com) da **Azure Active Directory** > **Accesso condizionale**. Per praticità, è possibile accedere a questo pannello anche da Intune nel portale di Azure in **Intune** > **Accesso condizionale**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Aggiornamenti per i messaggi di posta elettronica di conformità <!--1637547 -->

Quando viene inviato un messaggio di posta elettronica per segnalare un dispositivo non conforme, vengono inclusi dettagli sul dispositivo non conforme.

### <a name="intune-apps"></a>App di Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nuove funzionalità per l'azione "Risolvi" per i dispositivi Android <!--1583480-->

L'app Portale aziendale per Android sta estendendo l'azione "Risolvi" di **Aggiorna impostazioni del dispositivo** in modo da risolvere i [problemi di crittografia del dispositivo](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Blocco remoto disponibile nell'app Portale aziendale per Windows 10 <!--676506-->
Gli utenti possono ora bloccare i dispositivi in modalità remota dall'app Portale aziendale per Windows 10. L'opzione non verrà visualizzata per il dispositivo locale in uso.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Risoluzione dei problemi di conformità semplificata per l'app Portale aziendale per Windows 10 <!--676546-->
Gli utenti finali con dispositivi Windows potranno toccare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema.

<!-- ########################## -->
## <a name="december-2017"></a>Dicembre 2017

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nuova impostazione per la ridistribuzione automatica <!-- 1469168 -->
L'impostazione **Ridistribuzione automatica** consente agli utenti con diritti amministrativi di eliminare tutti i dati utente e tutte le impostazioni utente usando **CTRL+tasto WINDOWS+R** nella schermata di blocco del dispositivo. Il dispositivo viene automaticamente riconfigurato e registrato di nuovo nella gestione. Questa impostazione è disponibile in Windows 10 > Limitazioni del dispositivo > Generale > Ridistribuzione automatica. Per i dettagli, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Supporto di altre edizioni di origine nei criteri di aggiornamento dell'edizione di Windows 10  <!-- 903672,  1119689 -->
È ora possibile usare i criteri di aggiornamento dell'edizione di Windows 10 per l'aggiornamento da altre edizioni di Windows 10 (Windows 10 Pro, Windows 10 Pro Education, Windows 10 Cloud e così via). Prima di questa versione, i percorsi di aggiornamento delle edizioni supportati erano più limitati. Per altri dettagli, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Nuove impostazioni per il profilo di configurazione del dispositivo Windows Defender Security Center (WDSC) <!-- 1335507 -->

Intune aggiunge una nuova sezione alle impostazioni per il profilo di configurazione del dispositivo in Endpoint Protection denominata **Windows Defender Security Center**. Gli amministratori IT possono configurare gli elementi chiave dell'app Windows Defender Security Center accessibili per gli utenti finali. Se un amministratore IT nasconde un elemento chiave nell'app Windows Defender Security Center, tutte le notifiche correlate all'elemento nascosto non vengono visualizzate nel dispositivo dell'utente.

Questi sono gli elementi chiave che gli amministratori possono nascondere dalle impostazioni del profilo di configurazione del dispositivo per Windows Defender Security Center:
- Protezione da virus e minacce
- Prestazioni e integrità del dispositivo
- Protezione firewall e della rete
- Controllo delle app e del browser
- Opzioni famiglia

Gli amministratori IT possono anche personalizzare le notifiche ricevute dagli utenti. Ad esempio, è possibile specificare se gli utenti ricevono tutte le notifiche generate dagli elementi chiave visibili in WDSC o solo le notifiche critiche. Le notifiche non critiche includono riepiloghi periodici delle attività di Windows Defender Antivirus e notifiche per il completamento delle analisi. Tutte le altre notifiche sono considerate critiche. È inoltre possibile personalizzare il contenuto della notifica, ad esempio specificare informazioni di contatto IT da incorporare nelle notifiche visualizzate sui dispositivi degli utenti.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Supporto di più connettori per la gestione dei certificati SCEP e PFX <!-- 1361755 -->

I clienti che usano NDES Connector in locale per il recapito dei certificati ai dispositivi possono ora configurare più connettori in un singolo tenant.

Questa nuova funzionalità supporta lo scenario seguente:

- **Disponibilità elevata**

Ogni istanza di NDES Connector esegue il pull delle richieste di certificato da Intune.  Se un'istanza di NDES Connector risulta offline, l'altro connettore può continuare a elaborare le richieste.

#### <a name="customer-subject-name-can-use-aad_device_id-variable-----1468599---"></a>Per il nome soggetto del cliente è possibile usare la variabile AAD_DEVICE_ID  <!-- 1468599 -->

Quando si crea un profilo certificato SCEP in Intune, è ora possibile usare la variabile AAD_DEVICE_ID quando si compila il nome soggetto personalizzato.   Quando viene richiesto il certificato con questo profilo SCEP, la variabile viene sostituita con l'ID del dispositivo AAD del dispositivo che effettua la richiesta di certificato.


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gestire dispositivi macOS registrati in Jamf con il motore di conformità dei dispositivi di Intune <!-- 1592747 -->
È ora possibile usare Jampf per inviare informazioni sullo stato dei dispositivi macOS a Intune, che ne valuterà la conformità ai criteri definiti nella console di Intune. In base allo stato di conformità dei dispositivi e ad altre condizioni (ad esempio la posizione, il rischio utente e così via), l'accesso condizionale imporrà la conformità ai dispositivi macOS che accedono alle applicazioni cloud e locali connesse ad Azure AD, incluso Office 365. Altre informazioni sulla [configurazione dell'integrazione Jamf](conditional-access-integrate-jamf.md) e l'[applicazione della conformità per i dispositivi gestiti Jamf](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nuova azione per dispositivi iOS   <!-- 1424701 -->

È ora possibile arrestare i dispositivi iOS 10.3 con supervisione. Questa azione arresta il dispositivo immediatamente senza avviso all'utente finale. L'azione **Shut down (supervised only)** (Arresta - solo con supervisione) è disponibile nelle proprietà del dispositivo quando si seleziona un dispositivo nel carico di lavoro **Dispositivo**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Impedire modifiche di data/ora nei dispositivi Samsung Knox <!-- 1468103 -->

È stata aggiunta a una nuova funzionalità che consente di bloccare le modifiche di data e ora nei dispositivi Samsung Knox. Questa impostazione è disponibile in **Profili di configurazione dei dispositivi** > **Limitazioni del dispositivo (Android)**  > **Generale**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Supporto dell'account della risorsa per Surface Hub <!-- 1566442  -->

È stata aggiunta una nuova azione del dispositivo in modo gli amministratori possano definire e aggiornare l'account della risorsa associato a un dispositivo Surface Hub.

L'account della risorsa viene usato da Surface Hub per l'autenticazione con Skype/Exchange in modo da poter partecipare a una riunione. È possibile creare un account della risorsa univoco in modo che il dispositivo Surface Hub compaia nella riunione come sala riunioni. Ad esempio, l'account della risorsa potrebbe essere visualizzato come *Sala riunioni B41/6233*. L'account della risorsa (noto come account del dispositivo) per Surface Hub in genere deve essere configurato per la posizione della sala riunione e quando occorre modificare altri parametri dell'account della risorsa.

Quando gli amministratori vogliono aggiornare l'account della risorsa in un dispositivo, devono specificare le credenziali correnti di Active Directory o Azure Active Directory associate al dispositivo. Se la rotazione delle password è attivata per il dispositivo, gli amministratori devono passare ad Azure Active Directory per trovare la password.

> [!NOTE]
> Tutti i campi vengano inviati in blocco e sovrascrivono tutti i campi configurati in precedenza. Anche i campi vuoti sovrascrivono i campi esistenti.

L'elenco seguente include le impostazioni configurabili dagli amministratori:

- **Account della risorsa**
  - **Utente di Active Directory**

    NomeDominio\NomeUtente o nome dell'entità utente (UPN): user@domainname.com

  - **Password**

- **Parametri facoltativi per l'account della risorsa** (devono essere impostati tramite l'account della risorsa specificato)

  - **Periodo di rotazione delle password**

    Assicura che la password dell'account venga aggiornata automaticamente da Surface Hub ogni settimana per motivi di sicurezza. Per configurare eventuali parametri dopo aver abilitato questo account, è prima di tutto necessario reimpostare la password dell'account in Azure Active Directory.

  - **Indirizzo SIP (Session Initiation Protocol)**

    Usato solo quando l'individuazione automatica ha esito negativo.

  - **Posta elettronica**

    Indirizzo di posta elettronica di dispositivo/account della risorsa.

  - **Exchange Server**

    Necessario solo quando l'individuazione automatica ha esito negativo.

  - **Sincronizzazione calendario**

    Specifica se sono abilitati la sincronizzazione del calendario e altri servizi di Exchange Server. Ad esempio, la sincronizzazione delle riunioni.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installare app di Office in dispositivi macOS <!-- 1494311 -->
È ora possibile installare app di Office nei dispositivi macOS. Questo nuovo tipo di app consentirà di installare Word, Excel, PowerPoint, Outlook e OneNote. Queste app includono anche Microsoft AutoUpdater (MAU), per mantenere più facilmente sicure e aggiornate le app.

### <a name="app-management"></a>Gestione delle app

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminare un token Volume Purchasing Program iOS <!-- 820879 -->
È possibile eliminare il token Volume Purchasing Program (VPP) iOS tramite la console. Ciò potrebbe risultare necessario in presenza di istanze duplicate di un token VPP.

### <a name="intune-apps"></a>App di Intune


### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Una nuova raccolta di entità denominata Current User è limitata ai dati degli utenti attualmente attivi <!-- 1667026 -->

La raccolta di entità **Users** contiene tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione. Nel corso dell'ultimo mese, ad esempio, è possibile che un utente sia stato aggiunto e rimosso da Intune. Pertanto, se anche l'utente non è presente al momento del report, l'utente e lo stato sono comunque presenti nei dati. In questo caso, è possibile creare un report che mostri la durata della presenza storica dell'utente nei dati.

La nuova raccolta di entità **Current User**, invece, contiene solo gli utenti che non sono stati rimossi. La raccolta di entità **Current User**, quindi, è limitata agli utenti attualmente attivi. Per informazioni sulla raccolta di entità **Current User**, vedere [Informazioni di riferimento per l'entità User corrente](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>API Graph aggiornate <!-- 1736360 -->

In questa versione sono state aggiornate alcune delle API Graph per Intune in versione beta. Vedere il [log delle modifiche delle API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) mensile per altre informazioni.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune supporta le app non consentite di Windows Information Protection (WIP) <!-- 1479103 -->
È possibile specificare app non consentite in Intune. Le app non consentite non possono accedere alle informazioni aziendali e si tratta in effetti della condizione opposta alle app incluse nell'elenco delle app consentite. Per altre informazioni, vedere la [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Elenco consigliato delle app non consentite per Windows Information Protection).

<!-- ########################## -->
## <a name="november-2017"></a>Novembre 2017

### <a name="troubleshoot-enrollment-issues-----746324---"></a>Risolvere i problemi di registrazione  <!-- 746324 -->

L'area di lavoro **Risoluzione dei problemi** ora visualizza i problemi di registrazione dell'utente. Informazioni dettagliate sul problema e i passaggi suggeriti per la correzione possono essere utili ad amministratori e operatori di help desk per la risoluzione dei problemi. Alcuni problemi di registrazione non vengono rilevati ed è possibile che per alcuni errori non siano disponibili suggerimenti per la correzione.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrizioni di registrazione assegnate ai gruppi <!-- 747598 -->

L'amministratore di Intune ora può [creare restrizioni di registrazione Tipo di dispositivo e Limite di dispositivi personalizzate per i gruppi di utenti](enrollment-restrictions-set.md).

Il portale di Azure di Intune consente di creare fino a 25 istanze di ogni tipo di restrizione, che possono essere successivamente assegnate ai gruppi di utenti. Le restrizioni assegnate ai gruppi sostituiscono le restrizioni predefinite.

Tutte le istanze di un tipo di restrizione vengono mantenute in un elenco nell'ordine. L'ordine definisce un valore di priorità per la risoluzione dei conflitti. Un utente interessato da più istanze di restrizione viene limitato solo dall'istanza con il valore di priorità più alto. È possibile modificare la priorità di un'istanza specifica trascinandola in una posizione diversa nell'elenco.

Questa funzionalità verrà rilasciata con la migrazione delle impostazioni di Android for Work dal menu di registrazione di Android for Work al menu Restrizioni registrazione. Poiché la migrazione può richiedere diversi giorni, è possibile che l'account venga aggiornato per altre parti del rilascio di novembre prima che l'assegnazione dei gruppi risulti abilitata per le restrizioni di registrazione.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Supporto di più connettori del servizio Registrazione dispositivi di rete <!-- 1528104 -->

Il servizio Registrazione dispositivi di rete (NDES, Network Device Enrollment Service) consente ai dispositivi mobili in esecuzione senza credenziali di dominio di ottenere certificati basati sul protocollo SCEP (Simple Certificate Enrollment Protocol).
Con questo aggiornamento, sono supportati più connettori del servizio Registrazione dispositivi di rete.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gestire i dispositivi Android for Work indipendentemente dai dispositivi Android <!-- 1490731 EEready-->

Intune supporta la gestione della registrazione di dispositivi Android for Work indipendentemente dalla piattaforma Android. Queste impostazioni vengono gestite in **Registrazione del dispositivo** > **Restrizioni registrazione** > **Restrizioni sul tipo di dispositivi**. In precedenza erano disponibili in **Registrazione del dispositivo** > **Registrazione di Android for Work** > **Impostazioni di registrazione per Android for Work**.

Per impostazione predefinita, le impostazioni dei dispositivi Android for Work corrispondono alle impostazioni dei dispositivi Android. Tuttavia, dopo la modifica delle impostazioni Android for Work questa corrispondenza andrà persa.

Se si blocca la registrazione dei dispositivi Android for Work personali, solo i dispositivi Android aziendali possono essere registrati come Android for Work.

Durante l'uso delle nuove impostazioni, considerare i punti seguenti:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work non è mai stata caricata in precedenza

La nuova piattaforma Android for Work è bloccata nelle Restrizioni sul tipo di dispositivi predefinite. Dopo aver caricato la funzionalità, è possibile consentire la registrazione dei dispositivi con Android for Work. A tale scopo, modificare il valore predefinito o creare una nuova restrizione dei tipi di dispositivo per sostituire la restrizione predefinita.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work è stata caricata

Se la registrazione è stata caricata in precedenza, la situazione varia a seconda dell'impostazione selezionata:

| Impostazione | Stato di Android for Work nella restrizione dei tipi di dispositivo predefinita | Note |
| --- | --- | --- |
| **Gestisci tutti i dispositivi come Android** | Bloccato | Tutti i dispositivi Android devono essere registrati senza Android for Work. |
| **Gestisci i dispositivi supportati come Android for Work** | Consentito | Tutti i dispositivi Android che supportano Android for Work devono essere registrati con Android for Work. |
| **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work** | Bloccato | Per sostituire l'impostazione predefinita è stato creato un criterio Restrizione dei tipi di dispositivo separato. Questo criterio definisce i gruppi precedentemente selezionati per consentire la registrazione di Android for Work. Gli utenti inclusi nei gruppi selezionati continueranno a essere autorizzati a registrare i loro dispositivi Android for Work. A tutti gli altri utenti non è consentita la registrazione con Android for Work. |

In tutti i casi, viene mantenuto il regolamento previsto. Per mantenere l'autorizzazione globale o per i singoli gruppi di Android for Work nel proprio ambiente non è necessario eseguire alcuna operazione.

### <a name="google-play-protect-support-on-android----908720---"></a>Supporto di Google Play Protect in Android <!-- 908720 -->

Con il rilascio di Android Oreo, Google introduce un gruppo di funzionalità di sicurezza denominato Google Play Protect che consente a utenti e organizzazioni di eseguire app e immagini Android sicure. Intune ora supporta le funzionalità di Google Play Protect, inclusa l'attestazione remota SafetyNet. Gli amministratori possono impostare requisiti per i criteri di conformità che richiedono la configurazione e l'integrità di Google Play Protect.
L'**attestazione dispositivo SafetyNet** richiede che il dispositivo si connetta a un servizio Google per verificare che il dispositivo sia integro e non compromesso. Gli amministratori possono anche definire un'impostazione del profilo di configurazione per far sì che Android for Work richieda la verifica delle app installate da parte di Google Play Services. Se un dispositivo non è conforme ai requisiti di Google Play Protect, l'accesso condizionale può impedire agli utenti di accedere alle risorse aziendali.

- Informazioni su [come creare un criterio di conformità del dispositivo per abilitare Google Play Protect](compliance-policy-create-android.md).

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocollo di testo consentito dalle app gestite <!-- 1414050  -->

Le app gestite da Intune App SDK sono in grado di inviare messaggi SMS.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Report sull'installazione delle app aggiornato per includere lo stato Installazione in sospeso <!-- 1249446 -->  

Il report **Stato di installazione dell'app**, accessibile per ogni app attraverso l'elenco **App** nel carico di lavoro **App client** ora contiene il conteggio **L'installazione è in sospeso** per utenti e dispositivi.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API di inventario delle app iOS 11 per il rilevamento delle minacce per i dispositivi mobili <!-- 1391759 -->

Intune raccoglie le informazioni degli inventari delle app dei dispositivi personali e aziendali e le rende disponibili per i provider del servizio di rilevamento delle minacce per i dispositivi mobili (MTD, Mobile Threat Detection), ad esempio Lookout for Work. Si possono raccogliere gli inventari delle app dagli utenti di dispositivi iOS 11 e versioni successive.

**Inventario delle app**  
Gli inventari dei dispositivi aziendali e personali iOS 11 e versioni successive vengono inviati al provider del servizio MTD. I dati dell'inventario delle app includono:

- ID dell'app
- Versione dell'app
- Versione breve dell'app
- Nome dell'app
- Dimensione del bundle dell'app
- Dimensione dinamica dell'app
- Indicazione sulla convalida dell'app
- Indicazione sulla gestione dell'app

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Eseguire la migrazione di dispositivi e utenti dalla soluzione MDM ibrida alla versione autonoma di Intune <!-- 1463747 wnready -->
Sono ora disponibili nuovi strumenti e processi per lo spostamento di utenti e dei relativi dispositivi dalla soluzione MDM ibrida a Intune nel portale di Azure, che consentono di eseguire le attività seguenti:
- Copiare criteri e profili dalla console di Configuration Manager a Intune nel portale di Azure
- Spostare un sottoinsieme di utenti a Intune nel portale di Azure, mantenendo il resto nella soluzione MDM ibrida
- Eseguire la migrazione di dispositivi a Intune nel portale di Azure senza la necessità di registrarli nuovamente

Per informazioni dettagliate, vedere [Eseguire la migrazione di dispositivi e utenti dalla soluzione MDM ibrida alla versione autonoma di Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale  <!-- 676614 -->
Dopo che Exchange Connector crea una connessione a Exchange usando il CAS specificato, il connettore è ora in grado di individuare altri CAS. Se il CAS principale diventa non disponibile, il connettore eseguirà il failover a un altro CAS, se disponibile, fino a quando non diventa disponibile il CAS principale. Per altri dettagli, vedere [Supporto a disponibilità elevata di Exchange Connector locale](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Riavvio remoto del dispositivo iOS (solo supervisionato) <!-- 1424595 -->

È ora possibile riavviare un dispositivo iOS 10.3 e versioni successive supervisionato usando un'azione del dispositivo. Per altre informazioni sull'uso dell'azione di riavvio del dispositivo, vedere [Riavviare i dispositivi in remoto con Intune](device-restart.md).

> [!Note]
> Per eseguire questo comando sono necessari un dispositivo supervisionato e il diritto di accesso **Device Lock** (Blocco dispositivo). Il dispositivo viene riavviato immediatamente. I dispositivi iOS bloccati con passcode non si ricollegano a una rete Wi-Fi dopo il riavvio. È possibile che dopo il riavvio non siano in grado di comunicare con il server.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Supporto Single Sign-On per iOS <!-- 1333645 -->  

È possibile usare Single Sign-On per gli utenti iOS. Le app iOS codificate per la ricerca delle credenziali dell'utente nel payload Single Sign-on funzionano con questo aggiornamento della configurazione del payload. È anche possibile usare l'UPN e l'ID dispositivo di Intune per configurare il nome dell'entità e l'area di autenticazione. Per informazioni dettagliate, vedere [Configurare Intune per l'accesso Single Sign-On al dispositivo iOS](sso-ios.md).

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Aggiungere "Trova il mio iPhone" per i dispositivi personali <!--1427287-->
È ora possibile verificare se i dispositivi iOS hanno il Blocco attivazione attivato. Questa funzionalità era disponibile in precedenza nel portale classico di Intune.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloccare in remoto un dispositivo macOS gestito con Intune <!-- 1437691 -->

È possibile bloccare un dispositivo macOS smarrito e impostare un PIN di ripristino di 6 cifre. Quando il dispositivo è bloccato, il pannello **Device overview** (Panoramica dispositivo) visualizza il PIN fino a quando non viene inviata un'altra azione del dispositivo.

Per altre informazioni, vedere [Bloccare in remoto i dispositivi gestiti con Intune](device-remote-lock.md).

### <a name="new-scep-profile-details-supported----1559808---"></a>Nuovi dettagli del profilo SCEP supportati <!-- 1559808 -->

Gli amministratori ora possono configurare impostazioni aggiuntive durante la creazione di un profilo SCEP nelle piattaforme Windows, iOS, macOS e Android.  Gli amministratori possono impostare IMEI, numero di serie o nome comune, inclusa la posta elettronica nel formato del nome soggetto.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>Mantenere i dati durante il ripristino delle impostazioni predefinite  <!--1588489 -->
Quando si reimposta Windows 10 versione 1709 e successive ripristinando le impostazioni predefinite, è disponibile una nuova funzionalità. Gli amministratori possono specificare se la registrazione del dispositivo e altri dati di provisioning vengono mantenuti nel dispositivo quando viene eseguito il ripristino delle impostazioni predefinite.

Quando viene eseguito il ripristino delle impostazioni predefinite vengono mantenuti i dati seguenti:
- Account utente associati al dispositivo
- Stato del computer (aggiunto a un dominio, aggiunto ad Azure Active Directory)
- Registrazione MDM
- App installate OEM (app dello Store e Win32)
- Profilo utente
- Dati utente esterni al profilo utente
- Accesso automatico dell'utente

I dati seguenti non vengono mantenuti:
- File dell'utente
- App installate dell'utente (app dello Store e Win32)
- Impostazioni del dispositivo non predefinite


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Assegnazioni degli anelli di aggiornamento di Windows 10 visualizzate <!-- 1621837 -->
Durante la **Risoluzione dei problemi** per l'utente visualizzato le assegnazioni degli anelli di aggiornamento di Windows 10 sono visibili.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Impostazioni della frequenza di creazione di report di Windows Defender Advanced Threat Protection  <!-- 1455974  -->
Il servizio Windows Defender Advanced Threat Protection (WDATP) consente agli amministratori di gestire la frequenza di creazione di report per i dispositivi gestiti. Con la nuova opzione **Accelera la frequenza di creazione di report di telemetria**, WDATP raccoglie i dati e valuta i rischi con maggior frequenza. L'impostazione predefinita per la creazione di report ottimizza velocità e prestazioni. L'aumento della frequenza di creazione di report può essere utile per i dispositivi a rischio elevato. Questa impostazione è disponibile nel profilo **Windows Defender ATP** in **Configurazioni dispositivi**.

### <a name="audit-updates----1412961---"></a>Aggiornamenti dei controlli <!-- 1412961 -->  
La funzione di controllo di Intune offre un record delle operazioni di modifica correlate a Intune.  Tutte le operazioni di creazione, aggiornamento ed eliminazione e le attività remote vengono acquisite e mantenute per un anno.  Il portale di Azure offre una visualizzazione degli ultimi 30 giorni dei dati di controllo di ogni carico di lavoro a cui è possibile applicare filtri.  Un'API Graph corrispondente consente il recupero dei dati di controllo archiviati dell'ultimo anno.

La funzione di controllo è disponibile nel gruppo **MONITOR**. Viene visualizzata una voce di menu **Log di controllo** per ogni carico di lavoro.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>L'app Portale aziendale per macOS è ora disponibile <!--1541700-->
L'app Portale aziendale Intune in macOS offre una nuova esperienza utente, ottimizzata in modo da visualizzare correttamente tutte le informazioni e le notifiche di conformità necessarie agli utenti in relazione a tutti i dispositivi che hanno registrato. Dopo aver distribuito l'app Portale aziendale Intune in un dispositivo, Microsoft AutoUpdate per macOS fornirà i necessari aggiornamenti. È possibile scaricare la nuova app Portale aziendale Intune per macOS accedendo al sito Web dell'app Portale aziendale Intune da un dispositivo macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner è ora incluso nell'elenco di app approvate per la gestione delle app mobili  <!-- 1248473 -->
L'app Microsoft Planner per iOS e Android fa ora parte delle app approvate in base ai criteri di gestione delle app mobili. L'app può essere configurata tramite il pannello Protezione app di Intune nel portale di Azure di tutti i tenant.
- Altre informazioni sull'[elenco di app approvate per la gestione dei dispositivi mobili](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frequenza di aggiornamento dei requisiti di VPN per app nei dispositivi iOS   <!-- 1547061 -->  
Gli amministratori possono ora rimuovere i requisiti di VPN per app relativi alle app installate in dispositivi iOS; i dispositivi interessati verranno aggiornati dopo la successiva archiviazione di Intune, che si verifica in genere entro 15 minuti.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Supporto per Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->
È ora disponibile il Management Pack di System Center Operations Manager per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questa funzionalità consente di eseguire il monitoraggio del servizio in diversi modi quando è necessario risolvere un problema.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Co-gestione per dispositivi Windows 10  <!-- 1243445 -->
La co-gestione è una soluzione che rappresenta un ponte tra la gestione tradizionale e quella moderna e consente di effettuare la transizione con un approccio graduale. La co-gestione è fondamentalmente una soluzione in cui i dispositivi Windows 10 vengono gestiti contemporaneamente da Configuration Manager e Microsoft Intune e aggiunti ad Active Directory (AD) e Azure Active Directory (Azure AD).  Questa configurazione offre la possibilità di effettuare una modernizzazione graduale con un ritmo adatto alla propria organizzazione nei casi in cui una transizione immediata non è possibile.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Limitare la registrazione di Windows specificando la versione del sistema operativo <!-- 245498 -->
L'amministratore di Intune può ora specificare una versione minima e massima di Windows 10 per le registrazioni dei dispositivi. È possibile impostare queste limitazioni nel pannello **Configurazioni della piattaforma**.

Intune supporta ancora la registrazione di PC e telefoni Windows 8.1. È però possibile impostare solo le versioni di Windows 10 con limiti minimi e massimi. Per consentire la registrazione di dispositivi 8.1, non specificare il limite minimo.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Avvisi per dispositivi non assegnati Windows AutoPilot  <!-- 1631236 -->
Nella pagina **Microsoft Intune** > **Registrazione del dispositivo** > **Panoramica** è disponibile un nuovo avviso per dispositivi non assegnati Windows AutoPilot. In questo avviso viene specificato il numero di dispositivi del programma AutoPilot che non hanno profili di AutoPilot Deployment assegnati. Usare le informazioni contenute nell'avviso per creare i profili e assegnarli ai dispositivi non assegnati. Selezionando l'avviso, verrà visualizzato un elenco completo di dispositivi Windows AutoPilot e le relative informazioni dettagliate. Per altre informazioni, vedere [Registrare dispositivi Windows con il programma Windows AutoPilot Deployment](enrollment-autopilot.md).


### <a name="refresh-button-for-devices-list-------1333581---"></a>Pulsante Aggiorna per l'elenco di dispositivi    <!-- 1333581 -->
Poiché l'elenco dei dispositivi non viene aggiornato automaticamente, è possibile usare il nuovo pulsante Aggiorna per aggiornare i dispositivi contenuti nell'elenco.

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Supporto dell'autorità di certificazione Symantec Cloud  <!-- 1333638 -->    
Intune supporta ora la CA Symantec Cloud, che consente al Connettore di certificati di Intune di rilasciare certificati PKCS dalla CA Symantec Cloud a dispositivi gestiti Intune. Se si usa già il Connettore di certificati di Intune con l'autorità di certificazione (CA) Microsoft, è possibile usare la configurazione esistente del Connettore di certificati di Intune per aggiungere il supporto della CA Symantec.

### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nuovi elementi aggiunti all'inventario dei dispositivi   <!--1404455 -->
I nuovi elementi sono ora disponibili nell'[inventario dei dispositivi registrati](device-inventory.md):

- Indirizzo MAC Wi-Fi
- Spazio di archiviazione totale
- Spazio disponibile totale
- MEID
- Gestore telefonico del sottoscrittore

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Impostare l'accesso per le app mediante una patch di protezione Android minima nel dispositivo<!-- 1278463 -->   
L'amministratore può definire la patch di protezione Android minima che deve essere installata nel dispositivo per poter accedere a un'applicazione gestita in un account gestito.

> [!Note]  
> Questa funzionalità limita solo le patch di protezione rilasciate da Google nei dispositivi Android 6.0 e versioni successive.

### <a name="app-conditional-launch-support----1193313---"></a>Supporto di avvio condizionale all'app <!-- 1193313 -->
Gli amministratori IT possono ora impostare un requisito usando il portale di amministrazione di Azure per applicare un passcode anziché un PIN numerico PIN attraverso la gestione delle applicazioni mobili (MAM) all'avvio dell'applicazione. Se il requisito viene configurato, all'utente viene richiesto di impostare e usare un passcode prima di accedere alle applicazioni con supporto MAM. Un passcode è un PIN numerico con almeno un carattere speciale o una lettera maiuscola o minuscola. In questa versione di Intune la funzione è abilitata **solo in iOS**. Il supporto di Intune per i passcode è simile a quello dei PIN numerici: viene impostata una lunghezza minima e sono consentiti caratteri e sequenze ripetuti. Questa funzionalità richiede il supporto delle applicazioni (ovvero di WXP, Outlook, Managed Browser, Yammer) per l'integrazione di Intune App SDK con il codice della funzionalità stessa, in modo che le impostazioni di passcode possano essere applicate nelle applicazioni di destinazione.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Numero di versione delle app line-of-business nel report sullo stato dell'installazione del dispositivo <!-- 1233999 -->
In questa versione il report sullo stato dell'installazione del dispositivo visualizza il numero di versione dell'app per le app line-of-business per iOS e Android. Queste informazioni possono essere usate per la risoluzioni dei problemi delle app o per individuare i dispositivi che eseguono versioni delle app non aggiornate.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Gli amministratori possono ora configurare le impostazioni del firewall in un dispositivo usando un profilo di configurazione del dispositivo <!-- 951708 -->   
Gli amministratori possono attivare il firewall per i dispositivi e anche configurare diversi protocolli per le reti di dominio, private e pubbliche.  Le impostazioni del firewall sono disponibili nel profilo "Endpoint Protection".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard consente di proteggere i dispositivi dai siti Web non attendibili specificati dall'organizzazione <!-- 958257 -->   
Gli amministratori possono definire i siti come "attendibili" o "aziendali" usando un flusso di lavoro Windows Information Protection o il nuovo profilo "limite di rete" disponibile nelle configurazioni del dispositivo. I siti non elencati nel limite di rete attendibile del dispositivo Windows 10 a 64 bit e visualizzati con Microsoft Edge vengono invece aperti in un browser all'interno di un computer virtuale Hyper-V.

Application Guard è disponibile nei profili di configurazione del dispositivo, nel profilo "Endpoint Protection". Nel profilo gli amministratori possono configurare l'iterazione tra il browser virtualizzato e il computer host, i siti non attendibili e i siti attendibili e l'archiviazione dei dati nel browser virtualizzato. Per usare Application Guard in un dispositivo, è necessario innanzitutto configurare un limite di rete. È importante definire un solo limite di rete per dispositivo.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Il controllo delle applicazioni di Windows Defender in Windows 10 Enterprise consente di considerare attendibili solo le app autorizzate <!-- 1031096 -->    
Considerate le migliaia di nuovi file dannosi creati ogni giorno, l'uso di un sistema di rilevamento antivirus basato su firma per la protezione da software dannoso potrebbe non offrire più una difesa adeguata dai nuovi attacchi. Con il controllo delle applicazioni di Windows Defender in Windows 10 Enterprise è possibile modificare la configurazione del dispositivo passando da una modalità in cui vengono considerate attendibili tutte le app a eccezione di quelle bloccate da un antivirus o da un'altra soluzione di sicurezza a una modalità in cui il sistema operativo considera attendibili solo le app autorizzate dalla propria organizzazione. È possibile impostare le app come attendibili nel controllo delle applicazioni di Windows Defender.

Usando Intune è possibile configurare i criteri di controllo delle applicazioni in modalità "solo controllo" o in modalità di imposizione. In modalità "solo controllo" le app non vengono bloccate. La modalità "solo controllo" registra tutti gli eventi nei log del client locali. È anche possibile specificare se autorizzare l'esecuzione solo dei componenti Windows e delle app di Microsoft Store o anche quella di altre app affidabili in base a quanto definito da Intelligent Security Graph.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender Exploit Guard è un nuovo set di funzionalità di prevenzione intrusioni per Windows 10 <!-- 1063615 -->   
Windows Defender Exploit Guard include regole personalizzate per ridurre la vulnerabilità agli exploit delle applicazioni, evitare le minacce di macro e script, blocca automaticamente le connessioni di rete verso indirizzi IP con reputazione negativa ed è in grado di proteggere i dati da ransomware e minacce sconosciute. Windows Defender Exploit Guard include i componenti seguenti:

- La **Riduzione della superficie di attacco** offre regole che consentono di evitare le minacce di macro, script e posta elettronica.
- L'**Accesso controllato alle cartelle** blocca automaticamente l'accesso al contenuto delle cartelle protette.
- Il **filtro di rete** blocca la connessione in uscita di tutte le app verso indirizzi IP o domini con reputazione negativa
- La **protezione dagli exploit** offre limitazioni di memoria, flusso di controllo e criteri che è possibile usare per proteggere un'applicazione dagli exploit.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gestire gli script di PowerShell in Intune per i dispositivi Windows 10 <!-- 790537 -->

L'estensione di gestione di Intune consente di caricare script di PowerShell in Intune da eseguire in dispositivi Windows 10. L'estensione integra le funzionalità di gestione di dispositivi mobili (MDM, Mobile Device Management) di Windows 10 e rende più semplice il passaggio a una gestione moderna. Per informazioni dettagliate, vedere [Gestire gli script di PowerShell in Intune per i dispositivi Windows 10](intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nuove impostazioni per le restrizioni dei dispositivi per Windows 10      <!-- 1308850 -->
- Messaggistica (solo dispositivi mobili): disabilitare il test o i messaggi MMS
- Password: impostazioni per l'abilitazione di FIPS e l'uso dei dispositivi secondari Windows Hello per l'autenticazione 
- Visualizzazione: impostazioni per attivare o disattivare il ridimensionamento del programma GDI per le app legacy

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Limitazioni del dispositivo per la modalità tutto schermo per Windows 10 <!-- 1308872 -->   
È possibile impostare una limitazione per la modalità tutto schermo per gli utenti dei dispositivi Windows 10 che limita gli utenti a un set di app predefinite.  A tale scopo, creare un profilo di limitazione del dispositivo Windows 10 e specificare le impostazioni della modalità a tutto schermo.

La modalità a tutto schermo supporta due modalità: la modalità **applicazione singola** che consente all'utente di eseguire una sola app e la modalità **app multiple** che consente l'accesso a più app.  Definire l'account utente e il nome del dispositivo che determinano le app supportate.  Dopo aver eseguito l'accesso, l'utente sarà limitato alle app definite.  Per altre informazioni, vedere [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (Provider del servizio di configurazione AssignedAccess). 

Per la modalità a tutto schermo sono necessari i requisiti seguenti:

- Intune deve essere l'autorità MDM.
- Le app devono essere già installate nel dispositivo di destinazione.
- Il [provisioning](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions) del dispositivo deve essere stato eseguito correttamente.

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuovo profilo di configurazione del dispositivo per la creazione di limiti di rete <!-- 1311967 -->   
Un nuovo profilo di configurazione del dispositivo denominato **Limite di rete** è disponibile con gli altri profili di configurazione. Usare questo profilo per definire le risorse online da considerare aziendali e affidabili. È necessario definire un limite di rete per un dispositivo *prima* di usare funzionalità come Windows Defender Application Guard e Windows Information Protection nel dispositivo. È importante definire un solo limite di rete per dispositivo.

È possibile definire le risorse cloud aziendali, gli intervalli di indirizzi IP e i server proxy interni da considerare attendibili. Il limite di rete definito può essere utilizzato da altre funzionalità, ad esempio Windows Defender Application Guard e Windows Information Protection.

### <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Due impostazioni aggiuntive per Windows Defender Antivirus <!-- 1338409 -->  
**Livello di blocco di file**

| | |
|---|---|
| Non configurato | **Non configurato** usa il livello di blocco predefinito di Windows Defender Antivirus e offre un rilevamento sicuro senza aumentare il rischio di rilevare file legittimi. |
| Alta | **Alto** applica un livello di rilevamento elevato.
| Elevato +  | **Elevato +** offre il livello Alto con misure di protezione aggiuntive che potrebbero influire sulle prestazioni del client.
| Tolleranza zero  | **Tolleranza zero** blocca tutti gli eseguibili sconosciuti. |

Sebbene sia improbabile, l'impostazione su **Alto** potrebbe causare il rilevamento di file legittimi.
È consigliabile impostare il livello di blocco di file sul valore predefinito **Non configurato**.

**Estensione del timeout per l'analisi dei file dal cloud**  

| | |
|--|--|
| Numero di secondi (0-50) | Specificare la quantità massima di tempo per la quale Windows Defender Antivirus deve bloccare un file in attesa di un risultato dal cloud. La quantità predefinita è 10 secondi: il tempo specificato con questa opzione (fino a un massimo di 50 secondi) viene aggiunto ai 10 secondi. Nella maggior parte dei casi l'analisi richiede molto meno tempo rispetto al tempo massimo. L'estensione della quantità di tempo consente al cloud di analizzare nel dettaglio i file sospetti. È consigliabile abilitare questa impostazione e specificare almeno 20 secondi aggiuntivi. |

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix aggiunta per i dispositivi Windows 10 <!-- 1512457 -->  
È possibile configurare la VPN Citrix per i dispositivi Windows 10. Durante la configurazione di una VPN per Windows 10 e versioni successive è possibile scegliere la VPN Citrix nell'elenco *Selezionare un tipo di connessione* nel pannello **VPN di base**.

> [!Note]
> Configurazione Citrix per iOS e Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Chiavi precondivise supportate da connessioni Wi-Fi in iOS <!-- 1550823 -->
Per usare le chiavi precondivise per le connessioni WPA/WPA2-Personal in dispositivi iOS, è possibile configurare profili Wi-Fi. Questi profili vengono inviati al dispositivo dell'utente quando il dispositivo viene registrato in Intune.

Dopo che il profilo è stato inviato al dispositivo, il passaggio successivo cambia a seconda della configurazione del profilo.  Se è impostato per connettersi automaticamente, la connessione viene eseguita automaticamente quando viene richiesta la rete.  Se il profilo si connette manualmente, la connessione deve essere attivata manualmente dall'utente.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Accesso ai log di app gestite per iOS <!-- 1469920 -->
Gli utenti finali che hanno installato Managed Browser possono ora visualizzare lo stato di gestione di tutte le app pubblicate Microsoft e inviare i log per la risoluzione dei problemi delle app iOS gestite.

Per altre informazioni su come abilitare la modalità di risoluzione dei problemi in Managed Browser in un dispositivo iOS, vedere [How to access to managed app logs using the Managed Browser on iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios) (Come accedere a log di app gestite tramite Managed Browser in iOS).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Miglioramenti al flusso di lavoro di configurazione dei dispositivi in Portale aziendale per iOS (versione 2.9.0) <!-- 1417174 -->

Il flusso di lavoro di configurazione dei dispositivi nell'app Portale aziendale per iOS è stato migliorato. Il linguaggio è più semplice e, dove possibile, sono state inserite schermate. Con l'inserimento del nome della società nel testo di configurazione, il linguaggio è più specifico per la società di riferimento. È possibile visualizzare il flusso di lavoro aggiornato nella pagina sulle  [novità nell'interfaccia utente delle app](whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>L'entità User contiene i dati utente più recenti nel modello di dati del data warehouse <!-- 1544273 -->
La prima versione del modello di dati del data Warehouse di Intune contiene solo i dati storici e recenti di Intune. Durante la creazione di report non è possibile acquisire lo stato corrente di un utente. In questo aggiornamento l'**entità User** viene popolata con i dati utente più recenti.

<!-- ########################## -->
## <a name="october-2017"></a>Ottobre 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>Il numero di versione delle app line-of-business iOS e Android è visibile <!-- 1380712 -->

Nelle app in Intune viene ora visualizzato il numero di versione per le app line-of-business iOS e Android. Il numero viene visualizzato nel portale di Azure nell'elenco delle app e nel pannello della panoramica dell'app. Gli utenti finali possono visualizzare il numero dell'app nell'app Portale aziendale e nel portale Web.

__Numero di versione completo__ Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800)

Il numero di versione completo include due componenti:

- **Versione**  
  Il numero di versione è il numero di versione leggibile dell'app. Viene usato dagli utenti finali per identificare diverse versioni dell'app.

- **Numero di build**  
  Il numero di build è un numero interno che può essere usato nel rilevamento delle app e per gestire l'app a livello di codice. Il numero di build si riferisce a un'iterazione dell'app che fa riferimento alle modifiche nel codice.

Per altre informazioni sui numeri di versione e lo sviluppo di app line-of-business, vedere [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integrazione della gestione delle applicazioni e dei dispositivi <!-- 677972 -->   
Ora che la gestione di dispositivi mobili (MDM) e la gestione di applicazioni mobili (MAM) di Intune sono entrambe accessibili dal portale di Azure, in Intune è stata iniziata l'integrazione dell'esperienza di amministrazione IT nella gestione delle applicazioni e dei dispositivi. Queste modifiche hanno lo scopo di rendere più semplice l'esperienza di gestione dei dispositivi e delle app.

Per altre informazioni sulle modifiche MDM e MAM annunciate, vedere il [blog del team di supporto di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nuovi avvisi di registrazione per i dispositivi Apple <!-- 1471790 -->
Nella pagina di panoramica per la registrazione verranno visualizzati avvisi utili per gli amministratori IT riguardanti la gestione dei dispositivi Apple. Gli avvisi verranno visualizzati nella pagina Panoramica quando il certificato per le notifiche push MDM Apple sta per scadere o è già scaduto, quando il token di Device Enrollment Program sta per scadere o è già scaduto e quando vi sono dispositivi non assegnati in Device Enrollment Program.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Sostituzione dei token di supporto per la configurazione di app senza registrazione del dispositivo <!-- 1080364 -->

È possibile usare i token per i valori dinamici nelle configurazioni di app per le app nei dispositivi che non sono registrati. Per altre informazioni, vedere [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md) (Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Aggiornamenti all'app Portale aziendale per Windows 10 <!--1299474-->
La pagina Impostazioni dell'app Portale aziendale per Windows 10 è stata aggiornata in modo da rendere più coerenti le impostazioni e le azioni previste dall'utente sui vari tipi di impostazioni. Ne è stato aggiornato anche il layout per uniformarlo a quello delle altre app Windows. È possibile trovare le immagini "Prima/Dopo" nella pagina sulle [novità nell'interfaccia utente delle app](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Comunicare agli utenti finali quali informazioni possono essere visualizzate per i dispositivi Windows 10 <!--1337920-->
È stata aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo nell'app Portale aziendale per Windows 10. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente da questa pagina dalla documentazione di Intune per gli utenti finali. Potranno accedere a queste informazioni anche dalla schermata **Informazioni**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Richiesta di commenti e suggerimenti per l'app Portale aziendale per Android <!--1165249-->
L'app Portale aziendale per Android richiede ora commenti e suggerimenti da parte degli utenti finali. I commenti vengono inviati direttamente a Microsoft e offrono agli utenti finali la possibilità di valutare l'app nello store pubblico Google Play. L'invio di commenti e suggerimenti non è comunque obbligatorio e può essere facilmente ignorato per continuare a usare regolarmente l'app.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Consentire agli utenti di usare l'app Portale aziendale per Android <!-- 1573324, 1573150, 1558616, 1564878 -->

L'app Portale aziendale per Android include ora istruzioni per gli utenti finali per consentire di comprendere e, dove possibile, risolvere autonomamente nuovi casi d'uso.
- Gli utenti finali verranno indirizzati al [portale di Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) per rimuovere un dispositivo se è stato raggiunto il numero massimo di dispositivi che sono autorizzati ad aggiungere.
- Agli utenti finali verranno indicati i passaggi da eseguire per [correggere gli errori di attivazione sui dispositivi Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) o per [disattivare la modalità di risparmio energia](/intune-user-help/power-saving-mode-android). Se nessuna delle soluzioni proposte corregge il problema, verrà descritto come [inviare i log a Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nuova azione 'Risolvi' disponibile per i dispositivi Android <!-- 1583480 -->

L'app del portale aziendale per Android include ora una nuova azione 'Risolvi' nella pagina _Aggiorna impostazioni del dispositivo_. La selezione di questa opzione indirizza l'utente finale direttamente all'impostazione che rende il dispositivo non conforme. L'app del portale aziendale per Android supporta attualmente questa opzione per le impostazioni di [passcode del dispositivo](/intune-user-help/set-your-pin-or-password-android), [debug USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [origini sconosciute](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicatore dello stato di avanzamento della configurazione del dispositivo nel Portale aziendale per Android <!-- 1565657 -->
Quando un utente registra un dispositivo, nell'app Portale aziendale per Android viene visualizzato un indicatore dello stato di avanzamento del processo di configurazione del dispositivo. L'indicatore elenca i nuovi stati nell'ordine seguente: "Configurazione del dispositivo...", "Registrazione del dispositivo...", "Completamento della registrazione del dispositivo..." e "Completamento della configurazione del dispositivo...".

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Supporto dell'autenticazione basata sui certificati nel Portale aziendale per iOS <!--1029830-->
È stato aggiunto il supporto dell'autenticazione basata sui certificati (CBA) nell'app del portale aziendale per iOS. Gli utenti con autenticazione basata sui certificati immettono il nome utente e quindi toccano il collegamento "Sign in with a certificate" (Accedi con un certificato). L'autenticazione basata sui certificati è già supportata nelle app del portale aziendale per Android e Windows. Altre informazioni sono disponibili nella pagina di [accesso all'app del portale aziendale](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Le app disponibili con o senza registrazione possono essere ora installate senza richiesta di registrazione. <!-- 1334712 -->

Le app aziendali rese disponibili con o senza registrazione nell'app Portale aziendale Android possono essere ora installate senza richiesta di registrazione.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Supporto del programma Windows AutoPilot Deployment in Microsoft Intune  <!-- 747617  -->
Ora è possibile usare Microsoft Intune con il programma AutoPilot Deployment di Windows per consentire agli utenti di attivare e gestire i dispositivi aziendali senza interventi del personale IT. È possibile personalizzare la Configurazione guidata con informazioni che consentono agli utenti di aggiungere il dispositivo ad Azure AD e di registrarlo in Intune. Microsoft Intune e AutoPilot di Windows eseguiti insieme eliminano la necessità di distribuire, gestire e aggiornare le immagini del sistema operativo. Per informazioni dettagliate, vedere [Enroll Windows devices using Windows AutoPilot Deployment Program](enrollment-autopilot.md) (Registrare dispositivi Windows con il programma AutoPilot Deployment).

### <a name="quickstart-for-device-enrollment-----1425655---"></a>Avvio rapido per la registrazione del dispositivo  <!-- 1425655 --> 
In **Registrazione del dispositivo** ora è disponibile una sezione di avvio rapido che include una tabella di riferimenti per la gestione delle piattaforme e la configurazione del processo di registrazione. L'esecuzione delle fasi iniziali della registrazione è facilitata mediante una breve descrizione di ciascun elemento e collegamenti ad argomenti di documentazione con procedure dettagliate.

### <a name="device-categorization----1427491---"></a>Categorizzazione dei dispositivi <!-- 1427491 -->
Il grafico della piattaforma dei dispositivi registrati nella scheda **Dispositivi > Panoramica** organizza i dispositivi per piattaforma e include Android, iOS, macOS, Windows e Windows Mobile.  I dispositivi che eseguono altri sistemi operativi vengono inclusi in "Altro".  Questa categoria include i dispositivi prodotti da Blackberry, NOKIA e altri produttori.  

Per informazioni sui dispositivi interessati nel tenant, scegliere **Gestisci > Tutti i dispositivi** e quindi usare **Filtra** per limitare il campo **Sistema operativo**.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuovo partner di Mobile Threat Defense   <!-- 954681 -->  
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi eseguita da Zimperium, una soluzione Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Zimperium. È possibile configurare criteri di accesso condizionale EMS in base alla valutazione dei rischi di Zimperium abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10  <!--- 978575, 1308849, -->  
Sono state aggiunte nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 nella categoria Windows Defender SmartScreen.

Per informazioni dettagliate sul profilo di restrizione dei dispositivi Windows 10, vedere [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Supporto remoto per dispositivi Windows e Windows Mobile   <!-- 1070473 -->  
Intune ora supporta l'uso del software [TeamViewer](https://www.teamviewer.com), acquistabile separatamente, per l'assistenza remota agli utenti con dispositivi Windows e Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analizzare dispositivi con Windows Defender <!-- 1280988  1280990   -->
Ora è possibile eseguire un'**analisi veloce**, un'**analisi completa** e l'**aggiornamento delle firme** con Windows Defender Antivirus nei dispositivi Windows 10 gestiti. Dal pannello della panoramica del dispositivo, scegliere l'azione da eseguire nel dispositivo. Verrà chiesto di confermare l'azione prima che il comando venga inviato al dispositivo. 

**Analisi veloce**: l'analisi veloce analizza i percorsi in cui il malware si registra per l'avvio, ad esempio le chiavi del Registro di sistema e le cartelle di avvio di Windows note. L'analisi veloce richiede in media cinque minuti. Unita all'impostazione della **protezione in tempo reale Always On** che analizza i file quando vengono aperti, chiusi e ogni volta che un utente passa a una cartella, l'analisi veloce consente di fornire protezione da software dannoso che potrebbe trovarsi nel sistema o nel kernel. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Analisi completa**: l'analisi completa può essere utile nei dispositivi in cui sono state riscontrate minacce malware per identificare se sono presenti componenti inattivi che richiedono una pulizia più approfondita ed è utile per l'esecuzione di analisi su richiesta. L'analisi completa può richiedere un'ora. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Aggiornare le firme**: il comando di aggiornamento delle firme aggiorna le definizioni e le firme malware di Windows Defender Antivirus, garantendo l'efficacia nel rilevamento di malware. Questa funzionalità è applicabile solo ai dispositivi Windows 10 con connettività Internet. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Il pulsante Abilita/Disabilita viene rimosso dalla pagina Autorità di certificazione nel portale di Azure di Intune  <!-- 1400455 -->
 È stato eliminato un passaggio aggiuntivo nella configurazione del Connettore di certificati di Intune. Attualmente è necessario scaricare il Connettore di certificati e quindi abilitarlo nella console di Intune. Se tuttavia si disattiva il connettore nella console di Intune, questo continua a emettere certificati.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
A partire da ottobre, il pulsante Abilita/Disabilita non viene più visualizzato nella pagina Autorità di certificazione del portale di Azure. La funzionalità del connettore resta invariata. I certificati vengono ancora distribuiti ai dispositivi registrati in Intune. È possibile continuare a scaricare e installare il Connettore di certificati. Per interrompere l'emissione di certificati ora è necessario disinstallare il Connettore di certificati anziché disattivarlo.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Se il Connettore di certificati è disattivato, è necessario disinstallarlo.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team   <!--- 1308838 -->
In questa versione vengono aggiunte molte nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team per la gestione dei dispositivi Surface Hub.

Per altre informazioni su questo profilo, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedire agli utenti dei dispositivi Android di modificare data e ora del dispositivo  <!-- 1333292 -->
È possibile usare [criteri personalizzati per dispositivi Android](custom-settings-android.md) per impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo.

A tale scopo, configurare criteri personalizzati di Android impostando l'URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange su **TRUE** e quindi assegnarli ai gruppi necessari.

### <a name="bitlocker-device-configuration----1397398---"></a>Configurazione di BitLocker nel dispositivo <!-- 1397398 -->
**Crittografia di Windows > Impostazioni di base** include la nuova impostazione **Avviso per la crittografia dischi di altro tipo** che consente di disabilitare il [prompt di avviso](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption) per crittografie dischi di altro tipo eventualmente in uso nel dispositivo dell'utente.  Il prompt di avviso richiede il consenso dell'utente finale prima di configurare BitLocker nel dispositivo e blocca la configurazione di BitLocker fino alla conferma dell'utente finale.  La nuova impostazione disabilita l'avviso per l'utente finale.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Le app Volume Purchase Program per le aziende ora vengono sincronizzate con il tenant Intune <!-- 800882 -->  
Gli sviluppatori di terze parti possono distribuire privatamente le app ai membri del Volume Purchase Program di Apple per le aziende indicati in iTunes Connect. I membri VPP per le aziende possono accedere a Volume Purchase Program App Store e acquistare le app.

A partire dalla versione corrente le app VPP per le aziende acquistate dall'utente finale vengono sincronizzate con il rispettivo tenant Intune.

### <a name="select-apple-countryregion-store-to-sync-vpp-apps-----1332311---"></a>Selezionare l'Apple Store del paese/dell'area per la sincronizzazione delle app VPP  <!-- 1332311 -->  
È possibile configurare lo Store del paese/dell'area per il Volume Purchase Program (VPP) quando si carica il token VPP. Intune sincronizza le app VPP per tutte le impostazioni locali dello Store VPP del paese/dell'area specificato.

> [!NOTE]  
> Attualmente Intune sincronizza solo le app VPP dello Store VPP del paese/dell'area corrispondenti alle impostazioni locali di Intune in cui è stato creato il tenant di Intune.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloccare la funzionalità di copia e incolla tra i profili di lavoro e i profili personali in Android for Work <!-- 1098994 -->
Con questa versione è possibile configurare il profilo di lavoro di Android for Work per bloccare l'operazione di copia e incolla tra le app di lavoro e le app personali. Questa nuova impostazione è disponibile nel profilo **Limitazioni del dispositivo** per la piattaforma **Android for Work** in **Impostazioni del profilo di lavoro**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creare app iOS limitate ad Apple App Store di aree specifiche <!-- 1281692 -->
Sarà possibile specificare le impostazioni locali del paese/dell'area durante la creazione di un'app gestita da Apple App Store.

> [!Note]  
> Attualmente è possibile creare solo app gestite di Apple App Store disponibili nello Store degli Stati Uniti.

### <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Aggiornare le app VPP iOS concesse in licenza a utenti e dispositivi  <!-- 1305564 -->  
Sarà possibile configurare il token VPP iOS per aggiornare tutte le app acquistate per tale token tramite il servizio Intune. Intune rileverà gli aggiornamenti delle app VPP nell'App Store e li invierà automaticamente al dispositivo quando questo si connette.

Per la descrizione dettagliata dell'impostazione di un token VPP e dell'attivazione degli aggiornamenti automatici, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune] (/intune/vpp-app-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Raccolta di entità di associazione dei dispositivi degli utenti aggiunta al modello di dati di Data Warehouse di Intune <!-- 1187917 -->
Ora è possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi. Il modello di dati è accessibile tramite il file di Power BI (PBIX) recuperato dalla pagina Data warehouse di Intune, tramite l'endpoint OData oppure sviluppando un client personalizzato.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Esaminare la conformità ai criteri per gli anelli di aggiornamento di Windows 10 <!-- 1067886 -->
È possibile esaminare un report sui criteri per gli anelli di aggiornamento di Windows 10 in Aggiornamenti software > Stato di distribuzione per ogni anello di aggiornamento. Il report sui criteri include lo stato di distribuzione degli anelli di aggiornamento configurati. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuovo report che elenca i dispositivi iOS con versioni precedenti di iOS   <!-- 1352223 -->
Il report **Dispositivi iOS non aggiornati** è disponibile nell'area di lavoro **Aggiornamenti software**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento di iOS e con aggiornamenti disponibili. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visualizzare le assegnazioni dei criteri di protezione delle app per la risoluzione dei problemi <!--  1475003 -->
In questa versione futura verrà aggiunta un'opzione per i **criteri di protezione delle app** all'elenco a discesa **Assegnazioni** disponibile nel pannello della risoluzione dei problemi. Sarà ora possibile selezionare Criteri di protezione delle app per visualizzare i criteri assegnati agli utenti selezionati.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Miglioramenti del flusso di lavoro di installazione dei dispositivi nel Portale aziendale <!--1490692-->
È stato migliorato il flusso di lavoro di installazione dei dispositivi nell'app Portale aziendale per Android. Il linguaggio è più semplice e specifico per l'azienda e sono state inserite schermate dove possibile. È possibile visualizzare i miglioramenti nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Miglioramento delle linee guida per la richiesta di accesso ai contatti nei dispositivi Android <!--1484985-->

L'app Portale aziendale per Android richiede spesso all'utente finale di accettare l'autorizzazione per i contatti. Se un utente finale rifiuta l'accesso, ora viene visualizzata una notifica in-app che avvisa dell'autorizzazione per l'accesso condizionale. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Correzione dell'avvio sicuro per Android <!--1490712-->

Gli utenti finali con dispositivi Android potranno selezionare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notifiche push aggiuntive per gli utenti finali dell'app Portale aziendale per Android Oreo <!--1475932-->

Gli utenti visualizzeranno notifiche aggiuntive che indicano quando l'app Portale aziendale per Android Oreo sta eseguendo attività in background, ad esempio il recupero di criteri dal servizio Intune. Questa funzionalità aumenta la trasparenza per gli utenti finali, che sapranno quando sono in corso attività amministrative del Portale aziendale nei loro dispositivi, È uno degli aspetti dell'intera [ottimizzazione dell'interfaccia utente del portale aziendale](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) per l'app Portale aziendale per Android Oreo. 

Sono disponibili altre ottimizzazioni per i nuovi elementi dell'interfaccia utente che sono abilitate in Android Oreo.  Gli utenti finali visualizzeranno notifiche aggiuntive che indicheranno loro quando l'app Portale aziendale sta eseguendo attività in background, ad esempio il recupero di criteri dal servizio di Intune.  In questo modo per gli utenti finali sarà più chiaro quando l'app Portale aziendale sta eseguendo attività amministrative nel dispositivo.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuovi comportamenti dell'app Portale aziendale per Android con i profili di lavoro <!-- 1485783 -->

Quando si registra un dispositivo Android for Work con un profilo di lavoro, è l'app del portale aziendale nel profilo di lavoro a eseguire attività di gestione nel dispositivo. 

A meno che non si usi un'app abilitata per MAM nel profilo personale, l'app del portale aziendale per Android non è più utile. Per migliorare l'esperienza con i profili di lavoro, Intune nasconderà automaticamente l'app del portale aziendale personale dopo la registrazione del profilo di lavoro.

L'app del portale aziendale per Android può essere abilitata in qualsiasi momento nel profilo personale passando al [portale aziendale in Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e selezionando **Abilita**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Passaggio dell'app Portale aziendale per Windows 8.1 e Windows Phone 8.1 alla modalità di solo supporto <!--1428681-->

A partire da ottobre 2017, le app del portale aziendale per Windows 8.1 e Windows Phone 8.1 passeranno alla modalità di mantenimento. Le app e gli scenari esistenti, ad esempio la registrazione e la conformità, continueranno a essere supportati per queste piattaforme. Queste app rimarranno disponibili per il download tramite i canali di rilascio esistenti, ad esempio Microsoft Store. 

Nella modalità di mantenimento, queste app ricevono solo aggiornamenti della sicurezza critici. Non verranno rilasciati altri aggiornamenti o funzionalità per queste app. Per le nuove funzionalità è consigliabile aggiornare i dispositivi a Windows 10 o Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Bloccare la registrazione di dispositivi Samsung Knox non supportati  <!-- 1490695 -->

L'app Portale aziendale tenta di registrare solo i dispositivi Samsung Knox supportati. Per evitare errori di attivazione Knox che impediscono la registrazione MDM, la registrazione del dispositivo viene eseguita solo se il dispositivo viene visualizzato nell'[elenco di dispositivi pubblicato da Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). I dispositivi Samsung possono avere numeri di modello che supportano Knox oppure no. Verificare la compatibilità Knox con il rivenditore del dispositivo prima dell'acquisto e della distribuzione. È possibile trovare l'elenco completo dei dispositivi verificati nelle [impostazioni dei criteri Android e Samsung Knox Standard](supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Fine del supporto per Android 4.3 e versioni precedenti <!-- 1171126, 1326920 -->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate nei dispositivi registrati <!--1165314-->
Verrà aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo in tutte le app Portale aziendale. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente dall'articolo [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Questa opzione verrà presto implementata in tutte le app Portale aziendale. Per iOS, l'annuncio è stato fatto a [settembre](#september-2017).

<!-- ########################## -->
## <a name="september-2017"></a>Settembre 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune supporta iOS 11 <!--1428975-->
Intune supporta iOS 11. Annuncio precedentemente fatto nel [blog del supporto tecnico di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fine del supporto per iOS 8.0 <!-- 1164477 -->
Le app gestite e l'app Portale aziendale per iOS richiederanno iOS 9.0 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati entro settembre non potranno accedere al Portale aziendale o a tali app. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Azione di aggiornamento aggiunta all'app Portale aziendale per Windows 10 <!--1132468-->
L'app Portale aziendale per Windows 10 consente agli utenti di aggiornare i dati nell'app trascinando verso il basso per aggiornare o, nei desktop, premendo F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate per iOS <!--739894-->

È stata aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo nell'app Portale aziendale per iOS. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente da questa pagina dalla documentazione di Intune per gli utenti finali. Potranno accedere a queste informazioni anche nella schermata Informazioni su.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Consentire agli utenti di accedere all'app Portale aziendale per Android senza registrazione <!---1169910--->

Gli utenti finali potranno presto non avere l'obbligo di registrare il dispositivo per accedere all'app Portale aziendale per Android. Agli utenti finali di organizzazioni che usano criteri di protezione delle app non verrà più richiesto di registrare il dispositivo quando aprono l'app Portale aziendale. Gli utenti finali potranno anche installare app dal Portale aziendale senza registrare il dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Testo più comprensibile per l'app Portale aziendale per Android <!---1396349--->  

Il processo di registrazione per l'app del portale aziendale per Android è ora più semplice per gli utenti finali, grazie all'uso di un nuovo testo più comprensibile. Se si usa una documentazione personalizzata per la registrazione, è consigliabile aggiornarla sulla base delle nuove schermate. È possibile trovare immagini di esempio nella pagina [Aggiornamenti dell'interfaccia utente per le app degli utenti finali in Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>App Portale aziendale di Windows 10 aggiunta ai criteri per il consenso di Windows Information Protection <!-- 677129 -->

L'app Portale aziendale di Windows 10 è stata aggiornata per supportare Windows Information Protection (WIP). L'app può essere aggiunta ai criteri Consenti di WIP. Con questa modifica non è più necessario aggiungere l'app all'elenco **Esente**.


<!-- ########################## -->
## <a name="august-2017"></a>Agosto 2017

### <a name="improvements-to-device-overview----1404453---"></a>Miglioramenti alla panoramica del dispositivo <!-- 1404453 -->  
In seguito ai miglioramenti, la panoramica del dispositivo ora visualizza i dispositivi registrati ma esclude i dispositivi gestiti da Exchange ActiveSync. I dispositivi Exchange ActiveSync non hanno le stesse opzioni di gestione dei dispositivi registrati. Per visualizzare il numero di dispositivi registrati e il numero di dispositivi registrati per piattaforma in Intune nel portale di Azure, scegliere **Dispositivi** > **Panoramica**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Miglioramenti dell'inventario dei dispositivi gestito da Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
In questa versione sono stati apportati i miglioramenti seguenti alle informazioni di inventario raccolte dai dispositivi gestiti dall'utente:
 
- Per i dispositivi Android ora è possibile aggiungere all'inventario dei dispositivi una colonna che mostra il livello di patch più recente per ogni dispositivo. Aggiungere la colonna **Security patch level** (Livello patch di protezione) all'elenco di dispositivi per visualizzare il risultato.
- Quando si applica un filtro alla visualizzazione dei dispositivi ora è possibile filtrare i dispositivi per data di registrazione. Ad esempio, è possibile visualizzare solo i dispositivi registrati dopo una data specificata.
- Sono stati apportati miglioramenti al filtro usato per l'elemento **Last Check-in Date** (Data ultima archiviazione).
- Nell'elenco dei dispositivi ora è possibile visualizzare il numero di telefono dei dispositivi di proprietà dell'azienda.
È inoltre possibile usare il riquadro del filtro per cercare i dispositivi in base al numero di telefono.

Per altri dettagli sull'inventario dei dispositivi, vedere [Come visualizzare l'inventario dei dispositivi di Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Supporto dell'accesso condizionale per dispositivi macOS 
<!-- 720172 -->
Ora è possibile impostare un criterio di accesso condizionale che richiede che i dispositivi Mac vengano registrati in Intune e siano conformi ai relativi criteri di conformità dei dispositivi. Ad esempio, gli utenti possono scaricare l'app Portale aziendale Intune per macOS e registrare i propri dispositivi Mac in Intune. Intune valuta se il dispositivo Mac è conforme a requisiti come PIN, crittografia, versione del sistema operativo e integrità del sistema.

- Altre informazioni sul [supporto dell'accesso condizionale per dispositivi macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>L'app Portale aziendale per macOS è disponibile in anteprima pubblica <!---1484796--->
L'app Portale aziendale per macOS è ora disponibile come parte dell'anteprima pubblica dell'accesso condizionale in Enterprise Mobility + Security. Questa versione supporta macOS 10.11 e versioni successive. È disponibile in [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nuove impostazioni per le restrizioni dei dispositivi per Windows 10    
<!--1063965, 1308850  -->
In questa versione sono state aggiunte nuove impostazioni per il [profilo di restrizione dei dispositivi Windows 10](/intune/device-restrictions-windows-10) nelle categorie seguenti:

- Windows Defender SmartScreen
- App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Aggiornamenti delle impostazioni del profilo dispositivo Endpoint Protection di Windows 10 per BitLocker
<!--1459533 -->    
In questa versione sono stati apportati i miglioramenti seguenti al funzionamento delle impostazioni BitLocker in un profilo di dispositivo Endpoint Protection di Windows 10:
 
- In **Impostazioni dell'unità del sistema operativo BitLocker** per l'impostazione **BitLocker con chip TPM non compatibile**, quando in precedenza si selezionava **Blocca** in realtà BitLocker veniva autorizzato. Questo problema è stato risolto e ora quando si seleziona questa opzione BitLocker viene bloccato.
- In **Impostazioni dell'unità del sistema operativo BitLocker**, per l'impostazione **Agente di recupero dati basato su certificati** ora è possibile bloccare in modo esplicito l'agente di recupero dati basato su certificati. Per impostazione predefinita l'agente è consentito.
- In **Impostazioni delle unità dati fisse BitLocker**, per l'impostazione **Agente di recupero dati** ora è possibile bloccare in modo esplicito l'agente di recupero dati.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nuova esperienza di accesso per gli utenti dell'app Portale aziendale per Android e gli utenti dei criteri di protezione delle app <!-- 621669 -->
Gli utenti finali possono ora esplorare le app, gestire i dispositivi e visualizzare le informazioni sul contatto IT tramite l'app Portale aziendale per Android senza registrare i dispositivi Android. Inoltre, se un utente finale usa già un'app protetta tramite i criteri di protezione app di Intune e avvia l'app Portale aziendale per Android, l'utente finale non riceve più la richiesta di registrare il dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nuova impostazione nell'app Portale aziendale per Android per attivare/disattivare l'ottimizzazione della batteria <!--1405990-->
La pagina **Impostazioni** nell'app Portale aziendale per Android include una nuova impostazione che consente agli utenti di disattivare facilmente l'ottimizzazione della batteria per le app Portale aziendale e Microsoft Authenticator. Il nome dell'app visualizzato nell'impostazione varia a seconda dell'app usata per gestire l'account aziendale. È consigliabile che gli utenti disattivino l'ottimizzazione della batteria per migliorare le prestazioni delle app aziendali che sincronizzano posta elettronica e dati. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Supporto di più identità per OneNote per iOS      <!-- 1234281 -->
Ora gli utenti finali possono usare account diversi (aziendali e personali) con Microsoft OneNote per iOS. I criteri di protezione app possono essere applicati ai dati aziendali nei notebook di lavoro senza influire sul notebook personale dell'utente. Ad esempio un criterio può consentire a un utente di trovare informazioni nei notebook aziendali, ma impedirà all'utente di copiare e incollare dati aziendali dal notebook aziendale a un notebook personale.
 
- Altre informazioni sulle app che supportano la [protezione delle app e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nuove impostazioni per consentire e bloccare app nei dispositivi Samsung Knox Standard
<!-- 1305423 822899-->  
In questa versione vengono aggiunte nuove [impostazioni di restrizione dei dispositivi](device-restrictions-android.md) che consentono di specificare gli elenchi di app seguenti:
 
- App che gli utenti sono autorizzati a installare
- App che gli utenti non possono eseguire
- App che sono nascoste all'utente nel dispositivo
 
È possibile specificare l'app in base all'URL, al nome del pacchetto o dall'elenco di app che si gestiscono.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nuovo collegamento da Intune all'interfaccia utente per i criteri di accesso condizionale basati su app di Azure AD
<!-- 1016201 -->
Ora gli amministratori IT possono impostare criteri condizionali basati su app tramite la nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Azure AD. Per ora l'accesso condizionale basato su app disponibile nella sezione Protezione app di Intune del portale di Azure resta in tale posizione e viene applicato affiancato. Per comodità è anche disponibile un collegamento alla nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Intune.

- Altre informazioni sull'[accesso condizionale basato su app in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

<!-- ########################## -->
## <a name="july-2017"></a>Luglio 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restrizione della registrazione dei dispositivi Android e iOS in base alla versione del sistema operativo  <!--- 1333256,  1245463 --->
Intune ora supporta la restrizione della registrazione di Android e iOS in base al numero di versione del sistema operativo. In **Restrizione dei tipi di dispositivo** l'amministratore IT può ora impostare una configurazione della piattaforma per limitare la registrazione tra un valore minimo e massimo del sistema operativo. Le versioni del sistema operativo Android devono essere specificate come Principale.Secondaria.Build.Rev, dove Secondaria, Build e Rev sono facoltativi. Le versioni di iOS devono essere specificate come Principale.Secondaria.Build, dove Build è facoltativa. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

>[!NOTE]
>Non limitare la registrazione tramite i programmi DEP Apple o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Limitare la registrazione dei dispositivi personali Android, iOS e macOS  <!--- 1333272,  1333275, 1245709 --->
Intune può limitare la registrazione dei dispositivi personali creando un elenco dei dispositivi aziendali consentiti con i relativi numeri IMEI. Intune ha ora esteso questa funzionalità a iOS, Android e macOS usando i numeri di serie del dispositivo. Caricando i numeri di serie in Intune, è possibile predichiarare i dispositivi come proprietà dell'azienda. Tramite le restrizioni della registrazione, è possibile bloccare i dispositivi personali (BYOD, Bring Your Own Device), consentendo così la registrazione solo per i dispositivi di proprietà dell'azienda. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

Per importare i numeri di serie, passare a **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**, fare clic su **Aggiungi** e quindi caricare un file con estensione csv senza intestazione ma con due colonne per il numero di serie e i dettagli come i numeri IMEI. Per limitare i dispositivi personali, accedere a **Registrazione del dispositivo** > **Restrizioni registrazione**. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinita** e **Configurazioni della piattaforma**. È possibile scegliere **Consenti** o **Blocca** per i dispositivi personali per iOS, Android e macOS.


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nuova azione del dispositivo per forzare la sincronizzazione con Intune <!-- 711369 -->
In questa versione è stata aggiunta una nuova azione del dispositivo che forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.
Per informazioni dettagliate, vedere [Sincronizzare il dispositivo](device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzare i dispositivi iOS supervisionati per installare automaticamente l'aggiornamento software più recente disponibile <!-- 777100 -->
È disponibile un nuovo criterio dall'area di lavoro degli aggiornamenti software, che consente di forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione. Per informazioni dettagliate, vedere [Configurare i criteri di aggiornamento per iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile: nuovo partner di Mobile Threat Defense  <!-- 954651, 1172027 -->
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi eseguita da Checkpoint SandBlast Mobile, una soluzione Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Checkpoint SandBlast Mobile. È possibile configurare criteri di accesso condizionale EMS basati sulla valutazione dei rischi di Checkpoint SandBlast Mobile e abilitati tramite i criteri di conformità dei dispositivi di Intune. È possibile consentire o bloccare l'accesso alle risorse aziendali ai dispositivi non conformi in base alle minacce rilevate.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Distribuire un'app come disponibile in Microsoft Store per le aziende <!-- 748101 -->
Con questa versione, gli amministratori possono ora assegnare Microsoft Store per le aziende come disponibile. Con questa impostazione, gli utenti finali possono installare l'app dall'app Portale aziendale o dal sito Web del portale aziendale senza essere reindirizzati a Microsoft Store.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Aggiornamenti dell'interfaccia utente del sito Web Portale aziendale <!--1313244 part 1-->
Sono stati introdotti vari aggiornamento all'interfaccia utente del [sito Web portale aziendale](https://portal.manage.microsoft.com) per migliorare l'esperienza per gli utenti finali.

- __Miglioramenti per i riquadri delle app__: le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente in base al colore dominante dell'icona, se rilevabile. Se applicabile, questo sfondo sostituisce il bordo grigio precedentemente visibile nei riquadri delle app.

    In una versione futura è previsto che il sito Web del portale aziendale visualizzi le icone grandi ogniqualvolta possibile. È consigliabile che gli amministratori IT pubblichino app con icone ad alta risoluzione di dimensioni minime pari a 120x120 pixel. 

- __Modifiche alla struttura di spostamento__: gli elementi della barra di spostamento sono stati spostati nel menu hamburger in alto a sinistra. La pagina delle categorie è stata rimossa. Gli utenti possono ora filtrare il contenuto in base alla categoria durante l'esplorazione.

- __Aggiornamenti per le app in primo piano__: è stata aggiunta una pagina dedicata nel sito, nella quale gli utenti possono visualizzare le app che hanno scelto di mettere in primo piano e sono state apportate alcune modifiche all'interfaccia utente della sezione In primo piano nella home page.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Supporto di iBooks per il sito Web Portale aziendale <!--1231841-->
È stata aggiunta una pagina dedicata al sito Web del portale aziendale che consente agli utenti di visualizzare e scaricare iBooks. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Dettagli aggiuntivi per la risoluzione dei problemi dell'help desk <!---  Applies to 1263399, 1326964, 1341642 --->
Intune ha aggiornato la visualizzazione della risoluzione dei problemi e aggiunto le informazioni che fornisce agli amministratori e al personale dell'help desk. È ora disponibile una tabella **Assegnazioni** che fornisce un riepilogo di tutte le assegnazioni dell'utente in base all'appartenenza a gruppi. L'elenco include:
- App per dispositivi mobili
- Criteri di conformità
- Profili di configurazione

Inoltre, la tabella **Dispositivi** ora include le colonne **Tipo di join per Azure AD** e **Conforme con Azure AD**. Per altre informazioni, vedere [Aiutare gli utenti nella risoluzione dei problemi](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Data warehouse di Intune (anteprima pubblica)
Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologica dell'ambiente. È possibile accedere ai dati tramite un file di Power BI (PBIX), un collegamento OData compatibile con molti strumenti di analisi oppure interagendo con l'API REST. Per altre informazioni, vedere [Usare il data warehouse di Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modalità chiara e modalità scura disponibili per l'app Portale aziendale per Windows 10 <!---676547--->
Gli utenti finali potranno personalizzare la modalità di colore per l'app Portale aziendale per Windows 10. L'utente potrà apportare la modifica nella sezione delle impostazioni dell'app Portale aziendale. La modifica verrà visualizzata dopo che l'utente avrà riavviato l'app. Per Windows 10 versione 1607 e successive, la modalità dell'app predefinita sarà l'impostazione di sistema. Per Windows 10 versione 1511 e precedenti, la modalità dell'app predefinita sarà la modalità chiara.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Consentire agli utenti finali di contrassegnare il gruppo di dispositivi nell'app Portale aziendale per Windows 10 <!---807046-->
Gli utenti finali possono ora selezionare il gruppo a cui appartiene il dispositivo contrassegnandolo direttamente dall'app Portale aziendale per Windows 10.

<!-- ########################## -->
## <a name="june-2017"></a>Giugno 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nuovo accesso di amministrazione basato su ruoli per gli amministratori di Intune   <!-- 1099990 -->  
È stato aggiunto un nuovo ruolo di amministrazione dell'accesso condizionale per visualizzare, creare, modificare ed eliminare i criteri di accesso condizionale di Azure AD. In precedenza, solo gli amministratori globali e gli amministratori della sicurezza disponevano di questa autorizzazione. È possibile concedere l'autorizzazione di questo ruolo agli amministratori di Intune, in modo che possano accedere ai criteri di accesso condizionale.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Contrassegno dei dispositivi di proprietà dell'azienda con i numeri di serie <!-- 1215070 -->  
Intune supporta ora il caricamento di numeri di serie iOS, macOS e Android come identificatori dei dispositivi aziendali. Attualmente non è possibile usare i numeri di serie per bloccare la registrazione dei dispositivi personali, perché i numeri di serie non vengono verificati durante la registrazione. La funzionalità di blocco dei dispositivi personali in base al numero di serie sarà disponibile a breve.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nuove azioni remote per i dispositivi iOS <!-- 854689 -->
In questa versione sono state aggiunte due nuove azioni remote dei dispositivi per i dispositivi iPad condivisi che gestiscono l'app Classroom Apple:

- [Disconnetti l'utente corrente](device-logout-user.md): disconnette l'utente corrente di un dispositivo iOS selezionato.
- [Rimuovi utente](device-remove-user.md): elimina un utente selezionato dalla cache locale di un dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Supporto per gli iPad condivisi con l'app Classroom iOS <!-- 1044681 -->
In questa versione è stato esteso il supporto per la gestione dell'app Classroom per iOS per includere gli studenti che accedono agli iPad condivisi usando il proprio ID Apple gestito.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Modifiche alle app Intune predefinite <!-- 1332306 -->
Intune conteneva in precedenza un numero di app predefinite che era possibile assegnare rapidamente. In base ai commenti e suggerimenti ricevuti, abbiamo rimosso l'elenco e le app predefinite non verranno più visualizzate.
Tuttavia, se sono già state assegnate app predefinite, le app assegnate saranno ancora visibili nell'elenco delle app. È possibile continuare ad assegnare queste app in base alle proprie esigenze.
In una versione successiva si prevede di aggiungere un metodo più semplice per la selezione e l'assegnazione delle app predefinite dal portale di Azure.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Installazione più semplice delle app di Office 365 <!--- 1121362 --->
Un nuovo tipo di applicazioni **Office 365 ProPlus** semplifica l'assegnazione delle app Office 365 ProPlus 2016 ai dispositivi gestiti che eseguono la versione più recente di Windows 10. È anche possibile installare Microsoft Project e Microsoft Visio, se si hanno le relative licenze. Le app desiderate vengono unite in bundle e visualizzate come un'unica app nell'elenco di app della console di Intune.
Per altre informazioni, vedere [How to add Office 365 apps for Windows 10](apps-add-office365.md) (Come aggiungere app di Office 365 per Windows 10).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Supporto per le app offline da Microsoft Store per le aziende <!--- 777044 --->
Le app offline acquistate da Microsoft Store per le aziende verranno ora sincronizzate nel portale di Azure. È possibile quindi distribuire tali app a gruppi di dispositivi o di utenti. Le app offline vengono installate da Intune, non dallo Store.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>L'app Microsoft Teams è ora inclusa nell'elenco CA basato su app delle app approvate   <!-- 1257019 -->
L'app Microsoft Teams per iOS e Android fa ora parte delle app approvate per i criteri di accesso condizionale basati su app per Exchange e SharePoint Online. L'app può essere configurata tramite il pannello Protezione app di Intune nel portale di Azure di tutti i tenant che usano attualmente l'accesso condizionale basato su app.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integrazione di Managed Browser e del proxy di applicazione <!-- 1287310 -->
Intune Managed Browser può essere ora integrato con il servizio proxy di applicazione di Azure AD per consentire agli utenti di accedere ai siti Web interni, anche quando lavorano in remoto. Gli utenti del browser immettono l'URL nel modo consueto e Managed Browser instrada la richiesta attraverso il gateway Web del proxy di applicazione. Per altre informazioni, vedere [Manage Internet access using Managed browser policies](app-configuration-managed-browser.md) (Gestire l'accesso a Internet usando i criteri di Managed Browser).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nuove impostazioni di configurazione dell'app per Intune Managed Browser <!-- 682951 -->
In questa versione sono state aggiunte altre configurazioni per l'app Intune Managed Browser per iOS e Android. È possibile ora usare i criteri di configurazione delle app per configurare la home page predefinita e i segnalibri del browser.
Per altre informazioni, vedere [Manage Internet access using managed browser policies](app-configuration-managed-browser.md) (Gestire l'accesso a Internet usando i criteri di Managed Browser).

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Impostazioni BitLocker per Windows 10  <!-- 951707 -->
È ora possibile configurare le impostazioni BitLocker per i dispositivi Windows 10 con un nuovo profilo di dispositivo di Intune. Ad esempio, è possibile richiedere che i dispositivi vengano crittografati e anche configurare altre impostazioni che vengono applicate quando BitLocker è attivato.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
In questa versione sono stati aggiunte nuove impostazioni per il profilo di restrizione del dispositivo Windows 10, nelle categorie seguenti:

- Windows Defender
- Rete cellulare e connettività
- Esperienza della schermata bloccata
- Privacy
- Cerca
- Contenuti in evidenza di Windows
- Browser Microsoft Edge

Per altre informazioni sulle impostazioni di Windows 10, vedere [Windows 10 and later device restriction settings](device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>L'app Portale aziendale per Android ora include una nuova esperienza utente finale per i criteri di protezione delle app <!--1305217-->
In base ai suggerimenti dei clienti, l'app Portale aziendale per Android è stata modificata e ora include un pulsante **Accesso al contenuto aziendale**. Lo scopo è impedire che gli utenti finali eseguano inutilmente il processo di registrazione quando hanno solo necessità di accedere alle app che supportano i criteri di protezione delle app, una funzionalità di gestione delle applicazioni mobili di Intune. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nuova azione di menu per rimuovere facilmente Portale aziendale <!--1164569-->
In risposta al feedback degli utenti, per l'app Portale aziendale per Android è stata aggiunta una nuova azione di menu per eseguire la rimozione di Portale aziendale dal dispositivo. Questa azione rimuove il dispositivo dalla gestione di Intune in modo che l'utente possa rimuovere l'app dal dispositivo. È possibile visualizzare queste modifiche nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md) e nella [documentazione per gli utenti finali di Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Miglioramenti alla sincronizzazione di app con Windows 10 Creators Update <!--676505-->
L'app Portale aziendale per Windows 10 avvierà ora automaticamente una sincronizzazione per le richieste di installazione di app per dispositivi con Windows 10 Creators Update (1703). Ciò consente di limitare il problema di installazione di app quando lo stato è "In attesa di sincronizzazione". Inoltre, gli utenti saranno in grado di avviare manualmente la sincronizzazione all'interno dell'app. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nuova esperienza guidata per il Portale aziendale di Windows 10 <!---1058938--->
L'app Portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate che guidano l'utente nella procedura di registrazione in Azure Active Directory (obbligatoria per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale. Gli utenti possono continuare a usare l'app se non completano la registrazione, ma le funzionalità saranno limitate.

Questo aggiornamento è visibile solo nei dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 (build 1607) o versioni successive. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Disponibilità generale delle console di amministrazione di Microsoft Intune e dell'accesso condizionale
Questo è l'annuncio della disponibilità generale sia della nuova console di amministrazione di Intune nel portale di Azure che della nuova console di amministrazione dell'accesso condizionale. Con Intune nel portale di Azure è ora possibile gestire tutte le funzionalità MAM e MDM di Intune con un'esperienza di amministrazione consolidata, sfruttando allo stesso tempo le funzioni di raggruppamento e targeting di Azure AD. L'accesso condizionale in Azure offre funzionalità avanzate per Azure AD e Intune in un'unica console unificata. Per quanto riguarda l'esperienza di amministrazione, inoltre, il passaggio alla piattaforma Azure consente di usare browser moderni.

Intune è ora visibile senza l'etichetta di **anteprima** nel portale di Azure all'indirizzo portal.azure.com.

Al momento non è richiesto alcun intervento da parte dei clienti esistenti, a meno che non si riceva uno di una serie di messaggi nel centro messaggi che richiede di intervenire in modo da consentire a Microsoft di eseguire la migrazione dei gruppi. È anche possibile che si riceva una notifica nel centro messaggi che informa che la migrazione richiede più tempo a causa di errori di Microsoft. Stiamo continuando a lavorare con impegno per completare la migrazione di tutti i clienti interessati.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Miglioramenti dei riquadri dell'app Portale aziendale per iOS
È stata aggiornata la progettazione dei riquadri dell'app nella home page in modo che rispecchino il colore personalizzato impostato per Portale aziendale. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Selezione account ora disponibile per l'app Portale aziendale per iOS
Gli utenti di dispositivi iOS potrebbero ora visualizzare la nuova selezione account quando accedono al Portale aziendale se usano l'account aziendale o dell'istituto di istruzione per accedere ad altre app Microsoft. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

<!-- ########################## -->
## <a name="may-2017"></a>Maggio 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Modifica dell'autorità MDM senza annullare la registrazione dei dispositivi gestiti <!--1103950-->
È ora possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Nella console di Configuration Manager è possibile [modificare l'autorità MDM](/sccm/mdm/deploy-use/change-mdm-authority) da Imposta su Configuration Manager (ibrida) a Microsoft Intune (autonoma) o viceversa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notifica migliorata per i PIN di avvio Samsung Knox <!--1087143-->
Quando gli utenti finali devono impostare un PIN di avvio su dispositivi Samsung Knox per garantire la conformità alla crittografia, toccando la notifica visualizzata, gli utenti finali verranno indirizzati alla posizione esatta nell'app Impostazioni.  In precedenza, la notifica rimandava gli utenti finali alla schermata di modifica della password.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Supporto di Apple School Manager (ASM) con iPad condiviso <!-- 748864, 770395-->

Intune supporta ora l'uso di Apple School Manager (ASM) al posto di Apple Device Enrollment Program per fornire funzionalità di registrazione pronte all'uso per i dispositivi iOS. L'onboarding di ASM è necessario usare l'app Classroom per iPad condivisi e per consentire la sincronizzazione dei dati da ASM ad Azure Active Directory tramite Microsoft School Data Sync (SDS). Per altre informazioni, vedere [Abilitare la registrazione di dispositivi iOS con Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> La configurazione di iPad condivisi per l'uso dell'app Classroom richiede configurazioni di iOS Education in Azure non ancora disponibili.  Questa funzionalità verrà aggiunta presto.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Fornire assistenza remota ai dispositivi Android con TeamViewer <!-- 675418 -->

Intune può ora usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per consentire agli amministratori di offrire assistenza remota agli utenti che eseguono dispositivi Android. Per altre informazioni, vedere [Fornire assistenza remota per i dispositivi Android gestiti da Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Gestione delle app

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nuove condizioni dei criteri di protezione delle app per MAM <!-- 679864 -->

È ora possibile impostare un requisito per MAM senza registrare gli utenti, che consente di applicare i criteri seguenti:

- Versione minima dell'applicazione
- Versione minima del sistema operativo
- Versione minima di Intune App SDK per l'applicazione di destinazione (solo iOS)

Questa funzionalità è disponibile sia per Android che per iOS. Intune supporta l'imposizione della versione minima per le versioni delle piattaforme del sistema operativo, per le versioni delle applicazioni e per Intune App SDK. In iOS applicazioni con SDK integrato possono anche imporre la versione minima a livello di SDK. L'utente non potrà accedere all'applicazione di destinazione se i requisiti minimi definiti tramite i criteri di protezione delle app non vengono soddisfatti ai tre diversi livelli definiti in precedenza. A questo punto, l'utente può rimuovere l'account (per le applicazioni con identità multiple), chiudere l'applicazione o aggiornare la versione del sistema operativo o dell'applicazione.

È anche possibile configurare impostazioni aggiuntive per fornire una notifica che non causa blocchi per consigliare un aggiornamento del sistema operativo o dell'applicazione. Questa notifica può essere chiusa e l'applicazione può essere usata normalmente.

Per altre informazioni, vedere [Impostazioni dei criteri di protezione delle app per iOS](app-protection-policy-settings-ios.md) e [Impostazioni dei criteri di protezione delle app per Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configurare le configurazioni delle app per Android for Work <!-- 621621 -->
Alcune app Android dallo store supportano opzioni di configurazione gestite che consentono a un amministratore IT di controllare l'esecuzione di un'app nel profilo di lavoro. Con Intune è ora possibile visualizzare le configurazioni supportate da un'app e definirle dal portale di Azure con una finestra di progettazione della configurazione o un editor JSON. Per altre informazioni, vedere [Usare configurazioni di app per Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nuove funzionalità di configurazione delle app per MAM senza registrazione <!-- 677969 -->
È ora possibile creare criteri di configurazione delle app tramite MAM senza canale di registrazione. Questa funzionalità equivale ai criteri di configurazione delle app disponibili per la configurazione delle app di gestione di dispositivi mobili (MDM). Per un esempio di configurazione di app con MAM senza registrazione, vedere [Gestire l'accesso a Internet usando criteri di Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configurare elenchi di URL consentiti e bloccati per Managed Browser <!-- 682960 -->
È ora possibile configurare un elenco di domini e URL consentiti o bloccati per Managed Browser con le impostazioni di configurazione delle app nel portale di Azure. Queste impostazioni possono essere configurate indipendentemente dal fatto che questa soluzione venga usata in un dispositivo gestito o non gestito. Per altre informazioni, vedere [Gestire l'accesso a Internet usando i criteri di Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Visualizzazione per il supporto tecnico dei criteri di protezione delle app <!-- 1069473 -->
Gli utenti del supporto tecnico IT possono ora controllare lo stato delle licenze utente e lo stato delle app con criteri di protezione delle app assegnati agli utenti nel pannello Risoluzione dei problemi. Per informazioni dettagliate, vedere [Risoluzione dei problemi](./help-desk-operators.md).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Controllare le visite ai siti Web nei dispositivi iOS <!-- 723832 -->
È ora possibile controllare i siti Web che gli utenti di dispositivi iOS possono visitare tramite uno dei due metodi seguenti:

- Aggiungere URL consentiti e bloccati tramite il filtro predefinito dei contenuti Web di Apple.

- Consentire l'accesso dal browser Safari solo ai siti Web specificati. Per ogni sito specificato viene creato il segnalibro corrispondente in Safari.

Per altre informazioni, vedere [Impostazioni di filtraggio del contenuto Web di Intune per i dispositivi iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Preconfigurare le autorizzazioni dei dispositivi per le app Android for Work <!-- 621614 -->
Per le app distribuite in profili di lavoro di dispositivi Android For Work, è ora possibile configurare lo stato delle autorizzazioni per le singole app.  Per impostazione predefinita, le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiederanno agli utenti di accettare o rifiutare le autorizzazioni.  Se ad esempio un'app usa il microfono del dispositivo, all'utente finale viene chiesto di concedere all'app l'autorizzazione per l'uso del microfono. Questa funzionalità consente di definire le autorizzazioni per conto dell'utente finale.  È possibile configurare le autorizzazioni per a) negare automaticamente senza avvisare l'utente, b) approvare automaticamente senza avvisare l'utente o c) richiedere all'utente di accettare o negare. Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Definire il PIN specifico dell'app per i dispositivi Android for Work <!-- 728976, 1102534 -->
I dispositivi Android 7.0 e versioni successive con un profilo di lavoro gestito come dispositivo Android for Work consentono all'amministratore di definire criteri di passcode applicabili solo alle app nel profilo di lavoro.  Le opzioni includono:

- Definire solo criteri di passcode a livello di dispositivo: si tratta del passcode che l'utente deve usare per sbloccare l'intero dispositivo.
- Definire solo criteri di passcode del profilo di lavoro: agli utenti finali viene chiesto di immettere un passcode ogni volta che viene aperta un'app nel profilo di lavoro.
- Definire criteri sia del dispositivo che del profilo di lavoro: l'amministratore IT può scegliere di definire sia criteri di passcode del dispositivo che criteri di passcode del profilo di lavoro con complessità diverse (ad esempio, un PIN di 4 cifre per sbloccare il dispositivo, ma un PIN di 6 cifre per aprire un'app di lavoro).

Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Questa funzionalità è disponibile solo in Android 7.0 e versioni successive.  Per impostazione predefinita, l'utente finale può usare i due PIN definiti separatamente oppure scegliere di combinare i due PIN definiti in quello più complesso.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nuove impostazioni per i dispositivi Windows 10 <!-- 978585 -->
Sono state aggiunte nuove [impostazioni di restrizione dei dispositivi Windows](device-restrictions-windows-10.md) che controllano funzionalità come schermi wireless, individuazione dei dispositivi, passaggio da un'attività a un'altra e messaggi di errore della scheda SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Aggiornamenti della configurazione del certificato <!-- 918991 and 823198 -->
Per la creazione di un profilo di certificato SCEP, l'opzione <strong>Personalizzato</strong> per <strong>Formato nome soggetto</strong> è disponibile per i dispositivi iOS, Android e Windows. Prima dell'aggiornamento, il campo <strong>Personalizzato</strong> era disponibile solo per i dispositivi iOS. Per altre informazioni, vedere [Come creare un profilo certificato SCEP](certificates-profile-scep.md).

Per la creazione di un profilo di certificato PKCS, è disponibile l'opzione **Custom Azure AD attribute** (Attributo Azure AD personalizzato) per **Nome alternativo soggetto**. È disponibile l'opzione **Reparto** quando si seleziona **Custom Azure AD attribute** (Attributo Azure AD personalizzato). Per altre informazioni, vedere [Creare un profilo certificato SCEP](certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configurare più app che possono essere eseguite quando un dispositivo Android è in modalità tutto schermo <!-- 662059 -->
Quando un dispositivo Android è in modalità tutto schermo, in precedenza era possibile configurare una sola app per consentirne l'esecuzione. È ora possibile configurare più app usando l'ID, l'URL dello store oppure selezionando un'app Android già gestita. Per altre informazioni vedere [Impostazioni della modalità tutto schermo](device-restrictions-android.md#kiosk).



<!-- ########################## -->
## <a name="april-2017"></a>Aprile 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Supporto per la gestione dell'app Classroom Apple
È ora possibile gestire l'app Classroom iOS nei dispositivi iPad. Configurare l'app Classroom nell'iPad degli insegnanti con la classe e i dati sugli studenti corretti, quindi configurare gli iPad degli studenti registrati in una classe, in modo da poterli controllare tramite l'app.
Per altri dettagli, vedere [Configurare le impostazioni di iOS relative alla formazione](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Supporto per le opzioni di configurazione gestita per le app Android <!-- 621621 -->
Le app Android nel Play Store che supportano le opzioni di configurazione gestita ora possono essere configurate da Intune.  Questa funzionalità consente ai responsabili IT di visualizzare l'elenco dei valori di configurazione supportati da un'app e fornisce un'interfaccia utente guidata avanzata per consentire la configurazione di tali valori.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nuovi criteri Android per PIN complessi <!-- 722069 -->
È ora possibile impostare una [password](device-restrictions-android.md#password) obbligatoria di tipo Complessa numerica in un profilo di dispositivo Android per i dispositivi che eseguono Android 5.0 e versioni successive.  Usare questa impostazione per impedire agli utenti dei dispositivi di creare un PIN contenente numeri ripetuti o consecutivi, ad esempio 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Supporto aggiuntivo per i dispositivi Android for Work
- **Gestire le impostazioni delle password e dei profili di lavoro** <!-- 612808 -->

  Questo nuovo criterio di restrizione dei dispositivi Android for Work ora consente di gestire le impostazioni delle password e dei profili di lavoro nei dispositivi Android for Work gestiti.

- **Consenti la condivisione dei dati tra i profili di lavoro e personali** <!-- 1045102 -->

Questo profilo di restrizione dei dispositivi Android for Work ora offre nuove opzioni che consentono di configurare la condivisione dei dati tra i profili di lavoro e quelli personali.

- **Limitare il copia e incolla tra i profili di lavoro e personali** <!-- 1046094 -->

  Un nuovo profilo di dispositivo personalizzato per i dispositivi Android for Work consente ora di limitare le operazioni di copia e incolla tra app di lavoro e personali.

Per altre informazioni, vedere l'articolo sulle [restrizioni dei dispositivi per Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Assegnare app LOB a dispositivi iOS e Android <!-- 1057568 -->
È ora possibile assegnare a utenti o dispositivi app line-of-business (LOB) per [iOS](lob-apps-ios.md) (file con estensione ipa) e per [Android](lob-apps-android.md) (file con estensione apk).


### <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nuovi criteri dei dispositivi per iOS <!-- 723774, 723815, 723826, 723830 -->
- **App nella schermata iniziale**: stabilisce quali sono le app visualizzate dagli utenti nella [schermata iniziale dei loro dispositivi iOS](home-screen-settings-ios.md). Questo criterio modifica il layout della schermata iniziale ma non distribuisce nessuna app.

- **Connessioni ai dispositivi AirPrint**: specifica i [dispositivi AirPrint](air-print-settings-ios-macos.md) (stampanti di rete) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Connessioni ai dispositivi AirPlay**: specifica i [dispositivi AirPlay](airplay-settings-ios.md) (come Apple TV) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Messaggio personalizzato della schermata di blocco**: consente di configurare un messaggio personalizzato che gli utenti visualizzeranno nella schermata di blocco del loro dispositivo iOS, in sostituzione del messaggio della schermata di blocco predefinito. Per altre informazioni, vedere [Attivare la modalità di dispositivo perso nei dispositivi iOS](device-lost-mode.md).

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Limitare le notifiche push per le app per iOS <!-- 723767 -->
In un profilo di restrizione del dispositivo di Intune è possibile configurare le [impostazioni di notifica](app-notification-settings-ios.md) seguenti per i dispositivi iOS:

- Attivare o disattivare completamente la notifica per un'app specificata.
- Attivare o disattivare la notifica nel Centro notifiche per un'app specificata.
- Specificare il tipo di avviso, ovvero **Nessuno**, **Banner** o **Modal Alert** (Avviso modale).
- Specificare se sono consentite le notifiche per questa app.
- Specificare se sono consentite le notifiche audio.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurare le app per iOS per l'esecuzione in modo autonomo in Modalità applicazione singola <!-- 737837 -->
È possibile usare un profilo di dispositivo di Intune per configurare i dispositivi iOS per l'esecuzione delle applicazioni specificate in [Modalità applicazione singola autonoma](device-restrictions-ios.md#autonomous-single-app-mode). Quando questa modalità è configurata e l'app è in esecuzione, il dispositivo è bloccato in modo che possa eseguire solo quell'app. Un esempio è quando si configura un'app che consente agli utenti di eseguire un test nel dispositivo. Quando le operazioni dell'app sono state completate o si rimuove questo criterio, il dispositivo torna allo stato normale.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurare i domini attendibili per posta elettronica ed esplorazione Web nei dispositivi iOS <!-- 723765 -->
Da un profilo di restrizione del dispositivo iOS è ora possibile configurare le [impostazioni di dominio](device-restrictions-ios.md#domains) seguenti:

- **Domini di posta elettronica non contrassegnati**: i messaggi inviati o ricevuti dall'utente che non corrispondono ai domini specificati qui verranno contrassegnati come non attendibili.

- **Domini Web gestiti**: i documenti scaricati dagli URL specificati qui verranno considerati gestiti (solo Safari).  

- **Domini con riempimento automatico della password di Safari**: gli utenti possono salvare le password in Safari solo dagli URL corrispondenti ai modelli specificati qui. Per usare questa impostazione, il dispositivo deve essere in modalità con supervisione e non deve essere configurato per più utenti (iOS 9.3 e versioni successive).


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>App VPP disponibili nel portale aziendale iOS <!-- 748782 -->
È ora possibile assegnare app per iOS acquistate con Volume Purchase Program (VPP) come installazioni **disponibili** per gli utenti finali. Gli utenti finali avranno bisogno di un account Apple Store per installare l'app.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizzare eBook dallo Store VPP di Apple <!-- 800878 -->
È ora possibile [sincronizzare i libri](vpp-apps-ios.md) acquistati nello store Apple Volume Purchase Program con Intune e assegnarli agli utenti.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestione di più utenti per i dispositivi Samsung Knox Standard <!-- 971988 -->
I dispositivi che eseguono Samsung Knox Standard sono ora supportati per la [gestione multiutente](android-enroll.md) in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure Active Directory e il dispositivo è gestito centralmente indipendentemente dal fatto che sia o meno in uso.  Dopo aver eseguito l'accesso gli utenti finali possono accedere alle app e implementare i criteri loro assegnati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Altre impostazioni relative alle restrizioni dei dispositivi per Windows <!-- 818566 -->
Sono ora supportate altre [impostazioni di restrizione dei dispositivi per Windows](device-restrictions-windows-10.md), ad esempio maggiore supporto per il browser Microsoft Edge, personalizzazione della schermata di blocco del dispositivo, personalizzazioni del menu Start, sfondo per la ricerca Windows Spotlight e impostazione del proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Supporto multiutente per Windows 10 Creators Update <!-- 822547 -->
È stato aggiunto il supporto per la [gestione multiutente](windows-enroll.md) per i dispositivi che eseguono Windows 10 Creators Update e sono aggiunti al dominio di Azure Active Directory. Ciò significa che quando utenti standard diversi accedono al dispositivo con le credenziali di Azure AD ricevono tutte le app e i criteri assegnati al loro nome utente. Gli utenti non possono attualmente usare il portale aziendale per scenari self-service, ad esempio l'installazione di app.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start per i PC Windows 10<!-- 1004830 -->
È ora disponibile una nuova [azione del dispositivo Fresh Start](device-fresh-start.md) per i PC Windows 10.  Quando si esegue questa azione, vengono rimosse tutte le app precedentemente installate nel PC e il computer è aggiornato automaticamente alla versione più recente di Windows. Questa funzionalità può essere usata per rimuovere le app OEM che spesso sono preinstallate in un nuovo PC. È possibile configurare se i dati utente devono essere conservati quando si esegue questa azione del dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Percorsi di aggiornamento aggiuntivi per Windows 10 <!-- 903672 -->
È ora possibile creare [criteri di aggiornamento dell'edizione per aggiornare i dispositivi](edition-upgrade-configure-windows-10.md) alle seguenti edizioni aggiuntive di Windows 10:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Registrazione in blocco di dispositivi Windows 10 <!-- 747607 -->
È ora possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune con Windows Configuration Designer (WCD). Per abilitare la [registrazione MDM in blocco](windows-bulk-enroll.md) del tenant di Azure AD, creare un pacchetto di provisioning che aggiunga i dispositivi al tenant di Azure AD usando Windows Configuration Designer e applicare il pacchetto ai dispositivi di proprietà dell'azienda che si vuole registrare e gestire in blocco. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento gli scenari di tipo self-service o portale aziendale non sono supportati.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nuove impostazioni MAM per PIN e posizioni di archiviazione gestita <!-- 581122, 736644 -->
Sono ora disponibili due nuove impostazioni dell'app per semplificare gli scenari di gestione di applicazioni mobili (MAM):

- **Disabilitare il PIN dell'app quando il PIN del dispositivo è gestito**: consente di rilevare se nel dispositivo registrato è presente un PIN del dispositivo e, in tal caso, di ignorare il PIN dell'app attivato dai criteri di protezione delle app. Questa impostazione consentirà di ridurre il numero di volte in cui gli utenti visualizzeranno un prompt di richiesta del PIN all'apertura di un'applicazione abilitata per MAM in un dispositivo registrato. Questa funzionalità è disponibile per sia per Android che per iOS.

- **Selezionare i servizi di archiviazione in cui è possibile salvare i dati aziendali**: consente di specificare i percorsi di archiviazione in cui salvare i dati aziendali. Gli utenti possono eseguire il salvataggio nei servizi di posizione di archiviazione selezionati, il che significa che tutti gli altri servizi di posizione di archiviazione non elencati verranno bloccati.

  I servizi di posizione di archiviazione supportati sono i seguenti:

  - OneDrive
  - Business SharePoint Online
  - Archiviazione locale

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portale del supporto tecnico per la risoluzione dei problemi <!-- 907448 -->
Il nuovo [portale per la risoluzione dei problemi](help-desk-operators.md) consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare utenti e dispositivi e di eseguire attività per la risoluzione dei problemi tecnici di Intune.

<!-- ########################## -->
## <a name="march-2017"></a>Marzo 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Supporto per la modalità di dispositivo perso di iOS <!--431695-->
Per i dispositivi iOS 9.3 e versioni successive, Intune ha aggiunto il supporto per la **modalità di dispositivo perso**. È ora possibile bloccare un dispositivo per impedirne l'uso e visualizzare un messaggio e un numero di telefono di contatto nella schermata di blocco del dispositivo.

L'utente finale non sarà in grado di sbloccare il dispositivo finché la modalità di dispositivo perso non verrà disabilitata da un amministratore. Quando la modalità di dispositivo perso è abilitata, è possibile usare l'azione **Individua il dispositivo** per visualizzare la posizione geografica del dispositivo su una mappa nella console di Intune.

Deve trattarsi di un dispositivo iOS di proprietà dell'azienda, registrato con DEP, in cui sia attiva la modalità con supervisione.

Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).

### <a name="improvements-to-device-actions-report---677150--"></a>Miglioramenti al report Azioni del dispositivo <!--677150-->
Le prestazioni del report Azioni del dispositivo sono state migliorate. È inoltre possibile filtrare il report in base allo stato. Si possono ad esempio mostrare solo le azioni del dispositivo che sono state completate.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Assegnare app line-of-business agli utenti con dispositivi non registrati <!--748823-->
Ora è possibile assegnare app line-of-business dallo store agli utenti anche se i dispositivi degli utenti non sono registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale.

### <a name="new-compliance-reports---846671--"></a>Nuovi report di conformità <!--846671-->
Sono ora disponibili report di conformità che definiscono il comportamento di conformità dei dispositivi in ambito aziendale e consentono di risolvere rapidamente i problemi correlati alla conformità riscontrati dagli utenti. È possibile visualizzare le informazioni seguenti:

- Stato di conformità generale dei dispositivi
- Stato di conformità per una singola impostazione
- Stato di conformità per singoli criteri

È anche possibile usare questi report per eseguire il drill-down in un singolo dispositivo e visualizzare le impostazioni e i criteri specifici che hanno effetto su tale dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima della registrazione di Apple era accessibile solo dai collegamenti nel portale di Azure. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.


<!-- ########################## -->
## <a name="february-2017"></a>Febbraio 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilità di limitare la registrazione di dispositivi mobili <!--747600, 795782-->
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.

* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.  
* Solo per iOS e Android è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](device-enrollment.md).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Visualizzare tutte le azioni nei dispositivi gestiti <!--677150-->
Il nuovo report __Azioni del dispositivo__ mostra gli utenti che hanno eseguito azioni remote come il ripristino delle impostazioni predefinite nei dispositivi e lo stato dell'azione. Vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->
Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="display-device-categories---814654--"></a>Visualizzare le categorie di dispositivi <!--814654-->
È ora possibile visualizzare la categoria dei dispositivi come colonna dell'elenco dei dispositivi. È inoltre possibile modificare la categoria nella sezione delle proprietà del pannello delle proprietà del dispositivo. Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurare le impostazioni di Windows Update for Business <!--776716-->

Windows as a Service è il nuovo modo per distribuire gli aggiornamenti per Windows 10. A partire da Windows 10, i nuovi aggiornamenti qualitativi e delle funzionalità includeranno il contenuto di tutti gli aggiornamenti precedenti. Ciò significa che, una volta installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 sono perfettamente aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Usando Windows Update for Business, è possibile semplificare l'esperienza di gestione degli aggiornamenti in modo da non dover approvare singoli aggiornamenti per gruppi di dispositivi. È comunque possibile gestire i rischi nei propri ambienti configurando una strategia di implementazione degli aggiornamenti. In questo modo, Windows Update verificherà che gli aggiornamenti vengano installati al momento opportuno. Microsoft Intune offre la possibilità di configurare le impostazioni di aggiornamento sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. Per gli aggiornamenti i dispositivi accedono direttamente a Windows Update. Usare Intune per configurare e gestire gli **anelli di aggiornamento di Windows 10**. Un anello di aggiornamento contiene un gruppo di impostazioni che definiscono quando e come vengono installati gli aggiornamenti di Windows 10. Per informazioni dettagliate, vedere [Configurare le impostazioni di Windows Update for Business](windows-update-for-business-configure.md).
