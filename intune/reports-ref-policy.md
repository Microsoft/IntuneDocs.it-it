---
title: Informazioni di riferimento per le entità della categoria Policy
titlesuffix: Microsoft Intune
description: Argomento di riferimento per la categoria Policy delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 9fb05991b3e289d4a24cc2f3a5b2c398c12b1a15
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032436"
---
# <a name="reference-for-policy-entities"></a>Informazioni di riferimento per le entità della categoria Policy

La categoria **Policy** contiene le entità per i dispositivi mobili che tengono traccia delle informazioni come:

  -  Inventario dei profili di configurazione del dispositivo, profili di configurazione dell'app e criteri di conformità  
  -  Numero di dispositivi nello stato completato, in sospeso, non riuscito o di errore al giorno  
  -  Numero di utenti nello stato completato, in sospeso, non riuscito o di errore al giorno  
  -  Numero cumulativo di dispositivi nello stato completato, in sospeso, non riuscito o di errore  

## <a name="policy"></a>Criteri

l'entità **Policy** elenca profili di configurazione del dispositivo, profili di configurazione dell'app e criteri di conformità. È possibile assegnare i criteri con Gestione dispositivi mobili (MDM) a un gruppo nell'organizzazione.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| PolicyKey |Chiave univoca per rappresentare i criteri nel data warehouse. |123 |
| PolicyId |Identificatore univoco del criterio nel data warehouse. |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Nome del criterio. |"Windows 10 Baseline" |
| PolicyVersion |Versione del criterio. Quando il criterio viene modificato o cambiato, viene creata una versione più recente. |1, 2, 3 |
| IsDeleted |Indica se il record Policy è stato aggiornato.  <br>True: il criterio ha un nuovo record con i campi aggiornati. <br>False: l'ultimo record per il criterio. |True/False |
| StartDateInclusiveUTC |Data e ora in formato UTC della creazione del criterio nel data warehouse. |23/11/2016 12.00.00 |
| DeletedDateUTC |Data e ora in formato UTC in cui IsDeleted è stato impostato su True. |23/11/2016 12.00.00 |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica del criterio nel data warehouse. |23/11/2016 12.00.00 |

## <a name="policytype"></a>PolicyType

L'entità **PolicyType** elenca i tipi di profilo di configurazione del dispositivo, profili di configurazione dell'app e criteri di conformità. È possibile assegnare i criteri con Gestione dispositivi mobili (MDM) a un gruppo nell'organizzazione.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| PolicyTypeId |Identificatore univoco del criterio nel sistema di origine. |123 |
| PolicyTypeKey |Identificatore univoco del criterio nel data warehouse. |1 |
| PolicyTypeName |Nome del tipo di criterio. |Criteri di conformità di Windows 10. |

## <a name="deviceconfiguration"></a>DeviceConfiguration

L'entità **DeviceConfigurationProfileDeviceActivity** elenca il numero di dispositivi nello stato completato, in sospeso, non riuscito o di errore al giorno. Il numero rispecchia i profili di configurazione dispositivo assegnati all'entità. Ad esempio, se un dispositivo è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un dispositivo sono assegnati due profili, uno nello stato completato e l'altro in uno stato di errore, l'entità incrementa il contatore di completamento e colloca il dispositivo in stato di errore. L'entità elenca quanti dispositivi sono in un determinato stato in un giorno specifico negli ultimi 30 giorni.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| DateKey |Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |20160703 |
| Pending |Numero di dispositivi univoci in sospeso. |123 |
| Operazione completata |Numero di dispositivi univoci in stato completato. |12 |
| Errore |Numero di dispositivi univoci in stato di errore. |10 |
| Operazione non riuscita |Numero di dispositivi univoci in stato non riuscito. |2 |



L'entità **DeviceConfigurationProfileUserActivity** elenca il numero di utenti con stato completato, in sospeso, non riuscito o di errore per ogni giorno. Il numero rispecchia i profili di configurazione dispositivo assegnati all'entità. Ad esempio, se un utente è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un utente sono assegnati due profili, uno con stato completato e l'altro con stato di errore, viene considerato l'utente con lo stato di errore.  L'entità **DeviceConfigurationProfileUserActivity** elenca il numero di utenti in ogni stato diverso in un giorno specifico degli ultimi 30 giorni.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| DateKey |Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |20160703 |
| Pending |Numero di utenti univoci in sospeso. |123 |
| Operazione completata |Numero di utenti univoci in stato completato. |12 |
| Errore |Numero di utenti univoci in stato di errore. |10 |
| Operazione non riuscita |Numero di utenti univoci in stato non riuscito. |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

L'entità **PolicyTypeActivity** elenca il numero cumulativo di dispositivi nello stato completato, in sospeso, non riuscito o di errore. Vengono elencati questi stati rispetto a un profilo di configurazione del dispositivo, un profilo di configurazione dell'app o ai criteri di conformità per ogni giorno.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| DateKey |Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |20160703 |
| PolicyKey |Chiave dei criteri, può essere unita con i criteri per ottenere policyName. |Windows 10 baseline |
| PolicyTypeKey |Tipo di chiave dei criteri, può essere unita con il tipo di criterio per ottenere il nome del tipo di criterio. |Criteri di conformità di Windows 10 |
| Pending |Numero di dispositivi univoci in sospeso. |123 |
| Operazione completata |Numero di dispositivi univoci in stato completato. |12 |
| Errore |Numero di dispositivi univoci in stato di errore. |10 |
| Operazione non riuscita |Numero di dispositivi univoci in stato non riuscito. |2 |

## <a name="compliance-policy"></a>Criteri di conformità

Le informazioni di riferimento sull'API dei criteri di conformità contengono le entità che forniscono informazioni sullo stato per i criteri di conformità assegnati ai dispositivi.

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

La tabella seguente contiene un riepilogo dello stato di assegnazione dei criteri di conformità ai dispositivi. La tabella elenca il numero di dispositivi trovati in ogni stato di conformità.


|Proprietà     |Descrizione  |Esempio  |
|---------|---------|---------|
|DateKey  |Chiave della data in cui è stato creato il riepilogo per i criteri di conformità.|20161204 |
|Sconosciuto  |Numero di dispositivi che sono offline o che non sono riusciti a comunicare con Intune o Azure AD per altri motivi. |5|
|NotApplicable      |Numero di dispositivi in cui i criteri di conformità dei dispositivi assegnati dall'amministratore non sono applicabili.|201 |
|Conforme      |Numero di dispositivi che hanno applicato correttamente uno o più criteri di conformità dei dispositivi assegnati dall'amministratore. |4083 |
|InGracePeriod      |Numero di dispositivi che non sono conformi, ma che si trovano nel periodo di tolleranza definito dall'amministratore. |57|
|NonCompliant      |Numero di dispositivi che non sono riusciti ad applicare uno o più criteri di conformità assegnati dall'amministratore o in cui l'utente non ha soddisfatto la conformità ai criteri assegnati dall'amministratore.|43 |
|Errore      |Numero di dispositivi che non sono riusciti a comunicare con Intune o Azure AD e che hanno restituito un messaggio di errore. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

La tabella seguente contiene un riepilogo dello stato di assegnazione dei criteri di conformità ai dispositivi in base a ciascun criterio e al tipo di criterio. La tabella elenca il numero di dispositivi trovati in ogni stato di conformità per ogni criterio di conformità assegnato.



|Proprietà  |Descrizione  |Esempio  |
|---------|---------|---------|
|DateKey  |Chiave della data in cui è stato creato il riepilogo per i criteri di conformità.|20161219|
|PolicyKey     |Chiave per il criterio di conformità per cui è stato creato il riepilogo. |10178 |
|PolicyPlatformKey      |Chiave per il tipo di piattaforma del criterio di conformità per cui è stato creato il riepilogo.|5|
|Sconosciuto     |Numero di dispositivi che sono offline o che non sono riusciti a comunicare con Intune o Azure AD per altri motivi.|13|
|NotApplicable     |Numero di dispositivi in cui i criteri di conformità dei dispositivi assegnati dall'amministratore non sono applicabili.|3|
|Conforme      |Numero di dispositivi che hanno applicato correttamente uno o più criteri di conformità dei dispositivi assegnati dall'amministratore. |45|
|InGracePeriod      |Numero di dispositivi che non sono conformi, ma che si trovano nel periodo di tolleranza definito dall'amministratore. |3|
|NonCompliant      |Numero di dispositivi che non sono riusciti ad applicare uno o più criteri di conformità assegnati dall'amministratore o in cui l'utente non ha soddisfatto la conformità ai criteri assegnati dall'amministratore.|7|
|Errore      |Numero di dispositivi che non sono riusciti a comunicare con Intune o Azure AD e che hanno restituito un messaggio di errore. |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

La tabella seguente contiene i tipi di piattaforma di tutti i criteri assegnati. I tipi di piattaforma dei criteri che non sono mai stati assegnati ad alcun dispositivo non sono inclusi nella tabella.


|Proprietà  |Descrizione  |Esempio  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |Chiave univoca per il tipo di piattaforma dei criteri. |20170519 |
|PolicyPlatformTypeId      |Identificatore univoco per il tipo di piattaforma dei criteri.|1|
|PolicyPlatformTypeName      |Nome del tipo di piattaforma dei criteri.|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

La tabella seguente elenca il numero di dispositivi con stato completato, in sospeso, non riuscito o di errore ogni giorno. Il numero riflette i dati per ogni profilo del tipo di criteri. Ad esempio, se un dispositivo è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un dispositivo sono assegnati due profili, uno nello stato completato e l'altro in uno stato di errore, l'entità incrementa il contatore di completamento e colloca il dispositivo in stato di errore. L'entità PolicyDeviceActivity elenca il numero di dispositivi che sono in un determinato stato in un giorno specifico negli ultimi 30 giorni.

|Proprietà  |Descrizione  |Esempio  |
|---------|---------|---------|
|DateKey|Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse.|20160703|
|Pending|Numero di dispositivi univoci in sospeso.|123|
|Operazione completata|Numero di dispositivi univoci in stato completato.|12|
PolicyKey|Chiave dei criteri, può essere unita con i criteri per ottenere policyName.|Windows 10 baseline|
|Errore|Numero di dispositivi univoci in stato di errore.|10|
|Operazione non riuscita|Numero di dispositivi univoci in stato non riuscito.|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

La tabella seguente elenca il numero di utenti con stato completato, in sospeso, non riuscito o di errore ogni giorno. Il numero riflette i dati per ogni profilo del tipo di criteri. Ad esempio, se un utente è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un utente sono assegnati due profili, uno con stato completato e l'altro con stato di errore, viene considerato l'utente con lo stato di errore. L'entità PolicyUserActivity elenca il numero di utenti in ogni stato in un giorno specifico negli ultimi 30 giorni.


| Proprietà  |                                         Descrizione                                         |       Esempio       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |      20160703       |
|  Pending  |                         Numero di dispositivi univoci in sospeso.                          |         123         |
| Operazione completata |                         Numero di dispositivi univoci in stato completato.                          |         12          |
| PolicyKey |                Chiave dei criteri, può essere unita con i criteri per ottenere policyName.                 | Windows 10 baseline |
|   Errore   |                          Numero di dispositivi univoci in stato di errore.                           |         10          |

