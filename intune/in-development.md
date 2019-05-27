---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca66a2fa331fe4dcc30c32d369db32a57ba9999c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047304"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>In fase di sviluppo per Microsoft Intune - Maggio 2019

Per supportare gli utenti nella preparazione e pianificazione, questa pagina illustra gli aggiornamenti e le funzionalità dell'interfaccia utente di Intune che sono in fase di sviluppo ma non ancora rilasciati. Inoltre:

- Se sono previste azioni prima di una modifica, verrà pubblicato un post complementare nel Centro messaggi di Office.
- Quando una funzionalità viene avviata nell'ambiente di produzione, sia in versione anteprima sia disponibile a livello generale, la descrizione della funzionalità verrà spostata da questa pagina alla [pagina delle novità](whats-new.md).
- Questa pagina e la [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere la [Roadmap di Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per informazioni sulle sequenze temporali e i risultati finali strategici.

> [!Note]
> Questi elementi riflettono le aspettative correnti di Microsoft sulle funzionalità di Intune introdotte in una versione futura. Le date e le singole funzionalità possono cambiare. Questa pagina non include una descrizione della funzione per tutti gli elementi in fase di sviluppo.

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Supporto di base per la ricerca con parole chiave  <!-- 3082036         -->
Durante la creazione o la modifica di un profilo di base di sicurezza sarà presto possibile usare la *ricerca* per filtrare le impostazioni visualizzate nella console.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Reimpostare e cancellare i dispositivi in blocco usando l'API Graph <!-- 3295288 -->
Sarà possibile reimpostare e cancellare un massimo di 100 dispositivi in blocco tramite l'API Graph.

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gli utenti dei dispositivi potranno visualizzare tutte le app gestite che hanno installato o tentato di installare <!-- 2352913 -->
Nel Portale aziendale per Windows saranno ancora elencate tutte le app gestite&ndash; sia obbligatorie che disponibili&ndash; installate nel dispositivo dell'utente. Gli utenti potranno visualizzare le installazioni di app tentate e in sospeso e i rispettivi stati correnti. Se l'organizzazione non rende le app obbligatorie o disponibili, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Gli utenti potranno anche ordinare o filtrare le app in base allo stato di installazione.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Usare le "regole di applicabilità" durante la creazione dei profili di configurazione dispositivo Windows 10 <!-- 2549910 -->
Creare profili di configurazione dispositivo Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** per la piattaforma). Sarà possibile creare una **regola di applicabilità** in modo che il profilo si applichi solo a un'edizione o versione specifica. Creare ad esempio un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applichi solo ai dispositivi che eseguono Windows 10 Enterprise.

Si applica a: 
- Windows 10 e versioni successive



## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


