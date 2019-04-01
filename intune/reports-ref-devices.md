---
title: Dispositivi - Data warehouse di Intune
titlesuffix: Microsoft Intune
description: Argomento di riferimento per la categoria Devices delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 29213400b5baf9705c188bb45b3666b65262d577
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358234"
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

### <a name="example"></a>Esempio

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
| 15 |HoloLens |Dispositivo HoloLens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android gestito con il profilo proprietario Android |
| 100 |Blackberry |Dispositivo BlackBerry |
| 101 |Palm |Dispositivo palmare |
| 255 |Sconosciuto |Tipo di dispositivo sconosciuto |

## <a name="enrollmentactivities"></a>enrollmentActivities 
L'entità **EnrollmentActivity** indica l'attività di una registrazione del dispositivo.

| Proprietà                      | Descrizione                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Chiave della data in cui è stata registrata questa attività di registrazione.               |
| deviceEnrollmentTypeKey       | Chiave del tipo della registrazione.                                        |
| enrollmentEventStatusKey      | Chiave dello stato che indica l'esito positivo o negativo della registrazione.    |
| enrollmentFailureCategoryKey  | Chiave della categoria di errore di registrazione (se la registrazione non è riuscita).        |
| enrollmentFailureReasonKey    | Chiave del motivo dell'errore di registrazione (se la registrazione non è riuscita).          |
| osVersion                     | Versione del sistema operativo del dispositivo.                               |
| count                         | Numero totale delle attività di registrazione corrispondenti alle classificazioni precedenti.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
L'entità **EnrollmentEventStatus** indica il risultato di una registrazione del dispositivo.

| Proprietà                   | Descrizione                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Identificatore univoco dello stato della registrazione nel data warehouse (chiave surrogata)  |
| enrollmentEventStatusName  | Nome dello stato della registrazione. Vedere gli esempi di seguito.                            |

### <a name="example"></a>Esempio

| enrollmentEventStatusName  | Descrizione                            |
|----------------------------|----------------------------------------|
| Operazione completata                    | Registrazione del dispositivo riuscita         |
| Operazione non riuscita                     | Registrazione del dispositivo non riuscita             |
| Non disponibile              | Lo stato di registrazione non è disponibile.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
L'entità **EnrollmentFailureCategory** indica perché la registrazione di un dispositivo non è riuscita. 

| Proprietà                       | Descrizione                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Identificatore univoco della categoria di errore della registrazione nel data warehouse (chiave surrogata)  |
| enrollmentFailureCategoryName  | Nome della categoria di errore della registrazione. Vedere gli esempi di seguito.                            |

### <a name="example"></a>Esempio

| enrollmentFailureCategoryName   | Descrizione                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Non applicabile                  | La categoria di errore della registrazione non è applicabile.                                                            |
| Non disponibile                   | La categoria di errore della registrazione non è disponibile.                                                             |
| Sconosciuto                         | Errore sconosciuto.                                                                                                |
| Autenticazione                  | Autenticazione non riuscita.                                                                                        |
| Autorizzazione                   | La chiamata è stata autenticata, ma non autorizzata alla registrazione.                                                         |
| AccountValidation               | Non è stato possibile convalidare l'account per la registrazione (account bloccato, registrazione non abilitata).                      |
| UserValidation                  | Non è stato possibile convalidare l'utente (utente inesistente, licenza mancante).                                           |
| DeviceNotSupported              | Il dispositivo non è supportato per la gestione di dispositivi mobili.                                                         |
| InMaintenance                   | L'account è in manutenzione.                                                                                    |
| BadRequest                      | Il client ha inviato una richiesta non riconosciuta/supportata dal servizio.                                        |
| FeatureNotSupported             | Le funzionalità usate da questa registrazione non sono supportate per questo account.                                        |
| EnrollmentRestrictionsEnforced  | Le restrizioni di registrazione configurate dall'amministratore hanno bloccato questa registrazione.                                          |
| ClientDisconnected              | Timeout del client o registrazione interrotta dall'utente finale.                                                        |
| UserAbandonment                 | La registrazione è stata abbandonata dall'utente finale. L'utente finale ha avviato l'onboarding, ma non è riuscito a completarlo in tempo utile.  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
L'entità **EnrollmentFailureReason** indica un motivo più dettagliato per un errore di registrazione del dispositivo all'interno di una determinata categoria di errore.  

| Proprietà                     | Descrizione                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Identificatore univoco del motivo dell'errore di registrazione nel data warehouse (chiave surrogata)  |
| enrollmentFailureReasonName  | Nome del motivo dell'errore di registrazione. Vedere gli esempi di seguito.                            |

### <a name="example"></a>Esempio

| enrollmentFailureReasonName      | Descrizione                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Non applicabile                   | La categoria di errore di registrazione non è applicabile.                                                                                                                                                       |
| Non disponibile                    | La categoria di errore di registrazione non è disponibile.                                                                                                                                                        |
| Sconosciuto                          | Errore sconosciuto.                                                                                                                                                                                         |
| UserNotLicensed                  | L'utente non è stato trovato in Intune o non ha una licenza valida.                                                                                                                                     |
| UserUnknown                      | L'utente non è noto a Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Un solo utente può registrare un dispositivo. Questo dispositivo è stato registrato in precedenza da un altro utente.                                                                                                                |
| EnrollmentOnboardingIssue        | L'autorità di gestione di dispositivi mobili (MDM) di Intune non è ancora configurata.                                                                                                                                 |
| AppleChallengeIssue              | L'installazione del profilo di gestione iOS è stato posticipata o non è riuscita.                                                                                                                                         |
| AppleOnboardingIssue             | Un certificato per le notifiche push MDM Apple è necessario per la registrazione in Intune.                                                                                                                                       |
| DeviceCap                        | L'utente ha provato a registrare più dispositivi del numero massimo consentito.                                                                                                                                        |
| AuthenticationRequirementNotMet  | Il servizio di registrazione di Intune non è riuscito ad autorizzare la richiesta.                                                                                                                                            |
| UnsupportedDeviceType            | Questo dispositivo non soddisfa i requisiti minimi per la registrazione in Intune.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | Questo dispositivo non è riuscito a eseguire la registrazione a causa di una regola configurata per le restrizioni della registrazione.                                                                                                                          |
| BulkDeviceNotPreregistered       | Non è stato possibile trovare il valore IMEI (International Mobile Equipment Identifier) o il numero di serie di questo dispositivo.  Senza questo identificatore, i dispositivi vengono riconosciuti come dispositivi di proprietà personale, che sono attualmente bloccati.  |
| FeatureNotSupported              | L'utente ha provato ad accedere a una funzionalità non ancora rilasciata per tutti i clienti o non compatibile con la configurazione specifica di Intune.                                                            |
| UserAbandonment                  | La registrazione è stata abbandonata dall'utente finale. L'utente finale ha avviato l'onboarding, ma non è riuscito a completarlo in tempo utile.                                                                                           |
| APNSCertificateExpired           | Non è possibile gestire i dispositivi Apple con un certificato per le notifiche push MDM Apple scaduto.                                                                                                                            |
## <a name="ownertypes"></a>OwnerTypes

L'entità **EnrollmentTypes** indica se un dispositivo è aziendale, personale o sconosciuto.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| ownerTypeID |Identificatore univoco del tipo di proprietario. | |
| ownerTypeKey |Identificatore univoco del tipo di proprietario nel data warehouse, chiave surrogata. | |
| ownerTypeName |Rappresenta il tipo di proprietario dei dispositivi:  <br>Aziendale - dispositivo è di proprietà aziendale. <br>Personal - il dispositivo è di proprietà personale (BYOD).  <br>Unknown - nessuna informazione su questo dispositivo. |Unknown personale aziendale |

> [!Note]  
> Per il `ownerTypeName` in Azure ad durante la creazione di gruppi dinamici per i dispositivi, è necessario impostare il valore del filtro `deviceOwnership` come `Company`. Per altre informazioni, vedere [regole per i dispositivi](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="managementstates"></a>ManagementStates

L'entità **ManagementStates** fornisce informazioni dettagliate sullo stato del dispositivo. I dettagli possono rivelarsi utili nei casi in cui vengono applicate azioni remote, il dispositivo è jailbroken o rooted.

| Proprietà  | Descrizione |
|---------|------------|
| managementStateID | Identificatore univoco dello stato di gestione. |
| managementStateKey | Identificatore univoco dello stato di gestione nel data warehouse - chiave surrogata. |
| managementStateName | Indica lo stato dell'azione remota applicata al dispositivo. |

### <a name="example"></a>Esempio

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

## <a name="managementagenttypes"></a>ManagementAgentTypes

L'entità **ManagementAgentTypes** rappresenta gli agenti usati per gestire un dispositivo.

| Proprietà  | Descrizione |
|---------|------------|
| ManagementAgentTypeID | Identificatore univoco del tipo di agente di gestione. |
| ManagementAgentTypeKey | Identificatore univoco del tipo di agente di gestione nel data warehouse, chiave surrogata. |
| ManagementAgentTypeName |Indica il tipo di agente che viene usato per gestire il dispositivo. |

### <a name="example"></a>Esempio

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
| OwnerTypeKey | Chiave dell'attributo tipo di proprietario per questo dispositivo: aziendale, personale o sconosciuto. |
| objectSourceKey | Ignorare questa colonna. |
| ManagementAgentKey | Chiave dell'agente di gestione associato al dispositivo. |
| ManagementStateKey | Chiave dello stato di gestione associato al dispositivo, che indica lo stato più recente di un'azione remota o se è jailbroken/rooted. |
| OSVersion | Versione sistema operativo |
| OSMajorVersion | Componente della versione principale del sistema operativo (major.minor.build.revision). |
| OSMinorVersion | Componente della versione secondaria del sistema operativo (major.minor.build.revision). |
| OSBuildNumber | Componente della versione build del sistema operativo (major.minor.build.revision). |
| OSRevisionNumber | Componente della versione di revisione del sistema operativo (major.minor.build.revision). |
| SerialNumber | Numero di serie del dispositivo, se disponibile. |
| RowLastModifiedDateTimeUTC | Data dell'ultima modifica apportata al record. |
| DeviceAction | Ultima azione del dispositivo eseguita. Ignorare per adesso. |
| Produttore | Produttore del dispositivo. |
| Modello | Modello del dispositivo. |
| IsDeleted | Impostato su True se il dispositivo non è più gestito da Intune. Conserva l'ultimo stato noto. |
| AndroidSecurityPatchLevel |Data della patch di sicurezza più recente del dispositivo. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

L'entità **DevicePropertyHistory** ha le stesse proprietà della tabella dei dispositivi e snapshot quotidiani del record di ciascun dispositivo per ognuno degli ultimi 90 giorni. La colonna DateKey indica il giorno per ogni riga.

| Proprietà  | Descrizione |
|---------|------------|
| DateKey |Riferimento alla tabella di data che indica il giorno. |
| DeviceKey |Identificatore univoco del dispositivo nel data warehouse - chiave surrogata. Si tratta di un riferimento alla tabella Device che contiene l'ID dispositivo Intune. |
| DeviceName |Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi. |
| OwnerTypeKey |Chiave dell'attributo tipo di proprietario per questo dispositivo: aziendale, personale o sconosciuto. |
| objectSourceKey |Ignorare questa colonna. |
| ManagementStateKey |Chiave dello stato di gestione associato al dispositivo, che indica lo stato più recente di un'azione remota o se è jailbroken/rooted. |
| OSVersion |Versione del sistema operativo. |
| OSMajorVersion |Componente della versione principale del sistema operativo (major.minor.build.revision). |
| OSMinorVersion |Componente della versione secondaria del sistema operativo (major.minor.build.revision). |
| OSBuildNumber |Componente della versione build del sistema operativo (major.minor.build.revision). |
| DeviceAction |Ultima azione del dispositivo eseguita. Ignorare per adesso. |

## <a name="applicationinventory"></a>ApplicationInventory

L'entità **ApplicationInventory** elenca le app trovate nel dispositivo al momento della raccolta inventario.


|      Proprietà      |                       Descrizione                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              Riferimento alla tabella devices.               |
|   ApplicationKey   | ? (copiato da ExchangeDeviceService\DeviceApplication). |
|  ApplicationName   | ? (copiato da ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion | ? (copiato da ExchangeDeviceService\DeviceApplication). |
|     BundleSize     | ? (copiato da ExchangeDeviceService\DeviceApplication). |

