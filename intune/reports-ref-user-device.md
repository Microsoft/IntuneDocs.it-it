---
title: Associazione utente-dispositivo nel data warehouse di Intune | Microsoft Docs
description: Elenco delle modifiche nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 095395be4c86780ad65ba1e24b856f6eef8d41ae
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2018
---
# <a name="user-device-association"></a>Associazione utente-dispositivo

L'entità **UserDeviceAssociation** contiene le associazioni utente-dispositivo presenti nell'organizzazione.

| Name               | Descrizione                                                                                      | Esempio                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificatore univoco dell'utente nel data warehouse (chiave sostitutiva).                              | 123                    |
| DeviceKey          | Identificatore univoco del dispositivo nel data warehouse.                                            | 123                    |
| CreatedDateTimeUTC | Data e ora della creazione dell'associazione utente-dispositivo. Viene usato il formato UTC.                                | 23/11/2016 12.00.00 |
| IsDeleted          | Indica che l'utente ha annullato la registrazione del dispositivo e che l'associazione non è più aggiornata. | True/False             |
| EndedDateTimeUTC   | Data e ora in formato UTC in cui IsDeleted è stato impostato su **True**.                                              | 23/06/2017 12.00.00 |
