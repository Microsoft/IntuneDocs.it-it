---
title: Sequenza temporale dell'entità User nel data warehouse
titlesuffix: Microsoft Intune
description: Informazioni sul data warehouse di Intune che rappresenta le entità User in una sequenza temporale.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 222636c271140edb528da3ebfbbf7dbe9e44b727
ms.sourcegitcommit: 445a54dc6826a549d770a9953549ae2191d391c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727540"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>Rappresentazione della durata degli utenti nel data warehouse di Microsoft Intune

È possibile usare il mese degli snapshot di dati archiviati nel data warehouse di Intune per rispondere alle domande sulle tendenze basate sul tempo. È possibile, ad esempio, conoscere il numero di utenti aggiunti nell'arco di un mese o chiedere quanti utenti sono stati rimossi dal sistema nello stesso periodo.

Per fornire queste informazioni, il data warehouse archivia informazioni cronologiche. Il data warehouse può tenere traccia della durata di un'entità. Il warehouse registra infatti il momento in cui viene creata un'entità, quelli in cui viene modificato lo stato dell'entità e il momento in cui l'entità viene eliminata. Con queste informazioni cronologiche acquisite tramite snapshot giornalieri di misure quantitative, è possibile confrontare ogni giorno rispetto al giorno precedente e così via.

Fare riferimento alla durata delle entità, tuttavia, può generare confusione, poiché lo stato delle entità è in continua evoluzione. Se, ad esempio, si controlla uno snapshot il giorno 30, è possibile che nei dati non sia possibile trovare un record utente con uno stato attivo, mentre è possibile che il record dell'entità esistesse come attivo nei giorni 28 e 29 e che, prima del giorno 28, l'utente non esistesse affatto.

Questo scenario può essere più chiaro se si esamina la durata di un'entità.

Si supponga che all'utente **John Smith** venga assegnata una licenza in data 01/06/2017 e che la tabella **User** contenga la voce seguente: 
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | 31/12/9999 | TRUE
 
John Smith rinuncia alla licenza in data 25/07/2017. La tabella **User** contiene le voci seguenti. Eventuali modifiche ai record esistenti sono contrassegnate con `marked`. 

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 26/07/2017 | 31/12/9999 | TRUE 

La prima riga indica che John Smith è esistito in Intune dal giorno 01/06/2017 al giorno 25/07/2017. Il secondo record indica che l'utente è stato eliminato il 25/07/2017 e non è più presente in Intune.

Si supponga ora che a John Smith venga assegnata una nuova licenza il 31/08/2017 e che la tabella User contenga le voci seguenti:
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | 26/07/2017 | FALSE 
| John Smith | TRUE | 26/07/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 31/08/2017 | 31/12/9999 | TRUE 
 
Un utente che voglia visualizzare lo stato corrente di tutti gli utenti può applicare un filtro in cui `IsCurrent = TRUE`. 
 
Un utente che voglia visualizzare solo gli utenti esistenti può applicare un filtro in cui `IsCurrent = TRUE AND IsDeleted = FALSE`.

## <a name="dimension-tables-in-the-entity-lifetime"></a>Tabelle delle dimensioni nella durata di un'entità

Per poter archiviare la cronologia delle modifiche di stato delle entità, Intune non elimina i record, ma li contrassegna come eliminati. Questa operazione viene definita "eliminazione temporanea". Le tabelle delle dimensioni usano varie colonne di metadati per tenere traccia della durata dei record. 

Le colonne di metadati usate più comunemente sono: 

| Nome proprietà metadati  | Interpretazione dei valori |
|--|--|
| IsDeleted | Indica se l'entità è stata eliminata in Intune. |
| StartDateInclusiveUTC  | Data e ora in formato UTC in cui l'entità è stata caricata nel data warehouse di Intune. È possibile che l'entità sia stata creata prima di essere importata nel data warehouse di Intune. |
| DeletedDateUTC  | Data e ora in formato UTC in cui l'entità è stata eliminata in Intune. |  

Qualsiasi colonna di metadati che inizia con il prefisso **Row**, ad esempio **RowLastModifiedDateTimeUTC**, indica il momento in cui un record è stato creato o modificato nel data warehouse di Intune. Il warehouse si trova a valle rispetto ai dati di Intune. Questo valore non ha alcuna relazione con la durata dell'entità in Intune.  
 
Chiunque voglia visualizzare solo le entità di dimensioni attualmente esistenti, quindi, può applicare un filtro in cui **IsDeleted = FALSE**.

## <a name="next-steps"></a>Passaggi successivi

 - Per altre informazioni sull'entità **Current User**, vedere [Informazioni di riferimento per l'entità User corrente](reports-ref-current-user.md).
 - Per altre informazioni sull'entità **User**, vedere [Informazioni di riferimento per l'entità User](reports-ref-user.md).