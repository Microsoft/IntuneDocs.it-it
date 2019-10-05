---
title: Gestione delle app mobili (MAM)
titleSuffix: Microsoft Intune
description: Argomento di riferimento per la categoria Gestione delle app mobili delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f06d2b4b61d522dced12e5d08cd1e854aefd9de8
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939938"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Informazioni di riferimento per le entità di gestione delle app mobili (MAM)

La categoria **Gestione delle app mobili** contiene entità per le app per dispositivi mobili come:

- App
- Instances
- Stato di archiviazione
- Stato di integrità
- Stato criteri
- Stato registrazione
- Tipi di piattaforma

## <a name="mamapplications"></a>mamApplications

L'entità **mamApplication** elenca le app Line-of-Business (LOB) gestite attraverso Gestione delle app mobili (MAM) senza la registrazione aziendale.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| mamApplicationKey |Identificatore univoco dell'applicazione MAM. | 432 |
| mamApplicationName |Nome dell'applicazione MAM. |Esempio di nome dell'applicazione MAM |
| mamApplicationId |ID applicazione dell'applicazione MAM. | 123 |
| isDeleted |Indica se il record dell'app MAM è stato aggiornato. <br>True: l'app MAM ha un nuovo record con i campi aggiornati in questa tabella. <br>False: l'ultimo record per questa app MAM. |True/False |
| startDateInclusiveUTC |Data e ora in formato UTC della creazione dell'app MAM nel data warehouse. |23/11/2016 12.00.00 |
| deletedDateUTC |Data e ora in formato UTC in cui IsDeleted è stato impostato su True. |23/11/2016 12.00.00 |
| rowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica dell'app MAM nel data warehouse. |23/11/2016 12.00.00 |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

L'entità **mamApplicationInstance** elenca le app MAM (Gestione di applicazioni mobili) come istanze individuali per ogni utente di ciascun dispositivo. Tutti gli utenti e i dispositivi elencati nell'entità sono protetti, cioè hanno almeno un criterio MAM assegnato.


|          Proprietà          |                                                                                                  Descrizione                                                                                                  |               Esempio                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               Identificatore univoco dell'istanza dell'app MAM nel data warehouse, chiave surrogata.                                                                |                 123                  |
|           userId           |                                                                              ID dell'utente che ha installato l'app MAM.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              Identificatore univoco dell'istanza dell'app MAM, simile ad ApplicationInstanceKey, ma l'identificatore è una chiave naturale.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | ID dell'applicazione MAM per cui è stata creata questa istanza di applicazione MAM.   | 23/11/2016 12.00.00   |
|     applicationVersion     |                                                                                     Versione dell'applicazione dell'app MAM.                                                                                      |                  2                   |
|        createdDate         |                                                                 Data di creazione del record dell'istanza di app MAM. Il valore può essere Null.                                                                 |        23/11/2016 12.00.00        |
|          piattaforma          |                                                                          Piattaforma del dispositivo in cui è installata l'app MAM.                                                                           |                  2                   |
|      platformVersion       |                                                                      Versione della piattaforma del dispositivo in cui è installata l'app MAM.                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            Versione dell'SDK MAM con cui è stato eseguito il wrapping dell'app MAM.                                                                            |                 3.2                  |
| mamDeviceId | ID del dispositivo a cui è associata l'istanza di applicazione MAM.   | 23/11/2016 12.00.00   |
| mamDeviceType | Tipo di dispositivo a cui è associata l'istanza di applicazione MAM.   | 23/11/2016 12.00.00   |
| mamDeviceName | Nome del dispositivo a cui è associata l'istanza di applicazione MAM.   | 23/11/2016 12.00.00   |
|         isDeleted          | Indica se il record dell'istanza di app MAM è stato aggiornato. <br>True: quest'istanza di app MAM ha un nuovo record con i campi aggiornati in questa tabella. <br>False: l'ultimo record per questa istanza di app MAM. |              True/False              |
|   startDateInclusiveUtc    |                                                              Data e ora in formato UTC della creazione dell'istanza dell'app MAM nel data warehouse.                                                               |        23/11/2016 12.00.00        |
|       deletedDateUtc       |                                                                             Data e ora in formato UTC in cui IsDeleted è stato impostato su True.                                                                              |        23/11/2016 12.00.00        |
| rowLastModifiedDateTimeUtc |                                                           Data e ora in formato UTC dell'ultima modifica apportata all'istanza dell'app MAM nel data warehouse.                                                            |        23/11/2016 12.00.00        |


## <a name="mamcheckins"></a>mamCheckins

L'entità **mamCheckin** rappresenta i dati raccolti quando un'istanza di app MAM (Gestione di applicazioni mobili) viene sincronizzata con il servizio Intune. 

> [!Note]  
> Quando un'istanza di app viene archiviata più volte al giorno, il data warehouse la memorizza come archiviazione unica.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| dateKey |Chiave data in cui l'archiviazione dell'app MAM è stata registrata nel data warehouse. | 20160703 |
| applicationInstanceKey |Chiave dell'istanza dell'app associata all'archiviazione dell'app MAM. | 123 |
| userKey |Chiave dell'utente associata all'archiviazione dell'app MAM. | 4323 |
| mamApplicationKey |Chiave applicazione associato all'archiviazione dell'applicazione MAM. | 432 |
| deviceHealthKey |Chiave di DeviceHealth associata all'archiviazione dell'app MAM. | 321 |
| platformKey |Rappresenta la piattaforma del dispositivo associato all'archiviazione dell'app MAM. |123 |
| effectiveAppliedPolicyKey |Rappresenta il criterio valido applicato, associato a questa archiviazione dell'app MAM. Un criterio valido applicato risulta dall'unione di tutti i criteri pertinenti a una particolare app e utente. | 322 |
| pastCheckInDate |Data e ora dell'ultima archiviazione di questa app MAM. Il valore può essere Null. |23/11/2016 12.00.00 |


## <a name="mamdevicehealth"></a>mamDeviceHealth

L'entità **mamDeviceHealth** rappresenta i dispositivi in cui sono stati distribuiti criteri MAM (Gestione di applicazioni mobili) anche se sono jailbroken.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| deviceHealthKey |Identificatore univoco del dispositivo e integrità associata nel data warehouse, chiave surrogata. |123 |
| deviceHealth |Identificatore univoco del dispositivo e integrità associata, simile a DeviceHealthKey ma l'identificatore è una chiave naturale. |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |Rappresenta lo stato del dispositivo. <br>Non disponibile- nessuna informazione su questo dispositivo. <br>Integro - dispositivo non jailbroken. <br>Non integro - dispositivo jailbroken. |Non disponibile Integro Non integro |
| rowLastModifiedDateTimeUtc |Data e ora in formato UTC dell'ultima modifica apportata all'integrità del dispositivo MAM specifico nel data warehouse. |23/11/2016 12.00.00 |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

L'entità **mamEffectivePolicy** elenca tutti i criteri validi di Gestione di applicazioni mobili (MAM) applicati nell'organizzazione. Un criterio valido applicato risulta dall'unione di tutti i criteri pertinenti a una particolare app e utente.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| effectivePolicyKey |Identificatore univoco del criterio valido MAM nel data warehouse. |2 |
| realPolicyKey |Identificatore univoco del criterio MAM creato dal professionista IT. |1 |
| rowCreatedDateTimeUtc |Data e ora in formato UTC in cui il criterio valido MAM è stato creato nel data warehouse. |23/11/2016 12.00.00 |

## <a name="mamplatforms"></a>mamPlatforms

L'entità **mamPlatform** elenca i nomi e i tipi di piattaforma in cui è stata installata l'app MAM (Gestione di applicazioni mobili).


|          Proprietà          |                                    Descrizione                                    |                         Esempio                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     Identificatore univoco della piattaforma nel data warehouse, chiave surrogata.      |                           123                           |
|          piattaforma          | Identificatore univoco della piattaforma, simile a PlatformKey ma è una chiave naturale. |                           123                           |
|        platformName        |                                   Nome della piattaforma                                   | Non disponibile <br>Nessuno <br>Windows <br>iOS <br>Android. |
| rowLastModifiedDateTimeUtc | Data e ora in formato UTC dell'ultima modifica della piattaforma nel data warehouse.  |                 23/11/2016 12.00.00                  |

