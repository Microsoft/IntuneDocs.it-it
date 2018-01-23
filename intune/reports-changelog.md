---
title: Registro modifiche per il data warehouse di Intune | Microsoft Docs
description: Elenco delle modifiche nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e17ca34897a707360d802e37ffe3fa91fad0860
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2018
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro modifiche per l'API data warehouse di Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Tenersi aggiornati con il data warehouse di Intune.

## <a name="1710"></a>1710
_Ultimo aggiornamento: novembre 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Una nuova raccolta di entità denominata Current User è limitata ai dati degli utenti attualmente attivi <!-- 1544273 -->

La raccolta di entità **Users** contiene tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione. In questi record sono inclusi gli stati utente registrati nel periodo di raccolta dei dati, anche se l'utente è stato rimosso. Nel corso dell'ultimo mese, ad esempio, è possibile che un utente sia stato aggiunto e rimosso da Intune. Pertanto, se anche l'utente non è presente al momento del report, l'utente e lo stato sono comunque presenti nei dati. In questo caso, è possibile creare un report che mostri la durata della presenza storica dell'utente nei dati.

La nuova raccolta di entità **Current User**, invece, contiene solo gli utenti che non sono stati rimossi. La raccolta di entità **Current User**, quindi, è limitata agli utenti attualmente attivi. Per informazioni sulla raccolta di entità **Current User**, vedere [Informazioni di riferimento per l'entità User corrente](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Ultimo aggiornamento: ottobre 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Raccolta di entità di associazione dei dispositivi degli utenti aggiunta al modello di dati di Data Warehouse di Intune <!-- 1187917 -->

Ora è possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi. Il modello di dati è accessibile tramite il file di Power BI (PBIX) recuperato dalla pagina Data warehouse di Intune, tramite l'endpoint OData oppure sviluppando un client personalizzato. Per altre informazioni, vedere [Associazione utente-dispositivo](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nuove entità nel modello di dati del data warehouse <!-- 1479526 --><!-- -->

 - È stata aggiunta l'entità [**UserDeviceAssociation**](reports-ref-user-device.md). L'entità **UserDeviceAssociation** contiene le associazioni utente-dispositivo presenti nell'organizzazione. Ora è possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi.  
 - Entità [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md)aggiunta. **IntuneManagementExtension** contiene le entità per i dispositivi mobili che tengono traccia delle informazioni, quali stato di installazione e versione.

## <a name="next-steps"></a>Passaggi successivi
 - Informazioni sulle [novità di Intune ogni settimana](whats-new.md), oltre a indicazioni su modifiche previste, avvisi importanti sul servizio e informazioni sulle versioni precedenti.
 - Leggere il [blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882).
