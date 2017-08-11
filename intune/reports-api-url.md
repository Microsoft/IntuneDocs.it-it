---
title: Endpoint dell'API data warehouse di Intune | Microsoft Docs
description: Argomento di riferimento che descrive la struttura URL dell'API.
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7723bb42eedcd97142f039ca52b60911fa91838b
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2017
---
# <a name="intune-data-warehouse-api-endpoint"></a>Endpoint dell'API data warehouse di Intune

È possibile usare l'API data warehouse di Intune con un account con credenziali di Azure AD e controlli di accesso basati sui ruoli specifici. Sarà quindi possibile autorizzare il client REST con Azure AD usando OAuth 2.0. E, infine, si formerà un URL significativo per chiamare una risorsa del data warehouse.

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisiti delle credenziali di Azure AD e Intune

L'autenticazione e l'autorizzazione si basano sulle credenziali di Azure AD e sul controllo degli accessi in base al ruolo di Intune (RBAC). Tutti gli amministratori globali e gli amministratori del servizio Intune per il tenant hanno accesso all'API per impostazione predefinita. Usare i ruoli di Intune per fornire accesso per più utenti, offrendo loro l'accesso alla **risorsa di creazione report**.

I requisiti per l'accesso all'API sono:

  -  Licenza di Intune assegnata all'utente
  -  L'utente deve essere uno dei seguenti:
      -  Amministratore globale di Azure AD
      -  Amministratore del servizio Intune
      -  Utente con accesso basato sui ruoli alla risorsa **Report**

## <a name="authorization"></a>Autorizzazione

In Azure Active Directory (Azure AD) si utilizza OAuth 2.0 per consentire all'utente di autorizzare l'accesso ad applicazioni Web e API Web nel proprio tenant di Azure AD. Questa guida è indipendente dal linguaggio e descrive come inviare e ricevere messaggi HTTP senza usare alcuna libreria open source. Il flusso del codice di autorizzazione OAuth 2.0 è descritto nella [sezione 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) della specifica OAuth 2.0.

Per altre informazioni, vedere [Autorizzare l'accesso alle applicazioni Web tramite OAuth 2.0 e Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Struttura URL API

Gli endpoint dell'API data warehouse leggono le entità per ogni set. L'API supporta un verbo HTTP **GET** e un subset di opzioni di query.

L'URL per Intune usa il formato seguente:  
https://fef.{***location***}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{***entity-collection***}?api-version={***api-version***}

L'URL contiene gli elementi seguenti:

| Elemento | Esempio | Descrizione |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | L'URL di base è reperibile visualizzando il pannello dell'API data warehouse nel portale di Azure. |
| entity-collection | dates | Il nome della raccolta di entità OData. Per altre informazioni sulle raccolte e sulle entità nel modello di dati, vedere [Modello di dati](reports-ref-data-model.md). |
| api-version | beta | Si intende la versione dell'API a cui accedere. Per altre informazioni, vedere [Versione](#API-version-information). |


## <a name="api-version-information"></a>Informazioni sulla versione dell'API

La versione corrente delle API è: `beta`. 

## <a name="odata-query-options"></a>Opzioni di query OData

La versione corrente supporta i parametri di query OData seguenti: `$skip, $top, $filter, $orderby`.