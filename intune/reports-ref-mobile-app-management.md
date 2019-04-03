---
title: Gestione delle app mobili (MAM)
titlesuffix: Microsoft Intune
description: Argomento di riferimento per la categoria Gestione delle app mobili delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 524a4f39ba6a319f42ca23c7d85e84ffd86fce0d
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358217"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Informazioni di riferimento per le entità di gestione delle app mobili (MAM)

La categoria **Gestione delle app mobili** contiene entità per le app per dispositivi mobili come:

  -  App
  -  Instances
  -  Stato di archiviazione
  -  Stato di integrità
  -  Stato criteri
  -  Stato registrazione
  -  Tipi di piattaforma

## <a name="mamapplication"></a>MamApplication

L'entità **MamApplication** elenca le app Line-of-Business (LOB) gestite attraverso Gestione delle app mobili (MAM) senza la registrazione aziendale.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| IsDeleted |Indica se il record dell'app MAM è stato aggiornato. <br>True: l'app MAM ha un nuovo record con i campi aggiornati in questa tabella. <br>False: l'ultimo record per questa app MAM. |True/False |
| StartDateInclusiveUTC |Data e ora in formato UTC della creazione dell'app MAM nel data warehouse. |23/11/2016 12.00.00 |
| DeletedDateUTC |Data e ora in formato UTC in cui IsDeleted è stato impostato su True. |23/11/2016 12.00.00 |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica dell'app MAM nel data warehouse. |23/11/2016 12.00.00 |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

L'entità **MamApplicationInstance** elenca le app Gestione delle app mobili (MAM) come istanze individuali per ogni utente di ciascun dispositivo. Tutti gli utenti e i dispositivi elencati nell'entità sono protetti, cioè hanno almeno un criterio MAM assegnato.


|          Proprietà          |                                                                                                  Descrizione                                                                                                  |               Esempio                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Identificatore univoco dell'istanza dell'app MAM nel data warehouse, chiave surrogata.                                                                |                 123                  |
|           UserId           |                                                                              ID dell'utente che ha installato l'app MAM.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Identificatore univoco dell'istanza dell'app MAM, simile ad ApplicationInstanceKey, ma l'identificatore è una chiave naturale.                                              | b66bc706-ffff-7437-0340-032819502773 |
|     ApplicationVersion     |                                                                                     Versione dell'applicazione dell'app MAM.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Data di creazione del record dell'istanza di app MAM. Il valore può essere Null.                                                                 |        23/11/2016 12.00.00        |
|          Piattaforma          |                                                                          Piattaforma del dispositivo in cui è installata l'app MAM.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Versione della piattaforma del dispositivo in cui è installata l'app MAM.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            Versione dell'SDK MAM con cui è stato eseguito il wrapping dell'app MAM.                                                                            |                 3.2                  |
|         IsDeleted          | Indica se il record dell'istanza di app MAM è stato aggiornato. <br>True: quest'istanza di app MAM ha un nuovo record con i campi aggiornati in questa tabella. <br>False: l'ultimo record per questa istanza di app MAM. |              True/False              |
|   StartDateInclusiveUTC    |                                                              Data e ora in formato UTC della creazione dell'istanza dell'app MAM nel data warehouse.                                                               |        23/11/2016 12.00.00        |
|       DeletedDateUtc       |                                                                             Data e ora in formato UTC in cui IsDeleted è stato impostato su True.                                                                              |        23/11/2016 12.00.00        |
| RowLastModifiedDateTimeUtc |                                                           Data e ora in formato UTC dell'ultima modifica apportata all'istanza dell'app MAM nel data warehouse.                                                            |        23/11/2016 12.00.00        |

## <a name="mamcheckin"></a>MamCheckin

L'entità **MamCheckin** rappresenta i dati raccolti quando un'istanza di app Gestione di applicazioni mobili (MAM) è stata archiviata con il servizio Intune. 

> [!Note]  
> Quando un'istanza di app viene archiviata più volte al giorno, il data warehouse la memorizza come archiviazione unica.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| DateKey |Chiave data in cui l'archiviazione dell'app MAM è stata registrata nel data warehouse. | 20160703 |
| ApplicationInstanceKey |Chiave dell'istanza dell'app associata all'archiviazione dell'app MAM. | 123 |
| UserKey |Chiave dell'utente associata all'archiviazione dell'app MAM. | 4323 |
| DeviceHealthKey |Chiave di DeviceHealth associata all'archiviazione dell'app MAM. | 321 |
| PlatformKey |Rappresenta la piattaforma del dispositivo associato all'archiviazione dell'app MAM. |123 |
| EffectiveAppliedPolicyKey |Rappresenta il criterio valido applicato, associato a questa archiviazione dell'app MAM. Un criterio valido applicato risulta dall'unione di tutti i criteri pertinenti a una particolare app e utente. | 322 |
| LastCheckInDate |Data e ora dell'ultima archiviazione di questa app MAM. Il valore può essere Null. |23/11/2016 12.00.00 |

## <a name="mamdevicehealth"></a>MamDeviceHealth

L'entità **MamDeviceHealth** rappresenta i dispositivi in cui sono stati distribuiti i criteri di Gestione per applicazioni mobili (MAM) anche se sono jailbroken.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| DeviceHealthKey |Identificatore univoco del dispositivo e integrità associata nel data warehouse, chiave surrogata. |123 |
| DeviceHealth |Identificatore univoco del dispositivo e integrità associata, simile a DeviceHealthKey ma l'identificatore è una chiave naturale. |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |Rappresenta lo stato del dispositivo. <br>Non disponibile- nessuna informazione su questo dispositivo. <br>Integro - dispositivo non jailbroken. <br>Non integro - dispositivo jailbroken. |Non disponibile Integro Non integro |
| RowLastModifiedDateTimeUtc |Data e ora in formato UTC dell'ultima modifica apportata all'integrità del dispositivo MAM specifico nel data warehouse. |23/11/2016 12.00.00 |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

L'entità **MamEffectivePolicy** elenca tutti i criteri validi di Gestione di applicazioni mobili (MAM) applicati nell'organizzazione. Un criterio valido applicato risulta dall'unione di tutti i criteri pertinenti a una particolare app e utente.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| EffectivePolicyKey |Identificatore univoco del criterio valido MAM nel data warehouse. |2 |
| RealPolicyKey |Identificatore univoco del criterio MAM creato dal professionista IT. |1 |
| RowCreatedDateTimeUtc |Data e ora in formato UTC in cui il criterio valido MAM è stato creato nel data warehouse. |23/11/2016 12.00.00 |

## <a name="mamglobalapplication"></a>MamGlobalApplication

L'entità **MamGlobalApplication** elenca le app dello Store gestite attraverso Gestione delle app mobili (MAM) senza la registrazione aziendale.


|          Proprietà          |                                               Descrizione                                               |           Esempio            |
|----------------------------|---------------------------------------------------------------------------------------------------------|------------------------------|
|       ApplicationKey       |          Identificatore univoco dell'app dello store nel data warehouse, noto come chiave surrogata.          |             123              |
|       ApplicationId        | Identificatore univoco dell'app dello store. L'identificatore è simile a ApplicationKey, ma è una chiave naturale.  | com.microsoft.skydrive.<ios> |
|      ApplicationName       |                                      Nome dell'applicazione globale MAM.                                       |           OneDrive           |
| RowLastModifiedDateTimeUtc | Data e ora in formato UTC dell'ultima modifica apportata all'applicazione globale MAM specifica nel data warehouse. |    23/11/2016 12.00.00    |

## <a name="mamplatform"></a>MamPlatform

L'entità **MamPlatform** elenca i nomi e i tipi di piattaforma in cui è stata installata l'app di Gestione di applicazioni mobili (MAM).


|          Proprietà          |                                    Descrizione                                    |                         Esempio                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Identificatore univoco della piattaforma nel data warehouse, chiave surrogata.      |                           123                           |
|          Piattaforma          | Identificatore univoco della piattaforma, simile a PlatformKey ma è una chiave naturale. |                           123                           |
|        PlatformName        |                                   Nome della piattaforma                                   | Non disponibile <br>Nessuno <br>Windows <br>iOS <br>Android. |
| RowLastModifiedDateTimeUtc | Data e ora in formato UTC dell'ultima modifica della piattaforma nel data warehouse.  |                 23/11/2016 12.00.00                  |

