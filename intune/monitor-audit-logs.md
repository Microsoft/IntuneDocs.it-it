---
title: Log di controllo per le attività di Microsoft Intune
description: Informazioni su come esaminare i log di controllo che registrano le attività di Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98540af0f0b7d259973d1a7e873c68fc64f488d1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460679"
---
# <a name="audit-logs-for-intune-activities"></a>Log di controllo per le attività di Intune
I log di controllo includono una registrazione delle attività che generano una modifica in Microsoft Intune. Le azioni di creazione, aggiornamento (modifica), eliminazione ed assegnazione, o le attività remote, generano eventi di controllo che è possibile esaminare. È possibile esaminare i log di controllo per la maggior parte dei carichi di lavoro di Intune. Il controllo è abilitato per impostazione predefinita per tutti i clienti e non può essere disabilitato. Gli eventi di controllo sono stati registrati per la prima volta nel rilascio della funzionalità di dicembre 2017, gli eventi precedenti non sono disponibili.

## <a name="who-can-access-the-data"></a>Utenti autorizzati ad accedere ai dati
Gli utenti con le autorizzazioni seguenti possono esaminare i log di controllo:
- Amministratore globale
- Amministratore del servizio Intune
- Amministratori assegnati a un ruolo di Intune con le autorizzazioni **Dati di controllo** - **Lettura**

## <a name="audit-logs-for-intune-workloads"></a>Log di controllo per i carichi di lavoro di Intune
È possibile esaminare i log di controllo nel gruppo Monitoraggio per ogni carico di lavoro di Intune.  
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere il carico di lavoro per cui si vogliono esaminare i log di controllo, ad esempio **Dispositivi**.
4. Nel gruppo **Monitoraggio** per il carico di lavoro scegliere **Log di controllo**.

## <a name="review-audit-events"></a>Esaminare gli eventi di controllo
![Log di controllo](./media/monitor-audit-logs.png "Log di controllo")

Per un log di controllo è disponibile una visualizzazione elenco predefinita che mostra gli elementi seguenti:    

- Data e ora in cui si è verificato l'evento
- Azione avviata da (attore)
- Nome applicazione
- Attività
- Destinazione/i
- Categoria
- Stato

È possibile fare clic su un elemento nella visualizzazione elenco per ottenere tutti i dettagli disponibili.

![Log di controllo](./media/monitor-audit-log-detail.png "Log di controllo")

> [!Note]    
> La sezione **Azione avviata da (attore)** nei dettagli del log di controllo include informazioni sull'utente che ha eseguito l'attività e la posizione da cui è stata eseguita. Ad esempio, se si esegue l'attività in Intune nel portale di Azure, in **Applicazione** è sempre indicato **Microsoft Intune portal extension** e **ID applicazione** usa sempre lo stesso GUID. 
>    
> La sezione **Destinazione/i** può elencare più destinazioni e le proprietà che sono state modificate.  


## <a name="filter-audit-events"></a>Filtrare gli eventi di controllo
Ogni carico di lavoro include una voce di menu che pre-filtra la categoria di eventi di controllo associata a tale riquadro. Un'opzione di filtro separata consente di passare a categorie diverse e visualizzare i dettagli delle azioni di evento all'interno di tale categoria. È possibile eseguire ricerche in base all'UPN, ad esempio l'utente che ha eseguito l'azione. Un filtro di intervallo di date include le opzioni 24 ore, 7 giorni o 30 giorni. Per impostazione predefinita, vengono visualizzati gli ultimi 30 giorni di eventi di controllo.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Usare l'API Graph per recuperare gli eventi di controllo
Per informazioni dettagliate su come usare l'API Graph per recuperare fino a un anno di eventi di controllo, vedere [List auditEvents](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list).
