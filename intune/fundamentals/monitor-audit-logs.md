---
title: Controllare modifiche ed eventi in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni su come esaminare i log di controllo che registrano le attività di Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d999603abc539fda4d152d15dd1ab965c465f39e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736299"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Usare i log di controllo per tenere traccia degli eventi e monitorarli in Microsoft Intune

I log di controllo includono una registrazione delle attività che generano una modifica in Microsoft Intune. Le operazioni di creazione, aggiornamento (modifica), eliminazione e assegnazione, così come le azioni remote creano tutte eventi di controllo che gli amministratori possono esaminare per la maggior parte dei carichi di lavoro di Intune. Per impostazione predefinita, il controllo è abilitato per tutti i clienti. Non può essere disabilitato.

> [!NOTE]
> La registrazione degli eventi di controllo è iniziata con la versione di dicembre 2017 (rilascio di nuove funzionalità). Gli eventi precedenti non sono disponibili.

## <a name="who-can-access-the-data"></a>Utenti autorizzati ad accedere ai dati

Gli utenti con le autorizzazioni seguenti possono esaminare i log di controllo:

- Amministratore globale
- Amministratore del servizio Intune
- Amministratori assegnati a un ruolo di Intune con le autorizzazioni **Dati di controllo** - **Lettura**

## <a name="audit-logs-for-intune-workloads"></a>Log di controllo per i carichi di lavoro di Intune

È possibile esaminare i log di controllo nel gruppo di monitoraggio per ogni carico di lavoro di Intune:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Scegliere il carico di lavoro per cui si vogliono esaminare i log di controllo. Selezionare, ad esempio, **Dispositivi**.
3. In **Monitoraggio** scegliere **Log di controllo**.

## <a name="route-logs-to-azure-monitor"></a>Indirizzare i log a Monitoraggio di Azure

I log di controllo e i log operativi possono essere anche indirizzati a Monitoraggio di Azure. In **Log di controllo** selezionare **Esporta impostazioni dati**:

![Esportare i dati di log in Monitoraggio di Azure selezionando Esporta impostazioni dati in Intune](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

Per altre informazioni su questa funzionalità, vedere [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Esaminare gli eventi di controllo

![Scegliere i log di controllo in Intune per visualizzare le azioni e le date in cui si sono verificati gli eventi](./media/monitor-audit-logs/monitor-audit-logs.png "Log di controllo")

Per un log di controllo è disponibile una visualizzazione elenco predefinita che mostra gli elementi seguenti:

- Data e ora in cui si è verificato l'evento
- Azione avviata da (attore)
- Nome applicazione
- Attività
- Destinazione/i
- Categoria
- Stato

Per visualizzare informazioni più specifiche su un evento, selezionare un elemento nell'elenco:

![Ottenere informazioni più specifiche su chi ha fatto cosa nei log di controllo in Intune](./media/monitor-audit-logs/monitor-audit-log-detail.png "Dettagli dei log di controllo")

> [!NOTE]
> **Azione avviata da (attore)** include informazioni su chi ha eseguito l'attività e dove è stata eseguita. Ad esempio, se si esegue l'attività in Intune nel portale di Azure, in **Applicazione** è sempre indicato **Microsoft Intune portal extension** e **ID applicazione** usa sempre lo stesso GUID.
> 
> La sezione **Destinazione/i** elenca più destinazioni e le proprietà che sono state modificate.  

## <a name="filter-audit-events"></a>Filtrare gli eventi di controllo

Ogni carico di lavoro include una voce di menu che pre-filtra la categoria di eventi di controllo associata a tale riquadro. Un'opzione di filtro separata consente di passare a categorie diverse e visualizzare i dettagli delle azioni di evento all'interno di tale categoria. È possibile eseguire ricerche in base all'UPN, ad esempio l'utente che ha eseguito l'azione. Un filtro di intervallo di date include le opzioni 24 ore, 7 giorni o 30 giorni. Per impostazione predefinita, vengono visualizzati gli ultimi 30 giorni di eventi di controllo.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Usare l'API Graph per recuperare gli eventi di controllo

Per informazioni sull'uso dell'API Graph per ottenere fino a un anno di eventi di controllo, vedere [List auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Passaggi successivi

[Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics](review-logs-using-azure-monitor.md).

[Esaminare i log di protezione delle app client](../apps/app-protection-policy-settings-log.md).
