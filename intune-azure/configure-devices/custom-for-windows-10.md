---
title: Impostazioni personalizzate di Intune per dispositivi Windows 10
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 647415914fb0f44807eff7baf7a56ea3a382f027
ms.lasthandoff: 02/18/2017


---

# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Impostazioni personalizzate per i dispositivi Windows 10 in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 Usare il profilo **personalizzato** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows 10 rende disponibili molte impostazioni tramite il [provider del servizio di configurazione dei criteri](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](how-to-configure-custom-settings.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** scegliere **Impostazioni** per aggiungere una o più impostazioni URI OMA.
3. Nel pannello **Impostazioni OMA-URI personalizzate** fare clic su **Aggiungi** per aggiungere un nuovo valore. È anche possibile fare clic su **Esporta** per creare un elenco di tutti i valori configurati in un file con valori delimitati da virgole (estensione CSV).
4. Per ogni impostazione URI OMA che si vuole aggiungere, immettere le informazioni seguenti. Usare l'elenco in questo argomento per informazioni sulle impostazioni che è possibile usare:
    - **Nome impostazione**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione impostazione**: immettere facoltativamente una descrizione per l'impostazione.
    - **Tipo di dati**: scegliere tra:
        - **Stringa**
        - **Stringa (XML)**
        - **Data e ora**
        - **Intero**
        - **A virgola mobile**
        - **Booleano**
    - **URI OMA (maiuscole/minuscole)**: specificare l'impostazione URI OMA per cui si vuole fornire un'impostazione.
    - **Valore**: specificare il valore da associare all'impostazione URI OMA specificata.
5. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.
Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="example"></a>Esempio
Nella schermata seguente è stata abilitata l'impostazione **Connectivity/AllowVPNOverCellular**. Ciò consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

> ![Esempio di un criterio personalizzato contenente le impostazioni VPN](./media/custom-policy-example.png)


## <a name="policy-settings"></a>Impostazioni criteri

|Nome e URI criteri|Dettagli|
|---------------|------------|-----------|
|**Allow Auto Update**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Solo Desktop<br>**Tipo di dati:** Integer<br />**Valori:** **0** - **5** (predefinito: **1**)|
|**Schedule Install Day**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Solo Mobile<br>**Tipo di dati:** Integer<br />**Valori:**<br>**0** - Tutti i giorni (impostazione predefinita)<br>**1** - domenica<br>**2** - lunedì<br>**3** - martedì<br>**4** - mercoledì<br>**5** - giovedì<br>**6** - venerdì<br>**7** - sabato|
|**Schedule Install Time**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0** – **23** ore **0** corrisponde a mezzanotte) (predefinito: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: l'utente non può impostare il timer del periodo di tolleranza della password; il valore è impostato su "ogni ora"<br>**1**: l'utente può impostare il timer del periodo di tolleranza della password (impostazione predefinita)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consente **l'uso della connessione Wi-Fi**.<br>**1**: **consente l'uso della connessione Wi-Fi** (impostazione predefinita)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Desktop e Mobile<br>**Tipo di dati:** Integer<br />**Valori:** **0**: non consente la condivisione Internet, **1**: consente la condivisione Internet (impostazione predefinita)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non sono consentite connessioni Wi-Fi oltre a quelle con provisioning MDM.<br>**1**: consente l'aggiunta di nuovi SSID di rete oltre a quelli con provisioning MDM (impostazione predefinita)|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Desktop e Mobile<br>**Tipo di dati:** Integer<br />**Valori:**<br>**0** : non consentito (solo impostazione aziendale)<br>**1** : limitato<br>**2**: completo (impostazione predefinita)<br>**3**: completo e informazioni sulla diagnostica|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** : non consentito<br>**1**: solo impostazioni (impostazione predefinita)<br>**2**: impostazioni e sperimentazione|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consente la modalità AntiTheft<br>**1**: preferenza utente (impostazione predefinita)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: la VPN non è consentita sulla connessione cellulare<br>**1**: la VPN può usare qualsiasi connessione, inclusa la connessione cellulare (impostazione predefinita)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non consente all'utente di attivare la funzione Bluetooth.<br>**1**: riservato. L'utente può attivare e configurare la funzione Bluetooth (non supportato in Windows Phone 8.1 per MDM, EAS, Windows 10 Desktop o Windows 10 Mobile)<br>**2**: consentito. L'utente può attivare e configurare la funzione Bluetooth (impostazione predefinita)|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consente il roaming, **1**: consente il roaming (impostazione predefinita)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0** (impostazione predefinita), **1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**, **1** (impostazione predefinita)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0** (impostazione predefinita), **1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0** (impostazione predefinita), **1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0** (impostazione predefinita), **1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**, **1** (impostazione predefinita)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0** (impostazione predefinita), **1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0** (impostazione predefinita), **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** : non consente<br>Open Extended Dictionary è disattivato.<br>Un utente non può:<br>-Aggiungere un nuovo Open Extended Dictionary<br />-Aggiungere un nuovo file di configurazione di integrazione di ricerca<br>-Usare la funzionalità per i candidati dal cloud<br>-Inviare parole registrate dall'utente.<br>**1**: consenti<br>Open Extended Dictionary può essere aggiunto e usato per impostazione predefinita. Inoltre, la funzione di integrazione ricerca può essere usata per impostazione predefinita.<br>Un utente può:<br>Usare la funzionalità per i candidati dal cloud.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: la registrazione di conversioni errate è disabilitata<br>**1**: la registrazione di conversioni errate è abilitata (impostazione predefinita)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito **1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri Shift JIS|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br />**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri JIS0208|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri JIS0208 o EUDC|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** : rigido, filtro massimo del contenuto per adulti<br>**1**: moderato, filtro moderato del contenuto per adulti, i risultati di ricerca validi non verranno filtrati (impostazione predefinita)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Force Start Size**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: consente all'utente di modificare le dimensioni (impostazione predefinita)<br>**1**: forza la modalità non a schermo non intero<br>**2**: forza la modalità a schermo intero|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non rinvia l'aggiornamento, rimane nel Current Branch, CB (impostazione predefinita)<br>**1**: abilita il rinvio degli aggiornamenti (il dispositivo segue le regole del Current Branch for Business, CBB)<br />Per informazioni dettagliate, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Pianificare la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Desktop e Mobile<br>**Descrizione:** criterio per rinviare gli aggiornamenti software per un massimo di 4 settimane<br />**Tipo di dati:** Integer<br />**Valori:**<br> **0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**-**4**: numero di settimane di rinvio degli aggiornamenti software.<br />Per informazioni dettagliate, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Pianificare la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Desktop e Mobile<br>**Descrizione:** criterio per rinviare gli aggiornamenti delle funzionalità per un massimo di 8 mesi<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**-**8**: numero di mesi di rinvio degli aggiornamenti delle funzionalità.<br />Per informazioni dettagliate, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Pianificare la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Desktop e Mobile<br>**Descrizione:** consente a un dispositivo di non ricevere più gli aggiornamenti per 5 settimane.<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**: sospendi gli aggiornamenti (scade dopo 5 settimane)|

## <a name="windows-defender-settings"></a>Impostazioni di Windows Defender

|Nome e URI criteri|Dettagli|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: monitora tutti i file (impostazione predefinita)<br>**1** : esegue il monitoraggio dei file in ingresso<br>**2** : esegue il monitoraggio dei file in uscita|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** - **90**: indica il malware conservato e il periodo di conservazione<br>**Predefinito:** **0**: mantiene sempre nella cartella della quarantena e non rimuove automaticamente|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**1**: analisi veloce (impostazione predefinita)<br>**2**: analisi completa|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: tutti i giorni (impostazione predefinita)<br>**1**: lunedì<br>**2**: martedì<br>**3**: mercoledì<br>**4**: giovedì<br>**5**: venerdì<br>**6**: sabato<br>**7**: domenica<br>**8** : nessuna analisi pianificata|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0** – 12:00<br>**60** – 1:00<br>**120** – 2:00 (impostazione predefinita)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1381** -Finestra di manutenzione|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Solo Desktop<br>**Tipo di dati:** Integer<br />**Valori:**<br>**0** – 12:00<br>**60** – 1:00<br>**120** – 2:00 (impostazione predefinita)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1380** – 22:00|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0** - **100** (impostazione predefinita: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Solo Desktop<br />**Tipo di dati:** Integer<br>**Valori:** **0**: non consentito (impostazione predefinita), **1**: consentito|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito (impostazione predefinita), **1**: consentito|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita). Se impostato su consentito, viene eseguito anche quando RTP è attivo|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: non controlla le firme in un intervallo<br>**1**: controlla le firme ogni ora<br>**2**: controlla ogni 2 ore e così via<br>**24**: controlla tutti i giorni<br>**Valore predefinito:** 8: controlla ogni 8 ore|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: richiedere sempre (impostazione predefinita)<br>**1** : inviare campioni sicuri automaticamente<br>**2** : non inviare mai<br>**3** : inviare tutti i campioni automaticamente|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:**<br>*&lt;elenco di estensioni separate da punto e virgola&gt;* ad esempio **obj;lib**<br>**Valore predefinito:** nessuna estensione viene esclusa|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:**<br />*&lt;elenco di percorsi separati da punto e virgola&gt;*<br />Esempio: **c:\test;c:\test1.exe**<br />**Valore predefinito:** nessun percorso viene escluso|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:**<br>*&lt;elenco di percorsi separati da punto e virgola&gt;*<br>Esempio: **c:\test.exe;c:\test1.exe**<br>**Valore predefinito:** nessun processo viene escluso|

## <a name="edge-browser-settings"></a>Impostazioni del browser Edge

|Nome e URI criteri|Dettagli|
|---------------|------------|-----------|
|**Allow Browser**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Solo Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: esplorazione disabilitata, **1**: esplorazione abilitata (impostazione predefinita)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non mostrare suggerimenti, **1**: mostra suggerimenti (impostazione predefinita)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**:  disabilitato, apre i siti Intranet nel browser Microsoft Edge (impostazione predefinita)<br>**1**: abilitato, apre i siti Intranet in Internet Explorer.|
|**Allow Do Not Track**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: disabilitato (DNT non inviato), **1**: abilitato (invia DNT)|
|**Configure SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:** **0**: non consentito, **1**: consentito (impostazione predefinita)|
|**Allow Pop-ups**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: blocca popup (impostazione predefinita), **1**: consenti popup|
|**Allow Cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: consente i cookie provenienti da tutti i siti Web (impostazione predefinita)<br>**1**: blocca solo i cookie di terze parti<br>**2**: blocca tutti i cookie|
|**Allow Save Password**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Desktop e Mobile<br />**Tipo di dati:** Integer<br />**Valori:**<br>**0**: lo strumento per la gestione delle password è disabilitato; <br>**1**: lo strumento per la gestione delle password è abilitato (impostazione predefinita)|
|**Allow Autofill**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Solo Desktop<br />**Tipo di dati:** Integer<br />**Valori:** **0**: disabilitato (impostazione predefinita), **1**: abilitato|
|**Configure Enterprise Site List**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Solo Desktop<br />**Tipo di dati:** stringa<br />**Valori:<br>**0**: non configurato<br>**1**: usa l'elenco dei siti della modalità Enterprise di IE se è configurato (impostazione predefinita)<br>**2**: consente di specificare il percorso dell'elenco dei siti della modalità Enterprise|

