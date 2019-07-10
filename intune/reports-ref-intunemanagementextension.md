---
title: Entità IntuneManagementExtension
titleSuffix: Microsoft Intune
description: Argomento di riferimento per l'entità della categoria IntuneManagementExtension della raccolta di entità nell'API Data Warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 934742108effda0a88f4bcc42e06daa12c55288c
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648848"
---
# <a name="reference-for-intune-management-extension"></a>Informazioni di riferimento per Intune Management Extension (Estensione di gestione di Intune)

La categoria **IntuneManagementExtension** contiene le entità per i dispositivi mobili che tengono traccia di informazioni come:

  - Versioni di IntuneManagementExtension
  - Stato di installazione di IntuneManagementExtension

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

L'entità **IntuneManagementExtensionVersion** elenca tutte le versioni usate da IntuneManagementExtension.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| ExtensionVersionKey |Identificatore univoco della versione IntuneManagementExtension. | 1 |
| ExtensionVersion |Numero della versione a 4 cifre. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

**IntuneManagementExtensionHealthState** elenca tutti i possibili stati di integrità di IntuneManagementExtension.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| ExtensionStateKey |Identificatore univoco dello stato di integrità. | 2 |
| ExtensionState |Stato di integrità di IntuneManagementExtension. | Healthy |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

**IntuneManagementExtension** elenca l'integrità di IntuneManagementExtension su ogni dispositivo Windows 10 al giorno.
I dati mantenuti sono quelli relativi agli ultimi 60 giorni. 


|      Proprietà       |                         Descrizione                         | Esempio |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               Identificatore univoco della data.                |   123   |
|      TenantKey      |              Identificatore univoco del tenant.               |   456   |
|      DeviceKey      |              Identificatore univoco del dispositivo.               |   789   |
| ExtensionVersionKey | Identificatore univoco della versione IntuneManagementExtension. |    1    |
|  ExtensionStateKey  |             Identificatore univoco dello stato di integrità.              |    2    |

