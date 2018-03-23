---
title: API data warehouse di Intune
titlesuffix: Microsoft Intune
description: È possibile usare l'API data warehouse di Intune per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7291e6f0d6094801383ba7fd606c0238e85ba01f
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2018
---
#  <a name="intune-data-warehouse-api"></a>API data warehouse di Intune

L'API data warehouse di Intune consente di accedere ai dati di Intune in un formato leggibile da computer per l'uso nello strumento di analisi preferito. È possibile usare l'API per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione. L'API usa il protocollo OData, che segue i modelli standard per:

  -   Intestazioni di richiesta e risposta
  -   Codici di stato
  -   Metodi HTTP
  -   Convenzioni degli URL
  -   Tipi di supporti
  -   Formati di payload
  -   Opzioni di query

Il protocollo OData (Open Data Protocol) è uno standard dell'organizzazione OASIS (Organization for the Advancement of Structured Information Standards) che definisce la procedura consigliata per creare e utilizzare le API RESTful. Il data warehouse di Intune usa OData versione 4.0.

Questa sezione di riferimento offre una panoramica sugli endpoint, sui metodi HTTP supportati, sui formati di payload restituiti e sulla documentazione del modello di dati Data warehouse di Intune.

> [!Important]  
> È possibile provare le funzionalità più recenti del data warehouse usando la versione beta. A tale scopo, l'URL deve contenere il parametro di query `api-version=beta`. La versione beta offre funzionalità prima che vengano rese disponibili a livello generale come servizio supportato. Quando Intune aggiunge nuove funzionalità, la versione beta può cambiare comportamento e contratti di dati. Qualsiasi codice personalizzato o strumento di creazione di report dipendente dalla versione beta può subire danni con gli aggiornamenti in corso. <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

## <a name="odata-custom-client"></a>Client personalizzato OData

È possibile accedere al modello di dati data warehouse di Intune tramite endpoint RESTful. Per ottenere l'accesso ai dati, è necessario autorizzare il client con Azure Active Directory (Azure AD) tramite OAuth 2.0. Prima, è necessario configurare un'app Web e un'app client in Azure e quindi concedere le autorizzazioni al client. Dopo aver ottenuto l'autorizzazione, il client locale potrà comunicare con gli endpoint del data warehouse.

Per altre informazioni, vedere [Recuperare dati dall'API data warehouse con un client REST](reports-proc-data-rest.md)

> [!Note]  
> È possibile accedere al [repository del data warehouse Intune di GitHub](https://github.com/Microsoft/Intune-Data-Warehouse) in Github per gli esempi di codice.

## <a name="interacting-with-the-api"></a>Interazione con l'API

L'API richiede l'autorizzazione con Azure AD. Azure AD usa OAuth 2.0. Una volta autorizzata, è possibile ottenere i dati dall'API usando un verbo HTTP GET e contattando le raccolte di entità esposte. Per ulteriori informazioni vedere:

 -  [Autorizzazione](reports-api-url.md)
 -  [Struttura URL API](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Modello di dati del data warehouse Intune

OData definisce un modello di dati astratto e un protocollo che consente a qualsiasi client di accedere alle informazioni esposte da qualsiasi origine dati. L'argomento della documentazione del modello di dati contiene una spiegazione degli spazi dei nomi, delle entità e degli oggetti restituiti nel modello di dati del data warehouse di Intune. Per altre informazioni, vedere [Modello di dati del data warehouse](reports-ref-data-model.md).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'uso di Azure AD, vedere [Scenari di autenticazione per Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

Le risorse OData sono disponibili in [odata.org](http://www.odata.org).
  
Rivedere lo standard OData versione 4.0 in [OData Version 4.0] (http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  
