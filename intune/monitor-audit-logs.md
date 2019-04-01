---
title: Controllo delle modifiche e gli eventi in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni su come esaminare i log di controllo che registrano le attività di Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394902"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Usare i log di controllo per tenere traccia e monitorare gli eventi in Microsoft Intune

I log di controllo includono una registrazione delle attività che generano una modifica in Microsoft Intune. Creazione, aggiornamento (modifica), delete, assegnare e azioni remote creano eventi di controllo che gli amministratori possono esaminare per la maggior parte dei carichi di lavoro di Intune. Per impostazione predefinita, il controllo è abilitato per tutti i clienti. Non può essere disattivato.

> [!NOTE]
> Controlla eventi avviato la registrazione nel rilascio di funzionalità di dicembre 2017. Gli eventi precedenti non sono disponibili.

## <a name="who-can-access-the-data"></a>Utenti autorizzati ad accedere ai dati

Gli utenti con le autorizzazioni seguenti possono esaminare i log di controllo:

- Amministratore globale
- Amministratore del servizio Intune
- Amministratori assegnati a un ruolo di Intune con le autorizzazioni **Dati di controllo** - **Lettura**

## <a name="audit-logs-for-intune-workloads"></a>Log di controllo per i carichi di lavoro di Intune

È possibile esaminare i log di controllo nel gruppo di monitoraggio per ogni carico di lavoro di Intune:

1. Nel [portale di Azure](https://portal.azure.com/) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Scegliere il carico di lavoro che si desidera esaminare i log di controllo. Ad esempio, selezionare **dispositivi**.
3. Sotto **Monitoring**, scegliere **log di controllo**.

## <a name="route-logs-to-azure-monitor"></a>Indirizzare i log a Monitoraggio di Azure

I log di controllo e i log operativi possono essere indirizzati anche a monitoraggio di Azure. Nelle **log di controllo**, selezionare **Esporta impostazioni dati**:

![Esportare i dati di log in Azure monitor selezionando le impostazioni di esportazione dei dati in Intune](./media/audit-logs-export-data-settings.png)

Per altre informazioni su questa funzionalità, vedere [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Esaminare gli eventi di controllo

![Scegliere i log di controllo in Intune per visualizzare le azioni e le date quando gli eventi si sono verificati](./media/monitor-audit-logs.png "log di controllo")

Per un log di controllo è disponibile una visualizzazione elenco predefinita che mostra gli elementi seguenti:

- Data e ora in cui si è verificato l'evento
- Azione avviata da (attore)
- Nome applicazione
- Attività
- Destinazione/i
- Categoria
- Stato

Per visualizzare informazioni più specifiche su un evento, selezionare un elemento nell'elenco:

![Ottenere informazioni più specifiche su chi ha fatto cosa nel controllo Registra in Intune](./media/monitor-audit-log-detail.png "i dettagli del log di controllo")

> [!NOTE]
> **Azione avviata da (attore)** include informazioni su che hanno eseguito l'attività e in cui è stato eseguito. Ad esempio, se si esegue l'attività in Intune nel portale di Azure, in **Applicazione** è sempre indicato **Microsoft Intune portal extension** e **ID applicazione** usa sempre lo stesso GUID.
> 
> La sezione **Destinazione/i** elenca più destinazioni e le proprietà che sono state modificate.  

## <a name="filter-audit-events"></a>Filtrare gli eventi di controllo

Ogni carico di lavoro include una voce di menu che pre-filtra la categoria di eventi di controllo associata a tale riquadro. Un'opzione di filtro separata consente di passare a categorie diverse e visualizzare i dettagli delle azioni di evento all'interno di tale categoria. È possibile cercare di UPN, ad esempio l'utente che ha eseguito l'azione. Un filtro di intervallo di date include le opzioni 24 ore, 7 giorni o 30 giorni. Per impostazione predefinita, vengono visualizzati gli ultimi 30 giorni di eventi di controllo.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Usare l'API Graph per recuperare gli eventi di controllo

Per informazioni sull'uso dell'API graph per ottenere fino a un anno di eventi di controllo, vedere [List auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Passaggi successivi

[Inviare i dati di log all'archiviazione, hub eventi o log analitica](review-logs-using-azure-monitor.md).

[Esaminare i log di protezione delle app client](app-protection-policy-settings-log.md).
