---
title: Informazioni di riferimento per le entità della categoria Application
titleSuffix: Microsoft Intune
description: Argomento di riferimento per la categoria Application delle raccolte di entità nell'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
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
ms.openlocfilehash: a5436de6b972e5cbe8b2b17d42f0974cb38df47e
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313802"
---
# <a name="reference-for-application-entities"></a>Informazioni di riferimento per le entità della categoria Application

La categoria **Application** contiene le entità per i dispositivi mobili che tengono traccia delle informazioni come:

- Versioni di un'app
- Origine dell'installazione di un'app
- Tipo di sviluppatori che hanno creato un'app
- Tipi di software gestiti per un'app, ad esempio **sidecar** o **desktop**
- Stato Volume Purchasing Program (VPP) di un'app

## <a name="apprevisions"></a>appRevisions

L'entità **appRevision** elenca tutte le versioni di un'app.

| Proprietà  | Descrizione | Esempio |
|---------|------------|--------|
| appKey |Identificatore univoco dell'app. |123 |
| applicationId |Identificatore univoco dell'app, simile a AppKey, ma è una chiave naturale. |b66bc706-ffff-7437-0340-032819502773 |
| revision |La versione indicata dall'amministratore durante il caricamento del file binario. |2 |
| title |Titolo dell'app. |Excel |
| publisher |Autore della pubblicazione dell'app. |Microsoft |
| uploadState |Stato di caricamento dell'app. |1 |
| appTypeKey |Riferimento ad AppType descritto nella sezione seguente. | |
| vppProgramTypeKey |Riferimento a VppProgramType descritto di seguito. | |
| creationTime |Ora di creazione della revisione. |23/11/2016 12.00.00 |
| modifiedTime |Ora dell'ultima modifica apportata a qualsiasi elemento relativo a questa revisione. |23/11/2016 12.00.00 |
| dimensioni |Dimensioni del file binario. | |
| startDateInclusiveUTC |Data e ora in formato UTC della creazione della revisione dell'app nel data warehouse. |23/11/2016 12.00.00 |
| endDateExclusiveUTC |Data e ora in formato UTC in cui la revisione dell'app è diventata obsoleta. |23/11/2016 12.00.00 |
| isCurrent |Indica se la versione dell'app è corrente nel data warehouse. |True/False |
| rowLastModifiedDateTimeUTC |Data e ora in formato UTC dell'ultima modifica della versione dell'app nel data warehouse. |23/11/2016 12.00.00 |

## <a name="apptypes"></a>appTypes

L'entità **appType** elenca l'origine dell'installazione di un'app.

| Proprietà  | Descrizione |
|---------|------------|
| appTypeID |ID per il tipo |
| appTypeKey |Chiave surrogata per la chiave |
| appTypeName |Tipo di app |

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


## <a name="vppprogramtypes"></a>vppProgramTypes

L'entità **vppProgramType** elenca i tipi di programma VPP possibili per un'app.

| Proprietà  | Descrizione |
|---------|------------|
| vppProgramTypeID | ID per il tipo. |
| vppProgramTypeKey | Chiave surrogata per la chiave. |
| vppProgramTypeName | Tipo di programma VPP. |

### <a name="example"></a>Esempio

| VppProgramID  | Name | Descrizione |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Programma VPP Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Non ancora disponibile | Valore predefinito, nessun VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Programma VPP Apple. |



## <a name="applicationinventories"></a>applicationInventories

L'entità **applicationInventory** elenca le applicazioni trovate nel dispositivo al momento della raccolta dei dati di inventario.

| Proprietà  | Descrizione |
|---------|------------|
| deviceKey | Si tratta di un riferimento alla tabella Device che contiene l'ID dispositivo Intune. |
| dateKey | Riferimento alla tabella di data che indica il giorno dell'inventario. |
| applicationName | Il nome dell'applicazione. |
| applicationVersion | Versione dell'applicazione. |
| bundleSize | Dimensione dell'app in byte. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

L'entità **mobileAppInstallState** rappresenta lo stato di installazione per un'applicazione per dispositivi mobili dopo l'assegnazione a un gruppo che contiene dispositivi, utenti o entrambi.

| Proprietà | Descrizione |
|---|---|
| appInstallStateKey | ID univoco dello stato di installazione dell'app per l'account. |
| appInstallState | Valore di enumerazione dello stato di installazione dell'app. |
| appInstallStateName | Nome dello stato di installazione dell'app. |



