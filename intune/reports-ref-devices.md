---
title: Devices nel data warehouse di Intune | Microsoft Docs
description: "Argomento di riferimento per la categoria Devices delle raccolte di entità nell'API data warehouse di Intune."
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f304e07de7ceefb09152aeb30d113c378e716d38
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="reference-for-devices-entities"></a>Informazioni di riferimento per le entità della categoria Devices

La categoria **Devices** contiene le entità per i dispositivi mobili che tengono traccia delle informazioni come:

  -  Tipo di dispositivo
  -  Registrazione del dispositivo e stato della registrazione
  -  Proprietà del dispositivo
  -  Stato gestione del dispositivo
  -  Appartenenza del dispositivo allo stato di Azure AD
  -  Stato registrazione
  -  Informazioni cronologiche sul dispositivo
  -  Inventario delle app sul dispositivo

## <a name="devicetypes"></a>DeviceTypes

L'entità **DeviceTypes** rappresenta il tipo di dispositivo a cui fanno riferimento altre entità di data warehouse. Il tipo di dispositivo descrive in genere il modello o il produttore del dispositivo oppure una combinazione di entrambi.

| Proprietà  | Descrizione |
|---------|------------|
| DeviceTypeID |Identificatore univoco tipo di dispositivo |
| DeviceTypeKey |Identificatore univoco del tipo di dispositivo nel data warehouse - chiave surrogata |
| DeviceTypeName |Tipo di dispositivo |

## <a name="example"></a>Esempio

| deviceTypeID  | Name | Descrizione |
|---------|------------|--------|
| 0 |Desktop |Dispositivo Windows Desktop |
| 1 |WindowsRT |Dispositivo WindowsRT |
| 2 |WinMO6 |Dispositivo Windows Mobile 6.0 |
| 3 |Nokia |Dispositivo Nokia |
| 4 |WindowsPhone |Dispositivo Windows Phone |
| 5 |Mac |Dispositivo Mac |
| 6 |WinCE |Dispositivo Windows CE |
| 7 |WinEmbedded |Dispositivo con Windows Embedded |
| 8 |IPhone |Dispositivo iPhone |
| 9 |IPad |Dispositivo iPad |
| 10 |IPod |Dispositivo iPod |
| 11 |Android |Dispositivo Android gestito con l'amministratore del dispositivo |
| 12 |ISocConsumer |Dispositivo consumer iSoc |
| 14 |MacMDM |Dispositivo Mac OS X gestito con l'agente MDM incorporato |
| 15 |HoloLens |Dispositivo Holo Lens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android gestito con il profilo proprietario Android for Work |
| 100 |Blackberry |Dispositivo BlackBerry |
| 101 |Palm |Dispositivo palmare |
| 255 |Sconosciuto |Tipo di dispositivo sconosciuto |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

L'entità **ClientRegistrationStateTypes** rappresenta il tipo di registrazione cui fanno riferimento altre tabelle di data warehouse.

| Proprietà  | Descrizione |
|---------|------------|
| clientRegisterationStateID |Identificatore univoco per lo stato di registrazione |
| clientRegisterationStateKey |Identificatore univoco dello stato di registrazione nel data warehouse - chiave surrogata |
| clientRegisterationStateName |Stato di registrazione |

## <a name="example"></a>Esempio

| ClientRegisterationStateID  | Name | Descrizione |
|---------|------------|--------|
| 0 |NotRegistered |Non registrato |
| 1 |SMSIDConflict |Conflitto ID SMS |
| 2 |Registrato |Registrato |
| 3 |Revoked |Lo stato indica che l'amministratore IT ha bloccato il client e che il client può essere sbloccato. Un dispositivo può anche essere nello stato Revoked dopo la cancellazione o il ritiro. |
| 4 |KeyConflict |Conflitto di chiave |
| 5 |ApprovalPending |Approvazione in sospeso |
| 6 |ResetCert |Reimpostazione certificato |
| 7 |NotRegisteredPendingEnrollment |Non registrato con registrazione in sospeso |
| 8 |Sconosciuto |Stato sconosciuto |

## <a name="enrollmenttypes"></a>EnrollmentTypes

L'entità **EnrollmentTypes** indica in che modo è stato registrato un dispositivo. Il tipo di registrazione acquisisce il metodo di registrazione. Gli esempi elencano i diversi tipi di registrazione e il relativo significato.

| Proprietà  | Descrizione |
|---------|------------|
| managementStateID |Identificatore univoco dello stato di gestione. |
| managementStateKey |Identificatore univoco dello stato di gestione nel data warehouse - chiave surrogata. |
| managementStateName |Indica lo stato dell'azione remota applicata al dispositivo. |

## <a name="example"></a>Esempio

| enrollmentTypeID  | Name | Descrizione |
|---------|------------|--------|
| 0 |Sconosciuto |Il tipo di registrazione non è stato raccolto |
| 1 |UserEnrollment |Registrazione avviata dall'utente |
| 2 |DeviceEnrollment |Registrazione del dispositivo con profilo senza utente associato |
| 3 |DeviceEnrollmentWithUDA |Registrazione del dispositivo con profilo UDA. |
| 4 |AzureDomainJoined |Registrazione del dispositivo avviata dall'utente tramite Azure Active Directory |
| 5 |UserEnrollmentWithServiceAccount |Registrazione avviata dall'utente tramite account del servizio |
| 6 |DepDeviceEnrollment |Registrazione del dispositivo DEP con profilo senza utente associato |
| 7 |DepDeviceEnrollmentWithUDA |Registrazione del dispositivo DEP con profilo UDA |
| 8 |AutoEnrollment |Registrazione combinata di DRS e MDM per lo scenario BYOD |

## <a name="ownertypes"></a>OwnerTypes

L'entità **EnrollmentTypes** indica se un dispositivo è aziendale, personale o sconosciuto.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| ownerTypeID |Identificatore univoco del tipo di proprietario. | |
| ownerTypeKey |Identificatore univoco del tipo di proprietario nel data warehouse, chiave surrogata. | |
| ownerTypeName |Rappresenta il tipo di proprietario dei dispositivi:  <br>Società - il dispositivo è di proprietà dell'azienda. <br>Personal - il dispositivo è di proprietà personale (BYOD).  <br>Unknown - nessuna informazione su questo dispositivo. |Company Personal Unknown |

## <a name="mdmstatuses"></a>MdmStatuses

L'entità **MdmStatuses** indica lo stato di conformità del dispositivo.

| Proprietà  | Descrizione |
|---------|------------|
| MdmStatusID |Identificatore univoco dello stato di conformità |
| MdmStatusKey |Identificatore univoco dello stato di conformità nel data warehouse - chiave surrogata | 
| ComplianceStatus |Stato di conformità del dispositivo. Deve avere uno dei valori nella tabella seguente. | 


## <a name="example"></a>Esempio

| MdmStatusID  | ComplianceStatus | Descrizione |
|---------|------------|--------|
| 0 |Sconosciuto |Lo stato di conformità del dispositivo è sconosciuto. |
| 1 |Conforme |Il dispositivo è conforme. |
| 2 |Non conforme |Il dispositivo non è conforme. |
| 3 |Conflitto |La conformità del dispositivo ha generato un conflitto. |
| 4 |Errore |Errore durante la lettura dello stato di conformità del dispositivo. |


## <a name="managementstates"></a>ManagementStates

L'entità **ManagementStates** fornisce informazioni dettagliate sullo stato del dispositivo. I dettagli possono rivelarsi utili nei casi in cui vengono applicate azioni remote, il dispositivo è jailbroken o rooted.

| Proprietà  | Descrizione |
|---------|------------|
| managementStateID | Identificatore univoco dello stato di gestione. |
| managementStateKey | Identificatore univoco dello stato di gestione nel data warehouse - chiave surrogata. |
| managementStateName | Indica lo stato dell'azione remota applicata al dispositivo. |

## <a name="example"></a>Esempio

| managementStateID  | Name | Descrizione |
|---------|------------|--------|
| 0 |Gestiti | Gestito senza azioni remote in sospeso. |
| 1 |RetirePending | C'è un comando di disattivazione in sospeso per il dispositivo. |
| 2 |RetireFailed | Il comando di ritiro del dispositivo non è riuscito. |
| 3 |WipePending | C'è un comando di cancellazione in sospeso per il dispositivo. |
| 4 |WipeFailed | Il comando di cancellazione del dispositivo non è riuscito. |
| 5 |Unhealthy | Stato non integro. |
| 6 |DeletePending | C'è un comando di eliminazione in sospeso per il dispositivo. |
| 7 |RetireIssued | Al dispositivo è stato inviato un comando di ritiro. |
| 8 |WipeIssued | Al dispositivo è stato inviato un comando di cancellazione. |
| 9 |WipeCanceled | Il comando di cancellazione è stato annullato. |
| 10 |RetireCanceled | Il comando di ritiro è stato annullato. |
| 11 |Discovered | Il dispositivo è stato individuato recentemente da Intune; quando viene archiviato per la prima volta passa allo stato Gestito. |

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

L'entità **WorkPlaceJoinStateTypes** rappresenta lo stato Workplace Join di Azure Active Directory del dispositivo.  Il flusso di lavoro di registrazione può usare uno o più certificati per eseguire la verifica o l'autenticazione. Quando viene registrato un dispositivo WorkPlace, questi certificati vengono usati per convalidare il dispositivo e l'utente. Il rilascio di certificati viene fornito tramite un server SCEP (Simple Certificate Enrollment Protocol). I valori nell'entità indicano vari stati in cui potrebbe trovarsi un dispositivo durante il processo. Alcuni di questi stati includono l'errore di Workplace Join a causa del mancato rilascio di un certificato richiesto (da un server SCEP). Se un dispositivo non ha mai attraversato questo flusso di lavoro, il valore è impostato su Unknown.

| Proprietà  | Descrizione |
|---------|------------|
| WorkPlaceJoinStateID | Identificatore univoco dello stato di aggiunta all’area di lavoro |
| WorkPlaceJoinStateKey | Identificatore univoco dello stato di aggiunta all’area di lavoro nel data warehouse - chiave surrogata |
| WorkPlaceJoinStateName | Stato di aggiunta all’area di lavoro |

## <a name="example"></a>Esempio

| workPlaceJoinStateID  | Name | Descrizione |
|---------|------------|--------|
| 0 |Sconosciuto |Se un dispositivo non è stato aggiunto all'area di lavoro, è in stato Unknown |
| 1 |Operazione completata |Aggiunta all'area di lavoro riuscita |
| 2 |FailureToGetScepMetadata |Impossibile ottenere metadati SCEP |
| 3 |FailureToGetScepChallenge |Impossibile ottenere challenge SCEP |
| 4 |DeviceFailureToInstallScepCommand |Errore di installazione comando SCEP sul dispositivo |
| 5 |DeviceFailureToGetCertificate |Impossibile ottenere il certificato del dispositivo tramite SCEP |
| 6 |DeviceScepPending |Stato in sospeso; il dispositivo sta ancora eseguendo SCEP |
| 7 |DeviceScepFailed |Non è stato possibile installare il certificato tramite SCEP |
| 8 |AADValidationFailed |Impossibile convalidare, il dispositivo esiste in AAD |

## <a name="managementagenttypes"></a>ManagementAgentTypes

L'entità **ManagementAgentTypes** rappresenta gli agenti usati per gestire un dispositivo.

| Proprietà  | Descrizione |
|---------|------------|
| ManagementAgentTypeID | Identificatore univoco del tipo di agente di gestione. |
| ManagementAgentTypeKey | Identificatore univoco del tipo di agente di gestione nel data warehouse, chiave surrogata. |
| ManagementAgentTypeName |Indica il tipo di agente che viene usato per gestire il dispositivo. |

## <a name="example"></a>Esempio

| ManagementAgentTypeID  | Name | Descrizione |
|---------|------------|--------|
| 1 |EAS | Il dispositivo è gestito tramite Exchange Active Sync |
| 2 |MDM | Il dispositivo è gestito tramite un agente MDM |
| 3 |EasMdm | Il dispositivo è gestito da Exchange Active Sync e un agente MDM |
| 4 |IntuneClient | Il dispositivo è gestito dall'agente PC di Intune |
| 5 |EasIntuneClient | Il dispositivo è gestito da Exchange Active Sync e un agente PC di Intune |
| 8 |ConfigManagerClient | Il dispositivo è gestito dall'agente System Center Configuration Manager |
| 16 |Sconosciuto | Tipo di agente di gestione sconosciuto |

## <a name="devices"></a>Dispositivi

L'entità **Devices** elenca tutti i dispositivi registrati in gestione e le proprietà corrispondenti.

| Proprietà  | Descrizione |
|---------|------------|
| DeviceKey | Identificatore univoco del dispositivo nel data warehouse - chiave surrogata. |
| DeviceId | Identificatore univoco del dispositivo. |
| DeviceName | Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi. |
| DeviceTypeKey | Chiave dell'attributo tipo di dispositivo per il dispositivo. |
| ClientRegisterationStateKey | Chiave dell'attributo stato di registrazione client per il dispositivo. |
| OwnerTypeKey | Chiave dell'attributo tipo di proprietario per questo dispositivo: aziendale, personale o sconosciuto. |
| objectSourceKey | Ignorare questa colonna. |
| CreatedDate | Data di registrazione del dispositivo. |
| LastContact | Ultima archiviazione nota con Intune. |
| LastContactNotification | Ultima notifica di Intune nel dispositivo per l'archiviazione con Intune. |
| LastContactWorkplaceJoin | Il timestamp che indica l'ultimo stato Workplace Join noto per questo dispositivo. |
| ManagementAgentKey | Chiave dell'agente di gestione associato al dispositivo. |
| ManagementStateKey | Chiave dello stato di gestione associato al dispositivo, che indica lo stato più recente di un'azione remota o se è jailbroken/rooted. |
| ReferenceId | ID dispositivo in Azure Active Directory. |
| WorkPlaceJoinStateKey | Chiave dello stato di aggiunta all'area di lavoro associataa questo dispositivo. |
| CategoryId | Ignorare questa colonna. |
| EnrollmentTypeKey | Chiave del tipo di registrazione associata al dispositivo, che indica il metodo di registrazione. |
| CertExpirationDate | Data di scadenza del certificato di gestione MDM. |
| MdmStatusKey | Chiave per MdmStatus. |
| OSFamily | Famiglia del sistema operativo (Windows, iOS, Android, ecc.) |
| OSVersion | Versione sistema operativo |
| OSMajorVersion | Componente della versione principale del sistema operativo (major.minor.build.revision). |
| OSMinorVersion | Componente della versione secondaria del sistema operativo (major.minor.build.revision). |
| OSBuildNumber | Componente della versione build del sistema operativo (major.minor.build.revision). |
| OSRevisionNumber | Componente della versione di revisione del sistema operativo (major.minor.build.revision). |
| EasID | ID EAS del dispositivo, se è gestito da Exchange Active Sync. |
| GraphDeviceIsManaged | Ultimo stato di gestione impostato da Intune in Azure AD. |
| GraphDeviceIsCompliant | Ultimo stato di conformità impostato da Intune in Azure AD. |
| SerialNumber | Numero di serie del dispositivo, se disponibile. |
| EnrolledByUser | ID dell'utente che ha registrato il dispositivo che fa riferimento alla colonna userId nella tabella User. |
| RowLastModifiedDateTimeUTC | Data dell'ultima modifica apportata al record. |
| ProcessorArchitecture | Architettura del processore. |
| DeviceAction | Ultima azione del dispositivo eseguita. Ignorare per adesso. |
| Produttore | Produttore del dispositivo. |
| Modello | Modello del dispositivo. |
| LastPolicyUpdateUtc | Data dell'ultimo aggiornamento dei criteri del dispositivo. |
| LastExchangeStatusUtc | Data dell'ultima sincronizzazione del dispositivo con Exchange. |
| IsDeleted | Impostato su True se il dispositivo non è più gestito da Intune. Conserva l'ultimo stato noto. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

L'entità **DevicePropertyHistory** ha le stesse proprietà della tabella dei dispositivi e snapshot quotidiani del record di ciascun dispositivo per ognuno degli ultimi 90 giorni. La colonna DateKey indica il giorno per ogni riga.

| Proprietà  | Descrizione |
|---------|------------|
| DateKey |Riferimento alla tabella di data che indica il giorno. |
| DeviceKey |Identificatore univoco del dispositivo nel data warehouse - chiave surrogata. Si tratta di un riferimento alla tabella Device che contiene l'ID dispositivo Intune. |
| DeviceName |Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi. |
| DeviceTypeKey |Chiave dell'attributo tipo di dispositivo per il dispositivo. |
| ClientRegisterationStateKey |Chiave dell'attributo stato di registrazione client per il dispositivo. |
| OwnerTypeKey |Chiave dell'attributo tipo di proprietario per questo dispositivo: aziendale, personale o sconosciuto. |
| objectSourceKey |Ignorare questa colonna. |
| CreatedDate |Data di registrazione del dispositivo. |
| LastContact |Ultima archiviazione nota con Intune. |
| LastContactNotification |Ultima notifica di Intune nel dispositivo per l'archiviazione con Intune. |
| LastContactWorkplaceJoin |Il timestamp che indica l'ultimo stato Workplace Join noto per questo dispositivo. |
| ManagementAgentKey |Chiave dell'agente di gestione associato al dispositivo. |
| ManagementStateKey |Chiave dello stato di gestione associato al dispositivo, che indica lo stato più recente di un'azione remota o se è jailbroken/rooted. |
| ReferenceId |ID dispositivo in Azure Active Directory. |
| WorkPlaceJoinStateKey |Chiave dello stato di aggiunta all'area di lavoro associataa questo dispositivo. |
| CategoryId |Ignorare questa colonna. |
| EnrollmentTypeKey |Chiave del tipo di registrazione associata al dispositivo, che indica il metodo di registrazione. |
| CertExpirationDate |Data di scadenza del certificato di gestione MDM. |
| MdmStatusKey |Chiave per MdmStatus. |
| OSFamily |Famiglia del sistema operativo (Windows, iOS, Android, ecc.) |
| OSVersion |Versione del sistema operativo. |
| OSMajorVersion |Componente della versione principale del sistema operativo (major.minor.build.revision). |
| OSMinorVersion |Componente della versione secondaria del sistema operativo (major.minor.build.revision). |
| OSBuildNumber |Componente della versione build del sistema operativo (major.minor.build.revision). |
| OSRevisionNumber |Componente della versione di revisione del sistema operativo (major.minor.build.revision). |
| EasID |ID EAS del dispositivo, se è gestito da Exchange Active Sync. |
| GraphDeviceIsManaged |Ultimo stato di gestione impostato da Intune in Azure AD. |
| GraphDeviceIsCompliant |Ultimo stato di conformità impostato da Intune in Azure AD. |
| SerialNumber |Numero di serie del dispositivo, se disponibile. |
| EnrolledByUser |ID dell'utente che ha registrato il dispositivo che fa riferimento alla colonna userId nella tabella User. |
| RowLastModifiedDateTimeUTC |Data dell'ultima modifica apportata al record. |
| ProcessorArchitecture |Architettura del processore. |
| DeviceAction |Ultima azione del dispositivo eseguita. Ignorare per adesso. |
| Produttore |Produttore del dispositivo. |
| Modello |Modello del dispositivo. |
| LastPolicyUpdateUtc |Data dell'ultimo aggiornamento dei criteri del dispositivo. |
| LastExchangeStatusUtc |Data dell'ultima sincronizzazione del dispositivo con Exchange. |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

L'entità **MdmDeviceInventoryHistories** contiene gli snapshot quotidiani dei dati di inventario per i dispositivi gestiti da MDM negli ultimi 90 giorni. La colonna DateKey indica il giorno per la riga. Alcune proprietà potrebbero non essere applicabili o popolate per tutti i dispositivi, quindi consultare questa pagina per ulteriori dettagli. Per altre informazioni, vedere [Informazioni sui dispositivi con inventario in Microsoft Intune](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune).

| Proprietà  | Descrizione |
|---------|------------|
| DateKey | Riferimento alla tabella di data che indica il giorno. |
| DeviceKey |Identificatore univoco del dispositivo nel data warehouse - chiave surrogata. Si tratta di un riferimento alla tabella Device che contiene l'ID dispositivo Intune. |
| DeviceModel |Modello del dispositivo. |
| Sistema operativo |Sistema operativo del dispositivo. |
| DeviceName |Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi. |
| SoftwareVersion |Nella maggior parte dei casi si tratta della versione del sistema operativo, ad eccezione delle piattaforme Apple, dove è diversa dalla versione del sistema operativo. |
| Imei |Numero IMEI |
| HardwareInventoryTimeUtc |Prima volta in cui l'inventario è stato segnalato per questo dispositivo. |
| InventoryModifiedTimeUtc |Ultima archiviazione dell'inventario dall'acquisizione dello snapshot. |
| InventoryReportingTimeUtc |Ultima volta in cui è stato raccolto l'inventario per questo dispositivo. |
| ExchangeActiveSyncId |ID dispositivo Exchange ActiveSync. |
| ComputerSystemDescription |Descrizione del sistema. |
| ComputerSystemName |Nome del sistema. |
| ComputerSystemManufacturer |Produttore del sistema. |
| ComputerSystemModel |Modello di sistema. |
| UserName |Nome dell'utente. |
| OSType |Tipo di sistema operativo. |
| OSCaption |Didascalia del sistema operativo. |
| OSName |Nome del sistema operativo. |
| OSManufacturer |Produttore del sistema operativo. |
| OSProductSuite |Gruppo di prodotti del sistema operativo. |
| OSProductType |Tipo di prodotto del sistema operativo. |
| Impostazioni locali |Impostazioni locali del sistema operativo. |
| PhysicalMemoryCapacity |Capacità di memoria fisica (in byte). |
| PhysicalMemoryRemovable |Memoria rimovibile fisica (in byte). |
| SystemEnclosureChassisTypesInnerText |Definisce il tipo di chassis del sistema per questo dispositivo. I numeri indicano i valori seguenti:  <br>0 o vuoto = Sconosciuto   <br>1 = Desktop   <br>2 = Laptop  <br>3 = Workstation  <br>4 = Server aziendale  <br>100 = Telefono  <br>101 = Tablet  <br>102/103 = Tipo di dispositivo mobile sconosciuto |
| SystemEnclosureModel |Modello di chassis. |
| SystemEnclosureSerialNumber |Numero di serie dello chassis. |
| NetworkAdapterConfigurationText |Testo di configurazione della scheda di rete. |
| MacAddress |Indirizzo MAC. |
| SmsID |ID dispositivo di Intune. |
| CertExpiry |Data di scadenza del certificato di gestione MDM. |
| DeviceClientAgentVersion |Versione dell'agente client. |
| DeviceClientID |ID client del dispositivo. |
| SerialNumber |Numero di serie. |
| DeviceManufacturer |Produttore del dispositivo. |
| DMVersion |Versione DM. |
| FirmwareVersion |Versione del firmware. |
| HardwareVersion |Versione dell'hardware. |
| PlatformType |Tipo di piattaforma. |
| ProcessorLevel |Livello del processore. |
| ProcessorRevision |Revisione del processore. |
| Prodotto |Prodotto. |
| ProductVersion |Versione del prodotto. |
| OEM |OEM (Original Equipment Manufacturer). |
| DeviceBuildVersion |Versione build del dispositivo. |
| Meid |Identificativo di apparecchiatura mobile. |
| PhoneNumber |Numero di telefono. |
| SubscriberCarrierNetwork |Nome rete del gestore telefonico. |
| CellularTechnology |Tipo di rete del gestore telefonico (CDMA/GSM). |
| Imsi |Numero IMSI. |
| JailBroken |True se il dispositivo è jailbroken o rooted. |
| IsActivationLockEnabled |True se è il blocco attivazione è abilitato |
| DeviceType |Tipo di dispositivo |
| IsSupervised |È sotto supervisione |
| DeviceDisplayNumberOfColors |Numero di colori di visualizzazione del dispositivo |
| HorizontalResolution |Risoluzione orizzontale dello schermo del dispositivo |
| VerticalResolution |Risoluzione verticale dello schermo del dispositivo |
| StorageFree |Spazio di archiviazione disponibile (in byte) |
| StorageTotal |Spazio di archiviazione totale (in byte) |
| ProgramFree |Memoria programma libera (in byte) |
| ProgramTotal |Memoria programma totale (in byte) |
| RemovableStorageFree |Archivi rimovibili liberi (in byte) |
| RemovableStorageTotal |Archivi rimovibili totali (in byte) |
| DeviceMemoryDeviceCapacity |Capacità memoria del dispositivo |
| DeviceMemoryAvailableDeviceCapacity |Capacità disponibile memoria del dispositivo |
| DeviceOSVersion |Versione sistema operativo |
| DeviceOSPlatform |Piattaforma del sistema operativo |
| DeviceOSLanguage |Lingua del sistema operativo |
| PasswordMaxAttemptsBeforeWipe |Numero massimo di tentativi di password consentiti prima della cancellazione del dispositivo |
| PasswordMinComplexChars |Numero minimo di caratteri complessi richiesti per la password |
| PasswordMinLength |Lunghezza minima richiesta della password |
| PasswordHistory |Password - Numero minimo di password cronologiche non accettate |
| PasswordEnabled |Password - Abilitata? |
| PasswordExpiration |Password - Data di scadenza. |
| AllowRecoveryPassword |Consentire il ripristino della password. |
| PasswordAutoLockTimeout |Password - Timeout di blocco automatico. |
| PasswordType |Tipo di password. |
| BacklightACTimeout |Timeout retroilluminazione quando collegato a una fonte di alimentazione. |
| BacklightBatTimeout |Timeout retroilluminazione a batteria. |
| PowerBackupPercent |Percentuale di backup energia. |
| BatteryPercent |Percentuale di batteria rimanente. |
| PlatformID |ID piattaforma. |
| ExchangeDeviceID |ID dispositivo di Exchange. |
| SmsProcessorDescription |Descrizione del processore. |
| OwnerEmailAddress |Indirizzo di posta elettronica del proprietario. |
| DeviceOSName |Nome del sistema operativo. |
| WifiMac |Indirizzo MAC Wi-Fi. |
| EthernetMac |Indirizzo MAC Ethernet. |
| RequireEncryption |Indica se il dispositivo è crittografato o no. |
| ActivationLockBypassCode |Codice di bypass del blocco attivazione. |

## <a name="applicationinventory"></a>ApplicationInventory

L'entità **ApplicationInventory** elenca le app trovate nel dispositivo al momento della raccolta inventario.

| Proprietà  | Descrizione |
|---------|------------|
| DeviceKey |Riferimento alla tabella devices. |
| ApplicationKey |? (copiato da ExchangeDeviceService\DeviceApplication). |
| ApplicationName |? (copiato da ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion |? (copiato da ExchangeDeviceService\DeviceApplication). |
| BundleSize |? (copiato da ExchangeDeviceService\DeviceApplication). |
