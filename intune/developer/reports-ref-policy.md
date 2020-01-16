---
title: Informazioni di riferimento per le entità della categoria Policy
titleSuffix: Microsoft Intune
description: Argomento di riferimento per la categoria Policy delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fe4fabc86e7be647fa161d68fe8a4fe35e9eb6b
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654125"
---
# <a name="reference-for-policy-entities"></a>Informazioni di riferimento per le entità della categoria Policy

La categoria **policies** contiene le entità per i dispositivi mobili che tengono traccia delle informazioni come:

- Inventario dei profili di configurazione del dispositivo, profili di configurazione dell'app e criteri di conformità  
- Numero di dispositivi nello stato completato, in sospeso, non riuscito o di errore al giorno  
- Numero di utenti nello stato completato, in sospeso, non riuscito o di errore al giorno  
- Numero cumulativo di dispositivi nello stato completato, in sospeso, non riuscito o di errore  

## <a name="policies"></a>criteri

L'entità **policy** elenca profili di configurazione del dispositivo, profili di configurazione delle app e criteri di conformità. È possibile assegnare i criteri con Gestione dispositivi mobili (MDM) a un gruppo nell'organizzazione.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| policyKey |Chiave univoca per rappresentare i criteri nel data warehouse. |123 |
| policyId |Identificatore univoco del criterio nel data warehouse. |b66bc706-ffff-7437-0340-032819502773 |
| policyName |Nome del criterio. |"Windows 10 Baseline" |
| policyVersion |Versione del criterio. Quando il criterio viene modificato o cambiato, viene creata una versione più recente. |1, 2, 3 |
| isDeleted |Indica se il record Policy è stato aggiornato.  <br>True: il criterio ha un nuovo record con i campi aggiornati. <br>False: l'ultimo record per il criterio. |True/False |
| startDateInclusiveUTC |Data e ora in formato UTC della creazione del criterio nel data warehouse. |23/11/2016 12.00.00 |
| deletedDateUTC |Data e ora in formato UTC in cui IsDeleted è stato impostato su True. |23/11/2016 12.00.00 |
| rowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica del criterio nel data warehouse. |23/11/2016 12.00.00 |

## <a name="policytypes"></a>policyTypes

L'entità **policyType** elenca i tipi di profilo di configurazione del dispositivo, i profili di configurazione delle app e i criteri di conformità. È possibile assegnare i criteri con Gestione dispositivi mobili (MDM) a un gruppo nell'organizzazione.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| policyTypeId |Identificatore univoco del criterio nel sistema di origine. |123 |
| policyTypeKey |Identificatore univoco del criterio nel data warehouse. |1 |
| policyTypeName |Nome del tipo di criterio. |Criteri di conformità di Windows 10. |

## <a name="device-configuration"></a>Configurazione dei dispositivi

L'entità **deviceConfigurationProfileDeviceActivity** elenca il numero di **dispositivi** nello stato completato, in sospeso, non riuscito o di errore al giorno. Il numero rispecchia i profili di configurazione dispositivo assegnati all'entità. Se ad esempio un **dispositivo** è nello stato completato per tutti i criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un dispositivo sono assegnati due profili, uno nello stato completato e l'altro in uno stato di errore, l'entità incrementa il contatore di completamento e colloca il dispositivo in stato di errore. L'entità elenca quanti dispositivi sono in un determinato stato in un giorno specifico negli ultimi 30 giorni.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| dateKey |Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |20160703 |
| in sospeso |Numero di dispositivi univoci in sospeso. |123 |
| riuscito |Numero di dispositivi univoci in stato completato. |12 |
| error |Numero di dispositivi univoci in stato di errore. |10 |
| non riuscito |Numero di dispositivi univoci in stato non riuscito. |2 |

L'entità **deviceConfigurationProfileUserActivity** elenca il numero di **utenti** con stato completato, in sospeso, non riuscito o di errore per ogni giorno. Il numero rispecchia i profili di configurazione dispositivo assegnati all'entità. Se ad esempio un **utente** è nello stato completato per tutti i criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un utente sono assegnati due profili, uno con stato completato e l'altro con stato di errore, viene considerato l'utente con lo stato di errore.  L'entità **deviceConfigurationProfileUserActivity** elenca il numero di utenti in ogni stato diverso in un giorno specifico degli ultimi 30 giorni.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| dateKey |Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |20160703 |
| in sospeso |Numero di utenti univoci in sospeso. |123 |
| riuscito |Numero di utenti univoci in stato completato. |12 |
| error |Numero di utenti univoci in stato di errore. |10 |
| non riuscito |Numero di utenti univoci in stato non riuscito. |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

L'entità **policyTypeActivity** elenca il numero cumulativo di dispositivi nello stato completato, in sospeso, non riuscito o di errore. Vengono elencati questi stati rispetto a un profilo di configurazione del dispositivo, un profilo di configurazione dell'app o ai criteri di conformità per ogni giorno.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| dateKey |dateKey in cui l'archiviazione del profilo di configurazione del dispositivo è stata registrata nel data warehouse. |20160703 |
| policyKey |policyKey, può essere unita a policy per ottenere policyName. |Windows 10 baseline |
| policyTypeKey |Tipo di chiave dei criteri, può essere unita con il tipo di criterio per ottenere il nome del tipo di criterio. |Criteri di conformità di Windows 10 |
| in sospeso |Numero di dispositivi univoci in sospeso. |123 |
| riuscito |Numero di dispositivi univoci in stato completato. |12 |
| error |Numero di dispositivi univoci in stato di errore. |10 |
| non riuscito |Numero di dispositivi univoci in stato non riuscito. |2 |

## <a name="compliance-policy"></a>Criteri di conformità

Le informazioni di riferimento sull'API dei criteri di conformità contengono le entità che forniscono informazioni sullo stato per i criteri di conformità assegnati ai dispositivi.

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

La tabella seguente contiene un riepilogo dello stato di assegnazione dei criteri di conformità ai dispositivi. La tabella elenca il numero di dispositivi trovati in ogni stato di conformità.


|Proprietà     |Descrizione  |Esempio  |
|---------|---------|---------|
|dateKey  |Chiave della data in cui è stato creato il riepilogo per i criteri di conformità.|20161204 |
|unknown  |Numero di dispositivi che sono offline o che non sono riusciti a comunicare con Intune o Azure AD per altri motivi. |5|
|notApplicable      |Numero di dispositivi in cui i criteri di conformità dei dispositivi assegnati dall'amministratore non sono applicabili.|201 |
|compliant      |Numero di dispositivi che hanno applicato correttamente uno o più criteri di conformità dei dispositivi assegnati dall'amministratore. |4083 |
|inGracePeriod      |Numero di dispositivi che non sono conformi, ma che si trovano nel periodo di tolleranza definito dall'amministratore. |57|
|nonCompliant      |Numero di dispositivi che non sono riusciti ad applicare uno o più criteri di conformità assegnati dall'amministratore o in cui l'utente non ha soddisfatto la conformità ai criteri assegnati dall'amministratore.|43 |
|error      |Numero di dispositivi che non sono riusciti a comunicare con Intune o Azure AD e che hanno restituito un messaggio di errore. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

La tabella seguente contiene un riepilogo dello stato di assegnazione dei criteri di conformità ai dispositivi in base a ciascun criterio e al tipo di criterio. La tabella elenca il numero di dispositivi trovati in ogni stato di conformità per ogni criterio di conformità assegnato.



|Proprietà  |Descrizione  |Esempio  |
|---------|---------|---------|
|dateKey  |Chiave della data in cui è stato creato il riepilogo per i criteri di conformità.|20161219|
|policyKey     |Chiave per il criterio di conformità per cui è stato creato il riepilogo. |10178 |
|policyPlatformKey      |Chiave per il tipo di piattaforma del criterio di conformità per cui è stato creato il riepilogo.|5|
|unknown     |Numero di dispositivi che sono offline o che non sono riusciti a comunicare con Intune o Azure AD per altri motivi.|13|
|notApplicable     |Numero di dispositivi in cui i criteri di conformità dei dispositivi assegnati dall'amministratore non sono applicabili.|3|
|compliant      |Numero di dispositivi che hanno applicato correttamente uno o più criteri di conformità dei dispositivi assegnati dall'amministratore. |45|
|inGracePeriod      |Numero di dispositivi che non sono conformi, ma che si trovano nel periodo di tolleranza definito dall'amministratore. |3|
|nonCompliant      |Numero di dispositivi che non sono riusciti ad applicare uno o più criteri di conformità assegnati dall'amministratore o in cui l'utente non ha soddisfatto la conformità ai criteri assegnati dall'amministratore.|7|
|error      |Numero di dispositivi che non sono riusciti a comunicare con Intune o Azure AD e che hanno restituito un messaggio di errore. |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

La tabella seguente contiene i tipi di piattaforma di tutti i criteri assegnati. I tipi di piattaforma dei criteri che non sono mai stati assegnati ad alcun dispositivo non sono inclusi nella tabella.


|Proprietà  |Descrizione  |Esempio  |
|---------|---------|---------|
|policyPlatformTypeKey      |Chiave univoca per il tipo di piattaforma dei criteri. |20170519 |
|policyPlatformTypeId      |Identificatore univoco per il tipo di piattaforma dei criteri.|1|
|policyPlatformTypeName      |Nome del tipo di piattaforma dei criteri.|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

La tabella seguente elenca il numero di dispositivi con stato completato, in sospeso, non riuscito o di errore ogni giorno. Il numero riflette i dati per ogni profilo del tipo di criteri. Ad esempio, se un dispositivo è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un dispositivo sono assegnati due profili, uno nello stato completato e l'altro in uno stato di errore, l'entità incrementa il contatore di completamento e colloca il dispositivo in stato di errore. L'entità policyDeviceActivity elenca il numero di dispositivi che sono in un determinato stato in un giorno specifico negli ultimi 30 giorni.

|Proprietà  |Descrizione  |Esempio  |
|---------|---------|---------|
|dateKey|Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse.|20160703|
|in sospeso|Numero di dispositivi univoci in sospeso.|123|
|Operazione riuscita|Numero di dispositivi univoci in stato completato.|12|
|policyKey|policyKey, può essere unita a policy per ottenere policyName.|Windows 10 baseline|
|error|Numero di dispositivi univoci in stato di errore.|10|
|non riuscito|Numero di dispositivi univoci in stato non riuscito.|2|

### <a name="policyuseractivities"></a>policyUserActivities

La tabella seguente elenca il numero di utenti con stato completato, in sospeso, non riuscito o di errore ogni giorno. Il numero riflette i dati per ogni profilo del tipo di criteri. Ad esempio, se un utente è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un utente sono assegnati due profili, uno con stato completato e l'altro con stato di errore, viene considerato l'utente con lo stato di errore. L'entità PolicyUserActivity elenca il numero di utenti in ogni stato in un giorno specifico negli ultimi 30 giorni.


| Proprietà  |                                         Descrizione                                         |       Esempio       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |      20160703       |
|  in sospeso  |                         Numero di dispositivi univoci in sospeso.                          |         123         |
| riuscito |                         Numero di dispositivi univoci in stato completato.                          |         12          |
| policyKey |                 policyKey, può essere unita a policy per ottenere policyName.                 | Windows 10 baseline |
|   error   |                          Numero di dispositivi univoci in stato di errore.                           |         10          |

