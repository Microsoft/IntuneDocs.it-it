---
title: API data warehouse di Intune | Microsoft Docs
description: "È possibile usare l'API per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione."
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 52b498beb024b86282c93be7aa5a248800db6609
ms.sourcegitcommit: 294de4d4058de2c625abb8143e90880d27da9284
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2017
---
#  <a name="intune-data-warehouse-api"></a>API data warehouse di Intune

L'API data warehouse di Intune consente di accedere ai dati di Intune in un formato leggibile da computer per l'uso nello strumento analitico preferito. È possibile usare l'API per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione. L'API usa il protocollo OData, che segue i modelli standard per:

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

È possibile accedere al modello di dati data warehouse di Intune tramite endpoint RESTful. Per ottenere l'accesso ai dati, è necessario autorizzare il client con Microsoft Azure Active Directory (Azure AD) tramite OAuth 2.0. Prima, è necessario configurare un'app Web e un'app client in Azure e quindi concedere le autorizzazioni al client. Il client locale otterrà l'autorizzazione e quindi potrà comunicare con gli endpoint data warehouse.

Per altre informazioni, vedere [Recuperare dati dall'API data warehouse con un client REST](reports-proc-data-rest.md)

## <a name="interacting-with-the-api"></a>Interazione con l'API

L'API richiede l'autorizzazione con Azure AD. Azure AD usa OAuth 2.0. Una volta autorizzata, è possibile ottenere i dati dall'API usando un verbo HTTP GET e contattando le raccolte di entità esposte. Per ulteriori informazioni vedere:

 -  [Autorizzazione](reports-api-url.md)
 -  [Struttura URL API](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Modello di dati del data warehouse Intune

OData definisce un modello di dati astratto e un protocollo che consente a qualsiasi client di accedere alle informazioni esposte da qualsiasi origine dati. L'argomento della documentazione del modello di dati contiene una spiegazione degli spazi dei nomi, delle entità e degli oggetti restituiti nel modello di dati del data warehouse di Intune. Per altre informazioni, vedere [Modello di dati del data warehouse](reports-ref-data-model.md).

## <a name="next-steps"></a>Passaggi successivi

[Scenari di autenticazione per Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData versione 4.0](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  