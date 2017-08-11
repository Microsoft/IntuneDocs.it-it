---
title: Usare il data warehouse di Intune | Microsoft Docs
description: Usare il data warehouse di Intune per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione.
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: db6661dd92b890d711f655a60eb883b417a30d8a
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2017
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

> [!Important]  
> È possibile provare le funzionalità più recenti del data warehouse usando la versione beta. A tale scopo, l'URL deve contenere il parametro di query `api-version=beta`. La versione beta offre funzionalità prima che vengano rese disponibili a livello generale come servizio supportato. Quando Intune aggiunge nuove funzionalità, la versione beta può cambiare comportamento e contratti di dati. Qualsiasi codice personalizzato o strumento di creazione di report dipendente dalla versione beta può subire danni con gli aggiornamenti in corso. <!-- If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

**Passaggi successivi**

- Ottenere un collegamento e usare Power BI per ottenere informazioni dettagliate. Per istruzioni, vedere [Connettersi al data warehouse con Power BI](reports-proc-get-a-link-powerbi.md).
- Per ottenere altre informazioni sull'API del data warehouse di Intune, sul modello di dati e sulle relazioni tra entità<!-- , and an example of creating a custom client to retrieve data,--> vedere [API data warehouse di Intune](reports-nav-intune-date-warehouse.md).