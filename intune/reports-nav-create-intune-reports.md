---
title: Usare il data warehouse di Intune
titlesuffix: Microsoft Intune
description: Usare il data warehouse di Intune per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99c2824e8f229ad6f4d68516bc892ad3818ac5c1
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843018"
---
# <a name="use-the-microsoft-intune-data-warehouse"></a>Usare il data warehouse di Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare il data warehouse di Intune per compilare report che consentono di comprendere l'ambiente per dispositivi mobili dell'organizzazione. Ad esempio, alcuni dei report includono:
-   Tendenza degli utenti che si registrano a Intune per poter ottimizzare gli acquisti di licenze
-   Suddivisione di versioni del sistema operativo e app per poter esaminare lo stato dei dispositivi mobili
-   Tendenze di registrazione e conformità dispositivo per poter distribuire in modo uniforme gli aggiornamenti dei criteri

## <a name="data-warehouse-benefits"></a>Vantaggi del data warehouse

Il data warehouse permette di accedere ad altre informazioni sull'ambiente per dispositivi mobili rispetto al portale di Azure. Con il data warehouse di Intune è possibile accedere a:

  -  Dati cronologici di Intune
  -  Dati aggiornati con cadenza giornaliera
  -  Un modello di dati che usa lo standard OData

> [!Note]
> Se con System Center Configuration Manager e Microsoft Intune si usa una gestione di dispositivi mobili (MDM) ibrida, recuperare i dati da SCCM. Il data warehouse di Intune contiene solo i dati di Intune. Per i report personalizzati, è possibile usare un dashboard di Power BI per SCCM. Per altre informazioni, vedere "[Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)" (Annuncio del modello di soluzione di Power BI per System Center Configuration Manager) e "[Contenuto di Power BI per Dynamics 365](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page)".

> [!Important]  
> È ora possibile usare la versione v1.0 del data warehouse di Intune impostando il parametro di query `api-version=v1.0`. Gli aggiornamenti alle raccolte nel data warehouse sono additivi per progettazione e non causano interruzioni per gli scenari esistenti.<br><br>
> È possibile provare le funzionalità più recenti del data warehouse usando la versione beta. A tale scopo, l'URL deve contenere il parametro di query  `api-version=beta`. La versione beta offre funzionalità prima che vengano rese disponibili a livello generale come servizio supportato. Quando Intune aggiunge nuove funzionalità, la versione beta può cambiare comportamento e contratti di dati. Qualsiasi codice personalizzato o strumento di creazione di report dipendente dalla versione beta può subire danni con gli aggiornamenti in corso.

## <a name="next-steps"></a>Passaggi successivi

- Ottenere un collegamento e usare Power BI per ottenere informazioni dettagliate. Per istruzioni, vedere [Connettersi al data warehouse con Power BI](reports-proc-get-a-link-powerbi.md).
- Con il collegamento, creare un report personalizzato con Power BI. Per istruzioni, vedere [Creare un report dal feed OData con Power BI](reports-proc-create-with-odata.md).
- Per ottenere altre informazioni sull'API del data warehouse di Intune, sul modello di dati e sulle relazioni tra entità<!-- , and an example of creating a custom client to retrieve data,--> vedere [API data warehouse di Intune](reports-nav-intune-data-warehouse.md).
