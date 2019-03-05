---
title: Entità IntuneManagementExtension
titlesuffix: Microsoft Intune
description: Argomento di riferimento per l'entità della categoria IntuneManagementExtension della raccolta di entità nell'API Data Warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1f56b7b1a2349ff6e5ab11fb5c4de4278f5af36
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228664"
---
# <a name="reference-for-intune-management-extension"></a>Informazioni di riferimento per Intune Management Extension (Estensione di gestione di Intune)

La categoria **IntuneManagementExtension** contiene le entità per i dispositivi mobili che tengono traccia di informazioni come:

  -  Versioni di IntuneManagementExtension
  -  Stato di installazione di IntuneManagementExtension

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

