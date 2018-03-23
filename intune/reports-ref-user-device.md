---
title: Associazione utente-dispositivo nel data warehouse di Intune
titlesuffix: Microsoft Intune
description: Elenco delle modifiche nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: de14444376cb2998f17f406f084c428523ef4e4f
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2018
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
