---
title: User - Data warehouse di Intune
titlesuffix: Microsoft Intune
description: Argomento di riferimento per la categoria User delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 52201b68e946ec59b7c70ea5ff735c26728e27ce
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429730"
---
# <a name="reference-for-user-entity"></a>Informazioni di riferimento per l'entità User

La categoria **User** contiene l'entità **User** che definisce le proprietà utente nel modello di dati.

## <a name="user"></a>Utente

L'entità **User** elenca tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione.

La raccolta di entità **User** contiene i dati utente. In questi record sono inclusi gli stati utente registrati nel periodo di raccolta dei dati, anche se l'utente è stato rimosso. Nel corso dell'ultimo mese, ad esempio, è possibile che un utente sia stato aggiunto e rimosso da Intune. Pertanto, se anche l'utente non è presente al momento del report, l'utente e lo stato sono comunque presenti nei dati del mese precedente. In questo caso, è possibile creare un report che mostri la durata della presenza storica dell'utente nei dati.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| UserKey |Identificatore univoco dell'utente nel data warehouse, chiave surrogata. |123 |
| UserId |Identificatore univoco dell'utente, simile a UserKey, ma è una chiave naturale. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Indirizzo di posta elettronica dell'utente. |John@constoso.com |
| UPN | UPN dell'utente. | John@constoso.com |
| DisplayName |Nome visualizzato dell'utente. |Luca |
| IntuneLicensed |Specifica se l'utente ha una licenza per Intune. |True/False |
| IsDeleted | Indica se tutte le licenze dell'utente sono scadute e se l'utente è stato quindi rimosso da Intune. Per un singolo record, questo flag non cambia. Per un nuovo stato utente viene creato invece un nuovo record. |True/False |
| StartDateInclusiveUTC |Se IsDeleted = FALSE, data e ora in formato UTC del momento in cui all'utente è stata assegnata una licenza e ne è iniziata la presenza in Intune. Se IsDeleted = TRUE, data e ora in formato UTC del momento in cui sono scadute le licenze dell'utente e quest'ultimo è stato quindi rimosso da Intune. |23/11/2016 12.00.00 |
| EndDateExclusiveUTC |Se IsDeleted = FALSE, data e ora in formato UTC del momento in cui è scaduta la licenza dell'utente e quest'ultimo è stato quindi rimosso da Intune. La licenza è scaduta nel corso del giorno precedente. Se IsDeleted = TRUE, data e ora in formato UTC del momento in cui l'utente ha riacquisito una nuova licenza ed è stato ricreato in Intune.  |23/11/2016 12.00.00 |
| IsCurrent |Indica se il record rappresenta lo stato più recente dell'utente. Per un utente possono esistere più record, ma solo uno ne rappresenta lo stato corrente.  |True/False |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica del record nel data warehouse  |23/11/2016 12.00.00 |

## <a name="next-steps"></a>Passaggi successivi
 - È possibile usare la raccolta di entità **Current User** per limitare i dati agli utenti attualmente attivi. Per altre informazioni, vedere [Informazioni di riferimento per l'entità Current User](reports-ref-current-user.md).
 - Per altre informazioni su come il data warehouse controlla la durata di un utente in Intune, vedere [Rappresentazione della durata degli utenti nel data warehouse di Intune](reports-ref-user-timeline.md).
