---
title: Associazione utente-dispositivo nel data warehouse di Intune
titleSuffix: Microsoft Intune
description: L'entità UserDeviceAssociation contiene le associazioni utente-dispositivo presenti nell'organizzazione.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 466066faf03cbdf560697a04310eac844d4f1b87
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798261"
---
# <a name="reference-for-user-device-association-entity"></a>Riferimento per l'entità dell'associazione utente-dispositivo

L'entità **UserDeviceAssociation** contiene le associazioni utente-dispositivo presenti nell'organizzazione.

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        Name        |                                           Descrizione                                            |        Esempio         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              Identificatore univoco dell'utente nel data warehouse (chiave sostitutiva).               |          123           |
|     DeviceKey      |                      Identificatore univoco del dispositivo nel data warehouse.                      |          123           |
| CreatedDateTimeUTC |           Data e ora della creazione dell'associazione utente-dispositivo. Viene usato il formato UTC.           | 23/11/2016 12.00.00 |
|     IsDeleted      | Indica che l'utente ha annullato la registrazione del dispositivo e che l'associazione non è più aggiornata. |       True/False       |
|  EndedDateTimeUTC  |              Data e ora in formato UTC in cui IsDeleted è stato impostato su <strong>True</strong>.               | 23/06/2017 12.00.00 |

## <a name="next-steps"></a>Passaggi successivi

- Altre informazioni sul [data warehouse di Intune](reports-nav-create-intune-reports.md).
