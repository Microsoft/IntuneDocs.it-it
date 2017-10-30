---
title: Associazione utente-dispositivo | Microsoft Docs
description: "Argomento di riferimento per la categoria di associazione utente-dispositivo della raccolte di entità nell'API data warehouse di Intune."
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: BCDBABCB-A7B1-42F2-BDD1-D055E33F2239
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 490e29f87c65875a385472e6abe9400363383f9b
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-device-association-entity"></a>Riferimento per l'entità dell'associazione utente-dispositivo

La categoria dell'**associazione utente-dispositivo** include l'entità dell'**associazione utente-dispositivo** usata per definire le associazioni dei dispositivi nell'organizzazione.

**Associazione utente-dispositivo**

L'entità dell'**associazione utente-dispositivo** rappresenta le associazioni dei dispositivi nell'organizzazione.

| Nome               | Descrizione                                                                                      | Esempio                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificatore univoco dell'utente nel data warehouse, chiave surrogata.                             | 123                    |
| DeviceKey          | Identificatore univoco del dispositivo nel data warehouse.                                           | 123                    |
| CreatedDateTimeUTC | Data e ora in formato UTC della creazione dell'associazione utente-dispositivo.                               | 23/11/2016 12.00.00 |
| IsDeleted          | Indica che l'utente ha annullato la registrazione del dispositivo e che l'associazione non è più aggiornata. | True                   |
| EndedDateTimeUTC   | Data e ora in formato UTC in cui IsDeleted è stato impostato su **True**.                                         | 23/06/2017 12.00.00 |