---
title: Raccolte del data warehouse di Intune
titlesuffix: Microsoft Intune
description: Le raccolte del data warehouse di Intune forniscono dettagli relativi all'API Data Warehouse.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cdf7ea715a13809c860e77412914e3fd2b45a28
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400484"
---
#  <a name="intune-data-warehouse-collections"></a>Raccolte del data warehouse di Intune

Le raccolte del data warehouse di Intune seguenti forniscono le proprietà, le descrizioni ed esempi per le raccolte v1.0 delle entità dell'API Data Warehouse. 

## <a name="apprevisions"></a>appRevisions
L'entità **appRevision** elenca tutte le versioni di un'app.

|          Proprietà          |                                      Descrizione                                      |                Esempio               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | Identificatore univoco dell'app.                                                         | 123                                  |
| ApplicationId              | Identificatore univoco dell'app, simile ad AppKey, ma è una chiave naturale.        | b66bc706-ffff-7437-0340-032819502773 |
| Revisione                   | La versione indicata dall'amministratore durante il caricamento del file binario.                   | 2                                    |
| Titolo                      | Titolo dell'app.                                                                     | Excel                                |
| Pubblicazione                  | Autore della pubblicazione dell'app.                                                                 | Microsoft                            |
| UploadState                | Stato di caricamento dell'app.                                                              | 1                                    |
| AppTypeKey                 | Riferimento ad AppType descritto nella sezione seguente.                            | 1                                    |
| VppProgramTypeKey          | Riferimento a VppProgramType descritto di seguito.                                        | 30876                                |
| CreationTime               | Ora di creazione della revisione.                                            | 23/11/2016 0:00                      |
| ModifiedTime               | Ora dell'ultima modifica apportata a qualsiasi elemento relativo a questa revisione.                            | 23/11/2016 0:00                      |
| Dimensioni                       | Dimensioni del file binario in byte.                                                          | 120.392.000                          |
| StartDateInclusiveUTC      | Data e ora in formato UTC della creazione della revisione dell'app nel data warehouse.      | 23/11/2016 0:00                      |
| EndDateExclusiveUTC        | Data e ora in formato UTC in cui la revisione dell'app è diventata obsoleta.                        | 23/11/2016 0:00                      |
| IsCurrent                  | Indica se la versione dell'app è corrente o meno nel data warehouse.         | True/False                           |
| RowLastModifiedDateTimeUTC | Data e ora in formato UTC dell'ultima modifica della versione dell'app nel data warehouse. | 23/11/2016 0:00                      |

## <a name="apptypes"></a>appTypes
L'entità **appType** elenca l'origine dell'installazione di un'app.

|   Proprietà  |        Descrizione        |
|:-----------:|:-------------------------:|
| AppTypeID   | ID per il tipo           |
| AppTypeKey  | Chiave surrogata per la chiave |
| AppTypeName | Tipo di app                  |

### <a name="example"></a>Esempio

| AppTypeID |                Name               |                     Descrizione                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | App di Android Store               | Un'app di Android Store.                             |
| 1         | App LOB Android                 | Un'app line-of-business Android.                  |
| 2         | App di Android Store gestita (MAM) | Un'app di Android Store abilitata per la gestione. |
| 3         | App di iOS Store                   | Un'app di iOS Store.                                 |
| 4         | App LOB iOS                     | Un'app line-of-business iOS.                      |
| 5         | App dello Store iOS gestita (MAM?)     | Un'app iOSstore abilitata per la gestione.       |
| 6         | O365 Pro Plus Suite             | Office 365 Pro Plus Suite per Windows 10.     |
| 7         | App Web                         | Un'app Web.                                        |
| 8         | App di Windows Phone 8.1 Store     | Un'app dello Store per Windows Phone 8.1.                    |
| 9         | App di Windows Store               | Un'app di Windows Store.                              |
| 10        | App LOB di Windows                | Un'app line-of-business AppX per Windows.              |
| 11        | Windows Mobile MSI              | Un'app line-of-business MSI.                      |
| 12        | App LOB di Windows Phone           | Un'app line-of-business per Windows Phone.             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
La tabella seguente contiene un riepilogo dello stato di assegnazione dei criteri di conformità ai dispositivi. La tabella elenca il numero di dispositivi trovati in ogni stato di conformità.

|    Proprietà   |                                                                                      Descrizione                                                                                     |  Esempio |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | Chiave della data in cui è stato creato il riepilogo per i criteri di conformità.                                                                                                                   | 20161204 |
| Sconosciuto       | Numero di dispositivi che sono offline o che non sono riusciti a comunicare con Intune o Azure AD per altri motivi.                                                                           | 5        |
| NotApplicable | Numero di dispositivi in cui i criteri di conformità dei dispositivi assegnati dall'amministratore non sono applicabili.                                                                                     | 201      |
| Conforme     | Numero di dispositivi che hanno applicato correttamente uno o più criteri di conformità dei dispositivi assegnati dall'amministratore.                                                                        | 4083     |
| InGracePeriod | Numero di dispositivi che non sono conformi, ma che si trovano nel periodo di tolleranza definito dall'amministratore.                                                                                  | 57       |
| NonCompliant  | Numero di dispositivi che non sono riusciti ad applicare uno o più criteri di conformità assegnati dall'amministratore o in cui l'utente non ha soddisfatto la conformità ai criteri assegnati dall'amministratore. | 43       |
|    Errore      |    Numero di dispositivi che non sono riusciti a comunicare con Intune o Azure AD e che hanno restituito un messaggio di errore.                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
La tabella seguente contiene un riepilogo dello stato di assegnazione dei criteri di conformità ai dispositivi in base a ciascun criterio e al tipo di criterio. La tabella elenca il numero di dispositivi trovati in ogni stato di conformità per ogni criterio di conformità assegnato.

|      Proprietà     |                                                                                      Descrizione                                                                                     |  Esempio |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | Chiave della data in cui è stato creato il riepilogo per i criteri di conformità.                                                                                                                   | 20161219 |
| PolicyKey         | Chiave per il criterio di conformità per cui è stato creato il riepilogo.                                                                                                                   | 10178    |
| PolicyPlatformKey | Chiave per il tipo di piattaforma del criterio di conformità per cui è stato creato il riepilogo.                                                                                            | 5        |
| Sconosciuto           | Numero di dispositivi che sono offline o che non sono riusciti a comunicare con Intune o Azure AD per altri motivi.                                                                           | 13       |
| NotApplicable     | Numero di dispositivi in cui i criteri di conformità dei dispositivi assegnati dall'amministratore non sono applicabili.                                                                                     | 3        |
| Conforme         | Numero di dispositivi che hanno applicato correttamente uno o più criteri di conformità dei dispositivi assegnati dall'amministratore.                                                                        | 45       |
| InGracePeriod     | Numero di dispositivi che non sono conformi, ma che si trovano nel periodo di tolleranza definito dall'amministratore.                                                                                  | 3        |
| NonCompliant      | Numero di dispositivi che non sono riusciti ad applicare uno o più criteri di conformità assegnati dall'amministratore o in cui l'utente non ha soddisfatto la conformità ai criteri assegnati dall'amministratore. | 7        |
| Errore             | Numero di dispositivi che non sono riusciti a comunicare con Intune o Azure AD e che hanno restituito un messaggio di errore.                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      Proprietà      |                       Descrizione                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | Stato di conformità dei dispositivi con mdmStatusKey       |
| complianceStateKey | Chiave di conformità corrispondente allo stato del dispositivo e della conformità |
| complianceStateID  | ID corrispondente a questo stato di conformità                |

### <a name="example"></a>Esempio

|  complianceStatus  |                       Descrizione                      |
|:------------------:|:------------------------------------------------------:|
|    Sconosciuto         |    sconosciuta.                                                                        |
|    Conforme       |    Conforme.                                                                      |
|    Non conforme    |       Il dispositivo non è conforme e l'accesso alle risorse aziendali è bloccato.             |
|    Conflitto        |    Conflitto con altre regole.                                                      |
|    Errore           |       Errore.                                                                       |
|    ConfigManager   |    Gestito da Configuration Manager.                                                      |
|    InGracePeriod   |       Il dispositivo non è conforme ma può comunque accedere alle risorse aziendali          |

## <a name="dates"></a>dates
L'entità **dates** rappresenta le date a cui si fa riferimento tra più entità del data warehouse.

|     Proprietà    |                       Descrizione                      |    Esempio    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | Identificatore univoco della data nel data warehouse. | 20160703      |
| FullDate        | Data nel formato di Data/ora completo.        | 7/3/2016 0:00 |
| DayOfWeek       | Giorno della settimana                                            | 1             |
| DayOfMonth      | Giorno del mese                                           | 3             |
| DayOfYear       | Giorno dell'anno                                            | 185           |
| WeekOfYear      | Settimana dell'anno                                           | 28            |
| MonthOfYear     | Mese dell'anno                                      | 7             |
| CalendarQuarter | Trimestre di calendario                                       | 3             |
| CalendarYear    | Anno di calendario                                          | 2016          |
| DateKey         | Identificatore univoco della data nel data warehouse. | 20160703      |
| FullDate        | Data nel formato di Data/ora completo.        | 7/3/2016 0:00 |
| DayOfWeek       | Giorno della settimana                                            | 1             |
| DayOfMonth      | Giorno del mese                                           | 3             |
| DayOfYear       | Giorno dell'anno                                            | 185           |
| WeekOfYear      | Settimana dell'anno                                           | 28            |
| MonthOfYear     | Mese dell'anno                                      | 7             |
| CalendarQuarter | Trimestre di calendario                                       | 3             |
| CalendarYear    | Anno di calendario                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      Proprietà      |                                    Descrizione                                   |                Esempio               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | Identificatore univoco della categoria di dispositivi.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | Identificatore univoco della categoria di dispositivi nel data warehouse - chiave surrogata | 1                                    |
| deviceCategoryName | Nome visualizzato della categoria di dispositivi.                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
L'entità **DeviceConfigurationProfileDeviceActivity** elenca il numero di dispositivi nello stato completato, in sospeso, non riuscito o di errore al giorno. Il numero rispecchia i profili di configurazione dispositivo assegnati all'entità. Ad esempio, se un dispositivo è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un dispositivo sono assegnati due profili, uno nello stato completato e l'altro in uno stato di errore, l'entità incrementa il contatore di completamento e colloca il dispositivo in stato di errore. L'entità elenca quanti dispositivi sono in un determinato stato in un giorno specifico negli ultimi 30 giorni.

|  Proprietà |                                          Descrizione                                          |  Esempio |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | Chiave della data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. | 20160703 |
| Pending   | Numero di dispositivi univoci in sospeso.                                                    | 123      |
| Operazione completata | Numero di dispositivi univoci in stato completato.                                                    | 12       |
| Errore     | Numero di dispositivi univoci in stato di errore.                                                      | 10       |
| Operazione non riuscita    | Numero di dispositivi univoci in stato non riuscito.                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
L'entità **DeviceConfigurationProfileUserActivity** elenca il numero di utenti con stato completato, in sospeso, non riuscito o di errore per ogni giorno. Il numero rispecchia i profili di configurazione dispositivo assegnati all'entità. Ad esempio, se un utente è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un utente sono assegnati due profili, uno con stato completato e l'altro con stato di errore, viene considerato l'utente con lo stato di errore. L'entità **DeviceConfigurationProfileUserActivity** elenca il numero di utenti in ogni stato diverso in un giorno specifico degli ultimi 30 giorni. 

| Proprietà  | Descrizione  | Esempio  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse.  | 20160703  |
| Pending  | Numero di utenti univoci in sospeso.  | 123  |
| Operazione completata  | Numero di utenti univoci in stato completato.  | 12  |
| Errore  | Numero di utenti univoci in stato di errore.  | 10  |
| Operazione non riuscita  | Numero di utenti univoci in stato non riuscito.  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          Proprietà          |                                                                                      Descrizione                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Riferimento alla tabella di data che indica il giorno.                                                                                                                                          |
| DeviceKey                  | Identificatore univoco del dispositivo nel data warehouse - chiave surrogata. Si tratta di un riferimento alla tabella Device che contiene l'ID dispositivo Intune.                               |
| DeviceName                 | Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi. |
| DeviceRegistrationStateKey | Chiave dell'attributo stato di registrazione dispositivo per il dispositivo.                                                                                                                    |
| OwnerTypeKey               | Chiave dell'attributo tipo di proprietario per questo dispositivo: aziendale, personale o sconosciuto.                                                                                                  |
| ManagementStateKey         | Chiave dello stato di gestione associato al dispositivo, che indica lo stato più recente di un'azione remota o se è jailbroken/rooted.                                                |
| AzureADRegistered          | Indica se il dispositivo è registrato in Azure Active Directory.                                                                                                                             |
| ComplianceStateKey         | Una chiave per ComplianceState.                                                                                                                                                            |
| OSVersion                  | Versione del sistema operativo.                                                                                                                                                                          |
| JailBroken                 | Indica se il dispositivo è jailbroken o rooted.                                                                                                                                         |
| DeviceCategoryKey          | Chiave dell'attributo di categoria di dispositivo per questo dispositivo.                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
L'entità **DeviceRegistrationState** rappresenta il tipo di registrazione a cui fanno riferimento altre raccolte del data warehouse. 

|           Proprietà          |                                     Descrizione                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | Identificatore univoco per lo stato di registrazione                                            |
| deviceRegistrationStateKey  | Identificatore univoco dello stato di registrazione nel data warehouse - chiave surrogata |
| deviceRegistrationStateName | Stato di registrazione                                                                  |
|    NotRegistered                     |    Non registrato                                                                                                                                                                  |
|    Registrato                        |       Registrato                                                                                                                                                                   |
|    Revoked                           |       Lo stato indica che l'amministratore IT ha bloccato il client e che il client può essere sbloccato. Un dispositivo può anche essere nello stato Revocato dopo la cancellazione o il ritiro.        |
|    KeyConflict                       |    Conflitto di chiave                                                                                                                                                                    |
|    ApprovalPending                   |    Approvazione in sospeso                                                                                                                                                                |
|    CertificateReset                  |    Reimpostazione certificato                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    Non registrato con registrazione in sospeso                                                                                                                                               |
|    Sconosciuto                           |    Stato sconosciuto                                                                                                                                                                   |

## <a name="devices"></a>devices
L'entità **device** elenca tutti i dispositivi registrati in gestione e le proprietà corrispondenti.

|          Proprietà          |                                                                                       Descrizione                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Identificatore univoco del dispositivo nel data warehouse - chiave surrogata.                                                                                                               |
| DeviceId                   | Identificatore univoco del dispositivo.                                                                                                                                                     |
| DeviceName                 | Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Nelle altre piattaforme Intune crea un nome in base ad altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi. |
| DeviceTypeKey              | Chiave dell'attributo tipo di dispositivo per il dispositivo.                                                                                                                                    |
| DeviceRegistrationState    | Chiave dell'attributo stato di registrazione client per il dispositivo.                                                                                                                      |
| OwnerTypeKey               | Chiave dell'attributo tipo di proprietario per questo dispositivo: aziendale, personale o sconosciuto.                                                                                                    |
| EnrolledDateTime           | Data e ora in cui è stato registrato questo dispositivo.                                                                                                                                         |
| LastSyncDateTime           | Ultima archiviazione nota con Intune.                                                                                                                                              |
| ManagementAgentKey         | Chiave dell'agente di gestione associato al dispositivo.                                                                                                                             |
| ManagementStateKey         | Chiave dello stato di gestione associato al dispositivo, che indica lo stato più recente di un'azione remota o se è jailbroken/rooted.                                                |
| AzureADDeviceId            | L'ID dispositivo Azure per questo dispositivo.                                                                                                                                                  |
| AzureADRegistered          | Indica se il dispositivo è registrato in Azure Active Directory.                                                                                                                             |
| DeviceCategoryKey          | Chiave della categoria associata al dispositivo.                                                                                                                                     |
| DeviceEnrollmentType       | Chiave del tipo di registrazione associata al dispositivo, che indica il metodo di registrazione.                                                                                             |
| ComplianceStateKey         | Chiave dello stato di conformità associato a questo dispositivo.                                                                                                                             |
| OSVersion                  | Versione del sistema operativo del dispositivo.                                                                                                                                                |
| EasDeviceId                | ID Exchange ActiveSync del dispositivo.                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | Identificatore univoco per l'utente associato al dispositivo.                                                                                                                           |
| RowLastModifiedDateTimeUTC | Data e ora in formato UTC dell'ultima modifica del dispositivo nel data warehouse.                                                                                                       |
| Produttore               | Produttore del dispositivo                                                                                                                                                             |
| Modello                      | Modello del dispositivo                                                                                                                                                                    |
| OperatingSystem            | Sistema operativo del dispositivo. Windows, iOS e così via.                                                                                                                                   |
| IsDeleted                  | Dati binari per indicare se il dispositivo viene eliminato o meno.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Livello di patch di protezione per Android                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Stato del dispositivo con supervisione                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Spazio di archiviazione disponibile in byte.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Spazio di archiviazione totale in byte.                                                                                                                                                                |
| EncryptionState            | Stato della crittografia nel dispositivo.                                                                                                                                                      |
| SubscriberCarrier          | Gestore telefonico del sottoscrittore del dispositivo                                                                                                                                                       |
| PhoneNumber                | Numero di telefono del dispositivo                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Tecnologia cellulare del dispositivo                                                                                                                                                    |
| WiFiMacAddress             | MAC Wi-Fi                                                                                                                                                                              |


## <a name="devicetypes"></a>deviceTypes
L'entità **deviceType** rappresenta il tipo di dispositivo a cui fanno riferimento altre entità del data warehouse. Il tipo di dispositivo descrive in genere il modello o il produttore del dispositivo oppure una combinazione di entrambi.

|    Proprietà    |                                  Descrizione                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | Identificatore univoco del tipo di dispositivo                                       |
| DeviceTypeKey  | Identificatore univoco del tipo di dispositivo nel data warehouse - chiave surrogata |
| DeviceTypeName | Tipo di dispositivo                                                                |

### <a name="example"></a>Esempio

| deviceTypeID |        Name       |                      Descrizione                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | Non disponibile   | Il tipo di dispositivo non è disponibile.                     |
| 0            | Desktop           | Dispositivo Windows Desktop                              |
| 1            | Windows           | Dispositivo Windows                                      |
| 2            | WinMO6            | Dispositivo Windows Mobile 6.0                           |
| 3            | Nokia             | Dispositivo Nokia                                        |
| 4            | WindowsPhone      | Dispositivo Windows Phone                                |
| 5            | Mac               | Dispositivo Mac                                          |
| 6            | WinCE             | Dispositivo Windows CE                                   |
| 7            | WinEmbedded       | Dispositivo Windows Embedded                             |
| 8            | IPhone            | Dispositivo iPhone                                       |
| 9            | IPad              | Dispositivo iPad                                         |
| 10           | IPod              | Dispositivo iPod                                         |
| 11           | Android           | Dispositivo Android gestito con l'amministratore del dispositivo   |
| 12           | ISocConsumer      | Dispositivo consumer iSoc                                |
| 13           | Unix              | Dispositivo UNIX                                         |
| 14           | MacMDM            | Dispositivo Mac OS X gestito con l'agente MDM incorporato |
| 15           | HoloLens          | Dispositivo Holo Lens                                    |
| 16           | SurfaceHub        | Dispositivo Surface Hub                                  |
| 17           | AndroidForWork    | Dispositivo Android gestito con il profilo proprietario Android  |
| 18           | AndroidEnterprise | Dispositivo Android Enterprise.                          |
| 100          | Blackberry        | Dispositivo BlackBerry                                   |
| 101          | Palm              | Dispositivo palmare                                         |
| 255          | Sconosciuto           | Tipo di dispositivo sconosciuto                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
L'entità **deviceEnrollmentType** indica in che modo è stato registrato un dispositivo. Il tipo di registrazione acquisisce il metodo di registrazione. Gli esempi elencano i diversi tipi di registrazione e il relativo significato.

|         Proprietà         |                                    Descrizione                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | Identificatore univoco del tipo di registrazione.                                       |
| deviceEnrollmentTypeKey  | Identificatore univoco del tipo di registrazione nel data warehouse, chiave surrogata. |
| deviceEnrollmentTypeName | Nome del tipo di registrazione.                                                           |

### <a name="example"></a>Esempio

| enrollmentTypeID |                Name                |                                        Descrizione                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Sconosciuto                            | Il tipo di registrazione non è stato raccolto                                                      |
| 1                | UserEnrollment                     | Registrazione basata sull'utente tramite il canale BYOD.                                           |
| 2                | DeviceEnrollmentManager            | Registrazione dell'utente con un account del manager di registrazione dispositivi.                              |
| 3                | AppleBulkWithUser                  | Registrazione in blocco Apple con verifica utente. (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | Registrazione in blocco Apple senza verifica utente.   (DEP, Apple Configurator, Mobile Config) |
| 5                | WindowsAzureADJoin                 | Aggiunta ad Azure AD Windows 10.                                                                |
| 6                | WindowsBulkUserless                | Registrazione in blocco di Windows 10 tramite ICD con certificato.                               |
| 7                | WindowsAutoEnrollment              | Registrazione automatica di Windows 10.   (Aggiunta account aziendale)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Aggiunta ad Azure AD in blocco Windows 10.                                                           |
| 9                | WindowsCoManagement                | Co-gestione Windows 10 attivata da AutoPilot o Criteri di gruppo.                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | Aggiunta ad Azure AD Windows 10 con autenticazione del dispositivo.                                            |

## <a name="enrollmentactivities"></a>enrollmentActivities 
L'entità **EnrollmentActivity** indica l'attività di una registrazione del dispositivo.

| Proprietà                      | Descrizione                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Chiave della data in cui è stata registrata questa attività di registrazione.               |
| deviceEnrollmentTypeKey       | Chiave del tipo della registrazione.                                        |
| deviceTypeKey                 | Chiave del tipo di dispositivo.                                                |
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
| ClientDisconnected              | Il client ha raggiunto il timeout o la registrazione è stata interrotta dall'utente finale.                                                        |
| UserAbandonment                 | La registrazione è stata abbandonata dall'utente finale. L'utente finale ha avviato l'onboarding, ma non è riuscito a completarlo in modo tempestivo.  |

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
| UserAbandonment                  | La registrazione è stata abbandonata dall'utente finale. L'utente finale ha avviato l'onboarding, ma non è riuscito a completarlo in modo tempestivo.                                                                                           |
| APNSCertificateExpired           | Non è possibile gestire i dispositivi Apple con un certificato per le notifiche push MDM Apple scaduto.                                                                                                                            |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions
**intuneManagementExtension** elenca l'integrità di **intuneManagementExtension** su ogni dispositivo Windows 10 al giorno. I dati mantenuti sono quelli relativi agli ultimi 60 giorni.

|       Proprietà      |                          Descrizione                          | Esempio |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | Identificatore univoco della data.                                | 123     |
| TenantKey           | Identificatore univoco del tenant.                              | 456     |
| DeviceKey           | Identificatore univoco del dispositivo.                              | 789     |
| ExtensionVersionKey | Identificatore univoco della versione di IntuneManagementExtension. | 1       |
| ExtensionStateKey   | Identificatore univoco dello stato di integrità.                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
**IntuneManagementExtensionHealthState** elenca tutti i possibili stati di integrità di **IntuneManagementExtension**.

|      Proprietà     |                   Descrizione                  | Esempio |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | Identificatore univoco dello stato di integrità.           | 2       |
| ExtensionState    | Stato di integrità di IntuneManagementExtension. | Healthy |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
L'entità **IntuneManagementExtensionVersion** elenca tutte le versioni usate da **IntuneManagementExtension**.

|       Proprietà      |                          Descrizione                          | Esempio |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | Identificatore univoco della versione di IntuneManagementExtension. | 1       |
| ExtensionVersion    | Numero della versione a 4 cifre.                                   | 1.0.2.0 |

## <a name="managementagenttypes"></a>managementAgentTypes
L'entità **managementAgentType** rappresenta gli agenti usati per gestire un dispositivo.

|         Proprietà        |                                       Descrizione                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | Identificatore univoco del tipo di agente di gestione.                                         |
| ManagementAgentTypeKey  | Identificatore univoco del tipo di agente di gestione nel data warehouse - chiave surrogata. |
| ManagementAgentTypeName | Indica il tipo di agente che viene usato per gestire il dispositivo.                              |

### <a name="example"></a>Esempio

| ManagementAgentTypeID |                Name               |                                  Descrizione                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | Il dispositivo è gestito tramite Exchange Active Sync                         |
| 2                     | MDM                               | Il dispositivo è gestito tramite un agente MDM                                   |
| 3                     | EasMdm                            | Il dispositivo è gestito da Exchange Active Sync e un agente MDM        |
| 4                     | IntuneClient                      | Il dispositivo è gestito dall'agente PC di Intune                               |
| 5                     | EasIntuneClient                   | Il dispositivo è gestito da Exchange Active Sync e l'agente PC di Intune |
| 8                     | ConfigManagerClient               | Il dispositivo è gestito dall'agente System Center Configuration Manager     |
| 10                    | ConfigurationManagerClientMdm     | Il dispositivo è gestito da Configuration Manager e MDM.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | Il dispositivo è gestito da Configuration Manager, MDM ed Exchange Active Sync.               |
| 16                    | Sconosciuto                           | Tipo di agente di gestione sconosciuto                                              |
| 32                    | Jamf                              | Gli attributi del dispositivo vengono recuperati da Jamf.                               |
| 64                    | GoogleCloudDevicePolicyController |  Il dispositivo è gestito da CloudDPC di Google.                                 |

## <a name="managementstates"></a>managementStates
L'entità **ManagementState** fornisce informazioni dettagliate sullo stato del dispositivo. I dettagli possono rivelarsi utili nei casi in cui vengono applicate azioni remote, il dispositivo è jailbroken o rooted.

|       Proprietà      |                                     Descrizione                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | Identificatore univoco dello stato di gestione.                                       |
| managementStateKey  | Identificatore univoco dello stato di gestione nel data warehouse - chiave surrogata. |
| managementStateName | Indica lo stato dell'azione remota applicata al dispositivo.                 |

### <a name="example"></a>Esempio

| managementStateID |      Name      |                                                   Descrizione                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | Gestiti        | Gestito senza azioni remote in sospeso.                                                                       |
| 1                 | RetirePending  | C'è un comando di ritiro in sospeso per il dispositivo.                                                             |
| 2                 | RetireFailed   | Il comando di ritiro del dispositivo non è riuscito.                                                                      |
| 3                 | WipePending    | C'è un comando di cancellazione in sospeso per il dispositivo.                                                               |
| 4                 | WipeFailed     | Il comando di cancellazione del dispositivo non è riuscito.                                                                        |
| 5                 | Unhealthy      | Stato non integro.                                                                                              |
| 6                 | DeletePending  | C'è un comando di eliminazione in sospeso per il dispositivo.                                                             |
| 7                 | RetireIssued   | Al dispositivo è stato inviato un comando di ritiro.                                                               |
| 8                 | WipeIssued     | Al dispositivo è stato inviato un comando di cancellazione.                                                                               |
| 9                 | WipeCanceled   | Il comando di cancellazione è stato annullato.                                                                               |
| 10                | RetireCanceled | Il comando di ritiro è stato annullato.                                                                             |
| 11                | Discovered     | Il dispositivo è stato individuato recentemente da Intune; quando viene archiviato per la prima volta passa allo stato Gestito. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
L'entità MobileAppInstallState rappresenta lo stato di installazione per un'applicazione per dispositivi mobili dopo l'assegnazione a un gruppo che contiene dispositivi, utenti o entrambi.

|       Proprietà      |                        Descrizione                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | ID univoco dello stato di installazione dell'app per l'account. |
| AppInstallState     | Valore di enumerazione dello stato di installazione dell'app.                     |
| AppInstallStateName | Nome dello stato di installazione dell'app.                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
Rappresenta uno stato di installazione di app per dispositivi mobili per un tipo di dispositivo di destinazione specificato mediante la gestione di applicazioni per dispositivi mobili tramite Microsoft Intune.

|      Proprietà      |                                                          Descrizione                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | Chiave della data di registrazione dello stato di installazione dell'app.                                                                     |
| AppKey             | Chiave dell'app per dispositivi mobili usata per identificare un'istanza di AppRevision.                                                          |
| DeviceTypeKey      | Chiave del tipo di dispositivo associata all'applicazione per dispositivi mobili.                                                              |
| AppInstallStateKey | Chiave dello stato di installazione dell'app usata per identificare un'istanza di MobileAppInstallState.                                         |
| ErrorCode          | Codice di errore restituito dal programma di installazione dell'app, dalla piattaforma per dispositivi mobili o dal servizio in merito all'installazione dell'app. |
| Conteggio              | Numero totale.                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
L'entità **ownerType** indica se un dispositivo è aziendale, personale o sconosciuto.

|    Proprietà   |                                                                                     Descrizione                                                                                    |           Esempio          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | Identificatore univoco del tipo di proprietario.                                                                                                                                               |                            |
| ownerTypeKey  | Identificatore univoco del tipo di proprietario nel data warehouse - chiave surrogata.                                                                                                       |                            |
| ownerTypeName | Rappresenta il tipo di proprietario dei dispositivi: Corporate - il dispositivo è di proprietà aziendale.  Personal - il dispositivo è di proprietà personale (BYOD).   Unknown - nessuna informazione su questo dispositivo. | Unknown personale aziendale |

> [!Note]  
> Per il `ownerTypeName` filtro in Azure ad durante la creazione di gruppi dinamici per i dispositivi, è necessario impostare il valore `deviceOwnership` come `Company`. Per altre informazioni, vedere [regole per i dispositivi](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="policies"></a>criteri
l'entità **Policy** elenca profili di configurazione del dispositivo, profili di configurazione dell'app e criteri di conformità. È possibile assegnare i criteri con Gestione dispositivi mobili (MDM) a un gruppo nell'organizzazione.

|          Proprietà          |                                                                       Descrizione                                                                      |                Esempio               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | Chiave univoca per rappresentare i criteri nel data warehouse.                                                                                              | 123                                  |
| PolicyId                   | Identificatore univoco del criterio nel data warehouse.                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | Nome del criterio.                                                                                                                                    | "Windows 10 Baseline"                |
| PolicyVersion              | Versione del criterio. Quando il criterio viene modificato o cambiato, viene creata una versione più recente.                                                             | 1, 2, 3                              |
| IsDeleted                  | Indica se il record del criterio è stato aggiornato.  True: il criterio ha un nuovo record con campi aggiornati.  False: è l'ultimo record per il criterio. | True/False                           |
| StartDateInclusiveUTC      | Data e ora in formato UTC della creazione del criterio nel data warehouse.                                                                              | 23/11/2016 0:00                      |
| DeletedDateUTC             | Data e ora in formato UTC in cui IsDeleted è stato impostato su True.                                                                                                   | 23/11/2016 0:00                      |
| RowLastModifiedDateTimeUTC | Data e ora in formato UTC dell'ultima modifica del criterio nel data warehouse.                                                                        | 23/11/2016 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
La tabella seguente elenca il numero di dispositivi con stato completato, in sospeso, non riuscito o di errore ogni giorno. Il numero riflette i dati per ogni profilo del tipo di criteri. Ad esempio, se un dispositivo è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un dispositivo sono assegnati due profili, uno nello stato completato e l'altro in uno stato di errore, l'entità incrementa il contatore di completamento e colloca il dispositivo in stato di errore. L'entità **policyDeviceActivity** elenca il numero di dispositivi che sono in un determinato stato in un giorno specifico negli ultimi 30 giorni.

|  Proprietà |                                           Descrizione                                           |        Esempio        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | Chiave della data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. | 20160703              |
| Pending   | Numero di dispositivi univoci in stato sospeso.                                                    | 123                   |
| Operazione completata | Numero di dispositivi univoci in stato completato.                                                    | 12                    |
| PolicyKey | Chiave dei criteri, può essere unita a Policy per ottenere policyName.                                  | Baseline Windows 10 |
| Errore     | Numero di dispositivi univoci in stato di errore.                                                      | 10                    |
| Operazione non riuscita    | Numero di dispositivi univoci in stato non riuscito.                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        Proprietà        |                      Descrizione                      |     Esempio    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | Chiave univoca per il tipo di piattaforma dei criteri.        | 20170519       |
| PolicyPlatformTypeId   | Identificatore univoco per il tipo di piattaforma dei criteri. | 1              |
| PolicyPlatformTypeName | Nome del tipo di piattaforma dei criteri.              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
L'entità **PolicyTypeActivity** elenca il numero cumulativo di dispositivi nello stato completato, in sospeso, non riuscito o di errore. Vengono elencati questi stati rispetto a un profilo di configurazione del dispositivo, un profilo di configurazione dell'app o ai criteri di conformità per ogni giorno.

|    Proprietà   |                                          Descrizione                                          |           Esempio           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | Chiave della data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. | 20160703                    |
| PolicyKey     | Chiave dei criteri, può essere unita a Policy per ottenere policyName.                                | Windows 10 baseline         |
| PolicyTypeKey | Tipo di chiave dei criteri, può essere unita al tipo di criterio per ottenere il nome del tipo di criterio.             | Criteri di conformità di Windows 10 |
| Pending       | Numero di dispositivi univoci in sospeso.                                                    | 123                         |
| Operazione completata     | Numero di dispositivi univoci in stato completato.                                                    | 12                          |
| Errore         | Numero di dispositivi univoci in stato di errore.                                                      | 10                          |
| Operazione non riuscita        | Numero di dispositivi univoci in stato non riuscito.                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
L'entità **PolicyType** elenca i tipi di profilo di configurazione del dispositivo, profili di configurazione dell'app e criteri di conformità. È possibile assegnare i criteri con Gestione dispositivi mobili (MDM) a un gruppo nell'organizzazione.

|    Proprietà    |                       Descrizione                      |            Esempio            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | Identificatore univoco del criterio nel sistema di origine.  | 123                           |
| PolicyTypeKey  | Identificatore univoco del criterio nel data warehouse. | 1                             |
| PolicyTypeName | Nome del tipo di criterio.                               | Criteri di conformità di Windows 10. |

## <a name="policyuseractivities"></a>policyUserActivities
La tabella seguente elenca il numero di utenti con stato completato, in sospeso, non riuscito o di errore ogni giorno. Il numero riflette i dati per ogni profilo del tipo di criteri. Ad esempio, se un utente è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un utente sono assegnati due profili, uno con stato completato e l'altro con stato di errore, viene considerato l'utente con lo stato di errore. L'entità **PolicyUserActivity** elenca il numero di utenti in ogni stato in un giorno specifico negli ultimi 30 giorni.

|  Proprietà |                                          Descrizione                                          |       Esempio       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | Chiave della data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. | 20160703            |
| Pending   | Numero di dispositivi univoci in sospeso.                                                    | 123                 |
| Operazione completata | Numero di dispositivi univoci in stato completato.                                                    | 12                  |
| PolicyKey | Chiave dei criteri, può essere unita a Policy per ottenere policyName.                                | Windows 10 baseline |
| Errore     | Numero di dispositivi univoci in stato di errore.                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
L'entità **termsAndConditions** rappresenta i metadati e il contenuto di un criterio Termini e condizioni specificato. Il contenuto dei criteri Termini e condizioni viene presentato agli utenti in occasione del primo tentativo di registrazione in Intune e successivamente in caso di modifiche per le quali un amministratore richiede di accettarli nuovamente. Consentono agli amministratori di comunicare le condizioni che un utente deve accettare per poter registrare il dispositivo in Intune.

|    Proprietà        |    Descrizione    |    Esempio        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    Chiave corrispondente a una voce nella raccolta 'userTermsAndConditionsAcceptances'    |    123    |
|    termsAndCondidionsId    |    ID per questa voce termsAndConditions    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    Versione di questa voce di termini e condizioni    |    1    |
|    name    |    Nome di questa voce termsAndConditions.        |    Condizioni per l'utilizzo di Intune     |
|    description    |    Descrizione di questi termini e condizioni.     |         |
|    title    |    Titolo per questi termini e condizioni.     |    Criteri aziendali di gestione di dispositivi        |
|    summaryOfTerms    |    Riepilogo delle condizioni fornite all'utente.     |    Accetto i termini e le condizioni.    |
|    termsAndConditionsBodyText    |    Il corpo del testo per questi termini e condizioni.       |    *Crittografia del dispositivo* Imposizione del PIN di 6 cifre    |
|    isDeleted    |    Valore true o false per indicare se questo valore viene eliminato.     |    False    |
|    startDateInclusiveUTC    |    Data di inizio di questi termini e condizioni.     |    23/08/2018 4:01:34    |
|    endDateEclusiveUTC    |    Data di fine di questi termini e condizioni.     |    31/12/9999 12:00:00    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
L'entità **UserDeviceAssociation** contiene le associazioni utente-dispositivo presenti nell'organizzazione.

|        Name        |                                             Descrizione                                            |     Esempio     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | Identificatore univoco dell'utente nel data warehouse   (chiave sostitutiva).                            | 123             |
| DeviceKey          | Identificatore univoco del dispositivo nel data warehouse.                                             | 123             |
| CreatedDateTimeUTC | Data e ora della creazione dell'associazione utente-dispositivo. Viene usato il formato UTC.                     | 23/11/2016 0:00 |
| IsDeleted          | Indica che l'utente ha annullato la registrazione del dispositivo e che l'associazione non è più aggiornata. | True/False      |
| EndedDateTimeUTC   | Data e ora in formato UTC in cui IsDeleted è stato impostato su True.                                               | 23/06/2017 0:00  |

## <a name="users"></a>utenti
L'entità **user** elenca tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione.

La raccolta di entità **user** contiene i dati utente. In questi record sono inclusi gli stati utente registrati nel periodo di raccolta dei dati, anche se l'utente è stato rimosso. Nel corso dell'ultimo mese, ad esempio, è possibile che un utente sia stato aggiunto e rimosso da Intune. Se anche l'utente non è presente al momento del report, l'utente e lo stato sono comunque presenti nei dati del mese precedente. In questo caso, è possibile creare un report che mostri la durata della presenza storica dell'utente nei dati.

|          Proprietà          |                                                                                                           Descrizione                                                                                                          |                Esempio               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Identificatore univoco dell'utente nel data warehouse - chiave surrogata.                                                                                                                                                         | 123                                  |
| UserId                     | Identificatore univoco dell'utente, simile a UserKey, ma è una chiave naturale.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | Indirizzo di posta elettronica dell'utente.                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | UPN dell'utente.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Nome visualizzato dell'utente.                                                                                                                                                                                                      | Luca                                 |
| IntuneLicensed             | Specifica se l'utente ha una licenza per Intune.                                                                                                                                                                              | True/False                           |
| IsDeleted                  | Indica se tutte le licenze dell'utente sono scadute e se l'utente è stato pertanto rimosso da Intune. Per un singolo record, questo flag non cambia. Per un nuovo stato utente viene creato invece un nuovo record. | True/False                           |
| RowLastModifiedDateTimeUTC | Data e ora in formato UTC dell'ultima modifica del record nel data warehouse                                                                                                                                                 | 23/11/2016 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
Un'entità **userTermsAndConditionsAcceptance** rappresenta lo stato di accettazione di un determinato criterio Termini e condizioni da parte di un utente specificato. Gli utenti devono accettare la versione più aggiornata delle condizioni per mantenere l'accesso al portale aziendale.

|    Proprietà    |    Descrizione    |    Esempio    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    Chiave corrispondente a un valore di data nella raccolta 'dates'.     |    20180823    |
|    userKey    |    Mapping della chiave utente a un utente nella raccolta 'users'.     |    20000    |
|    termsAndConditionsKey    |    Chiave corrispondente a una voce nella raccolta 'termsAndConditions'    |    1    |
|    acceptedDateTimeUTC    |    Ora in cui l'utente ha accettato questi termini e condizioni    |    23/08/2018 4:01:34    |
|    lastModifiedDateTimeUTC    |    Data/ora dell'ultima modifica di questa voce.     |    23/08/2018 4:01:34    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
L'entità **vppProgramType** elenca i tipi di programma VPP possibili per un'app.

|      Proprietà      |          Descrizione         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | ID per il tipo.           |
| VppProgramTypeKey  | Chiave surrogata per la chiave. |
| VppProgramTypeName | Tipo di programma VPP.          |

### <a name="example"></a>Esempio

|             VppProgramID             |         Name        | Descrizione                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Programma VPP Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Non ancora disponibile | Valore predefinito, nessun VPP.   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Programma VPP Apple.     |

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sul data warehouse di Intune, vedere [Modello di dati del data warehouse](https://docs.microsoft.com/intune/reports-ref-data-model).

