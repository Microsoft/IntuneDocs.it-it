---
title: User | Microsoft Docs
description: "Argomento di riferimento per la categoria User delle raccolte di entità nell'API data warehouse di Intune."
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: be8b7041882539c4e379074cffea385f582f686e
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-entity"></a>Informazioni di riferimento per l'entità User

La categoria **User** contiene l'entità **User** che definire le proprietà utente e agente nel modello di dati.

**Utente**

L'entità **User** elenca tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| UserKey |Identificatore univoco dell'utente nel data warehouse, chiave surrogata. |123 |
| UserId |Identificatore univoco dell'utente, simile a UserKey, ma è una chiave naturale. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Indirizzo di posta elettronica dell'utente. |John@constoso.com |
| DisplayName |Nome visualizzato dell'utente. |Luca |
| IntuneLicensed |Specifica se l'utente ha una licenza per Intune. |True/False |
| IsDeleted |Indica se il record utente è stato aggiornato.  True: questo utente ha un nuovo record con i campi aggiornati in questa tabella. False: l'ultimo record per questo utente. |True/False |
| StartDateInclusiveUTC |Data e ora in formato UTC della creazione dell'utente nel data warehouse. |23/11/2016 12.00.00 |
| EndDateExclusiveUTC |Data e ora in formato UTC in cui IsDeleted è stato impostato su True. |23/11/2016 12.00.00 |
| IsCurrent |Indica se il record dell'utente è corrente nel data warehouse. |True/False |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica dell'utente nel data warehouse. |23/11/2016 12.00.00 |

