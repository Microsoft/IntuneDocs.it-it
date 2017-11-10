---
title: Associazione utente-dispositivo nel data warehouse di Intune | Microsoft Docs
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
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c47455b0139f7451796257a77859cbd9899a7dd
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2017
---
# <a name="user-device-association"></a>Associazione utente-dispositivo

L'entità **UserDeviceAssociation** contiene le associazioni utente-dispositivo presenti nell'organizzazione.

| Nome               | Descrizione                                                                                      | Esempio                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificatore univoco dell'utente nel data warehouse (chiave sostitutiva).                              | 123                    |
| DeviceKey          | Identificatore univoco del dispositivo nel data warehouse.                                            | 123                    |
| CreatedDateTimeUTC | Data e ora della creazione dell'associazione utente-dispositivo. Viene usato il formato UTC.                                | 23/11/2016 12.00.00 |
| IsDeleted          | Indica che l'utente ha annullato la registrazione del dispositivo e che l'associazione non è più aggiornata. | True/False             |
| EndedDateTimeUTC   | Data e ora in formato UTC in cui IsDeleted è stato impostato su **True**.                                              | 23/06/2017 12.00.00 |
