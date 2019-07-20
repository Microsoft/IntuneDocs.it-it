---
title: API Graph per configurare i dispositivi in Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Vedere un elenco di tutte le entità API Graph con l'URI di offset e di offset Windows corrispondente nei dispositivi Windows 10 e le versioni più recenti usate per la configurazione dei dispositivi in Microsoft Intune. Vedere l'API e il CSP corrispondenti per i PC condivisi, Endpoint Protection, Windows Defender Advanced Threat Protection, Identity Protection, Windows 10 teams, Kiosk e Windows Update for business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3732a4539c13ad05ae8c95621246429b7f38987e
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354412"
---
# <a name="graph-apis-and-matching-windows-10-csps-used-in-intune"></a>API Graph e corrispondenti CSP di Windows 10 usati in Intune

Microsoft Intune usa le [entità API Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview) (apre un altro sito docs) per configurare i dispositivi (**configurazione del dispositivo** **Intune** > ) che eseguono Windows 10 e versioni successive. Il API Graph usa i provider di servizi di configurazione (CSP) per leggere, impostare, modificare e/o eliminare le impostazioni di configurazione nei dispositivi.

Questo elenco si applica a:

- Windows 10 e versioni successive

Questo articolo elenca le entità Graph e gli URI di offset e i CSP Windows 10 corrispondenti.

Queste informazioni sono utili per diversi scenari. Vedere ad esempio gli elementi usati da Intune, vedere le impostazioni da includere nelle configurazioni URI OMA personalizzate e così via. 

## <a name="windows-10-csps"></a>CSP di Windows 10

Per ulteriori informazioni sui provider di servizi di configurazione Windows 10, vedere la Guida di [riferimento del provider di servizi di configurazione](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (apre un altro sito docs).

## <a name="graph-api-properties-to-csp-mapping"></a>API Graph le proprietà al mapping CSP

Nell'elenco seguente viene illustrata la maggior parte delle entità API Graph utilizzate da Microsoft Intune per la configurazione del dispositivo Windows 10. Mostra anche l'URI di offset e CSP di Windows 10 corrispondente.

Per visualizzare le versioni di Windows 10 a cui si applicano le seguenti API, usare il [riferimento del provider di servizi di configurazione](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) Windows 10 (apre un altro sito docs).

### <a name="editionupgradeconfigurationlicense"></a>EditionUpgradeConfiguration.License 
**CSP**:./Device/vendor/MSFT/WindowsLicensing  
**URI offset**:/UpgradeEditionWithLicense

### <a name="editionupgradeconfigurationlicensetype"></a>EditionUpgradeConfiguration.LicenseType 
**CSP**:./Device/vendor/MSFT/WindowsLicensing  
**URI offset**:/LicenseKeyType

### <a name="editionupgradeconfigurationproductkey"></a>EditionUpgradeConfiguration.ProductKey 
**CSP**:./Device/vendor/MSFT/WindowsLicensing  
**URI offset**:/UpgradeEditionWithProductKey

### <a name="editionupgradeconfigurationwindowssmode"></a>EditionUpgradeConfiguration.WindowsSMode 
**CSP**:./Device/vendor/MSFT/WindowsLicensing  
**URI offset**:/SMode/SwitchingPolicy

### <a name="sharedpcconfigurationaccountmanagerpolicy"></a>SharedPCConfiguration.AccountManagerPolicy 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/DeletionPolicy,/DiskLevelCaching,/InactiveThreshold,/DiskLevelDeletion

### <a name="sharedpcconfigurationaccountmanagerpolicy-windows-holographic-for-business-edition-targeted-devices"></a>SharedPCConfiguration. AccountManagerPolicy (dispositivi di destinazione Windows Olografic for Business Edition) 
**CSP**:./Vendor/MSFT/AccountManagement  
**URI offset**:/DeletionPolicy,/StorageCapacityStartDeletion,/StorageCapacityStopDeletion,/ProfileInactivityThreshold

### <a name="sharedpcconfigurationallowedaccounts"></a>SharedPCConfiguration.AllowedAccounts 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/AccountModel

### <a name="sharedpcconfigurationallowlocalstorage"></a>SharedPCConfiguration.AllowLocalStorage 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/RestrictLocalStorage

### <a name="sharedpcconfigurationdisableaccountmanager"></a>SharedPCConfiguration.DisableAccountManager 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/EnableAccountManager

### <a name="sharedpcconfigurationdisableedupolicies"></a>SharedPCConfiguration.DisableEduPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/SetEduPolicies

### <a name="sharedpcconfigurationdisablepowerpolicies"></a>SharedPCConfiguration.DisablePowerPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/SetPowerPolicies

### <a name="sharedpcconfigurationdisablesigninonresume"></a>SharedPCConfiguration.DisableSignInOnResume 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/SignInOnResume

### <a name="sharedpcconfigurationenabled"></a>SharedPCConfiguration.Enabled 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/EnableSharedPCMode

### <a name="sharedpcconfigurationidletimebeforesleepinseconds"></a>SharedPCConfiguration.IdleTimeBeforeSleepInSeconds 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/InactiveThreshold

### <a name="sharedpcconfigurationkioskappdisplayname"></a>SharedPCConfiguration.KioskAppDisplayName 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/KioskModeUserTileDisplayText

### <a name="sharedpcconfigurationkioskappusermodelid"></a>SharedPCConfiguration.KioskAppUserModelId 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/KioskModeAUMID

### <a name="sharedpcconfigurationlocalstorage"></a>SharedPCConfiguration.LocalStorage 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/RestrictLocalStorage

### <a name="sharedpcconfigurationmaintenancestarttime"></a>SharedPCConfiguration.MaintenanceStartTime 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/MaintenanceStartTime

### <a name="sharedpcconfigurationsetaccountmanager"></a>SharedPCConfiguration.SetAccountManager
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/EnableAccountManager

### <a name="sharedpcconfigurationsetedupolicies"></a>SharedPCConfiguration.SetEduPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/SetEduPolicies

### <a name="sharedpcconfigurationsetpowerpolicies"></a>SharedPCConfiguration.SetPowerPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/SetPowerPolicies

### <a name="sharedpcconfigurationsigninonresume"></a>SharedPCConfiguration.SignInOnResume 
**CSP**:./Vendor/MSFT/SharedPC  
**URI offset**:/SignInOnResume

### <a name="windows10endpointconfigurationsmartscreenblockoverrideforfiles"></a>Windows10endpointconfiguration.smartScreenBlockOverrideForFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/SmartScreen/PreventOverrideForFilesInShell

### <a name="windows10endpointprotectionconfigurationapplicationguardallowfilesaveonhost"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowFileSaveOnHost 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/SaveFilesToHost

### <a name="windows10endpointprotectionconfigurationapplicationguardallowpersistence"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPersistence 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/AllowPersistence

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttolocalprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToLocalPrinters 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttonetworkprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToNetworkPrinters 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttopdf"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToPDF 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttoxps"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToXPS 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowvirtualgpu"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowVirtualGPU 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/AllowVirtualGPU

### <a name="windows10endpointprotectionconfigurationapplicationguardblockclipboardsharing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockClipboardSharing 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/ClipboardSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardblockfiletransfer"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockFileTransfer 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/ClipboardFileType

### <a name="windows10endpointprotectionconfigurationapplicationguardblocknonenterprisecontent"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockNonEnterpriseContent 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/BlockNonEnterpriseContent

### <a name="windows10endpointprotectionconfigurationapplicationguardenabled"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardEnabled 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/Settings/AllowWindowsDefenderApplicationGuard

### <a name="windows10endpointprotectionconfigurationapplicationguardforceauditing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardForceAuditing 
**CSP**:./Device/vendor/MSFT/WindowsDefenderApplicationGuard  
**URI offset**:/audit/AuditApplicationGuard

### <a name="windows10endpointprotectionconfigurationbitlockerallowstandarduserencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerAllowStandardUserEncryption 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI offset**:/AllowStandardUserEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerdisablewarningforotherdiskencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerDisableWarningForOtherDiskEncryption 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI offset**:/AllowWarningForOtherDiskEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerenablestoragecardencryptiononmobile"></a>Windows10EndpointProtectionConfiguration.BitLockerEnableStorageCardEncryptionOnMobile 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI offset**:/RequireStorageCardEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerencryptdevice"></a>Windows10EndpointProtectionConfiguration.BitLockerEncryptDevice 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI offset**:/RequireDeviceEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerfixeddrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerFixedDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI offset**:/EncryptionMethodByDriveType,/FixedDrivesRequireEncryption,/FixedDrivesRecoveryOptions

### <a name="windows10endpointprotectionconfigurationbitlockerremovabledrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerRemovableDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI offset**:/EncryptionMethodByDriveType,/RemovableDrivesRequireEncryption

### <a name="windows10endpointprotectionconfigurationbitlockersystemdrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerSystemDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI offset**:/EncryptionMethodByDriveType,/SystemDrivesRequireStartupAuthentication,/SystemDrivesMinimumPINLength,/SystemDrivesRecoveryMessage,/SystemDrivesRecoveryOptions

### <a name="windows10endpointprotectionconfigurationclientconnectionencryptionlevel"></a>windows10endpointprotectionconfiguration.clientConnectionEncryptionLevel 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteDesktopServices/ClientConnectionEncryptionLevel

### <a name="windows10endpointprotectionconfigurationconfiguresmbv1clientdriver"></a>windows10endpointprotectionconfiguration.configureSMBV1ClientDriver 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSecurityGuide/ConfigureSMBV1ClientDriver

### <a name="windows10endpointprotectionconfigurationconnectivitydownloadingofprintdriversoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityDownloadingOfPrintDriversOverHttp 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/DisableDownloadingOfPrintDriversOverHTTP

### <a name="windows10endpointprotectionconfigurationconnectivityhardeneduncpaths"></a>Windows10EndpointProtectionConfiguration.ConnectivityHardenedUncPaths 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/HardenedUNCPaths

### <a name="windows10endpointprotectionconfigurationconnectivityinternetdownloadforwebpublishingandonlineorderingwizards"></a>Windows10EndpointProtectionConfiguration.ConnectivityInternetDownloadForWebPublishingAndOnlineOrderingWizards 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/DisableInternetDownloadForWebPublishingAndOnlineOrderingWizards

### <a name="windows10endpointprotectionconfigurationconnectivityprintingoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityPrintingOverHttp 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/DiablePrintingOverHTTP

### <a name="windows10endpointprotectionconfigurationcredentialsuienumerateadministrators"></a>Windows10EndpointProtectionConfiguration.CredentialsUIEnumerateAdministrators 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/CredentialsUI/EnumerateAdministrators

### <a name="windows10endpointprotectionconfigurationdefenderadditionalguardedfolders"></a>Windows10EndpointProtectionConfiguration.DefenderAdditionalGuardedFolders 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/Defender/ControlledFolderAccessProtectedFolders

### <a name="windows10endpointprotectionconfigurationdefenderadvancedransomewareprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderAdvancedRansomewareProtectionType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderattacksurfacereductionexcludedpaths"></a>Windows10EndpointProtectionConfiguration.DefenderAttackSurfaceReductionExcludedPaths 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionOnlyExclusions

### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecution"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecution 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowEmailScanning

### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecutionType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxml"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXml 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/ExploitGuard/ExploitProtectionSettings

### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxmlfilename"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXmlFileName 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/ExploitGuard/ExploitProtectionSettings

### <a name="windows10endpointprotectionconfigurationdefenderguardedfoldersallowedapppaths"></a>Windows10EndpointProtectionConfiguration.DefenderGuardedFoldersAllowedAppPaths 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/Defender/ControlledFolderAccessAllowedApplications

### <a name="windows10endpointprotectionconfigurationdefenderguardmyfolderstype"></a>Windows10EndpointProtectionConfiguration.DefenderGuardMyFoldersType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/EnableControlledFolderAccess

### <a name="windows10endpointprotectionconfigurationdefendernetworkprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderNetworkProtectionType 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/Defender/EnableNetworkProtection

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunch"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunch 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunchtype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunchType
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocess"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcess 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcessType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjection"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjectionType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType 

### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32imports"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32Imports 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32importstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32ImportsType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderpreventcredentialstealingtype"></a>Windows10EndpointProtectionConfiguration.DefenderPreventCredentialStealingType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderprocesscreation"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreation 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderprocesscreationtype"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreationType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderprotectagainstpotentiallyunwantedapplications"></a>Windows10EndpointProtectionConfiguration.DefenderProtectAgainstPotentiallyUnwantedApplications 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSecurityGuide/TurnOnWindowsDefenderProtectionAgainstPotentiallyUnwantedApplications

### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecution"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecution 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecutionType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocode"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocodetype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCodeType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterblockexploitprotectionoverride"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterBlockExploitProtectionOverride 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableaccountui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAccountUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/DisableAccountProtectionUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableappbrowserui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAppBrowserUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/DisableAppBrowserUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablefamilyui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableFamilyUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/DisableFamilyUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablehealthui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableHealthUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/DisableHealthUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablenetworkui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableNetworkUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/DisableNetworkUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablesecurebootui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableSecureBootUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/HideSecureBoot

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisabletroubleshootingui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableTroubleshootingUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/HideTPMTroubleshooting

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablevirusui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableVirusUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/DisableVirusUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpemail"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpEmail 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/email

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpphone"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpPhone 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/Phone

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpurl"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpURL 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/URL

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenteritcontactdisplay"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterITContactDisplay 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/WindowsDefenderSecurityCenter/EnableCustomizedToasts,/WindowsDefenderSecurityCenter/EnableInAppCustomization

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenternotificationsfromapp"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterNotificationsFromApp 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/HideWindowsSecurityNotificationAreaControl

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterorganizationdisplayname"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterOrganizationDisplayName 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsDefenderSecurityCenter/CompanyName

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutable"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutable 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutabletype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutableType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocess"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcess 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcessType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI di offset**:/config/Defender/ATTACKSURFACEREDUCTIONRULES (CSP/Configuration richiede proprietà del grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdeviceguardenablesecurebootwithdma"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableSecureBootWithDMA 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceGuard/RequirePlatformSecurityFeatures

### <a name="windows10endpointprotectionconfigurationdeviceguardenablevirtualizationbasedsecurity"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableVirtualizationBasedSecurity 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/DeviceGuard/EnableVirtualizationBasedSecurity

### <a name="windows10endpointprotectionconfigurationdeviceguardlaunchsystemguard"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLaunchSystemGuard 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceGuard/ConfigureSystemGuardLaunch

### <a name="windows10endpointprotectionconfigurationdeviceguardlocalsystemauthoritycredentialguardsettings"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLocalSystemAuthorityCredentialGuardSettings 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceGuard/LsaCfgFlags

### <a name="windows10endpointprotectionconfigurationdmaguarddeviceenumerationpolicy"></a>Windows10EndpointProtectionConfiguration.DmaGuardDeviceEnumerationPolicy 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DmaGuard/DeviceEnumerationPolicy

### <a name="windows10endpointprotectionconfigurationeventlogserviceapplicationlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceApplicationLogMaximumFileSizeInKb 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/EventLogService/SpecifyMaximumFileSizeApplicationLog

### <a name="windows10endpointprotectionconfigurationeventlogservicesecuritylogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSecurityLogMaximumFileSizeInKb 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/EventLogService/SpecifyMaximumFileSizeSecurityLog

### <a name="windows10endpointprotectionconfigurationeventlogservicesystemlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSystemLogMaximumFileSizeInKb 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/EventLogService/SpecifyMaximumFileSizeSystemLog

### <a name="windows10endpointprotectionconfigurationexplorerdataexecutionprevention"></a>Windows10EndpointProtectionConfiguration.ExplorerDataExecutionPrevention 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/FileExplorer/TurnOffDataExecutionPreventionForExplorer

### <a name="windows10endpointprotectionconfigurationexplorerheapterminationoncorruption"></a>Windows10EndpointProtectionConfiguration.ExplorerHeapTerminationOnCorruption 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/FileExplorer/TurnOffHeapTerminationOnCorruption

### <a name="windows10endpointprotectionconfigurationfirewallblockstatefulftp"></a>Windows10EndpointProtectionConfiguration.FirewallBlockStatefulFTP 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/DisableStatefulFtp

### <a name="windows10endpointprotectionconfigurationfirewallcertificaterevocationlistcheckmethod"></a>Windows10EndpointProtectionConfiguration.FirewallCertificateRevocationListCheckMethod 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/CRLcheck

### <a name="windows10endpointprotectionconfigurationfirewallidletimeoutforsecurityassociationinseconds"></a>Windows10EndpointProtectionConfiguration.FirewallIdleTimeoutForSecurityAssociationInSeconds 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/SaIdleTime

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowdhcp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowDHCP 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowicmp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowICMP 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowneighbordiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowNeighborDiscovery 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowrouterdiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowRouterDiscovery 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallmergekeyingmodulesettings"></a>Windows10EndpointProtectionConfiguration.FirewallMergeKeyingModuleSettings 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/OpportunisticallyMatchAuthSetPerKM

### <a name="windows10endpointprotectionconfigurationfirewallpacketqueueingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPacketQueueingMethod 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/EnablePacketQueue

### <a name="windows10endpointprotectionconfigurationfirewallpresharedkeyencodingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPreSharedKeyEncodingMethod 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/MdmStore/Global/PresharedKeyEncoding

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomain"></a>Windows10EndpointProtectionConfiguration.FirewallProfileDomain 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/EnableFirewall,/DisableStealthMode,/Shielded,/DisableUnicastResponsesToMulticastBroadcast,/DisableInboundNotifications,/AuthAppsAllowUserPrefMerge,/GlobalPortsAllowUserPrefMerge,/AllowLocalPolicyMerge,/ DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundConnectionsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/domainprofile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/domainprofile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/domainprofile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomainoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.outboundConnectionsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/domainprofile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivate"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePrivate 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/EnableFirewall,/DisableStealthMode,/Shielded,/DisableUnicastResponsesToMulticastBroadcast,/DisableInboundNotifications,/AuthAppsAllowUserPrefMerge,/GlobalPortsAllowUserPrefMerge,/AllowLocalPolicyMerge,/ DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivatefirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.firewallEnabled 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PrivateProfile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundConnectionsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PrivateProfile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundNotificationsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PrivateProfile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.outboundConnectionsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PrivateProfile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublic"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePublic 
**CSP**:./Vendor/MSFT/firewall  
**URI offset**:/EnableFirewall,/DisableStealthMode,/Shielded,/DisableUnicastResponsesToMulticastBroadcast,/DisableInboundNotifications,/AuthAppsAllowUserPrefMerge,/GlobalPortsAllowUserPrefMerge,/AllowLocalPolicyMerge,/ DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicconnectionsecurityrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.connectionSecurityRulesFromGroupPolicyMerged 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PublicProfile/AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicfirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.firewallEnabled 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PublicProfile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundConnectionsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PublicProfile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundNotificationsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PublicProfile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.outboundConnectionsBlocked 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PublicProfile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicpolicyrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.policyRulesFromGroupPolicyMerged 
**CSP**:./Device/vendor/MSFT/firewall  
**URI offset**:/MdmStore/PublicProfile/AllowLocalPolicyMerge

### <a name="windows10endpointprotectionconfigurationlanmanagerauthenticationlevel"></a>Windows10EndpointProtectionConfiguration.LanManagerAuthenticationLevel 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkSecurity\_LANManagerAuthenticationLevel

### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationdisableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationDisableInsecureGuestLogons 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LanmanWorkstation/EnableInsecureGuestLogons

### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationenableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationEnableInsecureGuestLogons 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LanmanWorkstation/EnableInsecureGuestLogons

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratoraccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorAccountName 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_RenameAdministratorAccount

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratorelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorElevationPromptBehavior
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_BehaviorOfTheElevationPromptForAdministrators

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowanonymousenumerationofsamaccountsandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowAnonymousEnumerationOfSAMAccountsAndShares 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowpku2uauthenticationrequests"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowPKU2UAuthenticationRequests 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkSecurity\_AllowPKU2UAuthenticationRequests

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanager"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManager 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanagerhelperbool"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManagerHelperBool 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowsystemtobeshutdownwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowSystemToBeShutDownWithoutHavingToLogOn 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Shutdown\_AllowSystemToBeShutDownWithoutHavingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationElevation 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_AllowUIAccessApplicationsToPromptForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationsforsecurelocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationsForSecureLocations 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowundockwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUndockWithoutHavingToLogon 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Devices\_AllowUndockWithoutHavingToLogon

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockmicrosoftaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockMicrosoftAccounts 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_BlockMicrosoftAccounts

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremotelogonwithblankpassword"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteLogonWithBlankPassword 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremoteopticaldriveaccess"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteOpticalDriveAccess 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Devices\_RestrictCDROMAccessToLocallyLoggedOnUserOnly

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockusersinstallingprinterdrivers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockUsersInstallingPrinterDrivers 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Devices\_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclearvirtualmemorypagefile"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClearVirtualMemoryPageFile 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Shutdown\_ClearVirtualMemoryPageFile

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientDigitallySignCommunicationsAlways 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsAlways

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientsendunencryptedpasswordtothirdpartysmbservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientSendUnencryptedPasswordToThirdPartySMBServers 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_SendUnencryptedPasswordToThirdPartySMBServers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdetectapplicationinstallationsandpromptforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDetectApplicationInstallationsAndPromptForElevation 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_DetectApplicationInstallationsAndPromptForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableAdministratorAccount 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_EnableAdministratorAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableclientdigitallysigncommunicationsifserveragrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableClientDigitallySignCommunicationsIfServerAgrees 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsIfServerAgrees

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableGuestAccount 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_EnableGuestAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsAlways 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsAlways

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsifclientagrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsIfClientAgrees 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsIfClientAgrees

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotallowanonymousenumerationofsamaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotAllowAnonymousEnumerationOfSAMAccounts 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSAMAccounts

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotrequirectrlaltdel"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotRequireCtrlAltDel 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotRequireCTRLALTDEL

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotstorelanmanagerhashvalueonnextpasswordchange"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotStoreLANManagerHashValueOnNextPasswordChange 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkSecurity\_DoNotStoreLANManagerHashValueOnNextPasswordChange

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableAdministratorAccount 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_EnableAdministratorAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableGuestAccount 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_EnableGuestAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsformatandejectofremovablemediaalloweduser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsFormatAndEjectOfRemovableMediaAllowedUser 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Devices\_AllowedToFormatAndEjectRemovableMedia

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsguestaccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsGuestAccountName 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/Accounts\_RenameGuestAccount

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshidelastsignedinuser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideLastSignedInUser 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotDisplayLastSignedIn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshideusernameatsignin"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideUsernameAtSignIn 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotDisplayUsernameAtSignIn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationdisplayedonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationDisplayedOnLockScreen 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_DisplayUserInformationWhenTheSessionIsLocked

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationshownonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationShownOnLockScreen 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_DisplayUserInformationWhenTheSessionIsLocked

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetext"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageText 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTextForUsersAttemptingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetitle"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageTitle 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTitleForUsersAttemptingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimit"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimit 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_MachineInactivityLimit

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimitinminutes"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimitInMinutes 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_MachineInactivityLimit

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedclients"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedClients 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedClients

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedServers 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedServers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsonlyelevatesignedexecutables"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsOnlyElevateSignedExecutables 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_OnlyElevateExecutableFilesThatAreSignedAndValidated

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsrestrictanonymousaccesstonamedpipesandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsRestrictAnonymousAccessToNamedPipesAndShares 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictAnonymousAccessToNamedPipesAndShares

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionssmartcardremovalbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSmartCardRemovalBehavior 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/InteractiveLogon\_SmartCardRemovalBehavior

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsstandarduserelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsStandardUserElevationPromptBehavior 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_BehaviorOfTheElevationPromptForStandardUsers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsswitchtosecuredesktopwhenpromptingforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSwitchToSecureDesktopWhenPromptingForElevation 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_SwitchToTheSecureDesktopWhenPromptingForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmode"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_UseAdminApprovalMode

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmodeforadministrators"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalModeForAdministrators 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_RunAllAdministratorsInAdminApprovalMode

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsvirtualizefileandregistrywritefailurestoperuserlocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsVirtualizeFileAndRegistryWriteFailuresToPerUserLocations 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/LocalPoliciesSecurityOptions/userAccountControl\_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations

### <a name="windows10endpointprotectionconfigurationnetworkicmpredirectsoverrideospfgeneratedroutes"></a>Windows10EndpointProtectionConfiguration.NetworkIcmpRedirectsOverrideOspfGeneratedRoutes 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSLegacy/AllowICMPRedirectsToOverrideOSPFGeneratedRoutes

### <a name="windows10endpointprotectionconfigurationnetworkignorenetbiosnamereleaserequestsexceptfromwinsservers"></a>Windows10EndpointProtectionConfiguration.NetworkIgnoreNetBiosNameReleaseRequestsExceptFromWinsServers 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSLegacy/AllowTheComputerToIgnoreNetBIOSNameReleaseRequestsExceptFromWINSServers

### <a name="windows10endpointprotectionconfigurationnetworkipsourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpSourceRoutingProtectionLevel 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSLegacy/IPSourceRoutingProtectionLevel

### <a name="windows10endpointprotectionconfigurationnetworkipv6sourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpV6SourceRoutingProtectionLevel 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSLegacy/IPv6SourceRoutingProtectionLevel

### <a name="windows10endpointprotectionconfigurationpasswordpinlogon"></a>Windows10EndpointProtectionConfiguration.PasswordPinLogOn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/CredentialProviders/AllowPINLogon

### <a name="windows10endpointprotectionconfigurationpowershellshellscriptblocklogging"></a>Windows10EndpointProtectionConfiguration.PowerShellShellScriptBlockLogging 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsPowerShell/TurnOnPowerShellScriptBlockLogging

### <a name="windows10endpointprotectionconfigurationremoteassistancesolicitedsetting"></a>Windows10EndpointProtectionConfiguration.RemoteAssistanceSolicitedSetting 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/HardenedUNCPaths

### <a name="windows10endpointprotectionconfigurationremotedesktopservicesclientconnectionencryptionlevel"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesClientConnectionEncryptionLevel 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteDesktopServices/ClientConnectionEncryptionLevel

### <a name="windows10endpointprotectionconfigurationremotedesktopservicesdriveredirection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesDriveRedirection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteDesktopServices/DoNotAllowDriveRedirection

### <a name="windows10endpointprotectionconfigurationremotedesktopservicespasswordsaving"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPasswordSaving 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteDesktopServices/DoNotAllowPasswordSaving

### <a name="windows10endpointprotectionconfigurationremotedesktopservicespromptforpassworduponconnection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPromptForPasswordUponConnection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteDesktopServices/PromptForPasswordUponConnection

### <a name="windows10endpointprotectionconfigurationremotedesktopservicessecurerpccommunication"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesSecureRpcCommunication 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteDesktopServices/RequireSecureRPCCommunication

### <a name="windows10endpointprotectionconfigurationremotehostdelegationofnonexportablecredentials"></a>Windows10EndpointProtectionConfiguration.RemoteHostDelegationOfNonExportableCredentials 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/CredentialsDelegation/RemoteHostAllowsDelegationOfNonExportableCredentials

### <a name="windows10endpointprotectionconfigurationremotemanagementclientbasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientBasicAuthentication 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**: client\_/config/RemoteManagement/AllowBasicAuthentication

### <a name="windows10endpointprotectionconfigurationremotemanagementclientdigestauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientDigestAuthentication 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteManagement/DisallowDigestAuthentication

### <a name="windows10endpointprotectionconfigurationremotemanagementclientunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientUnencryptedTraffic 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**: client\_/config/RemoteManagement/AllowUnencryptedTraffic

### <a name="windows10endpointprotectionconfigurationremotemanagementservicebasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceBasicAuthentication 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**: servizio\_/config/RemoteManagement/AllowBasicAuthentication

### <a name="windows10endpointprotectionconfigurationremotemanagementservicestoringrunascredentials"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceStoringRunAsCredentials 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteManagement/DisallowStoringOfRunAsCredentials

### <a name="windows10endpointprotectionconfigurationremotemanagementserviceunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceUnencryptedTraffic 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**: servizio\_/config/RemoteManagement/AllowUnencryptedTraffic

### <a name="windows10endpointprotectionconfigurationrpcunauthenticatedclientoptions"></a>Windows10EndpointProtectionConfiguration.RpcUnauthenticatedClientOptions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteProcedureCall/RestrictUnauthenticatedRPCClients

### <a name="windows10endpointprotectionconfigurationsecurityguideapplyuacrestrictionstolocalaccountsonnetworklogon"></a>Windows10EndpointProtectionConfiguration.SecurityGuideApplyUacRestrictionsToLocalAccountsOnNetworkLogon 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSecurityGuide/ApplyUACRestrictionsToLocalAccountsOnNetworkLogon

### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1clientdriverstartconfiguration"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1ClientDriverStartConfiguration 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSecurityGuide/ConfigureSMBV1ClientDriver

### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1server"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1Server 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSecurityGuide/ConfigureSMBV1Server

### <a name="windows10endpointprotectionconfigurationsecurityguidestructuredexceptionhandlingoverwriteprotection"></a>Windows10EndpointProtectionConfiguration.SecurityGuideStructuredExceptionHandlingOverwriteProtection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSecurityGuide/EnableStructuredExceptionHandlingOverwriteProtection

### <a name="windows10endpointprotectionconfigurationsecurityguidewdigestauthentication"></a>Windows10EndpointProtectionConfiguration.SecurityGuideWDigestAuthentication 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/MSSecurityGuide/WDigestAuthentication

### <a name="windows10endpointprotectionconfigurationsmartscreenblockoverrideforfiles"></a>Windows10EndpointProtectionConfiguration.SmartScreenBlockOverrideForFiles 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/DeviceGuard/RequirePlatformSecurityFeatures

### <a name="windows10endpointprotectionconfigurationsmartscreenenableinshell"></a>Windows10EndpointProtectionConfiguration.SmartScreenEnableInShell 
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/SmartScreen/EnableSmartScreenInShell

### <a name="windows10endpointprotectionconfigurationsolicitedremoteassistance"></a>windows10endpointprotectionconfiguration.solicitedRemoteAssistance 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/RemoteAssistance/SolicitedRemoteAssistance

### <a name="windows10endpointprotectionconfigurationuserrightsaccesscredentialmanagerastrustedcaller"></a>Windows10EndpointProtectionConfiguration.UserRightsAccessCredentialManagerAsTrustedCaller 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/AccessCredentialManagerAsTrustedCaller

### <a name="windows10endpointprotectionconfigurationuserrightsaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsAccessFromNetwork 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/AccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsactaspartoftheoperatingsystem"></a>Windows10EndpointProtectionConfiguration.userRightsActAsPartOfTheOperatingSystem 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ActAsPartOfTheOperatingSystem

### <a name="windows10endpointprotectionconfigurationuserrightsallowaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsAllowAccessFromNetwork 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/AccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsbackupdata"></a>Windows10EndpointProtectionConfiguration.UserRightsBackupData 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/BackupFilesAndDirectories

### <a name="windows10endpointprotectionconfigurationuserrightsblockaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsBlockAccessFromNetwork 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/DenyAccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightschangesystemtime"></a>Windows10EndpointProtectionConfiguration.UserRightsChangeSystemTime 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ChangeSystemTime

### <a name="windows10endpointprotectionconfigurationuserrightscreateglobalobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateGlobalObjects 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/CreateGlobalObjects

### <a name="windows10endpointprotectionconfigurationuserrightscreatepagefile"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePageFile 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/CreatePageFile

### <a name="windows10endpointprotectionconfigurationuserrightscreatepermanentsharedobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePermanentSharedObjects 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/CreatePermanentSharedObjects

### <a name="windows10endpointprotectionconfigurationuserrightscreatesymboliclinks"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateSymbolicLinks 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/CreateSymbolicLinks

### <a name="windows10endpointprotectionconfigurationuserrightscreatetoken"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateToken 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/CreateToken

### <a name="windows10endpointprotectionconfigurationuserrightsdebugprograms"></a>Windows10EndpointProtectionConfiguration.UserRightsDebugPrograms 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/DebugPrograms

### <a name="windows10endpointprotectionconfigurationuserrightsdelegation"></a>Windows10EndpointProtectionConfiguration.UserRightsDelegation 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/EnableDelegation

### <a name="windows10endpointprotectionconfigurationuserrightsdenyaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsDenyAccessFromNetwork 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/DenyAccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsgeneratesecurityaudits"></a>Windows10EndpointProtectionConfiguration.UserRightsGenerateSecurityAudits 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/GenerateSecurityAudits

### <a name="windows10endpointprotectionconfigurationuserrightsimpersonateclient"></a>Windows10EndpointProtectionConfiguration.UserRightsImpersonateClient 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ImpersonateClient

### <a name="windows10endpointprotectionconfigurationuserrightsincreaseschedulingpriority"></a>Windows10EndpointProtectionConfiguration.UserRightsIncreaseSchedulingPriority 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/IncreaseSchedulingPriority

### <a name="windows10endpointprotectionconfigurationuserrightsloadunloaddrivers"></a>Windows10EndpointProtectionConfiguration.UserRightsLoadUnloadDrivers 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/LoadUnloadDeviceDrivers

### <a name="windows10endpointprotectionconfigurationuserrightslocallogon"></a>Windows10EndpointProtectionConfiguration.UserRightsLocalLogOn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/AllowLocalLogOn

### <a name="windows10endpointprotectionconfigurationuserrightslockmemory"></a>Windows10EndpointProtectionConfiguration.UserRightsLockMemory 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/LockMemory

### <a name="windows10endpointprotectionconfigurationuserrightsmanageauditingandsecuritylogs"></a>Windows10EndpointProtectionConfiguration.UserRightsManageAuditingAndSecurityLogs 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ManageAuditingAndSecurityLog

### <a name="windows10endpointprotectionconfigurationuserrightsmanagevolumes"></a>Windows10EndpointProtectionConfiguration.UserRightsManageVolumes 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ManageVolume

### <a name="windows10endpointprotectionconfigurationuserrightsmodifyfirmwareenvironment"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyFirmwareEnvironment 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ModifyFirmwareEnvironment

### <a name="windows10endpointprotectionconfigurationuserrightsmodifyobjectlabels"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyObjectLabels 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ModifyObjectLabel

### <a name="windows10endpointprotectionconfigurationuserrightsprofilesingleprocess"></a>Windows10EndpointProtectionConfiguration.UserRightsProfileSingleProcess 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/ProfileSingleProcess

### <a name="windows10endpointprotectionconfigurationuserrightsregisterprocessasservice"></a>Windows10EndpointProtectionConfiguration.UserRightsRegisterProcessAsService 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/DenyLocalLogOn

### <a name="windows10endpointprotectionconfigurationuserrightsremotedesktopserviceslogon"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteDesktopServicesLogOn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/DenyRemoteDesktopServicesLogOn

### <a name="windows10endpointprotectionconfigurationuserrightsremoteshutdown"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteShutdown 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/RemoteShutdown

### <a name="windows10endpointprotectionconfigurationuserrightsrestoredata"></a>Windows10EndpointProtectionConfiguration.UserRightsRestoreData 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/RestoreFilesAndDirectories

### <a name="windows10endpointprotectionconfigurationuserrightstakeownership"></a>Windows10EndpointProtectionConfiguration.UserRightsTakeOwnership 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/UserRights/TakeOwnership

### <a name="windows10endpointprotectionconfigurationwindowsconnectionmanagerconnectiontonondomainnetworks"></a>Windows10EndpointProtectionConfiguration.WindowsConnectionManagerConnectionToNonDomainNetworks 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsConnectionManager/ProhitConnectionToNonDomainNetworksWhenConnectedToDomainAuthenticatedNetwork

### <a name="windows10endpointprotectionconfigurationwindowslogonsigninlastinteractiveuseraftersysteminitiatedrestart"></a>Windows10EndpointProtectionConfiguration.WindowsLogOnSignInLastInteractiveUserAfterSystemInitiatedRestart 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsLogon/SignInLastInteractiveUserAutomaticallyAfterASystemInitiatedRestart

### <a name="windows10endpointprotectionconfigurationxboxservicesaccessorymanagementservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesAccessoryManagementServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxservicesenablexboxgamesavetask"></a>Windows10EndpointProtectionConfiguration.XboxServicesEnableXboxGameSaveTask 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/TaskScheduler/EnableXboxGameSaveTask

### <a name="windows10endpointprotectionconfigurationxboxservicesliveauthmanagerservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveAuthManagerServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxserviceslivegamesaveservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveGameSaveServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/SystemServices/XboxServicesLiveGameSaveServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxserviceslivenetworkingservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveNetworkingServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode

### <a name="windows10enterprisemodernappmanagementconfigurationuninstallbuiltinapps"></a>Windows10EnterpriseModernAppManagementConfiguration.UninstallBuiltInApps
**CSP**: N/A API Graph chiamare solo l' **URI di offset**: N/A API Graph solo chiamata

### <a name="windows10generalconfigurationaccountsblockaddingnonmicrosoftaccountemail"></a>Windows10GeneralConfiguration.AccountsBlockAddingNonMicrosoftAccountEmail 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/accounts/AllowAddingNonMicrosoftAccountsManually

### <a name="windows10generalconfigurationantitheftmodeblocked"></a>Windows10GeneralConfiguration.AntiTheftModeBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Security/AntiTheftMode

### <a name="windows10generalconfigurationappmanagementmsiallowusercontroloverinstall"></a>Windows10GeneralConfiguration.AppManagementMSIAllowUserControlOverInstall 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/MSIAllowUserControlOverInstall

### <a name="windows10generalconfigurationappmanagementmsialwaysinstallwithelevatedprivileges"></a>Windows10GeneralConfiguration.AppManagementMSIAlwaysInstallWithElevatedPrivileges 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges

### <a name="windows10generalconfigurationappsallowtrustedappssideloading"></a>Windows10GeneralConfiguration.AppsAllowTrustedAppsSideloading 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/AllowAllTrustedApps

### <a name="windows10generalconfigurationappsblockwindowsstoreoriginatedapps"></a>Windows10GeneralConfiguration.AppsBlockWindowsStoreOriginatedApps 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/DisableStoreOriginatedApps

### <a name="windows10generalconfigurationappsmicrosoftaccountsoptional"></a>Windows10GeneralConfiguration.AppsMicrosoftAccountsOptional 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/AppRuntime/AllowMicrosoftAccountsToBeOptional

### <a name="windows10generalconfigurationassignedaccessmultimodeprofiles"></a>Windows10GeneralConfiguration.AssignedAccessMultiModeProfiles 
**CSP**:./Device/vendor/MSFT/AssignedAccess  
**URI offset**:/configurazione

### <a name="windows10generalconfigurationassignedaccesssinglemodeappusermodelid"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeAppUserModelId 
**CSP**:./Device/vendor/MSFT/AssignedAccess  
**URI offset**:/configurazione

### <a name="windows10generalconfigurationassignedaccesssinglemodeusername"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeUserName 
**CSP**:./Device/vendor/MSFT/AssignedAccess  
**URI offset**:/configurazione

### <a name="windows10generalconfigurationauthenticationallowfidodevice"></a>Windows10GeneralConfiguration.AuthenticationAllowFIDODevice 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/authentication/AllowFidoDeviceSignon

### <a name="windows10generalconfigurationauthenticationallowsecondarydevice"></a>Windows10GeneralConfiguration.AuthenticationAllowSecondaryDevice 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/authentication/AllowSecondaryAuthenticationDevice

### <a name="windows10generalconfigurationauthenticationpreferredazureadtenantdomainname"></a>Windows10GeneralConfiguration.AuthenticationPreferredAzureADTenantDomainName 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/authentication/PreferredAadTenantDomainName

### <a name="windows10generalconfigurationauthenticationwebsignin"></a>Windows10GeneralConfiguration.AuthenticationWebSignIn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/authentication/EnableWebSignIn

### <a name="windows10generalconfigurationautoplaydefaultautorunbehavior"></a>Windows10GeneralConfiguration.AutoPlayDefaultAutoRunBehavior 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/AutoPlay/SetDefaultAutoRunBehavior

### <a name="windows10generalconfigurationautoplayfornonvolumedevices"></a>Windows10GeneralConfiguration.AutoPlayForNonVolumeDevices 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/AutoPlay/DisallowAutoplayForNonVolumeDevices

### <a name="windows10generalconfigurationautoplaymode"></a>Windows10GeneralConfiguration.AutoPlayMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/AutoPlay/TurnOffAutoPlay

### <a name="windows10generalconfigurationbluetoothallowedservices"></a>Windows10GeneralConfiguration.BluetoothAllowedServices 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Bluetooth/ServicesAllowedList

### <a name="windows10generalconfigurationbluetoothblockadvertising"></a>Windows10GeneralConfiguration.BluetoothBlockAdvertising 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Bluetooth/AllowAdvertising

### <a name="windows10generalconfigurationbluetoothblockdiscoverablemode"></a>Windows10GeneralConfiguration.BluetoothBlockDiscoverableMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Bluetooth/AllowDiscoverableMode

### <a name="windows10generalconfigurationbluetoothblocked"></a>Windows10GeneralConfiguration.BluetoothBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowBluetooth

### <a name="windows10generalconfigurationbluetoothblockprepairing"></a>Windows10GeneralConfiguration.BluetoothBlockPrePairing 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Bluetooth/AllowPrepairing

### <a name="windows10generalconfigurationbluetoothblockpromptedproximalconnections"></a>Windows10GeneralConfiguration.BluetoothBlockPromptedProximalConnections 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Bluetooth/AllowPromptedProximalConnections

### <a name="windows10generalconfigurationbluetoothdevicename"></a>Windows10GeneralConfiguration.BluetoothDeviceName 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Bluetooth/LocalDeviceName

### <a name="windows10generalconfigurationbootstartdriverinitialization"></a>windows10generalconfiguration.bootStartDriverInitialization 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/System/BootStartDriverInitialization

### <a name="windows10generalconfigurationcamerablocked"></a>Windows10GeneralConfiguration.CameraBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/camera/AllowCamera

### <a name="windows10generalconfigurationcellularblockdatawhenroaming"></a>Windows10GeneralConfiguration.CellularBlockDataWhenRoaming 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowCellularDataRoaming

### <a name="windows10generalconfigurationcellularblockvpn"></a>Windows10GeneralConfiguration.CellularBlockVpn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowVPNOverCellular

### <a name="windows10generalconfigurationcellularblockvpnwhenroaming"></a>Windows10GeneralConfiguration.CellularBlockVpnWhenRoaming 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowVPNRoamingOverCellular

### <a name="windows10generalconfigurationcellulardata"></a>Windows10GeneralConfiguration.CellularData 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowCellularData

### <a name="windows10generalconfigurationcertificatesblockmanualrootcertificateinstallation"></a>Windows10GeneralConfiguration.CertificatesBlockManualRootCertificateInstallation 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Security/AllowManualRootCertificateInstallation

### <a name="windows10generalconfigurationconnecteddevicesserviceblocked"></a>Windows10GeneralConfiguration.ConnectedDevicesServiceBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowConnectedDevices

### <a name="windows10generalconfigurationcopypasteblocked"></a>Windows10GeneralConfiguration.CopyPasteBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowCopyPaste

### <a name="windows10generalconfigurationcortanablocked"></a>Windows10GeneralConfiguration.CortanaBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/AboveLock/AllowCortanaAboveLock

### <a name="windows10generalconfigurationcryptographyallowfipsalgorithmpolicy"></a>Windows10GeneralConfiguration.CryptographyAllowFipsAlgorithmPolicy 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Cryptography/AllowFipsAlgorithmPolicy

### <a name="windows10generalconfigurationdataprotectionblockdirectmemoryaccess"></a>Windows10GeneralConfiguration.DataProtectionBlockDirectMemoryAccess 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DataProtection/AllowDirectMemoryAccess

### <a name="windows10generalconfigurationdefenderblockenduseraccess"></a>Windows10GeneralConfiguration.DefenderBlockEndUserAccess 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowUserUIAccess

### <a name="windows10generalconfigurationdefenderblockonaccessprotection"></a>Windows10GeneralConfiguration.DefenderBlockOnAccessProtection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowOnAccessProtection

### <a name="windows10generalconfigurationdefendercloudblocklevel"></a>Windows10GeneralConfiguration.DefenderCloudBlockLevel 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/CloudBlockLevel

### <a name="windows10generalconfigurationdefendercloudextendedtimeout"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeout 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/CloudExtendedTimeout

### <a name="windows10generalconfigurationdefendercloudextendedtimeoutinseconds"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeoutInSeconds 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/CloudExtendedTimeout

### <a name="windows10generalconfigurationdefenderdaysbeforedeletingquarantinedmalware"></a>Windows10GeneralConfiguration.DefenderDaysBeforeDeletingQuarantinedMalware 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/DaysToRetainCleanedMalware

### <a name="windows10generalconfigurationdefenderdetectedmalwareactions"></a>Windows10GeneralConfiguration.DefenderDetectedMalwareActions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ThreatSeverityDefaultAction

### <a name="windows10generalconfigurationdefenderfileextensionstoexclude"></a>Windows10GeneralConfiguration.DefenderFileExtensionsToExclude 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ExcludedExtensions

### <a name="windows10generalconfigurationdefenderfilesandfolderstoexclude"></a>Windows10GeneralConfiguration.DefenderFilesAndFoldersToExclude 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ExcludedPaths

### <a name="windows10generalconfigurationdefendermonitorfileactivity"></a>Windows10GeneralConfiguration.DefenderMonitorFileActivity 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowRealtimeMonitoring

### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappaction"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppAction 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/PUAProtection

### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappactionsetting"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppActionSetting 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/PUAProtection

### <a name="windows10generalconfigurationdefenderprocessestoexclude"></a>Windows10GeneralConfiguration.DefenderProcessesToExclude 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ExcludedProcesses

### <a name="windows10generalconfigurationdefenderpromptforsamplesubmission"></a>Windows10GeneralConfiguration.DefenderPromptForSampleSubmission 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/SubmitSamplesConsent

### <a name="windows10generalconfigurationdefenderrequirebehaviormonitoring"></a>Windows10GeneralConfiguration.DefenderRequireBehaviorMonitoring 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowBehaviorMonitoring

### <a name="windows10generalconfigurationdefenderrequirecloudprotection"></a>Windows10GeneralConfiguration.DefenderRequireCloudProtection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowCloudProtection

### <a name="windows10generalconfigurationdefenderrequirenetworkinspectionsystem"></a>Windows10GeneralConfiguration.DefenderRequireNetworkInspectionSystem 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowIntrusionPreventionSystem

### <a name="windows10generalconfigurationdefenderrequirerealtimemonitoring"></a>Windows10GeneralConfiguration.DefenderRequireRealTimeMonitoring 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowRealtimeMonitoring

### <a name="windows10generalconfigurationdefenderscanarchivefiles"></a>Windows10GeneralConfiguration.DefenderScanArchiveFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowArchiveScanning

### <a name="windows10generalconfigurationdefenderscandownloads"></a>Windows10GeneralConfiguration.DefenderScanDownloads 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowIOAVProtection

### <a name="windows10generalconfigurationdefenderscanincomingmail"></a>Windows10GeneralConfiguration.DefenderScanIncomingMail 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowScanningNetworkFiles

### <a name="windows10generalconfigurationdefenderscanmappednetworkdrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanMappedNetworkDrivesDuringFullScan 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowFullScanOnMappedNetworkDrives

### <a name="windows10generalconfigurationdefenderscanmaxcpu"></a>Windows10GeneralConfiguration.DefenderScanMaxCpu 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AvgCPULoadFactor

### <a name="windows10generalconfigurationdefenderscannetworkfiles"></a>Windows10GeneralConfiguration.DefenderScanNetworkFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowScanningNetworkFiles

### <a name="windows10generalconfigurationdefenderscanremovabledrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanRemovableDrivesDuringFullScan 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowFullScanRemovableDriveScanning

### <a name="windows10generalconfigurationdefenderscanscriptsloadedininternetexplorer"></a>Windows10GeneralConfiguration.DefenderScanScriptsLoadedInInternetExplorer 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/AllowScriptScanning

### <a name="windows10generalconfigurationdefenderscantype"></a>Windows10GeneralConfiguration.DefenderScanType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ScanParameter

### <a name="windows10generalconfigurationdefenderscheduledquickscantime"></a>Windows10GeneralConfiguration.DefenderScheduledQuickScanTime 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ScheduleQuickScanTime

### <a name="windows10generalconfigurationdefenderscheduledscantime"></a>Windows10GeneralConfiguration.DefenderScheduledScanTime 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ScheduleScanTime

### <a name="windows10generalconfigurationdefenderschedulescanday"></a>Windows10GeneralConfiguration.DefenderScheduleScanDay 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ScheduleScanDay

### <a name="windows10generalconfigurationdefendersignatureupdateintervalinhours"></a>Windows10GeneralConfiguration.DefenderSignatureUpdateIntervalInHours 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/SignatureUpdateInterval

### <a name="windows10generalconfigurationdefendersubmitsamplesconsenttype"></a>Windows10GeneralConfiguration.DefenderSubmitSamplesConsentType 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/SubmitSamplesConsent

### <a name="windows10generalconfigurationdefendersystemscanschedule"></a>Windows10GeneralConfiguration.DefenderSystemScanSchedule 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Defender/ScheduleScanDay

### <a name="windows10generalconfigurationdeveloperunlocksetting"></a>Windows10GeneralConfiguration.DeveloperUnlockSetting 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/AllowDeveloperUnlock

### <a name="windows10generalconfigurationdevicemanagementblockfactoryresetonmobile"></a>Windows10GeneralConfiguration.DeviceManagementBlockFactoryResetOnMobile 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/System/AllowUserToResetPhone

### <a name="windows10generalconfigurationdevicemanagementblockmanualunenroll"></a>Windows10GeneralConfiguration.DeviceManagementBlockManualUnenroll 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowManualMDMUnenrollment

### <a name="windows10generalconfigurationdiagnosticsdatasubmissionmode"></a>Windows10GeneralConfiguration.DiagnosticsDataSubmissionMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/System/AllowTelemetry

### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedoff"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOff 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/display/TurnOffGdiDPIScalingForApps

### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedon"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/display/TurnOnGdiDPIScalingForApps

### <a name="windows10generalconfigurationedgeallowstartpagesmodification"></a>Windows10GeneralConfiguration.EdgeAllowStartPagesModification 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/HomePages

### <a name="windows10generalconfigurationedgeblockaccesstoaboutflags"></a>Windows10GeneralConfiguration.EdgeBlockAccessToAboutFlags 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/PreventAccessToAboutFlagsInMicrosoftEdge

### <a name="windows10generalconfigurationedgeblockaddressbardropdown"></a>Windows10GeneralConfiguration.EdgeBlockAddressBarDropdown 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowAddressBarDropdown

### <a name="windows10generalconfigurationedgeblockautofill"></a>Windows10GeneralConfiguration.EdgeBlockAutofill 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowAutofill

### <a name="windows10generalconfigurationedgeblockcompatibilitylist"></a>Windows10GeneralConfiguration.EdgeBlockCompatibilityList 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowMicrosoftCompatibilityList

### <a name="windows10generalconfigurationedgeblockdevelopertools"></a>Windows10GeneralConfiguration.EdgeBlockDeveloperTools 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowDeveloperTools

### <a name="windows10generalconfigurationedgeblocked"></a>Windows10GeneralConfiguration.EdgeBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowBrowser

### <a name="windows10generalconfigurationedgeblockeditfavorites"></a>Windows10GeneralConfiguration.EdgeBlockEditFavorites 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/LockdownFavorites

### <a name="windows10generalconfigurationedgeblockextensions"></a>Windows10GeneralConfiguration.EdgeBlockExtensions 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowExtensions

### <a name="windows10generalconfigurationedgeblockfullscreenmode"></a>Windows10GeneralConfiguration.EdgeBlockFullScreenMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowFullScreenMode

### <a name="windows10generalconfigurationedgeblockinprivatebrowsing"></a>Windows10GeneralConfiguration.EdgeBlockInPrivateBrowsing 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowInPrivate

### <a name="windows10generalconfigurationedgeblocklivetiledatacollection"></a>Windows10GeneralConfiguration.EdgeBlockLiveTileDataCollection 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/PreventLiveTileDataCollection

### <a name="windows10generalconfigurationedgeblockpasswordmanager"></a>Windows10GeneralConfiguration.EdgeBlockPasswordManager 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowPasswordManager

### <a name="windows10generalconfigurationedgeblockpopups"></a>Windows10GeneralConfiguration.EdgeBlockPopups 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowPopups

### <a name="windows10generalconfigurationedgeblockprelaunch"></a>Windows10GeneralConfiguration.EdgeBlockPrelaunch 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowPrelaunch

### <a name="windows10generalconfigurationedgeblockprinting"></a>Windows10GeneralConfiguration.EdgeBlockPrinting 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowPrinting

### <a name="windows10generalconfigurationedgeblocksavinghistory"></a>Windows10GeneralConfiguration.EdgeBlockSavingHistory 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowSavingHistory

### <a name="windows10generalconfigurationedgeblocksearchsuggestions"></a>Windows10GeneralConfiguration.EdgeBlockSearchSuggestions 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowSearchSuggestionsinAddressBar

### <a name="windows10generalconfigurationedgeblocksendingdonottrackheader"></a>Windows10GeneralConfiguration.EdgeBlockSendingDoNotTrackHeader 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowDoNotTrack

### <a name="windows10generalconfigurationedgeblocksendingintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeBlockSendingIntranetTrafficToInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/SendIntranetTraffictoInternetExplorer

### <a name="windows10generalconfigurationedgeblocksideloadingextensions"></a>Windows10GeneralConfiguration.EdgeBlockSideloadingExtensions 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowSideloadingOfExtensions

### <a name="windows10generalconfigurationedgeblocktabpreloading"></a>Windows10GeneralConfiguration.EdgeBlockTabPreloading 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowTabPreloading

### <a name="windows10generalconfigurationedgeblockwebcontentonnewtabpage"></a>Windows10GeneralConfiguration.EdgeBlockWebContentOnNewTabPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowWebContentOnNewTabPage

### <a name="windows10generalconfigurationedgeclearbrowsingdataonexit"></a>Windows10GeneralConfiguration.EdgeClearBrowsingDataOnExit 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ClearBrowsingDataOnExit

### <a name="windows10generalconfigurationedgecookiepolicy"></a>Windows10GeneralConfiguration.EdgeCookiePolicy 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowCookies

### <a name="windows10generalconfigurationedgedisablefirstrunpage"></a>Windows10GeneralConfiguration.EdgeDisableFirstRunPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/PreventFirstRunPage

### <a name="windows10generalconfigurationedgeenterprisemodesitelistlocation"></a>Windows10GeneralConfiguration.EdgeEnterpriseModeSiteListLocation 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/EnterpriseSiteListServiceUrl

### <a name="windows10generalconfigurationedgefavoritesbarvisibility"></a>Windows10GeneralConfiguration.EdgeFavoritesBarVisibility 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ConfigureFavoritesBar

### <a name="windows10generalconfigurationedgefavoriteslistlocation"></a>Windows10GeneralConfiguration.EdgeFavoritesListLocation 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ProvisionFavorites

### <a name="windows10generalconfigurationedgefirstrunurl"></a>Windows10GeneralConfiguration.EdgeFirstRunUrl 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/FirstRunURL

### <a name="windows10generalconfigurationedgehomebuttonconfiguration"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/SetHomeButtonURL

### <a name="windows10generalconfigurationedgehomebuttonconfigurationenabled"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfigurationEnabled 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ConfigureHomeButton

### <a name="windows10generalconfigurationedgehomepageurls"></a>Windows10GeneralConfiguration.EdgeHomepageUrls 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/SetHomeButtonURL

### <a name="windows10generalconfigurationedgenewtabpageurl"></a>Windows10GeneralConfiguration.EdgeNewTabPageURL 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/SetNewTabPageURL

### <a name="windows10generalconfigurationedgeopenswith"></a>Windows10GeneralConfiguration.EdgeOpensWith 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ConfigureOpenMicrosoftEdgeWith

### <a name="windows10generalconfigurationedgepreventcertificateerroroverride"></a>Windows10GeneralConfiguration.EdgePreventCertificateErrorOverride 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/browser/PreventCertErrorOverrides

### <a name="windows10generalconfigurationedgerequiresmartscreen"></a>Windows10GeneralConfiguration.EdgeRequireSmartScreen 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/AllowSmartScreen

### <a name="windows10generalconfigurationedgesearchengine"></a>Windows10GeneralConfiguration.EdgeSearchEngine 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/SetDefaultSearchEngine

### <a name="windows10generalconfigurationedgesendintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeSendIntranetTrafficToInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/SendIntranetTraffictoInternetExplorer

### <a name="windows10generalconfigurationedgeshowmessagewhenopeninginternetexplorersites"></a>Windows10GeneralConfiguration.EdgeShowMessageWhenOpeningInternetExplorerSites 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ShowMessageWhenOpeningSitesInInternetExplorer

### <a name="windows10generalconfigurationedgesyncfavoriteswithinternetexplorer"></a>Windows10GeneralConfiguration.EdgeSyncFavoritesWithInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/SyncFavoritesBetweenIEAndMicrosoftEdge

### <a name="windows10generalconfigurationedgetelemetryformicrosoft365analytics"></a>Windows10GeneralConfiguration.EdgeTelemetryForMicrosoft365Analytics 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ConfigureTelemetryForMicrosoft365Analytics

### <a name="windows10generalconfigurationenableautomaticredeployment"></a>Windows10GeneralConfiguration.EnableAutomaticRedeployment 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/CredentialProviders/DisableAutomaticReDeploymentCredentials

### <a name="windows10generalconfigurationenterprisecloudprintdiscoveryendpoint"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryEndPoint 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint

### <a name="windows10generalconfigurationenterprisecloudprintdiscoverymaxlimit"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryMaxLimit 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit

### <a name="windows10generalconfigurationenterprisecloudprintmopriadiscoveryresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintMopriaDiscoveryResourceIdentifier 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/EnterpriseCloudPrint/MopriaDiscoveryResourceId

### <a name="windows10generalconfigurationenterprisecloudprintoauthauthority"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthAuthority 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

### <a name="windows10generalconfigurationenterprisecloudprintoauthclientidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthClientIdentifier 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

### <a name="windows10generalconfigurationenterprisecloudprintresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintResourceIdentifier 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/EnterpriseCloudPrint/CloudPrintResourceId

### <a name="windows10generalconfigurationexperienceblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.ExperienceBlockConsumerSpecificFeatures 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowWindowsConsumerFeatures

### <a name="windows10generalconfigurationexperienceblockdevicediscovery"></a>Windows10GeneralConfiguration.ExperienceBlockDeviceDiscovery 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowDeviceDiscovery

### <a name="windows10generalconfigurationexperienceblockerrordialogwhennosim"></a>Windows10GeneralConfiguration.ExperienceBlockErrorDialogWhenNoSIM 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowSIMErrorDialogPromptWhenNoSIM

### <a name="windows10generalconfigurationexperienceblocktaskswitcher"></a>Windows10GeneralConfiguration.ExperienceBlockTaskSwitcher 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowTaskSwitcher

### <a name="windows10generalconfigurationexperienceblockwindowsspotlight"></a>Windows10GeneralConfiguration.ExperienceBlockWindowsSpotlight 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowWindowsSpotlight

### <a name="windows10generalconfigurationexperiencedonotsyncbrowsersettings"></a>Windows10GeneralConfiguration.ExperienceDoNotSyncBrowserSettings 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Experience/DoNotSyncBrowserSettings

### <a name="windows10generalconfigurationgamedvrblocked"></a>Windows10GeneralConfiguration.GameDvrBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/AllowGameDVR

### <a name="windows10generalconfigurationhardwaredeviceinstallationbydeviceidentifiers"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationByDeviceIdentifiers 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

### <a name="windows10generalconfigurationhardwaredeviceinstallationbysetupclasses"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationBySetupClasses 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

### <a name="windows10generalconfigurationinkworkspaceaccess"></a>Windows10GeneralConfiguration.InkWorkspaceAccess 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsInkWorkspace/AllowWindowsInkWorkspace

### <a name="windows10generalconfigurationinkworkspaceaccessstate"></a>Windows10GeneralConfiguration.InkWorkspaceAccessState 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsInkWorkspace/AllowWindowsInkWorkspace

### <a name="windows10generalconfigurationinkworkspaceblocksuggestedapps"></a>Windows10GeneralConfiguration.InkWorkspaceBlockSuggestedApps 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace

### <a name="windows10generalconfigurationinternetexploreractivexcontrolsinprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerActiveXControlsInProtectedMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DoNotAllowActiveXControlsInProtectedMode

### <a name="windows10generalconfigurationinternetexplorerautocomplete"></a>Windows10GeneralConfiguration.InternetExplorerAutoComplete 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/AllowAutoComplete

### <a name="windows10generalconfigurationinternetexplorerblockoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerBlockOutdatedActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DoNotBlockOutdatedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarnings"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarnings 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableBypassOfSmartScreenWarnings

### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarningsaboutuncommonfiles"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarningsAboutUncommonFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableBypassOfSmartScreenWarningsAboutUncommonFiles

### <a name="windows10generalconfigurationinternetexplorercertificateaddressmismatchwarning"></a>Windows10GeneralConfiguration.InternetExplorerCertificateAddressMismatchWarning 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/AllowCertificateAddressMismatchWarning

### <a name="windows10generalconfigurationinternetexplorercheckservercertificaterevocation"></a>Windows10GeneralConfiguration.InternetExplorerCheckServerCertificateRevocation 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/CheckServerCertificateRevocation

### <a name="windows10generalconfigurationinternetexplorerchecksignaturesondownloadedprograms"></a>Windows10GeneralConfiguration.InternetExplorerCheckSignaturesOnDownloadedPrograms 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/CheckSignaturesOnDownloadedPrograms

### <a name="windows10generalconfigurationinternetexplorercrashdetection"></a>Windows10GeneralConfiguration.InternetExplorerCrashDetection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableCrashDetection

### <a name="windows10generalconfigurationinternetexplorerdisableprocessesinenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerDisableProcessesInEnhancedProtectedMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableProcessesInEnhancedProtectedMode

### <a name="windows10generalconfigurationinternetexplorerdownloadenclosures"></a>Windows10GeneralConfiguration.InternetExplorerDownloadEnclosures 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableEnclosureDownloading

### <a name="windows10generalconfigurationinternetexplorerencryptionsupport"></a>Windows10GeneralConfiguration.InternetExplorerEncryptionSupport 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableEncryptionSupport

### <a name="windows10generalconfigurationinternetexplorerenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerEnhancedProtectedMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/AllowEnhancedProtectedMode

### <a name="windows10generalconfigurationinternetexplorerfallbacktossl3"></a>Windows10GeneralConfiguration.InternetExplorerFallbackToSsl3 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/AllowFallbackToSSL3

### <a name="windows10generalconfigurationinternetexplorerignorecertificateerrors"></a>Windows10GeneralConfiguration.InternetExplorerIgnoreCertificateErrors 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableIgnoringCertificateErrors

### <a name="windows10generalconfigurationinternetexplorerincludeallnetworkpaths"></a>Windows10GeneralConfiguration.InternetExplorerIncludeAllNetworkPaths 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/IncludeAllNetworkPaths

### <a name="windows10generalconfigurationinternetexplorerinternetzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAccessToDataSources 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowAccessToDataSources

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowVBScriptToRun 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowVBScriptToRunInInternetExplorer

### <a name="windows10generalconfigurationinternetexplorerinternetzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAutomaticPromptForFileDownloads 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowAutomaticPromptingForFileDownloads

### <a name="windows10generalconfigurationinternetexplorerinternetzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCopyAndPasteViaScript 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowCopyPasteViaScript

### <a name="windows10generalconfigurationinternetexplorerinternetzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCrossSiteScriptingFilter 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneEnableCrossSiteScriptingFilter

### <a name="windows10generalconfigurationinternetexplorerinternetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDotNetFrameworkReliantComponents 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowNETFrameworkReliantComponents

### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadSignedActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneDownloadSignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadUnsignedActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneDownloadUnsignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragAndDropOrCopyAndPasteFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowDragAndDropCopyAndPasteFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneIncludeLocalPathWhenUploadingFilesToServer

### <a name="windows10generalconfigurationinternetexplorerinternetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneJavaPermissions


### <a name="windows10generalconfigurationinternetexplorerinternetzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneLaunchingApplicationsAndFilesInIFRAME

### <a name="windows10generalconfigurationinternetexplorerinternetzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLessPrivilegedSites 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowLessPrivilegedSites

### <a name="windows10generalconfigurationinternetexplorerinternetzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLoadingOfXamlFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowLoadingOfXAMLFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLogonOptions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneLogonOptions

### <a name="windows10generalconfigurationinternetexplorerinternetzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneNavigateWindowsAndFrames

### <a name="windows10generalconfigurationinternetexplorerinternetzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerInternetZonePopupBlocker 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneUsePopupBlocker

### <a name="windows10generalconfigurationinternetexplorerinternetzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneProtectedMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneEnableProtectedMode

### <a name="windows10generalconfigurationinternetexplorerinternetzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptingOfWebBrowserControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowScriptingOfInternetExplorerWebBrowserControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptInitiatedWindows 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowScriptInitiatedWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptlets 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowScriptlets

### <a name="windows10generalconfigurationinternetexplorerinternetzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneShowSecurityWarningForPotentiallyUnsafeFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSmartScreen 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerinternetzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUpdatesToStatusBarViaScript 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowUpdatesToStatusBarViaScript

### <a name="windows10generalconfigurationinternetexplorerinternetzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUserDataPersistence 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/InternetZoneAllowUserDataPersistence

### <a name="windows10generalconfigurationinternetexplorerintranetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/IntranetZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerintranetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/IntranetZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/IntranetZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LocalMachineZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddowninternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownInternetZoneSmartScreen 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LockedDownInternetZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerlockeddownintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownIntranetZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LockedDownIntranetJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownLocalMachineZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LockedDownLocalMachineZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LockedDownRestrictedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneSmartScreen 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LockedDownRestrictedSitesZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerlockeddowntrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownTrustedZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/LockedDownTrustedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerpreventmanagingsmartscreenfilter"></a>Windows10GeneralConfiguration.InternetExplorerPreventManagingSmartScreenFilter 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/PreventManagingSmartScreenFilter

### <a name="windows10generalconfigurationinternetexplorerpreventperuserinstallationofactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerPreventPerUserInstallationOfActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/PreventPerUserInstallationOfActiveXControls

### <a name="windows10generalconfigurationinternetexplorerprocessesconsistentmimehandling"></a>Windows10GeneralConfiguration.InternetExplorerProcessesConsistentMimeHandling 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/ConsistentMimeHandlingInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesmimesniffingsafetyfeature"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMimeSniffingSafetyFeature 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/MimeSniffingSafetyFeatureInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesmkprotocolsecurityrestriction"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMKProtocolSecurityRestriction 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/MKProtocolSecurityRestrictionInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesnotificationbar"></a>Windows10GeneralConfiguration.InternetExplorerProcessesNotificationBar 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/NotificationBarInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesprotectionfromzoneelevation"></a>Windows10GeneralConfiguration.InternetExplorerProcessesProtectionFromZoneElevation 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/ProtectionFromZoneElevationInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictactivexinstall"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictActiveXInstall 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictActiveXInstallInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictfiledownload"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictFileDownload 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictFileDownloadInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesscriptedwindowsecurityrestrictions"></a>Windows10GeneralConfiguration.InternetExplorerProcessesScriptedWindowSecurityRestrictions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/ScriptedWindowSecurityRestrictionsInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerremoverunthistimebuttonforoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRemoveRunThisTimeButtonForOutdatedActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RemoveRunThisTimeButtonForOutdatedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAccessToDataSources 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowAccessToDataSources

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneactivescripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneActiveScripting 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowActiveScripting

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowVBScriptToRun 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowVBScriptToRunInInternetExplorer

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAutomaticPromptForFileDownloads 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowAutomaticPromptingForFileDownloads

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonebinaryandscriptbehaviors"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneBinaryAndScriptBehaviors 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowBinaryAndScriptBehaviors

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCopyAndPasteViaScript 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowCopyPasteViaScript

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCrossSiteScriptingFilter 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneEnableCrossSiteScriptingFilter

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDotNetFrameworkReliantComponents 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowNETFrameworkReliantComponents

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadSignedActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneDownloadSignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadUnsignedActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneDownloadUnsignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragAndDropOrCopyAndPasteFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowDragAndDropCopyAndPasteFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonefiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneFileDownloads 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowFileDownloads

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneIncludeLocalPathWhenUploadingFilesToServer

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneLaunchingApplicationsAndFilesInIFRAME

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLessPrivilegedSites 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowLessPrivilegedSites

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLoadingOfXamlFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowLoadingOfXAMLFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLogonOptions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneLogonOptions

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonemetarefresh"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneMetaRefresh 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowMETAREFRESH

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneNavigateWindowsAndFrames

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZonePopupBlocker 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneUsePopupBlocker

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneProtectedMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneTurnOnProtectedMode

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerunactivexcontrolsandplugins"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunActiveXControlsAndPlugins 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneRunActiveXControlsAndPlugins

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptactivexcontrolsmarkedsafeforscripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptActiveXControlsMarkedSafeForScripting 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneScriptActiveXControlsMarkedSafeForScripting

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofjavaapplets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfJavaApplets 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneScriptingOfJavaApplets

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfWebBrowserControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowScriptingOfInternetExplorerWebBrowserControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptInitiatedWindows 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowScriptInitiatedWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptlets 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowScriptlets

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneShowSecurityWarningForPotentiallyUnsafeFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSmartScreen 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUpdatesToStatusBarViaScript 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowUpdatesToStatusBarViaScript

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUserDataPersistence 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/RestrictedSitesZoneAllowUserDataPersistence

### <a name="windows10generalconfigurationinternetexplorersecuritysettingscheck"></a>Windows10GeneralConfiguration.InternetExplorerSecuritySettingsCheck 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DisableSecuritySettingsCheck

### <a name="windows10generalconfigurationinternetexplorersecurityzonesuseonlymachinesettings"></a>Windows10GeneralConfiguration.InternetExplorerSecurityZonesUseOnlyMachineSettings 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/SecurityZonesUseOnlyMachineSettings

### <a name="windows10generalconfigurationinternetexplorersoftwarewhensignatureisinvalid"></a>Windows10GeneralConfiguration.InternetExplorerSoftwareWhenSignatureIsInvalid 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/AllowSoftwareWhenSignatureIsInvalid

### <a name="windows10generalconfigurationinternetexplorertrustedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/TrustedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorertrustedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/TrustedSitesZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorertrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneJavaPermissions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/TrustedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexploreruseactivexinstallerservice"></a>Windows10GeneralConfiguration.InternetExplorerUseActiveXInstallerService 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/SpecifyUseOfActiveXInstallerService

### <a name="windows10generalconfigurationinternetexplorerusersaddingsites"></a>Windows10GeneralConfiguration.InternetExplorerUsersAddingSites 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DoNotAllowUsersToAddSites

### <a name="windows10generalconfigurationinternetexploreruserschangingpolicies"></a>Windows10GeneralConfiguration.InternetExplorerUsersChangingPolicies 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/InternetExplorer/DoNotAllowUsersToChangePolicies

### <a name="windows10generalconfigurationinternetsharingblocked"></a>Windows10GeneralConfiguration.InternetSharingBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WiFi/AllowInternetSharing

### <a name="windows10generalconfigurationlocationservicesblocked"></a>Windows10GeneralConfiguration.LocationServicesBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/System/AllowLocation

### <a name="windows10generalconfigurationlockscreenallowtimeoutconfiguration"></a>Windows10GeneralConfiguration.LockScreenAllowTimeoutConfiguration 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/AllowScreenTimeoutWhileLockedUser/config

### <a name="windows10generalconfigurationlockscreenblockactioncenternotifications"></a>Windows10GeneralConfiguration.LockScreenBlockActionCenterNotifications 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/AboveLock/AllowActionCenterNotifications

### <a name="windows10generalconfigurationlockscreenblockcortana"></a>Windows10GeneralConfiguration.LockScreenBlockCortana 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/AboveLock/AllowCortanaAboveLock

### <a name="windows10generalconfigurationlockscreenblocktoastnotifications"></a>Windows10GeneralConfiguration.LockScreenBlockToastNotifications 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/AboveLock/AllowToasts

### <a name="windows10generalconfigurationlockscreencamera"></a>Windows10GeneralConfiguration.LockScreenCamera 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/PreventEnablingLockScreenCamera

### <a name="windows10generalconfigurationlockscreenhidenetworkselectionui"></a>Windows10GeneralConfiguration.LockScreenHideNetworkSelectionUI 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsLogon/DontDisplayNetworkSelectionUI

### <a name="windows10generalconfigurationlockscreenslideshow"></a>Windows10GeneralConfiguration.LockScreenSlideShow 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/PreventLockScreenSlideShow

### <a name="windows10generalconfigurationlockscreentimeoutinseconds"></a>Windows10GeneralConfiguration.LockScreenTimeoutInSeconds 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/ScreenTimeoutWhileLocked

### <a name="windows10generalconfigurationlogonblockfastuserswitching"></a>Windows10GeneralConfiguration.LogonBlockFastUserSwitching 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WindowsLogon/HideFastUserSwitching

### <a name="windows10generalconfigurationmessagingblockmms"></a>Windows10GeneralConfiguration.MessagingBlockMMS 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Messaging/AllowMMS

### <a name="windows10generalconfigurationmessagingblockrichcommunicationservices"></a>Windows10GeneralConfiguration.MessagingBlockRichCommunicationServices 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Messaging/AllowRCS

### <a name="windows10generalconfigurationmessagingblocksync"></a>Windows10GeneralConfiguration.MessagingBlockSync 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Messaging/AllowMessageSync

### <a name="windows10generalconfigurationmicrosoftaccountblocked"></a>Windows10GeneralConfiguration.MicrosoftAccountBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/accounts/AllowMicrosoftAccountConnection

### <a name="windows10generalconfigurationmicrosoftaccountblocksettingssync"></a>Windows10GeneralConfiguration.MicrosoftAccountBlockSettingsSync 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowSyncMySettings

### <a name="windows10generalconfigurationmicrosoftaccountsigninassistantsettings"></a>Windows10GeneralConfiguration.MicrosoftAccountSignInAssistantSettings 
**CSP**:./Device/vendor/MSFT/accounts  
**URI offset**:/AllowMicrosoftAccountSignInAssistant

### <a name="windows10generalconfigurationnetworkproxyapplysettingsdevicewide"></a>Windows10GeneralConfiguration.NetworkProxyApplySettingsDeviceWide 
**CSP**:./Device/vendor/MSFT/NetworkProxy  
**URI offset**:/ProxySettingsPerUser

### <a name="windows10generalconfigurationnetworkproxyautomaticconfigurationurl"></a>Windows10GeneralConfiguration.NetworkProxyAutomaticConfigurationUrl 
**CSP**:./Device/vendor/MSFT/NetworkProxy  
**URI offset**:/SetupScriptUrl

### <a name="windows10generalconfigurationnetworkproxydisableautodetect"></a>Windows10GeneralConfiguration.NetworkProxyDisableAutoDetect 
**CSP**:./Device/vendor/MSFT/NetworkProxy  
**URI offset**:/AutoDetect

### <a name="windows10generalconfigurationnetworkproxyserver"></a>Windows10GeneralConfiguration.NetworkProxyServer 
**CSP**:./Vendor/MSFT/NetworkProxy  
**URI offset**:/ProxyAddress,/Exceptions e/UseProxyForLocalAddresses

### <a name="windows10generalconfigurationnfcblocked"></a>Windows10GeneralConfiguration.NfcBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowNFC

### <a name="windows10generalconfigurationonedrivedisablefilesync"></a>Windows10GeneralConfiguration.OneDriveDisableFileSync 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/System/DisableOneDriveFileSync

### <a name="windows10generalconfigurationpasswordblocksimple"></a>Windows10GeneralConfiguration.PasswordBlockSimple 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/AllowSimpleDevicePassword

### <a name="windows10generalconfigurationpasswordexpirationdays"></a>Windows10GeneralConfiguration.PasswordExpirationDays 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/DevicePasswordExpiration

### <a name="windows10generalconfigurationpasswordminimumageindays"></a>Windows10GeneralConfiguration.PasswordMinimumAgeInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/MinimumPasswordAge

### <a name="windows10generalconfigurationpasswordminimumcharactersetcount"></a>Windows10GeneralConfiguration.PasswordMinimumCharacterSetCount 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/MinDevicePasswordComplexCharacters

### <a name="windows10generalconfigurationpasswordminimumlength"></a>Windows10GeneralConfiguration.PasswordMinimumLength 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/MinDevicePasswordLength

### <a name="windows10generalconfigurationpasswordminutesofinactivitybeforescreentimeout"></a>Windows10GeneralConfiguration.PasswordMinutesOfInactivityBeforeScreenTimeout 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/MaxInactivityTimeDeviceLock

### <a name="windows10generalconfigurationpasswordpreviouspasswordblockcount"></a>Windows10GeneralConfiguration.PasswordPreviousPasswordBlockCount 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/DevicePasswordHistory

### <a name="windows10generalconfigurationpasswordrequired"></a>Windows10GeneralConfiguration.PasswordRequired 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/DevicePasswordEnabled

### <a name="windows10generalconfigurationpasswordrequiredtype"></a>Windows10GeneralConfiguration.PasswordRequiredType 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/AlphanumericDevicePasswordRequired

### <a name="windows10generalconfigurationpasswordrequirewhenresumefromidlestate"></a>Windows10GeneralConfiguration.PasswordRequireWhenResumeFromIdleState 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/AllowIdleReturnWithoutPassword

### <a name="windows10generalconfigurationpasswordsigninfailurecountbeforefactoryreset"></a>Windows10GeneralConfiguration.PasswordSignInFailureCountBeforeFactoryReset 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeviceLock/MaxDevicePasswordFailedAttempts

### <a name="windows10generalconfigurationpersonalizationdesktopimageurl"></a>Windows10GeneralConfiguration.PersonalizationDesktopImageUrl 
**CSP**:./Device/vendor/MSFT/Personalization  
**URI offset**:/DesktopImageUrl

### <a name="windows10generalconfigurationpersonalizationlockscreenimageurl"></a>Windows10GeneralConfiguration.PersonalizationLockScreenImageUrl 
**CSP**:./Device/vendor/MSFT/Personalization  
**URI offset**:/LockScreenImageUrl

### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhileonbattery"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhileOnBattery 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Power/RequirePasswordWhenComputerWakesOnBattery

### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhilepluggedin"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhilePluggedIn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Power/RequirePasswordWhenComputerWakesPluggedIn

### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhileonbattery"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhileOnBattery 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Power/AllowStandbyStatesWhenSleepingOnBattery

### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhilepluggedin"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhilePluggedIn 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Power/AllowStandbyWhenSleepingPluggedIn

### <a name="windows10generalconfigurationpreventinstallationofmatchingdeviceids"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceIDs 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

### <a name="windows10generalconfigurationpreventinstallationofmatchingdevicesetupclasses"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceSetupClasses 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

### <a name="windows10generalconfigurationprinterblockaddition"></a>Windows10GeneralConfiguration.PrinterBlockAddition 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Education/PreventAddingNewPrinters

### <a name="windows10generalconfigurationprinterdefaultname"></a>Windows10GeneralConfiguration.PrinterDefaultName 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Education/DefaultPrinterName

### <a name="windows10generalconfigurationprinternames"></a>Windows10GeneralConfiguration.PrinterNames 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Education/PrinterNames

### <a name="windows10generalconfigurationprivacyadvertisingid"></a>Windows10GeneralConfiguration.PrivacyAdvertisingId 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/privacy/DisableAdvertisingID

### <a name="windows10generalconfigurationprivacyautoacceptpairingandconsentprompts"></a>Windows10GeneralConfiguration.PrivacyAutoAcceptPairingAndConsentPrompts 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/privacy/AllowAutoAcceptPairingAndPrivacyConsentPrompts

### <a name="windows10generalconfigurationprivacyblockactivityfeed"></a>Windows10GeneralConfiguration.PrivacyBlockActivityFeed 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/privacy/EnableActivityFeed

### <a name="windows10generalconfigurationprivacyblockinputpersonalization"></a>Windows10GeneralConfiguration.PrivacyBlockInputPersonalization 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/privacy/AllowInputPersonalization

### <a name="windows10generalconfigurationprivacyblockpublishuseractivities"></a>Windows10GeneralConfiguration.PrivacyBlockPublishUserActivities 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/privacy/PublishUserActivities

### <a name="windows10generalconfigurationsafesearchfilter"></a>Windows10GeneralConfiguration.SafeSearchFilter 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Search/SafeSearchPermissions

### <a name="windows10generalconfigurationscreencaptureblocked"></a>Windows10GeneralConfiguration.ScreenCaptureBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowScreenCapture

### <a name="windows10generalconfigurationsearchblockdiacritics"></a>Windows10GeneralConfiguration.SearchBlockDiacritics 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/AllowUsingDiacritics

### <a name="windows10generalconfigurationsearchblockwebresults"></a>Windows10GeneralConfiguration.SearchBlockWebResults 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/DoNotUseWebResults

### <a name="windows10generalconfigurationsearchdisableautolanguagedetection"></a>Windows10GeneralConfiguration.SearchDisableAutoLanguageDetection 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/AlwaysUseAutoLangDetection

### <a name="windows10generalconfigurationsearchdisableindexerbackoff"></a>Windows10GeneralConfiguration.SearchDisableIndexerBackoff 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/DisableBackoff

### <a name="windows10generalconfigurationsearchdisableindexingencrypteditems"></a>Windows10GeneralConfiguration.SearchDisableIndexingEncryptedItems 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/AllowIndexingEncryptedStoresOrItems

### <a name="windows10generalconfigurationsearchdisableindexingremovabledrive"></a>Windows10GeneralConfiguration.SearchDisableIndexingRemovableDrive 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/DisableRemovableDriveIndexing

### <a name="windows10generalconfigurationsearchdisablelocation"></a>Windows10GeneralConfiguration.SearchDisableLocation 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/AllowSearchToUseLocation

### <a name="windows10generalconfigurationsearchdisableuselocation"></a>Windows10GeneralConfiguration.SearchDisableUseLocation 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/AllowSearchToUseLocation

### <a name="windows10generalconfigurationsearchenableautomaticindexsizemanangement"></a>Windows10GeneralConfiguration.SearchEnableAutomaticIndexSizeManangement 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/PreventIndexingLowDiskSpaceMB

### <a name="windows10generalconfigurationsearchenableremotequeries"></a>Windows10GeneralConfiguration.SearchEnableRemoteQueries 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Search/PreventRemoteQueries

### <a name="windows10generalconfigurationsecurityblockazureadjoineddevicesautoencryption"></a>Windows10GeneralConfiguration.SecurityBlockAzureADJoinedDevicesAutoEncryption 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices

### <a name="windows10generalconfigurationsettingsblockaccountspage"></a>Windows10GeneralConfiguration.SettingsBlockAccountsPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockaddprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockAddProvisioningPackage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Security/AllowAddProvisioningPackage

### <a name="windows10generalconfigurationsettingsblockappspage"></a>Windows10GeneralConfiguration.SettingsBlockAppsPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockchangelanguage"></a>Windows10GeneralConfiguration.SettingsBlockChangeLanguage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/AllowLanguage

### <a name="windows10generalconfigurationsettingsblockchangepowersleep"></a>Windows10GeneralConfiguration.SettingsBlockChangePowerSleep 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/AllowPowerSleep

### <a name="windows10generalconfigurationsettingsblockchangeregion"></a>Windows10GeneralConfiguration.SettingsBlockChangeRegion 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/AllowRegion

### <a name="windows10generalconfigurationsettingsblockchangesystemtime"></a>Windows10GeneralConfiguration.SettingsBlockChangeSystemTime 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/AllowDateTime

### <a name="windows10generalconfigurationsettingsblockdevicespage"></a>Windows10GeneralConfiguration.SettingsBlockDevicesPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockeaseofaccesspage"></a>Windows10GeneralConfiguration.SettingsBlockEaseOfAccessPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockeditdevicename"></a>Windows10GeneralConfiguration.SettingsBlockEditDeviceName 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/AllowEditDeviceName

### <a name="windows10generalconfigurationsettingsblockgamingpage"></a>Windows10GeneralConfiguration.SettingsBlockGamingPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblocknetworkinternetpage"></a>Windows10GeneralConfiguration.SettingsBlockNetworkInternetPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockpersonalizationpage"></a>Windows10GeneralConfiguration.SettingsBlockPersonalizationPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockprivacypage"></a>Windows10GeneralConfiguration.SettingsBlockPrivacyPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockremoveprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockRemoveProvisioningPackage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Security/AllowRemoveProvisioningPackage

### <a name="windows10generalconfigurationsettingsblocksystempage"></a>Windows10GeneralConfiguration.SettingsBlockSystemPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblocktimelanguagepage"></a>Windows10GeneralConfiguration.SettingsBlockTimeLanguagePage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockupdatesecuritypage"></a>Windows10GeneralConfiguration.SettingsBlockUpdateSecurityPage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationshareduserappdataallowed"></a>Windows10GeneralConfiguration.SharedUserAppDataAllowed 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/AllowSharedUserAppData

### <a name="windows10generalconfigurationsmartscreenblockpromptoverride"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverride 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/PreventSmartScreenPromptOverride

### <a name="windows10generalconfigurationsmartscreenblockpromptoverrideforfiles"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverrideForFiles 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/PreventSmartScreenPromptOverrideForFiles

### <a name="windows10generalconfigurationsmartscreenenableappinstallcontrol"></a>Windows10GeneralConfiguration.SmartScreenEnableAppInstallControl 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/SmartScreen/EnableAppInstallControl

### <a name="windows10generalconfigurationstartblockunpinningappsfromtaskbar"></a>Windows10GeneralConfiguration.StartBlockUnpinningAppsFromTaskbar 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/NoPinningToTaskbar

### <a name="windows10generalconfigurationstartmenuapplistvisibility"></a>Windows10GeneralConfiguration.StartMenuAppListVisibility 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Start/HideAppList

### <a name="windows10generalconfigurationstartmenuhidechangeaccountsettings"></a>Windows10GeneralConfiguration.StartMenuHideChangeAccountSettings 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideChangeAccountSettings

### <a name="windows10generalconfigurationstartmenuhidefrequentlyusedapps"></a>Windows10GeneralConfiguration.StartMenuHideFrequentlyUsedApps 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideFrequentlyUsedApps

### <a name="windows10generalconfigurationstartmenuhidehibernate"></a>Windows10GeneralConfiguration.StartMenuHideHibernate 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideHibernate

### <a name="windows10generalconfigurationstartmenuhidelock"></a>Windows10GeneralConfiguration.StartMenuHideLock 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideLock

### <a name="windows10generalconfigurationstartmenuhidepowerbutton"></a>Windows10GeneralConfiguration.StartMenuHidePowerButton 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Start/HidePowerButton

### <a name="windows10generalconfigurationstartmenuhiderecentjumplists"></a>Windows10GeneralConfiguration.StartMenuHideRecentJumpLists 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideRecentJumplists

### <a name="windows10generalconfigurationstartmenuhiderecentlyaddedapps"></a>Windows10GeneralConfiguration.StartMenuHideRecentlyAddedApps 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideRecentlyAddedApps

### <a name="windows10generalconfigurationstartmenuhiderestartoptions"></a>Windows10GeneralConfiguration.StartMenuHideRestartOptions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Start/HideRestart

### <a name="windows10generalconfigurationstartmenuhideshutdown"></a>Windows10GeneralConfiguration.StartMenuHideShutDown 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideShutDown

### <a name="windows10generalconfigurationstartmenuhidesignout"></a>Windows10GeneralConfiguration.StartMenuHideSignOut 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideSignOut

### <a name="windows10generalconfigurationstartmenuhidesleep"></a>Windows10GeneralConfiguration.StartMenuHideSleep 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideSleep

### <a name="windows10generalconfigurationstartmenuhideswitchaccount"></a>Windows10GeneralConfiguration.StartMenuHideSwitchAccount 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/HideSwitchAccount

### <a name="windows10generalconfigurationstartmenuhideusertile"></a>Windows10GeneralConfiguration.StartMenuHideUserTile 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Start/HideUserTile

### <a name="windows10generalconfigurationstartmenulayoutedgeassetsxml"></a>Windows10GeneralConfiguration.StartMenuLayoutEdgeAssetsXml 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/Start/ImportEdgeAssets

### <a name="windows10generalconfigurationstartmenulayoutxml"></a>Windows10GeneralConfiguration.StartMenuLayoutXml 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/StartLayout

### <a name="windows10generalconfigurationstartmenumode"></a>Windows10GeneralConfiguration.StartMenuMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/ForceStartSize

### <a name="windows10generalconfigurationstartmenupinnedfolderdocuments"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDocuments 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderDocuments

### <a name="windows10generalconfigurationstartmenupinnedfolderdownloads"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDownloads 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderDownloads

### <a name="windows10generalconfigurationstartmenupinnedfolderfileexplorer"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderFileExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderFileExplorer

### <a name="windows10generalconfigurationstartmenupinnedfolderhomegroup"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderHomeGroup 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderHomeGroup

### <a name="windows10generalconfigurationstartmenupinnedfoldermusic"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderMusic 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderMusic

### <a name="windows10generalconfigurationstartmenupinnedfoldernetwork"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderNetwork 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderNetwork

### <a name="windows10generalconfigurationstartmenupinnedfolderpersonalfolder"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPersonalFolder 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderPersonalFolder

### <a name="windows10generalconfigurationstartmenupinnedfolderpictures"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPictures 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderPictures

### <a name="windows10generalconfigurationstartmenupinnedfoldersettings"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderSettings 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderSettings

### <a name="windows10generalconfigurationstartmenupinnedfoldervideos"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderVideos 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Start/AllowPinnedFolderVideos

### <a name="windows10generalconfigurationstorageblockremovablestorage"></a>Windows10GeneralConfiguration.StorageBlockRemovableStorage 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/System/AllowStorageCard

### <a name="windows10generalconfigurationstoragerequiremobiledeviceencryption"></a>Windows10GeneralConfiguration.StorageRequireMobileDeviceEncryption 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Security/RequireDeviceEncryption

### <a name="windows10generalconfigurationstoragerestrictappdatatosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppDataToSystemVolume 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/RestrictAppDataToSystemVolume

### <a name="windows10generalconfigurationstoragerestrictappinstalltosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppInstallToSystemVolume 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/RestrictAppToSystemVolume

### <a name="windows10generalconfigurationsystembootstartdriverinitialization"></a>Windows10GeneralConfiguration.SystemBootStartDriverInitialization 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/System/BootStartDriverInitialization

### <a name="windows10generalconfigurationsystemtelemetryproxyserver"></a>Windows10GeneralConfiguration.SystemTelemetryProxyServer 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/System/TelemetryProxy

### <a name="windows10generalconfigurationtaskmanagerblockendtask"></a>Windows10GeneralConfiguration.TaskManagerBlockEndTask 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/taskmanager/AllowEndTask

### <a name="windows10generalconfigurationtenantlockdownrequirenetworkduringoutofboxexperience"></a>Windows10GeneralConfiguration.TenantLockdownRequireNetworkDuringOutOfBoxExperience 
**CSP**:./Vendor/MSFT/TenantLockdown  
**URI offset**:/RequireNetworkInOOBE

### <a name="windows10generalconfigurationusbblocked"></a>Windows10GeneralConfiguration.UsbBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Connectivity/AllowUSBConnection

### <a name="windows10generalconfigurationvoicerecordingblocked"></a>Windows10GeneralConfiguration.VoiceRecordingBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowVoiceRecording

### <a name="windows10generalconfigurationwebrtcblocklocalhostipaddress"></a>Windows10GeneralConfiguration.WebRtcBlockLocalhostIpAddress 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/PreventUsingLocalHostIPAddressForWebRTC

### <a name="windows10generalconfigurationwifiblockautomaticconnecthotspots"></a>Windows10GeneralConfiguration.WiFiBlockAutomaticConnectHotspots 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WiFi/AllowAutoConnectToWiFiSenseHotspots

### <a name="windows10generalconfigurationwifiblocked"></a>Windows10GeneralConfiguration.WiFiBlocked 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WiFi/AllowWiFi

### <a name="windows10generalconfigurationwifiblockmanualconfiguration"></a>Windows10GeneralConfiguration.WiFiBlockManualConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WiFi/AllowManualWiFi/Configuration

### <a name="windows10generalconfigurationwifiscaninterval"></a>Windows10GeneralConfiguration.WiFiScanInterval 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WiFi/WLANScanMode

### <a name="windows10generalconfigurationwindowslogonlocalusersondomainjoinedcomputers"></a>Windows10GeneralConfiguration.WindowsLogOnLocalUsersOnDomainJoinedComputers 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/WindowsLogon/EnumerateLocalUsersOnDomainJoinedComputers

### <a name="windows10generalconfigurationwindowsspotlightblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockConsumerSpecificFeatures 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowWindowsConsumerFeatures

### <a name="windows10generalconfigurationwindowsspotlightblocked"></a>Windows10GeneralConfiguration.WindowsSpotlightBlocked 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowWindowsSpotlight

### <a name="windows10generalconfigurationwindowsspotlightblockonactioncenter"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockOnActionCenter 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowWindowsSpotlightOnActionCenter

### <a name="windows10generalconfigurationwindowsspotlightblocktailoredexperiences"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockTailoredExperiences 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowTailoredExperiencesWithDiagnosticData

### <a name="windows10generalconfigurationwindowsspotlightblockthirdpartynotifications"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockThirdPartyNotifications 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowThirdPartySuggestionsInWindowsSpotlight

### <a name="windows10generalconfigurationwindowsspotlightblockwelcomeexperience"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWelcomeExperience 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowWindowsSpotlightWindowsWelcomeExperience

### <a name="windows10generalconfigurationwindowsspotlightblockwindowstips"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWindowsTips 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/Experience/AllowWindowsTips

### <a name="windows10generalconfigurationwindowsspotlightconfigureonlockscreen"></a>Windows10GeneralConfiguration.WindowsSpotlightConfigureOnLockScreen 
**CSP**:./User/vendor/MSFT/Policy  
**URI offset**:/config/Experience/ConfigureWindowsSpotlightOnLockScreen

### <a name="windows10generalconfigurationwindowsstoreblockautoupdate"></a>Windows10GeneralConfiguration.WindowsStoreBlockAutoUpdate 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/AllowAppStoreAutoUpdate

### <a name="windows10generalconfigurationwindowsstoreblocked"></a>Windows10GeneralConfiguration.WindowsStoreBlocked 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/AllowStore

### <a name="windows10generalconfigurationwindowsstoreenableprivatestoreonly"></a>Windows10GeneralConfiguration.WindowsStoreEnablePrivateStoreOnly 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/ApplicationManagement/RequirePrivateStoreOnly

### <a name="windows10generalconfigurationwirelessdisplayblockprojectiontothisdevice"></a>Windows10GeneralConfiguration.WirelessDisplayBlockProjectionToThisDevice 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WirelessDisplay/AllowProjectionToPC

### <a name="windows10generalconfigurationwirelessdisplayblockuserinputfromreceiver"></a>Windows10GeneralConfiguration.WirelessDisplayBlockUserInputFromReceiver 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WirelessDisplay/AllowUserInputFromWirelessDisplayReceiver

### <a name="windows10generalconfigurationwirelessdisplayrequirepinforpairing"></a>Windows10GeneralConfiguration.WirelessDisplayRequirePinForPairing 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/WirelessDisplay/RequirePINForPairing

### <a name="windows10networkboundaryconfigurationwindowsnetworkisolationpolicy"></a>Windows10NetworkBoundaryConfiguration.WindowsNetworkIsolationPolicy 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/NetworkIsolation/EnterpriseCloudResources,/config/NetworkIsolation/EnterpriseIPRange,/config/NetworkIsolation/EnterpriseIPRangesAreAuthoritative,/config/NetworkIsolation/ EnterpriseInternalProxyServers, /Config/NetworkIsolation/EnterpriseNetworkDomainNames, /Config/NetworkIsolation/EnterpriseProxyServers, /Config/NetworkIsolation/EnterpriseProxyServersAreAuthoritative, /Config/NetworkIsolation/ NeutralResources

### <a name="windows10policyoverrideconfigurationprefermdmovergrouppolicy"></a>Windows10PolicyOverrideConfiguration.PreferMdmOverGroupPolicy 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/ControlPolicyConflict/MDMWinsOverGP

### <a name="windows10secureassessmentconfigurationallowprinting"></a>Windows10SecureAssessmentConfiguration.AllowPrinting 
**CSP**:./Vendor/MSFT/SecureAssessment  
**URI offset**:/RequirePrinting

### <a name="windows10secureassessmentconfigurationallowscreencapture"></a>Windows10SecureAssessmentConfiguration.AllowScreenCapture 
**CSP**:./Vendor/MSFT/SecureAssessment  
**URI offset**:/AllowScreenMonitoring

### <a name="windows10secureassessmentconfigurationallowtextsuggestion"></a>Windows10SecureAssessmentConfiguration.AllowTextSuggestion 
**CSP**:./Vendor/MSFT/SecureAssessment  
**URI offset**:/AllowTextSuggestions

### <a name="windows10secureassessmentconfigurationconfigurationaccount"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccount 
**CSP**:./Vendor/MSFT/SecureAssessment  
**URI offset**:/TesterAccount

### <a name="windows10secureassessmentconfigurationconfigurationaccounttype"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccountType 
**CSP**:./Vendor/MSFT/SecureAssessment  
**URI offset**:/TesterAccount

### <a name="windows10secureassessmentconfigurationlaunchuri"></a>Windows10SecureAssessmentConfiguration.LaunchUri 
**CSP**:./Vendor/MSFT/SecureAssessment  
**URI offset**:/LaunchURI

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsblocktelemetry"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsBlockTelemetry 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/MOMAgent/WorkspaceID e/MOMAgent/WorkspaceKey

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspaceid"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceId 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/MOMAgent/WorkspaceID

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspacekey"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceKey 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/MOMAgent/WorkspaceKey

### <a name="windows10teamgeneralconfigurationconnectappblockautolaunch"></a>Windows10TeamGeneralConfiguration.ConnectAppBlockAutoLaunch 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/InBoxApps/Connect/AutoLaunch

### <a name="windows10teamgeneralconfigurationdeviceaccountblockexchangeservices"></a>Windows10TeamGeneralConfiguration.DeviceAccountBlockExchangeServices 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/DeviceAccount/email

### <a name="windows10teamgeneralconfigurationdeviceaccountemailaddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountEmailAddress 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/DeviceAccount/email

### <a name="windows10teamgeneralconfigurationdeviceaccountexchangeserveraddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountExchangeServerAddress 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/DeviceAccount/ExchangeServer

### <a name="windows10teamgeneralconfigurationdeviceaccountrequirepasswordrotation"></a>Windows10TeamGeneralConfiguration.DeviceAccountRequirePasswordRotation 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/DeviceAccount/PasswordRotationEnabled

### <a name="windows10teamgeneralconfigurationdeviceaccountsessioninitiationprotocoladdress"></a>Windows10TeamGeneralConfiguration.DeviceAccountSessionInitiationProtocolAddress 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/DeviceAccount/SipAddress

### <a name="windows10teamgeneralconfigurationmaintenancewindowblocked"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowBlocked 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/MaintenanceHoursSimple/hours/Duration e/MaintenanceHoursSimple/hours/StartTime

### <a name="windows10teamgeneralconfigurationmaintenancewindowdurationinhours"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowDurationInHours 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/MaintenanceHoursSimple/hours/Duration

### <a name="windows10teamgeneralconfigurationmaintenancewindowstarttime"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowStartTime 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/MaintenanceHoursSimple/hours/StartTime

### <a name="windows10teamgeneralconfigurationmiracastblocked"></a>Windows10TeamGeneralConfiguration.MiracastBlocked 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/InBoxApps/WirelessProjection/Enabled

### <a name="windows10teamgeneralconfigurationmiracastchannel"></a>Windows10TeamGeneralConfiguration.MiracastChannel 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/InBoxApps/WirelessProjection/Channel

### <a name="windows10teamgeneralconfigurationmiracastrequirepin"></a>Windows10TeamGeneralConfiguration.MiracastRequirePin 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/InBoxApps/WirelessProjection/PINRequired

### <a name="windows10teamgeneralconfigurationsettingsblockmymeetingsandfiles"></a>Windows10TeamGeneralConfiguration.SettingsBlockMyMeetingsAndFiles 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/Properties/DoNotShowMyMeetingsAndFiles

### <a name="windows10teamgeneralconfigurationsettingsblocksessionresume"></a>Windows10TeamGeneralConfiguration.SettingsBlockSessionResume 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/Properties/AllowSessionResume

### <a name="windows10teamgeneralconfigurationsettingsblocksigninsuggestions"></a>Windows10TeamGeneralConfiguration.SettingsBlockSigninSuggestions 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/Properties/DisableSigninSuggestions

### <a name="windows10teamgeneralconfigurationsettingsdefaultvolume"></a>Windows10TeamGeneralConfiguration.SettingsDefaultVolume 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/Properties/DefaultVolume

### <a name="windows10teamgeneralconfigurationsettingsscreentimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsScreenTimeoutInMinutes 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/Properties/ScreenTimeout

### <a name="windows10teamgeneralconfigurationsettingssessiontimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSessionTimeoutInMinutes 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/Properties/SessionTimeout

### <a name="windows10teamgeneralconfigurationsettingssleeptimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSleepTimeoutInMinutes 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/Properties/SleepTimeout

### <a name="windows10teamgeneralconfigurationwelcomescreenbackgroundimageurl"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBackgroundImageUrl 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/InBoxApps/Welcome/CurrentBackgroundPath

### <a name="windows10teamgeneralconfigurationwelcomescreenblockautomaticwakeup"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBlockAutomaticWakeUp 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/InBoxApps/Welcome/AutoWakeScreen

### <a name="windows10teamgeneralconfigurationwelcomescreenmeetinginformation"></a>Windows10TeamGeneralConfiguration.WelcomeScreenMeetingInformation 
**CSP**:./Vendor/MSFT/SurfaceHub  
**URI offset**:/InBoxApps/Welcome/MeetingInfoOption

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI offset**:/Offboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingFilename
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI offset**:/Offboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI offset**:/onboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingFilename 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI offset**:/onboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationallowsamplesharing"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AllowSampleSharing 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI offset**:/Configuration/SampleSharing

### <a name="windowsdefenderadvancedthreatprotectionconfigurationenableexpeditedtelemetryreporting"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.EnableExpeditedTelemetryReporting 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI offset**:/Configuration/TelemetryReportingFrequency

### <a name="windowsdeliveryoptimizationconfigurationdeliveryoptimizationmode"></a>WindowsDeliveryOptimizationConfiguration.DeliveryOptimizationMode 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/DeliveryOptimization/DODownloadMode

### <a name="windowsidentityprotectionconfigurationenhancedantispoofingforfacialfeaturesenabled"></a>WindowsIdentityProtectionConfiguration.EnhancedAntiSpoofingForFacialFeaturesEnabled 
**CSP**:./Device/vendor/MSFT/PassportForWork  
**URI offset**:/Biometrics/FacialFeaturesUseEnhancedAntiSpoofing

### <a name="windowsidentityprotectionconfigurationpinexpirationindays"></a>WindowsIdentityProtectionConfiguration.PinExpirationInDays 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/PINComplexity/expiration

### <a name="windowsidentityprotectionconfigurationpinlowercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinLowercaseCharactersUsage 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/PINComplexity/LowercaseLetters

### <a name="windowsidentityprotectionconfigurationpinmaximumlength"></a>WindowsIdentityProtectionConfiguration.PinMaximumLength 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/PINComplexity/MaximumPINLength

### <a name="windowsidentityprotectionconfigurationpinminimumlength"></a>WindowsIdentityProtectionConfiguration.PinMinimumLength 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/PINComplexity/MinimumPINLength

### <a name="windowsidentityprotectionconfigurationpinpreviousblockcount"></a>WindowsIdentityProtectionConfiguration.PinPreviousBlockCount 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/PINComplexity/History

### <a name="windowsidentityprotectionconfigurationpinrecoveryenabled"></a>WindowsIdentityProtectionConfiguration.PinRecoveryEnabled 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/EnablePinRecovery

### <a name="windowsidentityprotectionconfigurationpinspecialcharactersusage"></a>WindowsIdentityProtectionConfiguration.PinSpecialCharactersUsage 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/PINComplexity/SpecialCharacters

### <a name="windowsidentityprotectionconfigurationpinuppercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinUppercaseCharactersUsage
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/PINComplexity/UppercaseLetters

### <a name="windowsidentityprotectionconfigurationsecuritydevicerequired"></a>WindowsIdentityProtectionConfiguration.SecurityDeviceRequired 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/RequireSecurityDevice

### <a name="windowsidentityprotectionconfigurationunlockwithbiometricsenabled"></a>WindowsIdentityProtectionConfiguration.UnlockWithBiometricsEnabled 
**CSP**:./Device/vendor/MSFT/PassportForWork  
**URI offset**:/Biometrics/UseBiometrics

### <a name="windowsidentityprotectionconfigurationusecertificatesforonpremisesauthenabled"></a>WindowsIdentityProtectionConfiguration.UseCertificatesForOnPremisesAuthEnabled 
**CSP**:./Device/vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/UseCertificateForOnPremAuth

### <a name="windowsidentityprotectionconfigurationwindowshelloforbusinessblocked"></a>WindowsIdentityProtectionConfiguration.WindowsHelloForBusinessBlocked 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI offset**:/{AADTenantId}/Policies/UsePassportForWork

### <a name="windowskioskconfigurationedgekioskenablepublicbrowsing"></a>WindowsKioskConfiguration.EdgeKioskEnablePublicBrowsing 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ConfigureKioskMode

### <a name="windowskioskconfigurationedgekioskresetafteridletimeinminutes"></a>WindowsKioskConfiguration.EdgeKioskResetAfterIdleTimeInMinutes 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/browser/ConfigureKioskResetAfterIdleTimeout

### <a name="windowskioskconfigurationkioskbrowserblockedurlexceptions"></a>WindowsKioskConfiguration.KioskBrowserBlockedUrlExceptions 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/KioskBrowser/BlockedUrlExceptions

### <a name="windowskioskconfigurationkioskbrowserblockedurls"></a>WindowsKioskConfiguration.KioskBrowserBlockedURLs 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/KioskBrowser/BlockedUrls

### <a name="windowskioskconfigurationkioskbrowserdefaulturl"></a>WindowsKioskConfiguration.KioskBrowserDefaultUrl 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/KioskBrowser/DefaultUrl

### <a name="windowskioskconfigurationkioskbrowserenableendsessionbutton"></a>WindowsKioskConfiguration.KioskBrowserEnableEndSessionButton 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/KioskBrowser/EnableEndSessionButton

### <a name="windowskioskconfigurationkioskbrowserenablehomebutton"></a>WindowsKioskConfiguration.KioskBrowserEnableHomeButton 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/KioskBrowser/EnableHomeButton

### <a name="windowskioskconfigurationkioskbrowserenablenavigationbuttons"></a>WindowsKioskConfiguration.KioskBrowserEnableNavigationButtons 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/KioskBrowser/EnableNavigationButtons

### <a name="windowskioskconfigurationkioskbrowserrestartonidletimeinminutes"></a>WindowsKioskConfiguration.KioskBrowserRestartOnIdleTimeInMinutes 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/KioskBrowser/KioskBrowserRestartOnIdleTimeInMinutes

### <a name="windowsupdateforbusinessconfigurationautomaticupdatemode"></a>WindowsUpdateForBusinessConfiguration.AutomaticUpdateMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/AllowAutoUpdate

### <a name="windowsupdateforbusinessconfigurationautorestartnotificationdismissal"></a>WindowsUpdateForBusinessConfiguration.AutoRestartNotificationDismissal 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/AutoRestartRequiredNotificationDismissal

### <a name="windowsupdateforbusinessconfigurationbusinessreadyupdatesonly"></a>WindowsUpdateForBusinessConfiguration.BusinessReadyUpdatesOnly 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/BranchReadinessLevel

### <a name="windowsupdateforbusinessconfigurationdeliveryoptimizationmode"></a>WindowsUpdateForBusinessConfiguration.DeliveryOptimizationMode 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/DeliveryOptimization/DODownloadMode

### <a name="windowsupdateforbusinessconfigurationdriversexcluded"></a>WindowsUpdateForBusinessConfiguration.DriversExcluded 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/ExcludeWUDriversInQualityUpdate

### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineForFeatureUpdatesInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/EngagedRestartDeadlineForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/EngagedRestartDeadline

### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleForFeatureUpdatesInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/EngagedRestartSnoozeScheduleForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/EngagedRestartSnoozeSchedule

### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleForFeatureUpdatesInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/EngagedRestartTransitionScheduleForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/EngagedRestartTransitionSchedule

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesDeferralPeriodInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/DeferFeatureUpdatesPeriodInDays

### <a name="windowsupdateforbusinessconfigurationfeatureupdatespaused"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPaused 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/PauseFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationfeatureupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPauseStartDateTime 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/PauseFeatureUpdatesStartTime

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackStartDateTime
**CSP**: N/A-API Graph solo **URI di offset**: N/A-solo API Graph

### <a name="windowsupdateforbusinessconfigurationfeatureupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesWillBeRolledBack 
**CSP**: N/A-API Graph solo **URI di offset**: N/A-solo API Graph

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackwindowindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackWindowInDays
**CSP**: N/A-API Graph solo **URI di offset**: N/A-solo API Graph

### <a name="windowsupdateforbusinessconfigurationinstallationschedule"></a>WindowsUpdateForBusinessConfiguration.InstallationSchedule
**CSP**:./Device/vendor/MSFT/Policy **URI offset**:/config/update/ActiveHoursStart,/config/update/ActiveHoursEnd,/config/update/ScheduledInstallDay,/config/update/ScheduledInstallTime

### <a name="windowsupdateforbusinessconfigurationmicrosoftupdateserviceallowed"></a>WindowsUpdateForBusinessConfiguration.MicrosoftUpdateServiceAllowed 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/AllowMUUpdateService

### <a name="windowsupdateforbusinessconfigurationpreviewbuildsetting"></a>WindowsUpdateForBusinessConfiguration.PreviewBuildSetting 
**CSP**:./Vendor/MSFT/Policy  
**URI offset**:/config/update/ManagePreviewBuilds

### <a name="windowsupdateforbusinessconfigurationqualityupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesDeferralPeriodInDays 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/DeferQualityUpdatesPeriodInDays

### <a name="windowsupdateforbusinessconfigurationqualityupdatespaused"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPaused 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/PauseQualityUpdates

### <a name="windowsupdateforbusinessconfigurationqualityupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPauseStartDateTime 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/PauseQualityUpdatesStartTime

### <a name="windowsupdateforbusinessconfigurationqualityupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesRollbackStartDateTime
**CSP**: N/A-API Graph solo **URI di offset**: N/A-solo API Graph

### <a name="windowsupdateforbusinessconfigurationqualityupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesWillBeRolledBack 
**CSP**: N/A-API Graph solo **URI di offset**: N/A-solo API Graph

### <a name="windowsupdateforbusinessconfigurationscheduleimminentrestartwarninginminutes"></a>WindowsUpdateForBusinessConfiguration.ScheduleImminentRestartWarningInMinutes 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/ScheduleImminentRestartWarning

### <a name="windowsupdateforbusinessconfigurationschedulerestartwarninginhours"></a>WindowsUpdateForBusinessConfiguration.ScheduleRestartWarningInHours 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/ScheduleRestartWarning

### <a name="windowsupdateforbusinessconfigurationskipchecksbeforerestart"></a>WindowsUpdateForBusinessConfiguration.SkipChecksBeforeRestart 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/SetEDURestart

### <a name="windowsupdateforbusinessconfigurationupdateweeks"></a>WindowsUpdateForBusinessConfiguration.UpdateWeeks 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/ScheduledInstallEveryWeek,/config/update/ScheduledInstallFirstWeek,/config/update/ScheduledInstallFourthWeek,/config/update/ScheduledInstallSecondWeek,/config/update/ScheduledInstallThirdWeek

### <a name="windowsupdateforbusinessconfigurationuserpauseaccess"></a>WindowsUpdateForBusinessConfiguration.UserPauseAccess 
**CSP**:./Device/vendor/MSFT/Policy  
**URI offset**:/config/update/SetDisablePauseUXAccess


## <a name="next-steps"></a>Passaggi successivi

- [Panoramica della configurazione del dispositivo](device-profiles.md)
- [Riferimento al provider del servizio di configurazione](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (apre un altro sito docs)
