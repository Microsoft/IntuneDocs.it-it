---
title: Registro modifiche per il data warehouse di Intune | Microsoft Docs
description: Elenco delle modifiche nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b81846c2e45f968184d50d2ea7c50aabb86b4964
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro modifiche per l'API data warehouse di Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Tenersi aggiornati con il data warehouse di Intune.

## <a name="1710"></a>1710
_Versione rilasciata a ottobre 2017_

### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>L'entità User contiene i dati utente più recenti nel modello di dati del data warehouse <!-- 1544273 -->

La prima versione del modello di dati del data Warehouse di Intune contiene solo i dati storici e recenti di Intune. Durante la creazione di report non è possibile acquisire lo stato corrente di un utente. In questo aggiornamento l'[**entità User** ](reports-ref-user.md) viene popolata con i dati utente più recenti.

### <a name="new-entity-in-the-in-data-warehouse-data-model----1479526---"></a>Nuova entità nel modello di dati del data warehouse <!-- 1479526 -->

È stata aggiunta l'entità [**UserDeviceAssociation**](reports-ref-user-device.md). L'entità **UserDeviceAssociation** contiene le associazioni utente-dispositivo presenti nell'organizzazione.

## <a name="next-steps"></a>Passaggi successivi
 - Informazioni sulle [novità di Intune ogni settimana](whats-new.md), oltre a indicazioni su modifiche previste, avvisi importanti sul servizio e informazioni sulle versioni precedenti. 
 - Leggere il [blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882).