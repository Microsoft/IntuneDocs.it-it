---
title: Current User nel data warehouse di Intune
titlesuffix: Microsoft Intune
description: Argomento di riferimento per la categoria User delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3b94001310f9117b2c3ba7591d40891db891e86d
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="reference-for-current-user-entity"></a>Informazioni di riferimento per l'entità Current User

La categoria **Current User** contiene le proprietà utente nel modello di dati. La raccolta di entità **Current User** è limitata agli utenti attualmente attivi. L'entità contiene tutti gli utenti di Azure Active Directory attualmente assegnati a una licenza. La licenza può essere una licenza di Intune, una licenza ibrida o una licenza di Microsoft Office 365. Se un utente è stato rimosso, non verrà rappresentato nella raccolta Current User. Per una raccolta contenente una cronologia delle modifiche apportate allo stato di un utente, vedere [Informazioni di riferimento per l'entità User](reports-ref-user.md).


## <a name="current-user"></a>Utente corrente

L'entità **Current User** elenca tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| UserKey |Identificatore univoco dell'utente nel data warehouse, chiave surrogata. |123 |
| UserId |Identificatore univoco dell'utente, simile a UserKey, ma è una chiave naturale. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Indirizzo di posta elettronica dell'utente. |John@constoso.com |
| UPN | UPN dell'utente. | John@constoso.com |
| DisplayName |Nome visualizzato dell'utente. |Luca |
| IntuneLicensed |Specifica se l'utente ha una licenza per Intune. |True/False |
| StartDateInclusiveUTC |Data e ora in formato UTC della creazione dell'utente nel data warehouse. |23/11/2016 12.00.00 |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica dell'utente nel data warehouse. |23/11/2016 12.00.00 |

## <a name="next-steps"></a>Passaggi successivi
 - È possibile usare la raccolta di entità **User** per estendere i dati anche agli utenti non attualmente attivi. Per altre informazioni, vedere [Informazioni di riferimento per l'entità User](reports-ref-user.md).
 - Per altre informazioni su come il data warehouse controlla la durata di un utente in Intune, vedere [Rappresentazione della durata degli utenti nel data warehouse di Intune](reports-ref-user-timeline.md).
