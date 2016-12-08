---
title: Impostazioni dei criteri di Windows 10 | Microsoft Intune
description: Usare le impostazioni dei criteri indicate nell&quot;argomento per configurare le impostazioni personalizzate integrate per dispositivi registrati Windows 10 Desktop e Windows 10 Mobile.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/03/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad36bfd7b4f60626181ecaf27c51a9b108005979
ms.openlocfilehash: 8c970a4d1362def67e17da656b5e12e5bab2667b


---

# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Impostazioni dei criteri di Intune per i dispositivi Windows 10 in Microsoft Intune

Questo argomento contiene informazioni che consentono di comprendere le impostazioni dei criteri di Intune che è possibile usare per gestire i dispositivi Windows 10. Leggere questo argomento insieme alle procedure descritte in [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) per configurare le impostazioni predefinite e personalizzate per i dispositivi Windows 10 Desktop e Windows 10 Mobile registrati. Non è possibile usare questi criteri con PC che eseguono il [software client per PC di Intune](/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune).

È possibile scegliere tra due tipi di criteri:

- **Criteri personalizzati**: usare i **criteri personalizzati** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows 10 rende disponibili molte impostazioni tramite il [provider del servizio di configurazione dei criteri](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Criteri di configurazione generali**: usare questo tipo di criteri quando si vogliono selezionare le impostazioni dall'elenco predefinito fornito con Microsoft Intune.

## <a name="custom-policy-settings"></a>Impostazioni di criteri personalizzati

Specificare le impostazioni seguenti in un criterio personalizzato.

### <a name="general"></a>Generale

Immettere un nome e una descrizione facoltativa per i criteri che consenta di identificarli nella console di Intune.

### <a name="oma-uri-settings"></a>Impostazioni OMA-URI

Per ogni impostazione URI OMA che si vuole aggiungere, immettere le informazioni seguenti. Usare il [riferimento alle impostazioni URI di Windows 10](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) in questo argomento per informazioni sulle impostazioni che è possibile usare:

- **Nome impostazione**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
- **Descrizione impostazione**: immettere facoltativamente una descrizione per l'impostazione.
- **Tipo di dati**: scegliere tra i tipi di dati seguenti:
    - **Stringa**
    - **Stringa (XML)**
    - **Data e ora**
    - **Intero**
    - **A virgola mobile**
    - **Booleano**
- **URI OMA (maiuscole/minuscole)**: specificare l'URI OMA per cui si vuole fornire un'impostazione.
- **Valore**: specificare il valore da associare all'URI OMA immesso.

### <a name="example"></a>Esempio
Nella schermata seguente è stata abilitata l'impostazione **Connectivity/AllowVPNOverCellular**. Ciò consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

> ![Esempio di criterio personalizzato contenente le impostazioni VPN](./media/custom-policy-example.png)

## <a name="windows-10-uri-settings"></a>Impostazioni URI di Windows 10
Usare questa sezione per informazioni sulle impostazioni URI OMA che è possibile configurare con un **criterio personalizzato di Windows 10**.

### <a name="policy"></a>Criteri

|Nome e URI criteri|Dettagli|
|---------------|------------|-----------|
|**Allow Auto Update**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Solo Desktop<br>**Tipo di dati:** Integer<br />**Valori:** **0** - **5** (predefinito: **1**)|
|**Schedule Install Day**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Solo Mobile<br>**Tipo di dati:** Integer<br />**Valori:**<br>**0** - Tutti i giorni (impostazione predefinita)<br>**1** - domenica<br>**2** - lunedì<br>**3** - martedì<br>**4** - mercoledì<br>**5** - giovedì<br>**6** - venerdì<br>**7** - sabato|
|**Schedule Install Time**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** – **23** ore (**0** corrisponde a mezzanotte) (impostazione predefinita: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: l'utente non può impostare il timer del periodo di tolleranza della password; il valore è impostato su "ogni ora"<br>**1**: l'utente può impostare il timer del periodo di tolleranza della password (impostazione predefinita)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consente **l'uso della connessione Wi-Fi**<br>**1**: **consente l'uso della connessione Wi-Fi** (impostazione predefinita)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Desktop e Mobile<br>**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consente Internet condiviso <br> **1**: consente Internet condiviso (impostazione predefinita)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: consente solo le connessioni Wi-Fi configurate con MDM.<br>**1**: l'aggiunta di nuovi SSID di rete, oltre a quelli già creati da MDM, è consentita (impostazione predefinita)|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Desktop e Mobile<br>**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consentito (solo impostazione aziendale)<br>**1** : limitato<br>**2**: completo (impostazione predefinita)<br>**3**: completo e informazioni sulla diagnostica|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** : non consentito<br>**1**: solo impostazioni (impostazione predefinita)<br>**2**: impostazioni e sperimentazione|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consente la modalità AntiTheft<br>**1**: preferenza utente (impostazione predefinita)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br>**1**: consentito (impostazione predefinita)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: la VPN non è consentita sulla connessione cellulare<br>**1**: la VPN può usare qualsiasi connessione, inclusa la connessione cellulare (impostazione predefinita)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consente all'utente di attivare la funzione Bluetooth.<br>**1**: riservato. L'utente può attivare e configurare la funzione Bluetooth (non supportata in Windows Phone 8.1 per MDM, EAS, Windows 10 Desktop o Windows 10 Mobile).<br>**2**: consentito. L'utente può attivare e configurare la funzione Bluetooth (impostazione predefinita).|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentire il roaming<br> **1**: consenti il roaming (impostazione predefinita)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** : non consentito<br> **1**: consentito (impostazione predefinita)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** : non consentito<br> **1**: consentito (impostazione predefinita)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** (impostazione predefinita)<br> **1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0**<br> **1** (impostazione predefinita)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** (impostazione predefinita)<br> **1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** (impostazione predefinita)<br> **1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0** (impostazione predefinita)<br> **1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0**<br> **1** (impostazione predefinita)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** (impostazione predefinita)<br> **1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0** (impostazione predefinita)<br> **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consente.<br>Open Extended Dictionary è disattivato.<br>Un utente non può:<br>-Aggiungere un nuovo Open Extended Dictionary<br />-Aggiungere un nuovo file di configurazione di integrazione di ricerca<br>- Usare la funzionalità per i candidati dal cloud.<br>-Inviare parole registrate dall'utente.<br>**1**: consenti<br>Open Extended Dictionary può essere aggiunto e usato per impostazione predefinita. Inoltre, la funzione di integrazione ricerca può essere usata per impostazione predefinita.<br>Un utente può:<br>- Usare la funzionalità per i candidati dal cloud.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: la registrazione di conversioni errate è disabilitata<br>**1**: la registrazione di conversioni errate è abilitata (impostazione predefinita)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito <br>**1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri Shift JIS|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br />**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri JIS0208|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri JIS0208 o EUDC|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** : rigido, filtro massimo del contenuto per adulti<br>**1**: moderato, filtro moderato del contenuto per adulti, i risultati di ricerca validi non verranno filtrati (impostazione predefinita)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**Force Start Size**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: consente all'utente di modificare le dimensioni (impostazione predefinita)<br>**1**: forza la modalità a schermo non intero<br>**2**: forza la modalità a schermo intero|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non rinvia l'aggiornamento, rimane nel Current Branch, CB (impostazione predefinita)<br>**1**: abilita il rinvio degli aggiornamenti (il dispositivo segue le regole del Current Branch for Business, CBB)<br />Per informazioni dettagliate, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Pianificare la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Desktop e Mobile<br>**Descrizione:** criterio per rinviare gli aggiornamenti software per un massimo di quattro settimane<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**-**4**: numero di settimane di rinvio degli aggiornamenti software<br />Per informazioni dettagliate, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Pianificare la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Desktop e Mobile<br>**Descrizione:** criterio per rinviare gli aggiornamenti delle funzionalità per un massimo di otto mesi<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**-**8**: numero di mesi di rinvio degli aggiornamenti delle funzionalità<br />Per informazioni dettagliate, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Pianificare la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Desktop e Mobile<br>**Descrizione:** consente a un dispositivo di non ricevere più gli aggiornamenti per cinque settimane.<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**: sospende gli aggiornamenti (scade dopo cinque settimane)|

### <a name="windows-defender"></a>Windows Defender

|Nome e URI criteri|Dettagli|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0** : non consentito<br> **1**: consentito (impostazione predefinita)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: monitora tutti i file (impostazione predefinita)<br>**1** : esegue il monitoraggio dei file in ingresso<br>**2** : esegue il monitoraggio dei file in uscita|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** - **90**: indica per quanto tempo verrà conservato il malware<br>**0**: conserva per sempre il malware nella cartella di quarantena e non lo rimuove automaticamente (impostazione predefinita)|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**1**: analisi veloce (impostazione predefinita)<br>**2**: analisi completa|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: tutti i giorni (impostazione predefinita)<br>**1**: lunedì<br>**2**: martedì<br>**3**: mercoledì<br>**4**: giovedì<br>**5**: venerdì<br>**6**: sabato<br>**7**: domenica<br>**8** : nessuna analisi pianificata|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** – 12:00<br>**60** – 1:00<br>**120** – 2:00 (impostazione predefinita)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1381** -Finestra di manutenzione|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Solo Desktop<br>**Tipo di dati:** Integer<br />**Valori:**<br>**0** – 12:00<br>**60** – 1:00<br>**120** – 2:00 (impostazione predefinita)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1380** – 22:00|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0** - **100** (impostazione predefinita: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Solo Desktop<br />**Tipo di dati:** Integer<br>**Valori:<br>** **0**: non consentito (impostazione predefinita)<br> **1**: consentito|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito (impostazione predefinita)<br> **1**: consentito|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita). Se impostato su consentito, viene eseguito anche quando RTP è attivo|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non controlla le firme in un intervallo<br>**1**: controlla le firme ogni ora<br>**2**: controlla ogni due ore <br>**24**: controlla tutti i giorni<br>**8:** controlla ogni otto ore (impostazione predefinita)|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentito<br> **1**: consentito (impostazione predefinita)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: richiedere sempre (impostazione predefinita)<br>**1** : inviare campioni sicuri automaticamente<br>**2** : non inviare mai<br>**3** : inviare tutti i campioni automaticamente|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:**<br>*&lt;Elenco di estensioni separate da punto e virgola&gt;* Ad esempio: **obj;lib**<br>**Valore predefinito**: nessuna estensione viene esclusa|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:**<br />*&lt;Elenco di percorsi separati da punto e virgola&gt;*<br />Esempio: **c:\test;c:\test1.exe**<br />**Valore predefinito**: nessun percorso viene escluso|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:**<br>*&lt;Elenco di percorsi separati da punto e virgola&gt;*<br>Esempio: **c:\test.exe;c:\test1.exe**<br>**Valore predefinito**: nessun processo viene escluso|

### <a name="edge-browser"></a>Browser Edge

|Nome e URI criteri|Dettagli|
|---------------|------------|-----------|
|**Allow Browser**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: esplorazione disabilitata <br>**1**: esplorazione abilitata (impostazione predefinita)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non visualizza i suggerimenti<br> **1**: visualizza i suggerimenti (impostazione predefinita)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: disabilitato, apre i siti Intranet nel browser Microsoft Edge (impostazione predefinita)<br>**1**: abilitato, apre i siti Intranet in Internet Explorer|
|**Allow Do Not Track**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: disabilitato, DNT non inviato (impostazione predefinita)<br> **1**: abilitato, DNT inviato|
|**Configure SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: non consentire<br> **1**: consentito (impostazione predefinita)|
|**Allow Pop-ups**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:<br>** **0**: blocca finestre popup (impostazione predefinita)<br> **1**: consente finestre popup|
|**Allow Cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: consente i cookie provenienti da tutti i siti Web (impostazione predefinita)<br>**1**: blocca solo i cookie di terze parti<br>**2**: blocca tutti i cookie|
|**Allow Save Password**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: lo strumento per la gestione delle password è disabilitato <br>**1**: lo strumento per la gestione delle password è abilitato (impostazione predefinita)|
|**Allow Autofill**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori**:<br> **0**: disabilitato (impostazione predefinita)<br> **1**: abilitato|
|**Configure Enterprise Site List**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:**<br>**0**: non configurato<br>**1**: se configurato, usa l'elenco dei siti della modalità Enterprise di Internet Explorer (impostazione predefinita)<br>**2**: consente di specificare il percorso dell'elenco dei siti Enterprise|

## <a name="general-configuration-policy-settings"></a>Impostazioni dei criteri di configurazione generali

Usare i **criteri di configurazione generale** di Microsoft Intune per Windows 10 per configurare le impostazioni predefinite per dispositivi registrati Windows 10 Desktop e Mobile.

### <a name="password"></a>Password

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Richiedi una password per sbloccare i dispositivi**|-|
|**Tipo di password richiesto**|Specifica se la password deve essere alfanumerica o solo numerica|
|**Tipo di password richiesto** - **Numero minimo di set di caratteri**| Specifica quanti set di caratteri (lettere minuscole, lettere maiuscole, numeri e simboli) devono essere inclusi nella password|
|**Lunghezza minima password**|Si applica solo a Windows 10 Mobile|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**.|Per i dispositivi che eseguono Windows 10: se nel dispositivo è abilitato BitLocker, viene inserita la modalità di ripristino di BitLocker se l'accesso non riesce per il numero di volte specificato. Se nel dispositivo non è abilitato BitLocker, questa impostazione non si applica.<br>Per i dispositivi che eseguono Windows 10 Mobile: se l'accesso non riesce per il numero di volte specificato, il dispositivo viene cancellato.|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica per quanto tempo il dispositivo deve rimanere inattivo prima che lo schermo venga bloccato|
|**Scadenza password (giorni)**|Specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo|
|**Ricorda cronologia password**|Specifica se impedire all'utente di creare password già usate in precedenza|
|**Ricorda cronologia password** - **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare|
|**Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività**|Specifica che l'utente deve inserire una password per sbloccare il dispositivo (solo Windows 10 Mobile)|

### <a name="encryption"></a>Crittografia

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Richiedi crittografia sui dispositivi mobili**|Abilita la crittografia sui dispositivi di destinazione<br>(Solo Windows 10 Mobile)|

### <a name="system"></a>Sistema

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Consenti acquisizione schermo**|Consente all'utente di acquisire la schermata del dispositivo come immagine (solo Windows 10 Mobile).|
|**Consenti l'annullamento della registrazione manuale**|Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.|
|**Consenti installazione manuale del certificato radice**|Si applica a Windows 10 Mobile|
|**Consenti l'invio di dati di utilizzo e di diagnostica a Microsoft**|I valori possibili sono:<br><br>**No** - Non vengono inviati dati a Microsoft<br>**Di base**: vengono inviate a Microsoft informazioni limitate<br>**Avanzati**: vengono inviati a Microsoft dati di diagnostica avanzati<br>**Completi (scelta consigliata)** -Invia gli stessi dati di **Avanzati**, più dati aggiuntivi sullo stato del dispositivo|


### <a name="account-and-synchronization"></a>Account e sincronizzazione

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti account Microsoft**|Consente all'utente di associare un account Microsoft con il dispositivo|
|**Consenti aggiunta manuale di account non Microsoft**|Consente all'utente di aggiungere account di posta elettronica al dispositivo che non sono associati con un account Microsoft|
|**Consenti sincronizzazione delle impostazioni per gli account Microsoft**|Consente che le impostazioni del dispositivo e delle app associate con un account Microsoft vengano sincronizzate fra i dispositivi|

### <a name="microsoft-edge"></a>Microsoft Edge

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Consenti Web browser**|Consente l'uso del Web browser Microsoft Edge sul dispositivo<br>(Solo Windows 10 Mobile)|
|**Consenti suggerimenti di ricerca nella barra degli indirizzi**|Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca|
|**Consenti l'invio di traffico Intranet a Internet Explorer**|Consente agli utenti di aprire siti Web sulla Intranet in Internet Explorer<br>(Solo Windows 10 Desktop)|
|**Consenti Do Not Track**|Configura il browser Microsoft Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti|
|**Attiva SmartScreen**||
|**Consenti scripting**|Consente di eseguire script come Javascript nel browser Microsoft Edge|
|**Consenti popup**|Si applica solo a Windows 10 Desktop|
|**Consenti cookie**||
|**Allow Autofill**|Consente agli utenti di modificare le impostazioni di completamento automatico nel browser<br>(Solo Windows 10 Desktop)|
|**Consenti strumento per la gestione delle password**|Abilita o disabilita la funzione di gestione password di Microsoft Edge|
|**Posizione elenco siti modalità Enterprise**|Specifica dove trovare l'elenco di siti Web che si aprono in modalità Enterprise. L'elenco non è modificabile dagli utenti.<br>(Solo Windows 10 Desktop)|

### <a name="apps"></a>App

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti archivio applicazioni**|Si applica solo a Windows 10 Mobile|



### <a name="cellular"></a>Cellulare

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti roaming dei dati**|Consente il roaming tra reti quando si accede ai dati|
|**Consenti VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è collegato a una rete cellulare|
|**Consenti roaming VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è in roaming su una rete cellulare|

### <a name="hardware"></a>Hardware

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Consenti la fotocamera**|-|
|**Consenti archivi rimovibili**|Specifica se è possibile usare dispositivi di archiviazione esterni come le schede SD con il dispositivo|
|**Consenti Wi-Fi**|Si applica solo a Windows 10 Mobile|
|**Consenti Internet condiviso**|Consente l'uso della condivisione della connessione Internet sul dispositivo|
|**Consenti configurazione Wi-Fi manuale**|Controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi<br>(Solo Windows 10 Mobile)|
|**Consenti connessione automatica agli hotspot Wi-Fi gratuiti**|Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione|
|**Consenti georilevazione**|Specifica se il dispositivo può usare le informazioni dei servizi di posizione|
|**Consenti NFC**|Consente al dispositivo di usare le sue capacità NFC (Near Field Communication)|
|**Consenti Bluetooth**|-|
|**Consenti modalità individuabile Bluetooth**|Consente che il dispositivo sia scoperto da altri dispositivi con la funzione Bluetooth attivata|
|**Consenti annunci con Bluetooth**|Consente ai dispositivi di ricevere annunci tramite Bluetooth|
|**Consenti ripristino del telefono**|Controlla se l'utente può eseguire un ripristino delle impostazioni predefinite nel dispositivo|
|**Consenti connessione USB**|Controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni mediante una connessione USB|
|**Consenti modalità AntiTheft**|Configura se la modalità Antitheft di Windows è abilitata|

### <a name="features"></a>Caratteristiche

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti copia e incolla**|Si applica solo a Windows 10 Mobile|
|**Consenti registrazione vocale**|Si applica solo a Windows 10 Mobile|
|**Consenti Cortana**|Abilita o disabilita l'assistente vocale Cortana|
|**Consenti notifiche del Centro operativo**|Abilita o disabilita le notifiche del Centro operativo sulla schermata di blocco del dispositivo<br>(Solo Windows 10 Mobile)|

### <a name="windows-defender"></a>Windows Defender

Tutte le impostazioni sono solo per Windows 10 Desktop.

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti monitoraggio in tempo reale**|Abilita l'analisi in tempo reale per malware, spyware e altro software indesiderato|
|**Consenti monitoraggio comportamento**|Consente a Defender di controllare la presenza di modelli noti di attività sospette nei dispositivi|
|**Abilita Network Inspection System**|Network Inspection System (NIS) contribuisce a proteggere i dispositivi dagli exploit basati sulla rete usando le firme di vulnerabilità note di Microsoft Endpoint Protection Center per contribuire a rilevare e bloccare il traffico dannoso|
|**Analizza tutti i download**|Controlla se Defender deve analizzare tutti i file scaricati da Internet|
|**Consenti analisi script**|Consente a Defender di analizzare gli script usati in Internet Explorer|
|**Monitora l'attività di file e programmi**|Consente a Defender di monitorare l'attività di file e programmi nei dispositivi|
|**Giorni di rilevamento del malware risolto**|Consente a Defender di continuare a monitorare il malware risolto per il numero di giorni specificato, in modo che sia possibile controllare manualmente i dispositivi colpiti in precedenza. Se si imposta il numero di giorni su **0**, il malware rimane nella cartella della quarantena e non viene rimosso automaticamente. |
|**Consenti accesso all'interfaccia utente client**|Controlla se l'interfaccia utente di Windows Defender è nascosta agli utenti.<br>Quando questa impostazione viene modificata, ha effetto dal successivo avvio del PC da parte dell'utente.|
|**Pianifica analisi veloce giornaliera**|Consente di pianificare un'analisi veloce che viene eseguita giornalmente all'ora selezionata|
|**Pianifica analisi del sistema**|Consente di pianificare un'analisi completa o veloce del sistema che si verifica regolarmente il giorno e all'ora selezionati|
|**Limita utilizzo CPU durante un'analisi a**|Consente di limitare la quantità di CPU usata per le analisi (da **1** a **100**)|
|**Analizza file di archivio**|Consente a Defender di analizzare i file archiviati come i file con estensione zip o cab.|
|**Analisi dei messaggi di posta elettronica**|Consente a Defender di analizzare i messaggi di posta elettronica non appena arrivano sul dispositivo|
|**Analizza unità rimovibili**|Consente a Defender di analizzare le unità rimovibili, ad esempio le chiavette USB|
|**Analizza unità di rete mappate**|Consente a Defender di analizzare i file nelle unità di rete mappate.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|
|**Analizza file aperti da cartelle di rete condivise**|Consente a Defender di analizzare i file sulle unità di rete condivise, ad esempio quelli a cui si accede da un percorso UNC.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|
|**Intervallo di aggiornamento della firma**|Specifica l'intervallo in base a cui Defender controlla la presenza di nuovi file di firma.|
|**Consenti protezione cloud**|Consente o blocca la ricezione di informazioni sull'attività del malware da parte di Microsoft Active Protection Service dai dispositivi gestiti. Queste informazioni vengono usate per migliorare il servizio in futuro.|
|**Richiedi invio dei campioni agli utenti**|Controlla se i file che potrebbero richiedere ulteriore analisi da parte di Microsoft per determinare se sono dannosi vengono inviati automaticamente a Microsoft|
|**Rilevamento di applicazioni potenzialmente indesiderate**|Protegge i dispositivi desktop Windows registrati da eventuale software in esecuzione classificato da Windows Defender come potenzialmente indesiderato. È possibile ottenere protezione da tali applicazioni in esecuzione o usare la modalità di controllo per rilevare l'installazione di un'applicazione potenzialmente indesiderata.|
|**File e cartelle da escludere quando si esegue un'analisi o si usa la protezione in tempo reale**|Aggiunge uno o più file e cartelle come **C:\Percorso** o **%ProgramFiles%\Percorso\nomefile.exe** all'elenco di esclusione. Questi file e cartelle non sono inclusi nelle analisi in tempo reale o pianificate.|
|**Estensioni di file da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiungere uno o più estensioni di file come **jpg** o **txt** all'elenco delle esclusioni. I file con queste estensioni non sono inclusi nelle analisi in tempo reale o pianificate.|
|**Processi da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiunge uno o più processi del tipo **.exe**, **.com** o **.scr** all'elenco di esclusione. Questi processi non sono inclusi nelle analisi in tempo reale o pianificate.|


### <a name="updates"></a>Updates

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|---------------|
|**Consenti aggiornamenti automatici**|Consente gli aggiornamenti automatici. Configurare una delle impostazioni seguenti per controllare il comportamento di aggiornamento:<br />**Notifica download**<br />**Installa automaticamente durante la manutenzione**<br />**Installa e riavvia automaticamente durante la manutenzione**<br />**Installa e riavvia automaticamente all'ora pianificata**: tenere presente che quando è selezionata questa opzione è possibile configurare anche le impostazioni seguenti: **Elimina la notifica per l'utente finale** e **Definire il giorno di installazione per gli aggiornamenti pianificati**.<br>(Solo Windows 10 Desktop)|
|**Consenti funzionalità di versioni non definitive**|Consente a Microsoft di distribuire le impostazioni e le funzionalità della versione non definitiva nei dispositivi Windows 10. È possibile consentire l'installazione delle sole impostazioni oppure di tutte le impostazioni e le funzionalità della versione non definitiva.|

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO4-->


