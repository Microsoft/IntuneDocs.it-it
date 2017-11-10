---
title: Usare il data warehouse di Intune | Microsoft Docs
description: Usare il data warehouse di Intune per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione.
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d485f0d53ac57a2f159ebd56b6b3823a8a49d5ad
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2017
---
# <a name="use-the-intune-data-warehouse"></a>Usare il data warehouse di Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare il data warehouse di Intune per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione. Ad esempio, alcuni dei report includono:
-   Tendenza degli utenti che si registrano a Intune per poter ottimizzare gli acquisti di licenze
-   Suddivisione di versioni del sistema operativo e app per poter esaminare lo stato dei dispositivi mobili
-   Tendenze di registrazione e conformità dispositivo per poter distribuire in modo uniforme gli aggiornamenti dei criteri

Il data warehouse permette di accedere ad altre informazioni sull'ambiente per dispositivi mobili rispetto al portale di Azure. Con il data warehouse di Intune è possibile accedere a:

  -  Dati cronologici di Intune
  -  Dati aggiornati con cadenza giornaliera
  -  Un modello di dati che usa lo standard OData

> [!Note]
> Se con System Center Configuration Manager e Microsoft Intune si usa una gestione di dispositivi mobili (MDM) ibrida, recuperare i dati da SCCM. Il data warehouse di Intune contiene solo i dati di Intune. Per i report personalizzati, è possibile usare un dashboard di Power BI per SCCM. Per altre informazioni, vedere "[Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)" (Annuncio del modello di soluzione di Power BI per System Center Configuration Manager) e "[Create a Power BI report and dashboard](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/create-powerbi-report-dashboard)" (Creare un report e un dashboard Power BI).


> [!Important]  
> È possibile provare le funzionalità più recenti del data warehouse usando la versione beta. A tale scopo, l'URL deve contenere il parametro di query `api-version=beta`. La versione beta offre funzionalità prima che vengano rese disponibili a livello generale come servizio supportato. Quando Intune aggiunge nuove funzionalità, la versione beta può cambiare comportamento e contratti di dati. Qualsiasi codice personalizzato o strumento di creazione di report dipendente dalla versione beta può subire danni con gli aggiornamenti in corso.

**Passaggi successivi**

- Ottenere un collegamento e usare Power BI per ottenere informazioni dettagliate. Per istruzioni, vedere [Connettersi al data warehouse con Power BI](reports-proc-get-a-link-powerbi.md).
- Con il collegamento, creare un report personalizzato con Power BI. Per istruzioni, vedere [Creare un report dal feed OData con Power BI](reports-proc-create-with-odata.md).
- Per ottenere altre informazioni sull'API del data warehouse di Intune, sul modello di dati e sulle relazioni tra entità<!-- , and an example of creating a custom client to retrieve data,--> vedere [API data warehouse di Intune](reports-nav-intune-data-warehouse.md).