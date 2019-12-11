---
title: Endpoint dell'API data warehouse di Intune
titleSuffix: Microsoft Intune
description: Questo argomento di riferimento descrive la struttura dell'URL dell'API data warehouse di Intune. Sono riportati esempi di filtro.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 170ed2fbf300299796401b10a906d875b6f50bf5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490454"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Endpoint dell'API data warehouse di Intune

È possibile usare l'API data warehouse di Intune con un account con credenziali di Azure AD e controlli di accesso basati sui ruoli specifici. Sarà quindi possibile autorizzare il client REST con Azure AD usando OAuth 2.0. E, infine, si formerà un URL significativo per chiamare una risorsa del data warehouse.

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorizzazione

In Azure Active Directory (Azure AD) si utilizza OAuth 2.0 per consentire all'utente di autorizzare l'accesso ad applicazioni Web e API Web nel proprio tenant di Azure AD. Questa guida è indipendente dal linguaggio e descrive come inviare e ricevere messaggi HTTP senza usare alcuna libreria open source. Il flusso del codice di autorizzazione OAuth 2.0 è descritto nella [sezione 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) della specifica OAuth 2.0.

Per altre informazioni, vedere [Autorizzare l'accesso alle applicazioni Web tramite OAuth 2.0 e Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Struttura URL API

Gli endpoint dell'API data warehouse leggono le entità per ogni set. L'API supporta un verbo HTTP **GET** e un subset di opzioni di query.

L'URL per Intune usa il formato seguente:  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> Nell'URL precedente sostituire `{location}`, `{entity-collection}` e `{api-version}` in base ai dettagli specificati nella tabella seguente.

L'URL contiene gli elementi seguenti:

| Elemento | Esempio | Descrizione |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | L'URL di base è reperibile visualizzando il pannello dell'API data warehouse nel portale di Azure. |
| entity-collection | devicePropertyHistories | Il nome della raccolta di entità OData. Per altre informazioni sulle raccolte e sulle entità nel modello di dati, vedere [Modello di dati](reports-ref-data-model.md). |
| api-version | beta | Si intende la versione dell'API a cui accedere. Per altre informazioni, vedere [Versione](reports-api-url.md#api-version-information). |
| maxhistorydays | 7 | (Facoltativo) Numero massimo di giorni della cronologia di elaborazione da recuperare. Questo parametro può essere aggiunto a qualsiasi raccolta, ma è attivo solo per le raccolte che includono `dateKey` nella proprietà chiave. Per altre informazioni, vedere [Filtri di intervallo DateKey](reports-api-url.md#datekey-range-filters). |

## <a name="api-version-information"></a>Informazioni sulla versione dell'API

È ora possibile usare la versione v1.0 del data warehouse di Intune impostando il parametro di query `api-version=v1.0`. Gli aggiornamenti alle raccolte nel data warehouse sono additivi per progettazione e non causano interruzioni per gli scenari esistenti.

È possibile provare le funzionalità più recenti del data warehouse usando la versione beta. A tale scopo, l'URL deve contenere il parametro di query  `api-version=beta`. La versione beta offre funzionalità prima che vengano rese disponibili a livello generale come servizio supportato. Quando Intune aggiunge nuove funzionalità, la versione beta può cambiare comportamento e contratti di dati. Qualsiasi codice personalizzato o strumento di creazione di report dipendente dalla versione beta può subire danni con gli aggiornamenti in corso.

## <a name="odata-query-options"></a>Opzioni di query OData

La versione corrente supporta i seguenti parametri di query OData: `$filter`, `$select`, `$skip,` e `$top`. In `$filter`, solo `DateKey` o `RowLastModifiedDateTimeUTC` possono essere supportati quando le colonne sono applicabili, mentre altre proprietà comporterebbero l'attivazione di una richiesta non valida.

## <a name="datekey-range-filters"></a>Filtri di intervallo DateKey

I filtri di intervallo `DateKey` possono essere usati per limitare la quantità di dati scaricabili per alcune raccolte che hanno come proprietà chiave `dateKey`. Il filtro `DateKey` può essere usato per ottimizzare le prestazioni del servizio fornendo il parametro di query `$filter` seguente:

1. `DateKey` da solo in `$filter`, per il supporto degli operatori `lt/le/eq/ge/gt` e il join con l'operatore logico `and`, dove possono essere mappati a una data di inizio e/o una data di fine.
2. `maxhistorydays` viene specificato come opzione di query personalizzata.<br>

## <a name="filter-examples"></a>Esempi di filtro

> [!NOTE]
> Gli esempi di filtro presuppongono che la data odierna sia il 21 febbraio 2019.

|                             Filtra                             |           Ottimizzazione delle prestazioni           |                                          Descrizione                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Completo                                      |    Restituisce dati con `DateKey` tra 20180214 e 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Completo                                      |    Restituisce dati con `DateKey` uguale a 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Completo                                      |    Restituisce dati con `DateKey` tra 20180214 e 20180220.                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Completo                                      |    Restituisce dati con `DateKey` uguale a 20180214. `maxhistorydays` viene ignorato.                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    Completo                                       |    Restituisce dati con `RowLastModifiedDateTimeUTC` maggiore o uguale a `2018-02-21T23:18:51.3277273Z`                             |
