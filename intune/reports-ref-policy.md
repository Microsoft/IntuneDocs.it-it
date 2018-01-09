---
title: Policy | Microsoft Docs
description: "Argomento di riferimento per la categoria Policy delle raccolte di entità nell'API data warehouse di Intune."
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D5ADB9D8-D46A-43BD-AB0F-D6927508E3F4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 06c489f8519bda2f3f0359589c3af845ade423fe
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
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
| Failed |Numero di dispositivi univoci in stato non riuscito. |2 |

## <a name="userconfiguration"></a>UserConfiguration

L'entità **UserConfigurationProfileDeviceActivity** elenca il numero di utenti nello stato completato, in sospeso, non riuscito o di errore al giorno. Il numero rispecchia i profili di configurazione dispositivo assegnati all'entità. Ad esempio, se un utente è nello stato completato per tutti i relativi criteri assegnati, incrementa di uno il contatore di completamento per tale giorno. Se a un utente sono assegnati due profili, uno in stato completato mentre l'altro è in stato di errore, viene considerato l'utente nello stato di errore.  L'entità **UserConfigurationProfileDeviceActivity** elenca quanti utenti sono in un determinato stato in un giorno specifico negli ultimi 30 giorni.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| DateKey |Chiave data in cui l'archiviazione del profilo di configurazione dispositivo è stata registrata nel data warehouse. |20160703 |
| Pending |Numero di utenti univoci in sospeso. |123 |
| Operazione completata |Numero di utenti univoci in stato completato. |12 |
| Errore |Numero di utenti univoci in stato di errore. |10 |
| Failed |Numero di utenti univoci in stato non riuscito. |2 |

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
| Fail- |Numero di dispositivi univoci in stato non riuscito. |2 |