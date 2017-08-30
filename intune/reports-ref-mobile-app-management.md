---
title: Gestione delle app mobili (MAM) | Microsoft Docs
description: "Argomento di riferimento per la categoria Gestione delle app mobili delle raccolte di entità nell'API data warehouse di Intune."
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 44358d68a653760804f11668ab64d30ebf7ae9eb
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2017
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
| ApplicationKey |Identificatore univoco dell'app MAM nel data warehouse |123 |
| ApplicationName |Nome dell'app MAM |"Word" |
| ApplicationId |ID applicazione dell'app MAM |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Indica se il record dell'app MAM è stato aggiornato. True: l'app MAM ha un nuovo record con i campi aggiornati in questa tabella. False: l'ultimo record per questa app MAM. |True/False |
| StartDateInclusiveUTC |Data e ora in formato UTC in cui l'app MAM è stata creata nel data warehouse |23/11/2016 12.00.00 |
| DeletedDateUTC |Data e ora in formato UTC quando IsDeleted è diventato True |23/11/2016 12.00.00 |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica dell'app MAM nel data warehouse |23/11/2016 12.00.00 |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

L'entità **MamApplicationInstance** elenca le app Gestione delle app mobili (MAM) come istanze individuali per ogni utente di ciascun dispositivo. Tutti gli utenti e i dispositivi elencati nell'entità sono protetti, cioè hanno almeno un criterio MAM assegnato.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| ApplicationInstanceKey |Identificatore univoco dell'istanza di app MAM nel data warehouse - chiave surrogata |123 |
| UserId |Id utente dell'utente che ha installato l'app MAM |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |Identificatore univoco dell'istanza di app MAM - simile a ApplicationInstanceKey, ma l'identificatore è una chiave naturale |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |ID applicazione di questa app MAM |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |Versione dell'applicazione di questa app MAM |2 |
| CreatedDate |Data di creazione del record dell'istanza di app MAM. Il valore può essere Null. |23/11/2016 12.00.00 |
| Piattaforma |Piattaforma del dispositivo in cui è installata l'app MAM |2 |
| PlatformVersion |Versione della piattaforma del dispositivo in cui è installata l'app MAM |2.2 |
| SdkVersion |Versione dell'SDK MAM con cui è stato eseguito il wrapping di questa app MAM |3.2 |
| DeviceId |ID dispositivo del dispositivo in cui è installata l'app MAM |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |Nome del dispositivo in cui è installata l'app MAM |"MyDevice" |
| IsDeleted |Indica se il record dell'istanza di app MAM è stato aggiornato. True: quest'istanza di app MAM ha un nuovo record con i campi aggiornati in questa tabella. False: l'ultimo record per questa istanza di app MAM. |True/False |
| StartDateInclusiveUTC |Data e ora in formato UTC in cui l'istanza di app MAM è stata creata nel data warehouse |23/11/2016 12.00.00 |
| DeletedDateUtc |Data e ora in formato UTC quando IsDeleted è diventato True |23/11/2016 12.00.00 |
| RowLastModifiedDateTimeUtc |Data e ora in formato UTC dell'ultima modifica apportata all'istanza di app MAM nel data warehouse |23/11/2016 12.00.00 |

## <a name="mamcheckin"></a>MamCheckin

L'entità **MamCheckin** rappresenta i dati raccolti quando un'istanza di app Gestione di applicazioni mobili (MAM) è stata archiviata con il servizio Intune. 

> [!Note]  
> Quando un'istanza di app viene archiviata più volte al giorno, il data warehouse la memorizza come archiviazione unica.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| DateKey |Chiave data in cui l'archiviazione dell'app MAM è stata registrata nel data warehouse | 20160703 |
| ApplicationInstanceKey |Chiave dell'istanza di app associata a questa archiviazione dell'app MAM |2/5/1900 12.00.00 |
| UserKey |Chiave dell'utente associata a questa archiviazione dell'app MAM |12/1/1900 12.00.00 |
| ApplicationKey |Chiave dell'app MAM che è stata archiviata |10/1/1900 12.00.00 |
| DeviceHealthKey |Chiave DeviceHealth associata a questa archiviazione dell'app MAM |2/1/1900 12.00.00 |
| PlatformKey |Rappresenta la piattaforma del dispositivo associato a questa archiviazione dell'app MAM |1/1/1900 12:00:00 AM |
| EffectiveAppliedPolicyKey |Rappresenta il criterio valido applicato, associato a questa archiviazione dell'app MAM. Un criterio valido applicato risulta dall'unione di tutti i criteri pertinenti a una particolare app e utente. |2/5/1900 12.00.00 |
| LastCheckInDate |Data e ora dell'ultima archiviazione di questa app MAM. Il valore può essere Null. |23/11/2016 12.00.00 |

## <a name="mamdevicehealth"></a>MamDeviceHealth

L'entità **MamDeviceHealth** rappresenta i dispositivi in cui sono stati distribuiti i criteri di Gestione per applicazioni mobili (MAM) anche se sono jailbroken.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| DeviceHealthKey |Identificatore univoco del dispositivo e integrità associata nel data warehouse - chiave surrogata |1/1/1900 12:00:00 AM |
| DeviceHealth |Identificatore univoco del dispositivo e integrità, simile a DeviceHealthKey, ma l'identificatore è una chiave naturale |1/1/1900 12:00:00 AM |
| DeviceHealthName |Rappresenta lo stato del dispositivo. Non disponibile- nessuna informazione su questo dispositivo. Integro - dispositivo non jailbroken. Non integro - dispositivo jailbroken. |Non disponibile Integro Non integro |
| RowLastModifiedDateTimeUtc |Data e ora in formato UTC dell'ultima modifica apportata all'integrità del dispositivo specifico nel data warehouse |23/11/2016 12.00.00 |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

L'entità **MamEffectivePolicy** elenca tutti i criteri validi di Gestione di applicazioni mobili (MAM) applicati nell'organizzazione. Un criterio valido applicato risulta dall'unione di tutti i criteri pertinenti a una particolare app e utente.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| EffectivePolicyKey |Identificatore univoco del criterio valido MAM nel data warehouse |2 |
| RealPolicyKey |Identificatore univoco del criterio MAM creato dal professionista IT. |1 |
| RowCreatedDateTimeUtc |Data e ora in formato UTC in cui il criterio valido MAM è stato creato nel data warehouse. |23/11/2016 12.00.00 |

## <a name="mamglobalapplication"></a>MamGlobalApplication

L'entità **MamGlobalApplication** elenca le app dello Store gestite attraverso Gestione delle app mobili (MAM) senza la registrazione aziendale.

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| ApplicationKey |Identificatore univoco dell'app dello store nel data warehouse, noto come chiave surrogata. |123 |
| ApplicationId |Identificatore univoco dell'app dello store. L'identificatore è simile a ApplicationKey, ma è una chiave naturale. |com.microsoft.skydrive.<ios> |
| ApplicationName |Nome dell'applicazione globale MAM. |OneDrive |
| RowLastModifiedDateTimeUtc |Data e ora in formato UTC dell'ultima modifica apportata all'applicazione globale MAM specifica nel data warehouse. |23/11/2016 12.00.00 |

## <a name="mamplatform"></a>MamPlatform

L'entità **MamPlatform** elenca i nomi e i tipi di piattaforma in cui è stata installata l'app di Gestione di applicazioni mobili (MAM).

| Proprietà | Descrizione | Esempio |
|---------|------------|--------|
| PlatformKey |Identificatore univoco della piattaforma nel data warehouse - chiave surrogata |123 |
| Piattaforma |Identificatore univoco della piattaforma, simile a PlatformKey, ma è una chiave naturale |123 |
| PlatformName |Nome della piattaforma |Non è disponibile Nessuno Android IOS Windows |
| RowLastModifiedDateTimeUtc |Data e ora in formato UTC dell'ultima modifica di questa piattaforma nel data warehouse |23/11/2016 12.00.00 |