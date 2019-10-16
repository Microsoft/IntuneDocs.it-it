---
title: Archiviazione ed elaborazione dei dati in Intune
titleSuffix: Microsoft Intune
description: Informazioni su come vengono archiviati ed elaborati i dati personali in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c9a8bd5888ab0977d1ca553d059c1e96cccda75
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306890"
---
# <a name="data-storage-and-processing-in-intune"></a>Archiviazione ed elaborazione dei dati in Intune

Dopo la [raccolta dei dati](privacy-data-collect.md) in Intune, l'archiviazione e l'elaborazione di tali dati procede come indicato in dettaglio di seguito.

## <a name="storing-personal-data"></a>Archiviazione dei dati personali

Tutti i dati non di telemetria raccolti vengono elaborati tramite il servizio Intune e archiviati in una o più delle posizioni di archiviazione seguenti: 

- SQL Azure 
- Raccolte affidabili (Service Fabric)  
- Archiviazione di Azure 

I dati di telemetria (log del servizio, log di prestazioni, errori e così via) fondamentali per il monitoraggio e la fornitura di un servizio stabile vengono inviati agli archivi dati di telemetria Microsoft.

### <a name="storage-locations"></a>Posizioni di archiviazione

Microsoft offre e gestisce servizi di Intune in numerose aree in tutto il mondo. Intune rispetta le scelte per le posizioni di archiviazione effettuate dall'amministratore per i dati dei clienti.

Per altre informazioni, vedere [Dove vengono archiviati i tuoi dati](https://www.microsoft.com/trust-center/privacy/data-location)

### <a name="personal-data-retention"></a>Conservazione dei dati personali

In generale, i dati personali vengono conservati da Intune per 30 giorni dopo la rimozione dell'utente dalla gestione di Intune.

I dati di telemetria raccolti nell'ambito dell'utilizzo di Intune vengono conservati per un massimo di 30 giorni.

I log di controllo vengono mantenuti fino a un massimo di un anno.

## <a name="processing-personal-data"></a>Elaborazione dei dati personali

Intune elabora i dati personali con sistemi certificati ISO. Per altre informazioni, vedere [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Profilatura e marketing

Microsoft Intune non usa i dati personali raccolti nell'ambito della fornitura del servizio per scopi di profilatura o marketing. 

### <a name="restrict-processing-of-personal-data"></a>Limitare l'elaborazione dei dati personali

Per limitare l'elaborazione dei dati personali dell'utente, è possibile eliminare l'account dell'utente come segue:
1. Esportazione di una copia in formato elettronico dei dati personali dell'utente, tra cui
    - account
    - dati del servizio
    - log associati
2. Eliminazione dell'account dell'utente e dei dati associati da Intune.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni su come Intune [protegge e condivide](privacy-data-secure-share.md) i dati personali. 
