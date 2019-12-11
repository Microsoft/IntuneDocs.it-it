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
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991987"
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

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Amministrazione Tenant** > **log di controllo**.
3. Per filtrare i risultati, selezionare **Filtra** e perfezionare i risultati usando le opzioni seguenti.
    - **Categoria**: come la **conformità**, il **dispositivo**e il **ruolo**.
    - **Attività**: le opzioni elencate di seguito sono limitate dall'opzione scelta in **categoria**.
    - **Intervallo di date**: è possibile scegliere i log per il mese, la settimana o il giorno precedente.
4. Scegliere **Applica**.
4. Selezionare un elemento nell'elenco per visualizzare i dettagli dell'attività.

## <a name="route-logs-to-azure-monitor"></a>Indirizzare i log a Monitoraggio di Azure

I log di controllo e i log operativi possono essere anche indirizzati a Monitoraggio di Azure. In **Log di controllo** selezionare **Esporta impostazioni dati**:

![Esportare i dati di log in Monitoraggio di Azure selezionando Esporta impostazioni dati in Intune](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> Per altre informazioni su questa funzionalità e per esaminare i prerequisiti per usarla, vedere [inviare dati di log ad archiviazione, Hub eventi o log Analytics](review-logs-using-azure-monitor.md).

> [!NOTE]
> **Azione avviata da (attore)** include informazioni su chi ha eseguito l'attività e dove è stata eseguita. Ad esempio, se si esegue l'attività in Intune nel portale di Azure, in **Applicazione** è sempre indicato **Microsoft Intune portal extension** e **ID applicazione** usa sempre lo stesso GUID.
>
> La sezione **Destinazione/i** elenca più destinazioni e le proprietà che sono state modificate.  

## <a name="use-graph-api-to-retrieve-audit-events"></a>Usare l'API Graph per recuperare gli eventi di controllo

Per informazioni sull'uso dell'API Graph per ottenere fino a un anno di eventi di controllo, vedere [List auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Passaggi successivi

[Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics](review-logs-using-azure-monitor.md).

[Esaminare i log di protezione delle app client](../apps/app-protection-policy-settings-log.md).
