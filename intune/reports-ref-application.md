---
title: Application | Microsoft Docs
description: "Argomento di riferimento per la categoria Application delle raccolte di entità nell'API data warehouse di Intune."
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cd684feec1df6b20f9349052496a21895527710b
ms.sourcegitcommit: 0d9bfd92bf5958261ed83b1f150bf207b7ba7e56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2017
---
# <a name="reference-for-application-entities"></a>Informazioni di riferimento per le entità della categoria Application

La categoria **Application** contiene le entità per i dispositivi mobili che tengono traccia delle informazioni come:

  -  Versioni di un'app
  -  Origine dell'installazione di un'app
  -  Tipo di sviluppatori che hanno creato un'app
  -  Tipi di software gestiti per un'app, ad esempio **sidecar** o **desktop**
  -  Stato Volume Purchasing Program (VPP) di un'app

## <a name="apprevision"></a>AppRevision

L'entità **AppRevision** elenca tutte le versioni di un'app.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| AppKey |Identificatore univoco dell'app |123 |
| ApplicationId |Identificatore univoco dell'app, simile a AppKey, ma è una chiave naturale. |b66bc706-ffff-7437-0340-032819502773 |
| Revisione |La versione indicata dall'amministratore durante il caricamento del file binario |2 |
| Titolo |Titolo dell'app |Excel |
| Pubblicazione |Autore della pubblicazione dell'app |Microsoft |
| UploadState |Stato di upload dell'app |1 |
| AppTypeKey |Riferimento ad AppType descritto nella sezione seguente. | |
| VppProgramTypeKey |Riferimento a VppProgramType descritto di seguito | |
| CreationTime |Ora di creazione della revisione |23/11/2016 12.00.00 |
| ModifiedTime |Ora dell'ultima modifica apportata a qualsiasi elemento relativo a questa revisione |23/11/2016 12.00.00 |
| Dimensioni |Dimensioni del file binario | |
| StartDateInclusiveUTC |Data e ora in formato UTC in cui la revisione dell'app è stata creata nel data warehouse |23/11/2016 12.00.00 |
| EndDateExclusiveUTC |Data e ora in formato UTC in cui la revisione dell'app è divenuta obsoleta |23/11/2016 12.00.00 |
| IsCurrent |Indica se la versione dell'app è corrente o no nel data warehouse |True/False |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica della versione dell'app nel data warehouse |23/11/2016 12.00.00 |

## <a name="apptypes"></a>AppTypes

L'entità **AppTypes** elenca l'origine dell'installazione di un'app.

| Proprietà  | Descrizione |
|---------|------------|
| AppTypeID |ID per il tipo |
| AppTypeKey |Chiave surrogata per la chiave |
| AppTypeName |Tipo di App |

## <a name="example"></a>Esempio

| AppTypeID  | Nome | Descrizione |
|---------|------------|--------|
| 0 |App di Android Store |Un'app di Android Store |
| 1 |App di Android LOB |Un'app line-of-business Android |
| 2 |App di Android Store gestita (MAM) |Un'app di Android Store abilitata per la gestione |
| 3 |App di iOS Store |Un'app di iOS Store |
| 4 |App LOB iOS |Un'app line-of-business iOS |
| 5 |App dello Store iOS gestita (MAM?) |Un'app di iOS Store abilitata per la gestione |
| 6 |O365 Pro Plus Suite |Office 365 Pro Plus Suite per Windows 10 |
| 7 |App Web |Un'app web |
| 8 |App di Windows Phone 8.1 Store |Un'app di Windows Phone 8.1 Store |
| 9 |App di Windows Store |Un'app di Windows Store |
| 10 |App line-of-business di Windows |Un'app line-of-business appx Windows |
| 11 |Windows Mobile MSI |Un'app line-of-business MSI |
| 12 |App line-of-business di Windows Phone |Un'app line-of-business di Windows Phone |


## <a name="vppprogramtypes"></a>VppProgramTypes

L'entità **VppProgramTypes** elenca i tipi di programma VPP possibili per un'app.

| Proprietà  | Descrizione |
|---------|------------|
| VppProgramTypeID |ID per il tipo |
| VppProgramTypeKey |Chiave surrogata per la chiave |
| VppProgramTypeName |Tipo di programma VPP |

## <a name="example"></a>Esempio

| VppProgramID  | Nome | Descrizione |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Programma VPP di Microsoft |
| 00000000-0000-0000-0000-000000000000 |Non ancora disponibile |Valore predefinito, nessun VPP |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Programma VPP di Apple |



## <a name="applicationinventory"></a>ApplicationInventory

L'entità **ApplicationInventory** elenca le applicazioni trovate nel dispositivo al momento della raccolta dei dati di inventario.

| Proprietà  | Descrizione |
|---------|------------|
| DeviceKey |Si tratta di un riferimento alla tabella Device che contiene l'ID dispositivo Intune |
| DateKey |Riferimento alla tabella di data che indica il giorno dell'inventario |
| ApplicationName |Nome dell'applicazione |
| ApplicationVersion |Versione dell'applicazione |
| BundleSize |Dimensione dell'app in byte |
