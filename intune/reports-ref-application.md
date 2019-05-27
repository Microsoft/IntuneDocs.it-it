---
title: Informazioni di riferimento per le entità della categoria Application
titleSuffix: Microsoft Intune
description: Argomento di riferimento per la categoria Application delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: deea42bf9ef35d173761fddb16aa43eaa8876269
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041070"
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
| AppKey |Identificatore univoco dell'app. |123 |
| ApplicationId |Identificatore univoco dell'app, simile a AppKey, ma è una chiave naturale. |b66bc706-ffff-7437-0340-032819502773 |
| Revisione |La versione indicata dall'amministratore durante il caricamento del file binario. |2 |
| Titolo |Titolo dell'app. |Excel |
| Pubblicazione |Autore della pubblicazione dell'app. |Microsoft |
| UploadState |Stato di caricamento dell'app. |1 |
| AppTypeKey |Riferimento ad AppType descritto nella sezione seguente. | |
| VppProgramTypeKey |Riferimento a VppProgramType descritto di seguito. | |
| CreationTime |Ora di creazione della revisione. |23/11/2016 12.00.00 |
| ModifiedTime |Ora dell'ultima modifica apportata a qualsiasi elemento relativo a questa revisione. |23/11/2016 12.00.00 |
| Dimensioni |Dimensioni del file binario. | |
| StartDateInclusiveUTC |Data e ora in formato UTC della creazione della revisione dell'app nel data warehouse. |23/11/2016 12.00.00 |
| EndDateExclusiveUTC |Data e ora in formato UTC in cui la revisione dell'app è diventata obsoleta. |23/11/2016 12.00.00 |
| IsCurrent |Indica se la versione dell'app è corrente nel data warehouse. |True/False |
| RowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica della versione dell'app nel data warehouse. |23/11/2016 12.00.00 |

## <a name="apptypes"></a>AppTypes

L'entità **AppTypes** elenca l'origine dell'installazione di un'app.

| Proprietà  | Descrizione |
|---------|------------|
| AppTypeID |ID per il tipo |
| AppTypeKey |Chiave surrogata per la chiave |
| AppTypeName |Tipo di app |

### <a name="example"></a>Esempio

| AppTypeID  | Name | Descrizione |
|---------|------------|--------|
| 0 |App di Android Store | Un'app di Android Store. |
| 1 |App di Android LOB | Un'app line-of-business Android. |
| 2 |App di Android Store gestita (MAM) | Un'app di Android Store abilitata per la gestione. |
| 3 |App di iOS Store | Un'app dello Store iOS. |
| 4 |App LOB iOS | Un'app line-of-business iOS. |
| 5 |App dello Store iOS gestita (MAM?) | Un'app iOSstore abilitata per la gestione. |
| 6 |O365 Pro Plus Suite | Office 365 Pro Plus Suite per Windows 10. |
| 7 |App Web | Un'app Web. |
| 8 |App di Windows Phone 8.1 Store | Un'app dello Store per Windows Phone 8.1. |
| 9 |App di Windows Store | Un'app di Windows Store. |
| 10 |App line-of-business di Windows | Un'app line-of-business AppX per Windows. |
| 11 |Windows Mobile MSI | Un'app line-of-business MSI. |
| 12 |App line-of-business di Windows Phone | Un'app line-of-business per Windows Phone. |


## <a name="vppprogramtypes"></a>VppProgramTypes

L'entità **VppProgramTypes** elenca i tipi di programma VPP possibili per un'app.

| Proprietà  | Descrizione |
|---------|------------|
| VppProgramTypeID | ID per il tipo. |
| VppProgramTypeKey | Chiave surrogata per la chiave. |
| VppProgramTypeName | Tipo di programma VPP. |

### <a name="example"></a>Esempio

| VppProgramID  | Name | Descrizione |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Programma VPP Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Non ancora disponibile | Valore predefinito, nessun VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Programma VPP Apple. |



## <a name="applicationinventory"></a>ApplicationInventory

L'entità **ApplicationInventory** elenca le applicazioni trovate nel dispositivo al momento della raccolta dei dati di inventario.

| Proprietà  | Descrizione |
|---------|------------|
| DeviceKey | Si tratta di un riferimento alla tabella Device che contiene l'ID dispositivo Intune. |
| DateKey | Riferimento alla tabella di data che indica il giorno dell'inventario. |
| ApplicationName | Il nome dell'applicazione. |
| ApplicationVersion | Versione dell'applicazione. |
| BundleSize | Dimensione dell'app in byte. |

## <a name="mobileappinstallstate"></a>MobileAppInstallState

L'entità **MobileAppInstallState** rappresenta lo stato di installazione per un'applicazione per dispositivi mobili dopo l'assegnazione a un gruppo che contiene dispositivi, utenti o entrambi.

| Proprietà | Descrizione |
|---|---|
| AppInstallStateKey | ID univoco dello stato di installazione dell'app per l'account. |
| AppInstallState | Valore di enumerazione dello stato di installazione dell'app. |
| AppInstallStateName | Nome dello stato di installazione dell'app. |



